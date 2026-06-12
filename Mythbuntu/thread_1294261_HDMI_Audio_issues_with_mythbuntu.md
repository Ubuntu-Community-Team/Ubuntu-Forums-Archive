---
title: "HDMI Audio issues with mythbuntu"
date: 2009-10-18
forum: Mythbuntu
---

### Post by matmbl on 2009-10-18
Hi All,

I've finally dumped Vista MC and have install Mythbuntu and am (almost) very happy, 40" LCD, 1080p, Shuttle SG33G5, NOVA-T-500 DVB-T all working (almost) great. There's just a couple of little issues to be solved and I'm hope you guys can help

1. No Audio over the HDMI link: I've a Shuttle SG33G5 and have been running Vista MC happily (when it doesn't crash/run out of memory/etc) with audio on HDMI. With mythbuntu (9.04) I can't get audio working. I've got to the point where I have HDMI audio configured correctly in linux (if I do a speaker-test -Dhdmi:Intel I get sound!) but I can't figure out what to set it up as in mythtv??

I've typed hdmi:Intel into the General Setup/Audio page and randomly played with the other settings but to no joy! So I'm a little stuck!


2. My NOVA-T-500 DVB-T keeps loosing signal lock (so I have to reboot to get it back). I've just downgraded the firmware to 1.10 and it hasn't happened again in the last 30mins so maybe?!?!? Anyway, lets leave that one for now!


If anyone can help (and advise what info you need to help) that would be great!!!

Thanks

Matt

---

### Post by jyavenard on 2009-10-18
> **matmbl said:**
> Hi All,

I've finally dumped Vista MC and have install Mythbuntu and am (almost) very happy, 40" LCD, 1080p, Shuttle SG33G5, NOVA-T-500 DVB-T all working (almost) great. There's just a couple of little issues to be solved and I'm hope you guys can help

1. No Audio over the HDMI link: I've a Shuttle SG33G5 and have been running Vista MC happily (when it doesn't crash/run out of memory/etc) with audio on HDMI. With mythbuntu (9.04) I can't get audio working. I've got to the point where I have HDMI audio configured correctly in linux (if I do a speaker-test -Dhdmi:Intel I get sound!) but I can't figure out what to set it up as in mythtv??



Did you make sure the audio isn't muted (it's the default when upgrading alsa kernel module) ?

What does aplay -l and play -L return?

["I've typed hdmi:Intel into the General Setup/Audio page and "]

this is *never* going to work. that's not even a valid device name ; what made you think you could use that ?

---

### Post by matmbl on 2009-10-18
> **jyavenard said:**
> Did you make sure the audio isn't muted (it's the default when upgrading alsa kernel module) ?


How do I check that? I've gone into the 
"Mixer" on the desktop, "IEC958 2" is unchecked under Switches, checking this enables speaker-test to work!?

(BTW. I'm a little new to "desktop" linux (I've a headless server running for years but I don't need sound for that!)


> **jyavenard said:**
> 
What does aplay -l and play -L return?


mat@tvpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mat@tvpc:~$ aplay -L
default:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


> **jyavenard said:**
> 
["I've typed hdmi:Intel into the General Setup/Audio page and "]

this is *never* going to work. that's not even a valid device name ; what made you think you could use that ?

Err, 'cos speaker-test -Dhdmi:Intel works!!! devices are devices yes ?? :-)

Thanks for the response.

Matt

---

### Post by jyavenard on 2009-10-18
[QUOTE=matmbl;8123060]How do I check that? I've gone into the 
"Mixer" on the desktop, "IEC958 2" is unchecked under Switches, checking this enables speaker-test to work!?

(BTW. I'm a little new to "desktop" linux (I've a headless server running for years but I don't need sound for that!)




mat@tvpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[QUOTE]

So set your audio device as 
ALSA:plughw:0,3

and passthrough as "default" or ALSA:plughw:0,3
check AC3 and DTS.

Set speakers to "stereo" if using 0.21 or 0.22.
Set speakers to "5.1" if using trunk >= 22432

hdmi:Intel has *never* been a valid audio device in myth, and never will be...

There are documentation and a wiki on [www.mythtv.org](www.mythtv.org) were everything is clearly explained

---

### Post by matmbl on 2009-10-18
> 

So set your audio device as 
ALSA:plughw:0,3

and passthrough as "default" or ALSA:plughw:0,3
check AC3 and DTS.

Set speakers to "stereo" if using 0.21 or 0.22.
Set speakers to "5.1" if using trunk >= 22432

hdmi:Intel has *never* been a valid audio device in myth, and never will be...

There are documentation and a wiki on [www.mythtv.org](www.mythtv.org) were everything is clearly explained

Many thanks, I did that last time but..... doooh!!!! I typed plugw0,3 !!!!!

many thanks for the help 

Matt

---

### Post by jyavenard on 2009-10-18
> **matmbl said:**
> Many thanks, I did that last time but..... doooh!!!! I typed plugw0,3 !!!!!

many thanks for the help 

Matt

hum... the entry hw0,3 is an entry in the existing list in the configuration screen, just using the arrow keys and selecting the right one is all you need (on 0.22 that is).

---

### Post by WhistlerUK on 2009-10-19
> **matmbl said:**
> 2. My NOVA-T-500 DVB-T keeps loosing signal lock (so I have to reboot to get it back). I've just downgraded the firmware to 1.10 and it hasn't happened again in the last 30mins so maybe?!?!? Anyway, lets leave that one for now!



Sounds like the crappy USB Disconnects problem that these cards have. I know its proberly PCI card but the chips on them are seen as USB devices.
I got the same problem using the 1.10 FW, I upgraded to the 1.20 FW and it solved the problem for about 1 month and appears to have gone back to droping the lock again, going to try reloading the firmware again myself, when you update the FW you need to make sure the card is in "Cold State" to make sure the card is in Cold State shut the machine down and unplug it from the mains leave it for a few minutes to make sure all power is discharged (I read someone say they left theres over night to make sure, but I think that was over kill lol) power it back up and grep the dmesg to make sure it has loaded the new firmware, I had to rename dvb-usb-dib0700-1.20.fw to dvb-usb-dib0700-1.10.fw  to get it recognised and loaded as it looks for the 1.10 fw file.

Hope this helps you.

---

### Post by matmbl on 2009-10-19
> **jyavenard said:**
> hum... the entry hw0,3 is an entry in the existing list in the configuration screen, just using the arrow keys and selecting the right one is all you need (on 0.22 that is).

Didn't seem to appear on my list !! (hence my tpying hdmi:Intel :-) ). Still, all working now

---

### Post by matmbl on 2009-10-19
> **WhistlerUK said:**
> Sounds like the crappy USB Disconnects problem that these cards have. I know its proberly PCI card but the chips on them are seen as USB devices.
I got the same problem using the 1.10 FW, I upgraded to the 1.20 FW and it solved the problem for about 1 month and appears to have gone back to droping the lock again, going to try reloading the firmware again myself, when you update the FW you need to make sure the card is in "Cold State" to make sure the card is in Cold State shut the machine down and unplug it from the mains leave it for a few minutes to make sure all power is discharged (I read someone say they left theres over night to make sure, but I think that was over kill lol) power it back up and grep the dmesg to make sure it has loaded the new firmware, I had to rename dvb-usb-dib0700-1.20.fw to dvb-usb-dib0700-1.10.fw  to get it recognised and loaded as it looks for the 1.10 fw file.

Hope this helps you.

I left mythtv "watching tv" all night (oops, didn't realise it recorded everything). But all seems pretty stable now. I've downgraded firmware to 1.10 (renamed the file to 1.20) and also added the following into modprobe.d/options.conf

options dvb-usb-dib0700 force_lna_activation=1
options dvb_usb disable_rc_polling=1
options usbcore autosuspecd=-1

I would say the last one seems to have done the trick for me but I now see this is another example of my in-ability to type! Must be just the firmware swap!

Thx

Matt

---

