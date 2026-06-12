---
title: "Network manager authentication issue"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by yeleek on 2010-08-18
Hi,

Trying to change via Network Manager from DHCP to Static address.  Once complete asks for password, try my (ben) password and root password (have enabled root) and get authentication failures.  Normally the root password works fine as added rootpw to sudoers.

Auth.log gives
Aug 18 09:57:15 WOPR polkit-agent-helper-1[15450]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=ben rhost=  user=ben
Aug 18 09:57:15 WOPR polkit-agent-helper-1[15450]: pam_winbind(polkit-1:auth): getting password (0x00000388)
Aug 18 09:57:15 WOPR polkit-agent-helper-1[15450]: pam_winbind(polkit-1:auth): pam_get_item returned a password
Aug 18 09:57:15 WOPR polkit-agent-helper-1[15450]: pam_winbind(polkit-1:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug 18 09:57:20 WOPR polkit-agent-helper-1[15453]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=ben rhost=  user=ben
Aug 18 09:57:20 WOPR polkit-agent-helper-1[15453]: pam_winbind(polkit-1:auth): getting password (0x00000388)
Aug 18 09:57:20 WOPR polkit-agent-helper-1[15453]: pam_winbind(polkit-1:auth): pam_get_item returned a password
Aug 18 09:57:20 WOPR polkit-agent-helper-1[15453]: pam_winbind(polkit-1:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug 18 09:57:26 WOPR polkit-agent-helper-1[15454]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=ben rhost=  user=ben
Aug 18 09:57:26 WOPR polkit-agent-helper-1[15454]: pam_winbind(polkit-1:auth): getting password (0x00000388)
Aug 18 09:57:26 WOPR polkit-agent-helper-1[15454]: pam_winbind(polkit-1:auth): pam_get_item returned a password
Aug 18 09:57:26 WOPR polkit-agent-helper-1[15454]: pam_winbind(polkit-1:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug 18 09:57:28 WOPR polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 FAILED to authenticate to gain authorization for action org.freedesktop.network-manager-settings.system.modify for system-bus-name::1.66 [/usr/bin/nm-connection-editor] (owned by unix-user:ben)


And sudoers is

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset,rootpw

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Any ideas pls?

---

