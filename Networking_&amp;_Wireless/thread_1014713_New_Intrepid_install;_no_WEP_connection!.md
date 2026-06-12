---
title: "New Intrepid install; no WEP connection!"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by SamSmith17 on 2008-12-18
Hi All, 

I'm a bit of a noob here, and just installed a fresh copy of Intrepid on my hp pavilion zd7000. 

It is using a Broadcom BCM94301MPL wireless card, and the restricted drivers dialogue installed the "B43 Legacy Wireless Driver". The problem is that I cannot connect to "Open" WEP encrypted networks - or at least the two that I have tried. 

I don't own the routers, so I cannot change the settings, but I know them to be using a Motorola SBG900 modem/router. My friend is also not able to connect with hardy 8.04 on his computer, which is also using a broadcom card. The OS X laptops and the Windows computers have no problems connecting... so I am a bit baffled. Does anyone have any ideas? 

Here is dmesg |tail or so:
```

sam@sam-laptop:~$ dmesg |tail
[ 2372.940078] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 1
[ 2372.941720] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 1
[ 2373.140030] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 2
[ 2373.341274] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 3
[ 2373.540017] wlan0: direct probe to AP 00:14:a5:0d:98:21 timed out
[ 2383.716074] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 1
[ 2383.716766] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 1
[ 2383.916038] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 2
[ 2384.116035] wlan0: direct probe to AP 00:14:a5:0d:98:21 try 3
[ 2384.316031] wlan0: direct probe to AP 00:14:a5:0d:98:21 timed out

```

Is there any way to keep this from timing out? I appreciate any help. Thank you!
Sam

---

### Post by MaddMatt on 2008-12-18
I'm having the same problem - even after trying this:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
from [this forum]("http://ubuntuforums.org/showthread.php?t=995771&highlight=wireless+timeout"). 

Any ideas? Mine hasn't worked on the last 3 WEP networks I've tried to connect to, and I'm using the Broadcom driver on my MBP. 

M

---

### Post by MoKraak on 2008-12-19
The wireless networking has worked perfectly on this Fujitsu laptop with Gutsy, Hardy and Intrepid.  The hard drive crapped out so I did a fresh Intrepid install yesterday.  The wireless worked perfectly from the get-go and I used it to perform the first large update.

After the update, my WEP password does not work.  It will not connect even when WEP is turned off at the router and keeps asking me for the WEP password either way.

It is the same password that I have used for years so it's NOT the wrong password.  It's NOT the router because my other Ubuntu and Windows boxes hook right up to it.

I have read hundreds of posts today to no avail.  They keep going off on tangents about drivers.  Since wireless has worked perfectly with the same router for a long time, it should have nothing to do with drivers.  More likely, something was changed during the update that has caused this to happen.

lshw -C network info shows Prism 2.5 Wavelan chipset.  I wonder if that driver was changed during the update?

Any ideas?

---

### Post by MaddMatt on 2008-12-19
Yeah, can you list what you have in /var/log/dpkg.log ? This should show what was upgraded last, and maybe we can figure out via process of elimination.

---

### Post by MaddMatt on 2008-12-25
=[bump]

---

### Post by dav9000 on 2008-12-25
Hi. I have had the same problem as you I think. After yesterday updates, this morning network-manager wasn't able to connect through wlan. Ethernet was ok but it was impossible to connect on wlan0.

So... I installed WICD, a connections manager similar to NETWORK MANAGER. Check install instructions in [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) and you are done.

Goodbye nm, hello wicd.

Hope this solves your problems.

---

### Post by zrs_12 on 2008-12-25
I have a Dell Inspiron 600m with a Broadcom wireless card.  The drivers came with the installation of Intrepid, but the proprietary firmware did not.  See [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to check if you need this firmware.

---

