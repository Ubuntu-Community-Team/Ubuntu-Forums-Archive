---
title: "Wireless Network Issues : Cannot Join Network"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by erkerb on 2010-11-25
Hello Guys,

I have been a long time viewer of the forums. I have been able to resolve %95 of the issues with the help of forums, but i am having hard time defeating this problem. I have recently upgraded from 9.10, to 10.10. I have been using 9.10 with my current setup for the past year without issues. I decided to do a clean install with 10.10 but encountered the following network issue...

My Wireless NIC (Intel Advanced N 6200) seems to be recognised by the OS, however it is having hard time joining to my network. It is perfectly seeing all the networks around my area without an issue, but when it comes to joining the network it isn't doing anything. I have a Netgear WNDR3700 router with DD-WRT(Build 15506) installed. I have 2 SSID's, one for 2.4 and the other for 5GHz band. Whenever i try to join the network it asks for password. After providing the password, it tries to join the network but it prompts for password again after few moments. I have monitored my router to see if there was any activity, but i found out that, it does not even request an IP from DHCP.

Then i tried plugging in to the router directly. Even the wired connection couldn't get an IP address. I went to the network settings, and manually set the IP address, to get the system to go online. I have updated the OS, got the latest kernel installed. I tried again with the Wireless, but nothing changed.

I have a Dell Mini 1010. The only thing i have added was the network card, which is the Intel Advanced N 6200. 

I have looked around the the forums and was not able to come up with anything that was helpful. So, i wanted to ask you guys for help on debugging this issue. Here are some outputs that might be helpful:

> 
erkerb@HellSyMiniU:~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
> erkerb@HellSyMiniU:~$ sudo lsusb
[sudo] password for erkerb: 
Bus 004 Device 002: ID 413c:9500 Dell Computer Corp. USB CP210x UART Bridge Controller [DW700]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 064e:a129 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
> erkerb@HellSyMiniU:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:9a:18:f9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.25 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:40 ioport:2000(size=256) memory:d8410000-d8410fff memory:d8400000-d840ffff memory:d8420000-d843ffff
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:44:1f:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-23-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:41 memory:d8000000-d8001fff
> 
erkerb@HellSyMiniU:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off> 
erkerb@HellSyMiniU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:9a:18:f9  
          inet addr:192.168.1.25  Bcast:192.168.1.31  Mask:255.255.255.224
          inet6 addr: fe80::224:e8ff:fe9a:18f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88085654 (88.0 MB)  TX bytes:2332225 (2.3 MB)
          Interrupt:40 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:14:44:1f:10  
          inet6 addr: fe80::223:14ff:fe44:1f10/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22882 (22.8 KB)  TX bytes:34952 (34.9 KB)> erkerb@HellSyMiniU:~$ lsmod
Module                  Size  Used by
aes_i586                7280  104 
aes_generic            26875  1 aes_i586
psb                   147580  3 
drm_psb               178811  4 psb
agpgart                32011  1 drm_psb
i2c_algo_bit            5168  1 psb
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_realtek   217971  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
iwlagn                178948  0 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
joydev                  8735  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
iwlcore               127415  1 iwlagn
snd_rawmidi            17783  1 snd_seq_midi
mac80211              231541  2 iwlagn,iwlcore
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
btusb                  10969  2 
cp210x                 11206  0 
dell_laptop             5730  0 
cfg80211              144470  3 iwlagn,iwlcore,mac80211
compal_laptop           2078  0 
i2c_isch                3086  0 
usbserial              33100  1 cp210x
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
dcdbas                  5402  1 dell_laptop
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lpc_sch                 1761  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
uvesafb                22649  1 
usb_storage            40172  0 
r8169                  36489  0 
video                  18712  0 
pata_sch                1975  2 
output                  1883  1 video
mii                     4425  1 r8169
Output of [B]/etc/modprobe.d/blacklist.conf
[/B]> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edacThank you..

---

### Post by erkerb on 2010-11-26
Any guesses?

---

### Post by wet-willy on 2010-11-26
> Whenever i try to join the network it asks for password. After providing the password, it tries to join the network but it prompts for password again after few moments.
Whenever you join a new encrypted wireless network with Ubuntu you are asked to input the key, then you are asked for your keyring password which when input, you won't be prompted for the keyring password next time you join in, when you cancel, your child cannot join in without the password when he/she uses the unit later on, they will be prompted to input the proper keyring password, but you should still get connected with proper credentials after hitting cancel at the keyring password promp.

My guess:
Your card is working according to the ifconfig output, just a matter of security at a currently undetermined level. 
As for having to configure the NIC manually, I'm guessing that is either a hardware specific feature when joining the first time and/or administration settings. I have to do this with most new Windows installations whenever using a relatives business network for the high speed to do updates and such. I'll configure TCIP/SOMETHING properties to manually use an IP, after it's connected, I switch back to DHCP and it gets assigned an IP as well as after reboot.

```
Intel® Centrino® Advanced-N 6200 Technical Specifications
General
Dimensions (H x W x D) 26.80 mm x 30.00 mm x 2.4 mm Max (Top Side) / 1.35 mm Max (Bottom Side)
Weight 4.0 g
Diversity On-board diversity support for systems designed with two antennas
Radio ON/OFF Control4 Supported in both hardware and software
Connector interface Half Mini Card form factor, based on PCIe electrical interface
LED Output Single WLAN-LED (as per Mini Card specification)
Operating Temperature 0 to +60oC
Humidity Non-Operating 50% to 90% RH non-condensing (at temperatures of 25°C to 35°C)
Operating Systems:  Microsoft Windows XP* 32/64-bit, Microsoft Windows Vista* 32/64-bit, Microsoft Windows 7* 32/64-
                                         bit, [COLOR="Red"]Ubuntu Linux[/COLOR]*
Wi-Fi Alliance Wi-Fi CERTIFIED* for 802.11a, 802.11b, 802.11g, 802.11n, WMM*, WPA*, WPA2*, and WPS
Microsoft WHQL YES
IEEE WLAN Standard IEEE 802.11a/b/g/n, 802.11d, 802.11e, 802.11i, 802.11h
                  Infrastructure or ad hoc (peer-to-peer)
Architecture
Supports seamless roaming between respective access points
```

---

### Post by erkerb on 2010-11-26
It has never prompted me for keystring password. I looked around the forums and saw some suggestions to remove everything under .gnome2/keystring folder to re-initiate the keystring process... Now i can't even login..

[http://ubuntuforums.org/showpost.php?p=8899920&postcount=13](http://ubuntuforums.org/showpost.php?p=8899920&postcount=13)

---

### Post by erkerb on 2010-11-26
So i have decided to re-download Ubuntu. I downloaded the 10.10 Live version from unetbootin and created another Installation USB-Key. During the installation it saw both the Wireless networks. As soon as i tried to join one of them, it asked me to create a key string. So i created the keystring, but it was unable to join to the 5GHz band. Then i tried connecting with the  2.4GHz band. It was able to connect through the 2.4GHz radio, but not 5GHz. This is strange.. This is okay for home, but my school uses strictly 5GHz band..

Oh, when i plugged by wire, it was able to get an address from DHCP fine.. I did not have to set the ip address manually. This is very strange..

So it seems like 10.10 has some issues with 5GHz bands..
[http://ubuntuforums.org/showthread.php?p=10003872](http://ubuntuforums.org/showthread.php?p=10003872)

---

### Post by wet-willy on 2010-11-27
Upgrading seems to have many folks posting in forums. I only did it once and everything fell apart, and for the amount of time it takes to acquire the newer version and get it up and running compared to the time involved in doing a dist-upgrade (including the time spent in forums looking for answers), I don't see the point...
Keep in mind this distribution you have now is a somewhat bleeding edge development operating system, if you BUG maintainers, it might get resolved soon enough. If nobody complains, there are more than likely other more "pressing" issues on the table.

---

### Post by erkerb on 2010-11-30
> **wet-willy said:**
> Upgrading seems to have many folks posting in forums. I only did it once and everything fell apart, and for the amount of time it takes to acquire the newer version and get it up and running compared to the time involved in doing a dist-upgrade (including the time spent in forums looking for answers), I don't see the point...
Keep in mind this distribution you have now is a somewhat bleeding edge development operating system, if you BUG maintainers, it might get resolved soon enough. If nobody complains, there are more than likely other more "pressing" issues on the table.


The installation phase did not create any issues. Everything is working so far except this Wireless connectivity issue. I am aware that people are having issues, but what i wonder is if people are having issues connecting to 5GHz radios or not.. This is very annoying.

---

### Post by uncaspi on 2010-11-30
I read on the forum somewhere that 10.10 don't like mixed mode encryption.

Try WEP or WPA2

---

### Post by erkerb on 2010-11-30
> **uncaspi said:**
> I read on the forum somewhere that 10.10 don't like mixed mode encryption.

Try WEP or WPA2

I just tried both, I had my settings set to WPA2 Personal Mixed with TKIP+AES.. But the interesting thing is, this is the same spec for the 2.4GHz band, [WPA2 Personal Mixed with TKIP+AES] but it just works fine.. I tried setting the 5GHz radio to WPA2 Personal TKIP or AES, as well as WEP.. There is something fishy with this.

---

### Post by uncaspi on 2010-11-30
I think this must be a bug in 10.10.

---

### Post by erkerb on 2010-11-30
> **uncaspi said:**
> I think this must be a bug in 10.10.

I tried installing Ubuntu 10.4 over the weekend,and i encountered the same issue there. And yes, it did connect fine to 2.4GHz radio but did not connect to 5GHz radio.. I should have just lived with 9.10.. Everything was just right with that OS.. :D

---

### Post by erkerb on 2010-11-30
I appreciate all your inputs guys. Is there a way to submit this bug somehow? I would try my best to get this issue solved.

---

### Post by uncaspi on 2010-11-30
You can report a bug here

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)


And if you got any closer to the problem, please mark tis thread as solved . See thread tools.

---

### Post by erkerb on 2010-12-01
I did some digging around.. I have left a very important detail out.. The 5GHz radio was set to N-network only..I looked around all the bugs and noticed that 10.04 and 10.10 has a nasty bug with N Networks.. Hopefully it will be sorted out.. :(

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748)

---

