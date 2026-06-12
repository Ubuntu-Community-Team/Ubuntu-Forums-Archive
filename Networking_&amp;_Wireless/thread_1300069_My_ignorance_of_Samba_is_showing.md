---
title: "My ignorance of Samba is showing"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by clnanderson on 2009-10-24
I've been having problems with samba and have never been able to get it straightened out, after spending several evenings and afternoons reading howtos and trying to figure out what's wrong.

I feel like I don't understand authentication. I have a unix machine with an account name ("initials") and an xp machine with a username from work ("email"). I want to share folders for the xp machine.

My question is how I can "map" the logon /domain/"email" to a unix account "initials." 

The passwords are different and I can't figure out which username and which password should be provided when I try to browse the shares. I can see the shares, but when I click to browse in explorer, I get the logon prompt, but can't find any combination of user names and passwords to get logged on.

I have the following accounts

Unix accounts "initials" "email"
Samba accounts "initials" "email"
XP accounts "email"

which password and username is the logon window asking for when I try to logon from xp?

Thanks for any help.

Here's some parts of my smb.conf

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
# security = share
security=user
username map=/etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
map to guest = Bad User


#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
  browseable = yes
valid users = {"initials"}
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

---

