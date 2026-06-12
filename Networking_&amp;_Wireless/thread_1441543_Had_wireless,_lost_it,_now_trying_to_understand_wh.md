---
title: "Had wireless, lost it, now trying to understand what iwconfig, etc. are telling me"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by wphred on 2010-03-28
A friend who switched ISP's gave me his old Linksys WRT54-G wireless router. I went through the installation procedure and had a wireless connection up and running - smiley face. 

I had security set up for WPA, and decided to upgrade it to WPA2. Another smiley face.

When I went to connect (had already done so successfully), I noticed it referred to my wireless as Linksys - I was expecting to see the SSID. So I started playing around in Network Manager and now I have things all effed up.

Don't know exactly what I did, but now I have no wireless. So I ran a few commands (lshw -C network, iwconfig, ifconfig, and iwlist scan), and looking at the results I see what appear to be inconsistencies in the output.

I've posted them below, and make the following observations:

1. Under the lshw it refers to my wireless connection logical name as wmaster0, and has the correct MAC address, etc.

2. Under the iwconfig it says, 'wmaster0  no wireless extensions', but then refers to wlan0 as the wireless connection (although it does not seem to be running).

3. Under ifconfig I see both a wlan0 and a wlan0:avahi. The wlan0 has no IP, the wlan0:avahi does, but it is incorrect.

 and finally

4. Under iwlist scan it says, 'wmaster0  Interface doesn't support scanning', but then shows a scan for wlan0 where the connection seems to be running.

Am I missing something here, or more importantly, 'What the hell have I done?'. I'm new at this, and may be headed down the wrong trail trying to fix this.

Can someone give me some hints?

wphred@wphred-laptop:~$ sudo lshw -C network 
[sudo] password for wphred: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:33:96:ce
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.35 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:c9010000-c9010fff(prefetchable) memory:c9000000-c900ffff(prefetchable) memory:c9020000-c903ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:a5:e4:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:cb100000-cb10ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
wphred@wphred-laptop:~$ 



wphred@wphred-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.


wphred@wphred-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:33:96:ce  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe33:96ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2595614 (2.5 MB)  TX bytes:191131 (191.1 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:a5:e4:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:21:63:a5:e4:d9  
          inet addr:169.254.11.164  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-A5-E4-D9-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wphred@wphred-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:78:83:BB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a12f89a183
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 00050000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000

---

### Post by chili555 on 2010-03-29
Actually, everything looks rather good! First of all wmaster0 is a dummy interface the system uses; it may safely be ignored. Your wireless interface wlan0 is working.

I only see three things to question. First, you are connected and have an IP address with your wired ethernet:> duplex=full **ip=192.168.1.35 **latency=0 link=yes Network Manager is designed to use the wired connection if it's available and ignore the wireless. In order to connect with wireless, you will need to disconnect the ethernet cable.

Second, your scan result shows no ESSID or network name:> wlan0 Scan completed :
Cell 01 - Address: 00:18:F8:78:83:BB
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=27/70 Signal level=-83 dBm
Encryption keyn
[COLOR="Red"]ESSID:""[/COLOR]Is your ESSID hidden or did you obscure it here in the forum? If your router is not broadcasting the ESSID, you will need to set up a hidden network in Network Manager. Please see attached.

Last, the network you scanned has pretty low signal strength. I wonder if you will be able to connect and stay connected to a weak signal.> Quality=[COLOR="Red"]27/70[/COLOR] Signal level=-83 dBm 

Detach the cable, click the Network Manager icon and see if you can connect.

---

### Post by wphred on 2010-03-29
Sorry to take so long returning your post.

After removing the cable, I reran the same commands. I didn't see much difference, but have posted them below. 

The only change in the lshw command was that the speed for the ethernet interface dropped from 100 MB/s to 10 MB/s.

No changes in the results for the iwlist command.

In the ifconfig command the eth0 interface has no IP address, but then it is not connected. There are no other changes in the results, so it still shows wlan0 without an IP address, etc. 

In the iwlist scan results, the only change I see is a better signal strength (since then I have switched channels on my router and now have 70/70 signal strength.

I think my ESSID is blank because I am not broadcasting it from my router.

I still get no wireless connection. The results from the second run through of the commands are shown below.

Ideas?

wphred@wphred-laptop:~$ sudo lshw -C network
[sudo] password for wphred: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:33:96:ce
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:3000(size=256) memory:c9010000-c9010fff(prefetchable) memory:c9000000-c900ffff(prefetchable) memory:c9020000-c903ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:a5:e4:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:cb100000-cb10ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
wphred@wphred-laptop:~$ 



wphred@wphred-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.


wphred@wphred-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:33:96:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4349724 (4.3 MB)  TX bytes:547380 (547.3 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:a5:e4:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:21:63:a5:e4:d9  
          inet addr:169.254.11.164  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-A5-E4-D9-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wphred@wphred-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:78:83:BB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b56a5d5183
                    Extra: Last beacon: 5056ms ago
                    IE: Unknown: 00050000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000

vboxnet0  Interface doesn't support scanning.

---

### Post by chili555 on 2010-03-29
Did you try to set up a connection to a hidden network as per my attachment? Did it try to connect? Ubuntu is not going to, for security reasons, automatically connect to any old rogue, virus-ridden access point. You must direct it.

---

### Post by wphred on 2010-03-29
Okay - I have a wireless connection now. but I'm still confused about something.

chili555: I followed your procedure and it worked. But here is my question.

When I click on the 'connect to hidden wireless network' I get a pop up window. All boxes are selectable with 'new' as the connection. If I click on that drop down and select my ESSID, all the boxes, including the 'connect' box are greyed out. If I enter new network name and the security I can get a connection. If I put down my original ESSID down as the new network name, it works, but if I then look at network preferences, I have two wireless connections with the same name. I suppose I could make my life easier if I let my router broadcast my ESSID.

By the way, thank you for the time you are taking - it is very helpful.

---

### Post by chili555 on 2010-03-29
I have never tried a hidden network; frankly, I only vaguely understand how it works. My sense is that if you can connect satisfactorily, don't worry too much about the quirks. If you would like to know the answer to your puzzle for educational reasons, an excellant reason, in my opinion, I'd suggest a new thread referencing hidden networks.

Thank you for your kind comments. This is my payoff:> I have a wireless connection now.I love that!

---

### Post by wphred on 2010-03-29
chili555: I changed my router to allow it to broadcast my ESSID, removed the duplicate ESSID, and now things are working just fine - big thanks to you!!

An off topic question. Is there a way to have gui picks shown as their appropriate commands in an xterm as they occur? I'm an old unix user (and I do mean user - at work the IT department takes care of the administration. I use the os as a means of getting work done). I'm used to using an xterm and typing in the commands, and now that I am my own sys admin, I could do a better job of it if I could 'shadow' what the gui is doing.  I know a fair number of commands to use for other things, but I'm a babe in the woods wrt system administration.

---

### Post by chili555 on 2010-03-30
Sadly for me, that is a bit outside my area of experience. I do know you can run any GUI from the command line however, usually only warnings and errors display. You might ask over in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

