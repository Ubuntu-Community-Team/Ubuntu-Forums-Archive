---
title: "mediatomb deamon doesn't start"
date: 2008-09-17
forum: Multimedia Software
---

### Post by wildtiger23 on 2008-09-17
I can see the file in /etc/rc2.d/S20mediatomb and if I want to use it I need to start it manually... What can I do and where can I find logs to understand what's a penning?

---

### Post by wildtiger23 on 2008-09-19
Nobody can answer my little question...

---

### Post by drvid on 2008-10-11
I'm having this same problem on 8.04 amd64 :(

I have to sudo _/etc/init.d/mediatomb start_ after every time I reboot!

It's also in here I noticed...

lrwxrwxrwx 1 root root 19 2008-05-06 10:52 /etc/rc5.d/S20mediatomb -> ../init.d/mediatomb

---

### Post by amak79 on 2008-10-13
I suspect the reason it doesn't start at boot is that you are using NetworkManager. The problem with NetworkManager is that it enables your network device only after you have logged in, but MediaTomb needs to have the network device enabled during boot. To fix this issue just disable the "Enable roaming mode" option in the Network Settings applet.

---

