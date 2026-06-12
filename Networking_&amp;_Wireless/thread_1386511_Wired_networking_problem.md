---
title: "Wired networking problem"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by daboo911 on 2010-01-20
Hello all, newbie here.

I have a fresh install of Kubuntu on an old Dell Dimension 2400 that seems to be working perfectly except for the network connection.  I have a wired network connection to a linksys router connected to a cable modem.  This connection works on other devices.  

I've searched google and these forums, but I haven't found anything that would work.  

```
ifconfig
eth0
Link encap:Ethernet    HWaddr 00:0b:db:b6:cf:09
inet6 addr: fe80::20b:dbff:feb6:cf09/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:352 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carier:0
collisions:0 txqueuelen:1000
RX bytes:89867 (89.8 KB)   TX bytes:3952 (3.9 KB)
Interrupt:17
```
It also outputs the local loopback, but since I'm copying these by hand (no thumbdrive) I'll leave that out, unless it's relevant.  

Relevant lspci:
```
lspci -v
Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
Subsystem: Dell Device 8127
Flags: bus master, fast devsel, latency 64, IRQ 17
Memory at fe9ee000 (32-bit, nonprefetchable) [size=8k]
Expansion ROM at fe920000 [disabled] [size=16k]
Capabilities: <access denied>
Kernel driver in use: b44
Kernel modules: b44
```

Any help would be greatly appreciated, thanks in advance

---

### Post by Iowan on 2010-01-20
I'd say post **sudo lshw -C network**, but you already mentioned limitations. I presume you're using Kubuntu's version of Network Manager (I've never used Kubuntu). You might try manually running **dhclient** - I suspect it'll give the "no offers received - sleeping" response.

---

### Post by daboo911 on 2010-01-20
```
$ dhclient
Internet Systems Consortium DHCP ClientV3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /car/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted
``````
sudo lshw -C network
*-network
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 9
bus info: pci@0000:01:09.0
logical name: eth0
version: 01
serial: 00:0b:db:b6:cf:09
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:17 memory:fe9ee000-fe9effff memory:fe920000-fe923fff(prefetchable)
```

Hope this helps, thanks

---

### Post by Iowan on 2010-01-20
Sorry - try it as:```
sudo dhclient eth0
```

---

### Post by daboo911 on 2010-01-20
Haha, sorry.  I should have emphasized newbie.

```

$ sudo dhclient eth0
Listening on LPF/eth0/00:0b:db:b6:cf:09
Sending on LPF/eth0/00:0b:db:b6:cf:09
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 8
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 14
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 18
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 18
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I can't say I know what any of this means, but thanks

---

### Post by daboo911 on 2010-01-20
Not to sound too desperate, but I can't really do anything on this kubuntu box without an internet connection.  I'm definitely willing to transcribe any output in full if it will help.  I just don't know what the next step would be.
Thanks,
Jen

---

### Post by jpullen on 2010-01-21
RX packets:352 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carier:0

It looks like you're dropping a lot of packets.

I'm assuming you're running Kubuntu 9.10.  If you aren't then please post otherwise. You shouldn't have to do anything on the command line to make this work.  The broadcast address used to do the DHCP discover looks weird to me, indicating a bad manual configuration.  You can trust Kubuntu's auto config to handle wired network setup most of the time.

Step 1: Go to System Settings -> Network Settings
Step 2: Under Network Connections go to the Wired tab.  This should be empty.  If it isn't then delete all entries here.
Step 3: Click the network manager icon in the system tray at the bottom of the screen.  You should see an interface called "Auto eth0".  It should connect automatically if you have a DHCP server set up in your network.  You can click on "Auto eth0" to force a reconnect.

That's all you should have to do if you have a normal home / corporate setup.  If this doesn't do it then I'd investigate the following:
a) Turn off all wireless interfaces while you're troubleshooting (if applicable).
b) Does this computer support 10/100?  Be sure you aren't trying to connect a 10 Mbps interface to a 100 Mbps-only switch/hub/gateway.  Check your gateway settings to ensure that it supports auto-switching and has that enabled -- this is obviously dependent on your specific gateway.
c) Check/replace your ethernet cable
d) Try with another PC if possible to ensure that it can connect.  Check the IP information on the other PC (Windows: ipconfig, Linux: ifconfig) to see what IP address, netmask, and gateway it's getting.  The PC you're trying to set up should have the same netmask and gateway, and the IP address should be the same in the 1st and 2nd quads at least.

If none of this works then please post a response with a detailed description of your hardware configuration.  For hardware config you can type "lspci -v" on a command line.

---

### Post by daboo911 on 2010-01-21
Yes, I'm running 9.10, sorry for not mentioning that.  I haven't messed with the configuration manually at all, except for the attempts to make it work (all changes were reverted when I realized they didn't work).

The Wired tab in Network Settings is empty.  Clicking 'Auto eth0' does not connect.  It displays 'Activating...' for a minute or so underneath, which eventually disappears when it can't connect.

This computer does support 10/100.  The ethernet cable works on the Powerbook I'm posting this from.  

Ethernet controller:
```
lspci -v
Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
Subsystem: Dell Device 8127
Flags: bus master, fast devsel, latency 64, IRQ 17
Memory at fe9ee000 (32-bit, nonprefetchable) [size=8k]
Expansion ROM at fe920000 [disabled] [size=16k]
Capabilities: <access denied>
Kernel driver in use: b44
Kernel modules: b44
```

I know it's supposed to 'just work,' but it isn't, and I'm trying to figure out why.

---

### Post by daboo911 on 2010-01-21
I've tried commenting out the "option rfc3442" line in dhclient.conf as suggested [here]("http://ubuntuforums.org/showpost.php?p=7280398&postcount=3").  No difference.

And /etc/network/interfaces reads
```
auto lo
iface lo inet loopback
```

---

### Post by pricetech on 2010-01-21
It looks like your NIC is working, but it's not getting an IP from your DHCP server, assuming you have one.

What is upstream from the computers ??

Also, it could be a damaged network jack on the mobo.  Do you have another NIC you can put in the computer to test with ??

---

### Post by daboo911 on 2010-01-21
Upstream from the computer is a Linksys router plugged into a cable modem.  

It's possible that the jack is damaged, but I have no way of knowing (no NIC to pop in and test with).  One light (orange) flashes on the jack itself, and the light on the router blinks too, so it seems like it's alright.  Is there anyway to determine if it is the jack that is busted?  When I put this computer in a closet a year ago, it worked.  Nothing has happened to it since then (and I did clean it up before using it again).

Thanks

---

### Post by pricetech on 2010-01-21
Just for laughs, update the BIOS.  I've solved issues with older Dells by doing that.

The 2400 BIOS is a floppy disk image.  You'll need winders to extract it.

Let us know what that does for you.

---

### Post by pricetech on 2010-01-21
> **daboo911 said:**
> Upstream from the computer is a Linksys router plugged into a cable modem.

and DHCP is turned ON in the router, with no restrictions on handing out IPs ??

Just making sure.

---

### Post by daboo911 on 2010-01-21
Yes, DHCP is on, no restrictions.  Nothing wrong with checking obvious things.  More often than not that's the culprit.  

I wouldn't even know how to go about updating the BIOS, and I don't think I have a floppy drive on any computer other than the 2400, so it might be moot.

---

### Post by pricetech on 2010-01-21
> **daboo911 said:**
> I wouldn't even know how to go about updating the BIOS, and I don't think I have a floppy drive on any computer other than the 2400, so it might be moot.

Go to support.dell.com and click on the Drivers and Downloads link.  Use the service tag from your 2400 to pin down the right BIOS and download what they offer.  Run the executable and it will create a DOS boot disk with the new BIOS on it.

Obviously, you'll need to get a friend to help with this if you don't have a floppy in any other computer.

There is a way to update in Ubuntu, but I think Internet Access would be required to make it work.  At the least you'd have to get the right files downloaded and copied to removable media.

---

### Post by pricetech on 2010-01-21
Another thought;  Do you still have the CD you installed from ??  If so, try booting it again a run it live to see if the network card works that way.

I simply can't think of any reason your NIC would not "just plain work" since I have never had issue with NICs in Dell computers.

---

### Post by daboo911 on 2010-01-21
There is no connection on the LiveCD either.  Should we just declare this jack dead, despite signs of life?
If so, I have no open PCI slots for a new NIC...would a USB ethernet adapter work with kubuntu?

---

### Post by pricetech on 2010-01-21
> **daboo911 said:**
> There is no connection on the LiveCD either.  Should we just declare this jack dead, despite signs of life?
If so, I have no open PCI slots for a new NIC...would a USB ethernet adapter work with kubuntu?

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

The Ubuntu Hardware Wiki.  I can't say first hand, but you might also search the forums if you have a particular USB NIC in mind to see if there have been issues with it.

Good Luck.

---

### Post by daboo911 on 2010-01-21
Ok, so I just went out and bought a [Trendnet USB2.0 to 10/100 adapter]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsTrendNet"), and networking *still* is not working.  Clearly, it's not a hardware issue.  Any suggestions?  I'm getting desperate here.

edit: I should clarify "not working".  The adapter is recognized, and shows up as eth2.  It behaves exactly as the built-in jack, and upon clicking 'Auto eth2' will display 'Activating' for a minute or so, before stopping.  Rebooting doesn't make a difference.

---

### Post by pricetech on 2010-01-21
> **daboo911 said:**
> Ok, so I just went out and bought a [Trendnet USB2.0 to 10/100 adapter]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsTrendNet"), and networking *still* is not working.  Clearly, it's not a hardware issue.  Any suggestions?  I'm getting desperate here.

edit: I should clarify "not working".  The adapter is recognized, and shows up as eth2.  It behaves exactly as the built-in jack, and upon clicking 'Auto eth2' will display 'Activating' for a minute or so, before stopping.  Rebooting doesn't make a difference.

How does it behave with the live CD ??

---

### Post by pricetech on 2010-01-21
> **daboo911 said:**
> Haha, sorry.  I should have emphasized newbie.

```

$ sudo dhclient eth0
Listening on LPF/eth0/00:0b:db:b6:cf:09
Sending on LPF/eth0/00:0b:db:b6:cf:09
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 8
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 14
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 18
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 18
DHCPDISCOVER on eth0 to 155.155.155.155 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I can't say I know what any of this means, but thanks

I assumed when I saw this that the address of 155.155.155.155 was just a typo.  It is isn't it ??  The address should be 255.255.255.255

I'm looking over the thread to see if I've missed a "duh" somewhere.

---

### Post by daboo911 on 2010-01-21
Yes, that was a typo, sorry.  It is 255.255.255.255

It behaves the same on the live CD, except that it registers the adapter as eth1.  It behaves the same otherwise.  Thanks for sticking with me through this.

---

### Post by pricetech on 2010-01-21
From searching the forums I find lots of folks with network issues, but not many solutions.

You're running Karmic, right ??

Download and try [Puppy Linux]("http://puppylinux.com/") and see if it sees your network.  Puppy is small, about 60 megs last time I looked.

To be honest I don't know why you're not getting an IP from your router, but it seems that you are not alone.

---

### Post by pricetech on 2010-01-21
I stumbled upon this thread:
[http://ubuntuforums.org/showthread.php?t=1304843](http://ubuntuforums.org/showthread.php?t=1304843)
Lots of rants, but on the 3rd and 4th pages there seem to be some good suggestions.  Maybe they will apply to your situation.

---

### Post by Iowan on 2010-01-21
[This]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is one of those "really shouldn't matter (or work)" things that may not help, but it's easy enough to try (and undo).

---

### Post by pricetech on 2010-01-22
> **Iowan said:**
> [This]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is one of those "really shouldn't matter (or work)" things that may not help, but it's easy enough to try (and undo).

Sad.  If it were my router, and this worked, I'd beat it to death with a sledge hammer and never buy another one like it.

---

### Post by daboo911 on 2010-01-22
Ok, tried both of those suggestions.  Adding the line made no difference.  The few live CDs I  tried didn't connect either.  I did try both the integrated jack and the USB adapter.  Neither allowed me to connect.  So I guess that means that it isn't a software problem.  But as far as I can tell it isn't anything wrong with the network, either.  And it shouldn't be the jack either, since the adapter doesn't work...  I can't figure out what could be stopping this box from connecting.

---

### Post by pricetech on 2010-01-22
I have a couple of Dimension 2400s here gathering dust in case I need them for parts.

I just put one on the bench and it boots and runs Fiesty with Internet access.

I'm downloading Karmic Kubuntu now and I'll let you know how that goes when I get it burned.

This is one of those problems that turns into an obsession.

---

### Post by daboo911 on 2010-01-22
Haha, I'm glad I'm not the only one who is obsessed with this.  I'm starting to think more and more that this is a hardware problem, but it seems weird since the adapter makes no difference.  And the ethernet cable works.  And the router is handing out addresses.

---

### Post by pricetech on 2010-01-22
I get the "boots to black screen" problem on my 2400.  I have Jaunty on the way.

Latest BIOS for the 2400 is A05, which mine is upgraded to.

---

### Post by Pelgar on 2010-01-22
I'm new to Linux too and had the same problem you have, struggled with it all morning. I right clicked the Network Manager icon then clicked Edit Connections. Under the Wired Tab I selected Auto eth0 then the Edit button. My intent was to turn off the auto ip address and set a fixed addr. but decided to keep trying to get the auto working and backed out. I meant to click Cancel but hit Apply then closed the Network Manager. After this R Clicking the Network Manger showed no connection and I could no longer connect and could no longer reset the network via Network Manager. I did still have the Edit Network option so I went back in to see if I could figure out what I messed up. Retracing the same steps, select eth0 and Edit, all was exactly as it was when I went in originally! I hit Apply once more and exited the Manager and my network has been working ever since. I have no idea why, it makes no sense to me.
I like you had decided that I had a hardware problem but I have a bag full of Ethernet cards and had tried several. All with the exact same results, Network Manager said I was connected but I could not go anywhere.

---

### Post by pricetech on 2010-01-22
Kubuntu Jaunty just plain works.  Is that an option for you ??

I'm curious, you say all your PCI slots are full.  What's in them ??  The 2400 I'm working on has 3 slots and I can't think of that much to poke in there.

---

### Post by daboo911 on 2010-01-22
I have two tv capture cards and a video card for s-video out to a tv.  (this will be used as a mythbox in addition to some other functions).  I'll give both Pelgar's suggestion and Jaunty a try, will report back.

---

### Post by pricetech on 2010-01-22
> **daboo911 said:**
> I have two tv capture cards and a video card for s-video out to a tv.  (this will be used as a mythbox in addition to some other functions).  I'll give both Pelgar's suggestion and Jaunty a try, will report back.

That splains it.  I don't think you mentioned the video thing before.  If so I missed it.

Good Luck with it.  I'll be keeping an eye on the thread to see how you do.

---

### Post by daboo911 on 2010-01-22
Ok, so Pelgar's suggestion doesn't apply to me, since nothing appears under the Wired tab.  Glad it worked for you, even if it didn't make sense.  

I tried Ubuntu Jaunty (couldn't find a kubuntu version for download, whatever), and it could not connect either.  I'm more convinced than ever that it is something specific to this machine.  I don't know what, but this forum is probably not the place for it.  

Thanks to all who have helped so far, and if I do figure it out, I will come back and update this thread.  
If I don't post again, I've taken a bat to this computer and bought a new one.

---

### Post by daboo911 on 2010-01-22
Well, I've figured out the problem, but I don't understand it.  I picked up the tower, and brought it into the room with the router, and plugged it in using another cable, and it worked.  It connected without any fuss, just the way it is supposed to.  

BUT, and this is the big but, the cable it was plugged into at first seems to work.  I say that, because I'm posting this from my powerbook, with the wireless turned off, connected to that *very same* cable.  As far as I can tell, it works perfectly.  Even AIM and Skype work.  I don't understand it, but at least we found the problem, and I'll be running a new cable soon.  

Thanks all of you who went chasing windmills with me.  I shouldn't have doubted kubuntu. 

Cheers!

edit: is there some way to thank users, or give kudos, or points or something on this forum?

---

### Post by Iowan on 2010-01-22
> **daboo911 said:**
> edit: is there some way to thank users, or give kudos, or points or something on this forum? Not currently... but you CAN mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by pricetech on 2010-01-23
> **daboo911 said:**
> BUT, and this is the big but, the cable it was plugged into at first seems to work.  I say that, because I'm posting this from my powerbook, with the wireless turned off, connected to that *very same* cable.

Check the pinout on that cable.  If the wire colors don't exactly match on both ends, you probably have a crossover cable.  Some NICs can handle that, as well as some switches, but not all.

---

### Post by daboo911 on 2010-01-24
That was actually one of the first things I checked, but it's a straight cable.  Mystery, I guess

---

