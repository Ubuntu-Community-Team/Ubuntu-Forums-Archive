---
title: "Laptop to desktop shared internt connection help?"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by bnciwebdesign on 2009-08-17
My delima: I have dialup, because it's the only thing I can get in my area and that I can afford. My laptop had Ubuntu 9.04, and it works just fine for simple tasks.

My setup: I have a Windows XP Pro desktop downstairs with a wireless PCI card. It's sharing the dialup connection to the wireless so my laptop can get on the internet upstairs. 

What I need help on: Since my laptop decided it doesn't like being used all that much, I setup a desktop out of old and crappy parts using 7.10 (because my 8.04 and up disks were all damaged).

Is there a way I can just connect a crossover cable from the laptop to the desktop upstairs and share the wireless connection somehow?

Thanks:)

---

### Post by Iowan on 2009-08-17
Share from the desktop to the laptop to the other desktop to the internet?
Probably can be done: [https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless")

---

### Post by pdc124 on 2009-08-17
ive done  something similar connecting a small LAN to the www using an old laptop that was connected through a wireless connection

ie www----AP~~~~~~~wlan0:eth0--------LAN

I used shorewall as a frontend config to iptables.
try static IPs on  a different class C subnet ( eg 10.0.0.x) for' eth0 and the new machine if the winXP machine is using 192.168.x.x 

try sudo ifconfig -a on the laptop.

then  call wlan0 'net' and eth0 'loc'.

try a config that just passed everything from eth0 to wlan0 or 
use the 2 NIC shorewall config on the laptop ,

---

### Post by bnciwebdesign on 2009-08-17
> **Iowan said:**
> Share from the desktop to the laptop to the other desktop to the internet?
Probably can be done: [https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless")

XP desktop(192.168.0.1) -wireless to a laptop -wired to a desktop

if that makes sense

@pdc124 Let me see if this makes sense:

Shorewall is a program for my laptop? and I set up the wired IP as 10.x.x.x or something like that?

Lol, sorry, when it comes to  downloading stuff on the internet, I can spit out command line commands easy, but doing stuff on the machine itself is a whole different story

---

### Post by pdc124 on 2009-08-17
install shorewall and iptables on the  laptop in the middle. 
set up the 2 NIC shorewall system ( with static IP addresses for laptop-eth0 and newdesktop-eth0

or  setup shorewall to accept everything from loc(eth0) to net(wlan0) and vice versa

from memory the relevant configs are /etc/shorewall/interfaces and policy.

PS you can also put squid on the laptop which may speed up things a little

---

### Post by bnciwebdesign on 2009-08-17
Eh...It works fine if I remote into the XP one downstairs, but other ppl use the computer too, and my laptop kinda needs a new mobo, lol I'm just over using it till I can afford a new one

---

