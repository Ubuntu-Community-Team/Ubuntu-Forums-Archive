---
title: "Firmware missing for wireless connection"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by Welshybabe on 2013-01-16
Hi all, I am completely new to Ubuntu and love it so far, but cannot for the life of me get my wireless connection to work?

I have a Dell Inspiron 1520 and have the 12.04 version of Ubuntu running alongside Windows 7. I can connect using ethernet cable but not wireless!

At the top right of the screen in the network tab it says device not ready (firmware missing), and when i ran "sudo lshw -C network" in my terminal, i got *-network DISABLED. 



Would be really grateful if someone could help and in baby steps please as very new to all this, thanks ;)

---

### Post by pressi on 2013-01-16
[http://ubuntuforums.org/showpost.php?p=12001985&postcount=2](http://ubuntuforums.org/showpost.php?p=12001985&postcount=2)

or


[http://ubuntuforums.org/showthread.php?t=1974006](http://ubuntuforums.org/showthread.php?t=1974006)

---

### Post by mad2-814 on 2013-01-16
post the output of 
```
lspci -nn
```

---

