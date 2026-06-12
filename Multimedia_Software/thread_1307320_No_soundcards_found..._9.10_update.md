---
title: "No soundcards found... 9.10 update"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Eman64 on 2009-10-31
I have seen many people updating their grub and their alsa to the appropriate versions to fix this, but I still have had no luck. This is the only problem I'm currently having with the new update. Anyone wanna help me through a halloween of figuring this out?

```
user@comp:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

```
user@comp:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by Eman64 on 2009-10-31
[http://pastebin.ca/1650420]("http://pastebin.ca/1650420")

```
user@computer:~$ cat /proc/asound/cards;  sudo aptitude install gnome-alsamixer asoundconf-gtk alsa-utils flashplugin-nonfree-extrasound;  asoundconf list;  aplay -l;  sudo lshw -C sound;  ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl;  lsmod | grep snd
--- no soundcards ---
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

asoundconf: command not found
aplay: device_list:223: no soundcards found...
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fdff8000-fdffbfff
total 0
crw-rw----+  1 root audio 116, 33 2009-10-31 08:20 timer
crw-rw----+  1 root audio 116,  1 2009-10-31 08:20 seq
drwxr-xr-x   2 root root       80 2009-10-31 08:20 .
drwxr-xr-x  16 root root     4000 2009-10-31 08:31 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux Taos 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7300 GT] [10de:0393] (rev a1)
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
/usr/sbin/alsactl
snd_hda_intel          26560  0 
snd_hda_codec          78300  1 snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
snd_pcm_oss            37312  0 
snd_mixer_oss          16188  1 snd_pcm_oss
snd_pcm                74976  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29280  0 
snd_seq_midi            6624  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                51088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60900  13 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9060  2 snd_hda_intel,snd_pcm

```

Hope these can help you guys.

---

### Post by Eman64 on 2009-10-31
[http://pastebin.ca/1650827]("http://pastebin.ca/1650827")

Updated my ALSA libraries. Same aplay -l results, however. Please help if you can.

---

### Post by pblarry49 on 2009-10-31
I'm having the same problem...I continue to search

---

### Post by psd99 on 2009-10-31
same here well almost

it is so very frustrating
arghhhhhhhhhhhhhhhhhhhhh

---

### Post by Eman64 on 2009-11-01
If it helps anyone, sound does not work in a different user either.
Please help if possible.

---

### Post by Eman64 on 2009-11-02
```
user@comp:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861-VD Digital [ALC861-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Don't know how this happened, but my cards are now being picked up. But alas, no sound!

---

### Post by frznlogic on 2009-11-03
I was having the same problem with ALC861 on a Toshiba Satellite A100-178. After some tinkering i realized my modprobe.d was incorrectly setup. I winded up blacklisting the modem part (not sure this is necessary, but the less things to go wrong, the better):

oan@laptop4:/etc/modprobe.d$ tail -n1 blacklist-modem.conf 
snd_hda_codec_si3054

And most importantly, i removed/disabled all power-savings junk etc from the options for snd-hda-intel module:

[FONT=monospace]oan@laptop4:/etc/modprobe.d$ tail alsa-base.conf -n2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=0 enable_msi=1 model=ICH7

Experiment a bit with the power_save and power_save_controller options, as described in:

oan@laptop4:/etc/modprobe.d$ less /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz 

In the end, I just made all the changes in one go and rebooted, and now it works. I haven't tried the different combinations of options, so if you feel like it, try to just set the model= correctly. Maybe you get lucky. 

I hope this is some use and good luck!
[/FONT]

---

### Post by coldsystem on 2009-11-05
Please follow this wonderfull link . i got the same issue , but Now iam enjoying my Music :)
please  follow  the  instructions and  should  be  fine  : 
[http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)

---

### Post by Ulysses361 on 2009-11-06
@Eman64: your sound issue seems to be caused by this:

# Modprobe options (Sound related)
# --------------------------------
#  
# snd-hda-intel: model=3stack-dig
# snd-hda-intel: enable_msi=1
# snd-hda-intel: single_cmd=1
# snd-hda-intel: model=dell-m81
# snd-atiixp-modem: index=-2
# snd-intel8x0m: index=-2
# snd-via82xx-modem: index=-2
# snd-usb-audio: index=-2
# snd-usb-us122l: index=-2
# snd-usb-usx2y: index=-2
# snd-usb-caiaq: index=-2
# snd-cmipci: mpu_port=0x330 fm_port=0x388
# snd-pcsp: index=-2
# snd-hda-intel: model=auto

The wrong snd-hda-intel model options are set in  /etc/modprobe.d/alsa-base.conf

These wrong model options are causing the following error in the dmesg output:

# [   31.976160] ALSA hda_intel.c:1382: Codec #2 probe error; disabling it...
# [   32.008451] ALSA hda_intel.c:1408: no codecs initialized

First remove all model options from alsa-base.conf, save the change, reboot and retest sound. 

If that does not help, please proceed with this procedure:


# Open a terminal and enter the following command:

gksudo gedit /etc/modprobe.d/alsa-base.conf

# Add the following line at the end of the alsa-base.conf file and save the change:

options snd-hda-intel model=3stack

Reboot pc and retest headphones.

If 3stack does not work, try replacing the options line with this:

options snd-hda-intel model=lenovo

Then reboot and retest sound.

Here are the other possible "model" options for the ALC861VD. You might need to experiment with these model options to find one that makes both speakers and headphones work.

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

Hope this helps....

---

### Post by andrewj100 on 2009-11-06
Thanks Ulysses361 for....

# Open a terminal and enter the following command:
gksudo gedit /etc/modprobe.d/alsa-base.conf
# Add the following line at the end of the alsa-base.conf file and save the change:
options snd-hda-intel model=3stack

This worked for me on a Toshiba Satellite pro A120.

---

### Post by seifertd on 2009-11-10
I had made edits to /etc/modprobe.d/alsa-base.conf.  When upgrading, I was asked if I wanted to overwrite this file.  I answered no.  The upgrade process created a file called /etc/modprobe.d/alsa-base.conf.dpkg-dist.

I backed up /etc/modprobe.d/alsa-base.conf and copied over it with the dpkg-dist file:

sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.bak
sudo cp /etc/modprobe.d/alsa-base.conf.dpkg-dist /etc/modprobe.d/alsa-base.conf

then

sudo alsa force-reload

got sound working again.

---

### Post by jeangot on 2009-11-12
I too had the "no soundcard found" problem after upgrading from 09.04 to 09.10
I solved it by commenting out the line
options snd-hda-intel power_save=10 power_save_controller=N

at the end of /etc/modprobe.d/asla-base.conf

then doing 
sudo alsa force-reload

and presto, the sound card was back.

Jean

---

### Post by Eman64 on 2009-11-16
Ok, so I have tried what you recommended, Ulysses361, but it did not work. I still have a sound card that shows 0.00 dB when turned up all the way.

---

### Post by andrewj100 on 2009-12-20
> **andrewj100 said:**
> Thanks Ulysses361 for....

# Open a terminal and enter the following command:
gksudo gedit /etc/modprobe.d/alsa-base.conf
# Add the following line at the end of the alsa-base.conf file and save the change:
options snd-hda-intel model=3stack

This worked for me on a Toshiba Satellite pro A120.

After a few months of this running without a problem I now have to run sudo alsa force-reload every time I reboot my laptop, I dont have to change any files just run the reload. I'm guessing something hasnt been initialised when the conf file is run, any ideas?

---

### Post by efflandt on 2009-12-20
Did you activate any special hardware driver for a modem.  Winmodem drivers can interfere with sound.  Because of that I did NOT activate the driver for the modem in my Toshiba laptop and have had no problems with sound after 9.04 to 9.10 upgrade.

One other thing that can make sound not work is booting a Jaunty kernel in Karmic.

---

### Post by mrwoody on 2010-01-20
I have this sound card:

```

$ lspci|grep Audio
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)

```

and I also get this error:
```

$ aplay -l 
aplay: device_list:223: no soundcards found...

```

It used to work before I upgraded to 9.10. 

Does anyone have any hint on how to fix this?

---

### Post by mrwoody on 2010-01-20
I switched to OSS 
[https://help.ubuntu.com/community/OpenSound#Installing](https://help.ubuntu.com/community/OpenSound#Installing)
and now it works great (probably even better than earlier on with alsa).

---

### Post by Yellow Pasque on 2010-01-20
mrwoody, your link takes the user to the middle of the document and skips over important preparation.

---

### Post by mrwoody on 2010-01-20
> **Temüjin said:**
> mrwoody, your link takes the user to the middle of the document and skips over important preparation.

ok... thanks for the remark. I changed it.

---

