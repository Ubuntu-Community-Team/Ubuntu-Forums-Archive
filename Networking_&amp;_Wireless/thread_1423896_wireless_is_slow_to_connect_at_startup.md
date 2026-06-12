---
title: "wireless is slow to connect at startup"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by moveright on 2010-03-07
I am running 9.10 on my compaq laptop.  I tried linux a couple years ago and was not impressed with it's operation on this machine (wifi didn't work, pain in the butt to make it work) but I just installed 9.10 and to my surprise, everything on this machine seems to work now automatically!

One minor annoyance though, when I boot my machine and the gnome desktop loads, it takes about 1 minute until the wireless finds and connects to my router.  Granted, my SSID is set to not broadcast but I set ubuntu to find it as a hidden network and it does in fact work, just takes more time than usual to find and connect.  Normally with windows, when it loaded, my wifi was present and connected immediately.


Any suggestions?

---

### Post by Swagman on 2010-03-07
Probably....

Ubuntu boots faster to the desktop than win but the net interface takes longer to establish. Because your already at the desktop you want to instantly surf ?

How long does win take to get to a usable state from hitting the power on switch to being able to connect ?

---

### Post by moveright on 2010-03-07
Well, Ubuntu seems to be much faster overall performance wise, i.e. boot time, program loading, etc...  I was just curious if the net interface is for example, the last thing to load by default and I could change the priority so that it was one of the first things to load.  but yes, what I use the computer for is just internet mainly so when I boot the machine, it is the first thing I go to.

---

### Post by 2hot6ft2 on 2010-03-07
Seems to me that even though win7 shows it as connected at first but it soon switches to having a yellow circle (limited connection), then it actually connects.

---

### Post by lswb on 2010-03-07
One thing that may help is to right-click the NetworkManager icon, select Edit Connections/Wirelss, select your network from the list, then click on edit. You may be prompted for a password. In the dialog box that then appears, near the bottom, check the box for "Available to All Users". This will enable connection to the network before the Desktop loads.

If you don't see your network listed, you may have to make your ESSID visible in your router settings.

---

