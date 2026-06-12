---
title: "Help with IPW2200 WiFi wireless module"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by xbalanque on 2006-02-11
hi all :)

i'm trying to get the driver to work with a simple wireless router (LinkSys WR54G Firmware Version : v4.20.7), with no success. And I haven't got a clue what could be the problem :( Pls, any help would be greately apreciated :D

So, my very simple router setup (using wire network I can access the router configuration):

ESSID something
Channel 6
WEP 128bits, 13 hexa numbers


In my ubuntu breezy box (Linux laptop 2.6.12-10-686 #1 Mon Jan 16 17:58:04 UTC 2006 i686 GNU/Linux) I do:

$ rmmod ; modprobe ipw2200  --- I noticed that sometimes removing and reinstalling the modules help; It adds an eth0 wireless network adapter

$ iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX
                    ESSID:"something"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=84/100  Signal level=-46 dBm
                    Extra: Last beacon: 277ms ago

$ ipwconfig eth0 mode managed channel 6 key XXXX...(26 hexa letters, copy and pasted from what i entered in the router) essid "something"

After that, I suppose, it should be ready to run, but 

$ dhclient eth0

never gets an address

$ ping 192.168.1.1 (the router address)

not reachable, actually how would it, eth0 didn't even got an address yet

$ tcpdump -i eth0 (while the commands above)

also returns nothing 

Also, just to be sure some firewall is not interfering, before running the commands I did:

$ iptables -F ; iptables -X


Strange thing is that this used to work. And it still works in windows. :confused: 

I tried to configure the router to open, without WEP or anything, and it also didn't work.

But my tricks are over, anything else that I should check ? -- probably I'm missing the dumbest thing possible :-? 

many thanks in advance! :D 

- jan

ps.: I already checked the WiFiHowto, HOWTO: ipw2200 + wpa, and went to 
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/), but didn't get the courage yet to compile a new driver ... It is such a standard configuration, why shouldn't it work !?!? Why hardware makers makes users life such a mess :(, if they would just agree on some standard ...

<pre>
ps2.: $ dmesg | tail 
[4296650.566000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4296747.283000] ieee80211_crypt: registered algorithm 'NULL'
[4296747.290000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4296747.290000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4296747.300000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4296747.300000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4296747.305000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[4296747.310000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

and the pci list:
$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:04.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)
0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:02:06.4 0805: Texas Instruments: Unknown device 8034
0000:02:06.5 Communication controller: Texas Instruments: Unknown device 8035
0000:10:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11)
</pre>

---

