---
title: "ATH5001 - upgrade to 9.10 it worked, now not"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by dow mathis on 2009-11-26
Okay, I've got a Compaq cp60 with an atheros 5001 wifi.  Bought it in July, wiped the hard drive and installed 9.04.  Worked happily along.  Last week, I upgraded to 9.10.  Everything worked fine.  Rocked along until a couple of days ago, when the wifi was disabled after returning from suspend.  Re-enabled it through the network icon on the panel (checked the wireless box), and everything was great.  Then this morning, I powered it up and the wifi was disabled.  I unchecked the wireless check box, and now I can't check it again. 

lshw -C network shows:
```
dow@dow-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:71:e2:5d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:da:3a:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

```

iwconfig shows:
```
dow@dow-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:71:e2:5d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:da:3a:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

```

nm-tool shows:
```
dow@dow-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1F:16:71:E2:5D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:24:2B:DA:3A:B9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

I'm not any good with codeing, having gleaned these three commands from other posts tha I've read this morning.  I'm totally at a loss as to why the wireless would be turned off or how to turn it back on.  The laptop has a wifi button, but it's always orange, and has been since I got the computer and instaLLED 9.04.

Can anyone offer a solution?

Thanks,
Dow

---

### Post by drpjkurian on 2009-11-26
hi Dow
It is understood that your card is Atheros 802.11
Your problem can be solved by installing Madwifi drivers which is robust. I too have a same card. 

Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by dow mathis on 2009-11-26
Thanks, Dr. Kurian.  That worked great, and I'm back on wirelessly.  

I see that you use Wicd.  Would you expand on why you use this instead of the app that loads with ubuntu?

Also, I'm curios as to WHY my wireless worked for several days and then just quit working.  Any thoughts on that?

Thanks again!
Dow

---

### Post by drpjkurian on 2009-11-26
> **dow mathis said:**
> Thanks, Dr. Kurian.  That worked great, and I'm back on wirelessly.  

I see that you use Wicd.  Would you expand on why you use this instead of the app that loads with ubuntu?

Also, I'm curios as to WHY my wireless worked for several days and then just quit working.  Any thoughts on that?

Thanks again!
Dow

Hi Dow
You are most welcome.
1.You were using ath5k drivers for your atheros card which might have become unstable after kernel updates. 
2. Wicd is robust. It has not given me any glitches so far.
3.Madwifi too is robust. I have been using both Wicd as well as Madwifi from the period of Hardy heron till date.

With regards
Dr Kurian

---

### Post by dow mathis on 2009-12-05
Dr. Kurian,

I've got another question for you.  One of the things that I do is to connect to my work network via a VPN connection.  However, after installing Wicd, my VPN connection is gone, and apparently there is no way to build another via Wicd.  Do you have any recommendation on how I can recreate this connection?  If not, then can you please give me instructions on how to remove wicd and re-install the previous network control application?

Thanks for all of your help.

Dow

---

### Post by drpjkurian on 2009-12-06
> **dow mathis said:**
> Dr. Kurian,

I've got another question for you.  One of the things that I do is to connect to my work network via a VPN connection.  However, after installing Wicd, my VPN connection is gone, and apparently there is no way to build another via Wicd.  Do you have any recommendation on how I can recreate this connection?  If not, then can you please give me instructions on how to remove wicd and re-install the previous network control application?

Thanks for all of your help.



Dow

Hi
To remove Wicd, Navigate to System-->Administration--> Add Remove programmes.

Type Wicd in search bar. And then uninstall it by clicking 'apply' tab
With regards
Dr Kurian

---

### Post by n3had on 2009-12-06
> **drpjkurian said:**
> Hi Dow
You are most welcome.
1.You were using ath5k drivers for your atheros card which might have become unstable after kernel updates. 
2. Wicd is robust. It has not given me any glitches so far.
3.Madwifi too is robust. I have been using both Wicd as well as Madwifi from the period of Hardy heron till date.

With regards
Dr Kurian

Hi Dr. Kurion

I just a got new USB Wifi Dongle from my friend and connected it but i don't know how to install drivers on 64 bit karmic

lsusb gives
```
Bus 001 Device 003: ID 2001:3a03 D-Link Corp. [hex] DWL-G132 (no firmware)
```

so i tracked using this website [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link) that i need atheros ar5523 drivers. Any help would be appreciated

---

### Post by dow mathis on 2009-12-06
> **drpjkurian said:**
> Hi
To remove Wicd, Navigate to System-->Administration--> Add Remove programmes.

Type Wicd in search bar. And then uninstall it by clicking 'apply' tab
With regards
Dr Kurian

Thanks.  Will uninstalling wicd put the original tool back in place?

---

### Post by drpjkurian on 2009-12-07
> **dow mathis said:**
> Thanks.  Will uninstalling wicd put the original tool back in place?
Hi Dow mathis
Nope. Install Network manager from add remove programme.
Well regarding the wifi dongle, I am sorry to say that I am not an expert in dealing it.

With regards
Dr Kurian

---

### Post by dow mathis on 2009-12-08
Thanks, Dr. Kurian.  I'll give it a shot.

dow

---

