---
title: "No sound via HDMI on Dell XPS 1330"
date: 2011-01-06
forum: Multimedia Software
---

### Post by Mckormick on 2011-01-06
Hi all

After a fresh install of 10.10 on a Dell XPS 1330 I cannot get any audio when connecting to an LCD TV via HDMI.  I get video no problem but sound only from internal speakers.

Under System/Preferences/Sound on the Hardware tab there is an profile entry for 'Digital Stereo (HDMI) Output' but if I select   this all goes silent.  

I checked alsamixer and nothing is muted.  The aplay -l output is below.

Please can anyone help?

Thanks!

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by lidex on 2011-01-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Jeebs on 2011-01-07
I had this same problem a couple weeks ago. I was using an AMD ATI HD3400 series card. I called AMD and they insisted that sound was enabled on the card and I spent days trying to figure it out. Bottom line, only ATI HD5000 or better supports sound via HDMI. There is a good chance that it's your card.

---

### Post by Mckormick on 2011-01-07
Thanks for the replies - link to the alsa-info output:

[http://bit.ly/hauY6W](http://bit.ly/hauY6W)

From searching I'm pretty sure the XPS1330 supports audio over HDMI.  I have the version with the Intel GMA X3100.

---

### Post by lidex on 2011-01-07
You may want to toggle this mixer control to one of the analog settings:
```
control.19 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Digital Playback'
		comment.item.1 ADAT
		comment.item.2 'Analog Mux 1'
		comment.item.3 'Analog Mux 2'
		comment.item.4 'Analog Mux 3'
		iface MIXER
		[COLOR="Red"]name 'IEC958 Playback Source'
		value 'Digital Playback'[/COLOR]
	}
```
You're sure s/pdif, iec958 elements are not muted in alsamixer?
What is your video driver?
Can you post these outputs please:
```
cat /var/log/Xorg.0.log | grep -i glx
sudo lshw -C display
```

And try updating ubuntu, I believe there is a newer kernel available.

---

### Post by Mckormick on 2011-01-09
Doh!  SPDIF/1 was muted in alsamixer but I didn't notice as it was off the right edge of the screen!

Unmuted it and all perfect now - thanks for your help and time!

---

### Post by lidex on 2011-01-09
I'm glad that's over =D>

---

### Post by coreyaray on 2011-01-10
I am also having the same problem. I followed the steps outlined here and still no sound through hdmi. Here is my alsa output

[http://www.alsa-project.org/db/?f=09752478f1ffd31286d046e66f25978a30dae5dc](http://www.alsa-project.org/db/?f=09752478f1ffd31286d046e66f25978a30dae5dc)

---

### Post by lidex on 2011-01-11
> **coreyaray said:**
> I am also having the same problem. I followed the steps outlined here and still no sound through hdmi. Here is my alsa output

[http://www.alsa-project.org/db/?f=09752478f1ffd31286d046e66f25978a30dae5dc](http://www.alsa-project.org/db/?f=09752478f1ffd31286d046e66f25978a30dae5dc)
This thread is not for you - try this one:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by achkap on 2011-01-15
i have the exact same problem. i ve been searching for a week now and i can t find anything that could do the trick. i ve tried many things but i cant have hdmi sound.
please, please someone solve this.
i have unmuted all the spdif from alsamixer, i ve put hdmi output at sound preferences i ve tried some other things that i can t remember right now.

the alsa output is 
[http://www.alsa-project.org/db/?f=acd4aba55fd7f3c5abe56bc80d85c137b7e001d6](http://www.alsa-project.org/db/?f=acd4aba55fd7f3c5abe56bc80d85c137b7e001d6)

and my aplay -l
achilleas@achilleas-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

thank you...

---

### Post by achkap on 2011-01-15
i have the exact same problem. i ve been searching for a week now and i can t find anything that could do the trick. i ve tried many things but i cant have hdmi sound.
please, please someone solve this.
i have unmuted all the spdif from alsamixer, i ve put hdmi output at sound preferences i ve tried some other things that i can t remember right now.

the alsa output is 
[http://www.alsa-project.org/db/?f=acd4aba55fd7f3c5abe56bc80d85c137b7e001d6](http://www.alsa-project.org/db/?f=acd4aba55fd7f3c5abe56bc80d85c137b7e001d6)

and my aplay -l
achilleas@achilleas-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia_1 [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

thank you...

---

### Post by tjones00 on 2011-01-15
Try this achkap.

gksudo gedit /etc/modprobe.d/sound.conf

add this to the file

options snd-hda-intel probe_mask=0x04

Save the file and reboot.

I found this in your alsa info.

```
Codec: Nvidia GPU 0a HDMI/DP
Address: 0
Function Id: 0x1
Vendor Id: 0x10de000a
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 0a HDMI/DP
Address: 1
Function Id: 0x1
Vendor Id: 0x10de000a
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 0a HDMI/DP
Address: 2
Function Id: 0x1
Vendor Id: 0x10de000a
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=8
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GPU 0a HDMI/DP
Address: 3
Function Id: 0x1
Vendor Id: 0x10de000a
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=9
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
```

You do have a recognized hdmi connection on device 7 of your nvidia card. Try using the node call (0x04) in sound.conf to get it setup as default. If it doesn't work the first time try updating the initramfs and see if it works then. Sometimes edits to /etc/modprobe.d/ don't get picked up unless you update initramfs.

The easy way is to just sudo update-grub2 this should force an initramfs update.

---

### Post by achkap on 2011-01-15
my sound.conf file is empty. is it supposed to be like that?
if it is, i only add the line you said?
and thank you again for your quick reply

and i have already done (for another reason) the sudo update-grub2 command. but still i have the same problem

---

### Post by tjones00 on 2011-01-15
Try it again now I just realized I forgot the probe_mask part.

We're trying to tell snd-hda-intel hey dummy look at device 7

---

### Post by tjones00 on 2011-01-15
Well at any rate keep playing around with the probemask using values from that cat codec output.

More info about setting up hdmi on nvidia with multiple devices.

[http://ubuntuforums.org/showpost.php?p=9732345&postcount=8](http://ubuntuforums.org/showpost.php?p=9732345&postcount=8)

Yours is device 7 btw.

---

### Post by achkap on 2011-01-15
> **tjones00 said:**
> Try it again now I just realized I forgot the probe_mask part.

We're trying to tell snd-hda-intel hey dummy look at device 7

hmmmmmm.....
i don t know much from commands in linux...
sorry...
can you write me the command i should use?

---

### Post by tjones00 on 2011-01-15
He no problem every one of us had to learn this stuff at some time.

First confirm which device is responsible for audio.

Open a terminal Applications > Accessories > Terminal and type:
```

cat /proc/asound/card1/eld#1.0
```

If you see an output that has a line stating "monitor_present 1" and a bunch of other stuff your device is 1,7

If you don't see that output go and read the link that I posted.

Now if you've confirmed what device is recognized as an hdmi audio connection on your nvidia card in alsa. (cat /proc/asound/card1/#1.0 returned monitor_present 1)

Go back to that link I posted and make the asound.conf and default.pa edits described in the post setting them up for your device (which you established with the cat /proc/* step)

---

### Post by achkap on 2011-01-15
ok i did what you said. and i followed the link you gave me. and yes... i have audio from my tv. changing the audio.conf file and adding the line with the correct device did the thing that i have been trying for nearly one month... thank you very very much. but...
but now i don t have sound on my desktop.
i know that i can delete the entry from sound.conf file, reboot, and have sound from desktop (iknow, i tried it). but not from tv. isn t there a simplier way to change between outputs? i mean without rebooting.

i tried also to configure pulse (as the tutorial said) but it didn t work.

and again thank you very much for your help

---

### Post by lidex on 2011-01-16
> **achkap said:**
> ok i did what you said. and i followed the link you gave me. and yes... i have audio from my tv. changing the audio.conf file and adding the line with the correct device did the thing that i have been trying for nearly one month... thank you very very much. but...
but now i don t have sound on my desktop.
i know that i can delete the entry from sound.conf file, reboot, and have sound from desktop (iknow, i tried it). but not from tv. isn t there a simplier way to change between outputs? i mean without rebooting.

i tried also to configure pulse (as the tutorial said) but it didn t work.

and again thank you very much for your help

Have you tried changing your input/soundcard in 'sound preferences'?

---

### Post by tjones00 on 2011-01-16
If the probemask works for aplay hdmi:NVidia try:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hdmi:NVidia
```

in /etc/pulse/default.pa  If it doesn't work after that make sure you delete any local pulseaudio settings for the user so pulseaudio will use the default systemwide conf (default.pa)

---

