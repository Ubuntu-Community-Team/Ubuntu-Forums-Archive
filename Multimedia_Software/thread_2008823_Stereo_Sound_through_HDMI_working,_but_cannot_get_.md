---
title: "Stereo Sound through HDMI working, but cannot get 5.1 surround sound to work!"
date: 2012-06-23
forum: Multimedia Software
---

### Post by bultmann on 2012-06-23
I have an Nvidia GTS450 which is connected to a wireless HDMI transmitter. It transmits to my TV and from there it goes to my receiver. I am running Ubuntu 12.04. 

In pavucontrol I selected Digital Stereo (HDMI) Output, and it works beautifully. However, for surround sound (5.1) it showed only 1 option and it didn't work. So I followed the instructions in this post: [http://www.momentaryfascinations.com/technology/getting.7.1.hdmi.audio.working.under.ubuntu.html](http://www.momentaryfascinations.com/technology/getting.7.1.hdmi.audio.working.under.ubuntu.html). 

After adding the 5.1 entries, the extra-hdmi.conf file has these entries: 

[Mapping hdmi-stereo]
device-strings = hdmi:%f
description = Digital Stereo (HDMI) 0
paths-output = hdmi-output-0
channel-map = left,right
priority = 4
direction = output

[Mapping hdmi-surround]
description = Digital Surround 5.1 (HDMI) 0
device-strings = hdmi:%f
paths-output = hdmi-output-0
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
priority = 3
direction = output

[Mapping hdmi-stereo-extra1]
description = Digital Stereo (HDMI) 1
device-strings = hdmi:%f,1
paths-output = hdmi-output-1
channel-map = left,right
priority = 2
direction = output

[Mapping hdmi-surround-extra1]
description = Digital Surround 5.1 (HDMI) 1
device-strings = hdmi:%f,1
paths-output = hdmi-output-1
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
priority = 1
direction = output

[Mapping hdmi-stereo-extra2]
description = Digital Stereo (HDMI) 2
device-strings = hdmi:%f,2
paths-output = hdmi-output-2
channel-map = left,right
priority = 2
direction = output

[Mapping hdmi-surround-extra2]
description = Digital Surround 5.1 (HDMI) 2
device-strings = hdmi:%f,2
paths-output = hdmi-output-2
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
priority = 1
direction = output

[Mapping hdmi-stereo-extra3]
description = Digital Stereo (HDMI) 3
device-strings = hdmi:%f,3
paths-output = hdmi-output-3
channel-map = left,right
priority = 2
direction = output

[Mapping hdmi-surround-extra3]
description = Digital Surround 5.1 (HDMI) 3
device-strings = hdmi:%f,3
paths-output = hdmi-output-3
channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
priority = 1
direction = output


After rebooting the computer, I had three 5.1 options in pavucontrol, but none of them worked. The one that I really need (1) is not showing up in the GUI! I read somewhere that I have to add the same entries to the default.conf. So I tried that as well, but again, the one entry that I need still does not show up in the GUI. Any idea what I am missing? Thanks!

Oh, and I don't know if this helps, here is the output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by BicyclerBoy on 2012-06-23
The TVs ELD/EDID is controlling the audio capability reported to alsa/pulse.

AFAIK Most (maybe all) TVs do not output anything other than stereo. They are not likely to transcode because that requires a licence. Some may output AC3 if the original has this stream.

How is the TV connected to the HT amp HDMI audio return link or S/PDIF cable ?

The S/PDIF link can only carry stereo & AC3/DTS with no handshaking or capability reporting.

You can check the HDMI cap reported by looking at eld files..
dmesg | grep HDA
cat /proc/asound/card1/eld#3.0

---

### Post by bultmann on 2012-06-25
Thanks for the answer. Not sure what to do with it, but here's the output of 

dmesg | grep HDA
cat /proc/asound/card1/eld#3.0:

[   19.198273] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   19.198345] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.198419] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.198496] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.198562] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.198628] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.198694] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   19.198756] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   20.165168] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:05.0/0000:02:00.1/sound/card1/input15
[   20.165357] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:05.0/0000:02:00.1/sound/card1/input16
[   20.165547] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:05.0/0000:02:00.1/sound/card1/input17
[   20.165734] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:05.0/0000:02:00.1/sound/card1/input18

monitor_present		0
eld_valid		0


The amp is connected to the TV through an HDMI cable. 

So if the TV doesn't output 5.1 because of a license problem, would it be any different if I connected the HDMI transmitter directly to my amp (maybe the extra AUX HDMI input) and go to the TV from there? I might have to try that some time this week.

---

### Post by BicyclerBoy on 2012-06-25
Your above output shows no eld or monitor detected on hdmi card 1 device 9..

I should have asked about the video driver..
You have to use nvidia proprietary video driver to get the hdmi audio working..
But there may be some support in nouveau..

Audio return channel is negotiated between hdmi 1.4 devices..
Don't know if it supports more than stereo..
It is very unlikely your TV does any transcoding..

PC --> amp --> TV is the arrangement most likely to work.

The hot-plug problems:
- capability reporting only occurs when devices are switched on.
- AIUI devices modify the EDID/ELD as they pass it thru'.


Back to basic debugging:
In a terminal run
speaker-test -l 4 -c 2 -r 48000 -D hw:1,9
speaker-test -l 4 -c 2 -r 48000 -D hw:1,8
speaker-test -l 4 -c 2 -r 48000 -D hw:1,7
speaker-test -l 4 -c 2 -r 48000 -D hw:1,3

which one makes pink noise ?

---

### Post by bultmann on 2012-06-25
So I tried those four lines in a terminal with my original setup and I got pink noise for the third line: 

speaker-test -l 4 -c 2 -r 48000 -D hw:1,7

So next I connected my the wireless HDMI receiver to my amp instead of the TV and I rebooted my computer. I opened pavucontrol and the options that I needed finally showed up in the gui! I selected 5.1 surround sound and it works! I did a speaker test and all of them work. So it looks like you were right about the ELD/EDID thing. That kinda sucks that the TV doesn't give the right response. 

Even though 5.1 is now working with this new setup, there are some new problems. The audio sounds very boxy, I don't know if this is a problem with my amp settings or something else, but I know that 5.1 coming from the TV sounds great. It just seems like all the high tones are missing. When I switch back to 2.1, then everything sounds great again. 

Also, the resolution is not what it is supposed to be, the picture is kinda bad. Again, that could be a problem with the settings on my amp, I guess I have to play with that a little more.

---

### Post by BicyclerBoy on 2012-06-26
The device hw:1,7 should link to /proc/asound/card1/eld#1.0.

AFAIK The nVidia driver is required for HDMI audio.

"5.1" means lots of things..this can be supported over HDMI as multi-channel PCM, AC3/DTS & HDA formats..

To test multi-ch PCM over HDMI:
speaker-test -l 4 -c 6 -r 48000 -D hw:1,7
speaker-test -l 4 -c 8 -r 48000 -D hw:1,7
Can only use this to test raw audio formats.

Video:
Use nvidia-settings to dump the EDID or look into /var/log/Xorg.0.log.
This is a /etc/X11/xorg.conf option to debug videomodes.

Dumping EDID & re-applying it manually could fix the video but screw up the audio..

Dof-dof:
Any good HT amp has LFE setup/config for speaker arrangement & size etc.
Some US TV shows love LFE.

You might have EDID management options in the HT amp.

---

