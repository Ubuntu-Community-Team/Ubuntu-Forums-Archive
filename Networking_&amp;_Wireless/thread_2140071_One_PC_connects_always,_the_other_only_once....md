---
title: "One PC connects always, the other only once..."
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by ladasky on 2013-04-28
Hi folks,

I'm away from home, and my familiar computing setup.  I am visiting a friend.  I brought both my laptop and desktop computers with me.  The laptop is running Ubuntu 11.10, the desktop 12.04.1.  I can get the laptop to connect to my friend's wireless modem repeatedly, without problems.  My desktop computer, on the other hand, connected for just one session. After I powered the machine down and restarted it, I cannot get it to connect again.

My friend has a Cisco wireless modem.  Its internal router is a Linksys EA4500.  He uses a WPA2 protocol with a password. Everything is working smoothly with the laptop.

When I started the second session with the desktop machine, what I saw was a long attempt to connect (about 30 seconds).  Then the "wireless network authentication required" dialog box appears, as if I didn't have the correct password.  I have verified that I do indeed have the right password.  I can press "connect" as many times as I like.  Thirty seconds later, the dialog box appears again.

I tried connecting to other routers in the neighborhood, just to see if I would get the password dialog box, and I do.  I enter a password that I know will not work.  The symptoms I see are the same as I see when trying to connect to my friend's router.  But in any case, my desktop appears to be establishing an initial connection with any router I might try.

My home router has a setting which can limit the number of wireless devices connected to the network.  I shut down the laptop with the idea that I might need to open up a slot for the desktop machine to connect.  That didn't change anything.  In any case, I asked my friend (a software engineer) whether there was such a setting on his router, and he said no.

At home, my desktop machine is normally connected to our router by wire.  I had a hand-me-down wireless-N network card that I had never tried before.  It is so generic that the manufacturer's name doesn't even seem to be on it.  The model number on the sticker reads "WS-WNP671N", and apparently that card is made by a company called WinStar.

The laptop is old, an IBM ThinkPad Z60m.  The LAN hardware is apparently an Intel Wireless Pro card, which comes from the days before the wireless-N protocol.  At best, it is connecting to the router using wireless-G.

So I have a few different variables here -- laptop vs. desktop, two different wireless LAN cards, two slightly different operating systems.  I'm especially baffled by the fact that the desktop worked once, flawlessly, and now refuses to play an encore.

If any of you have any ideas how to proceed, I would appreciate it.  Thanks!

---

### Post by Hexxus on 2013-04-28
I would think perhaps DNS issue, try doing a ping from the desktop, see what it is (192.168.0.xxx or something similar), then on the laptop check its IP address and see if they are the same.

Also some cisco products do block traffic (I know you said you got it to work once then nothing) between the LAN and the Wireless/WAN. You might find a setting in there to allow communication between the two network types.

---

### Post by ladasky on 2013-04-28
> **Hexxus said:**
> I would think perhaps DNS issue, try doing a ping from the desktop, see what it is (192.168.0.xxx or something similar), then on the laptop check its IP address and see if they are the same.

I am not clear what you are asking me to do here.  If the desktop hasn't connected to the network, then it shouldn't have an IP address and it shouldn't be able to see any other IP addresses.  So what would I be pinging?

On the laptop, here is the output of **ifconfig**:

```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:fb:95:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:66:1f:89  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe66:1f89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43052 errors:11 dropped:11 overruns:0 frame:0
          TX packets:32870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34539200 (34.5 MB)  TX bytes:5966696 (5.9 MB)
          Interrupt:21 Base address:0xc000 Memory:b0002000-b0002fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5128 (5.1 KB)  TX bytes:5128 (5.1 KB)
```

So it looks like the laptop has connected to the router through eth1.  It has been assigned both an IPv4 address (192.168.1.123) and an IPv6 address (fe80::213:ceff:fe66:1f89/64).  I'm not sure which of those addresses it is using to communicate.

---

### Post by ladasky on 2013-04-28
Follow-up information: 

1) If I try to stop the desktop machine from connecting to the network by pressing "Cancel" in the "wireless network authentication required" dialog box: five minutes or so later, it tries to reconnect again anyway.  Is this behavior expected?

2) My friend just offered to let me use his iPhone's wireless hot spot to connect the desktop machine. That failed, exactly the same way that the connection to the home router failed.  I verified that the password was correct.  I conclude that, after that first lucky session, my desktop will not connect to ANY wireless access point.

3) [_This discussion_]("http://ubuntuforums.org/showthread.php?t=1790271") may be relevant. I am trying to read it now (English is not the first language of the OP).  Two years ago, this Ubuntu 11.04 user had a problem with this WinStar wireless card, which he appears to have fixed by updating its driver.  I would hope that that problem would have been solved by now, and that Linux ships with a functional driver for that card, but I can't be sure.  Of course, I'm still wondering why my system would connect once, but not a second time.

4) As a work-around, I am thinking about configuring my laptop as a network bridge.  Does anyone have any experience with that?  I did it once with Windows XP for my son's XBox, before I installed a proper wired network in our family room. I've installed bridge-utils on the laptop, but I haven't found a good users' guide yet.

---

### Post by ladasky on 2013-04-29
Follow-up #2:

I downloaded a package of updated wireless drivers from the WinTek web site.  The revision date was December 2012.  I found the build instructions to be incomprehensible.

Then it occurred to me that Ubuntu 13.04 should have those wireless drivers built in.  I downloaded the 13.04 ISO, made a bootable USB drive, and booted my desktop from it.  It's SLOW getting started, but it does start.

Unfortunately, the network symptoms were identical.  I entered the password on the authentication dialog box, waited thirty seconds, and was kicked back to the authentication dialog box again.  I got nowhere!

I am having similar difficulties in using my laptop as a network bridge.

I suppose that I don't have to use the desktop machine's WinTek wireless card, assuming that it is, in fact, the obstacle.  I am open to anyone's suggestions for another wireless-N network card that I could buy instead, which is known to be compatible with Linux (EDIT: I suppose that request is addressed by _[this thread]("http://ubuntuforums.org/showthread.php?t=370108")_?  I don't know how current the information is).

But I've been talking to myself in this thread for a while now... thanks to anyone who has suggestions!

---

### Post by varunendra on 2013-04-29
Not a suggestion yet, just an output request.. Please follow the "Wireless Script" link in my signature, follow the instructions there, and post back the contents of "netinfo.txt" file the script creates.

Also, the latest 13.04 seems to have some wrinkles that need to be ironed out before it gets reasonably stable. So, if possible, try to do the rest of the testing on relatively more stable 12.04.2 installation.

---

### Post by ladasky on 2013-04-29
> **varunendra said:**
> Not a suggestion yet, just an output request.. Please follow the "Wireless Script" link in my signature, follow the instructions there, and post back the contents of "netinfo.txt" file the script creates.

Also, the latest 13.04 seems to have some wrinkles that need to be ironed out before it gets reasonably stable. So, if possible, try to do the rest of the testing on relatively more stable 12.04.2 installation.

Thank you Varunendra.  The output I obtained from your script was posted to Ubuntu Pastebin, _[here]("http://pastebin.ubuntu.com/5616601/")_.

I will wait to install 13.04.  I do not want to complicate matters.  I was just hoping that I would obtain a more current wireless driver by upgrading.

I find it interesting that the wireless card worked for one full session, and only failed to connect after a reboot.  And since switching over to the 13.04 Live USB did not restore my connection, it looks like the change was not stored to my operating system -- but to the card.  Is there flash memory on the wireless card, used to store configuration information?  Was some incorrect information written to that flash memory during my first session?

---

### Post by varunendra on 2013-04-30
> **ladasky said:**
> Is there flash memory on the wireless card, used to store configuration information?  Was some incorrect information written to that flash memory during my first session?
As far as I know, there is no persistent memory in NICs. They do remember settings for a short while, or as long as their power is on, but it all disappears if they are left powerless for a while, about 10 minutes to a few hours.

However, there are some BIOS settings that may affect the NIC's behaviour and they persist as long as other BIOS settings. In that case, usually a BIOS reset fixes it all.

Interesting parts in your diagnostics report :
```

03:06.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
	Subsystem: Ralink corp. Device [1814:2860]
	Kernel driver in use: rt2800pci


**** rfkill ****

0: phy0: Wireless LAN
	**Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
	Hard blocked: no


**** NetworkManager.state ****

[main]
NetworkingEnabled=true
**WirelessEnabled=[COLOR="#FF0000"]false[/COLOR]**
WWANEnabled=true
WimaxEnabled=true
```

As you can notice, the wireless interface seems to be 'Soft Blocked' - means it is disabled in Network Manager.

Accordingly, please make sure "Enable Wireless" has a tick mark in the Network Manager's drop-down menu. If it is already enabled there, or grayed-out, check your BIOS to see it is enabled from there. If all this seems okay, try-
```
sudo rfkill unblock all
```
Then recheck -
```
rfkill list
```
It should show both Soft and Hard blocks as 'No'. Once it is done, try to connect. If the authentication box reappears, try -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
This will be a temporary change that will be lost at reboot. We can make it permanent if it helps.

Post back the result.

---

### Post by ladasky on 2013-04-30
> **varunendra said:**
> As you can notice, the wireless interface seems to be 'Soft Blocked' - means it is disabled in Network Manager.  Accordingly, please make sure "Enable Wireless" has a tick mark in the Network Manager's drop-down menu.

Whoops, that was my fault.  I had switched off the wireless when I was trying to connect the laptop up as a network bridge for the desktop machine.

AND once I re-enabled the wireless, and the password authentication dialog came up, and I clicked the checkbox to display the password -- I discovered that one character in the password had CHANGED!  I never re-typed it after that first time that I connected successfully, so I have no idea how it got written to disk incorrectly.  And once I corrected that one character -- I'm back on-line!

That was all very strange.  But thank you for your help!  I'm going to mark the thread as solved.

---

### Post by varunendra on 2013-04-30
> **ladasky said:**
> And once I corrected that one character -- I'm back on-line!

..in so much technical mumbo-jumbo, the magical changes occur so often :)
Glad it fixed...., somehow! :P

---

