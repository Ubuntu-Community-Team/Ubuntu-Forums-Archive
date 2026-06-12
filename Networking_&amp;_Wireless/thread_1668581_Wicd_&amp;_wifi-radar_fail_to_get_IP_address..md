---
title: "Wicd &amp; wifi-radar fail to get IP address."
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by AggravatedGestalt on 2011-01-16
When trying to connect to a wireless AP, neither wicd or wifi-radar are able to obtain an IP. With wicd, a string of various hex/dec characters flow by, with an eventual error. This happens with both WEP and unencrypted APs (- the hex/dec). With wifi-radar it simply fails, but not every time. NetworkManager connects with zero problems every time; though I prefer to not use NetworkManager, so please spare me of such replies. Someone please tell me why there should be only one wireless manager in Ubuntu that works? I have used wicd since before gutsy gibbon, and it always worked fine until the last two versions, Lucid, and Karmic. What is occurring in Ubuntu which over time breaks these excellent applications? I have tried this with four different wireless cards, and all suffer either identical or similar issues. Those chipsets are Broadcom, two RealTeks, and an Intel.

I really wish to emphasize that this post is not a request for a lecture on why I should use only NetworkManager, or why I should go find another distro. With something like Linux, maybe we could push a little harder, and have maybe say, two, wireless managers that actually work? I would honestly like to see more than two, but one is not enough. It baffles me a bit why new versions of Ubuntu mangle some perfectly good applications, but not others. In IT, surely networking, IP4, WEP, basic wifi technology, etc. has not changed so much that every six months whole new programs should need to be written to connect to a wireless access point. Nor should old ones need much tweaking. What's going on? With such boastings of repositories abundant and brimming with free apps, why does anyone want to make NetworkManager the only app that works?

---

### Post by ggarron on 2011-01-16
I'm using wicd on Slackware right now.

You may try to run:

wicd-curses (do not know if is the right command for Ubuntu)

Then, <shift>P (I mean uppercase P), then with right arrow, go to "External Programs".. And on DHCP client, select another one, one that may works.

Is not wicd fault, is your dhcp client fault, so just use another one. If you can guess which is Network Manager using, select that one.

I do not have network manager installed, so I can not help on that.

---

### Post by ggarron on 2011-01-16
I'm using wicd on Slackware right now.

You may try to run:

wicd-curses (do not know if is the right command for Ubuntu)

Then, <shift>P (I mean uppercase P), then with right arrow, go to "External Programs".. And on DHCP client, select another one, one that may works.

Is not wicd fault, is your dhcp client fault, so just use another one. If you can guess which is Network Manager using, select that one.

I do not have network manager installed, so I can not help on that.

Here is a Screenshot

[http://i.imgur.com/tQ7V8.png](http://i.imgur.com/tQ7V8.png)

---

### Post by ggarron on 2011-01-16
Sorry for the double post, ... the last one has a screenshot, if someone can, please delete the first one.

---

### Post by AggravatedGestalt on 2011-01-16
Thank you, ggarron. 

I installed DHCPCD, which did not work. I will attempt to apply your suggestions and report back.

---

### Post by AggravatedGestalt on 2011-01-16
Thank you, ggarron. 

I installed DHCPCD, which did not work. I will attempt to apply your suggestions and report back.

---

### Post by AggravatedGestalt on 2011-01-16
Thank you, ggarron. 

I installed DHCPCD, which did not work. I will attempt to apply your suggestions and report back. 

Regarding double posts, I am having trouble posting myself.

---

### Post by AggravatedGestalt on 2011-01-16
Thank you, ggarron. 

I installed DHCPCD, which did not work. I will attempt to apply your suggestions and report back.

---

### Post by AggravatedGestalt on 2011-01-16
Thank you, ggarron. 

I installed DHCPCD, which did not work. I will attempt to apply your suggestions and report back.

---

### Post by AggravatedGestalt on 2011-01-16
Thank you, ggarron. 

I installed DHCPCD, which did not work. I will attempt to apply your suggestions and report back. 

Regarding double posts, I am having trouble posting myself.

---

### Post by ggarron on 2011-01-17
Let me know how it goes.

---

### Post by AggravatedGestalt on 2011-01-17
Gee! All those duplicate posts look terrible. Sorry all. 

ggarron,



I attempted to set the dhcp client to both dhcpcd, and dhclient (what NM uses), and neither worked. I did this through wicd-curses, and the standard GUI. I might also mention that originally I had NM entirely removed, and wicd would work at least occasionally. However, I recently reinstalled NM and set it to not load at boot, and wicd is now completely useless. Should I proceed by installing the other dhcp clients listed in wicd? 

Unrelated side note: I am using Midori, and I think this is the cause of the duplicate postings. Every time I post, it deletes my text and tells me to enter "at least one character". I hope *everything* is not becoming incompatible with Ubuntu!

---

### Post by ggarron on 2011-01-18
Are you sure you do not have NM and Wicd daemons both running?
I use mostly Arch Linux and Slackware, and as I have to enable the daemons I want to run, is easy for me. 
With Ubuntu, they are enabled all by default IMHO, so be sure to disable NM and leave only Wicd enable.

---

### Post by ggarron on 2011-01-18
You may want to use some of these,

[http://www.go2linux.org/ntsysv-for-debian-sysvconfig-or-sysv-rc-conf](http://www.go2linux.org/ntsysv-for-debian-sysvconfig-or-sysv-rc-conf)

To check which daemons are enabled.

or use rcconf or update-rc.d

---

### Post by AggravatedGestalt on 2011-01-18
Yes, I am sure. 

Despite that it was an issue previously with NM completely uninstalled, I still did the following: sudo service network-manager stop. The ghastly thing respawns like a demon rather than daemon! (with: killall -9). I also tried uninstalling wicd altogether, reinstalling only the wicd-curses, and then only wicd after uninstalling wicd-curses. Nothing has had any effect. It's a bummer; I really like wicd, when it works. NM just plain sucks.

---

### Post by ggarron on 2011-01-19
Wow, I am really annoyed!
I do not understand why it is not working.
I also like wicd over NM, and never use NM... Just wicd.
Anyone, may help here?

---

### Post by ggarron on 2011-01-19
Wow, I am really annoyed!
I do not understand why it is not working.
I also like wicd over NM, and never use NM... Just wicd.
Anyone, may help here?

---

