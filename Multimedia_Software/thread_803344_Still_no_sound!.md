---
title: "Still no sound!"
date: 2008-05-22
forum: Multimedia Software
---

### Post by JollyGreenDragon on 2008-05-22
Trying to get the infamous X-Fi soundcard to work.

I've followed Temüjin's instructions ([http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)) for installing OSS, but I still get nothing.

ossdetect -v:

> Detected Creative SB X-Fi (EARLY BETA)
Detected Nvidia High Definition Audio (MCP55)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture


ossinfo:

> Version info: OSS 4.0 (b1015/200803240317) (0x00040003) 
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Azathoth)

Number of audio devices:	13
Number of audio engines:	29
Number of mixer devices:	3


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 nVidia HD Audio interrupts=412 (412)
    HD Audio controller nVidia HD Audio
    Vendor ID    0x10de0371
    Subvendor ID 0x017510de
     Codec  0: ALC888 (0x10ec0888/0x10de0175)
 2: sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=30523 (30523)
    PCI device 1102:0005, subdevice 1102:002c
 3: ossusb0 USB audio core services
 4: usb05560001-0 USB sound device
 5: usb05560001-1 USB sound device
 6: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio ALC888 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB046x/067x/ (Mixer 0 of device object 2)
 2: USB sound device (Mixer 0 of device object 4)

Audio devices
HD Audio front                    /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio rear                     /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio center/LFE               /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio side                     /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio pcm4                     /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 5)
HD Audio spdifout                 /dev/oss/hdaudio0/spdout1  (device index 6)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 7)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 8)
High Definition Audio spdif-in    /dev/oss/hdaudio0/spdin0  (device index 9)
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 10)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/sbxfi0/pcmin0  (device index 11)
USB sound device rec              /dev/oss/usb05560001-1/pcmin0  (device index 12)


Under System->Preferences->Sound, I tried testing under Autodetect, Alsa and Pulse:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

I'm thinking that OSS should be an option here - should I try reinstalling?

I have a feeling it's a botched install of OSS or my onboard sound. I cannot - or at least cannot figure out how to - disable the onboard sound on my nForce 780i.  Checked every menu, doesn't seem to be an option.

Thank you for your time.

~ Maro

---

### Post by JollyGreenDragon on 2008-05-30
Bump -_-

---

