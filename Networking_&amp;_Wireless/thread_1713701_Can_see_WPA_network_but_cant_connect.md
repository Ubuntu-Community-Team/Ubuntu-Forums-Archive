---
title: "Can see WPA network but cant connect"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by Sylos on 2011-03-24
Hello and thanks for looking.

I have 2 systems running ubuntu - 1 Karmic and one Lucid - that I am having problems connecting to my wireless network with. On both systems I am trying to use the same USB wireless dongle - a Linksys Wireless G 2.4Ghz 802.11g. On both systems it picks up my network (amongst others) but will not connect. I try to connect, enter the password/key and it processes for a little while an then just comes up with "You are now disconnected...". Very irritating!

I have a BT Homehub (gen 2 I think) which is set up to use WPA/WPA2 (from memonry). I did try downgrading it to WEP and got connected  (only tested on one machine) but dont much like using a less secure system.

So I fall upon the mercy of those who are better than me to try and guide me through this. I have looked into it on the forum but couldnt really get my head around the problem.

Can anyone give me some info on where to start and how to diagnose the issue?

Just in case anyone wonders - we have a laptop running karmic (im posting this on it now) that has no issues connecting so the network is accessible. I assume the problem I have lies with the linksys adapter and the software using it.

Thanks

---

### Post by conneco on 2011-03-24
you may already know this but Home hubs have protected wifi setup i think which means you have to press the wireless association button on them before connection your laptop/pc to them. Think this applys to the black curved one at least maybe the earlier ones but not to sure

---

### Post by Sylos on 2011-03-25
Thanks for the post but that hasnt been required to connect any other device. I have also just tried it and still get no connection.

Any other suggestions?

---

### Post by conneco on 2011-03-25
Just read your post again glad to hear you didnt stay on WEP, BT annoy me with that most of there gear up until recently had WEP as the default even though they had the option of WPA even there business hubs shipped with WEP default.

And ive had major issues with BT home hubs in the past before you start delving to deep into drivers and settings try a factory reset on the hub,

---

### Post by Sylos on 2011-03-29
Cheers but resetting and fiddling with the hub seems to make no difference. My ps3 and laptop have no issue connecting either.

Any thoughts?

Can anyone give me some advice on how to test if it is the drivers as Im about to go for some Ndiswrapper fun and would rather know before embarking on that if here is an easier way to verify its not the driver.

Thanks

---

### Post by Sylos on 2011-03-29
Kerbump!

---

### Post by TBABill on 2011-03-29
Can you open up a terminal session and provide the outputs of ```
lspci
``` and ```
sudo lshw -C network
```

---

### Post by TBABill on 2011-03-29
I see your Kerbump! and raise you a "watch for posts after you bump your own thread" :)

---

### Post by Sylos on 2011-03-30
My apologies - I was at work during some of the time between post and reply.

I appreciate the reply and here is the output of the commands:

lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
```

and lshw -C network:

```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:30:18:a1:f6:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:e000(size=256) memory:f7021000-f70210ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:83:e5:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

This seems to show that the device is being detected and is functioning (a fact backed up by the ability to see varying networks).

Any thoughts as to the issue or should I just go ahead and try installing drivers using Ndiswrapper.

Actually, the fact that the device shows from lshw implies that the drivers are working - yes? Perhaps the problem could be with wpasupplicant - this would make sense given that I can connect using WEP.

Is that right?

Thanks

EDIT: Might it be worth trying WICD as the network manager?

---

### Post by TBABill on 2011-03-31
Ugggg....forgive me. I gave you the wrong command. I just re-read and saw that your device is USB, not internal. Instead of PCI, we need to see ```
lsusb
``` and since you're going to be giving back info can you also give the output of ```
lsmod
``` so we can know which drivers are in use by the system?

---

### Post by Sylos on 2011-03-31
Thanks for the reply.

Im at work at the momnet but will have a crack tonight and post back the results.

And to be honest I should have twigged that lsusb was the way forward - a case of blindly following instruction from me there. :D

What do you reckon about the ...network output? I checked that command on our laptop that works and got a whole lot more output.

Cheers

---

### Post by TBABill on 2011-03-31
> **Sylos said:**
> My apologies - I was at work during some of the time between post and reply.
 
I appreciate the reply and here is the output of the commands:
 
lspci:
 
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
```
 
and lshw -C network:
 
```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:30:18:a1:f6:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:e000(size=256) memory:f7021000-f70210ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:83:e5:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
 
This seems to show that the device is being detected and is functioning (a fact backed up by the ability to see varying networks).
 
Any thoughts as to the issue or should I just go ahead and try installing drivers using Ndiswrapper.
 
Actually, the fact that the device shows from lshw implies that the drivers are working - yes? Perhaps the problem could be with wpasupplicant - this would make sense given that I can connect using WEP.
 
Is that right?
 
Thanks
 
EDIT: Might it be worth trying WICD as the network manager?
 
I think you'd see the driver and settings for the wireless if it were setup correctly. I have a feeling you just don't have the driver installed or configured, but till we know what driver you need it's not much help.

---

### Post by Sylos on 2011-03-31
Ok. Here is the output:

lsusb:

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


lsmod:

```
lsmod
Module                  Size  Used by
aes_i586                7268  0 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70694  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2500usb              18141  0 
rt2x00usb               9703  1 rt2500usb
rt2x00lib              27509  2 rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
snd                    54180  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
mac80211              205402  2 rt2x00usb,rt2x00lib
nvidia               4701243  22 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
parport_pc             25962  1 
amd64_agp               7165  1 
lp                      7028  0 
cfg80211              126528  2 rt2x00lib,mac80211
psmouse                63245  0 
serio_raw               3978  0 
i2c_viapro              5573  0 
soundcore               6620  1 snd
k8temp                  3152  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
shpchp                 28820  0 
agpgart                31724  2 nvidia,amd64_agp
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
floppy                 53016  0 
sata_via                7009  0 
pata_via                7272  3 

```

I assume  rt2x00usb is the fellow in use. How do I know if thats correct?

Many thanks for your patience.

---

### Post by TBABill on 2011-03-31
Looks like the right driver. Have you tried to install wicd and see if it works with the native Linux driver? If not, most listings online actually show people using the Windows XP driver via ndiswrapper. Is that a possibility?

---

### Post by Sylos on 2011-03-31
Yeah Im thinking about tryin ndiswrapper. 

Weird thing is it all worked out of the box under Hardy but as soon as I upgrade (fresh install) it fails.

I found a man page entry that seems to say that the 802.11 driver may not support the WPA. Im not even sure if this applies to me but it may explain why WEP works but not WPA:

[http://manpages.ubuntu.com/manpages/natty/en/man4/wi.4freebsd.html](http://manpages.ubuntu.com/manpages/natty/en/man4/wi.4freebsd.html)

Anyhow, Im gonna try installing the windoze driver through ndiswrapper and see if that works. Im gonna have to wait until I return from holiday to do it but I'll be back to the forums for more help if I hit problems.

I really appreciate your input.

---

### Post by Sylos on 2011-04-04
Ok. So heres the latest.

I tried uninstalling network manager and installing WICD. This didnt work - same story - tries to connect for a while then says bad password.

I then tried to install ndiswrapper and install the windows drivers obtained from the linksys site. They came in .exe form so I used WINE to get the files out and then installed the driver using ndis. Unfortunately, this appears to be the same rt2500usb driver that was already in use. I tried to remove and then reinstall anyway and it appeared to go ok BUT when I try to connect to the wireless network it is the same as always - bad password.

lshw - C network now shows "driver=ndiswrapper+tr2500usb"

Im not sure where to go from here. Is there any way of using the old Hardy driver (thats a desperate question and I know there are no doubt a thousand incompatibilities).

Any help appreciated.

---

### Post by Sylos on 2011-04-05
So reading here...

[http://ubuntuforums.org/showthread.php?t=1387583](http://ubuntuforums.org/showthread.php?t=1387583)

..suggests there is a problem with the driver itself and that it wont work with WPA/WPA2 switched on. The recomendation is to used only WPA but I dont think that the BTHomeHub has an option to use only one of these.

Has anyone had any luck getting this adapter to work with the HomeHub using the rt2500usb driver?

If not does anyone have any suggestions for a dongle that will work with the WPA/WPA2 on the hub?

Thanks

---

### Post by gerowen on 2011-04-05
Try turning off encryption altogether just as a test, and see if it lets you connect.  This could at least rule out whether it's WPA only or something more.

---

### Post by matt_symes on 2011-04-05
Hi

> **gerowen said:**
> Try turning off encryption altogether just as a test, and see if it lets you connect.  This could at least rule out whether it's WPA only or something more.

I concur. Also try with just WEP encryption.

Have you investigated a backport from maverick for your Lucid installation.

I also had an issues with WPA2 personnel on a different card and a back port fixed it for me.

Kind regards

---

### Post by Sylos on 2011-04-05
Cheers for the posts guys.

I have tried it with WEP and it works fine using that - it is the WPA/WPA2 that is failing. Im not sure what exactly is going on and Im not sure how to diagnose the problem. I keep thinking that the HW driver shouldnt make a difference to how the encryption gets dealt with which leads me to think the problem is with wpasupplicant. Sadly I have only recently become aware of its existence so have no idea how to test if the supplicant is the issue. Also, I have 2 machines using karmic with different wireless cars - 1 works fine out of box the other doesnt - which suggests it must be something specific to the card eg. driver. Frustrating!

Also, a guy in my work IT dpt said that WPA is less secure than WEP which is why BT dont offer it as a stand alone option on the V2 Hub - only WPA/WPA2. Dont understand that but does anyone know if its true?

Tried asking BT's support techs if I could set it up for only WPA2 - the indian gent on the phone kept telling me to reset the hub try the password etc. Eventually I gave up and hung up on them (sighs!).

Any indication where I might find a backport?

Any recomendation on a stable/compatible dongle?

---

### Post by Sylos on 2011-04-05
Success!

I found in the hubs advanced settings a way to make it only accept WPA2 security and that has resolved the issue - all connections now made!

Many thanks to those who stopped by to lend a hand. If anyone has any ideas as to why the driver/wpasupplicant wont work with WPA/WPA2 then I would be very interested to hear it - it would be good to know the source of this irritation.


Cheers

---

