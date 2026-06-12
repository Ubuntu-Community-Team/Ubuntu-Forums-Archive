---
title: "Wireless Interface Not Showing"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by wwastro on 2009-06-23
Hi People
Although there is a wireless card in this computer, no interface name seems to be recognised.
My Computer is a HP G7000 laptop with wireless chipset Atheros AR5006EG, however the command ifconfig does not show any wireless interface.
How would I get the computer to recognise the chipset to begin the process of connection?
I'm new to Ubuntu and I don't really understand so please bear with me.
Any help appreciated! Thanks.

PS - I am using Gutsy.
PPS - This is my Dad's account so ignore the stuff to do with the account...

---

### Post by pytheas22 on 2009-06-23
First off, you may have better luck if were using a more recent version of Ubuntu.  Wireless has come a long way since Gutsy; there's a good chance it would work out-of-the-box on Ubuntu 9.04.

Either way, please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
```

With that information, we can figure out how to make the wireless work regardless of your Ubuntu version.

---

### Post by md96360 on 2009-06-23
hello,
i have a similar problem with my wireless card.
I have installed ubuntu for the first time, but wifi worked just untill I have restarted my laptop. After that, i can't get any signal from my ISP, or any other hotspot. So, i formated my disc again, and reinstaled ubuntu, but seam thing happened. I had a signal and connection before first boot. And one other thing, when I turn off my wlan on shortcut button, I get information that the Wireless is Enabled, but when I turn it on (the blue flash lights on) it says that the Wireless is off. 

Now, I have two OS on my laptop, windows and Ubuntu, and on Win wifi works just fine.

after entering this code in terminal: ***lspci -nn*** i have got this informations:

[B][I]Network controler [0280]: Ralink RT2561/RT61 rev B 802.11g [1814:0302]
[/I][/B]

Please help!!!!

---

### Post by drrdf2 on 2009-06-23
Have a look at the previous post on this forum. That might help you?

---

### Post by pytheas22 on 2009-06-24
md96360: please post the output of all of the following commands--we need this information to know what could be the problem:
```

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
sudo iwlist scan
```

If you don't have any Internet access on Ubuntu (i.e. no wired ethernet), you can paste the output into a text file, then transfer that file over to Windows using a USB stick or CD so that it's easy to upload here.

---

### Post by md96360 on 2009-06-24
> **pytheas22 said:**
> md96360: please post the output of all of the following commands--we need this information to know what could be the problem:
```

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
sudo iwlist scan
```

If you don't have any Internet access on Ubuntu (i.e. no wired ethernet), you can paste the output into a text file, then transfer that file over to Windows using a USB stick or CD so that it's easy to upload here.

Thank you very much for your effort.
this is the output of those commands:

> rile@rile-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
05:04.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
05:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
05:04.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
05:09.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]
rile@rile-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ec:e2:dd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: wmaster0
       version: 00
       serial: 00:19:db:9b:b1:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:04:38:1c:ee:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rile@rile-laptop:~$ dmesg | grep -e ath -e wlan
[    3.453548] device-mapper: multipath: version 1.0.5 loaded
[    3.453552] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.536329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
rile@rile-laptop:~$ dmesg | grep -e ath -e wlan
[    3.453548] device-mapper: multipath: version 1.0.5 loaded
[    3.453552] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.536329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
rile@rile-laptop:~$ uname -rm
2.6.28-11-generic i686
rile@rile-laptop:~$ sudo iwlist scan
[sudo] password for rile: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

:popcorn:

---

### Post by wwastro on 2009-06-24
> **pytheas22 said:**
> First off, you may have better luck if were using a more recent version of Ubuntu.  Wireless has come a long way since Gutsy; there's a good chance it would work out-of-the-box on Ubuntu 9.04.

Either way, please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
```

With that information, we can figure out how to make the wireless work regardless of your Ubuntu version.

OK, so:
lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

lshw -C Network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:6e:29:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

dmesg | grep -e ath -e wlan
[   13.048000] ath_hal: module license 'Proprietary' taints kernel.
[   13.052000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.164000] wlan: 0.8.4.2 (0.9.3.2)
[   13.180000] ath_pci: 0.9.4.5 (0.9.3.2)

uname -rm
2.6.22-14-generic i686



So, any suggestions? I don't really understand this but I followed instructions. Thanks for the help so far!

---

### Post by pytheas22 on 2009-06-24
**md96360**: I'm a bit puzzled by your situation.  It looks like everything should be working, but your command-line output indicates that your card can't see any networks.  One possible explanation is that the card is operating in a different mode than your wireless router.  Do you know which mode your router operates in (this should be indicated in its configuration utility)?  There are four possibilities: 11a, 11b, 11g and 11n.  Most modern routers are on 11g or 11n, but if yours is on 11b, for example, but your card is searching in 11g mode, then the card would not be able to see your router.

It's also possible that your wireless card is disabled by a physical button or a software switch (like function+F2).  Do you have a switch like this, and are you sure it's on?

It would also be helpful to see the output of:
```

iwconfig
```

so we'll know which mode your card is operating in.
[B]
wwastro[/B]: I'm also not positive what's wrong for you.  The driver ath_pci should be claiming the card, but it doesn't seem to want to.  It may help to recompile ath_pci from source so that you'll have an updated version.  To do that, first go to [this page]("http://linuxwireless.org/download/compat-wireless-2.6/") and download the file named compat-wireless-old.tar.bz2.  Save it to your desktop.  Then run these commands:
```

cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless*
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot, and hopefully your wireless will work.  If it still doesn't, please post the output of:
```

dmesg | grep -e ath -e wlan
modinfo ath_pci
```

Also, if you upgraded to Ubuntu 8.10 or 9.04, your wireless would almost definitely "just work."  So if that's an option, you may want to consider it; it would ultimately be a better solution than recompiling ath_pci as per the instructions above.

---

### Post by md96360 on 2009-06-25
> **pytheas22 said:**
> **md96360**: I'm a bit puzzled by your situation.  It looks like everything should be working, but your command-line output indicates that your card can't see any networks.  One possible explanation is that the card is operating in a different mode than your wireless router.  Do you know which mode your router operates in (this should be indicated in its configuration utility)?  There are four possibilities: 11a, 11b, 11g and 11n.  Most modern routers are on 11g or 11n, but if yours is on 11b, for example, but your card is searching in 11g mode, then the card would not be able to see your router.

It's also possible that your wireless card is disabled by a physical button or a software switch (like function+F2).  Do you have a switch like this, and are you sure it's on?

It would also be helpful to see the output of:
```

iwconfig
```

so we'll know which mode your card is operating in.


ok, the first thing about stanards is that I belive thet my ISP is using g standards. I've made some screenshots so you can see it by yourself. I've made first photo in windows, and you can see that my network (the second one) is using g standard.

[IMG]http://farm4.static.flickr.com/3308/3659081149_c2af6bdaf2.jpg?v=0[/IMG]

Second thing is my wifi button. It's right by power button. and when it's turned on the blue flash lights. Funny thing (for me) is that when it's turned on in windows it's like turned off in ubuntu. This is the screenshot of my desktop (right up corner is my networkmanager, when I click right mouse button) when the blue flash lights on (for wifi)
[IMG]http://farm3.static.flickr.com/2482/3659876066_b0ed1721ae.jpg?v=0[/IMG]

When I press a wifi button (and blue flash turns off), this is the situation on my network manager (the option Network Enable isn't gray anymore):
[IMG]http://farm4.static.flickr.com/3549/3659874142_446cba3f49.jpg?v=0[/IMG]

And this is the output of iwconfig code:
> rile@rile-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=11 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

rile@rile-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=11 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


I don't know does it matter, but I did this input twice, for I belive turned on wifi and turned off ( blue light on and off), but as you can see the output is the identical in bouth cases...

---

### Post by pytheas22 on 2009-06-25
**md96360**: thanks for that information.  Your card and router are on the same mode, so that's not the problem.  I'm thinking that it most likely has to do with the wireless switch.  Please try the following and let me know the results:

1. turn the wireless off using the button on your computer, then run these commands and post the output:
```

lshw -C Network
dmesg | tail -20
```

2. now flip the wireless back on, wait ten seconds, then post the output of:
```

sudo iwlist scan
lshw -C Network
dmesg | tail -20
```

---

### Post by md96360 on 2009-06-25
> **pytheas22 said:**
> **md96360**: thanks for that information.  Your card and router are on the same mode, so that's not the problem.  I'm thinking that it most likely has to do with the wireless switch.  Please try the following and let me know the results:

1. turn the wireless off using the button on your computer, then run these commands and post the output:
```

lshw -C Network
dmesg | tail -20
```

2. now flip the wireless back on, wait ten seconds, then post the output of:
```

sudo iwlist scan
lshw -C Network
dmesg | tail -20
```

No, thank you :-)
I just did what you asked and this is the result:

> rile@rile-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ec:e2:dd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: wmaster0
       version: 00
       serial: 00:19:db:9b:b1:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:ef:dc:8c:09:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

rile@rile-laptop:~$ dmesg | tail -20
[  190.600065] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  190.600072] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  218.285755] usb 1-3: USB disconnect, address 2
[  218.665399] scsi 4:0:0:0: rejecting I/O to dead device
[  240.456288] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  240.456299] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  240.457534] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  240.457541] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  240.476752] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  240.476761] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  240.477997] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  240.478004] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  240.486609] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[  240.486617] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  240.487860] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[  240.487866] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[  276.749342] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).
[  276.749352] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[  276.750587] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0).
[  276.750594] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
rile@rile-laptop:~$ sudo iwlist scan
[sudo] password for rile: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:0F:AF:04:C2
                    ESSID:"NEON Caparde1"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level:-66 dBm  
                    Encryption key:off
                    IE: Unknown: 000D4E454F4E204361706172646531
                    IE: Unknown: 0108848B968C9298A4B0
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E0000000000660A03000030303A31443A30463A41463A30343A430000000005028509
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Extra:tsf=00000014029934cd
                    Extra: Last beacon: 1072ms ago
          Cell 02 - Address: 00:19:E0:63:A6:9E
                    ESSID:"NEON Caparde 2"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=47/100  Signal level:-76 dBm  
                    Encryption key:off
                    IE: Unknown: 000E4E454F4E20436170617264652032
                    IE: Unknown: 01070B168C9298A4B0
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E0000000000660A030000303031394530363341363945000000000000000005029909
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s
                    Extra:tsf=000000279bd05062
                    Extra: Last beacon: 804ms ago
          Cell 03 - Address: 02:19:E0:73:D7:4C
                    ESSID:"NEON Pristup"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=47/100  Signal level:-74 dBm  
                    Encryption key:off
                    IE: Unknown: 000C4E454F4E2050726973747570
                    IE: Unknown: 01070B168C9298A4B0
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E0000000000660A030000303031394530363341363945000000000000000005029909
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s
                    Extra:tsf=000000279bd0595b
                    Extra: Last beacon: 800ms ago

pan0      Interface doesn't support scanning.

rile@rile-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ec:e2:dd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: wmaster0
       version: 00
       serial: 00:19:db:9b:b1:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:ef:dc:8c:09:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A


I hope this is going to help.. Thanks one more time.

---

### Post by pytheas22 on 2009-06-25
**md96360**: the output of the 'sudo iwlist scan' command indicates that your card was able to see networks with the names "NEON Caparde1," "NEON Caparde2," and "NEON Pristup."  This is very good, because it means that your underlying wireless system is apparently working.

I'm not sure why NetworkManager isn't showing you any networks, but it may help to replace it with wicd, an alternate connection manager that sometimes works better.  To install wicd, run these commands (you will need to be plugged into the Internet first; if that's impossible, let me know and we can work around it):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu, and press the button to scan for networks.  If at first it doesn't show any networks, press the "Preferences" button in wicd and make sure that your wireless interface is specified as "wlan0", then try scanning again.  Do you have better luck with wicd?

---

### Post by md96360 on 2009-06-25
> **pytheas22 said:**
> **md96360**: the output of the 'sudo iwlist scan' command indicates that your card was able to see networks with the names "NEON Caparde1," "NEON Caparde2," and "NEON Pristup."  This is very good, because it means that your underlying wireless system is apparently working.

I'm not sure why NetworkManager isn't showing you any networks, but it may help to replace it with wicd, an alternate connection manager that sometimes works better.  To install wicd, run these commands (you will need to be plugged into the Internet first; if that's impossible, let me know and we can work around it):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu, and press the button to scan for networks.  If at first it doesn't show any networks, press the "Preferences" button in wicd and make sure that your wireless interface is specified as "wlan0", then try scanning again.  Do you have better luck with wicd?

I'm affraid that this is going to be a hardest way, because I don't have any other way to connect on internet. The only way is wireless network, and I use right now the wifi on my laptop but on the Windows XP. So, I would be thankfull if you tell me what to do in this situation.

---

### Post by pytheas22 on 2009-06-25
**ms96360**: that's alright; you can still install wicd without an ethernet connection.  To do it, first download [this file]("http://ubuntu.secs.oakland.edu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb"), and transfer it to your Ubuntu computer using a USB disk or CD (you could also just leave it in Windows, then access your Windows files from the Places menu in Ubuntu...whichever method is easier for you).  Save it on your desktop in Ubuntu.  Then double-click the file and an installer should open, like you're accustomed to seeing in Windows.  Run the installer to install wicd, then launch it from the Applications>Internet menu.

Let me know how this goes.

---

### Post by md96360 on 2009-06-25
> **pytheas22 said:**
> **ms96360**: that's alright; you can still install wicd without an ethernet connection.  To do it, first download [this file]("http://ubuntu.secs.oakland.edu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb"), and transfer it to your Ubuntu computer using a USB disk or CD (you could also just leave it in Windows, then access your Windows files from the Places menu in Ubuntu...whichever method is easier for you).  Save it on your desktop in Ubuntu.  Then double-click the file and an installer should open, like you're accustomed to seeing in Windows.  Run the installer to install wicd, then launch it from the Applications>Internet menu.

Let me know how this goes.


ok, I'll do it right now ;-)

---

### Post by md96360 on 2009-06-25
> **pytheas22 said:**
> **ms96360**: that's alright; you can still install wicd without an ethernet connection.  To do it, first download [this file]("http://ubuntu.secs.oakland.edu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb"), and transfer it to your Ubuntu computer using a USB disk or CD (you could also just leave it in Windows, then access your Windows files from the Places menu in Ubuntu...whichever method is easier for you).  Save it on your desktop in Ubuntu.  Then double-click the file and an installer should open, like you're accustomed to seeing in Windows.  Run the installer to install wicd, then launch it from the Applications>Internet menu.

Let me know how this goes.

I did as you told me, but when I tried to install the package, I've got a message: ERROR; CONFLICT WITH THE INSTALLED PACKAGE, NETWORK MANAGER.

What to do now, should I first uninstall Network manager, and if so, how???

---

### Post by pytheas22 on 2009-06-25
> I did as you told me, but when I tried to install the package, I've got a message: ERROR; CONFLICT WITH THE INSTALLED PACKAGE, NETWORK MANAGER.

What to do now, should I first uninstall Network manager, and if so, how???

Sorry, I didn't think this would be a problem.  But you can install Network Manager by typing:
```

sudo apt-get remove network-manager
```

Then try installing wicd again by double-clicking the icon.

---

### Post by md96360 on 2009-06-25
> **pytheas22 said:**
> Sorry, I didn't think this would be a problem.  But you can install Network Manager by typing:
```

sudo apt-get remove network-manager
```Then try installing wicd again by double-clicking the icon.

**pytheas, you are a king.. thank you very much.** I did as you said, and it's workig. I managged to connect to my ISP. I hope it'll work after a reboot system. 
Now, two more things, I can't see the little icon like it was with the network manager. It would be a good thing to have it (but not very important). I looked for a option to put it on a top bar, but I had no succes.
And other thing, I made a connection with the *sudo pppoeconfig *command, where I entered my username and password. Is there some other way to do it (beside to run this command in Terminal)??

Thank you very much one more time, hundred times more :popcorn:

---

### Post by md96360 on 2009-06-25
for shotcut icon it's OK now, it came up automaticly after reboot...
:P

---

### Post by pytheas22 on 2009-06-26
Glad it's working.  Unfortunately I don't think wicd can support pppoeconfig, so your only option there is to do it manually.  You could maybe also [write a boot script]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") to do pppoeconfig.

---

### Post by wwastro on 2009-06-27
Reply from wwastro to pytheas22:

1) Your last message to us asked for the output to the following set of commands:

cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless*
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install

The above failed at the make command with a message saying that the necessary compat-wireless* files were corrupted [I am writing this on behalf of my son, who submitted the original post. I don't have the details because my son did not record them at the time, and his laptop is currently off].

2) We then installed Ubuntu 8.10 in place of 7.10. However the problem appears to be precisely the same as before - no wireless interface showing with ifconfig, and the same response to the above set of procedures as before.

3) I note that the HP laptop has a wireless switch button. With the original Vista installation this was used to make the wireless connection with our router. I am wondering whether the driver for this has been wiped when we installed Ubuntu, and there is perhaps no equivalent linux driver in place?

I will try to get my son to send you the details of the output to the above commands when he is available.

Thanks again for your interest.

---

### Post by pytheas22 on 2009-06-27
**wwastro**: sorry to hear that the make command failed.  If it complained about corrupted files, it's likely the integrity of the compat-wireless files were compromised when they were being downloaded.  This happens sometimes.

I think the best thing to do now is to erase all of the compat-wireless files currently on your desktop (there should be a folder named compat-wireless-old.bz2; please delete them both).  Then go to [this page]("http://linuxwireless.org/download/compat-wireless-2.6/") and download the file named compat-wireless-2.6.tar.bz2 (note that this is different than the one that was downloaded before--this one does not have "old" in its name, because the "old" version will not work on Ubuntu 8.10).  With the file downloaded, please try running these commands again:

```
cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless*
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
echo ath9k | sudo tee -a /etc/modules
echo ath5k | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```

With any luck, it should work this time, and this will hopefully solve the problem and get wireless going on your machine.

---

### Post by icbolsh on 2009-06-27
> **pytheas22 said:**
> md96360: please post the output of all of the following commands--we need this information to know what could be the problem:
```

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
sudo iwlist scan
```

If you don't have any Internet access on Ubuntu (i.e. no wired ethernet), you can paste the output into a text file, then transfer that file over to Windows using a USB stick or CD so that it's easy to upload here.

Hi pytheas22 apparently you are the king...thank you helping everyone. I'm somewhat of a noob. I just got an Dell D610 from someone and downloaded and installed the latest version of ubuntu. I have a problem with the internal wireless card also. Sounds like it is similar to md96360 problem. It works in windows but not ubuntu. It has a power on and off using fn+F2 keys on the keyboard but nothing seems to happen when I do it in ubuntu(again works in windows). I ran the above code and here is the result.

pete@pete-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
pete@pete-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:15:79:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a ip=192.168.1.164 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:00:e2:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:1d:3d:a5:f6:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
pete@pete-laptop:~$ dmesg | grep -e ath -e wlan
[    3.086942] device-mapper: multipath: version 1.0.5 loaded
[    3.086945] device-mapper: multipath round-robin: version 1.0.0 loaded
pete@pete-laptop:~$ uname -rm
2.6.28-13-generic i686
pete@pete-laptop:~$ sudo iwlist scan

I hope you can help. Please (I am using the laptop with an ethernet, should I disconnect it before running the command?)

---

### Post by wwastro on 2009-06-27
pytheas22: I downloaded that file and started putting in those instructions. I hit errors, though. 
At sudo make load it came up with (obviously errors):
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwlagn...
Loading ath...
FATAL: Module ath not found.
Loading ar9170usb...
FATAL: Module ar9170usb not found.
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Loading mwl8k...
FATAL: Module mwl8k not found.
Loading mac80211_hwsim...
FATAL: Module mac80211_hwsim not found.
Loading at76c50x_usb...
FATAL: Module at76c50x_usb not found.
./scripts/load.sh: line 20: athload: command not found
./scripts/load.sh: line 22: b43load: command not found
make: *** [load] Error 127

After 'sudo make install' it came up with:
Now run:

make unload

And then load the wireless module you need. If unsure reboot.

I had already done 'sudo make unload' but I typed 'make unload' anyway and it came up with:
Unloading ieee80211_crypt...
FATAL: Module ieee80211_crypt is in use.
Unloading ieee80211...
FATAL: Module ieee80211 is in use.
Unloading ipw2100...
FATAL: Error removing ipw2100 (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/ipw2x00/ipw2100.ko): Operation not permitted
Unloading ipw2200...
FATAL: Error removing ipw2200 (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/ipw2x00/ipw2200.ko): Operation not permitted
Unloading libertas_cs...
FATAL: Error removing libertas_cs (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko): Operation not permitted
Unloading usb8xxx...
FATAL: Error removing usb8xxx (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/libertas/usb8xxx.ko): Operation not permitted
Unloading libertas...
FATAL: Module libertas is in use.
Unloading adm8211...
FATAL: Error removing adm8211 (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/adm8211.ko): Operation not permitted
Unloading zd1211rw...
FATAL: Error removing zd1211rw (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko): Operation not permitted
Unloading iwl3945...
FATAL: Error removing iwl3945 (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Operation not permitted
Unloading iwlagn...
FATAL: Error removing iwlagn (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Operation not permitted
Unloading iwlcore...
FATAL: Module iwlcore is in use.
Unloading p54pci...
FATAL: Error removing p54pci (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/p54/p54pci.ko): Operation not permitted
Unloading p54usb...
FATAL: Error removing p54usb (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/p54/p54usb.ko): Operation not permitted
Unloading p54common...
FATAL: Module p54common is in use.
Unloading rt2400pci...
FATAL: Error removing rt2400pci (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Operation not permitted
Unloading rt2500pci...
FATAL: Error removing rt2500pci (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Operation not permitted
Unloading rt61pci...
FATAL: Error removing rt61pci (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Operation not permitted
Unloading rt2500usb...
FATAL: Error removing rt2500usb (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Operation not permitted
Unloading rt73usb...
FATAL: Error removing rt73usb (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Operation not permitted
Unloading rt2x00usb...
FATAL: Module rt2x00usb is in use.
Unloading rt2x00lib...
FATAL: Module rt2x00lib is in use.
Unloading rtl8180...
FATAL: Error removing rtl8180 (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko): Operation not permitted
Unloading rtl8187...
FATAL: Error removing rtl8187 (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko): Operation not permitted
Unloading at76_usb...
FATAL: Error removing at76_usb (/lib/modules/2.6.27-14-generic/kernel/ubuntu/misc/wireless/at76/at76_usb.ko): Operation not permitted
Unloading rndis_wlan...
FATAL: Error removing rndis_wlan (/lib/modules/2.6.27-14-generic/updates/drivers/net/wireless/rndis_wlan.ko): Operation not permitted
Unloading rndis_host...
FATAL: Module rndis_host is in use.
Unloading cdc_ether...
FATAL: Module cdc_ether is in use.
Unloading usbnet...
FATAL: Module usbnet is in use.
Unloading eeprom_93cx6...
FATAL: Module eeprom_93cx6 is in use.
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.

I don't really understand but I finished putting the rest of the commands in and it still cannot show the wireless interface.

Thanks for your help so far!

---

### Post by wwastro on 2009-06-27
To pytheas22 from wwastro:

Further to our last post to you, a wireless interface named wlan0 has now appeared, and the connection GUI has clearly detected our home network. However connection does not work via the GUI.

We have also attempted to connect via the series of commands recommended in a previous sticky thread (by kevdog, "Manual Network Configuration without the need for Network Manager") - these have previously worked reliably on a Dell laptop. Our encryption system is WPA2, and the set of recommended commands (as transferred to the HP machine):

sudo rm -f /var/run/wpa_supplicant/wlan0
sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -w -Dmadwifi -iwlan0 -c/etc/wpa_supplicant.conf -dd
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

(coupled with the recommended /etc/wpa_supplicant.conf file). However the response we get is "Network down".

Our suspicion is that the ath_pci/madwifi module has not been correctly built. What are the diagnostics we need to check this? And how do we repair it?

We seem to have made some progress, but we're clearly not there yet.

Anyway, many thanks for all your help.

---

### Post by pytheas22 on 2009-06-27
**icbolsh**: you probably just need to install the firmware for your card.  Make sure your computer is plugged into the Internet via ethernet, then run:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

You'll be asked if you want to download firmware.  Say yes.  Then reboot and your wireless should work.  If it doesn't, I think it would make the most sense to start a new thread for your issue, since it's not very closely related to wwastro's.  So if you need more help, please open a new thread, let me know the URL and I'll help you there, just so things don't become too convoluted here.

(Note that the above instructions apply to icbolsh because he or she has a Broadcom wireless card; this does not apply to other types of wireless cards, like wwastro's Atheros-based one.)
[B]
wwastro[/B]: good to see that you have a wireless interface recognized--that's definitely progress (and for what it's worth, the error messages you received on 'sudo make load' and 'sudo make unload' aren't anything to worry about).

The reason you get the "Network down" message when running wpa_supplicant from the command line may have to do with NetworkManager interfering with wpa_supplicant.  It therefore may help to turn NetworkManager off by typing:
```

sudo /etc/init.d/NetworkManager stop
```

(or right-clicking NM and selecting 'Disable wireless') before running wpa_supplicant.

If your connection fails even with NM turned off, the best play to look for diagnostics is dmesg, which prints out messages from the kernel.  Immediately after wpa_supplicant errors out, run the command:
```

dmesg
```

for a list of all messages from the system since the last reboot (if the output is too long, you can use a command like 'dmesg | tail -20' to print just the last twenty messages).  Look for lines that have to do with the wireless connection.  Any useful messages there?

It may also be worth your while to try disabling WPA on your router temporarily, just to see if you can connect then.  This will at least let you know that the driver itself definitely works, and that it's just a matter of sorting out encryption issues.

Also, good work figuring out how to do wpa_supplicant from the command line.  It's not easy stuff, even with kevdog's instructions!

---

### Post by wwastro on 2009-06-29
I am not entirely sure what happened as my Dad helped me with most of it, although apparently we don't seem to have madwifi?
I tried those comands again with the Network Manager off and it still didn't work. My Dad looked through the dmesg things and I think he didn't find anything.
He seems to basically think there is a problem with me not having madwifi?
And we can only sometimes see the wireless interface, sometimes there is just 'loopback' I think?

---

### Post by pytheas22 on 2009-06-30
madwifi is now deprecated in favor of the Atheros drivers built into the [compat-wireless]("http://linuxwireless.org/en/users/Download") stack, which is an effort at creating wireless drivers for all types of devices on all Linux systems in a standardized way.  compat-wireless (which is what you installed a few days ago with those 'make' commands) contains a driver for your type of wireless card that's derived from madwifi.  So you basically are using madwifi; it's just not called that anymore.

Given that compat-wireless doesn't seem to be working for you, I'd suggest that you try ndiswrapper instead.  ndiswrapper drives your card using Windows drivers; it's not an ideal solution, but it should work fine on a normal network.  To set it up and install the appropriate drivers, run these commands:
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget burnthesorbonne.com/files/168c_001c_win32.zip
unzip 168c_001c_win32.zip
sudo ndiswrapper -i net5211.inf
sudo ndiswrapper -i
echo ndiswrapper | sudo tee -a /etc/modules
echo blacklist ath9k | sudo tee -a /etc/modules
echo blacklist ath5k | sudo tee -a /etc/modules
```

After this, please reboot and give your wireless another shot.  If it still doesn't work, please post the output of:
```

ndiswrapper -l
dmesg | grep -e ndis -e wlan
lsmod | grep -e ath -e ndis
```

---

### Post by cupevampe on 2009-07-01
Hello people, I'm not sure if o post here or make a new thread altogether... i think here its better.

I have a similar problem to the one in this thread, my Atheros Wifi Card is not showing anymore, and it was working till a couple of weeks ago. I dont really need it but since I use a laptop, it's quite handy to have it available.

I think the problem is the card is "unclaimed" as you can see below...

adama@adama:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:87:eb:f9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=89.125.6.147 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 56:d7:41:f2:a5:dd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I remember I had a similar problem months ago with ethernet... and I solved it somehow although i dont remember how (yeah, i'm one of those newbies for life). Any help is much appreciated!

Thx!

---

### Post by pytheas22 on 2009-07-01
**cupevampe**: it would actually be better if you started a new thread, I think, because this one is already becoming kind of long.  So please go ahead and open a new thread, and in it, please post the output of these commands, in this order:
```

lsmod | grep ath
sudo rmmod ath5k
sudo rmmod ath9k
sudo modprobe ath5k
dmesg | grep -e ath -e wlan
lspci -nn | grep Atheros
```

You didn't upgrade your version of Ubuntu in between the time the wireless worked, did you?  Which version of Ubuntu are you using now?

---

### Post by wwastro on 2009-07-03
Sorry it has been so long since I have posted.

I entered those commands that you posted and I still could not connect wirelessly.
Here are the results you asked for:

ndiswrapper -l:
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath5k)


dmesg | grep -e ndis -e wlan:
[   17.403722] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.445023] usbcore: registered new interface driver ndiswrapper

lsmod | grep -e ath -e ndis:
ndiswrapper           196380  0 
ath9k                 238388  0 
ath5k                 131848  0 
mac80211              225960  2 ath9k,ath5k
led_class              12164  2 ath9k,ath5k
ath                    16128  2 ath9k,ath5k
cfg80211               99872  4 ath9k,ath5k,mac80211,ath
usbcore               149488  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

Thanks so much for your help!

---

### Post by pytheas22 on 2009-07-03
**wwastro**: it looks like the new driver was installed properly, but the old one is still claiming the device for some reason.  To fix that, please try running these commands:
```

sudo rmmod ath5k
sudo rmmod ath9k
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

(You may receive an error message on some of these commands warning you that "Module ... does not exist in /proc/modules".  You can ignore messages like this and just go to the next command.)

After you run those commands, you should be using the new driver, so please try connecting again.  Does it work?

---

### Post by wwastro on 2009-07-08
Thanks for this advice. I am now replying on behalf of my son (whose computer is giving all these problems). Unfortunately the computer now fails to boot up, the final system messages appearing before it stops being:

[COLOR="Blue"]* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
Timeout reached while waiting for return value
Could not receive return value from daemon process.
                                                     [fail]
* Starting Common UNix Printing System: cupsd[/COLOR]

This also occurs on shutting down! He has reinstalled Ubuntu 8.10 again, followed by ndiswrapper etc, and the same problem occurs (though he has not kept a record of everything he has done this time, so it may well be different from the first time around). He attributes this boot failure to installing ndiswrapper, as he says his computer worked OK before attempting the wireless connection (though I am not so sure myself).

Any thoughts/suggestions re this latest problem would be much appreciated, though I realise we are moving outside the scope of the original issue.

---

### Post by pytheas22 on 2009-07-08
> **wwastro said:**
> Thanks for this advice. I am now replying on behalf of my son (whose computer is giving all these problems). Unfortunately the computer now fails to boot up, the final system messages appearing before it stops being:

[COLOR="Blue"]* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
Timeout reached while waiting for return value
Could not receive return value from daemon process.
                                                     [fail]
* Starting Common UNix Printing System: cupsd[/COLOR]

This also occurs on shutting down! He has reinstalled Ubuntu 8.10 again, followed by ndiswrapper etc, and the same problem occurs (though he has not kept a record of everything he has done this time, so it may well be different from the first time around). He attributes this boot failure to installing ndiswrapper, as he says his computer worked OK before attempting the wireless connection (though I am not so sure myself).

Any thoughts/suggestions re this latest problem would be much appreciated, though I realise we are moving outside the scope of the original issue.

I'm really sorry to hear the system isn't booting at all.  I did some googling, and this actually does seem to be an issue related to the wireless interface.  In one sense, this is kind of good because it means ndiswrapper is probably working and bringing up the wireless card--the problem is just that the system is confused about how to deal with it.  But according to the threads I read over, this shouldn't be too hard to fix.

To try to resolve the issue, please boot the computer.  When it gets to the point where it hangs, press control-alt-F2.  This will bring you to a command prompt.  Log in there, then type:
```

sudo nano /etc/network/interfaces
```

This will open a file in a text editor.  Comment out or delete everything that's in that file, with the exception of these lines:
```

auto lo
iface lo inet loopback
```

(You can comment out a line by prefixing it with the # sign.)

After you've made the changes, press control-O (the letter, not zero) to save the file.  Then reboot the computer by typing at the command line:
```

sudo reboot
```

This will hopefully fix the issue and get you into the graphical environment.  Please let me know.

---

### Post by wwastro on 2009-07-12
Thanks a lot for your help, however when I press Control-Alt-F2, absolutely nothing happens. Is it just a wrong shortcut or is this another problem?
Thanks!
--
This is very odd. Just after I pressed Control-Alt-F2, and nothing happened, I re-booted and it booted up fine! What is going on???
--
I tried re-booting again to see if it was permanently fixed and it won't boot up again. And Control-Alt-F2 still won't do anything! This is a headache, thanks for your patience and help!

---

### Post by pytheas22 on 2009-07-12
hmmm.  Control-alt-F2 is indeed the correct combination (actually anything between control-alt-F1 and control-alt-F6 should work, but if F2 isn't working, I doubt any of the others will either).  I'm wondering if the ndiswrapper module is causing your system to freeze so hard that it stops responding altogether.

When the system did boot correctly, did you edit your /etc/network/interfaces file as suggested in my last post?  If you didn't, I think your best bet at this point might be to try rebooting a few more times, and hopefully you'll hit one of the times when it will work.  If it does, take that opportunity to edit /etc/network/interfaces.

If you absolutely can't get it to boot again, you could edit the interfaces file using the live CD, although it would be more work.  But let me know if you need to go that route.

---

### Post by wwastro on 2009-07-14
Hello.
Thank you for your continued support!
Sadly, I didn't edit that file when I managed to boot up, but I have managed to boot up again, however, when I checked, the file only had the two lines you told me to keep anyway, so there was nothing I could do, there was nothing else to delete or comment out.
Now, I still cannot boot up and the file is exactly as you said it should be.
I don't really know what else to do, so any more suggestions would be greatly appreciated!

---

### Post by pytheas22 on 2009-07-14
wwastro: I'm really sorry for all these problems, and many thanks for your patience.

Since ndiswrapper is hanging your system and the /etc/network/interfaces file doesn't seem to have anything to do with it, the best thing I can think to do at this point is get rid of ndiswrapper.  To do that, you will need to get your system to boot, then run:
```

sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
sudo rm /lib/modules/$(uname -r)/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
```

After that, you can try compiling madwifi again, using a different revision of the source code that may work better (this one worked for someone else with the same kind of wireless card as you that I was helping recently).  To compile that, run:
```

sudo apt-get update
sudo apt-get install build-essential subversion
mkdir madwifi
cd madwifi
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4031-20090529.tar.gz
tar -xzvf madwifi*
cd madwifi*
make
sudo make install
echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ath9k | sudo tee -a /etc/modprobe.d/blacklist.conf
echo ath_pci | sudo tee -a /etc/modules
sudo update-initramfs -k all -u
```

After this, reboot.  Hopefully your luck will change and things will finally work!

---

### Post by wwastro on 2009-07-25
Hello!
Sorry it has been so long since I posted, there have been setbacks at our end.
All of the commands you told me to put in seemed to work without any error messages. After setting up the wpa_supplicant.conf file we tried connecting wirelessly as before, however of the interfaces which it recognised (lo, eth0, and pan0), pan0 was the only available candidate for the wireless interface. However, the command lshw -C network revealed the existence of the Atheros wireless card, but there was no associated interface name. It seems that our original problem of not having an identifiable wireless interface name still exists.
Thank you for your perseverance...
Help!
:confused:

---

### Post by pytheas22 on 2009-07-26
Sorry to hear the problem continues, but thanks again for your patience.  If you could please post the output of the following commands after a fresh reboot, it would help to figure out what's going on:
```

lsmod | grep ath
sudo modprobe ath9k
sudo modprobe ath5k
lshw -C Network
dmesg | grep -e ath -e wlan
```

Also, so you know, pan0 is just a virtual interface used by the system for internal traffic.  It doesn't represent a real wireless card, unfortunately.

---

### Post by wwastro on 2009-07-29
OK, here are the outputs to those:

lsmod | grep ath:
ath_pci                99096  0 
wlan                  212080  1 ath_pci
ath_hal               198864  1 ath_pci

sudo modprobe ath9k - there was absolutely no output for this command...


sudo modprobe ath5k:
FATAL: Module ath5k not found.

lshw -C Network:
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:6e:29:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:ad:63:2d:94:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

dmesg | grep -e ath -e wlan:
[   14.173603] ath_hal: module license 'Proprietary' taints kernel.
[   14.180155] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   14.203867] wlan: 0.9.4
[   14.254337] ath_pci: 0.9.4
[   14.254381] ath_pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.254397] ath_pci 0000:01:00.0: setting latency timer to 64
[   14.302907] ath_pci 0000:01:00.0: PCI INT A disabled
[  792.512965] ath9k: 0.1

---

### Post by pytheas22 on 2009-07-30
Given all the we've tried, I'm kind of starting to run out of ideas.  The one solid thought I have is to try using Ubuntu 9.04, since I believe you're currently on 8.10, correct?  This might help because it would provide a more up-to-date version of Ubuntu, and because it would be a clean environment--given all the changes we've made to your current system, the configuration has become pretty messy.

So if it's not too difficult, I think you should burn a CD of Ubuntu 9.04 and at least give it a test in live mode (don't worry about installing it to your hard disk at this point).  If the wireless doesn't "just work" in the live session, try running these commands to switch drivers:
```

sudo rmmod ath_pci
sudo rmmod ath_hal
sudo rmmod ath5k
sudo rmmod ath9k
sudo modprobe ath9k
```

Then try connecting (if an interface appears).  If it still fails, try:
```

sudo rmmod ath5k
sudo rmmod ath9k
sudo rmmod ath_pci
sudo rmmod ath_hal
sudo modprobe ath_pci
```

and try again.  This will switch you between the ath5k and the ath_pci modules, both of which should support your card, but one of which may work better than the other.

---

### Post by wwastro on 2009-08-05
Thank you for your help, but I do not have the time to do this today - I will do this though, thanks again for all your help! Will post again tomorrow...

---

### Post by wwastro on 2009-08-31
The wireless problem is now solved!

Apologies, pytheas22, for no posts for a while, but I left this to my son and he has not got round to it . . .

I managed to figure out on his behalf that the module he really needed was ath5k, and that maybe this was being blacklisted somewhere we did not know about. So after a bit of searching around (using grep and wildcards) I found that ath5k was indeed being blacklisted in /etc/modules. I changed this and instead blacklisted all the other ath modules (ath_pci, ath_hal and ath9k). On rebooting I could then connect directly via the wireless GUI. In order to make this connection automatic I then set the Network Manager to connect to our network.

This worked fine until my son accidentally pressed the wireless button on top of his HP, but when he realised what he had done he could immediately toggle back without difficulty. Now everything seems fine.

Thanks again for all your patience and help - no doubt we missed something you suggested on the way, so apologies if we wasted your time.

---

### Post by pytheas22 on 2009-08-31
I'm really glad to hear this is finally straightened out.  It actually sounds like the solution was pretty simple, so I'm sorry I made you go through so much instead of just trying ath5k.  But I'm glad it's working now and hope you and your son will be able to enjoy Ubuntu.

Also, thanks for marking the thread solved.

---

