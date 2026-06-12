---
title: "Good reason to leave linux - WPA, wirelss"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by tjpren on 2009-10-01
Hello,forum,

I made a post (twice) in the last day to which I received no help -thanks.

I had my wireless working (WG111-V2 USB stick) using ndiswrapper, under 8.04.  I wanted to up my security, so changed to WPA-psk.  My windows PC's connected with no problem using WPA-PSK and TKIP - except my Ubuntu.

The WG111 USB stick can work with WPA, as my dual boot (windows partition) connects to the router without issue.

I've tried numerous permutations to /etc/network/interfaces, and /etc/wpa-supplicant.conf without success.

It's this basic sort of issue that separates linux from Windows I'm afraid.

Unfortunately my Ubuntu is off the air, save for some help ?

---

### Post by goodvikings on 2009-10-01
> **tjpren said:**
> 
I made a post (twice) in the last day to which I received no help -thanks.


np.

---

### Post by bruno9779 on 2009-10-01
With this attitude you are not very likely to get any help.

have you googled for your issue? apparently not

[http://ubuntuforums.org/showthread.php?t=632651](http://ubuntuforums.org/showthread.php?t=632651)

---

### Post by tjpren on 2009-10-01
Thnakyou bruno9779, and goodvikings,

Yes, OK, probably a bit rude - I'm frustrated by my lack of ability in getting the wireless internet working.  No execuse, I know.

In actual fact, I have been googling and come through several 360's but still failing to get a connection.

My last feat was to try off the live CD.  It actually connects natively using, with WPA, but is flakey and drops out which was why I went to the ndiswrapper originally on the installed version.

Part of the frustration also, is that I love linux, but hate it when something which is so fundamental is so difficult to get right (particularly when XP and vista connect with amazing grace).

If the live CD can connect with WPA, then there must be some fundamental issue with my current setup - just can't pinpoint it.

Any help appreciated

---

### Post by tjpren on 2009-10-04
hello forum,

My Ubuntu is now back on-line.

I tried the LiveCD of 9.04, and to my surprise it recognized the WG111 out of the box, and connected with WPA.  I left it run for a few hours, and it remained connected.

I backed up all my files, and proceeded with a new install of 9.04.

All went smooth, and have started restoring my back-ups.

This is more like it - out of the box, up and running.  No code fixes, or configuration files.

I'm not even going to complain that the WG111 doesn't have a blue light.

I'm thinking of not bedding my 9.04 down, but wait to see what 9.10 is like, and if the liveCD works OK with the WG111, upgrade immediately.

---

### Post by SuperSonic4 on 2009-10-04
Try the beta on a live CD ;)

I had the same problem you did until ath5k came in

---

