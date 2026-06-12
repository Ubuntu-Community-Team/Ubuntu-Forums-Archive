---
title: "Ralink wifi usb will not connect"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by peter35 on 2009-10-20
I have just installed *karmic* in the hope of getting a new Ralink USB adapter up and running. However, no such luck. I tried to avoid buying Ralink as it always given me problems in the past. I am now tearing my hair out, as there is little else on the market. Any, here is some info to start with:

lsusb: ID 148f: 3070
iwconfig reports wlan0
lsmod :
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb

However, Network tools reports that wlan0 does not exist when I attempt to configure it.
The green led on the usb is flashing all the time, if that means anything.
I don't know where to go from here. Help would be welcome

---

### Post by pdc on 2009-10-22
would any of this be any use?

[http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)

---

### Post by Cuba71 on 2009-10-22
You may find the right driver [here]("http://eng.ralinktech.com.tw/support.php?s=2")

---

### Post by peter35 on 2009-10-23
Thanks. Tried to follow the guide in wiki, but it seems to fails at step 3.
"Couldn't find any package whose name or description matched "linux-image-2.6.30-bpo.1-generic"
also: Unpacking firmware-ralink (from .../firmware-ralink_0.17~bpo50+1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/firmware-ralink_0.17~bpo50+1_all.deb (--unpack):
 trying to overwrite '/lib/firmware/rt2561s.bin', which is also in package linux-firmware 0:1.21
Errors were encountered while processing:
 /var/cache/apt/archives/firmware-ralink_0.17~bpo50+1_all.deb

I don't understand wha'ts going on, as.although I've been using Linux for several years, this is my first encounter with Debian-based distro. Trying Ubuntu because I thought it would make life easier, Hmmm. 
Will try the driver from the Ralink site in the next post #3

---

### Post by peter35 on 2009-10-23
Yup, Lokos great. I think I found it before whilst fumbling for a solution. Unfortunately, it won't compile. Loads of warnings such as "the frame size of 1600 bytes is larger than 1024 bytes", but critically some errors which stop the Make.

In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/peter/Software/Ralink/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;

Ditto for members named stop, xmit, do_ioctl, get_stats, validate_addr

So, no luck there. Some fans say Ralink is well supported in Linux - I think I disagree.

---

