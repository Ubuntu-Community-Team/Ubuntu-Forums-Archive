---
title: "WiFi in 12.04 works, stops working, requires reboot"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by cyboreal on 2012-05-07
I am running Ubuntu 12.04 on an Acer Aspire 1810t with an Intel 5100 AGN wifi card that has performed flawlessly on Ubuntu 10.04. I assumed the stellar wireless support would continue with 12.04 but have run into a glitch that is a showstopper: wireless works as expected at first, and I can configure connections with Network Manager without any problem, including my WPA2-Personal home network, but after some time (usually a number of hours, almost always after a suspend-to-ram or hibernate) the wireless connection drops and is unable to reconnect. The only reliable solution is to reboot, which is not a solution. Before opening a bug on Launchpad, I thought I'd check and see if anyone else has managed to resolve this problem. Here's what I've got:

Problem: wifi in Ubuntu 12.04 64-bit stops working on the Acer Aspire 1810t (Intel WiFi 5100 AGN) after some time, often after a suspend-to-ram.

** $ uname -a **

Linux ubuntubox 3.4.0-030400rc5-generic #201205011817 SMP Tue May 1 22:18:19 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

(note: the problem is the same when running the stock 3.2.0 kernel)

** $ dmesg ** (at the time the connection drops)

[54671.300096] wlan0: authenticate with 00:24:7b:6d:32:62 (try 1)
[54671.301874] wlan0: authenticated
[54671.304312] wlan0: associate with 00:24:7b:6d:32:62 (try 1)
[54671.308760] wlan0: RX ReassocResp from 00:24:7b:6d:32:62 (capab=0x411 status=0 aid=3)
[54671.308766] wlan0: associated
[54681.808039] wlan0: no IPv6 routers present
[54692.009142] wlan0: deauthenticating from 00:24:7b:6d:32:62 by local choice (reason=3)


** $ sudo lshw -C network **

  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: <snip>
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.4.0-030400rc5-generic firmware=8.83.5.1 build 33692 ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d2500000-d2501fff

** $ sudo lspci -v **

02:00.0 Network controller: Intel Corporation WiFi Link 5100
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d2500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number <snip>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

** $ cat /etc/network/interfaces **

auto lo
iface lo inet loopback

** $ sudo rfkill list all **

2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
7: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
8: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


Troubleshooting
-----

* cannot connect to Open APs or WPA2 APs - when the wifi stops working, I cannot connect to any access points, even Open ones.
* once the network problems start, plugging in a USB WiFi adapter w/ Atheros chipset results in the same problem with both cards. This USB device is known to work with Ubuntu "out of the box", suggesting it is not an iwlwifi driver problem.
* disabling "N" mode in iwlifi does not work: "options iwlwifi 11n_disable=1" in /etc/modprobe.d/disable11n.conf
* no option to use ndiswrapper for this wifi card (which is probably a good thing!)
* unloading iwlwifi before suspend does not work: adding 'SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi"' in /etc/pm/config.d/unload_modules
* switching to kernel 2.6.39 (with iwlagn driver), 3.3.0, 3.4.0rc5 does not work
* removing the acer_wmi module (sudo rmmod acer_wmi) does not work, and disables bluetooth
* "sudo /etc/init.d/networking restart" does not work
* "sudo stop network-manager && sudo start network-manager" does not work
* "sudo rmmod iwlwifi && sudo modprobe iwlwifi" does not work
* deleting the connection in Network Manager and recreating it from scratch does not work

Next steps to try:
* use wicd (network-manager problem?)
* downgrade/upgrade openssl? (seems like a stretch, suggested in this thread: [http://crunchbanglinux.org/forums/topic/18848/solvedwireless-not-working-after-upgrade/](http://crunchbanglinux.org/forums/topic/18848/solvedwireless-not-working-after-upgrade/))

Any ideas? Thanks in advance!

---

### Post by pSYcl0Ne on 2012-05-07
I am having the same problem on an MSI Wind U100+ with Ralink RT2700E on 12.04 32bit.

The problem was also present in 10.04 - but I was able to fix it by editing /etc/modprobe.d/blacklist-rt2800.conf and adding 
# This is to fix wifi on the MSI Wind with the Ralink RT2700E.
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

But blacklist-rt2800.conf is no longer there.

---

### Post by hyfanious on 2012-05-07
I have a worse problem
After waking up from suspend if my wireless would be on as soon as making a connection with a wireless spot, the whole system hangs and a hard restart is required, but if the wireless would be off every thing goes right and after a couple minutes u can turn the wireless on and no problem occurs. 

system : MSI wind U100
Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller

---

### Post by cyboreal on 2012-05-07
I wonder if you are having problems with the driver. It doesn't seem to me to be the same problem as in the original post.

---

### Post by sportykev on 2012-05-10
I have the same exact problem and I believe it occurs when the screen is blanked to save power and/or being connected for a long duration.  I'm on a ThinkPad X200.

When WiFi is cut off, I'm unable to connect to any APs, and when I bring the drop-down of APs down and mouseover to "More Networks", it's a truncated menu and I do not see any APs (would be 20+ hotspots normally).

Help!

---

### Post by cyboreal on 2012-05-10
> **sportykev said:**
> I have the same exact problem and I believe it occurs when the screen is blanked to save power and/or being connected for a long duration.  I'm on a ThinkPad X200.

Does this happen every time the screen is blanked? On my Acer, it only happens after the laptop has been running for some time. The screen blanks many times before it dies, but it always dies. WiFi dies even "during" hibernation. I hibernated a functional laptop and it emerged from hibernation without functional WiFi.

Does 

$ sudo /etc/init.d/networking stop

crash your entire display like it does mine? Obviously, don't try this until you're in bugfix mode and ready to reboot. Not sure if it is compiz that crashes without networking running, but there is definitely a link between the display manager and the networking subsystem.

---

### Post by sportykev on 2012-05-10
> **cyboreal said:**
> Does this happen every time the screen is blanked? On my Acer, it only happens after the laptop has been running for some time. The screen blanks many times before it dies, but it always dies. WiFi dies even "during" hibernation. I hibernated a functional laptop and it emerged from hibernation without functional WiFi.

Does 

$ sudo /etc/init.d/networking stop

crash your entire display like it does mine? Obviously, don't try this until you're in bugfix mode and ready to reboot. Not sure if it is compiz that crashes without networking running, but there is definitely a link between the display manager and the networking subsystem.

Not necessarily.  Somewhat similar to you, sometimes during blanks, sometimes during long uptime (4-8+ hours), they may be related since it has to do with uptime.

This last time, it showed that I was still connected but no net, almost like a broken winsock.  I had to reboot.

---

### Post by cyboreal on 2012-05-11
When your wifi crashes, does `ifconfig` give you weird output, like this:


eth0      Link encap:Ethernet  HWaddr 00:26:9e:9d:f8:d7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2082346173504030 errors:12494089925926065 dropped:4164700936942650 overruns:2082350468471325 frame:10411743752422035
          TX packets:2082350468471325 errors:8329401873885300 dropped:0 overruns:2082350468471325 carrier:4164700936942650
          collisions:10411752342356625 txqueuelen:1000
          RX bytes:2082346173504030 (2.0 PB)  TX bytes:2082350468471325 (2.0 PB)
          Interrupt:45

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:159010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11368725 (11.3 MB)  TX bytes:11368725 (11.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:cb:37:f8
          inet6 addr: fe80::222:fbff:fecb:37f8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38377 (38.3 KB)  TX bytes:27509 (27.5 KB)


Note the bizarrely high number of packets showing on the eth0 interface, which has never been used on this laptop with Ubuntu 12.04. This does not look like an issue with the iwlwifi driver to me. It looks like something is messed up somewhere in the networking stack that affects other network interfaces as well.

When wireless is working, `ifconfig` shows:

eth0      Link encap:Ethernet  HWaddr 00:26:9e:9d:f8:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104152 (104.1 KB)  TX bytes:104152 (104.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:cb:37:f8  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:fecb:37f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:147673588 (147.6 MB)  TX bytes:5854028 (5.8 MB)

---

### Post by sportykev on 2012-05-11
Nope mine does not show anything crazy, that I notice at least.  Here is my ifconfig after wifi fails


eth0      Link encap:Ethernet  HWaddr 00:1f:b6:2d:04:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162379 (162.3 KB)  TX bytes:162379 (162.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 0b:50:56:c0:00:01  
          inet addr:192.168.158.1  Bcast:192.168.158.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:b0:56:c0:00:08  
          inet addr:172.16.50.1  Bcast:172.16.50.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:b6:c6:1c:cf:b0  
          inet6 addr: fe80::226:c6ff:fe1c:cff0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5083593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2753957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7649231497 (7.6 GB)  TX bytes:241733077 (241.7 MB)

---

### Post by RunningMan66 on 2012-05-12
> **sportykev said:**
> I have the same exact problem and I believe it occurs when the screen is blanked to save power and/or being connected for a long duration.  I'm on a ThinkPad X200.

When WiFi is cut off, I'm unable to connect to any APs, and when I bring the drop-down of APs down and mouseover to "More Networks", it's a truncated menu and I do not see any APs (would be 20+ hotspots normally).

Help!

I have the same issue with mine.  After I return from sleep mode, nothing appears in my AP list when I mouseover to "More Networks" or "VPN Connections".  I usually wind up rebooting anyways because I don't find 12.04 as stable as 11.10 and prefer to start fresh.  Seems like every other day there are new updates to install :-s

---

### Post by cyboreal on 2012-05-16
FWIW, I can confirm that the problem has to do with the iwlwifi driver. I opened up my laptop and replaced the Intel 5100 WiFi adapter with a card having an Atheros chipset and all the above problems have vanished. Things are working as expected, even after numerous suspend and resume cycles.

$ lspci
...
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

It's not an ideal fix, but a half-mini PCI express card on eBay is <$10. For me, switching the cards was painless and sure beats reinstalling/downgrading.

---

### Post by cyboreal on 2012-05-16
I take it back. The same problem happened with the Atheros wifi card, though it only happened after 8-10 suspend/resume cycles, rather than just 1. But this time, I was able to fix it without rebooting because the problem is not the wireless hardware or driver. It is the ethernet driver:

$ lspci
...
01:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)

As mentioned in a previous post, something is not working as expected with the eth0 interface, resulting in quadrillions of errant packets after a resume from suspend-to-ram. So simply reloading the ethernet driver fixes all the networking problems for both ethernet and wifi:

$ sudo rmmod atl1c
$ sudo modprobe atl1c

I've edited /etc/pm/config.d/unload_modules and added

SUSPEND_MODULES="$SUSPEND_MODULES atl1c"

to see if this fixes the problem. And no, I do not intend to reinstall the Intel 5100 card to see if it works there too.

---

### Post by Starcruiser322 on 2012-05-20
My problem is really getting out of hand, same as most above but after restarting for the third time today after only 8 mins uptime WHILE I was trying to put up a reply... ](*,)

BTW it's worth noting Windows 7 dual-boot, Windows has no problems whatsoever. I have to log into Windows to get a stable internet connection. :rolleyes:

The possible fix I posted? yeah, no. sorry still not working.

---

### Post by sportykev on 2012-05-31
There seems to be new updates every single day, and I can't say I have seen the issue crop up for a few days now.  Can't confirm that the problem isn't still around, just have not observed it but that's a good sign.

---

### Post by sebl on 2012-06-06
Well, mine Inte 5100 AGN also loses randomly the wifi-connection. Sometimes after 5min, sometimes after 1 hour. Afte rlosing connection I have to reboot, to enable wifi again. I disabled the n-mode and all works fine. This problem is almost 3 years old, but I hoped it was fixed by now.

---

### Post by Jim_in_Omaha on 2012-06-07
> **sebl said:**
> Well, mine Inte 5100 AGN also loses randomly the wifi-connection. Sometimes after 5min, sometimes after 1 hour. Afte rlosing connection I have to reboot, to enable wifi again. I disabled the n-mode and all works fine. This problem is almost 3 years old, but I hoped it was fixed by now.

I have this problem on a Thinkpad T500 with the Intel 5100. It is a nightmare at the school I am attending, but seems to work on everything else I have connected to (which is not a lot of places). To fix it, I have to reboot. I tried to connect to the school, it might connect, then it will stop while showing connected. 

I tried to connect to my Verizon MIFI, but it would not until I rebooted. And then the MIFI worked as usual. If I figure something out I will update.

---

### Post by Jim_in_Omaha on 2012-06-07
In the meantime while I am currently sitting in the student union at the University, I stumbled across a post saying to disable the N on the Intel 5100 adapter. Must be an issue with iwlwifi because there are a bunch of problems on the net.

Basically the commands are these:
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1

And so far the mighty T500 is staying connected to what was a very unstable connection just minutes before. I will update how the stability goes, but so far so good. Now I can view youtube with it halting also... Not that there's anything to watch on that thing...

Heres the link:
[http://ubuntuforums.org/showthread.php?t=1978457]("http://ubuntuforums.org/showthread.php?t=1978457")

Lenovo T500
Intel 5100 AGN wifi

---

### Post by Jim_in_Omaha on 2012-06-13
I fixed my connection problem the hard way. I replaced the wifi card in the laptop with a SL500 card part number 43Y6511. I bought one off of Ebay for $6 delivered. It is half the length and the screws at the position on the frame are short. So the screws that hold in the 5100 card are too long to fit there. I pulled some out of an old CDROM from a really old Thinkpad.

This is the new card.
lspci
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

It has zero issues connecting to the University's campus wifi and is fast. I had to make no changes to my 12.04, just booted and there it was..

---

### Post by Starcruiser322 on 2012-06-15
I hate to be the one to say it but...
Please no multi posts. Edit for other's sake. (let the hate messages flow)

Also, I have seen other people that tried switching their cards with limited success, if any. I saw one that had the result of a slight stability improvement, but no long term effect, and that was a total brand switch (Intel to AMD) 
I haven't noticed the problem since the 200 updates I installed this week, though. I even left it on all night, and even after it was forced to reconnect (power outage) it is fine. 
Here's hoping it's finally fixed (for my card :tongue:)

---

### Post by Jim_in_Omaha on 2012-06-15
Yea I hate multi-post too. Drives up the bean count.

And the new card worked great for over 8 hours this week at class...

---

### Post by Cobuntu on 2012-06-24
Aaaaaah, what a relief I found your thread. Same problem with Fujitsu T730 on Intel Centrino Advanced-N 6200. After checking out your linked threads it seems to be the explanation for problems with my wifi for almost half a year now. 

Is there a way to make the workaround permanent in 12.04 and how to switch N back on again in case?

---

### Post by jimbog007 on 2012-07-03
My DWA-131 was still dropping out with N switched off, although that did make it more stable.

I ended up buying one of these wifi bridges, which works well, you have to set it up under windows though.

[http://www.amazon.co.uk/Vonets-VAP11G-WIFI-Bridge/dp/B0050AI804](http://www.amazon.co.uk/Vonets-VAP11G-WIFI-Bridge/dp/B0050AI804)

---

### Post by MonkeyPaw on 2012-07-25
I have the same issue on an HP ProBook 4530s. 

I can narrow my issue down to being non-adapter specific, as I've used both Atheros and Realtek 802.11n cards and have the same issue on either. Also, it does not do it while running on AC, only if I suspend while on battery. Resume works, except wireless is disabled. Only a reboot cures it.

Hope that helps narrow it down.

---

### Post by kurt18947 on 2012-07-26
For those having trouble with wifi not waking up after suspend,  this might be worth a try.
[http://ubuntuforums.org/showpost.php?p=10226021&postcount=2](http://ubuntuforums.org/showpost.php?p=10226021&postcount=2)

Please note:  > Note to searchers: Substitute your wireless driver module for rt3572sta above.

---

### Post by Experimental Manatee on 2013-01-22
my status:  total newb
my setup:  inspiron 350, quad core, usb wifi = Rosewill RNX-N150UBE
Similar problem as original post:  after suspend, wifi card doesn't work
temporary solutions:  unplug usb wifi card or restart

my input:  I don't know if my first temporary solution sheds any light on the matter, but restarting is no longer necessary, since I simply need to uplug the wifi.

my question:  Is it possible to write a script (or whatever code solutions are called) that does something analogous to unmounting and then mounting the wifi card, regardless of whether the wifi card is usb or PCI express, or whatever?  In other words, is it possible to write code that effectively unplugs the wifi card for you, and then effectively plugs it back in?

---

