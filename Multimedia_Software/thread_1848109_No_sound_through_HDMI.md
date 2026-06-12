---
title: "No sound through HDMI"
date: 2011-09-22
forum: Multimedia Software
---

### Post by Ulysses4ever on 2011-09-22
When I plug in my HDMI cable in video card in order to watch movie on my TV in my Multimedia &#8212; Sound &#8212; Video preferences window I see HDMI and built-in analog device. When later get higher priority then former I can hear movie sound (playing through Dragon Player) from PC speakers. When I reverse the order I expect TV to play movie sound (which is what I really want) but get *no sound at all*.

Any suggestions how to get sound through HDMI? (Looked through forum but didn't find solution&#8230;)

---

### Post by BicyclerBoy on 2011-09-22
To help figure out a soln we could need to know:
video card
lspci | grep VGA
video driver
ubuntu distro or the kernel version..
uname -r

Post the output from these terminal commands:
aplay -l
speaker-test   (report just the alsa version)

---

### Post by Ulysses4ever on 2011-09-22
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
```
```
$ aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC883 Analog [ALC883 Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC883 Digital [ALC883 Digital]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 2: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 2: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 7: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 2: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 8: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 2: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 9: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
```
Didn't get what you meant under “speaker-test (report just the alsa version)”.```
$ speaker-test

speaker-test 1.0.24.2

&#1059;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#1076;&#1083;&#1103; &#1087;&#1088;&#1086;&#1080;&#1075;&#1088;&#1099;&#1074;&#1072;&#1085;&#1080;&#1103; - default
&#1055;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; &#1087;&#1086;&#1090;&#1086;&#1082;&#1072; - 48000&#1043;&#1094;, S16_LE, 1 &#1082;&#1072;&#1085;&#1072;&#1083;&#1086;&#1074;
&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; 16 &#1086;&#1082;&#1090;&#1072;&#1074; "&#1088;&#1086;&#1079;&#1086;&#1074;&#1086;&#1075;&#1086;" &#1096;&#1091;&#1084;&#1072;
&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1085;&#1072; &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072; &#1074; 48000&#1043;&#1094; (&#1079;&#1072;&#1087;&#1088;&#1086;&#1096;&#1077;&#1085;&#1086; 48000&#1043;&#1094;)
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1073;&#1091;&#1092;&#1077;&#1088;&#1072; &#1086;&#1090; 192 &#1076;&#1086; 2097152
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1087;&#1077;&#1088;&#1080;&#1086;&#1076;&#1072; &#1086;&#1090; 64 &#1076;&#1086; 699051
&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1084;&#1072;&#1082;&#1089;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1088;&#1072;&#1079;&#1084;&#1077;&#1088; &#1073;&#1091;&#1092;&#1077;&#1088;&#1072; 2097152
&#1055;&#1077;&#1088;&#1080;&#1086;&#1076;&#1099; = 4
&#1073;&#1099;&#1083; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; period_size = 524288
&#1073;&#1099;&#1083; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; buffer_size = 2097152
 0 - &#1055;&#1077;&#1088;&#1077;&#1076;&#1085;&#1080;&#1081; &#1083;&#1077;&#1074;&#1099;&#1081;
&#1042;&#1088;&#1077;&#1084;&#1103; &#1074; &#1087;&#1077;&#1088;&#1077;&#1080;&#1086;&#1076;&#1077; = 12,946741
```(Sorry for localised output...)

---

### Post by Ulysses4ever on 2011-09-22
```
$ uname -r
2.6.38-8-generic
```

---

### Post by BicyclerBoy on 2011-09-22
That info is all good..
Try:
speaker-test -c 2 -r 48000 -D hw:2,9

should hear pink noise directed at each channel.

If no noise, try changing 9 --> 8, 7, 3

Look for presence detect event:
dmesg | grep HDMI

If you get noise from hw:2,9 then..
Look for audio EDID ELD data from HDMI audio receiver..
cat /proc/asound/card2/eld#3.0

---

### Post by Ulysses4ever on 2011-09-23
BicyclerBoy! After reboot my aplay -l changed slightly:
```
~$ aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC883 Analog [ALC883 Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC883 Digital [ALC883 Digital]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 7: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 8: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 9: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
```
So the card number is 1 not 2 and I tried
```
speaker-test -c 2 -r 48000 -D hw:1,{9,8,7,3}
```
And I heard noise from TV screen only with hw:1,**8**. 

```
~$ dmesg | grep HDMI
[ 1517.231288] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[ 1517.281005] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[ 1518.100033] HDMI: detected monitor Panasonic-TV at connection type HDMI
[ 1518.100040] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[ 1518.876013] HDMI: detected monitor Panasonic-TV at connection type HDMI
[ 1518.876018] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
```

Then I tried 
```
~$ cat /proc/asound/card1/eld#{3,2,1}.0
```
and got `monitor_present`=1 only for eld#1.0:
```
~$ cat /proc/asound/card1/eld#1.0 
monitor_present         1
eld_valid               1
monitor_name            Panasonic-TV
connection_type         HDMI
eld_version             [0x2] CEA-861D or below
edid_version            [0x3] CEA-861-B, C or D
manufacture_id          0xa934
product_id              0xa0a6
port_id                 0x20000
support_hdcp            0
support_ai              0
audio_sync_delay        0
speakers                [0x0]
sad_count               1
sad0_coding_type        [0x1] LPCM
sad0_channels           2
sad0_rates              [0xe0] 44100 48000 88200
sad0_bits               [0x20000] 16
```(Trully, I connect my cable to Panasonic TV.)

---

### Post by BicyclerBoy on 2011-09-23
I find it very odd that the eld#1.0 seems to match up with hw:1,8
I expected:
 eld#0.0 == hw:1,3
 eld#1.0 == hw:1,7 etc...

What caused the soundcard number to change from 2 -->1 ?
Do you have any snd_hda_intel module options in /etc/modprobe.d/*.conf files ?
Did you have a kernel update ?

But if hw;1,8 works then we can not dispute it..

edit the /etc/pulse/default.pa file & add at the end:
load-module module-alsa-sink device=hw:1,8

be sure that there is **only one** module-alsa-sink entry.

Now this alsa device will appear in pulse audio as the 2nd HDMI device.
Use pavucontrol or gnome sound prefs..

---

### Post by Ulysses4ever on 2011-09-23
Sorry, seems that I messed 1,7 with 1,8. The noise is heard with 1,7.

> What caused the soundcard number to change from 2 -->1 ?
AFAIR only reboot. Note that HDMI cable is not connected to PC instantly, but during last 24 hours it was connected (again AFAIR). 

When I open System Preferences - Multimedia dilog in Kubuntu, it sometimes shows pop-up window that ther are some obsolete or removed audio devices and asks if I want to delete them from KDE settings. I usually answered "no", but not sure for this.

Unfortunately edition of /etc/pulse/default.pa (I added the line with 1,7 option and made sure tha there is no other module-alsa-sink entries) didn't make sound goes through HDMI. I tried to change various HDMI-* devices in System Preferences - Multimedia and after one of such change I saw pop-up window that this device is not available and sound would go through analog device (sound card) instead. Now there are number of HDMI devices each of which is inactive (in gray color) in System Preferences - Multimedia and I can't even choose them :cry:

---

### Post by BicyclerBoy on 2011-09-23
A reboot after a kernel update could cause audio stuff to change.
A kernel update can cause some module settings to get updated.

Did you try to build alsa from source ?
Did you download some drivers from outside package management (synaptic) ?
Did you run some update script ?

You should get rid of the old drivers for removed sound cards by answering yes. Audio drivers are in the kernel & alsa libs.

Can you try to use pavucontrol ?
I don't know the KDE way..

I should have stated before that for HDMI audio:
- you must be running the real nVidia X server driver. The GT240 has support from about version 260.xx
- X screen must be active
- a dummy X screen is required for audio only output.

---

### Post by Ulysses4ever on 2011-09-23
BicyclerBoy, my understanding of linux setup is not quite deep, so many things sound strange for me. I can perform any steps (from console or not) to find out what went wrong, but need exact directions.

> Did you try to build alsa from source ?
No. Should I? Any suggestions where to start doing this?
> Did you download some drivers from outside package management (synaptic) ?
No.
>Did you run some update script ?
May be the regular system update took place, but I'm not sure. Beside this - no.

> Can you try to use pavucontrol ?
Yes, sure, I've already installed it, but don't know wat exactly should I done with it.

> I should have stated before that for HDMI audio:
> - you must be running the real nVidia X server driver. The GT240 has support from about version 260.xx
I have an installed package "nvidia-current", which probably carries latest version of nvidia driver from repo and I suppose that it's older then 260.xx. Is there an easy way to update the driver from the third party (i.e. not from a repo)?

> - X screen must be active
It seems active, but I'm not sure, how to get convinced in it.

> - a dummy X screen is required for audio only output.
Mmm, don't know, what is “dummy X screen” — any suggestions, how to find out the info?

---

### Post by BicyclerBoy on 2011-09-23
I was asking those questions to help explain the strange audio/alsa responses. (card 2 card 1 etc).

You have the right video driver. No need to use dummy screen as you have a real HDMI screen with video & audio.

pavucontrol is better version of gnome sound preferences. It allows you to select the audio output device etc.

It is possible your previous pulse audio setup is interfering with the new setup.

From the pulse audio troubleshooting guide:
```

mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf

```
This gets rid of old config files (backups them up first).

---

