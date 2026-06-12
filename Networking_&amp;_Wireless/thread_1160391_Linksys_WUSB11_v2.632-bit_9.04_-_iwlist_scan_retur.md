---
title: "Linksys WUSB11 v2.6/32-bit 9.04 - iwlist scan returns no networks"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by e&gt;&lt;ogenic on 2009-05-15
Hi all :)

I'm having some trouble getting wireless internet working in my new Ubuntu 9.04 install.

Another community member helped me get the driver for my wireless adapter up and running (see [http://ubuntuforums.org/showthread.php?t=1159121](http://ubuntuforums.org/showthread.php?t=1159121) ), but now iwlist scan won't find any networks.

I'm dual-booting with Windows XP Home SP3 on the same machine and all network hardware is functioning correctly in Windows. I have internet access from Window but NOT from Ubuntu.

The machine is an HP Pavilion 533w, but you can safely disregard that as I've had the case apart and replaces pieces so often that not much of the original system is present any more :D

I don't have the option of updating the network hardware at the moment, and the router and wireless access point are as physically close as possible.

Here's the output requested in [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) :

```
exogenic@deadbox:~$ lsusb | grep 'Linksys'
Bus 002 Device 004: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
exogenic@deadbox:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:06:25:0d:ce:49  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe0d:ce49/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

exogenic@deadbox:~$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"Three17"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

exogenic@deadbox:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
ppdev                  15620  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 40212  0 
at76_usb               77532  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
intel_agp              34108  1 
agpgart                42696  1 intel_agp
usbhid                 42336  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
exogenic@deadbox:~$ dmesg | grep 'at76_usb'
[   12.443841] at76_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   13.970287] at76_usb 2-1:1.0: downloading internal firmware
[   16.400983] usbcore: registered new interface driver at76_usb
[   16.711870] at76_usb 2-1:1.0: downloading external firmware
exogenic@deadbox:~$ sudo lshw -C network
[sudo] password for exogenic: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:40:2b:40:5b:ae
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:0d:ce:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.17 firmware=1.101.4-84 ip=192.168.1.50 link=no wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:e2:42:9f:c5:2f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
exogenic@deadbox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

exogenic@deadbox:~$ lsb_release -d
Description:    Ubuntu 9.04
exogenic@deadbox:~$ uname -mr
2.6.28-11-generic i686
exogenic@deadbox:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
exogenic@deadbox:~$ 
```

This post replaces [http://ubuntuforums.org/showthread.php?t=1160165](http://ubuntuforums.org/showthread.php?t=1160165) which I shouldn't have posted as it doesn't have any of the requested info (my bad!).

---

### Post by e&gt;&lt;ogenic on 2009-05-16
Bump

---

### Post by Peter09 on 2009-05-16
Your first ifconfig output shows your wireless device as having an IP address? Is that true?

---

### Post by e&gt;&lt;ogenic on 2009-05-16
Yes - I needed to assign a static IP address to this machine in Windows and thought I had to carry on using that with Ubuntu.

---

### Post by Peter09 on 2009-05-16
Can you post the contents of

> /etc/network/interfaces

---

### Post by e&gt;&lt;ogenic on 2009-05-16
As advised in [http://ubuntuforums.org/showpost.php?p=7280009&postcount=18](http://ubuntuforums.org/showpost.php?p=7280009&postcount=18) the contents of the interfaces files are:

```
auto wlan0
iface wlan0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
wireless-essid Three17
```

---

### Post by Peter09 on 2009-05-16
As an experiment could you try saving this file and replacing it with one that looks like this

> 
auto lo
iface lo inet loopback



---

### Post by e&gt;&lt;ogenic on 2009-05-16
OK, replaced the interfaces file and restarted Ubuntu.

Tried using Firefox (which started in offline mode) to access google.com and it instantly failed. Then I tried using NetworkManager to create a new wireless network. Upon hitting connect, NetworkManager goes busy and then returns a 'Wireless Network Authentication Required' dialog. No matter what info I put in, NetworkManager goes busy and returns the same dialog over and over. I copied and pasted the WEP key from my router settings, so I know that's correct.

It may be pertinent to mention that with my previous interfaces file, Firefox did NOT start in offline mode and actually attempted to reach google.com (ie, the statusbar message changed to 'looking up google.com'), whereas currently it fails instantly.

---

### Post by Peter09 on 2009-05-16
The reason firefox started was because it believed you had a connection - because you had put all the information into the interfaces file, although you still did not have a connection.

With that removed we can see that the problem is the you cannot authenticate for some reason.

---

### Post by Peter09 on 2009-05-16
Do you see any wireless networks now when you left click on the network manager icon, top right.

---

### Post by e&gt;&lt;ogenic on 2009-05-16
No, nothing listed under Wireless Networks.

---

### Post by Peter09 on 2009-05-16
Can you post the output of

```
lshw -C network
```

---

### Post by e&gt;&lt;ogenic on 2009-05-16
```
exogenic@deadbox:~$ sudo lshw -C network
[sudo] password for exogenic: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:40:2b:40:5b:ae
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:0d:ce:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.17 firmware=1.101.4-84 ip=192.168.1.50 link=no wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:e2:42:9f:c5:2f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
exogenic@deadbox:~$
```

---

### Post by Peter09 on 2009-05-16
Does this link describe your problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316204)

---

### Post by e&gt;&lt;ogenic on 2009-05-16
It does seem to describe what happens pretty well (especially the loop I get stuck in when trying to get my network authorisation accepted), although being new to Linux in general I can't validate the error messages shown in that bug report as I'm not sure how to check for those messages while I'm trying to get connected.

The driver I'm using was downloaded from [http://at76c503a.berlios.de/](http://at76c503a.berlios.de/) and modified to compile as detailed in [http://ubuntuforums.org/showpost.php?p=7279256&postcount=16](http://ubuntuforums.org/showpost.php?p=7279256&postcount=16) .

---

### Post by Peter09 on 2009-05-16
You can see those messages by entering a terminal

```
dmesg | more
```

scroll through and see what you can find

---

### Post by e&gt;&lt;ogenic on 2009-05-16
There are a fair few references to at76c503, at76_usb, wlan0, etc, but without knowing how to filter out what's pertinent, it's hard for me to know what would be useful to post.

The last bit of dmesg at the moment is:

```
[   39.220025] [COLOR=Red]wlan0: no IPv6 routers present[/COLOR]
[   58.948219] wlan0: using BSSID 02:00:05:5f:c3:01
[   68.955120] wlan0: using BSSID 02:00:ee:17:5c:02
[   78.959168] wlan0: using BSSID 02:00:2c:c5:f4:02
[   88.967218] wlan0: using BSSID 02:00:f1:81:8d:03
[   98.971266] wlan0: using BSSID 02:00:09:2f:26:04
[  108.976698] wlan0: using BSSID 02:00:58:dc:be:04
[  118.979389] wlan0: using BSSID 02:00:60:89:57:05
[  120.315103] wlan0: using BSSID 02:00:2b:ec:6b:05
[  141.519967] wlan0: using BSSID 02:00:08:8a:af:06
[  151.524017] wlan0: using BSSID 02:00:4c:37:48:07
[  161.532067] wlan0: using BSSID 02:00:11:f4:e0:07
exogenic@deadbox:~$ 

```I didn't know if the highlighted red line was important or not.

Interestingly, this time after starting Ubuntu, NetworkManager immediately went busy and popped up the authentication dialog I mentioned before. It's never done that before (I've always had to manually select something before anything happened).

---

### Post by jsymolon on 2009-11-16
Also - (for those searching) Make sure that the card is turned on !

>iwconfig eth1
eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   **Tx-Power:off**   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(hit the keyboard wireless power on)

>iwconfig eth1
eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   **Tx-Power:32 dBm**   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

