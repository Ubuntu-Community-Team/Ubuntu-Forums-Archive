---
title: "Ethernet and Wireless Internet Slow on Presario c700 and Ubuntu 11.10"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by minicranium on 2012-02-19
Hello Everyone,

 I am a new Ubuntu user. I decided to put new life into a new laptop and installed Ubuntu 11.10 onto it. It seems that I now have a very very slow internet connection on both my Ethernet and Wireless cards. I have tried to install different versions of Ubuntu, including 10.10 and 11.04 and have the same problem. I have tried these versions on another laptop (different brand) and have not had any problems with it there. I was hoping you guys could help me:

Laptop:
Compaq Presario c700 with 2g RAM, Windows Vista

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

I should note that I have no problems when I use Vista, with normal speeds and such, but only in Ubuntu. Please help as I plan to use Ubuntu as my main operating system for this laptop. 

All help is appreciated.

Thank you.

---

### Post by roelforg on 2012-02-20
No worry's,
I was once new too (although my profile says different, i've been using ubuntu for years, just wanted to contribute to the community and made an account here, the join date is about 3-4 years off from when i started using ubuntu).

But i need more info;
Type the following in your terminal:
```

sudo bash
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lshw -C network

```Note: PM me if you've posted, i'm bad at following threads so an PM alerts me to look at one (though post the results from the commands to the thread so other can check it out as well). Feel free to PM me for other questions, i believe asking is better than failing and that it's better to ask a lot than a little.

---

### Post by minicranium on 2012-02-20
> **roelforg said:**
> No worry's,
I was once new too (although my profile says different, i've been using ubuntu for years, just wanted to contribute to the community and made an account here, the join date is about 3-4 years off from when i started using ubuntu).

But i need more info;
Type the following in your terminal:
```

sudo bash
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lshw -C network

```Note: PM me if you've posted, i'm bad at following threads so an PM alerts me to look at one (though post the results from the commands to the thread so other can check it out as well). Feel free to PM me for other questions, i believe asking is better than failing and that it's better to ask a lot than a little.

Thank you for your help here is the further info you requested:

```
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:5a:3c:87:7c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2806 errors:87 dropped:169 overruns:87 frame:0
          TX packets:3011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2095033 (2.0 MB)  TX bytes:533030 (533.0 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:88:ad:a5  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95470 (95.4 KB)  TX bytes:4191 (4.1 KB)


```


```
cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

```
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1
search home
```

```
lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:88:ad:a5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:91300000-91300fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:23:5a:3c:87:7c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.6 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff
```

I hope that helps. I should note that at the moment I have my wireless turned off since I am using the ethernet card for the moment. If you need the info with the wirless card on, please let me know.

---

### Post by roelforg on 2012-02-21
The error and drop count should be 0,
this can be either a bad cable somewhere down the line or the use of a hub.
Please try your cables with a different pc or try using a new cable and a different port on your switch/router/hub.
Cables can go bad when you pull to hard, they get stuck between doors,  you step on them, etc.
When cables go bad, they corrupts packets causing your NIC to either drop them or say they're corrupted and ignore them.
Once had that, speed's went down by 10fold because my router had to keep resending packets until one got through, a new 5 buck cable did the trick.

FYI, Wireless isn't my best side (never used it on my pc's); i'll see what i can do.
Try putting your (presumably) laptop next to the Wireless AP (router), you'd be amazed, my phone won't work over WiFi in 1 spot, 10 cm to the left, full speed, the location  is the trick.
Walls, doors, floors are all bad for WiFi Signals.

---

### Post by roelforg on 2012-02-21
My ifconfig looks like this:
```

eth0      Link encap:Ethernet  HWaddr 00:50:8b:6c:be:f7  
          inet addr:192.168.0.115  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8bff:fe6c:bef7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71590850 (71.5 MB)  TX bytes:63060708 (63.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:50:fc:a3:e2:42  
          inet addr:192.168.2.1  Bcast:192.168.2.254  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fea3:e242/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15213 (15.2 KB)
          Interrupt:18 Base address:0x1000 

eth2      Link encap:Ethernet  HWaddr 00:0b:cd:09:e4:e0  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe09:e4e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46545 (46.5 KB)  TX bytes:7131 (7.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3688 (3.6 KB)  TX bytes:3688 (3.6 KB)

```
You can ignore ETH1 on mine, it runs a different subnet, i've got a linux cluster on that one, my pc is main and the cluster switch is on eth1, my pc doubles as workstation,router,dhcpserver,tftpserver,pxeboot,nfsroot,etc. This leaves a rather odd setup, but setting up odd network configs is a real learning experience.
More important, see that my error and dropped counts are 0?
That means data goes to/from my pc without problems.
When you use a hub (like a friend of mine) those dropped counts go up.
But the error counts should stay low!
Try reading this: [http://nl.wikipedia.org/wiki/Hub_%28computernetwerk%29](http://nl.wikipedia.org/wiki/Hub_%28computernetwerk%29)
I know its in dutch, my point is mostly regarding the second picture, left is with a hub, right is with a switch;
note that the hub repeats the packets over every port, causing high "dropped" in ifconfig because the NIC ignores the packets not for your pc.
Errors occur when there are malformed packets arriving.
Both problems cause slow nets.

My TX/RX is big because i was transferring photo's from my phone (via wifi->router->switch->pc) to my home server.

---

### Post by roelforg on 2012-02-21
Before i forget, you've gotta pm me after the post.

---

### Post by minicranium on 2012-02-24
I have tried to change the cable, change the position on the router, but it still seems to have the same problem. I don't know what else to do for this. I have tried other Linux distros including older versions of Ubuntu (even 10), OpenSUSE, Linux MINT all to no avail. 

So I wonder, could it be:
1) A driver problem for both the ethernet and wireless card?
2) The Network Device Manager, maybe switching to the WICD program?

I have also tried the same cable and router position on another laptop running Ubuntu 11.04 and 11.10 and have not had problems with that laptop (granted it is a different ethernet card but does seem to eliminate the router/modem/cable).

Any help will be appreciated.

---

### Post by roelforg on 2012-02-24
> **minicranium said:**
> I have tried to change the cable, change the position on the router, but it still seems to have the same problem. I don't know what else to do for this. I have tried other Linux distros including older versions of Ubuntu (even 10), OpenSUSE, Linux MINT all to no avail. 

So I wonder, could it be:
1) A driver problem for both the ethernet and wireless card?
2) The Network Device Manager, maybe switching to the WICD program?

I have also tried the same cable and router position on another laptop running Ubuntu 11.04 and 11.10 and have not had problems with that laptop (granted it is a different ethernet card but does seem to eliminate the router/modem/cable).

Any help will be appreciated.
1) Could be. Is it a desktop/tower pc? If so, try using a (different) pci ethernet card.
2) Wouldn't know, i run Ubuntu Server opon which i added LXDE, and all my progs (no *buntu-desktop packages) and still use /etc/network/interfaces /etc/resolv.conf and other config files to configure the system.

---

### Post by minicranium on 2012-02-24
> **roelforg said:**
> 1) Could be. Is it a desktop/tower pc? If so, try using a (different) pci ethernet card.
2) Wouldn't know, i run Ubuntu Server opon which i added LXDE, and all my progs (no *buntu-desktop packages) and still use /etc/network/interfaces /etc/resolv.conf and other config files to configure the system.
It is a laptop pc. So switching out the PCI ethernet card won't work. I will try to reinstall the drivers and see how that goes.

---

### Post by roelforg on 2012-02-24
> **minicranium said:**
> It is a laptop pc. So switching out the PCI ethernet card won't work. I will try to reinstall the drivers and see how that goes.
Yeah, laptops+Linux usually are a recipe for network problems.

---

### Post by minicranium on 2012-02-24
I did have another question. When I type in lsmod, after reading in different forums, I got this:


```
lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          28358  2 
arc4                   12473  2 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
iwl3945                73401  0 
i915                  509554  3 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
iwl_legacy             71499  1 iwl3945
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32889  1 i915
hp_wmi                 13652  0 
mac80211              393421  2 iwl3945,iwl_legacy
psmouse                63474  0 
sparse_keymap          13658  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
drm                   196290  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
cfg80211              172427  3 iwl3945,iwl_legacy,mac80211
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
8139too                23283  0 
uas                    17699  0 
8139cp                 26762  0 
ahci                   21634  1 
libahci                25761  1 ahci
```

Now at the bottom where it states "8139too" and "8139cp" it doesn't state that it is being used (with showing a 0 instead of a 1) when the cable is plugged in. Could this be a problem? Especially if this is supposed to be the driver in use as shown from this code?


```
lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:135b]
	Kernel driver in use: iwl3945
--
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Kernel driver in use: 8139too
```

---

### Post by roelforg on 2012-02-25
> **minicranium said:**
> I did have another question. When I type in lsmod, after reading in different forums, I got this:


```
lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          28358  2 
arc4                   12473  2 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
iwl3945                73401  0 
i915                  509554  3 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
iwl_legacy             71499  1 iwl3945
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32889  1 i915
hp_wmi                 13652  0 
mac80211              393421  2 iwl3945,iwl_legacy
psmouse                63474  0 
sparse_keymap          13658  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
drm                   196290  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
cfg80211              172427  3 iwl3945,iwl_legacy,mac80211
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
8139too                23283  0 
uas                    17699  0 
8139cp                 26762  0 
ahci                   21634  1 
libahci                25761  1 ahci
```Now at the bottom where it states "8139too" and "8139cp" it doesn't state that it is being used (with showing a 0 instead of a 1) when the cable is plugged in. Could this be a problem? Especially if this is supposed to be the driver in use as shown from this code?


```
lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]
    Kernel driver in use: iwl3945
--
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
    Kernel driver in use: 8139too
```
Nah, one of my 3 NICS has the same chipset and uses that exact driver, works fine.

I just had a good sleep and feel really sharp, so i decided to go over the whole thread again.
Then i spotted something that changes the odds.

The WNIC (Wired NIC) has a connection speed of 100mb/s like it's supposed.
Could you check if a different computer shows the same netspeed problem?

---

### Post by minicranium on 2012-02-25
Hi have checked my connection with my desktop which also has Ubuntu installed (with no problems). Here is the code from sudo lshw -C network from my desktop:


```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 90:e6:ba:14:31:ea
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff
```

It also lists the speed at 100Mbit/s.

A new update to my presario is that I have gotten the wireless to work. As to how, I am unsure. Given that my wireless card is an Intel card, it constantly blinks when connecting to a network or receiving packages. So I was able to input a code to stop it from blinking which, amazingly, worked and got it to full speed. 

Although I am happy to have wireless work on it for now, I also wanted to see if I could get the Ethernet working, as that may be a big help. I also tried replacing the drivers last night using Ndiswrapper, old windows drivers, newer windows drivers, blacklisting 8139too, 8139cp all of which did not work at all. So I reverted everything back and re-enlisted the 8139too driver with the same result. 

I know some people would be happy with just the wireless, but I am a little picky that way :D and want to have my entire system work. Plus it is a great way for me to learn about Ubuntu... 

Thanks for your help

---

### Post by roelforg on 2012-02-26
> **minicranium said:**
> Hi have checked my connection with my desktop which also has Ubuntu installed (with no problems). Here is the code from sudo lshw -C network from my desktop:


```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 90:e6:ba:14:31:ea
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff
```It also lists the speed at 100Mbit/s.

A new update to my presario is that I have gotten the wireless to work. As to how, I am unsure. Given that my wireless card is an Intel card, it constantly blinks when connecting to a network or receiving packages. So I was able to input a code to stop it from blinking which, amazingly, worked and got it to full speed. 

Although I am happy to have wireless work on it for now, I also wanted to see if I could get the Ethernet working, as that may be a big help. I also tried replacing the drivers last night using Ndiswrapper, old windows drivers, newer windows drivers, blacklisting 8139too, 8139cp all of which did not work at all. So I reverted everything back and re-enlisted the 8139too driver with the same result. 

I know some people would be happy with just the wireless, but I am a little picky that way :D and want to have my entire system work. Plus it is a great way for me to learn about Ubuntu... 

Thanks for your help
The only thing your desktop shows is that  you've got a standard household router/switch.
If you want full speed from the gigabit card in the pc, think about a gigabit switch. (Those don't have to be expensive)

I don't think the drivers are the problem (i use the same ones and have full speed!).
I really don't know what could cause the wired problem (at least the wlan now works).

---

