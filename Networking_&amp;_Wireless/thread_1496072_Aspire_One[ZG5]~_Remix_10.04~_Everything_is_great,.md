---
title: "Aspire One[ZG5]~ Remix 10.04~ Everything is great, but wireless, please help?"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Rasa1111 on 2010-05-28
hey all, 

  Yesterday I installed Ubuntu netbook remix on a friends new Acer Aspire One Netbook~
It has windows XP, and I partitioned 60GB of the 160GB HD for Ubuntu~

 Everything runs great,  Both Ubuntu and XP~
and everything in Ubuntu works except for the wireless. 

Ive really not had much experience with wireless problems before,
so i truly am lost here. 

 It finds the signal(s), but just wont connect. 

It does work in the XP side though.

My friend is here now,and it would be cool to get this wireless going before he goes home.
any takers? lol

 Here is the info from the following commands~
> 
-netbook:~$** lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:3c:cb:5e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:0b:15:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:55200000-5520ffff
mx607@mx607-netbook:~$ 

> 
mx607@mx607-netbook:~$** lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
mx607@mx607-netbook:~$ 


> 
netbook:~$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3c:cb:5e  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe3c:cb5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:295668461 (295.6 MB)  TX bytes:56631871 (56.6 MB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58792 (58.7 KB)  TX bytes:58792 (58.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:0b:15:0b  
          inet6 addr: fe80::224:2bff:fe0b:150b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20001 (20.0 KB)  TX bytes:27856 (27.8 KB)

>  **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

I think that should be all relevant info,  yeah?

Thanks in advance for any insight. :popcorn:  lol

---

### Post by pdc on 2010-05-28
so if you right-click on network manager; (most left icon of those at top right ..........) and click on wireless; add ..... any joy there?

and you have unplugged the ethernet cable to see if wireless fires up?

---

### Post by Stancel on 2010-05-29
> **pdc said:**
> so if you right-click on network manager; (most left icon of those at top right ..........) and click on wireless; add ..... any joy there?

and you have unplugged the ethernet cable to see if wireless fires up?

The problem is Lucid, not anyone's ethernet cable or network settings. Something is different with Lucid that is causing these problems with wireless connections. I still don't know what it is and how to fix it, despite endless Googling and searching of these forums for any kind of answer. So I just decided not to use Lucid.

---

### Post by krimzonstarr on 2010-05-29
I know you don't want to hear it, but I am running 10.04 full edition with no wireless problems or otherwise. Perhaps not use the UNE? I never liked it due to the interface, but I understand some people have had issues with it.

Also, when I first installed 9.10 on the AAO zg5, the wireless toggle switch on the front was off, without me knowing it. So, try flipping it and rebooting a few times?

---

### Post by Stancel on 2010-05-29
> **krimzonstarr said:**
> I know you don't want to hear it, but I am running 10.04 full edition with no wireless problems or otherwise. Perhaps not use the UNE? I never liked it due to the interface, but I understand some people have had issues with it.

Also, when I first installed 9.10 on the AAO zg5, the wireless toggle switch on the front was off, without me knowing it. So, try flipping it and rebooting a few times?

It's not the netbook version. It's a problem with Lucid.  

Wi-fi always has a stable connection in both Jaunty and Karmic on my laptop. Only when I upgraded to Lucid did I experience these problems: being kicked off the Internet, trying to connect again, being constantly asked for my network key as if the one that I have on there isn't obviously the correct key, it not connecting, I reboot, it connects for some time then randomly kicks me off. That was hell, an endless cycle.

I am very pro-Ubuntu, but I'm not going to go through that. If I knew just how to fix it, I'd stop the bitter ranting. I tried everything I could find but it didn't work.

just for comparison with the thread starter:

> stancel@stancel-laptop:~$ lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:cd:42:d8
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:27 memory:d0888000-d0888fff ioport:30f8(size=8) memory:d0889c00-d0889cff memory:d0889800-d088980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:53:56:43
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:d0400000-d040ffff
stancel@stancel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
stancel@stancel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:cd:42:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:53:56:43  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe53:5643/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36051995 (36.0 MB)  TX bytes:2674719 (2.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3A-53-56-43-35-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

stancel@stancel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:4C:B5:F1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


It's the same adapter. Atheros AR5001.

---

### Post by Orestez on 2010-05-29
> **Stancel said:**
> It's not the netbook version. It's a problem with Lucid.  

Wi-fi always has a stable connection in both Jaunty and Karmic on my laptop. Only when I upgraded to Lucid did I experience these problems: being kicked off the Internet, trying to connect again, being constantly asked for my network key as if the one that I have on there isn't obviously the correct key, it not connecting, I reboot, it connects for some time then randomly kicks me off. That was hell, an endless cycle.
...

I got the exact same issue. It's sad, since Lucid is a LTS release... I didn't find a definitive bug report either, just several wifi bugs (sometimes with the same symptoms).

---

### Post by Rasa1111 on 2010-05-29
Thanks everyone for your replies! 

So there are "many" in the same 'boat' eh? 

 Dang. 

 A friend of mine just recently set-up someones netbook with 10.04 remix and he said the wireless worked right away. :(

  Would installing UNR 9.10 fix the wireless issue?
If so, I will go ahead and put that on for him. 
but who could really know without trying i guess eh? 
so i guess that is a silly question on my part. lol

hmm.....

now i must ponder.... lol

 Thanks again all, much appreciated. :)
Rasa

---

### Post by Orestez on 2010-05-29
Well, there are several work-arounds depending on your actual bug.

Things might help:
- sudo iwconfig wlan1 power off (substitute wlan1 for your device. turns off power management)
- installing backport-drivers
- blacklisting several rt2 drivers (google this, there's a bug report regarding ralink devices)

The blacklisting in conjunction with the power management command have fixed an issue where NM would repeatedly lose the connection without telling me about it and asking again and again for the credentials.

---

### Post by Tom_T on 2010-05-30
I have a similar issue on my acer D150 (same wireless chipset)
Wireless appears connected, and that doesn't drop.

But I have ongoing issues with the wireless just sitting there, no traffic is passed and then it suddenly starts working.

I tried the power off command as suggested, but got an error:
```
    Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```

I don't remember it being this bad on 8.xx or 9.xx :(

---

### Post by Tom_T on 2010-06-04
Ubuntu is virtually useless on my D150.
wireless is forever hanging, stalling etc.

Can anyone help ?

---

### Post by Orestez on 2010-06-04
> **Tom_T said:**
> Ubuntu is virtually useless on my D150.
wireless is forever hanging, stalling etc.

Can anyone help ?

Have you tried the work-arounds? Googled the wifi bugs in Lucid? See above.

---

### Post by carloshiga on 2010-06-04
I have an Asus EeePC 1000HA + AR5001 wireless network card. I spent more than 12 hours trying to get a good connection but it was not possible yet... There are lots of people with this same problem. Why is so hard to make it work?! In Karmic I used the Madwifi but it is not working for Lucid.
What is the solution? Go back to 9.10? That is ridiculous...
If someone knows how to make it work, please share with us.

---

### Post by Orestez on 2010-06-05
Did you upgrade or do a clean install? I had intermittent wifi problems on my Acer Aspire One (lucid), but it was solved after a few updates/blacklisting the ralink drivers (which is weird since it isn't a ralink wifi card).

Have you tried the different workarounds? what do the logs say etc? Help is hard to come by without more information.

---

### Post by Tom_T on 2010-06-05
Hi
I did an upgrade..

Please can you advise what logs I should be looking at !

What should I be searching for in google.  Sorry to ask basic questions, but when my connection works I can search...  Then is just sits there !!

Many thanks for you time and advice.

---

### Post by Orestez on 2010-06-05
> **Tom_T said:**
> Hi
I did an upgrade..

Please can you advise what logs I should be looking at !

What should I be searching for in google.  Sorry to ask basic questions, but when my connection works I can search...  Then is just sits there !!

Many thanks for you time and advice.


Upgrade can break things like that in my experience, and your chip should as far as I know work out of the box, so it's possible the upgrade broke some configuration.

1.
What you can try and what seemed to help on one of my atheros netbooks was deleting the folder /home/*username*/.gnome2/keyrings . this resets your keyrings, and seems to relate to a bug between network-manager and the keyring not being accessed properly for the password.

2.
You can also try installing the wireless backports drivers. Just search for wireless backports in synaptic, you should find it okay. In one case it started working after installing and (after rebooting) uninstalling these drivers.

3.
Thirdly, I don't know whether this works, but one of my computers had the same problem as yours, but a different wifi chipset (ralink), so this might not affect you at all. You can blacklist conflicting drivers by adding the following to the file /etc/modprobe.d/blacklist.conf (for instance by pressing Alt+F2 and typing 'gksu gedit /etc/modprobe.d/blacklist.conf'):

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib


A good starting place in terms of logs is typing dmesg | tail in a terminal after whatever wifi calamity has occured, you should get an error or similar from network-manager etc. Google that error in conjunction with your chipset and ubuntu version/computer model.

> To determine what wireless card/chipset you have, open up a terminal and type the following. lspci -v | less. Then, scroll to find your wireless device...

Let us know how it goes, might help others googlin' their way through the intertubes.

---

### Post by Tom_T on 2010-06-05
Many thanks for you reply & suggestions :)

lspci shows:
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e008
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 95100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

```

When my wireless drops out, I don't get any errors.. which is strange !

I will try your 3 suggestions and will report back :)
It will be tomorrow, before I can do this.

Thanks :)

---

### Post by phoenix1/4 on 2010-06-08
Hey, I'm a forums newbie so im not too sure if I'm supposed to reply to this one or start a new one...

Anyway I'm getting some similar issues to those above, my wireless is very flaky at the moment following upgrade to Lucid Remix. While I've been sitting here for the last 5 minutes (about 3 metres from the router), my signal strength has been sitting at about 20% consistently and has completely dropped twice.

It seems like it is a common problem across the release though, I'm not too sure if there is a process to raise this? Great if it has already been done.

---

### Post by z_diver on 2010-06-30
For what it's worth, my A150 with 10.4 remix wouldn't do anything for an Atheros AR5BXB63 chip.  'lshw -C network' listed the device but disabled and 'ifconfig' didn't even show a wlan interface at all.  So I installed the wireless backports driver metapackage and blacklisted the drivers as listed in steps 2 and 3 below and after rebooting, wifi just came up working.  I flipped the little wifi switch once or twice before restarting also but as I don't know if I turned it on and then off again, I'm not sure that it had much to do with it.  Anyway, there is some hope... good luck folks.

> **Orestez said:**
> 

2.
You can also try installing the wireless backports drivers. Just search for wireless backports in synaptic, you should find it okay. In one case it started working after installing and (after rebooting) uninstalling these drivers.

3.
Thirdly, I don't know whether this works, but one of my computers had the same problem as yours, but a different wifi chipset (ralink), so this might not affect you at all. You can blacklist conflicting drivers by adding the following to the file /etc/modprobe.d/blacklist.conf (for instance by pressing Alt+F2 and typing 'gksu gedit /etc/modprobe.d/blacklist.conf'):

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib


A good starting place in terms of logs is typing dmesg | tail in a terminal after whatever wifi calamity has occured, you should get an error or similar from network-manager etc. Google that error in conjunction with your chipset and ubuntu version/computer model.



Let us know how it goes, might help others googlin' their way through the intertubes.

---

### Post by Tootler on 2010-07-03
I have an Aspire One ZG5 with Linpus Linux Lite.

I would like to convert it to Ubuntu, but when I checked there seemed to be a few issues with the Netbook Remix and AA1 so I tried it running Lucid from a USB stick to test it before going ahead and installing Ubuntu.

It started up OK and most things seemed to work, but wifi did not. I tried connecting the Wireless network. My wifi is hidden, so I selected Connect to Hidden Wireless network, input my network name and security password and nothing When checked the wireless link it showed as not connected. I tried a second time and again nothing but this time when checking the wireless network it showed as disabled, so my attempts to connect had  caused the computer to disable the wireless network. 

Just to test the internet, I plugged in a LAN cable from my wife's computer and that connected fine and I was able to start up Firefox and connect to the internet no problems. 

I then spent the rest of the afternoon looking for a solution to my problem and poor wifi - if you get it at all seems to be a problem with the AA1 and there does not seem to be a universal solution. There is clearly a bug and it needs sorting. 

I am not going to waste much more energy on this. I will stick with Linpus for now until the Wifi issue is properly sorted. For all its faults Linpus on the AA1 does work properly.

I did get one benefit, though. I found a solution to the noisy cooling fan which also seems to be a common problem with the AA1.

---

### Post by pdc on 2010-07-03
so it seems that this computer has the 

> AR242x 802.11abg

and posts such as this

[http://ubuntuforums.org/showthread.php?t=1026770](http://ubuntuforums.org/showthread.php?t=1026770)

talk of the madwifi driver being the right one; 

[http://madwifi.org/](http://madwifi.org/)

is the direct link;

If you have lucid installed on a stick, and you made room for a bit of storage when you set it up, you should be able to install the madwifi drivers and see if it will work .... ?????

---

### Post by Tootler on 2010-07-04
> **pdc said:**
> ...posts such as this

[http://ubuntuforums.org/showthread.php?t=1026770](http://ubuntuforums.org/showthread.php?t=1026770)

talk of the madwifi driver being the right one; 

[http://madwifi.org/](http://madwifi.org/)

is the direct link;

If you have lucid installed on a stick, and you made room for a bit of storage when you set it up, you should be able to install the madwifi drivers and see if it will work .... ?????

I also came across reference to the madwifi driver on Apire One user forum but I did not make a great deal of sense of how to install the driver and, anyway, it seemed a bit hit or miss as to whether it worked, so I suspect it is no more reliable than any of the other proposed solutions. 

I followed up the madwifi link just now and while I got to the page linked every link from there that I tried to follow came up with either a 404 "Page Not Found" error or a 403 "Forbidden" error, so it was not a lot of use. 

It still seems to me that there is a need for a reliable, easy to implement solution - one that a Linux newcomer can easily implement. Having to download and compile software, including sorting out dependencies to make something work does not fit that bill. It is not something you should need to do to make the basics work.

Of course, Ubuntu should have got it right in the first place, but I accept that these things do happen through no one's particular fault.

Linpus works on the AA1 so, though I would prefer to replace it with Ubuntu, I will stick with it for a while longer until the wifi issue is properly sorted.

---

