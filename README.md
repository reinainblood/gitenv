# GitEnv

GitEnv is a simple and lightweight tool to dynamically switch between multiple Git profiles for work, personal, or any other use case. It also supports creating new profiles on-the-fly with custom configurations.

## Features

- Dynamically switches Git profiles by setting an environment variable (`GIT_PROFILE`).
- Supports interactive creation of new Git profiles with user-provided details.
- Works seamlessly with profiles using SSH, PGP signing, or both.
- Requires no additional files other than `~/.gitconfig-*` for each profile.

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/GitEnv.git
   cd GitEnv

## Make script executable and add to path

``` chmod +x switch_git_profile.sh
    mv switch_git_profile.sh /usr/local/bin/gitenv

    ## add to .*rc file optional
    alias gitenv="/usr/local/bin/gitenv"
    source ~/.bashrc
```
## Usage

 -  Switch to an Existing Profile
      Run the following command to switch to a profile (e.g., work or personal):

      ``` gitenv work ```
      This sets the environment variable GIT_PROFILE to work and dynamically includes the profile stored in ~/.gitconfig-work.
-  Create a New Profile
     If the specified profile does not exist, GitEnv will prompt you to create it interactively:
    ``` gitenv newprofile ```
- Unset profile
    To unset the active profile and revert to the default Git configuration:
    ``` gitenv ```
  
## Example Configurations
```
  ~/.gitconfig-work

  A profile with PGP signing:
  
  [user]
  name = Work User
  email = work@example.com
  signingkey = ABCD1234EF567890  # Your PGP key ID
  
  [commit]
  gpgSign = true
  
  [credential]
  helper = cache
  
  ~/.gitconfig-personal
  
  A profile using SSH:
  
  [user]
  name = Personal User
  email = personal@example.com
  
  [core]
  sshCommand = ssh -i ~/.ssh/id_rsa_personal ```
