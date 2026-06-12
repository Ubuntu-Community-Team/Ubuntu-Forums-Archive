---
title: "HP Mini 110-1046NR Wireless problems"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by james17 on 2011-06-01
complete noob when it comes to Ubuntu, want to get wireless on the laptop but it says firmware missing. If you all would please walk me through very detailed instuctions. Thanks Ubuntu peoples.

---

### Post by chili555 on 2011-06-01
We'll be glad to help. We are going to use the terminal a bit; it allows us to gather a lot of detailed data in a hurry. First, let's find out what wireless card you have. Open Applications > Terminal (or Applications > Accessories > Terminal) and run and post:```
lspci -nn
```Feel free to trim away any lines that are not your wireless card.

Can you walk your Mini over to the router and get an ethernet connection if we need to download something? We might be able to fix this in quick order!

---

### Post by james17 on 2011-06-01
thanks a lot Chili555, is this what i was looking for?
 
1:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by chili555 on 2011-06-01
Exactly, although it may turn out to be a challenge. Your device is claimed by two different drivers. I'm not quite sure which is best yet. Let's try one and blacklist the other and see if we coax your device to life. Open the terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor will open. Add two lines at the end.```
blacklist b43
blacklist ssb
```Proofread carefully, save and close gedit. Now hook up the ethernet cable, get a connection and do:```
sudo apt-get install bcmwl-kernel-source
```After it's done, detach the ethernet cable, reboot and tell us how your wireless is working.

NOTE: Blacklisting ssb may not be prudent if your ethernet card is a Broadcom card using b44 and ssb. Please check:```
lspci -nn
```Is your ethernet card a Broadcom?

---

### Post by bkratz on 2011-06-01
@Chili,  The fix for that particular card is in the stickies in post #1

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by chili555 on 2011-06-01
> **bkratz said:**
> @Chili,  The fix for that particular card is in the stickies in post #1

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)What? You think I should read the stickies? Read someone else's post except yours?? Outrageous!!

Seriously, james17, forget everything I said above and hook up the ethernet and do:```
sudo apt-get install firmware-b43-lpphy-installer
```Reboot and tell us if your wireless is a beautiful thing.

Thanks, bkratz!

---

### Post by james17 on 2011-06-02
james@james-HP-Mini-110-1000:~$ sudo apt-get install firmware-b43-lpphy-installer
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer

?? hah

---

### Post by chili555 on 2011-06-02
Are you on line with an ethernet connection?

---

### Post by james17 on 2011-06-02
yea...

---

### Post by josephmills on 2011-06-02
the firmware is a 3rd party peice of software you need to go to synaptic package manager then go to Setting-->Repositories then make sure all are ticked see pic then  close out of everything and open your terminal and type in ```
sudo apt-get update && sudo apt-get upgrade 
``` then go back and do what chili555 says

---

### Post by james17 on 2011-06-02
ok ill go try that, thanks a lot :)

---

### Post by james17 on 2011-06-02
in the top right where the Wifi signal is it says 'No network connection' i make it drop down and it only has two options 
 
Wired Network 
    disconected
 
VPN Connections           >
 
 
 
thats it, nothing about connecting to wireless but the updates and all worked
 help?
thanks
james16

---

### Post by james17 on 2011-06-02
never mind guys, it work great, thanks a whole lot. now that i have wifi connection i can start learning about linux a lot easier

1000000000 gratz

---

### Post by sh4rkbyt3 on 2012-11-15
Not to hijack the thread but I wanted to thank you chili555 as this also resolved the connection problem on my HP Mini 110-1025DX.
Thank you so much :)!

---

### Post by sh4rkbyt3 on 2012-11-16
Chili, not sure what's happening but after I shut down my HP Mini it cannot now find wireless connection? What did I do wrong or what do I need to do?

I've blacklisted b43 as well as ssb? It worked last night fine but today after shutdown it won't connect?

---

### Post by chili555 on 2012-11-17
@sh4rkbyt3-

Please confirm which device you have:```
lspci -nn | grep 0280
```Also, if you, purely as an experiment, load b43 does your wireless work?```
sudo modprobe b43
```

---

