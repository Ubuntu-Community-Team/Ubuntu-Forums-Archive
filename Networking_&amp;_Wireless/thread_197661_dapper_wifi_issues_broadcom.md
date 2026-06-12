---
title: "dapper wifi issues broadcom"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by kcallstar7 on 2006-06-16
please please give me some way to get my dv4000 wifi broadcom working... im to provide you with what i got so far ive tried alot so here it is

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl5.sys      invalid driver!

 iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

and my wifi light is on ... on my laptop so i dont know what to do at this point there has to be a way to install this and get it working... via wine ... ndiswrapper...  ive google and wiki'd and search but this might be the best way for me to get some solid input on my situation... i hold everyone on these forums in the highest respect because this forum community is the best...

What was easy is now gone... and what shall come in truth is freedom...
unix linux...  unbuntu (W-A.D) (windows after dealth)

---

### Post by ????? on 2006-06-16
I have a dv1000 and a Broadcom 4318..


try this:

```
sudo ndiswrapper -e bcmwl5.sys
sudo iwconfig eth1 essid youressidhere
```

Also it doesn't seem to work (bcm43xx and ndis) on the new kernel that you can get via update manager..

---

### Post by noname101 on 2006-06-16
You may need to do this too:
```
sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```
If that works then edit /etc/modprobe.d/blacklist and add blacklist bcm43xx to the end:
```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by trubblemaker on 2006-06-18
yeah I second that also check the howto in my signature to get it going.

hear's the supper easy script post I found
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

