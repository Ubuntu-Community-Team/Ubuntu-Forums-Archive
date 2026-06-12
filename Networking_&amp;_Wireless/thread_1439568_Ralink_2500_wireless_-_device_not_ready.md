---
title: "Ralink 2500 wireless - device not ready"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by apotts on 2010-03-26
After a 2 year gap, I thought I'd have another go at getting Ubuntu onto my laptop. All installed fine (9.10), apart from the wireless again. AFAIK the laptop has a Ralink USB adapter - it also has a proper kill switch (on) and NO soft switch.

The wireless is a non starter, because in Network Manager the "device is not ready".

```
andrew@andrew-laptop:~$ lsusb
Bus 001 Device 004: ID 0db0:6865 Micro Star International RT2570

andrew@andrew-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          **Tx-Power=off   **
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andrew@andrew-laptop:~$ lsmod
Module                  Size  Used by

rt2500usb              21152  0 
rt2x00usb              11548  1 rt2500usb
rt2x00lib              29756  2 rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib


andrew@andrew-laptop:~$ sudo lshw -C network
[sudo] password for andrew: 
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:3c:bb:27
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:2000(size=256) memory:ec005000-ec0050ff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:76:46:50:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

andrew@andrew-laptop:~$ iwlist scan

wlan0     Failed to read scan data : Network is down


```

I noticed that Ubuntu is wanting to ignore the adapter, so I unblocked it:

```

andrew@andrew-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
andrew@andrew-laptop:~$ rfkill unblock all
andrew@andrew-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

But this made no difference, apart from the TX power coming on (still "device not ready" in NM):

```
andrew@andrew-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
         ** Tx-Power=20 dBm  ** 
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Can anyone help me find a new direction to look in?

---

### Post by chili555 on 2010-03-26
Oh, boy! Ralink day!

Does it help if you do?```
sudo ifconfig wlan0 up
[COLOR="Red"]sudo[/COLOR] iwlist wlan0 scan
```

---

### Post by apotts on 2010-03-26
Chilli,

Thanks for taking the time to reply!

Yes, that works, but only after

```
rfkill unblock all
```

Network manager springs into life, asks for the WPA password and declares that it has connected. :)

Sadly though nothing is actually working. The network client has scooped up all the correct numbers from DHCP, but I can't even ping the router. :(

---

### Post by chili555 on 2010-03-26
Once it thinks it is connected, please do:```
iwconfig
ifconfig
route -n
cat /etc/resolv.conf
```Thanks.

---

### Post by apotts on 2010-03-26
Certainly!

```
andrew@andrew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"myessid"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:50:7F:9D:96:78   
          Bit Rate=36 Mb/s   Tx-Power=21 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andrew@andrew-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:3c:bb:27  
          inet6 addr: fe80::290:f5ff:fe3c:bb27/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2041 (2.0 KB)  TX bytes:4758 (4.7 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:816 (816.0 B)  TX bytes:816 (816.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0c:76:46:50:ad  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe46:50ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:439236 (439.2 KB)  TX bytes:13445 (13.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-76-46-50-AD-34-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

andrew@andrew-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
andrew@andrew-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

```

---

### Post by chili555 on 2010-03-26
It only looks perfect! What does this tell us?```
ping -c3 192.168.1.1
ping -c3 www.google.com
```I am interested in the exact message, please.

---

### Post by apotts on 2010-03-26
This is also my first check - and it won't ping the router:

```
andrew@andrew-laptop:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

andrew@andrew-laptop:~$ ping -c3 www.google.com
ping: unknown host www.google.com

```

---

### Post by chili555 on 2010-03-26
I wonder if it soft blocks immediately. After this wacky behavior, run rfkill again and let me know the result. What kind of Acer is it?

---

### Post by apotts on 2010-03-26
No, it remains unblocked all the time. I agree, it is odd. For good measure I disabled all security on the router, but no difference.

The laptop isn't an Acer, it's a "Rock Quaddro Pro" which is built on a Clevo D40EV Prescott chassis.

---

### Post by chili555 on 2010-03-26
May I please see:```
lsmod
dmesg | grep wlan
```Something funny is going on, or, more probably, *not* going on!

---

### Post by apotts on 2010-03-26
Here goes:

```
andrew@andrew-laptop:~$ rfkill unblock all
andrew@andrew-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
pcmcia                 36808  0 
snd_seq_midi            6464  0 
rt2500usb              21152  0 
rt2x00usb              11548  1 rt2500usb
rt2x00lib              29756  2 rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
gspca_zc3xx            47580  0 
gspca_main             22812  1 gspca_zc3xx
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               36736  1 gspca_main
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
v4l1_compat            14336  1 videodev
cfg80211               93052  2 rt2x00lib,mac80211
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_sis96x              3904  0 
shpchp                 32272  0 
ppdev                   6688  0 
parport_pc             31940  1 
irda                  189564  0 
crc_ccitt               1852  1 irda
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
r8169                  32064  0 
mii                     5212  1 r8169
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp

andrew@andrew-laptop:~$ dmesg | grep wlan
[   19.101212] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   70.296591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.182898] wlan0: authenticate with AP 00:50:7f:9d:96:78
[   78.184677] wlan0: authenticated
[   78.184683] wlan0: associate with AP 00:50:7f:9d:96:78
[   78.186905] wlan0: RX AssocResp from 00:50:7f:9d:96:78 (capab=0x431 status=0 aid=4)
[   78.186909] wlan0: associated
[   78.191780] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.608010] wlan0: no IPv6 routers present



```

---

### Post by chili555 on 2010-03-26
Boy, that still looks wacky. You evidently have an ethernet connection. I suggest you do:```
sudo apt-get install linux-backports-modules-karmic-generic
```There is a newer rt2500usb et al in there. Reboot and let's diagnose from there.

---

### Post by raghav1 on 2010-03-26
Hello Chili555,

I have been having the same problem as 'apotts'.  I followed your instructions in the last post.  My enable wireless button is now greyed out.  Any suggestions on how to proceed next?

Thanks!

---

### Post by chili555 on 2010-03-26
> **raghav1 said:**
> Hello Chili555,

I have been having the same problem as 'apotts'.  I followed your instructions in the last post.  My enable wireless button is now greyed out.  Any suggestions on how to proceed next?

Thanks!May we see:```
lsmod | grep rt2 
```Thanks.

---

### Post by raghav1 on 2010-03-26
Here it is

raghu@raghu-laptop:~$ lsmod | grep rt2
rt2500pci              15100  0 
rt2x00pci               7868  1 rt2500pci
rt2x00lib              29820  2 rt2500pci,rt2x00pci
led_class               4096  1 rt2x00lib
mac80211              210508  2 rt2x00pci,rt2x00lib
cfg80211              130632  2 rt2x00lib,mac80211
eeprom_93cx6            1916  1 rt2500pci
raghu@raghu-laptop:~$

---

### Post by apotts on 2010-03-27
> **chili555 said:**
> Boy, that still looks wacky. You evidently have an ethernet connection. I suggest you do:```
sudo apt-get install linux-backports-modules-karmic-generic
```There is a newer rt2500usb et al in there. Reboot and let's diagnose from there.

Done this, but now rfkill has it as hard blocked (when the hardware switch is on). *Unblock all* does not seem to unblock a hard block.

So now unfortunately I have nothing working at all. :( Is it easy to undo the installation of those modules?

---

### Post by chili555 on 2010-03-27
> Is it easy to undo the installation of those modules?Sure:```
sudo apt-get remove --purge linux-backports-modules-*
```The wildcard * removes the kernel-specific package as well as the meta package.

Post back and let us know the outcome.

---

### Post by raghav1 on 2010-03-27
Followed instruction from your last post.  The 'Enable Wireless" option is now available i.e. not greyed out.  I am now back to the original problem which is "device not ready".

---

### Post by chili555 on 2010-03-27
What does this tell us?```
dmesg | grep rt2
```Thanks.

---

### Post by raghav1 on 2010-03-27
This is what it shows

raghu@raghu-laptop:~$ dmesg | grep rt2
[   27.557176] rt2500pci 0000:00:09.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   27.784207] Registered led device: rt2500pci-phy0::radio
[   27.784232] Registered led device: rt2500pci-phy0::quality
[   28.292740] input: rt2500pci as /devices/pci0000:00/0000:00:09.0/input/input5
raghu@raghu-laptop:~$ 

Thanks.

---

### Post by chili555 on 2010-03-27
Your *dmesg* looks pretty normal. Now, how about:```
rfkill list
```What kind of laptop is it?

---

### Post by raghav1 on 2010-03-27
I have a Winbook.  4 years old.  I installed ubuntu to extend its life.  My wireless worked fine with the earlier version of ubuntu.  It stopped working on this new version Karmic Koala.

raghu@raghu-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
raghu@raghu-laptop:~$ 

Thanks again.

---

### Post by apotts on 2010-03-27
> **chili555 said:**
> Sure:```
sudo apt-get remove --purge linux-backports-modules-*
```The wildcard * removes the kernel-specific package as well as the meta package.

Post back and let us know the outcome.

Thanks - that reverted the laptop to its previous behaviour. Wireless now connects fine after *rfkill unblock all*, but there is no routing.

---

### Post by chili555 on 2010-03-27
> Wireless now connects fine after rfkill unblock all, but there is no routing.Very, very weird! I'd love to find a new, rational driver for this. May I see:```
lspci -nn
```Feel free to strip away everything that is not related to your Realtek.

Weird.

---

### Post by apotts on 2010-03-28
```
andrew@andrew-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 645xx [1039:0648] (rev 51)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 14)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.3 FireWire (IEEE 1394) [0c00]: Silicon Integrated Systems [SiS] FireWire Controller [1039:7007]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
00:0c.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]

```

I have been watching my router's syslog when the wireless is active. Oddly, there are DNS requests appearing. When you ping an ip there is nothing, but if you ping or traceroute or open a web address that is in the form of a URL, then the DNS request and response is being seen and sent by the router. But not received by the laptop.

---

### Post by chili555 on 2010-03-28
I wonder if the fault is actually in the router. Network Address Translation, etc. Do other computers work well attached to it? May I assume your ethernet is attached and works fine?

I wonder if it would make any difference if you used a static IP address. Please try System > Preferences > Network Connections, select Wireless and Edit IPv4 settings and put in a likely address, netmask, etc. Also, make sure IPv6 is set to Ignore.

Please see attached.

---

### Post by apotts on 2010-03-28
No, there is nothing wrong with the router. It works perfectly here with 3 PCs, 2 laptops, a squeezebox, 3 servers (win2k3, WHS and ubuntu), PS3, Humax, Topfield, iPhone and an HTC Android phone. ;) It also works perfectly with the ubuntu laptop in question with the wired connection (no fiddling around, just P&P with DHCP and off it went). It's just the ubuntu wireless that is fubar in this case.

I have already tried a static address and no wireless security. IPv6 has always been set to "ignore".

---

### Post by chili555 on 2010-03-28
> 3 PCs, 2 laptops, a squeezebox, 3 servers (win2k3, WHS and ubuntu), PS3, Humax, Topfield, iPhone and an HTC Android phone.That's all??!!

Please post:```
lsusb
```Also, please try:```
sudo rmmod -f rt2500usb
sudo modprobe rt2500usb nohwcrypt=1
```Any improvements?

---

### Post by apotts on 2010-03-28
Like so:

```
andrew@andrew-laptop:~$ sudo rfkill unblock all
[sudo] password for andrew: 
andrew@andrew-laptop:~$ lsusb
Bus 002 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0db0:6865 Micro Star International RT2570
Bus 001 Device 002: ID 07c4:a600 Datafab Systems, Inc. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
andrew@andrew-laptop:~$ sudo rmmod -f rt2500usb
andrew@andrew-laptop:~$ sudo modprobe rt2500usb nohwcrypt=1
andrew@andrew-laptop:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
andrew@andrew-laptop:~$ rfkill unblock all
andrew@andrew-laptop:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
andrew@andrew-laptop:~$ 

```

Sadly this has reduced the state back to square 0 (no ability to enable wireless by unblocking the soft block, so just "device not ready").

---

### Post by chili555 on 2010-03-28
This is maddening...and it isn't even my wireless! Please try:```
sudo su
echo 1 > /sys/class/rfkill/rfkill1/state
exit
rfkill list
```Is it still soft blocked? If you try to connect...dare I say it...do you have any success? If you try and fail, does it flip back to soft blocked again?

---

### Post by apotts on 2010-03-28
Chili555,

You are being so patient! I'm getting the feeling that support for this Ralink is just not there though...

Here's the whole process using those different modules. I always have to start by unblocking, then I do your mods, then I have to unblock again and initialise the adapter. Now NM tries to connect (twirling graphic and keeps asking for my WPA password). Eventually gives in:

```
andrew@andrew-laptop:~$ rfkill unblock all
andrew@andrew-laptop:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
^C
--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

andrew@andrew-laptop:~$ sudo rmmod -f rt2500usb
[sudo] password for andrew: 
andrew@andrew-laptop:~$ sudo modprobe rt2500usb nohwcrypt=1
andrew@andrew-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
andrew@andrew-laptop:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
andrew@andrew-laptop:~$ rfkill unblock all
andrew@andrew-laptop:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
andrew@andrew-laptop:~$ sudo ifconfig wlan0 up
andrew@andrew-laptop:~$ 
```

Here's your requested code (there's no issue with blocking here):

```

andrew@andrew-laptop:~$ sudo su
root@andrew-laptop:/home/andrew# echo 1 > /sys/class/rfkill/rfkill1/state
root@andrew-laptop:/home/andrew# exit
exit
andrew@andrew-laptop:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
andrew@andrew-laptop:~$ 



```

The closest I can get is:
Boot
Unblock
NM connects correctly.
No ping (but router sees DNS requests).

It can't be the hardware, because it all connects beautifully with WinXP. :rolleyes:

---

### Post by chili555 on 2010-03-28
You are quite correct that it's probably not the hardware; I suspect it's the driver. I have been reading quite a bit about it. I have been trying to find out if there is another newer driver available; evidently not.

I tried compiling the package rt2570-source and found no joy. I gather that there is some trick to turning the device on and keeping it on but I haven't discovered it.

Frankly, I am stuck. I am left with only two more suggestions. First, find the .inf and .sys files on your Windows partition and move them to Ubuntu and try ndiswrapper.

Otherwise, send it to me and I'll put it under the rear wheels of my truck! (read: get a different device.)

I wish I could find the answer; I hate being stuck. I hate when I wake up at 3:30am thinking 'rt2500.'

---

### Post by wherearethee on 2010-12-22
I think I have both found the problem and it's solution - the problem is rather stupid, and thus the solution rather simple ....

The problem is that ubuntu loads the wrong module. In my case, it loads both the rt2500usb and the rt73usb modules, with the effect that two wireless devices appear. Well - one of those is not compatible with the device, and "reads" a permanent "on" for the kill switch.

For me this  - ridiculously simple - solution works excellent. The incompatible driver is the rt2500usb, so:

```
 echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist.conf
```And, either restart, or remove that driver with:

```
rmmod rt2500usb
```If the rt73usb driver was already loaded, suddenly and out of nowhere NetworkManager lists the available APs .... and you may even connect

If not, load it:

```
modprobe rt73usb
```Hope this solution is not too simple to be true ;-)
Good luck!

---

