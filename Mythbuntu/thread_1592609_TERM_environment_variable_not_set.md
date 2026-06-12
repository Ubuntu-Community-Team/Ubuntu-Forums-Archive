---
title: "TERM environment variable not set"
date: 2010-10-10
forum: Mythbuntu
---

### Post by DrJohn999 on 2010-10-10
In a fresh install of Mythbuntu 10.10, running Accessories, Terminal (xfce terminal emulator):
```
> echo $TERM
dumb
> 
```
This results in apps that need to know what's available (top for example) reporting "TERM environment variable not set" and halting.
```
> export TERM=xterm
```
fixes this temporarily. This was seen earlier in some RC systems, bug reported, and apparently fixed [[COLOR="Navy"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1592373"), maybe only for gnome, but this should have been spotted and fixed before release; maybe it crept in at the last moment...?

---

### Post by tgm4883 on 2010-10-10
> **DrJohn999 said:**
> In a fresh install of Mythbuntu 10.10, running Accessories, Terminal (xfce terminal emulator):
```
> echo $TERM
dumb
> 
```
This results in apps that need to know what's available (top for example) reporting "TERM environment variable not set" and halting.
```
> export TERM=xterm
```
fixes this temporarily. This was seen earlier in some RC systems, bug reported, and apparently fixed [[COLOR="Navy"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1592373"), maybe only for gnome, **but this should have been spotted and fixed before release**; maybe it crept in at the last moment...?

I didn't look extremely hard, but I couldn't find a bug filed against Mythbuntu for that. It's hard to fix bugs we don't know about.

---

### Post by DrJohn999 on 2010-10-10
I couldn't find anything either: submitted Bug 658058

---

### Post by bokaal on 2010-10-11
Exactly the same with xubuntu 10.10, after an upgrade.

---

### Post by brunosouza on 2010-10-11
I had the same output with an ubuntu 10.10 fresh install.

---

### Post by justinmc on 2010-10-11
Confirmed as well, but only on the avant-window-navigator terminal. I am not getting the error with xterm or mrxvt.

---

### Post by DrJohn999 on 2010-10-11
Bug 658058 is a duplicate of bug 621927
    [https://bugs.launchpad.net/bugs/621927](https://bugs.launchpad.net/bugs/621927)

Pending a permanent fix this might help:

```
echo "export TERM=xterm" | sudo tee /etc/profile.d/set_term.sh && source /etc/profile
```

(copied from [https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/635804/comments/4](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/635804/comments/4) )

---

### Post by justinmc on 2010-10-11
Adding

```
export TERM=xterm
``` 

to the top of ~/.bashrc should work just as well. This way, you only edit your files. The downside is that, if you have multiple accounts, you would have to do this on every one.

FWIW, I like staying away from system stuff if possible :-)

---

