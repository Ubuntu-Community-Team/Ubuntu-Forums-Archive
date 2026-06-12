---
title: "Internet/networking connection has randomly stopped working! (wired)"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by cheway on 2011-01-29
Hi guys, bit of a strange one...

I'm running a minimal command line Ubuntu 10.04 (Lucid) + Fluxbox whose network connection has worked flawlessly for months; it worked straight out of the box when I did the installation. The LAN is an r8169 job.

I've tried an alternative computer, and the cable is fine. Have also tried a live CD just to check the hardware itself; also fine.

Have also tried removing module with "modprobe -r r8169" and re-adding it with "modprobe r8169", but that didn't work.

Everything looks like it should in "lspci". Doing an "ifconfig" doesn't display any IP addresses. Also cannot access my router page, so it's not just my Internet. Other machines on my network are working as they should.

Any help/pointers would be very much appreciated!

---

### Post by cheway on 2011-01-31
Any ideas guys? Really don't want to have to reinstall my system, just got it the way I like it!!

---

### Post by chili555 on 2011-01-31
Are you using some kind of Network Manager or did you configure with /etc/network/interfaces? What is the result if you do:```
sudo ifconfig eth0 down && sudo ifconfig eth0 up
sudo dhclient eth0
```The exact replies, even if they're blank, tell us something. Don't be like one of my colleagues whose reply was, "It didn't work."

Is this a dual-boot installation with Windows? Please see: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by cheway on 2011-01-31
Firstly, thank you for the reply.

Secondly, that fixed it! You're a legend. I had the words "up" and "down" buried somewhere in the back of my mind, but I would never have thought to use them here... seems obvious now.

To answer your question, I never used a network manager or did any kind of configuration - it just worked straight away (did a command line install with no issues).

The result of those commands (apart from fixing it :)) was...

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/40:61:86:91:c7:48
Sending on   LPF/eth0/40:61:86:91:c7:48
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.80.129 from 192.168.80.1
DHCPREQUEST of 192.168.80.129 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.80.129 from 192.168.80.1
bound to 192.168.80.129 -- renewal in 39497 seconds.

```

No, no Windows at all here.

May I thank you for sorting this out for me, I'm delighted it's working again, and please accept my apologies for the initial vague description... I just had no idea how else to describe it having never had a problem before!

Do you think my lack of network manager caused this problem in the first place?

---

### Post by chili555 on 2011-01-31
> Do you think my lack of network manager caused this problem in the first place?No. Generally, however, the directive to start automagically is given in /etc/network/interfaces. It ought to look something like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```The eth0 lines tell the system to start the interface automatically on boot and connect with DHCP. If these lines are present and it still doesn't start, we can take other measures.

---

### Post by cheway on 2011-02-06
I am having to run those commands every time I start up or network doesn't work.

My /etc/network/interfaces looks exactly as you have said.

I think I can work out how to run commands at startup, but how does one do it when sudo access is required? I don't want to have to type in a password every time.

Thanks for any and all help.

---

### Post by chili555 on 2011-02-06
It ought to start and run automagically; however, for whatever reason, it's not. Let's try to nudge it:```
sudo gedit /etc/rc.local
```Add these lines right above 'exit 0':```
ifdown eth0
sleep 5
ifup eth0
```Proofread, save and close gedit. Please let us know the outcome.

---

### Post by cheway on 2011-03-19
Apologies for the delay in my reply.

Unfortunately that did not work, but I have installed wicd, added it to run in my startup file, and that allows me to connect using the icon in the system tray.

Perfectly happy with this solution, but I can't work out how to connect automatically on startup, always have to connect manually. No biggie though.

Thank you very much for your help.

Cheers,
Matt.

---

