---
title: "ubuntu 9.10 &amp; eeepc 1001ha - wireless fix anyone?  :)"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by buntutu on 2009-12-28
[SIZE=4][COLOR=Blue]Hello![/COLOR][/SIZE] ):P

Please bear with me as I am fairly new to Linux although I have tried to learn as much as I can in this short space of time!  

I just installed** [COLOR=DarkOrange]Ubuntu 9.10[/COLOR]** 0n my [COLOR=Magenta]eeepc 1001ha[/COLOR] to dual-boot with windows (had to learn how to get the grub working etc - sheesh - hard, interesting work but that's another story :) ). [COLOR=RoyalBlue]windows is able to connect to the internet[/COLOR] via my router wirelessly but Ubuntu is not (and *[COLOR=DarkOrange]I'd rather use Ubuntu for the internet![/COLOR] * waaah!)  :-({|=

Network manager [COLOR=Magenta]does not even show me the option "enable wireless"[/COLOR].  It doesn't bring up any wireless networks at all.  [SIZE=2][COLOR=DarkOrange]wireless is enabled in the BIOS.[/COLOR][/SIZE] the blue light is on indicating the wireless is on.  I installed wicd and tried using that instead but had the same problem - it didn't pick up any wireless networks, so I put network manager back on. [COLOR=DarkOrchid] [COLOR=SeaGreen]my eeepc701 wireless works fine with the router[/COLOR][/COLOR] - I am using it now.    I emailed asus and got an automated reply to the effect of "make sure wireless is enabled in the BIOS" ](*,)

**I ran sudo [COLOR=Magenta]lspci -v -s[/COLOR]  and got this:**

02:00.0 [COLOR=DarkOrange]Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe[/COLOR]
    Subsystem: Device 1a3b:1087
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fbff0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number 00-25-d3-90-43-ca-00-00

[B]I ran [COLOR=Magenta]iwconfig[/COLOR] and got this ([COLOR=DarkOrange]no mention in there of wlan?[/COLOR]):
[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

**I ran [COLOR=Magenta]ifconfig wlan0 up[/COLOR] and got this:**
[COLOR=DarkOrange]
wlan0: [/COLOR]ERROR while getting interface flags: [COLOR=DarkOrange]No such device[/COLOR]

**I ran  [COLOR=Magenta]sudo lshw -C network[/COLOR] and got this:**

  [COLOR=DarkOrange]*-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbff0000-fbffffff[/COLOR]
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:89:13:32
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.2.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)


I am not sure, being a bear of little brain, what all this means yet.  If anyone could help me understand the problem and help me to fix it I'd be so grateful as I've been trying for days now!  

Cheers \\:D/

---

### Post by gordintoronto on 2009-12-28
This thread should help you, especially message 57:
[http://ubuntuforums.org/showthread.php?t=1274886&page=6](http://ubuntuforums.org/showthread.php?t=1274886&page=6)

Once you have the driver installed, you can right-click on the network manager icon, select "edit connections."  Select the wireless tab, then "add".  You will need your router's ID, encryption type and password.

---

### Post by margazhang on 2009-12-29
Once you get NM working, if it fails later on, I would recommend that you replace by installing wicd via Synaptic. For some reasons, NM does not work for wifi wireless all the time.

---

