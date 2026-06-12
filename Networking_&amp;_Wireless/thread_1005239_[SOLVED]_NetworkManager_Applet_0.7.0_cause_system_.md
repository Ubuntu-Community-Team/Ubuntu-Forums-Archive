---
title: "[SOLVED] NetworkManager Applet 0.7.0 cause system to freeze"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Ant68 on 2008-12-08
Hello,
I have done a fresh set up of ubuntu 8.10. Everything worked fine (i.e. rebooted successfully at each steps - recreated the bug i.e. did two rfesh install of 8.10 to identify the issue) until I set up my WIFI key with NetworkManager Applet 0.7.0 (I tried several times and had the system to freeze every time until I managed to get the key to work).

Now that the WIFI is configured correctly (I had it to work once - the session I was successful setting it up), every time I reboot, the system freezes when Gnome starts and the NetworkManager Applet 0.7.0 tries to pick up the WIFI.

I have a desktop with Realtek RTL 8185 wireless card.

hemona@hemona-desktop:~$ lspci
...
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

I suspect a bug with NetworkManager Applet 0.7.0.

Could you please help me?

1 - Rollback to previous stable status
2 - fix the issue with NetworkManager Applet 0.7.0

thanks

---

### Post by andreasis on 2008-12-08
what driver are you using?

[EDIT] I am guessing that you are using the driver that comes with ubuntu.  

Network Manager is notorious for causing problems where there are none.  Have you given Wicd [http://wicd.sourceforge.net](http://wicd.sourceforge.net) a try?  I find it works exponentially better than the gnome network manager.

Installing wicd is easy:

in a terminal:

```
deb http://apt.wicd.net intrepid extras
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

---

### Post by Ant68 on 2008-12-08
hi,
I did not set up any driver. I have only configured NetworkManager Applet 0.7.0. 

NetworkManager Applet 0.7.0 was showing the list of available wireless network and I put in the WEP Key. I tried a few times getting a freeze every time until it got eventually through and it now freeze when I am logged in Gnome (I suppose the NetworkManager Applet 0.7.0 starts automatically and then freezes).

---

### Post by andreasis on 2008-12-08
If you would like to keep on trying with network manager (although I highly recommend wicd) then it would be useful to look at/post the syslog/userlog located in /var/log/ to see if anything shows up in there.

[EDIT] I will return in about 18 hours to check up on your progress : )

---

### Post by Ant68 on 2008-12-08
I have added the 

deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

to 

/etc/apt/sources.list

then when I run:
wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

I get:
**gpg: no valid OpenPGP data found**

What should I do next? (sorry I am a newbie)...

---

### Post by Ant68 on 2008-12-09
I eventually managed to set it up but it causes the same freeze issue when I configure the WEP key.

I am going to set up the rtl 8185 driver.

---

### Post by Ant68 on 2008-12-12
I resolved the problem.

1 - to remove the connection causing the freeze, I run nm-connection-editor
2 - I set up the windows drive using the graphic interface that can be set up in the application section. It is called "Window Wirelss drivers". it then worked fine.

---

