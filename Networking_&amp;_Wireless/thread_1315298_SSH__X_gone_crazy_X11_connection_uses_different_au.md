---
title: "SSH / X gone crazy: X11 connection uses different authentication protocol."
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by ptrxyz on 2009-11-05
I have a desktop machine running Debian 5.0.3 and a Laptop running Ubuntu 9.10 Karmic Koala.
I setup a ssh server on my laptop so I should be able to connect from my desktop via ssh...all working great.

The problem: if I connect from the Debian machine to the laptop with:

ssh -XC <laptop> -vvvvv 

and start gedit I get this error:

```

....
debug1: channel 2: new [x11]
debug1: confirm x11
debug2: X11 connection uses different authentication protocol.
X11 connection rejected because of wrong authentication.
debug2: X11 rejected 2 i0/o0
debug2: channel 2: read failed
debug2: channel 2: close_read
....

```

All other applications ... like kate, xclock, xterm or gnome-terminal are working! but gedit doesn't!

Here is my sshd config:

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

And here my .ssh/config:

```

ForwardAgent		yes
ForwardX11			yes
ForwardX11Trusted	yes
Compression			yes

Host dektop
	User		<hidden ;)>
	HostName	<hidden ;)>

```

Any help would be appreciated... =)

Edit: X server on both machines is version 1.6.4

---

### Post by ptrxyz on 2009-11-05
I searched the web and found out it might be related to the .Xauthority file and something about gedit using an old version of Xlib...

So maybe someone needs that info to help me:

I deleted the .Xauthority file on both machines, now gedit works if i ssh from dektop to laptop, but not the other way....what am I doing wrong ... ?

Noone an idea?

---

### Post by ptrxyz on 2009-11-05
Another thing to add what I found out: if I am root on the desktop, I CAN start gedit...no errors. only when I am a normal user I get the error...

```

> ssh -YC normal_user@desktop
> gedit
X11 connection rejected because of wrong authentication.
>

```

```

> ssh -YC root@desktop
> gedit
> # starts as it should! since I am root...

```

So...ideas please?

---

### Post by ptrxyz on 2009-11-10
Bump =)

---

### Post by cougar97536 on 2009-11-24
have this same issue... trying to ssh from my ubuntu 9.04 laptop to my 9.10 desktop... all other apps seem to work but gedit is giving me this same error... hope you get it solved... sorry I couldn't be of any real help...

---

### Post by pondchn on 2010-12-17
here is the reason:
[https://bugzilla.redhat.com/show_bug.cgi?id=209452](https://bugzilla.redhat.com/show_bug.cgi?id=209452)

so,you need close gedit on your ssh server if you login in with the same account.if you login in with another account,the issue doesn't exist. you can try it.

---

### Post by Tarion on 2012-06-11
This was my problem too. Really hard to diagnose. 

Basically because gedit was open on the host computer, I couldn't open it locally via X11 tunneling. Does anyone know of any other programs that won't allow tunneling if they're already open?

Anyway, Thanks. This post helped me clear that up much faster.

---

### Post by cariboo on 2012-06-11
Thread closed, as it's over 2 years old.

---

