---
title: "Samba is pissing me the **** off..."
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2010-03-08
Alright, I've been trying to configure samba to let me log into my god damn password protected share for HOURS now, and the stupid friggin thing keeps insisting my password is wrong!

Here is my configuration file with the share causing trouble. Anything removed is default crap that comes in every smb.conf file:

```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# User map
  username map = /etc/samba/smbusers

# Location of usernames password file
  smb passwd file = /etc/samba/smbpasswd

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = smbpasswd

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

#======================= Share Definitions =======================

[ROUTER_LOGS]
path = /home/dillon/ROUTER_LOGS
browsable = no
write list = dillon
create mask = 0775
public = yes
guest ok = no

```

Now I've tried about 150 times to add myself as a user:

```
sudo smbpasswd -a dillon
```

And it appears to work.

Now for some reason in every other machine where I try to access \\<my-ip>\ROUTER_LOGS, I'm prompted to for my username and password. No matter what, every single friggin time it tells me my password is incorrect and prompts me again. The username and password I'm using are the ones I entered in smbpasswd, and yes, 'dillon' is an account also on the machine.

Any help would be GREATLY appreciated.

Thanks in advance for helping me avoid total insanity :)

---

### Post by cariboo on 2010-03-08
Have you enabled the user?

```
sudo smbpasswd -L -e dillon
```

Please refrain from using profanity, as this is a family friendly forum, we have users as young as 8 years old.

---

### Post by ownaginatious on 2010-03-08
Thanks. I just tried what you posted, but it unfortunately made no difference whatsoever :(.

Could it be something in my configuration posted above?

---

### Post by suseendran.rengabashyam on 2010-03-08
Hi,

In your smb.conf file try changing

```
security = share
```

to

```
security = user
```

and restart your SAMBA daemon.

Source:
Search for "write list" in the following link [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Hope this helps.

---

### Post by ownaginatious on 2010-03-08
Okay thank you, I'll give that a try.

Just one question though, will setting security to user disallow guests from connecting? I have some other shared folders that anyone can access.

Thanks.

---

### Post by suseendran.rengabashyam on 2010-03-08
Hi,

I guess that won't be an issue. The following lines in smb.conf is needed to create an anonymous read/write share 

```
[ReadWriteShare]
path = </path/to/shared/folder>
guest ok = yes
read only = no
force user = <username>
force group = <groupname>
```

Make necessary changes to path, force user,etc. The <username> and <groupname> would be the one relevant to the folder which you have mentioned in the path directive.

---

