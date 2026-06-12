---
title: "DWA-140/Wireless USB network adapter"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by Vielard on 2010-12-05
Ok, so I'm fresh to linux, and everything runs quite smoot, everything except the wireless internet connection...

I can see the networks around me, but I cannot connect to any of them (not even open ones).

It tries, for a while, then gives up.


I'd be really happy to get some help, and I'll give you any info you might need upon request (could be a good idea to tell me how to collect the requested information).



**Relevant information:**

*Linux ubuntu 2.6.32-26-generic*

lsusb: > 
ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]


-------------------------------------------------
Vielard Venets

---

### Post by northd_tech on 2010-12-05
Hi Vielard,

Will you run the following terminal command and post the output here:

```
sudo apt-get install wireless-tools
```

Also can you post the output from the following terminal commands:

```
lspci
lsmod
lshw -C network
ifconfig
iwconfig
```

I did find a HOWTO about the Ralink 2870 (but it's a little long and somewhat involved and might be old-ish information):

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

Let's see if there is an easier or quicker fix with the newer 10.xx ubuntu versions.

---

### Post by TBABill on 2010-12-05
Edit blacklist.conf as follows ```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add the following lines to the end of the file, then reboot:
```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```

Save and restart

---

### Post by Vielard on 2010-12-06
Thanks alot to the both of you..!
I will try this out right away, and post you the feedback here! :)

---

### Post by Vielard on 2010-12-06
Ok, so I tried the blacklist thing, and now I can see my WPA2 network, so that's good... however, still no luck in connecting to any network (not even open ones), so here ... the info requested..


Code:
sudo apt-get install wireless-tools
> 
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
wireless-tools er allerede nyeste versjon.
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 0 ikke oppgradert.

--------------------------
(translated freely: )
Reading list of packages ... Done
Making an overview of dependency circumstances
Reading conditioninformation ... Done   
wireless-tools allready newest version.
0 uppdated, 0 newly installed, 0 to remove and 0 not updated.




Code:
lspci
> 
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
07:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
07:06.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)



Code:
lsmod
> 
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  1 
usb_storage            49961  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_ens1371            23110  2 
gameport               10966  1 snd_ens1371
snd_ac97_codec        125394  1 snd_ens1371
ac97_bus                1450  1 snd_ac97_codec
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  5 snd_ens1371,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11072  0 
snd                    71251  22 snd_hda_codec_realtek,snd_ens1371,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      9336  0 
nvidia               8096262  24 
ohci1394               30260  0 
rt2870sta             525366  1 
intel_agp              29319  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
vgastate                9857  1 vga16fb
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83472  1 usbhid
ieee1394               94771  1 ohci1394
r8169                  39682  0 
mii                     5237  1 r8169
ahci                   37870  0 
pata_jmicron            2747  0 
sata_sil24             12903  0 
floppy                 63156  0 



Code:
lshw -C network
> 
*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:f0:9a:34:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless



Code:
ifconfig
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:370990 (370.9 KB)  TX bytes:370990 (370.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:9a:34:cc  
          inet6 addr: fe80::21c:f0ff:fe9a:34cc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:49572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1276 error:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5388601 (5.3 MB)  TX bytes:92912 (92.9 KB)


Code:
iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"Ole"  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr: off   Fragment thr: off  [COLOR="Red"](<----- NOTE: I made spaces between the ":" and the "o" to avoid making :o )[/COLOR]  
          Link Quality=100/100  Signal level:-53 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Hope you can help me with this, I really do :)
Thanks for your time so far! :)

---

### Post by TBABill on 2010-12-07
Ok, can you try ```
sudo gedit /etc/modules
``` and add ```
rt2870sta
``` to the end of the file, then save?
 
Then, in order to not have to restart, ```
[SIZE=2]sudo modprobe rt2870sta
``` then ```
[/SIZE][SIZE=2]sudo /etc/init.d/networking restart
``` and post back if it works or not.[/SIZE]

---

### Post by Vielard on 2010-12-07
> **TBABill said:**
> [SIZE=2]post back if it works or not.[/SIZE]

So I tried to do as listed above, and the results were the same.

As always - I tried to change my network to WEP instead of WPA2, just to be sure, and I saw the animation of the wireless-icon change just slightly..

A few seconds later, I was connected, and I am currently using my Linux to reply you..!

So thanks allot..! 
Good to see there's always a few helpful souls out there :)


Again, thank you!
:D

---

### Post by TBABill on 2010-12-07
Anytime!! Just keep a note of those tweaks in case you upgrade, hose your install, etc. and need to reinstall the system. Never know when you may need it :)

---

### Post by Vielard on 2010-12-09
> **TBABill said:**
> Anytime!! Just keep a note of those tweaks in case you upgrade, hose your install, etc. and need to reinstall the system. Never know when you may need it :)



I will do that :)
Thanks alot! :)

---

