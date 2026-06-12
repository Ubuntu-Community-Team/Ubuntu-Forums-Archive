---
title: "No Sound, 5.10 fresh install"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by sprocket87 on 2005-11-29
Okay, first post related to a fresh install of 5.10 (ub=awesome so far btw)

Here's the basics: No sound whatsoever - not on login, no events, music, nothing. Interestingly, I *had* sound very briefly. Basically, when I first setup ubuntu, I chose too high of a display resolution and when xserver started the monitor blanked out. Well, I tried rebooting and doing all sorts of tricky stuff. During this period of random "enter"ing, I got error beeps (sounded very "african" in nature?). Then somehow I got a very long, drawn out, but pleasing sound that I assumed was a login sound (no video, remember).

Eventually I rememberd I could cycle resolutions with Ctrl+Alt+"+" or "-", so that worked out. But after a reboot I lost my sound! I don't know what I did, but it's done broken...

I've followed the steps on several wiki.ubuntu entries, and followed the Sound troubleshooting HowTo, to no avail. Volume up, speakers on, Sound device enabled in Selector, and I've tried ALSA, ESD, and OSS. Added those few lines to my /etc/esd.conf (IIRC), nothing.

One thing I might add is that my system has 2 sound cards: The generic onboard audio (nForce chipset) that I'm NOT using, and a PCI Creative SB Live! card, which is the one I'm using. It shows up in Device Manager under the nForce PCI controller sub-listing, so the system sees it I think...

Also, when booting ubuntu and it scrolls the list of processes/devices it's starting, (Initializing (xxxxx).... "OK"), mine shows a "Setting up ALSA card 0...", but there's no "OK" (everything else OK's), so I think something is screwed up.

Thanks for any tips!

Jesse

---

### Post by amohanty on 2005-11-29
Did you disable the onboard audio in BIOS?

AM

---

### Post by sprocket87 on 2005-11-30
Good thought, I'll check it out... I just think it's strange how I temporarily had sound.

---

### Post by sprocket87 on 2005-11-30
Well I checked in the BIOS. I had it disabled already, probably since I had been using the secondary (Creative SB Live!) PCI card in Windows XP previously.

Just for fun I re-enabled the onboard audio in BIOS to see if ubuntu would pick it up. It did apparently, because in the System > Pref (or admin?) > Sound dialog I could choose "nForce audio" from the device drop-down. I switched to that one and tried to get some sound out of it, but couldn't still. I checked the levels in alsamixer again and tested the sources in Multimedia Selector, but nothing worked.

Help... :(

---

### Post by amohanty on 2005-11-30
Is everything turned on in alsamixer?

AM

---

### Post by sprocket87 on 2005-12-01
[QUOTE=amohanty]Is everything turned on in alsamixer?

AM[/QUOTE]

Yup... Just removed the Creative PCI card and tried only system board audio, no luck :(

---

### Post by amohanty on 2005-12-01
Put it back in and check the output of:

lspci 

to see if it is recognized. Usually SB cards are easily recognized by Ubuntu. I have an Audisy 2ZS and I have 5.1 no less.

AM

---

### Post by sprocket87 on 2005-12-01
[QUOTE=amohanty]Put it back in and check the output of:

lspci 

to see if it is recognized. Usually SB cards are easily recognized by Ubuntu. I have an Audisy 2ZS and I have 5.1 no less.

AM[/QUOTE]

I'll try that out when I get home tonight, thanks. I think I ran lspci when it was in and I was first having problems, and it showed up. I'll double check though. Assuming it does show up and is detected, what's the next logical step? 

Thanks for your help!

Jesse

---

### Post by amohanty on 2005-12-01
well then you have to make sure that the correct sound modules are loaded via
lsmod

AM

---

### Post by JeffreyRatcliffe on 2005-12-01
I am in the same situation - no sound from a 5.10 fresh install. Booting into XP gives me sound with no problem. aplay -l produces:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


[QUOTE=amohanty]Put it back in and check the output of:

lspci 

to see if it is recognized. Usually SB cards are easily recognized by Ubuntu. I have an Audisy 2ZS and I have 5.1 no less.

AM[/QUOTE]

However, if I try lspci, I don't see anything that looks like a sound card:

0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770 (rev 81)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771 (rev 81)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0147 (rev a2)
0000:02:01.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:04.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)
0000:02:05.0 Communication controller: Lucent Microelectronics: Unknown device 0620

Any ideas?

Thanks for any help

Jeff

---

### Post by amohanty on 2005-12-01
[QUOTE=JeffreyRatcliffe]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

0000:02:01.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)
0000:02:04.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)
[/QUOTE]

This tells me that you are using the onboard audio. Do you have a PCI sound card? If so:

1. disable the onboard audio in the BIOS
2. turn on everything in alsamixer. If the terminal is not convenient install gamix from the universe repos.
3. select alsa everywhere in the multimedia systems selector.
4. in preferences->sound make sure that the sound server is on (that starts esd - but its a safe starting point to have both alsa and esd on)

If it still does not work post the results of:
lsmod | grep snd

Let me know what happens.

AM

---

### Post by JeffreyRatcliffe on 2005-12-02
On closer inspection (it's a new PC - the first thing I did after buying it was to install Ubuntu)

0000:02:01.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)
0000:02:04.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)

seem to be input-only. I think they are the machine's two built-in TV tuners. I've attached the screenshot from the Windows Device Manager. There seems only to be the on-board sound card.

[QUOTE=amohanty]2. turn on everything in alsamixer. If the terminal is not convenient install gamix from the universe repos.
3. select alsa everywhere in the multimedia systems selector.
4. in preferences->sound make sure that the sound server is on (that starts esd - but its a safe starting point to have both alsa and esd on)[/QUOTE]

Done. No joy.

[QUOTE=amohanty]If it still does not work post the results of:
lsmod | grep snd[/QUOTE]

snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 saa7134,snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm

What does that tell you?

Thanks for the help

Jeff

---

### Post by amohanty on 2005-12-02
Try the following:

sudo killall esd
esd

Can you hear a tinkle?

OR

Take a look at this thread and see if it works for you.
[http://ubuntuforums.org/showthread.php?t=97118&highlight=realtek](http://ubuntuforums.org/showthread.php?t=97118&highlight=realtek)

Also try muting the SPDIF output in alsamixer.

HTH
AM

---

### Post by JeffreyRatcliffe on 2005-12-04
[QUOTE=amohanty]Try the following:

sudo killall esd
esd

Can you hear a tinkle?[/QUOTE]

esd just hangs it (although I can kill it with ctrl-c.

[QUOTE=amohanty]Take a look at this thread and see if it works for you.
[http://ubuntuforums.org/showthread.php?t=97118&highlight=realtek](http://ubuntuforums.org/showthread.php?t=97118&highlight=realtek)[/QUOTE]

Thanks for the tip, which I followed up. Still no joy - see that thread for details.

[QUOTE=amohanty]Also try muting the SPDIF output in alsamixer.[/QUOTE]

I don't have an SPDIF option in alsamixer.

Thanks for the help. Any other ideas?

Jeff

---

### Post by amohanty on 2005-12-04
> esd just hangs it (although I can kill it with ctrl-c.

It doesnt hang, its still running, to get back the prompt:
```
esd &
```

This puts the process in the backgroud.

Looked at that thread. Posting the actual terminal output would help ppl debug it better. ALso hunt the forums for Realtek audio and see if you can find something.

Other than that, I am sorry.

AM

---

### Post by JeffreyRatcliffe on 2005-12-05
[QUOTE=amohanty]It doesnt hang, its still running, to get back the prompt:
```
esd &
```[/QUOTE]

Trying to install that reaktek driver has evidently screwed things up properly. Now this gives me:

```
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default

```

and aplay -l produces:

```
aplay: device_list:218: no soundcards found...
```

I just tried reinstalling the original Ubuntu ALSA stuff but it made no difference.

> Looked at that thread. Posting the actual terminal output would help ppl debug it better. ALso hunt the forums for Realtek audio and see if you can find something.


I've added the terminal output. The forums have various other suggestions which I now can't try until I can get the soundcard found again.

Thanks

Jeff

---

### Post by amohanty on 2005-12-05
Try:

```
modprobe <soundccard driver module name>
```

AM

---

### Post by JeffreyRatcliffe on 2005-12-05
With

```
sudo modprobe
```

I can load everything from the old lsmod | grep snd list:

```
snd_hda_intel 15872 1
snd_hda_codec 72064 1 snd_hda_intel
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer 21764 1 snd_pcm
snd 48644 8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_timer
soundcore 9184 2 saa7134,snd
snd_page_alloc 10120 2 snd_hda_intel,snd_pcm
```

except snd_hda_intel and snd_hda_codec

which gives me:

```
FATAL: Module snd_hda_intel not found.
FATAL: Error running install command for snd_hda_intel
```

and indeed /lib/modules/2.6.12-10-386/kernel/sound/pci/hda/snd-hda-intel.ko is missing.

but /lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-intel.ko is there, so

```
sudo insmod snd-hda-codec.ko
sudo insmod snd-hda-intel.ko
```

(God I hope they didn't change anything in those modules).

That works. I can go to Applications/Sound and Video/Volume Control and turn everything on (why that didn't work from the alsamixer I don't know).

esd now gives me some beeps!

Jeff

---

### Post by amohanty on 2005-12-05
Ok.

Lets do this:

1. Reboot
2. Make sure that in the BIOS your onboard autdio is enabled.
3. post output of ```
lspci | grep snd
```
4. post output of ```
lsmod | grep snd
```

5. post entire contents of output.txt on your Desktop after doing the following.

```
./configure | tee ~/Desktop/output.txt
``` 
```
make | tee -a ~/Desktop/output.txt
``` 
```
sudo make install | tee -a ~/Desktop/output.txt
```

Apparently you need to build the drivers for this to work. So once everythign else is in place, lets try to build it.

AM

---

### Post by JeffreyRatcliffe on 2005-12-05
[QUOTE=amohanty]Ok.

Lets do this:

1. Reboot
2. Make sure that in the BIOS your onboard autdio is enabled.
3. post output of ```
lspci | grep snd
```
4. post output of ```
lsmod | grep snd
```[/QUOTE]

Back to no output after either of those.

> 5. post entire contents of output.txt on your Desktop after doing the following.

```
./configure | tee ~/Desktop/output.txt
``` 
```
make | tee -a ~/Desktop/output.txt
``` 
```
sudo make install | tee -a ~/Desktop/output.txt
```

```
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make dep
make[1]: Entering directory `/home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22'
make[2]: Entering directory `/home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22/acore'
make[2]: Leaving directory `/home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22/acore'
make[1]: Leaving directory `/home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22'
find /lib/modules/2.6.9-1.667smp/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22/acore'
make[1]: Leaving directory `/home/jeff/Desktop/realtek-linux-audiopack-3.5-2/alsa-driver-1.0.9b_22/acore'
```

I see that it is asking for the kernel source, but that isn't listed by synaptic.

Jeff

---

### Post by amohanty on 2005-12-05
Try this:

```
sudo apt-get install kernel-package libncurses5 libncurses5-dev
```


and repost the output of (5) in my previous post.
AM

---

### Post by JeffreyRatcliffe on 2005-12-06
I was being slightly slow.

I've just reinstalled the kernel using Synaptic and the tip with playing with the settings in Applications/Sound and Video/Volume Control has done the trick.

I now have sound!

I just need to get the card reader working (USB internal) and I will be very happy.

Thanks for all the help.

Jeff

---

### Post by amohanty on 2005-12-06
If you set the hotplug daemon to start at bootup, doesnt it work??

AM

---

### Post by JeffreyRatcliffe on 2005-12-07
[QUOTE=amohanty]If you set the hotplug daemon to start at bootup, doesnt it work??[/QUOTE]

I don't know how to do that without looking, but I suspect that the problem is rather deeper than that.

lsusb gives me:

```

Bus 005 Device 004: ID 0d8c:5200 C-Media Electronics, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0d8c C-Media Electronics, Inc.
  idProduct          0x5200
  bcdDevice            1.00
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               9
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

```

So you see the only thing that is recognised is the manufacturer - not even that it is a card reader.

Jeff

---

### Post by amohanty on 2005-12-07
Try this:

plug in a mem stick/cf/sd card into a port on the reader.

and post the o/p of :

```
sudo fdisk -l
```

also post the contents of:

```
/proc/bus/usb/devices
```

---

### Post by JeffreyRatcliffe on 2005-12-07
```
sudo fdisk -l
```

gives:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15197   122069871    7  HPFS/NTFS
/dev/sda2           15198       30401   122126130    5  Extended
/dev/sda5           15198       24315    73240303+   b  W95 FAT32
/dev/sda6           24316       24327       96358+  83  Linux
/dev/sda7           24328       24570     1951866   82  Linux swap / Solaris
/dev/sda8           24571       25786     9767488+  83  Linux
/dev/sda9           25787       30401    37069956   83  Linux

```

So that's just the internal hard drive with the XP NTFS boot, FAT32 share, plus Ubuntu partitions.

/proc/bus/usb/devices contains:

```

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  2/800 us ( 0%), #Int=  2, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 ehci_hcd
S:  Product=Intel Corporation I/O Controller Hub EHCI USB
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0606 Rev= 7.02
S:  Product=USB2.0 Hub
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

T:  Bus=05 Lev=02 Prnt=03 Port=01 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=148f ProdID=2570 Rev= 0.01
S:  Manufacturer=Ralink
S:  Product=802.11g WLAN 
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=300mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=05 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0bc7 ProdID=0006 Rev= 2.00
S:  Manufacturer=X10 WTI
S:  Product=RF receiver
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=ati_remote
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
E:  Ad=02(O) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0d8c ProdID=5200 Rev= 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   4 Ivl=32ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=Intel Corporation I/O Controller Hub UHCI USB #4
S:  SerialNumber=0000:00:1d.3
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=Intel Corporation I/O Controller Hub UHCI USB #3
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=3a11 Rev= 1.00
S:  Manufacturer=hp
S:  Product=officejet 5500 series
S:  SerialNumber=MY42QF209H96
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=cc Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 3 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=03(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=07(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=87(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=88(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=d4 Prot=00 Driver=(none)
E:  Ad=07(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=87(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=88(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=Intel Corporation I/O Controller Hub UHCI USB #2
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=323/900 us (36%), #Int=  3, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=Intel Corporation I/O Controller Hub UHCI USB #1
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04f2 ProdID=0420 Rev= 1.50
S:  Manufacturer=Chicony
S:  Product=USB Wireless HID Receiver
C:* #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   7 Ivl=10ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

```

Not even mentioned.

Thanks for the support

Jeff

---

### Post by amohanty on 2005-12-08
Well the /proc/bus/usb shows the devices as being recongnized. btw if it has a sd card reader, I think those are handled by the scsi stuff (dont know much about it so cant help you there). 
What does a

```
lsmod | grep usb
```

return?

I have two case USB ports that are hooked into the mobo + the USB mouse and I get the following:

```
aseem@kandinsky:~$ lsmod | grep usb
usblp                  11776  0
usbhid                 30688  0
usbcore               104316  5 usblp,usbhid,ehci_hcd,ohci_hcd

```

It should be somewhat like this.
Also post the output of :

```
lsusb
```

just that without the -v.

In my case
```
aseem@kandinsky:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

Also do it with at least one USB port having a mem stick.

---

### Post by JeffreyRatcliffe on 2005-12-08
lsmod | grep usb gives:

```
usblp                  11776  0
usbhid                 30688  0
usbcore               104316  6 ati_remote,usblp,usbhid,ehci_hcd,uhci_hcd
```

I also have a USB mouse, plus keyboard, WLAN, printer and TV card.

lsusb:
```
Bus 005 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc.
Bus 005 Device 006: ID 148f:2570
Bus 005 Device 004: ID 0d8c:5200 C-Media Electronics, Inc.
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:3a11 Hewlett-Packard OfficeJet 5510
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04f2:0420 Chicony Electronics Co., Ltd
```

With a USB mem stick (which is found correctly):
```
Bus 005 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc.
Bus 005 Device 006: ID 148f:2570
Bus 005 Device 004: ID 0d8c:5200 C-Media Electronics, Inc.
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 08ec:0802 M-Systems Flash Disk Pioneers
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:3a11 Hewlett-Packard OfficeJet 5510
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04f2:0420 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 0000:0000
```

Jeff

---

### Post by amohanty on 2005-12-08
So it is merely a matter of automounting the mem stick when it is inserted into the reader, right?

OK check to see if you have following packages installed:

autofs
gnome-volume-manager

If not install them:

```
sudo apt-get install autofs gnome-volume-manager
```

Then try inserting the USB stick and if you dont see an icon on the desktop, post the o/p of the following:

```
dmesg | tail -n 50
```

```
tail -n 50 /var/log/messages
```

Finally theres also an item in System->Preferences->Peripherals? (dont have access to my box right now) that allows you to specify what to do when media is mounted. Look for and set the options for removable media to something like 'open location'

HTH

---

### Post by xyz on 2005-12-08
Hi-
Could this have something to do with my NoSoundAtAll problem?Thanks for taking a look at this.

> ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

(noob!)
NB:don't know why the smilie instead of 2 dots one on top of the other.

---

### Post by JeffreyRatcliffe on 2005-12-08
[QUOTE=amohanty]So it is merely a matter of automounting the mem stick when it is inserted into the reader, right?[/QUOTE]

I think I misunderstood you when you said USB mem stick. I thought you meant a USB "dongle"-type storage stick, as opposed to the Sony memory stick that would go in the card reader, had I a memory stick. I've only got SD or CF to try.

Jeff

---

### Post by JeffreyRatcliffe on 2005-12-08
[QUOTE=xyz]NB:don't know why the smilie instead of 2 dots one on top of the other.[/QUOTE]

I don't know about your problem, but I imagine the smiley came not just from the colon, but the combination ":" and "(" = :(

Jeff

---

### Post by amohanty on 2005-12-08
Any memory card/stick/dngle will do. Basically anything that you can insert in there will do..

AM

---

### Post by amohanty on 2005-12-08
[QUOTE=xyz]Hi-
Could this have something to do with my NoSoundAtAll problem?Thanks for taking a look at this.


(noob!)
NB:don't know why the smilie instead of 2 dots one on top of the other.[/QUOTE]
Have you selected a device in System->Preferences->Multimedia Systems Selector??

---

### Post by xyz on 2005-12-08
[QUOTE=amohanty]Have you selected a device in System->Preferences->Multimedia Systems Selector??[/QUOTE]
Yes I did and all tests resulted in: Failed to construct test pipeline for...:
ALSA - Advanced Linux Sound Architecture
Artsd -ART Sound Daemon
ESD - Enlightenment Sound Daemon
OSS - Open Sound System
Custom

Also:
```
sudo sysv-rc-conf
```
Trying to learn a bit,I messed around in there reading the tuto found on the site.I think that's when I started having snd problems...an [X] or 2 may be missing there but I don't know for sure.
I also read this thread carefully and tried out what I could understand.I don't know if this helps...
```
lspci
```
> th@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)
0000:01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 33)
and...
```
lsmod
```
> Module                  Size  Used by
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
pcmcia                 26568  2
yenta_socket           25292  1
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  15748  0
toshiba_acpi           10716  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
af_packet              21768  2
joydev                  9984  0
tsdev                   7776  0
evdev                   9664  1
p4_clockmod             5036  0
speedstep_lib           4228  1 p4_clockmod
freq_table              4388  2 cpufreq_stats,p4_clockmod
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  0
lp                     12292  0
parport                35912  2 parport_pc,lp
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
e100                   34976  0
mii                     5696  1 e100
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  3
ide_generic             1376  0
piix                   10372  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,piix
unix                   26896  809
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

Excuse me for posting all this stuff if it turns out to be useless.I'm swimming in an ocean bigger than the Pacific Ocean.Thanks for your help and understanding.

---

### Post by xyz on 2005-12-08
[b]Unless you know what you're doing,you should not 
take my word for it.I tool my own risks on my own machine.You may just want to wait until one of people who know what they are doing comments on this.tnx[/b]
I found stuff 'googling away' and I got sound BUT now it sounds as if it has a HUGE reverb (echo) on it.I have far too little experience to say 'this is what I did and it worked' but I'd like to post my various attemps.
**1.**```
sudo gedit /etc/esound/esd.conf
```
and make it look like this:
> [esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options
**2.**```
sudo apt-get install libesd-alsa0
```
create or go to a "asound" file
```
sudo gedit /etc/asound.conf
```
to have it read...
> pcm.card0 {
type hw
card 0
}
 
pcm.!default {
type plug
slave.pcm "dmixer"
 
}
 
 
pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}
Mine used to read:
period_size 2048
buffer_size 32768
rate 48000
and finally...
```
sudo /etc/init.d/alsa restart
```
**3.**I also tried .
```
sudo apt-get --purge remove alsa-base
sudo apt-get install alsa-base
sudo apt-get install ubuntu-base gdm
```
Execute the last line only if gdm's gone.(gdm et ubuntu-base may uninstall along with Alsa)
**4.** I ran
```
sudo sysv-rc-conf
```
There I put [x] in all SysV Runlevel (1-2-3-4-5-0-6-S) in
acpi-supp$,acpid,alsa
...and now I've got sound but it's rotten!Hey,one step at a time!
Thanks to you professionals to comment,explain and so on.
**Please remember I have no idea as to what did the trick!**

---

### Post by amohanty on 2005-12-08
Most probably this:

> sudo apt-get install libesd-alsa0

---

### Post by JeffreyRatcliffe on 2005-12-16
[QUOTE=amohanty]Any memory card/stick/dngle will do. Basically anything that you can insert in there will do..AM[/QUOTE]

OK so back to the CF card, lsusb gives before:

```
Bus 005 Device 009: ID 0bc7:0006 X10 Wireless Technology, Inc.
Bus 005 Device 008: ID 148f:2570
Bus 005 Device 007: ID 0dbf:9001 Quik Tech Solutions
Bus 005 Device 004: ID 0d8c:5200 C-Media Electronics, Inc.
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:3a11 Hewlett-Packard OfficeJet 5510
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04f2:0420 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 0000:0000
```

and afterwards:

```
Bus 005 Device 009: ID 0bc7:0006 X10 Wireless Technology, Inc.
Bus 005 Device 008: ID 148f:2570
Bus 005 Device 007: ID 0dbf:9001 Quik Tech Solutions
Bus 005 Device 004: ID 0d8c:5200 C-Media Electronics, Inc.
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 120: ID 0bb4:0a05 High Tech Computer Corp.
Bus 003 Device 002: ID 03f0:3a11 Hewlett-Packard OfficeJet 5510
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04f2:0420 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 0000:0000
```

i.e. no change. The card reader IS listed, though - C-Media Electronics, Inc.

Jeff

---

### Post by ArmadaEnder on 2005-12-20
I've followed everything in this thread along with many others on this site and by googling and everything I tried still doens't fix my audio problem. (Which is no sound unless I turn the volume on my speakers ALL the way up and only then do I get a little sound, however very distorted).

I'm trying to use the audio output on my mobo as I do not have a pci audio card. Now I'm wondering: would it just be easier for me to go out and buy a 10 dollar audio card and find the drivers for it or is there a way in which I can get the audio to work from my mobo without having to turn my speakers all the way up? 

Any insight at all will be great appreciated. Thank-you.

---

### Post by ArmadaEnder on 2005-12-20
This is bizarre: I hook up my external speaker system (2.1 Labtec speaker system) and I can only hear sound when its turned up all the way, and it's barely audible. I hook up to an old crv monitor of mine (just the audio cable) and I can hear it perfectly except only out of the left speaker. This just boggles my mind. 

Anyone have a clue as to what could be going on? Thank you so much for your time.

---

### Post by girionis on 2005-12-20
Hello all it seems that I have the exact same, problem, I installed Ubuntu 5.10 on AMD64 and I get no sound at all from ym onboard audio.

Things I did

a) I enabled from the BIOS the onboard audio (I used the AC97 Audio option and I set it to [Auto] - the pother option I had was [Disable])
b) The command lspci | grep snd gives me nothig as result
c) The command lsmod | grep snd gives me the following:

snd_intel8x0           34816  1
snd_ac97_codec         87000  1 snd_intel8x0
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  1 snd_pcm
snd                    55784  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         11408  2 snd_intel8x0,snd_pcm

d) Doing alsamixer the "Master" and "PCM" channels are enabled and on the 87 value

e) When I try to play a song on xmms I get the following error message:

Please check that:

Your soundcard is configured properly
You have the correct output plugin selected
No other porgram is blocking the soundcard

f) From System -> Preferences -> Sound I have selected Default sound card the NVidia CK804 (the only option I have)

g)  From System -> Preferences -> Multimedia Systems Selector 

if I choose ALSA and do a test it gives me the error message:

Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

if I choose ESD it is testing

if I choose OSS it gives me the error message:

Failed to construct test pipeline for 'OSS - Open Sound System'

I am not sure what is going on, any thoughts/help is appreciated.

Regards

Panos

---

### Post by ArmadaEnder on 2005-12-21
I believe I may have figured out my problem. I followed everything that Gandalf had suggested on this [page]("http://www.ubuntuforums.org/showthread.php?t=103304&page=2&highlight=sound") and I got sound but only through the left speaker on both my monitor and headphones. Then I started playing around with different devices (other headphones, speakers, etc) and I noticed that when I had the plug only half way in the jack on my mobo, I had sound in both speakers. My problem wasn't with ubuntu nor any software, but with my shitty old mobo. 

Now I need to go spend 15 bucks on a sounds card, only problem is I'm broke, it sucks being a college student, no money for anything. Ha well thank-you everyone who helped.

---

### Post by girionis on 2005-12-22
I bought a new sound card and it all works fine now :)

---

