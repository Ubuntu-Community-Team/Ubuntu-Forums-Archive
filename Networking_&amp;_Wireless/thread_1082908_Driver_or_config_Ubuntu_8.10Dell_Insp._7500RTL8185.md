---
title: "Driver or config? Ubuntu 8.10/Dell Insp. 7500/RTL8185"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by Linux_Mc on 2009-02-28
I can see my network, and my neighbor's networks in the network manager, but I cannot connect with my laptop. I am able to connect with the same laptop when I load Windows2000 on it.

Is it my driver? or configuration in my computer?

I am new to Ubuntu/linux, so lease dumb it down for me. Thanks in advance.

Here is my computer info per the HOW TO post instructions:

lspci:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)



lsusb:
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17088 (17.0 KB)  TX bytes:17088 (17.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:33:92:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-D1-33-92-FC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



iwconfig:
lo        no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



lsmod | grep wlan0:
nothing


dmesg | grep wlan0:
[   81.680099] wlan0: authenticate with AP 00:1a:70:55:68:99
[   81.880125] wlan0: authenticate with AP 00:1a:70:55:68:99
[   82.080140] wlan0: authenticate with AP 00:1a:70:55:68:99
[   82.280083] wlan0: authentication with AP 00:1a:70:55:68:99 timed out
[  262.968171] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6265.400222] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6266.484418] wlan0: authenticate with AP 00:1a:70:55:68:99
[ 6266.684094] wlan0: authenticate with AP 00:1a:70:55:68:99
[ 6266.884102] wlan0: authenticate with AP 00:1a:70:55:68:99
[ 6267.084095] wlan0: authentication with AP 00:1a:70:55:68:99 timed out


sudo lshw -C network:
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 20
       serial: 00:14:d1:33:92:fc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:93:be:9a:f4:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


iwlist scan:
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:55:68:99
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/100  Signal level:17/65  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000151041497a1
                    Extra: Last beacon: 4ms ago



uname -mr:
2.6.27-7-generic i686



sudo /etc/init.d/networking restart:
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by chili555 on 2009-02-28
Do you feel like this is accurate?> Quality=14/100 Signal level:17/65 How far away *is* that router or access point?

---

### Post by Linux_Mc on 2009-02-28
> **chili555 said:**
> Do you feel like this is accurate?How far away *is* that router or access point?

That wouter was actually at my neighbor's house (I think). I have hooked up my router again. This time, it picked up my local router for sure. I renamed the router connection so I could verify that it was in fact mine.

My router is about 5 feet from the laptop I am trying to connect. I re-ran the "iwlist scan" again

Quality=101/100   Signal level:28/65

It still will not make the connection. The little blue fireball rotates over the network manager icon, and then I get the message "Disconnected".

I was able to connect to this router with the same computer when I had Windows2000 on it.

---

### Post by chili555 on 2009-02-28
Have you double-checked your encryption, WPA, WEP, etc.? Please do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you try to connect to your network and let's see if *messages* gives us any useful information.

---

### Post by Linux_Mc on 2009-03-01
> **chili555 said:**
> Have you double-checked your encryption, WPA, WEP, etc.? Please do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you try to connect to your network and let's see if *messages* gives us any useful information.

I have a Linksys router. I checked the WPA WEP settings. For security mode, I do not have WPA or WEP selected. I have "Disabled" selected.

One thing to note, I was able to download Wicd manager (wicd_1.5.9_all.deb) on my desktop, and via usb drive & some package manager, install it on my laptop instead of the normal network manager. I still cannot connect.

sudo tail -f /var/log/messages
Then I pulled up the Wicd manager and tried to connect again. Here is the text from the terminal:
> Mar  1 07:52:18 heath-laptop kernel: [  797.741872] USB Mass Storage support registered.
Mar  1 07:52:23 heath-laptop kernel: [  802.758392] scsi 2:0:0:0: Direct-Access     OTi      Flash Disk       1.89 PQ: 0 ANSI: 2
Mar  1 07:52:25 heath-laptop kernel: [  803.871124] ready
Mar  1 07:52:25 heath-laptop kernel: [  803.875125] sd 2:0:0:0: [sdb] 128000 512-byte hardware sectors (66 MB)
Mar  1 07:52:25 heath-laptop kernel: [  803.879116] sd 2:0:0:0: [sdb] Write Protect is off
Mar  1 07:52:25 heath-laptop kernel: [  803.898249] sd 2:0:0:0: [sdb] 128000 512-byte hardware sectors (66 MB)
Mar  1 07:52:25 heath-laptop kernel: [  803.908214] sd 2:0:0:0: [sdb] Write Protect is off
Mar  1 07:52:25 heath-laptop kernel: [  803.918356]  sdb: sdb1
Mar  1 07:52:25 heath-laptop kernel: [  803.926674] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Mar  1 07:52:25 heath-laptop kernel: [  803.927258] sd 2:0:0:0: Attached scsi generic sg2 type 0
Mar  1 07:57:28 heath-laptop kernel: [ 1106.880453] ADDRCONF(NETDEV_UP): wlan0: link is not ready



---

### Post by Linux_Mc on 2009-03-02
Since I can see the wireless router, does that eliminate the possibility of the wrong driver?

With my security mode in my router set do "disabled", do I need to configure anything in my laptop differently? or should I have the router set to WAP & the laptop set to WAP?

I am new to this, so please excuse my simple questions. Thanks.

---

### Post by chili555 on 2009-03-02
> Since I can see the wireless router, does that eliminate the possibility of the wrong driver?Pretty much. You seem to have a working driver in place.> With my security mode in my router set do "disabled", do I need to configure anything in my laptop differently? or should I have the router set to WAP & the laptop set to WAP?Not yet. Let's get connected reliably first and *then* set up WPA.> I am new to this, so please excuse my simple questions.We were all beginners once upon a time. No worries.

Since we are no longer trying to connect to 'linksys' which is far too far away, let's do a few commands in the terminal and see if we can figure out what's happening. I like terminal commands because they give error messages, if there are any, that we can use to trouble-shoot. Let's do:```
sudo iwlist wlan0 scan
```Does the scan result *confirm* that there is no encryption? Let's suppose the name you set for your router is 'myrouter.' Next do:```
sudo iwconfig wlan0 essid myrouter
sudo dhclient wlan0
```Did you connect or are there some interesting messages?

---

### Post by Linux_Mc on 2009-03-02
sudo iwlist wlan0 scan
> 
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:55:68:99
                    ESSID:"linksys-Mc"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=86/100  Signal level:25/65  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000026ea8184
                    Extra: Last beacon: 24ms ago


sudo iwconfig wlan0 essid linksys-Mc
Nothing

sudo dhclient wlan0

> Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:d1:33:92:fc
Sending on   LPF/wlan0/00:14:d1:33:92:fc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I did not connect.

---

### Post by chili555 on 2009-03-03
This is indeed weird! Here is you scan from Post #1:> wlan0 Scan completed :
Cell 01 - Address: **00:1A:70:55:68:99**
ESSID:"linksys"
Mode:Master
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=14/100 Signal level:17/65 And here is your scan from your most recent post:> wlan0 Scan completed :
Cell 01 - Address: **00:1A:70:55:68:99**
ESSID:"linksys-Mc"
Mode:Master
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=86/100 Signal level:25/65Did you borrow your neighbor's router? Or move closer? Or what...?

Please try the commands I suggested once again and then afterwards run:```
sudo iwconfig wlan0
dmesg | grep wlan0
dmesg | grep rtl8180
```I am especially interested in the iwconfig; I want to know if the essid sticks correctly. Thanks.

---

### Post by Linux_Mc on 2009-03-03
First Question. How do you type in that symbol "|" that is a straight up & down line? The only way I can get those commands in is by copy & paste.

The first router "linsys" was probably my router. I thought it was a neighbor's because I had unplugged mine. When I went back and plugged it in, I discovered that it was actually plugged in to power, just not my desktop, or my internet. Anyway, I reset the router to factory settings, and plugged it back in, and renamed it to linksys-Mc.

- I do know that with factory settings, my laptop was able to connect to it when Windows2000pro was installed.
- I have also tried connecting the laptop to other wireless routers that I know work (since Ubuntu was installed) and it hasn't connected to the internet where other wireless laptops have.

Anyway, here are tonight's results.
(And I do appreciate your helping with this stuff. Thanks)

sudo iwlist wlan0 scan
> 
[sudo] password for heath: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:F0:C5:02
                    ESSID:"dahlbergcentral"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/100  Signal level:17/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000014487795189
                    Extra: Last beacon: 532ms ago
          Cell 02 - Address: 00:1A:70:55:68:99
                    ESSID:"linksys-Mc"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/100  Signal level:17/65  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000143df6d18a
                    Extra: Last beacon: 288ms ago




sudo iwconfig wlan0 essid linksys-Mc
Nothing

sudo dhclient wlan0
> Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:d1:33:92:fc
Sending on   LPF/wlan0/00:14:d1:33:92:fc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


sudo iwconfig wlan0
> wlan0     IEEE 802.11bg  ESSID:"linksys-Mc"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sudo iwconfig wlan0
> wlan0     IEEE 802.11bg  ESSID:"linksys-Mc"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



dmesg | grep rtl8180
> 
[   51.720526] rtl8180 0000:06:00.0: enabling device (0000 -> 0003)
[   51.720562] rtl8180 0000:06:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   51.720600] rtl8180 0000:06:00.0: setting latency timer to 64

---

### Post by Linux_Mc on 2009-03-05
Any suggestions?

---

### Post by chili555 on 2009-03-09
Do you have *linux-backports-modules-intrepid-generic* installed? It apparently has a newer *rlt8180* driver. Perhaps that will work better.

---

