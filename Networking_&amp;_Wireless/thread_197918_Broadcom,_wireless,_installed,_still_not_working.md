---
title: "Broadcom, wireless, installed, still not working"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by blurredbrain on 2006-06-16
I've searched over the forums and haven't found anything like this.  I've installed the drivers for my broadcom wireless card (bcmwl5.inf), when I type ndiswrapper -l it says "driver present, hardware present"

The next stp is "ndiswrapper -m" which should turn on my wireless light.  it doesn't tell me anything, and the light doesn't turn on.  I can activate it in the NEtwork Manager, but it doesn't actually do anything.

Any help please.

I had this working in Breezy, but not in the newly installed Drake.

---

### Post by noname101 on 2006-06-16
Try sudo modprobe ndiswrapper. Also there may be another driver that its trying to use instead of ndiswrapper. So if sudo modprobe ndiswrapper doesn't work try this:
```
lsmod | grep bcm43xx
```
If it displays something then do this:
```

sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```
If thats the case then you should blacklist bcm43xx:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add at the bottom blacklist bcm43xx.
Also if you want ndiswrapper module to load at boot you'll have to do this:
```
sudo gedit /etc/modules
```
Add ndiswrapper to the end.

---

### Post by DarthMandeep on 2006-06-16
Did you type "sudo modprobe ndiswrapper" to load the ndiswrapper module into the kernel? This needs to be done before the card is usable.

If that works, then don't forget to add "ndiswrapper" to your /etc/modules file so that it gets loaded at startup.

Also, you need to blacklist the bcm43xx module before you can use ndiswrapper. To do that type "sudo rmmod bcm43xx" and add a "blacklist bcm43xx" line to the /etc/modprobe.d/blacklist file to prevent the bcm43xx driver from loading at startup.

Edit: Noname beat me to it.

---

### Post by blurredbrain on 2006-06-16
Yeah I've tried all that. 

bcm43xx is blacklisted and I've tried to modprobe ndiswrapper, it doesn't seem to do anything at all.  I'm pretty much stuck.  The stupid network manager is even telling me that my wireless connection is active.  But its not detecting anything at all (even when I'm running an unprotected wireless router right next to it.)

I was really surprised to have this issue because I had wireless running in

---

### Post by noname101 on 2006-06-16
What does iwconfig say?

---

### Post by blurredbrain on 2006-06-16
[QUOTE=noname101]What does iwconfig say?[/QUOTE]

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by noname101 on 2006-06-17
If sudo iwlist wlan0 scan shows your wireless router, then try this:
```
sudo iwconfig wlan0 essid myessid
sudo iwconfig wlan0 enc mywepkey
iwconfig
```
Now if iwconfig says your connected with your router then do this:
```
sudo dhclient wlan0
```

---

### Post by desiman on 2006-06-17
thanks guys, that solved my problem. i was really pissed why i upgraded ...not anymore  :-)

---

### Post by blurredbrain on 2006-06-17
iwlist wlan0 scan returns "no scan results" even though I know my wireless is up and running.

Edit:

When I run lsmod it shows me ndiswrapper running under usbcore, is this right?  This isn't a USB wireless device. Its an internal broadcom card that came in my Compaq Presario V2000.

---

