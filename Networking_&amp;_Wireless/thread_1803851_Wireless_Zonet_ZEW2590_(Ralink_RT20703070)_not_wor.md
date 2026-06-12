---
title: "Wireless Zonet ZEW2590 (Ralink RT2070/3070) not working"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by Develjas on 2011-07-13
Hi, I'm using Ubuntu 10.04 64-bit.

I am using the Zonet ZEW2590 USB stick for wireless, my wired connection is fine. As far as I can tell, the "card," uses either the Ralink RT2070 or Ralink RT3070 chipset.


ifconfig returns these results:

```
 

eth0 Link encap:Ethernet  HWaddr e0:cb:4e:[**REDACTED]**  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe49:4ebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20990797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11182 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:10303047 (10.3 MB)  TX bytes:1579170 (1.5 MB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10661 (10.6 KB)  TX bytes:10661 (10.6 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:[**REDACTED]**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
iwconfig returns this result:
```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


```
I have done nothing but plug the device into an empty USB-slot. 
Does anybody have an idea of what I need to do?

I tried going into the GUI network manager located at System/Preferences/Network Connections, but adding in my information into a new wireless connection doesn't allow me to do anything; after I enter in the BSSID, my wireless cards' MAC address, etc. the "apply," button isn't highlighted and I can only cancel or exit the manager.

Any help you guys will provide would be greatly appreciated. Let me know if I need to provide more information.


Thank you.

---

### Post by Develjas on 2011-07-14
Bump.


I am still unsure of what to do; as a new Linux user I hope you guys can provide some guidance for me.


Thank you.

---

### Post by wildmanne39 on 2011-07-14
> **Develjas said:**
> Bump.


I am still unsure of what to do; as a new Linux user I hope you guys can provide some guidance for me.


Thank you.Hi, run these commands in a terminal
```
lspci -nn
```
```
lsmod
```
If it is a usb wireless run this also
```
lsusb
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Develjas on 2011-07-15
Here you go, wildmanne39:


```
lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 9800 GT] [10de:0614] (rev a2)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)

``````
lsmod
Module                  Size  Used by
rt2870sta             525366  0 
arc4                    1473  2 
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238896  2 rt2x00usb,rt2x00lib
cfg80211              148341  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb
binfmt_misc             7960  1 
snd_hda_codec_via      33207  1 
ppdev                   6375  0 
parport_pc             29958  1 
asus_atk0110           10033  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
joydev                 11104  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
usblp                  12407  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usb_storage            50377  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_core              45423  0 
edac_mce_amd            9278  0 
psmouse                64576  0 
serio_raw               4918  0 
nvidia              10832442  38 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_piix4               9639  0 
atl1c                  32975  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41116  0 
hid                    83600  1 usbhid
ahci                   38030  2 
pata_atiixp             4209  0 

``````

lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:3611 Hewlett-Packard PSC 2410 PhotoSmart
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0b38:0010  
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by wildmanne39 on 2011-07-15
Hi, run this in a terminal
```
rfkill list
```
I want to see if your wireless is blocked, also you have the 3070 card and you have the 2870 driver loaded, that might be the problem, but run the command first and post the results then we will go from there.

---

### Post by Develjas on 2011-07-20
Sorry for the late reply, here's the result of rfkill list


```
 cms@cmstop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no 
```

---

### Post by wildmanne39 on 2011-07-21
Hi, run this in a terminal please.
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```
Then restart your computer, if this dirver is the correct one you should have wireless internet.

---

### Post by chili555 on 2011-07-21
The Wild Man is 100% correct. If it doesn't work as expected, post back and we'll be anxious to help you.

---

### Post by Develjas on 2011-07-23
After running the bash commands that were listed, here are the results of iwconfig and ifconfig:


```
 wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


```
 wlan0     Link encap:Ethernet  HWaddr c8:3a:35:[**REDACTED]**
          inet6 addr: fe80::ca3a:35ff:fecd:e38/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50077 (50.0 KB)  TX bytes:40460 (40.4 KB)

```



However, using the Network Manager still does not allow me to set up a wireless network by entering the SSID of the access point, the MAC address of my card, etc. as described in the original post.

Do you guys think I just need to use iwconfig and manually set up the network from the command-line? I have read about some wireless cards, though not mine, needing to do this.

---

### Post by nm_geo on 2011-07-23
Run the lsmod again.. with ethernet cable removed

```
lsmod 
```

```
sudo lshw -C network
```

reconnect cable and post..

---

### Post by Develjas on 2011-07-23
```


lsmod

Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_via      33207  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
fbcon                  39270  71 
tileblit                2487  1 fbcon
lp                      9336  0 
nvidia              10832442  38 
ppdev                   6375  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
font                    8053  1 fbcon
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 5811  1 fbcon
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
psmouse                65040  0 
edac_core              45423  0 
parport_pc             29958  1 
soundcore               8052  1 snd
vga16fb                12757  1 
parport                37160  3 lp,ppdev,parport_pc
edac_mce_amd            9278  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vgastate                9857  1 vga16fb
usb_storage            50377  0 
asus_atk0110           10033  0 
i2c_piix4               9639  0 
serio_raw               4918  0 
joydev                 11104  0 
rt2870sta             525366  1 
usblp                  12407  0 
atl1c                  32975  0 
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38030  2 
pata_atiixp             4209  0 

``````


sudo lshw -C network
[sudo] password for cms: 
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:[**REDACTED]**
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:febc0000-febfffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c8:3a:[**REDACTED]**
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless


```Thanks for the continued help guys.

---

### Post by nm_geo on 2011-07-23
Both MAC ethernet and wireless are not resolved... Lubuntu?? 
I really don't know why..
Wish i did but I don't ..

 serial: e0:cb:4e:[[B]REDACTED]

[/B] serial: c8:3a:[[B]REDACTED]

Did you removed them no  problem wondering.. :P
[/B]

---

### Post by nm_geo on 2011-07-23
```
sudo modprobe rt2870sta
```See if we can get the driver to start
[B][U]Never mind I am too sleepy here missed it 
Try a reboot..[/U][/B]

---

### Post by wildmanne39 on 2011-07-23
Hi, try these commands please if restarting your system does not work.
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
Thank you

---

### Post by Develjas on 2011-07-23
wildmanne39,

The commands you posted seemed to help matters. When trying to configure my wireless network with the graphical network manager, I can now save my settings and exit. However, my wireless still doesn't work. 

When I am using the network manager, I must put in my access points' SSID in the SSID field or I cannot apply/save my settings; trying to put the access point in BSSID doesn't allow me to save my settings.

Still unsure of what to do. :(

---

### Post by wildmanne39 on 2011-07-23
Hi, did you try what nm_geo suggested in post# 13?

---

### Post by Develjas on 2011-07-23
> **wildmanne39 said:**
> Hi, did you try what nm_geo suggested in post# 13?
Was unsure of what he was suggesting; either the command or rebooting or both.


I just tried the command and will now reboot to see what happens.

---

### Post by Develjas on 2011-07-23
Still unable to use wireless after suggestion in post #13.


iwconfig returns this result for wlan0:


```
 
wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-61 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


Which appears to suggest that after setting up the network using network manager, my card isn't connecting to the access point. There's no ESSID or Access Point listed.

---

### Post by wildmanne39 on 2011-07-23
Hi, can you click your internet icon in the top right corner then click on edit connections then see if you can enter your SSID because it says this ESSID:"" and it can not connect like this.
Thank you

---

### Post by Develjas on 2011-07-23
> **wildmanne39 said:**
> Hi, can you click your internet icon in the top right corner then click on edit connections then see if you can enter your SSID because it says this ESSID:"" and it can not connect like this.
Thank you


Ah, this worked out. After editing, I noticed that in the network manager there are two wireless connections, the "Auto [**SSID REDACTED]**" and the one I manually entered before. I don't know why it didn't automatically connect to the access point in the first place, or what I did wrong, but I will look into it more on my own and come back in a new thread with any questions.


Thank you guys so much for all of the help you have given, it has been invaluable. Now I can finally move this box out of the living room and into my office so the family can't complain anymore, :D


Thanks again!

---

### Post by nm_geo on 2011-07-23
Did you add the REDACTED words.. LOL curious here..

---

### Post by Develjas on 2011-07-23
> **nm_geo said:**
> Did you add the REDACTED words.. LOL curious here..
Yup. I don't generally like to go around letting people know the hardware addresses of my NIC's, access point, etc.

---

### Post by wildmanne39 on 2011-07-23
+1 on the curious. I am glad it is working and you are most welcome!would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by nm_geo on 2011-07-23
Well I guess that answered that I promise not to use your MAC numbers LOL
Although they can be changed mine sometimes hop I will never use yours LOL

---

