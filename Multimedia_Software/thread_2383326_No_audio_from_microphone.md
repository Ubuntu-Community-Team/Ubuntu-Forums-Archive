---
title: "No audio from microphone"
date: 2018-01-23
forum: Multimedia Software
---

### Post by gelo.linux on 2018-01-23
Hello there!

I'm running Kubuntu 16.04.3 LTS on an ASUS S56C

If I use teamspeak or another program that register the microphone sound (eg: audacity), everytime i hear a rustling noise, but not my voice.
My audio profile is set correctly to **Duplex Analog Stereo**, i've tried every possible setting but with no luck.
The only thing I know is that if I unmute loopback mixing through alsamixer, I can hear the same noise through the speakers, so I figured out that in someway the loopback device keeps the input device busy.

here are some useful informations:

_lspci_
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation 3rd Gen Core Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 740M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
```

[U]sudo lshw -C multimedia
[/U]```
*-usb                   
       description: Video
       product: USB Camera
       vendor: Azurewave
       physical id: 2
       bus info: usb@1:1.2
       version: 8.23
       serial: NULL                                                               
       capabilities: usb-2.00                                                     
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s             
  *-multimedia                                                                   
       description: Audio device                                                 
       product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation                                                 
       physical id: 1b                                                           
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:33 memory:f7a18000-f7a1bfff
```


_aplay -l_
```
Jan 22 17:50:58 gelobook pulseaudio[2511]: [pulseaudio]  bluez5-util.c: GetManagedObjects() failed:  org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible  causes include: the remote application did not send a reply, the message  bus security policy blocked the reply, the reply timeout expired, or  the network connection was broken.
Jan 21 19:08:33 gelobook  pulseaudio[2659]: [pulseaudio] module.c: Module "module-device-manager"  should be loaded once at most. Refusing to load.
Jan 21 19:45:22  gelobook pulseaudio[2402]: [pulseaudio] backend-ofono.c: Failed to  register as a handsfree audio agent with ofono:  org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not  provided by any .service files
Jan 21 20:08:15 gelobook  pulseaudio[2441]: [pulseaudio] backend-ofono.c: Failed to register as a  handsfree audio agent with ofono:  org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not  provided by any .service files
Il file binario (standard input) corrisponde
```


Thank you in advance!

---

### Post by TheFu on 2018-01-24
Welcome to the forums.

I've had this issue to.  The resolution was a different 3.5mm conversion plug. My laptop has a combined Mic/Speakers jack.  There are competing standards for which type of jack is used.  Laptops and smartphones appear to use different order for the speaker and mic connections inside the 3.5mm jack.  
[https://www.howtogeek.com/180395/how-to-connect-a-headset-to-a-laptop-tablet-or-smartphone-with-a-single-audio-jack/](https://www.howtogeek.com/180395/how-to-connect-a-headset-to-a-laptop-tablet-or-smartphone-with-a-single-audio-jack/)

Then there is the **[B]pavucontrol**[/B] application. There are multiple tabs which control almost everything about the audio system for most Linux installs.  Lubuntu doesn't/didn't use pulse-audio last time I checked, so **alsamixer** is the tool for that system instead of the pulse-audio controller.

---

