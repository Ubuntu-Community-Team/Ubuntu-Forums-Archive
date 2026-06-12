---
title: "ssh problem"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Alcareru on 2009-04-27
Hi

I recently installed fresh ubuntu jaunty on my desktop machine. Naturally now as I try to connect to it via ssh from my laptop in my LAN:
ssh timo@timo-desktop
I get error about changed fingerprint..

Now I know the simple solution to this. Just delete the line it complains about from the client and the next time I'd try to ssh it would ask me if I'd like to add the key. But if I do that I will not be able to ssh from my laptop to my desktop if I boot the older version of ubuntu.

So I guess what I'm asking is how do I add several accepted fingerprints for the same physical computer and/or how to make all different distributions on the same computer to have the same fingerprint? I guess I need a line in the known_hosts file. I just don't understand the known_hosts file, it looks like pure nonsense to me. Or then I need to copy some configuration files form the previous installation on my desktop machine but I don't know which ones to copy.

---

### Post by kevdog on 2009-04-27
You might want to set the following pararmeter to no in your situation:

  StrictHostKeyChecking
       If this flag is set to ``yes'', ssh will	never automatically add	host
       keys to the $HOME/.ssh/known_hosts file,	and refuses to connect to
       hosts whose host	key has	changed.  This provides	maximum	protection
       against trojan horse attacks, however, can be annoying when the
       /usr/local/etc/ssh_known_hosts file is poorly maintained, or connec-
       tions to	new hosts are frequently made.	This option forces the user
       to manually add all new hosts.  If this flag is set to ``no'', ssh
       will automatically add new host keys to the user	known hosts files.
       If this flag is set to ``ask'', new host	keys will be added to the
       user known host files only after	the user has confirmed that is what
       they really want	to do, and ssh will refuse to connect to hosts whose
       host key	has changed.  The host keys of known hosts will	be verified
       automatically in	all cases.  The	argument must be ``yes'', ``no'' or
       ``ask''.	 The default is	``ask''.

---

### Post by eldragon on 2009-04-27
check the error, it says which line of your known hosts is offending. you just need to delete it from ~/.ssh/known_hosts

this happened cause your destkop has the same hostname but a different fingerprint.. which gets stored the first time you connect to that box

---

### Post by Alcareru on 2009-04-27
> **kevdog said:**
> You might want to set the following pararmeter to no in your situation:

  StrictHostKeyChecking
       If this flag is set to ``yes'', ssh will	never automatically add	host
       keys to the $HOME/.ssh/known_hosts file,	and refuses to connect to
       hosts whose host	key has	changed.  This provides	maximum	protection
       against trojan horse attacks, however, can be annoying when the
       /usr/local/etc/ssh_known_hosts file is poorly maintained, or connec-
       tions to	new hosts are frequently made.	This option forces the user
       to manually add all new hosts.  If this flag is set to ``no'', ssh
       will automatically add new host keys to the user	known hosts files.
       If this flag is set to ``ask'', new host	keys will be added to the
       user known host files only after	the user has confirmed that is what
       they really want	to do, and ssh will refuse to connect to hosts whose
       host key	has changed.  The host keys of known hosts will	be verified
       automatically in	all cases.  The	argument must be ``yes'', ``no'' or
       ``ask''.	 The default is	``ask''.
I've tried:
ssh -o StrictHostKeyChecking=no timo@timo-desktop
but then it complains:
Password authentication is disabled to avoid man-in-the-middle attacks.
Keyboard-interactive authentication is disabled to avoid man-in-the-middle attacks.
Permission denied (publickey,password).

EDIT: That approach also has some security issues if I later want to make it possible for me to log in to my desktop from outside of my lan.


> **eldragon said:**
> check the error, it says which line of your known hosts is offending. you just need to delete it from ~/.ssh/known_hosts

this happened cause your destkop has the same hostname but a different fingerprint.. which gets stored the first time you connect to that box

As I said in my original post I don't want to delete the line because then I can't log in if I boot my desktop with the older ubuntu installation.

---

### Post by Alcareru on 2009-04-28
Ok I figured it out myself:
man sshd_config
     HostKey
             Specifies a file containing a private host key used by SSH.  The
             default is /etc/ssh/ssh_host_key for protocol version 1, and
             /etc/ssh/ssh_host_rsa_key and /etc/ssh/ssh_host_dsa_key for pro-
             tocol version 2.  Note that sshd(8) will refuse to use a file if
             it is group/world-accessible.  It is possible to have multiple
             host key files.  ``rsa1'' keys are used for version 1 and ``dsa''
             or ``rsa'' are used for version 2 of the SSH protocol.

So just make sure all of your os's on any ssh host computer use the same ssh host keys. Either copy those files from one of your os's to others or place them in a custom place that each of your os's have access to and specify the custom path to those files in the file /etc/ssh/sshd_config . If you are missing some of those files it is probably due to the fact that your ssh-server supports only ssh protocol 1 or 2 but not both, so don't worry about it.

Oh yeah. I almost forgot. You might also want to copy the .pub keyfiles (located in the same place as the other keys). I'm not sure if you are actually required to do that, but I did it :)

---

