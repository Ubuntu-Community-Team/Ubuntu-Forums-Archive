---
title: "Update shot all my internets!"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by mrhelp37 on 2010-02-22
Okay, so recently I updated from Jaunty Jackalope to Karmic Koala, and when I finished the upgrade I found that my wireless has been disabled. I never had a problem with it before the update. I can't find wireless networks at all. So I assumed that at some point during all the update my wireless card broke, so I pulled a USB wireless stick out of the closet.
The stick is a Lynksys Compact Wireless-G network adapter...with speed boost...wonderful. I figured I could attach it and find drivers for it online when I plugged in an ethernet cable to my laptop. The only problem is the computer won't connect even with a direct Ethernet connection. So now I can't get online to download drivers for my new wireless stick or my internal one that might still be working.

So is there any way I could un-disable my wireless or even get my ethernet to work again? I already tried re-installing Karmic Koala and it didn't help.

Thanks for any help I might receive.


The laptop is a Dell Inspiron E1505 with a Broadcom Dell Wireless 1390 WLAN Card.

---

### Post by mrhelp37 on 2010-02-22
bumpity.

---

### Post by northd_tech on 2010-02-22
Can you run the following commands in a terminal and post the results here so that we can see what your hardware is doing?

```
lspci 

lsusb

lsmod

uname -a

cat /etc/modules

cat /etc/modules.conf

sudo lshw -C network

ifconfig

iwconfig 
 
sudo iwlist scan 
 
nm-tool
```

You might want to save that information to a USB stick with a text editor (like Kate or gedit)- there will be a lot.

---

