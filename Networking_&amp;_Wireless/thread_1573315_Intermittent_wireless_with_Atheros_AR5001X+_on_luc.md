---
title: "Intermittent wireless with Atheros AR5001X+ on lucid."
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by mjc506 on 2010-09-12
Hi all,

I have an old Tatung tablet pc, with touchscreen, stupid speakers and an atheros wifi card (AR5001X+). With XP, everything works reasonably well, and wifi connectivity is rock solid. I know I'm asking for trouble installing *nix on this machine, but if the wireless worked, I'd be happy.

However... With an updated Lucid install, I can see and connect to open, WEP, and WPA(1/2/tkip/aes/whatever) networks. I get good speeds with every network I've tried, but after a minute or two, my connection speed drops to zero, only to recover after another few minutes. A few minutes later, the wireless dies again, then reconnects....

Both the router and the tablet show that I still have a connection, and the connection speed recorded by both does not change from the 'working' condition. I get nothing in the logs (router or tablet) and no indication (aside from transfers stalling) that there's any problem. The 'network history' part of Gnome system monitor shows the data rate dropping to zero, but a network monitor applet on the gnome panel shows transmissions and (later) recieves. Reported signal strength remains constant, and seems to have no bearing on the frequency or length of the dropouts.

I've tried the stock lucid drivers, the lucid wireless backports, and madwifi (currently on madwifi) with no change to symptoms. I did think that it may be to do with scanning for networks (iwevent showed completed scans as the dropouts ended) so I removed network manager and tried static configuration with /etc/network/interfaces . The problems persited (although iwevent is now silent) and I am now using Wicd with no change.

lscpi:
```
sudo lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (MOB) Ethernet Controller (rev 83)
02:09.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller

```ifconfig:
```
ath0      Link encap:Ethernet  HWaddr 00:0b:6b:30:70:63  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:654706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165009 errors:6 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:896220024 (896.2 MB)  TX bytes:14798025 (14.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:260515 (260.5 KB)  TX bytes:260515 (260.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0B-6B-30-70-63-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:621983 errors:0 dropped:0 overruns:0 frame:31948
          TX packets:186477 errors:97 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:509701359 (509.7 MB)  TX bytes:22478633 (22.4 MB)
          Interrupt:10
```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Tamarwaylers"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:15:B7:9F   
          Bit Rate:12 Mb/s   Tx-Power:20 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-59 dBm  Noise level=-84 dBm
          Rx invalid nwid:2887  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```I see nothing *too*bad in these, so I ran a longer test - I bash'd a while loop to ping the router, run ifconfig and iwconfig, and spit the results into files. I concurrently ran a wireshark capture. All of these contain a lot of text/data, so I've attached them here. I can't see any connection between the output of ifconfig/iwconfig/wireshark while the ping drops, but I'm no expert.

If you got this far, congratulations! I know there's a lot of text here, but I hoped to cover everything. Any help or suggestions on what to try next will be gratefully accepted!

[http://mattop.hopto.org/ifconfig](http://mattop.hopto.org/ifconfig)
[http://mattop.hopto.org/iwconfig](http://mattop.hopto.org/iwconfig)
[http://mattop.hopto.org/ping](http://mattop.hopto.org/ping)
[http://mattop.hopto.org/wireshark](http://mattop.hopto.org/wireshark)

---

### Post by bigfootnmd on 2010-09-12
You have encountered almost the same problem that I had with my Acer Aspire One A0751h,  The problem is that drivers included with Lucid do not work well with the Atheros WIFI chip.

There are several solutions one of which is the MADWIFI drivers.  This solution is detailed in this thread

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Please also see 

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Good luck

---

### Post by mjc506 on 2010-09-12
Thanks for your reply. Unfortunately, I've tried both of those drivers/threads. I'm currently running on madwifi at the moment in fact.

---

### Post by bigfootnmd on 2010-09-13
Ok,

A key point in these threads and in the WIFI docs is what can happen after a kernel update.  Also is this extra step

Additional step for kernel 2.6.32.22 and later

Kernel 2.6.32.22 changed the default for the rfkill parameter of ath_pci from 0 to 1, which had the effect of killing the methods described above. You'll need to make sure that it's set back to 0 on system startup. To do that, edit (or create) the file /etc/modprobe.d/options.conf to include the line

options ath_pci rfkill=0

Your wireless should work after you reboot. 

I have already had to remake my madwifi drivers once after a kernel update.  I also have  the 
"options ath_pci rfkill=0 in the /etc/modprobe.d/options.conf file.

With my router at home things work best if I set the WIFI channel to 11 instead of automatic.  Both my netbook and my
wifi enabled Blu-ray player always connect.


Have you tried the modified Kernel module for the Atheros cards?

---

### Post by mjc506 on 2010-09-13
Yeah, madwifi's been rebuilt after each kernel upgrade with no changes, which makes me think its a config issue, or potentially hardware... rkill shows both soft and hard blocks are off, and adding/removing the module option has no effect. I've also tried the hwcrypt option of the ath5k driver too.

Router is set to channel 6 at the moment (lots of wifi traffic on 11) but I tried a few minutes ago on 11 and it doesn't appear to have make any effect.

I'm stumped! Both ubuntu and arch linux's have had this problem, and I've had two ar5001x+ cards in the machine with no effect. Mainboard... I haven't checked, but I'd assume that a mb problem would prevent the card from even being seen?

Thanks for your help, by the way :)

---

### Post by mjc506 on 2010-09-14
Hrmmm.... I ran another run of logs like before, but mistakenly logged the output of 'rfkill list wifi'. A useful accident it seems, since I'm now seeing _hard_ blocks during the outages. I'm not sure why the network remains connected (not that it matters really) but **intermittent hard blocks**? wtf?

More research: The iwlagn guys keep an eye on the temp of the wifi chip, hard blocking it if it crosses a threshold temp of 110C, unblocking it 30secs later. This could be happening to me (although, obviously, with the atheros drivers) since the tablet is pretty cramped. The only cooling is a 25mm side-blow fan! (and that only directly cools the processor, which is a fair way from the wireless card.) Both drivers exhibit the same issue, so it's either a common solution to the overheating problem, or something physically built in to the device (or firmware I guess?) but either way, the chip is either actually overheating, or reporting a false temperature (which the centrino processor occasionally does too).

I'll check the ath5k and/or madwifi source to see if I can see any temperature checks (hopefully I can hack the code to log the temps), and if that is the problem, then I need to do some serious work cooling the thing down...

---

