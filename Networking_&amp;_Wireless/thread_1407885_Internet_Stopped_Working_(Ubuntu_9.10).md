---
title: "Internet Stopped Working (Ubuntu 9.10)"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Anaximander2889 on 2010-02-15
I'm still getting used to Ubuntu, but a few days ago, my brother told me that when he was googling something, Mozilla froze, and he did a manual power down and reboot.  Now, the network manager doesn't show up in the top right corner, and upon start up, I was asked to put in my password to unlock the keyring, but that didn't show up either.  I am unable to connect to the internet now either wireless or wired.  I'm not quite sure what to do.

---

### Post by ant2ne on 2010-02-15
I think I saw a thread somewhere around here about restoring network manager. I suggest a search.

---

### Post by Anaximander2889 on 2010-02-16
Well, two things have happened so far,

1. I found out that the internet still works at my apartment, but not at college anymore.

2. I got rid of network manager and installed wicd, which I'm not able to get working right now.  I tried entering wicd-client in terminal, and I get a message back saying "ImportError: No module named wicd.wpath"

---

### Post by Anaximander2889 on 2010-02-17
Just found out that now since I've installed wicd, I cannot connect to the internet anywhere, and wicd won't open.

---

### Post by Anaximander2889 on 2010-02-17
When I run wicd-client in terminal, I get a message saying 

ImportError: No module named wicd.wpath

---

### Post by ant2ne on 2010-02-18
I heard some rumor that wicd is not going to be in debian anymore. Not sure if that is related.

---

### Post by jruberto on 2010-02-18
Happened to me too.  The simple fix was to edit /etc/wicd/wired-settings.conf and find a line that is just a pair of brackets by itself like:  []  and delete it.

---

### Post by Anaximander2889 on 2010-02-19
The only folder I found in the /etc/wicd was the encryption folder, and I tried searching for it.  Also I tried running edit /etc/wicd/wired-settings.conf in terminal and I got a message saying

Error: no write permission for file "/etc/wicd/wired-settings.conf"

---

### Post by jruberto on 2010-02-19
You'll probably need to sudo edit the config file as it is a system config file.

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

If you aren't familiar with the console text editors, nano is probably the "easiest", at least the help is on the screen when you run it.  go out to a console and
```
 sudo nano /etc/wicd/wired-settings.conf
```find a line that is just 
```
 []
```and delete it. If there isn't a line that looks like that, then that isn't the problem, and i'm sorry.  Best of luck.

---

### Post by Anaximander2889 on 2010-02-19
When I ran the code that you told me to run, I don't see any lines of text at all.  Should I be able to see stuff other than just that?

---

### Post by jruberto on 2010-02-21
you can also just delete that file and restart.  easier.  might be even better to just totally remove & re-add wicd using synaptic or software center.

wicd has been kind of unpredictable on my system too, hoping there are some bugfix updates soon.

---

