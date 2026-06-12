---
title: "Karmic Koala no sound"
date: 2009-12-31
forum: Multimedia Software
---

### Post by etherealknight on 2009-12-31
I recently updated to Lucid Lynx and my sound still does not work...
The sound does work when I put headphones in though...
here are the lists of my outputs for the following commands:
hwinfo --sound

hwinfo --sound
28: PCI 10.1: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_26c
  Unique ID: wRyD.Ca3M1JwJNZ5
  SysFS ID: /devices/pci0000:00/0000:00:10.1
  SysFS BusID: 0000:00:10.1
  Hardware Class: sound
  Model: "Hewlett-Packard Company Presario V6133CL"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x026c "MCP51 High Definition Audio"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30b7 "Presario V6133CL"
  Revision: 0xa2
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xb0000000-0xb0003fff (rw,non-prefetchable)
  IRQ: 21 (32685 events)
  Module Alias: "pci:v000010DEd0000026Csv0000103Csd000030B7bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
and the contents of my alsabase.conf file
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
#options

---

### Post by etherealknight on 2009-12-31
help?

---

### Post by etherealknight on 2010-08-04
I now have lucid lynx and am still experiencing the same problems. I have no sound except through my headphones...

---

### Post by utilitytrack on 2010-08-04
Can you post here the output if these commands:```
$ uname -r


$ dpkg -l alsa-*


$ lspci -nn | grep Audio


$ cat /proc/asound/card0/codec#0 | grep Codec


# hwinfo --sound


$ cat /etc/modprobe.d/alsa-base.conf

```


and your PC/laptop model (it's you already gave us)
also recheck levels in [FONT='Courier New']alsamixer[/FONT]

---

### Post by etherealknight on 2010-08-09
2.6.32-24-generic
No packages found matching alsa-info.sh.
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
Codec: Conexant CX20549 (Venice)
27: PCI 10.1: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_26c
  Unique ID: wRyD.Ca3M1JwJNZ5
  SysFS ID: /devices/pci0000:00/0000:00:10.1
  SysFS BusID: 0000:00:10.1
  Hardware Class: sound
  Model: "Hewlett-Packard Company Presario V6133CL"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x026c "MCP51 High Definition Audio"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30b7 "Presario V6133CL"
  Revision: 0xa2
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xb0000000-0xb0003fff (rw,non-prefetchable)
  IRQ: 26 (1 event)
  Module Alias: "pci:v000010DEd0000026Csv0000103Csd000030B7bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Options
options snd-hda-intel model=dell-m4-3 enable_msi=1

Hp Pavilion 6119us
alsamixer is not working....

(update)
alsamixer is working the soundcard is being loaded and I only have sound in my earphones

---

### Post by utilitytrack on 2010-08-09
Aha, thank you for notification. You wrote that the sound present in headphones only. Ok, but I need know how to work the record on your laptop. Please run [FONT="Courier New"]alsamixer[/FONT], type F4 and make the levels up ("Capture", "Mic Boost", "Internal Mic Boost" and may be some other). If these controls are present then run the test (with internal and external mics):
```
$ arecord -vv -f cd -t wav sample.wav
```
And post here your impressions.

Also please say why this line are present in your [FONT="Courier New"]/etc/modprobe.d/alsa-base.conf[/FONT] file:
```
options snd-hda-intel model=dell-m4-3 enable_msi=1

```

---

### Post by etherealknight on 2010-08-09
ack... it is not detecting my card at all...
> options snd-hda-intel model=dell-m4-3 enable_msi=1 oh I was trying to figure out the model that worked... I no longer have that...

---

### Post by etherealknight on 2010-08-09
okay.. it is detecting my sound card... here are the results of the testing
```
arecord -vv -f cd -t wav sample.wav
Recording WAVE 'sample.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Plug PCM: Rate conversion PCM (48000, sformat=S32_LE)
Converter: libspeex (builtin)
Protocol version: 10002
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 7526
  period_size  : 940
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 940
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 7526
  silence_threshold: 0
  silence_size : 0
  boundary     : 986447872
Slave: Soft volume PCM
Control: Digital Capture Volume
min_dB: -30
max_dB: 30
resolution: 121
Its setup is:
  stream       : CAPTURE
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Direct Snoop PCM
Its setup is:
  stream       : CAPTURE
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 8192
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 8192
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : ENABLE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 1073741824
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0
####+                                              | 06%
####+                                              | 06%
####+                                              | 06%
####+                                              | 06%
####+                                              | 06%
Aborted by signal Interrupt...

```

---

### Post by etherealknight on 2010-08-09
I really do not know what to think of it...

---

### Post by petrus250 on 2010-08-09
simply purge pulse audio then reinstall it.

---

### Post by utilitytrack on 2010-08-09
I not understand nothing. Do you have a Hewlett-Packard Presario V6133CL laptop or not? Sound card are detected or not detected? Or you speak about some other problems? Please more definitely describe your troubles.

> *...here are the results of the testing*

You not understood me. I offer you make test and then **hear** the result. Outputs of arecord it's not intersting in this case.

And please don't send more messages to my PM. Please write all in this thread.

---

### Post by etherealknight on 2010-08-09
*sigh* I don't hear anything from the arecord...

---

### Post by etherealknight on 2010-08-09
> **utilitytrack said:**
> I not understand nothing. Do you have a Hewlett-Packard Presario V6133CL laptop or not? Sound card are detected or not detected? Or you speak about some other problems? Please more definitely describe your troubles.



You not understood me. I offer you make test and then **hear** the result. Outputs of arecord it's not intersting in this case.

And please don't send more messages to my PM. Please write all in this thread.

Alright...
I do not have a HP presario V6133CL.. I have an hp pavilion dv6119us model laptop
soundcard is detected as of now
my trouble is that my speakers are not working...
alright I will listen to the arecord...

---

### Post by etherealknight on 2010-08-09
Alright...
I do not have a HP presario V6133CL.. I have an hp pavilion dv6119us model laptop
soundcard is detected as of now
my trouble is that my speakers are not working...
alright I will listen to the arecord...

---

### Post by etherealknight on 2010-08-09
> **petrus250 said:**
> simply purge pulse audio then reinstall it.

I have already tried that

---

### Post by etherealknight on 2010-08-09
I don't hear anything from the arecord

---

### Post by utilitytrack on 2010-08-09
Ok. As I see it's difficult to speak with you. But because you still ask about help, I should help. Please run following command. This give me all neccesary info about your sound subsystem:
```
$ wget www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
After give here the link where located a ALSA information.

PS
See more about the alsa-info script on [https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems#Automatic%20Sound%20Information%20Collection")

---

### Post by etherealknight on 2010-08-09
[http://www.alsa-project.org/db/?f=f64e83b72843b2bf75dd734ae4cc365106e7d576]("http://www.alsa-project.org/db/?f=a4556199fc8eb570f4a2fd51f9cc3ca63ab9aa70")

here you go.

---

### Post by utilitytrack on 2010-08-09
I think that your troubles is more deep than I supposed earlier. You have a **Conexant CX20549 (Venice)** audio codec and as I see it hasn't properly support in ALSA subsystem. I hope that I'm mistaken, though.

Ok, you say that your attempt to record something was unsuccessful. I need clarity in this situation. Please enter to the BIOS on next reboot and very carefully to see on all sound-related options. For example, it may be disabled mic or soundcard. If something like this exists, enable it. Next try test recording (I already wrote how to do it). Also try test playing:
```
$ speaker-test -c2
```

Also two questions: in the system that you used before Ubuntu had these problems with sound? And why you named this thread as "Karmic Koala no sound" when you use Ubuntu 10.04.1 LTS? Or did you make the upgrade so quickly? Also please change the thread tags on "CX20549", "Conexant" and  "DV6119".

---

### Post by etherealknight on 2010-08-09
It has been several months since I made the first post... I since upgraded from Karmic to Lucid... I don't know how to get to audio options on my bios.. I don't see any... *sigh* The speaker test is going and I don't hear anything unless I plug in the earphones..

---

### Post by etherealknight on 2010-08-09
how do you edit the tags?

---

### Post by utilitytrack on 2010-08-09
> *I don't know how to get to audio options on my bios.. I don't see any... *

Is mutually exclusive statements.

> *how do you edit the tags?*

See on bottom of the page.

---

### Post by etherealknight on 2010-08-09
alright... Is there anything else I can do?

---

### Post by utilitytrack on 2010-08-09
At the moment I have not found anything that could be causing the problems to which you spoke except following:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5014]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5014")
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4710]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4710") 
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4163]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4163")
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/581546]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/581546")

All of this mean that support of CX20549 codec could be better. I can advice only recheck the BIOS settings and be sure that mini-jack plugs is not broken.

If you are sure that the problem is the driver, send a bug report on [ALSA bugtracking system]("https://bugtrack.alsa-project.org/alsa-bug/my_view_page.php")

---

### Post by etherealknight on 2010-08-09
> **utilitytrack said:**
> At the moment I have not found anything that could be causing the problems to which you spoke except following:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5014](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5014)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4710](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4710) 
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4163](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4163)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/581546](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/581546)

All of this mean that support of CX20549 codec could be better. I can advice only recheck the BIOS settings and be sure that mini-jack plugs is not broken.

If you are sure that the problem is the driver, send a bug report on [ALSA bugtracking system]("https://bugtrack.alsa-project.org/alsa-bug/my_view_page.php")

Thank you for your support, I will try these out and get back to you.:D

---

### Post by lidex on 2010-08-09
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by etherealknight on 2010-08-10
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thank you for your help, I tried to change the model, but I am still without sound. I only have one option for my output hardware and it says one input one output though I have 2 headphone jacks, 1 microphone jack, 2 mic holes on my screen a[IMG]file:///home/etherealknight/Desktop/Screenshot.png[/IMG]nd altec lansing speakers. Here is the updated alsa output

[http://www.alsa-project.org/db/?f=35f22418d806bb8c2c2fc2d2ed5b7af5cc039769](http://www.alsa-project.org/db/?f=35f22418d806bb8c2c2fc2d2ed5b7af5cc039769)

edit: also, all the levels are up in alsamixer

---

### Post by simosx on 2010-08-10
> **etherealknight said:**
> Thank you for your help, I tried to change the model, but I am still without sound. I only have one option for my output hardware and it says one input one output though I have 2 headphone jacks, 1 microphone jack, 2 mic holes on my screen a[IMG]file:///home/etherealknight/Desktop/Screenshot.png[/IMG]nd altec lansing speakers. Here is the updated alsa output

[http://www.alsa-project.org/db/?f=35f22418d806bb8c2c2fc2d2ed5b7af5cc039769](http://www.alsa-project.org/db/?f=35f22418d806bb8c2c2fc2d2ed5b7af5cc039769)

edit: also, all the levels are up in alsamixer

Thanks for the alsa-info.sh output. This helps to figure out what's going on.
The output looks generally OK; no major kernel issues and it shows that your hardware is detected. You have one analog output (headset or speakers) and a digital one (HDMI).

Your codec is Conexant CX20549 (Venice) which google brings about 
[http://kerneltrap.org/mailarchive/git-commits-head/2010/5/5/32501](http://kerneltrap.org/mailarchive/git-commits-head/2010/5/5/32501)
Alsa 1.0.23 was release in April 2010 while the above commit/fix was added in May 2010. It's possible you are affected by that bug.

What you can try is install the latest Alsa driver; not 1.0.23 but the snapshot. Try a snapshot from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) and get a new alsa-info.sh output.
Also, try out without a model specification (you have 'laptop', with parameters at the moment).

---

### Post by utilitytrack on 2010-08-10
to **simosx**

All of this we already know. But still it's some other driver issue, therefore I suggest to **etherealknight** to send a bug report about not properly work of CX20549 codec. As for other problem with it, "Fix 0 dB Conexant CX20549 (Venice)", I already saw this and **etherealknight** did not complain about it.

While I suppose that we can try to pass to module some other parameters except [FONT="Courier New"]model=laptop[/FONT] and hope to success. Just what? Is the question.

---

### Post by lidex on 2010-08-11
> **simosx said:**
> 
What you can try is install the latest Alsa driver; not 1.0.23 but the snapshot. Try a snapshot from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) and get a new alsa-info.sh output.
Also, try out without a model specification (you have 'laptop', with parameters at the moment).

Sounds like a good course of action.

---

### Post by etherealknight on 2010-08-11
I tried to install it but it stopped making the file with this error

```

  make -C  SUBDIRS=/home/etherealknight/alsa-driver-1.0.23.50.g68e3d.450.gf302c  CPP="gcc -E" CC="gcc" modules
make: *** SUBDIRS=/home/etherealknight/alsa-driver-1.0.23.50.g68e3d.450.gf302c: No such file or directory.  Stop.
make: *** [compile] Error 2

```

---

### Post by lidex on 2010-08-11
> **etherealknight said:**
> I tried to install it but it stopped making the file with this error

```

  make -C  SUBDIRS=/home/etherealknight/alsa-driver-1.0.23.50.g68e3d.450.gf302c  CPP="gcc -E" CC="gcc" modules
make: *** SUBDIRS=/home/etherealknight/alsa-driver-1.0.23.50.g68e3d.450.gf302c: No such file or directory.  Stop.
make: *** [compile] Error 2

```

Make sure build-essential is installed.
```
sudo aptitude install build-essential
```

---

### Post by etherealknight on 2010-08-12
> **lidex said:**
> Make sure build-essential is installed.
```
sudo aptitude install build-essential
```

Build essentials are installed, should I reinstall them?
I reinstalled them and even tried installing the snapshot via the alsa script, but it always stops there...
EDIT: Yay! I had to Go to line 163, which starts like:

$(MAKE) -C $(CONFIG_SND_KERNELBUILD) ........

and change it to:

$(MAKE) -C $(CONFIG_SND_KERNELDIR) .......

leaving the rest of the line the same.

it is now compiling, so, I will get back when I have the results.

Well, I ended up changing my OS to Windows 7 and am still having the same issue... XD oh lovely...

---

### Post by lidex on 2010-08-14
> **etherealknight said:**
> 
Well, I ended up changing my OS to Windows 7 and am still having the same issue... XD oh lovely...
Hate to see you go - what will I do with my spare time? ;)

If it's a cross-os problem it's either hardware or bios.
[http://h10025.www1.hp.com/ewfrf/wc/product?product=3250970&lc=en&cc=nz&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_nz/3250970/loc:0&cc=nz](http://h10025.www1.hp.com/ewfrf/wc/product?product=3250970&lc=en&cc=nz&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_nz/3250970/loc:0&cc=nz)
[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&product=3250970&](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&product=3250970&)
Or maybe you disabled something with a Fn key or switch. What have you done?

---

