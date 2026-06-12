---
title: "WPA/Wireless issues since Lucid Upgrade"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by kwiksand on 2010-05-17
Hey guys, 

I've been running Lucid since Alpha/Beta on 3 laptops:
- Dell XPS 1530 (Intel 4965)
- Dell Vostro 1700  (Intel 3945)
- Apple Macbook 5.4 Unibody (Broadcom BCM4322)

All three machines ran Karmic/9.10 before without any issues, but since the upgrade, take a long while to connect to my WPA networks at home and at the office (I've tried with a bunch of different auth mechanisms and channels).  

All behave in exactly the same way, behave perfectly once connected, but getting the initial connection is troublesome and can take anywhere from 30 seconds to 10 minutes.

I've seen numerous bug reports and forum threads regarding similar issues, but most seem to not be able to connect at all.  Is there something that has changed substantially in Lucid that wasn't present in previous versions that are causing this issue (Wireless is one thing thats been perfect on my machine(s) for several years).

---

### Post by BoneKracker on 2010-05-17
I dont' know, but the kernel wireless architecture has been evolving.  My wireless (ralink) broke when I upgraded to 2.6.33.  This could be a related issue.

I'd suggest you Google for information about your wireless chipset working under kernel versions 2.6.33 and 2.6.34.  You might need an updated driver that's not yet available in the kernel.

---

### Post by kwiksand on 2010-05-17
Thanks for your reply BoneKracker,

Strangely enough, all my machines are still running 2.6.32-x, as yet I've not seen the option in apt to update them, perhaps I'm being held back by something else.

I've done a bit of googling (and searching on these forums), checking the three chipset's, but none showed any signs of similar behaviour.

It just seems strange that all three machines were working fine with Karmic, and all exhibit the same problem after upgrading to Lucid. (I dont recall there being a major kernel version change either?)

---

### Post by BoneKracker on 2010-05-17
> **kwiksand said:**
> Thanks for your reply BoneKracker,

Strangely enough, all my machines are still running 2.6.32-x, as yet I've not seen the option in apt to update them, perhaps I'm being held back by something else.

I've done a bit of googling (and searching on these forums), checking the three chipset's, but none showed any signs of similar behaviour.

It just seems strange that all three machines were working fine with Karmic, and all exhibit the same problem after upgrading to Lucid. (I dont recall there being a major kernel version change either?)

Oh.  I don't run Ubuntu.  I thought you guys went to 2.6.34 with this release.  My bad.  

And you have new problems with three different wireless adapters?  Must be something else to do with the update.

---

### Post by kwiksand on 2010-05-17
Yea, they all exhibit the same or similar behavior too, on different routers as well.

- All three checked on a Netgear WGN2000 at home, and LinksysWRT54 (both WPA2)
- The Macbook additionally uses the Netgear WAPxx, Draytek 2820VG and Airport Extreme N+ at the office (Don't ask, we've got wireless networks all over the place, signal is strong and 'usually' trouble free though).

The only constant seems to be the move to Lucid

---

### Post by kwiksand on 2010-05-18
Nobody's having the same issues??

It seems odd, considering the wide range of hardware I'm noticing the issue with on both the client and AP side!

---

### Post by KilianValkhof on 2010-05-18
Having the same issues here.

---

### Post by rmcd on 2010-05-18
I can't connect at all to wpa2 since upgrading. WPA Enterprise works fine. (Update: I am failing to connect with WPA/TKIP, which I believe is WPA1, not WPA2.)

I have a Lenovo X200s, Intel 5100 chipset, iwlagn driver and the exact same problem occurs with my wife's Lenovo R61 (3945ABG Intel).

Symptom is that it keeps asking me for the passphrase. Connection was flawless under 9.10.

I get this in wpa_supplicant.log on the X200s, with the current router I'm rying to connect to, I get this, repeated many times:

May 18 08:45:24 fin8344m1 avahi-daemon[26719]: last message repeated 17 times
May 18 08:45:24 fin8344m1 kernel: [215240.380069] wlan0: authenticated
May 18 08:45:24 fin8344m1 kernel: [215240.380097] wlan0: associate with AP 00:1d:73:b1:2c:ae (try 1)
May 18 08:45:24 fin8344m1 avahi-daemon[26719]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)
May 18 08:45:24 fin8344m1 avahi-daemon[26719]: last message repeated 142 times
May 18 08:45:24 fin8344m1 kernel: [215240.576066] wlan0: associate with AP 00:1d:73:b1:2c:ae (try 2)
May 18 08:45:24 fin8344m1 avahi-daemon[26719]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)
May 18 08:45:24 fin8344m1 avahi-daemon[26719]: last message repeated 145 times
May 18 08:45:24 fin8344m1 kernel: [215240.776044] wlan0: associate with AP 00:1d:73:b1:2c:ae (try 3)
May 18 08:45:24 fin8344m1 avahi-daemon[26719]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)
May 18 08:45:25 fin8344m1 avahi-daemon[26719]: last message repeated 145 times
May 18 08:45:25 fin8344m1 kernel: [215240.976043] wlan0: association with AP 00:1d:73:b1:2c:ae timed out
May 18 08:45:25 fin8344m1 avahi-daemon[26719]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)

---

### Post by stmiller on 2010-05-28
I'm seeing the same thing. Keeps asking for WPA2 Personal passphrase. Bah!

Using 2.6.33 kernel from Ubuntu kernel PPA.

RaLink RT2860

Edit: This post works to compile your own module:

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by kwiksand on 2010-05-29
Hey guys,

Check out: [https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777)

Specifically Bug #35, seems to have helped the problem a bit.

---

### Post by gecko55 on 2011-11-06
I seem to have run into the same issue - i.e endless loop of WPA authentication requests but no successful connection. 

Thought it was a driver issue and tried to follow the solutions here:

[http://ubuntuforums.org/showthread.php?t=1434630]("http://ubuntuforums.org/showthread.php?t=1434630")

and here:

[http://ubuntuforums.org/showthread.php?t=1465779]("http://ubuntuforums.org/showthread.php?t=1465779")

also looked at the bug report here:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777")

But the solutions seemed far from certain (e.g. #35) and too intimidating for neophyte like me.

I have attached a text file that chronicles by trials and tribulations.

Computer is an Acer Extensa 4420 running Ubuntu 10.04 LTS and I am trying to get a DWA-125 USB Wireless N dongle working, for better connection speed.

Hope someone is still monitoring this thread. I am trying to like Linux but its not easy.

---

