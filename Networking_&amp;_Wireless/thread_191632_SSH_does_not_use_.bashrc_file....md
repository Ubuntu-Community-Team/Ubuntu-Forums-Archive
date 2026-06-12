---
title: "SSH does not use .bashrc file..."
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2006-06-07
As a normal users, if I ssh into my computer (either from a local network or a remote network), my bash shell does not load from the .bashrc file in my home directory. Now, I can run "source .bashrc" and it will load from that file, but whenever I ssh log in, it does not work. But here's the really strange part, if I open up a gui console on the machine, it DOES read from my .bashrc file. So, only ssh does not source read that file. 

Another very strange thing is that if I ssh log in as root on my computer, it DOES load the .bashrc file in the /root/ directory. So I know the files are good, (they are the same files). 

Can anyone help?

---

### Post by mlind on 2006-06-07
ssh probably uses .bash_profile, which is not sourcing .bashrc file

does your .bash_profile contain
```

if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

```

---

### Post by SadaraX on 2006-06-07
[QUOTE=mlind]ssh probably uses .bash_profile, which is not sourcing .bashrc file

does your .bash_profile contain
```

if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

```[/QUOTE]

There is no .bash_profile file in my home directory.... I have added that, and it fixed the problem. Very strange. This has never happened before...

---

### Post by mlind on 2006-06-07
[QUOTE=SadaraX]There is no .bash_profile file in my home directory.... I have added that, and it fixed the problem. Very strange. This has never happened before...[/QUOTE]

You can get the default version of .bash_profille from **/etc/skel**, just copy it
on your $HOME folder. These two files should have appeared there automatically
when user was created, if shell was set to bash. I dunno why this didn't happen,
but it's nothing to worry about.

---

### Post by davebgimp on 2006-10-20
I'm having a sort of similar issue. I have a remote server that I SSH into regularly. I have both a .bash_profile and .bashrc present in my home directory.

However, when I log in, it never reads the .bashrc unless I manually type **source .bashrc**

My .bash_profile seems in order and I'll post it below. Could there be something I'm missing or have not set correctly?

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.
 
# the default umask is set in /etc/login.defs
#umask 022
 
# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
. ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
PATH=~/bin:"${PATH}"
fi

```

---

### Post by taurus on 2006-10-20
Hey, your ~/.bash_profile is exactly like mine and I don't have any problem with it...  What is the output of this command then?

```
ls -la ~/.bash*
```

---

### Post by davebgimp on 2006-10-20
> **taurus said:**
> Hey, your ~/.bash_profile is exactly like mine and I don't have any problem with it...  What is the output of this command then?

```
ls -la ~/.bash*
```

-rw-r--r-- 1 daveb admin  353 2006-05-17 00:46 /home/daveb/.bash_aliases
-rw------- 1 daveb daveb 7880 2006-10-20 12:24 /home/daveb/.bash_history
-rw-r--r-- 1 daveb daveb  414 2006-05-15 12:28 /home/daveb/.bash_profile
-rw-r--r-- 1 daveb daveb 2227 2006-10-20 12:14 /home/daveb/.bashrc

---

### Post by davebgimp on 2006-10-25
Just futzing around, noticed that the /root folder was using .profile instead of .bash_profile.

So, I renamed my own .bash_profile similarly and logging in, my .bashrc is now being read.

---

