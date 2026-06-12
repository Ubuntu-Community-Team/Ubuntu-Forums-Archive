---
title: "Intel 3945ABG / Ubuntu 9.10 / Hasee L720T"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by jiapei100 on 2009-11-02
After installing "linux-backports-modules-karmic-generic-pae", finally, I obtained the following:
but still, "iwlist scan" won't find anything !!!!

1) Machine Brand and Model (PC/Laptop):

2) lspci
```
jiapei@jiapei-laptop:~$ lspci -nn | grep 'Wireless'
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

3) ifconfig and iwconfig
```

jiapei@jiapei-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:a9:19:ff
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fea9:19ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1837624 (1.8 MB)  TX bytes:312645 (312.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:7c:1b:71
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jiapei@jiapei-laptop:~$ iwconfig
jiapei@jiapei-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Managed  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

jiapei@jiapei-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  Mode:Managed  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


```

4)  lsmod
```

jiapei@jiapei-laptop:~$ lsmod                                          
Module                  Size  Used by                                  
binfmt_misc             8356  1                                        
ppdev                   6688  0                                        
snd_hda_codec_realtek   203328  1                                      
snd_hda_intel          26984  2                                        
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel    
snd_hwdep               7200  1 snd_hda_codec                          
snd_pcm_oss            37920  0                                        
snd_mixer_oss          16028  1 snd_pcm_oss                            
snd_pcm                75488  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0                                        
arc4                    1660  2                                        
snd_seq_oss            28576  0                                        
snd_seq_midi            6432  0                                        
snd_rawmidi            22208  1 snd_seq_midi                           
ecb                     2524  2                                        
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi               
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                71484  0
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 10272  0
iwlcore               114432  1 iwl3945
iptable_filter          3100  0
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              210504  2 iwl3945,iwlcore
sdhci_pci               7132  0
soundcore               7264  1 snd
sdhci                  17632  1 sdhci_pci
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
psmouse                56180  0
led_class               4096  3 iwl3945,iwlcore,sdhci
ip_tables              11692  1 iptable_filter
cfg80211              130536  3 iwl3945,iwlcore,mac80211
serio_raw               5280  0
lp                      8964  0
x_tables               16544  1 ip_tables
parport                35340  2 ppdev,lp
usbhid                 38304  0
e100                   32772  0
mii                     5212  1 e100
ohci1394               30220  0
video                  19380  0
output                  2780  1 video
ieee1394               86628  1 ohci1394
radeon                636576  2
ttm                    36308  1 radeon
drm                   160224  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27748  0
agpgart                35020  3 ttm,drm,intel_agp

jiapei@jiapei-laptop:~$ lsmod | grep iwl3945
iwl3945                71484  0
iwlcore               114432  1 iwl3945
mac80211              210504  2 iwl3945,iwlcore
led_class               4096  3 iwl3945,iwlcore,sdhci
cfg80211              130536  3 iwl3945,iwlcore,mac80211
jiapei@jiapei-laptop:~$ lsmod | grep wlan    ----  [COLOR="Red"]**nothing here**[/COLOR]
jiapei@jiapei-laptop:~$



```

5) dmesg
```

jiapei@jiapei-laptop:~$ dmesg | grep iwl3945
[   11.575677] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   11.575681] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   11.575752] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.575767] iwl3945 0000:03:00.0: setting latency timer to 64
[   11.647034] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   11.647038] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.647190] iwl3945 0000:03:00.0: irq 29 for MSI/MSI-X
[   19.725182] iwl3945 0000:03:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   19.972848] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

```

6) sudo lshw -C network
```

jiapei@jiapei-laptop:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:7c:1b:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:aa100000-aa100fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:09:08.0
       logical name: eth0
       version: 02
       serial: 00:40:d0:a9:19:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.4 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:a4000000-a4000fff ioport:1200(size=64)

```

7) iwlist scan
```

jiapei@jiapei-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

8) lsb_release -d
```

jiapei@jiapei-laptop:~$ lsb_release -d
Description:    Ubuntu 9.10

```

9) uname -mr
```

jiapei@jiapei-laptop:~$ uname -mr
2.6.31-14-generic-pae i686

```

10) sudo /etc/init.d/networking restart
```

jiapei@jiapei-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           [ OK ]

```


11) In addition:
```

jiapei@jiapei-laptop:~/Tools/IDEs$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```



Please can anybody help?

Best Regards
JIA

---

### Post by jiapei100 on 2009-11-03
It looks that 

module wl has not been successfully loaded.


```

jiapei@jiapei-laptop:~$ sudo modprobe wl
[sudo] password for jiapei:
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting wl (/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```


Please, can anybody help?

Cheers
JIA

---

### Post by posmobin on 2009-11-04
Please let me know if you get things working.  I'm also having problems with the 3945ABG with ubuntustudio 9.10.  

Currently, I am able to successfully scan for networks, but I can't connect to my wireless network.  This was after unloading iwl3945 and using ndiswrapper with a driver from hp.com (net39x5 I think).

---

### Post by jiapei100 on 2009-11-04
Hi, lucky you !!

I'm not able to scan the wireless at all !!!! So depressed...
How can I scan the wireless networks?

:S

> **posmobin said:**
> Please let me know if you get things working.  I'm also having problems with the 3945ABG with ubuntustudio 9.10.  

Currently, I am able to successfully scan for networks, but I can't connect to my wireless network.  This was after unloading iwl3945 and using ndiswrapper with a driver from hp.com (net39x5 I think).

---

### Post by posmobin on 2009-11-05
I just got my wireless working, but as I mentioned, I'm very new to Linux, so I'm not sure how helpful I can be to you.

As I mentioned, I was having problems with the default driver, so I used ndiswrapper to use the WinXP version of the driver from my laptop's manufacturer's website.  This didn't end up solving the problem for me, but if you want to try ti out, see the documentation here:
[http://www.mepis.org/docs/en/index.php/Using_Ndiswrapper](http://www.mepis.org/docs/en/index.php/Using_Ndiswrapper)

After that I was able to scan for networks in the Network Settings and using "iwlist wlan0 scan", but I still wasn't able to connect to anything.

Next thing I tried was installing the Wicd Network Manager:
sudo apt-get install wicd
After installing I could use wicd to scan and see all my networks, but when I tried to connect, it would fail when trying to obtain an IP address.

After unsuccessfully trying to get that to work for a while, I decided to revert to the default driver by removing ndiswrapper and un-blacklisting iwl3945 to back to the default driver.  After doing that and rebooting, I was able to connect to my wireless network using Wicd Network Manager.

I'm not sure how useful any of that is to your situation, but those are some of the steps I had to go through to get mine working.  Definitely give wicd a chance if you haven't already.

---

### Post by pdah on 2009-11-08
Just want to know if anybody had solved this issue ?
I'm still having problem with my wireless connection after upgrading to Ubuntu 9.10.
It can scan for wireless networks but cannot connect at all.
Checking /var/log/messages, I can see a lot of messages like this : 
```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Information from my system:
```

$ lspci | grep Wireless
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

```

$ lsmod | grep 3945
iwl3945                77212  0 
iwlcore               112508  1 iwl3945
mac80211              181236  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
cfg80211               93052  3 iwl3945,iwlcore,mac80211

```

---

### Post by mcooke1 on 2009-11-08
I have Itel 3945ABG in my Dell laptop and with 9.04 it would connect OK but disconnect randomly then after installing 9.10 the wireless was disabled and I searched the forum and this was what I found, Use Synaptic Package Manager, remove Network Manager  and at the same time install WICD then reboot.

---

### Post by pdah on 2009-11-08
@mcooke1: I had used wicd for a year and it worked without any problems until I upgrade to Ubuntu 9.10
here are some lines I got when tailing /var/log/messages 
```

Nov  8 15:46:22 localhost kernel: [ 5771.410133] Registered led device: iwl-phy0::radio
Nov  8 15:46:22 localhost kernel: [ 5771.410227] Registered led device: iwl-phy0::assoc
Nov  8 15:46:22 localhost kernel: [ 5771.410273] Registered led device: iwl-phy0::RX
Nov  8 15:46:22 localhost kernel: [ 5771.410317] Registered led device: iwl-phy0::TX
Nov  8 15:46:22 localhost kernel: [ 5771.428960] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by irishbreakfast on 2009-11-08
I have the same card, product: PRO/Wireless 3945ABG [Golan] Network Connection, at is has worked perfectly in 9.10 on a clean install without any extra modifications. did you check your 9.10 before installing?

However, under 8.04 and 9.04 I had some issues and found that using wicd was more helpful that the NetworkManager Applet.

I wish I could help with the scan...

---

### Post by mcooke1 on 2009-11-08
> **pdah said:**
> @mcooke1: I had used wicd for a year and it worked without any problems until I upgrade to Ubuntu 9.10
here are some lines I got when tailing /var/log/messages 
```

Nov  8 15:46:22 localhost kernel: [ 5771.410133] Registered led device: iwl-phy0::radio
Nov  8 15:46:22 localhost kernel: [ 5771.410227] Registered led device: iwl-phy0::assoc
Nov  8 15:46:22 localhost kernel: [ 5771.410273] Registered led device: iwl-phy0::RX
Nov  8 15:46:22 localhost kernel: [ 5771.410317] Registered led device: iwl-phy0::TX
Nov  8 15:46:22 localhost kernel: [ 5771.428960] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```


Sorry I can not help anymore I can only show you what worked for me and some other people.

---

### Post by pdah on 2009-11-08
Hi, good news is that I made it works now.
So for those who can scan the list of wireless networks but cannot connect to any of them, just try to install **linux-backports-modules-karmic** package and re-install **wicd**

---

