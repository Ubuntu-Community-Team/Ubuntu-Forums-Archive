---
title: "Broadcom STA Wireless on 9.10"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by JustinAlf on 2009-10-29
Installed the new 9.10 and no wireless.  Like most Dell laptop users, we were unable to use wireless when we made the upgrade.  There is a solution.  I did not come up with this, found it in the testing forums.

From Meborc:

> From USB, just browse to POOL->RESTRICTED->B->bcmwl.... and install the deb file from there

as i remember, you need to install 1 dependency first from the MAIN folder

USB has all the .deb files, so it is simple 

I already had the package installed.  Reinstalling it makes the wifi come alive!

Live CD should work just like the USB boot version.  Enjoy.

---

### Post by phamthanhnam on 2009-10-30
Thanks. It works now!

---

### Post by daniel.b.douglas on 2009-10-30
Hi there, I've been trying every solution I can find in forums but nothing, including the above, has helped so far.

My wireless was working in 9.04 after following the instructions at ([http://vladgh.com/2008/05/dell-wireless-1395-card-and-ubuntu-hardy-heron/](http://vladgh.com/2008/05/dell-wireless-1395-card-and-ubuntu-hardy-heron/)) but it was partially broken when I upgraded to 9.10beta and when I did a fresh install of 9.10 it was totally broken.

While using 9.10beta, I had to open a terminal and sudo rmmod b44, ssb, and ndiswrapper, then sudo modprobe ndiswrapper, ssb, b44, and it would work.  Writing a shall script to execute those six statements didn't work for some reason.

Now I am running 9.10, with the following info:
Computer: Dell Inspiron 1520
Wireless card: Dell 1395 wlan minicard

lspci -vnn output: 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Subsystem: Dell Device [1028:000b]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb

iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.

In the Administration > Hardware Drivers window, the Broadcom STA wireless driver has a green light and says "This driver is activated but not currently in use."

The WiFi light on the laptop is lit-up.

---

I've tried the above suggestion to reinstall the .deb, tried installing b43-fwcutter, as well as other suggestions from linux forums that I can't remember.  Any suggestions for what to try or more helpful information?

---

### Post by T-Keith on 2009-10-30
[http://ubuntuforums.org/showthread.php?t=1305860](http://ubuntuforums.org/showthread.php?t=1305860)

Same problem here with my Dell mini 9.  Kubuntu won't install on my desktop either.  9.10 is shaping out to be the worst Ubuntu release I've seen.

---

### Post by tim183 on 2009-10-30
this worked for me

THANKS!!!

---

### Post by daniel.b.douglas on 2009-10-30
The troubleshooting guide at [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) actually helped me to finally get the wireless to work! :)

---

### Post by Haythayt on 2009-11-01
This worked for me.. at least until i rebooted:

[http://ubuntuforums.org/showpost.php?p=8209076&postcount=6](http://ubuntuforums.org/showpost.php?p=8209076&postcount=6)

---

### Post by n411303 on 2009-11-01
I am having the same problem with Dell Mini 1011 netbook.  I got round it in Remix 9.04 by using Windows driver and Ndis but no joy for some reason with 9.10.  Also found I could see neighbours' networks but not my own even when ajacent to the router.  Then I read: 

"Why aren't channels 12 & 13 supported?  The driver only supports the default locale setting wich is ROW (Rest Of World) which does not include channels 12 or 13." 

in Broadcom's installation instructions for its driver.  Of couse my router was using channel 13!  Changing the router overcame this (not an aceptable solution).  However, after rebooting I had same problem reported above 

"the Broadcom STA wireless driver has a green light and says "This driver is activated but not currently in use.".

---

### Post by n411303 on 2009-11-01
Followed this to get NDIS working. Rebooted and I now have wireless.  Not sure if channels 12 & 13 are working with this Windows driver.  Life's too short.  

[http://vladgh.com/2008/05/dell-wireless-1395-card-and-ubuntu-hardy-heron/](http://vladgh.com/2008/05/dell-wireless-1395-card-and-ubuntu-hardy-heron/)

---

