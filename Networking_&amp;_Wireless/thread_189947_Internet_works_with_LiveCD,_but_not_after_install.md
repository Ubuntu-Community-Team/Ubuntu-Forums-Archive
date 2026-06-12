---
title: "Internet works with LiveCD, but not after install"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by hektisk on 2006-06-05
Hello,

After some contemplation, I decided yesterday to give linux a try on one of my machines.  After comparing some distributions, I decided to try ubuntu.  I made a LiveCD and booted up, and it looked wonderful.  I clicked on a few things and browsed a few menus, and browsed the net for a minute or two.  Everything looked and worked great, so I went for the full install.  The install went smoothly, but now I can't use the internet (I'm on another machine now).  I checked the settings, and everything looked okay, eth0 was on, etc.  I tried the liveCD again and the internet again worked perfectly, so I decided to compare the settings for eth0 on the liveCD and the full install: they appeared identical.  So now I'm quite perplexed.  

For some background, I have a cable modem which connects to a wireless router and I have wireless connectivity for my laptop (which I'm using now), my sister's computer in her room, etc, but the computer with Linux is hooked up directly to the router - that is, it's not wireless or anything like that.  

Any ideas on why the internet would work fine under LiveCD but not after its fully installed?  I tried reinstalling a few times but nothing helped.

Thanks!

---

### Post by hektisk on 2006-06-05
I looked at some other threads here (I should have done that before I posted; sorry) and will try powering off the modem and computer for a few minutes and hoping that it works when I turn it back on.  Have to tell the rest of the family that they'll have no internet for a minute I guess, but they'll live ;>

---

### Post by hektisk on 2006-06-05
I tried unplugging my modem.  When I booted my computer back up I clicked on the updater on the top right of the screen and it downloaded some packages, but nothing else (gaim, http) worked.  After the packages installed I clicked 'check updates' and that didn't work either.  It's like I had internet for a fraction of a second, then it went away.

---

### Post by hektisk on 2006-06-05
Here's the ifconfig (typed out, not c&p):

eth0  Link encap: Ethernet HWaddr 00:80:AD:88:3C:40
        inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0
        inet6 addr: fe80::280:adff:fe88:3c40/64 Scope:Link
        UP BROADCAST MULTICAST  MTU:1500 Metric:1
        RX packets:59 errors:184 dropped:0 overruns:0 frame:0
        TX packets:23 errors:1 dropped:0 overruns:1 carrier:1
        collisions:0 txqueuelen:1000
        RX bytes:9354 (9.1 KiB)  TX bytes:2770 (2.7 KiB)
        Interrupt:12 Base address:0xd800

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:81 errors:0 dropped:0 overruns:0 frame:0
        TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:7816 (7.6 KiB) TX bytes:7816 (7.6 KiB)


As far as network settings go, it says that interface eth0 is active.  Under 'properties' DHCP is checked, DNS 68.87.71.226/68.87.73.242 search domain hsd1.ma.comcast.net (it got that automatically; I didn't enter it in)
 under hosts: 
ff00::0 ip-mcastprefix
127.0.0.1 localhost adam-desktop
fe00::0 ip6-localnet
ff02::2 ip6-allrouters
ff02::1 ip6-allnodes
::1 ip6-localhost ip6-loopback
127.0.1.1 adam-desktop
ff02::3 ip6-allhosts

Not sure if any of that helps...

---

### Post by hektisk on 2006-06-05
Ifconfig from LiveCD version:

eth0      Link encap:Ethernet  HWaddr 00:80:AD:88:3C:40
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fe88:3c40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:546255 (533.4 KiB)  TX bytes:72646 (70.9 KiB)
          Interrupt:12 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)



As far as I can tell, the only real difference is the eth0 errors: 184 RX errors and 1 TX error under the fully installed version, 0 errors from LiveCD.

---

### Post by hektisk on 2006-06-05
Ah, changed cards and fixed it.  Didn't realize I had a Davidcom; otherwise [this]("http://ubuntuforums.org/showthread.php?t=186430") would have come in handy.  Oops :)

---

