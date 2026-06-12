---
title: "Wireless PCMCIA card won't work as eth1, but works MANUALLY as eth2"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by hollinch on 2006-02-07
This is a problem reported before in another thread, see [http://ubuntuforums.org/showthread.php?t=75544]("http://ubuntuforums.org/showthread.php?t=75544").

Situation:
IBM Thinkpad A31p with Cisco Aironet 350 PCMCIA wireless card
Linksys WRT54G wireless router using WEP

I have installed and ran various distributions using this combination without any wireless problems. The Aironet drivers are available in any distro, that's why I like the card eventhough it only runs 11 Mbps. I have successfully installed Fedora Core 2, 3, 4, SuSE 10, RHEL 3, and Knoppix live. They all detected and enabled the Aironet adapter without problems.

While installing Breezy it successfully enabled communication using the wireless card as eth1, after I supplied my WEP key. Thus, installation of Breezy was a breeze.

However, after installation the eth1 network adapter wouldn't retrieve any DHCP address from the router anymore. The only way I got it to work is by configuring and enabling eth2 (which Ubuntu installed for me, but left unconfigured). However, everytime I start the system I have to manually ifup the interface! Doing the same with eth1 never works, but eth2 does.

Both eth1 and eth2 see the wireless router perfectly well (using iwlist). They are configured identical. Yet eth1 will not reach the DHCP server, and eth2 I have to force manually. Frustrating!

I am not the only one having this exact same problem, so I suspect this to be an issue with the way Breezy enables this adapter, or a driver issue in Breezy.

Here's my interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid retuelle
        wireless-key <my key>

iface eth2 inet dhcp
wireless-essid retuelle
wireless-key <my key>

auto eth2
```

Here's an output of iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:"retuelle"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:97:D7:5E
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-50 dBm  Noise level=-94 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:65  Invalid misc:15153   Missed beacon:0

eth1      IEEE 802.11-DS  ESSID:"retuelle"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:97:D7:5E
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-50 dBm  Noise level=-94 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:65  Invalid misc:15153   Missed beacon:0

sit0      no wireless extensions.


```

Output of iwscan:
```
jaap@tpa31p:/var/log$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:97:D7:5E
                    ESSID:"retuelle"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:77/100  Signal level=-57 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s

jaap@tpa31p:/var/log$ iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:0F:66:97:D7:5E
                    ESSID:"retuelle"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:97/100  Signal level=-47 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s

```

And here's the output of ifup eth1:
```
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
eth1: unknown hardware address type 801
sit0: unknown hardware address type 776
eth1: unknown hardware address type 801
Listening on LPF/eth1/
Sending on   LPF/eth1/
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

And, to be complete, here's eth2's ifup output:
```
There is already a pid file /var/run/dhclient.eth2.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
eth1: unknown hardware address type 801
sit0: unknown hardware address type 776
eth1: unknown hardware address type 801
Listening on LPF/eth2/00:0c:85:45:85:fe
Sending on   LPF/eth2/00:0c:85:45:85:fe
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.100 -- renewal in 40086 seconds.

```

Any help GREATLY appreciated - this frustrates the hell out of me. I am very happy with Ubuntu, but this spoils a lot of the fun. Can't expect my wife to open a terminal session and execute a sudo ifup eth2 every time she boots... ;)

Cheers!
Jaap

---

### Post by hajk on 2006-02-08
You say that eth1 and eth2 are configured identically, but that's not entirely true since eth1 is handled by hotplug, and eth2 isn't. Have you tried commenting out the "map eth1" line in /etc/networking/interfaces? BTW, do you boot your ThinkPad with the PCMCIA card already inserted?

---

### Post by hollinch on 2006-02-08
Hi Hajk, thanks for your help! 

I have tried to change the interfaces file to support only eth1 or only eth2, but none has worked. Even manually reconfiguring the eth1 interface with iwconfig failed in trying to connect to the DHCP server. Doing the same with eth2 works fine.

I always have the pcmcia card inserted in the slot before I power on the laptop.

I have reinstalled Ubuntu 3 times already on this same laptop (not to try to resolve the problem!), and every time it created the same issue. A colleague of mine has the same network adapter and encountered the same problem.

Cheers, Jaap.

---

### Post by hajk on 2006-02-08
I have to confess that I went through similar frustrations installing my NetGear PCMCIA card on my (much older) ThinkPad. With > 10 years Debian behind me, I just KNEW that it had to be difficult, no? But it turned out that trying to do it yourself via iwconfig, etc, interferes with the foolproof Ubuntu/Gnome way of getting this done. 

So, here's my advice:

1. Clean out /etc/network/interfaces by removing all lines for the eth1 and eth2 interfaces, also the map eth1 option for hotplug. Do you have the "network-manager" package installed (the one running nm-applet)? Then remove it as well. 

2. Insert your card, then start System/Administration/Networking -- it should list an interface for your card under some name (may be eth1 or wlan0,...) and it should say not configured. I assume such an interface is present, otherwise you need a suitable kernel module...

3. Highlight that interface, select Properties, and then check the box to enable it. You can now configure the interface (you need to do this only once): select the essid ("retuelle"); type in the WEP key; select DHCP. Then OK, and activate the interface.

4. After it has activated, you can check that the necessary lines have been added to /etc/network/interfaces, no need to do this yourself.

5. If you shut down with the interface active, then it will automatically come up next time you boot with the card inserted. Should you elect to deactivate the interface before shutting down, then you'll have to activate it yourself after a reboot -- use System/Administration/Networking for that -- don't mess with ifup, iwconfig,...

Try it.

---

### Post by hollinch on 2006-02-08
OK, I'll give that a try tonight. Thanks. On the face of it I have to admit it looks like an obvious thing to try out, clearing all settings and starting from scratch, but I have to admit that this is something I hadn't thought of trying yet (other than tinkering with the interfaces file). I assumed that as Ubuntu detected and installed the wireless card effortless during installation, it wouldn't screw things up finalising the install. Maybe that's what's gone wrong.

I'll give that a go, and let you know the outcome later tonight. Thanks for the sane advice.

Cheers, Jaap

---

### Post by hollinch on 2006-02-08
It was a useful exercise, but to no avail. The interface eth1 remained useless, eth2 worked.

Some observations:
After removing everything from the interfaces file (save for the lo interface) I restarted the machine without the network card. Once back up I inserted the network adapter and went to the network settings. Lo and behold, both eth1 and eth2 were present! Unconfigured, but still, they were there!

Once I configured eth1 I tried to activate it, but it failed to retrieve an IP address, as before. After this I opened a terminal session and checked iwconfig - it listed both eth1 and eth2 with identical settings... ifconfig only showed eth1, but without IP address.

Once I repeated the process for eth2 it went straight through. 

So, conclusively, no change, the problem remains. Additionally it puzzles me how eth1 and eth2 can still show up in the network settings, even though I cleared out the interfaces file and restarted the machine without the adapter inserted. Where else is this information stored???

Cheers, Jaap.

---

### Post by hollinch on 2006-02-08
Interestingly enough, I noticed that ifconfig shows an odd (using dashes instead of colons) and very long MAC address for eth1, and a valid one for eth2. What may the reason be?

```
eth1      Link encap:UNSPEC  HWaddr 00-0C-85-45-85-FE-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:3583 errors:113 dropped:0 overruns:0 frame:113
          TX packets:1481 errors:33 dropped:0 overruns:0 carrier:33
          collisions:534 txqueuelen:100
          RX bytes:1930411 (1.8 MiB)  TX bytes:146051 (142.6 KiB)
          Interrupt:3 Base address:0x100

eth2      Link encap:Ethernet  HWaddr 00:0C:85:45:85:FE
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:85ff:fe45:85fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3583 errors:113 dropped:0 overruns:0 frame:113
          TX packets:1481 errors:33 dropped:0 overruns:0 carrier:33
          collisions:534 txqueuelen:1000
          RX bytes:1930411 (1.8 MiB)  TX bytes:146051 (142.6 KiB)
          Interrupt:3 Base address:0x100


```

---

### Post by mpvano on 2006-02-09
Do you know if you are using the "hostap" drivers? If so, the rest of this post may be relevant, otherwise ignore it.....

The hostap drivers have a bizarre interface involving creating multiple network devices. I've had no luck making them work consistently here under breezy (although they would have great benefits) because the network device names keep changing on me!

I think there's some kind of bad interaction with other breezy network configuration scripts - I've also noticed that many other interfaces come up with names that disagree with their documentation. I suspect it has something to do with bugs in an undocumented (?)  breezy service named "ifrename".

There also appears to be no useful documentation at all explaining what you are supposed to do with all the hostap created devices anywhere.

At any one time, it appears that you need to direct your configuration commands to only ONE of those devices, but which one it is seems to keep changing, at least for me!

The hostap drivers are very attractive because they temporarily install replacement firmware into cards with broken (or deliberately restricted) firmware functions. For example, they're the only way I've been able to get anything I have with Prism chipsets to scan properly.

I've had little trouble setting up hostap and getting it to work initially (when it's working, it works very well), but everytime I sleep or reboot, the names (and FUNCTION!) of the devices move around and I need to rewrite the network configuration files!

Furthermore, as you've detected, some of the devices it creates have strange (presumably ipv6 - but that makes no sense at all?) media addresses, and the raise hell on my lan if they happen to come up as the active device - my more security aware hosts lock them out instantly, since they perceive this kind of activity as spoofing attempts.

If anyone can point out a source for more reliable information about hostap, or why it malfunctions with ubuntu, I'd sure like to know the answer as well. For now, if this is what's causing your problem you may need to disable hostap like I did, and go back to using simpler drivers for your card.

hope this information helps in some way...

Mario

---

### Post by hollinch on 2006-02-09
Thanks for the help, and for your information. Had no idea something like 'hostap' existed. 

I have checked my system, and I can't find any reference to hostap. From reading online I understand this needs to be loaded as a module, so I checked /etc/modules and did an lsmod, but nothing found.

The modules this card is loading are airo and airo_cs, the former being the driver and the latter the PCMCIA wrapper. 

lsmod | grep airo gives me:
```
airo_cs                 6788  1
airo                   63776  1 airo_cs
pcmcia                 24584  5 airo_cs
pcmcia_core            44932  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

I also understand hostap is a driver for wireless cards using Intersil's Prism chipsets, which the Aironet is not using. See [this]("http://oob.freeshell.org/nzwireless/hostap.html") link.

Anyway, I really appreciate your help, thanks!

---

### Post by Pyrocuror on 2006-02-09
I had the [same issue.]("http://www.ubuntuforums.org/showthread.php?t=86545")  The solution?  When I upgraded my kernel to 2.6.15 it magically started working properly.  

Since then, I have reinstalled and I'm back to the 2.6.12 kernel and having to manually activate eth2 every time.  I'm waiting for 2.6.15 to show up in the Ubuntu Update Manager again.  Not to derail the thread, but is there anyway to get the Update Manager to give me the 2.6.15 kernel upgrade?  I have the install for almost 2 weeks now, and I haven't seen it; only 2.6.12 came up.

---

### Post by hollinch on 2006-02-09
I have 'solved' the problem.

Coincidentally I have a similar Cisco Aironet 350 adapter lying about, and I tried to insert it. It worked first time! No more eth2, eth1 worked immediately.

I haven't tried a reboot yet, but I am confident that this will be successful.

So the question that remains: what was the cause of that behaviour with the original adapter? Is it faulty? I think not, because under Windows it still works fine every time. No hiccups, good performance. And even under Ubuntu it works great as eth2, once manually enabled.

So why? The firmware of both adapters is the same, if I may believe /proc/driver/aironet/eth1/Status. It reports firmware version 5.60.17.

I am puzzled, but I will now reboot to see if that works. Be back later.

Cheers, Jaap.

---

### Post by hollinch on 2006-02-09
Yup, the restart worked perfectly well. No more manual enablements!

This is a weird problem, indeed. Anyone has **any** suggestion?

Anyone in dire need of a fine Cisco wireless PCMCIA card...? Works very well with Windows, and any Linux distro, as long as it is ***not*** Ubuntu Breezy... ;) 

Cheers, Jaap

---

### Post by ssalman on 2006-02-09
hollinch,
   were you able to use WEP? or are you using unsecured connections?

---

### Post by hollinch on 2006-02-10
Hi ssalman.

I use 128-bit WEP, don't broadcast my ESSID, and use MAC address filtering. Works fine, without any problem whatsoever. Wanted to use WPA, but my wireless print server only works with WEP. Besides, 128-bit WEP may be very easy to break into by someone who knows how to achieve this, but in this very small village I live the risk of this happening is very low. I have noticed a couple of other wireless networks in the building, open and unsecured. So I am fine here with my level of security.

Cheers, Jaap.

---

### Post by ssalman on 2006-02-10
hollinch, 
   did you do anything special for the WEP to work, I can't seam to get it to work on my card, I have firmware 5.60.21 and I can't get it to work with WEP, unsecured is fine. I downgraded my firmware to 5.60.17 after reading your post, and I still can't get it to work with WEP. I tried the card on a windows laptop and it worked just fine... this is starting to really bug me!!  ANY help will be greatly appreciated.


BTW do you know how to flash the firmware from Linux? so far I'm using a windows machine.

Thanks.

---

### Post by hollinch on 2006-02-12
No, I have not done anything special to get WEP to work, just supplied my HEX WEP key and zazoom, it worked. 

I have now ordered a new wireless PCMCIA card, the NetGear WG511T, apparently well supported under Linux.

Cheers, Jaap.

---

### Post by karld1 on 2006-02-28
I have the same issue here with an Aironet 340.  Have to enable eth2 each time I boot.

---

### Post by Niku on 2006-04-29
It's an old thread, but I just battled with the same problem myself and figured it out.

SOLUTION:

Edit /etc/iftab and comment out the entry for eth1.

EXPLANATION:

There is a tool called ifrename which reassigns network interface names based on some identifying criteria, typically MAC addresses, configured in /etc/iftab. The idea is to assign permanent names to the interfaces regardless of the order they happen to be inserted, loaded or hotplugged.

The airo/airo_cs driver for some reason makes the Cisco card visible as two interfaces, typically eth1 and wifi0, assuming eth0 is already reserved for a wired ethernet interface. eth1 is the actual interface while wifi0 has a strange, long HW address and is not usable as a network interface. All interfaces are included in /etc/iftab by default and they should be identified by their MAC addresses, but for some reason ifrename ends up renaming the useless wifi0 interface as eth1 and the actual, working interface then becomes eth2. The hotplug stuff operates on eth1, however, so it ends up trying to request an address via DHCP over the useless wifi0 interface.

Commenting out the eth1 entry in /etc/iftab allows the wireless interface names to stay as they are so eth1 will refer to the actual interface and wifi0 can be ignored (no idea what it's there for in the first place!).

---

