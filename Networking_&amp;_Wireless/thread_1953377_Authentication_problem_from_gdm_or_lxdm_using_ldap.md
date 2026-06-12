---
title: "Authentication problem from gdm or lxdm using ldap user"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by ultreja on 2012-04-06
Hi,
hope this is the right section.

i've problems trying login from login manager of my ubuntu 10.10 client using ldap user credential. Ldap server is squeeze.
i can enter only using the local user credentials of the client and i can login using a console(ctrl-alt-f1) using ldap user credentials but not with login manager as gdm or lxdm.

this is the output of auth.log:

Apr  4 15:50:51 dello gdm-session-worker[3414]: pam_succeed_if(gdm:auth): error retrieving information about user nslcd_proc
Apr  4 15:51:04 dello pkexec[3421]: gdm: The value for the SHELL variable was not found the /etc/shells file [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 15]
Apr  4 15:51:17 dello gdm-session-worker[3414]: pam_unix(gdm:auth): check pass; user unknown
Apr  4 15:51:17 dello gdm-session-worker[3414]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=
Apr  4 15:51:17 dello pkexec[3423]: gdm: The value for the SHELL variable was not found the /etc/shells file [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 15]
Apr  4 15:51:42 dello pkexec[3429]: gdm: The value for the SHELL variable was not found the /etc/shells file [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 15]

What is the problem?

---

### Post by lunamystry on 2012-06-13
Hey try this:
[https://help.ubuntu.com/community/LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication")

It seems to have worked for me. I was getting the same error as you. 

There is also a bug report if you are interested. I used the instructions from there to sort out lightdm: 
[https://bugs.launchpad.net/lightdm/+bug/944041]("https://bugs.launchpad.net/lightdm/+bug/944041")

Hope it helps,
Mandla

---

