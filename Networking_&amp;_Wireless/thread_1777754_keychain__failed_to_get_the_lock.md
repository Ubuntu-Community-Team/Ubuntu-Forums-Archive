---
title: "keychain : failed to get the lock"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by lalebarde on 2011-06-08
Hi all,
I am trying to use ssh and keychain on my local home network. ssh works well with X11 forwarding. So now **I want my pass-phrase kept by keychain. But it fails to "lock"**. I followed the following tutorials :
[LIST]http://www.ibm.com/developerworks/library/l-keyc2/
[http://en.gentoo-wiki.com/wiki/Keychain](http://en.gentoo-wiki.com/wiki/Keychain)
[/LIST]
But I get (ever by "hand" or with use of ~/.bashrc) :```
alain@IBM-ThinkPad:~$ ssh-add ~/.ssh/id_dsa
Enter passphrase for /home/alain/.ssh/id_dsa: 
Identity added: /home/alain/.ssh/id_dsa (/home/alain/.ssh/id_dsa)
alain@IBM-ThinkPad:~$ /usr/bin/keychain ~/.ssh/id_dsa

KeyChain 2.6.8; http://www.gentoo.org/proj/en/keychain/
Copyright 2002-2004 Gentoo Foundation; Distributed under the GPL

 * Waiting 30 seconds for lock, held by pid 6003
 * Waiting 29 seconds for lock, held by pid 6003
 * Waiting 28 seconds for lock, held by pid 6003
.....
 * Waiting 2 seconds for lock, held by pid 6003
 * Waiting 1 seconds for lock, held by pid 6003
 * Error: failed to get the lock, held by pid 6003: /usr/bin/keychain: 1489: cannot create /home/alain/.keychain/IBM-ThinkPad-lockf: Permission denied
```

**~/.bashrc**
```
### START-Keychain ###
# Let  re-use ssh-agent and/or gpg-agent between logins
/usr/bin/keychain $HOME/.ssh/id_dsa
source $HOME/.keychain/$HOSTNAME-sh
### End-Keychain ###

```

I tryed to add before this, still in ~/.bashrc :```
eval `ssh-agent`
```but it changes nothing.

If I check the file ~/.keychain/IBM-ThinkPad-lockf said [COLOR="Red"]Permission denied[/COLOR] in the error message above, I have : ```
alain@IBM-ThinkPad:~$ ls -l /home/alain/.keychain/IBM-ThinkPad-lockf
-r-------- 1 alain alain 5 2011-06-08 09:32 /home/alain/.keychain/IBM-ThinkPad-lockf
```If I chmod 777 it, it is correctly set to rwx for everybody, but when I retry the keychain command, I get the same error and the lock file is set back to user read only.


Any clue please ?

---

