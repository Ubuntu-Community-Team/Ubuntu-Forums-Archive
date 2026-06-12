---
title: "Wireless Icon Missing"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by zanknits on 2010-05-14
This is a repost from the Absolute Beginner's Forum - original thread is [here]("http://ubuntuforums.org/showthread.php?t=1482604").

I upgraded to lucid, and now my wireless icon is missing. I have the notification area and indicator panel up. When I run:
> nm-applet --sm-disable
I get:
> An instance of nm-applet is already running.

** (nm-applet:2186): WARNING **: <WARN> constructor(): Couldn't initialize the D-Bus manager.

ifconfig pulls up:
> eth0 Link encap:Ethernet HWaddr 00:1e:ec:f9:5b:e7 
inet addr:192.168.100.200 Bcast:192.168.100.255 Mask:255.255.255.0
inet6 addr: fe80::21e:ecff:fef9:5be7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:9652 errors:0 dropped:0 overruns:0 frame:0
TX packets:6797 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:9817767 (9.8 MB) TX bytes:1095450 (1.0 MB)
Interrupt:29 Base address:0xa000 

eth1 Link encap:Ethernet HWaddr 00:21:00:93:c5:9d 
inet6 addr: fe80::221:ff:fe93:c59d/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:960 (960.0 B) TX bytes:960 (960.0 B)

And iwconfig:
> lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

My wireless *did* work with hardy/jaunty/intrepid. Any ideas?

Also, this isn't a big issue but it's kinda annoying: when I unplug my ethernet cable then plug it back in, I have to reboot for my computer to recongize it's connected. Is that normal, or can I fix that?

Thank you so much!

---

### Post by zanknits on 2010-05-14
bump

---

### Post by McRat on 2010-05-14
I could not get it to work with U64.  When I switched to U32 10.04, everything worked as advertised.

---

### Post by zanknits on 2010-05-14
I found [this post]("http://ubuntuforums.org/showthread.php?t=1480419&page=2") that has a very similar issue. I'm going to follow jschille's post and see if that fixes it. (derp, I didn't find this post when I googled earlier because I didn't realize the wireless icon was called the "network manager"). I'll report back after a reboot!

---

### Post by zanknits on 2010-05-14
It worked! Here's what I did, step by step:
> gksudo gedit /etc/NetworkManager/nm-system-settings.conf

And changed "managed=false" to "true" (or vice-versa, can't remember)

---

### Post by d3shi on 2010-06-15
I'm new ubuntu user but I accidentally found a solution on the Wireless Network icon disappearing in the panel.
Just find "**libsnmp-base**" package in System->Administration->Synaptic Package Manager and uninstall it!
"libsnmp-base" is a package which is downloaded and somehow messes up the wireless network settings. It happened after i updated mu Ubuntu 10.04 lucid.
I hope it will work for You cuz it worked for me.

---

### Post by Coder68 on 2010-06-18
Neither of these worked for me. My wireless works, just no icon in the tray.  When I tried from the CD and installed the restricted  driver, not only did it work but the icon was there. 

Any other ideas?

Dell 15n, 10.0432bit.

Coder68

---

### Post by clairvoyant_rj on 2010-08-15
Thanks for posting your solution [zanknits]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=750168"), it worked for me.

---

### Post by dwaindibbley on 2010-10-22
Yes, thanks zanknits, it worked for me also on 10.10 Maverick Netbook edition. I had been playing with PPPoE and it disappeared somehow.

---

