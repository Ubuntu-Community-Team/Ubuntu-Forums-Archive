---
title: "Wireless on old Toshiba Pro 6100 - Newbie question"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by MonocleMike2 on 2011-10-06
Cannot connect to broadband router.  It can see the router and asks me for the key but cannot connect.  I know the key is right as I have another laptop running Ubuntu and connecting.  I have run lspci but cannot see any network adapter listed so I don't know what wireless card is built in.  I am still a newbie so any help gratefully received.
PS The wireless card works in Windows and has a hardware switch which also appears to work correctly.
PPS Extensive Googling of this problem leads me to believe it may be irreconcilable! It seems the built in wireless card is incompatible with current Ubuntu.  Does anyone know better?

---

### Post by gordintoronto on 2011-10-06
You might be looking at old information. If it sees the router, the wireless adapter is being recognized, and an appropriate driver is loaded.

It might have helped if you had copy/pasted the lspci output into your message. Also: what version of Ubuntu are you using? What is the router's ssid? (I've seen cases where changing the router's ssid to all lower case fixed the problem.)

If you right-click on the network manager icon and select "edit connections," then click the wireless tab, and "add" your router with its encryption type and password, what is the result?

In any case, please send us the lspci output.

---

### Post by MonocleMike2 on 2011-10-07
mike@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

mike@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

Thank you for your help.  Does this shed any light on the problem?  I have looked at Edit Connections and it appears to be in there;  by SSID do you mean key?  That's in there but does contain upper case.  I am scared of trying to change it on the router as there are other devices using it successfully, including visiting mobile phones etc.

If the internal card is a non-starter then I can switch it off and use a Belkin on a USB port but so far I can't get it to lead a driver for that!  I'm sure it can but my ignorance on how to do it is the problem!

PS In case it helps here is this

mike@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
michael_mic            12540  4 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
nouveau               621970  2 
orinoco_cs             12898  1 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
orinoco                69899  1 orinoco_cs
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
cfg80211              156212  1 orinoco
ttm                    65184  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
drm_kms_helper         40745  1 nouveau
drm                   184164  4 nouveau,ttm,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  1 orinoco_cs
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
irda                  185091  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 nouveau
parport_pc             32111  1 
soundcore              12600  1 snd
serio_raw              12990  0 
video                  18951  1 nouveau
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
toshiba_acpi           13796  0 
crc_ccitt              12595  1 irda
sparse_keymap          13666  1 toshiba_acpi
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 



All help gratefully received.

15:45
I've got the Belkin stick working.  I installed it in Windows together with switching on Wireless Zero Configuration, rebooted in Ubuntu and it knew what to do.  I only had to put in the key.
Ubuntu also now knows that the internal card is the Texas Instruments PCI1410 Cardbus controller listed in lscpi but it stll cannot connect.  It would be convenient to use the internal card rather than the stick but not worth great effort.  if someone can see a simple fix now it knows what he card is then I would be very pleased to try it.

---

### Post by gordintoronto on 2011-10-08
The PCI1410 is a PC Card controller. To identify the wireless adapter, run this command: lspcmcia

---

### Post by MonocleMike2 on 2011-10-08
x

---

### Post by MonocleMike2 on 2011-10-08
lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:0a.0)
Socket 0 Device 0:    [orinoco_cs]        (bus ID: 0.0)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:0b.0)
Socket 2 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:0b.1)

---

### Post by gordintoronto on 2011-10-08
It's possible this is relevant:
[http://ubuntuforums.org/showthread.php?t=1617549](http://ubuntuforums.org/showthread.php?t=1617549)

---

### Post by MonocleMike2 on 2011-10-09
THANK YOU VERY MUCH!  Worked like a dream.  I'm very grateful.

---

