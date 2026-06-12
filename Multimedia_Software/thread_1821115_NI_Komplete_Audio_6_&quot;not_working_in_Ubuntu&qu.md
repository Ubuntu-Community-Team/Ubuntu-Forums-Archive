---
title: "NI Komplete Audio 6 &quot;not working in Ubuntu&quot;"
date: 2011-08-08
forum: Multimedia Software
---

### Post by Peevy on 2011-08-08
I see a lot of people seem to have Native Instruments older usb interface "Audio Kontrol 1" working with Ubuntu but does anyone have their latest one "Komplete Audio 6" working? I've tried a few different things but it just sits in standby & its not available as a device in volume preferences nor does it appear show in the list with the command aplay -l.

The device itself is definitely working because I use it for music production on Windows 7 (the only reason I still use Windows)

I'd really appreciate any help to get this usb audio interface working.

---

### Post by Peevy on 2011-08-09
Bump

---

### Post by Peevy on 2011-08-12
OK...something really strange happened. I bootup my laptop yesterday & the KA6 just worked, even had it working with jack. Today, no go at all. I'm a bit stumped about this.

Could someone even give me some instruction on how to get a usb soundcard working in general with Ubuntu?

---

### Post by Peevy on 2011-08-14
Come on fellow Ubuntu users. Some help here would be very much appreciated!!

---

### Post by Peevy on 2011-08-20
106 views & not one helpful post. I'd really really appreciate some help here, even some general info on getting a usb soundcard working on linux.

I really do have faith in the open source community or I wouldn't still be here asking for assistance. I very much love Ubuntu/linux but at times like this it can be verrrry frustrating!!

---

### Post by orange2k on 2011-08-21
Why not try to contact Native Instruments support, or is NI Komplete not supported under Linux?

I would really like to help you, but I don't own NI Komplete so I don't know how it behaves under Linux...:(

---

### Post by Peevy on 2011-09-04
> **orange2k said:**
> Why not try to contact Native Instruments support, or is NI Komplete not supported under Linux?

I would really like to help you, but I don't own NI Komplete so I don't know how it behaves under Linux...:(

Thanks for chiming in anyway. My KA6 just sits in standby when I start up ubuntu. It shows up as usb device with "lsusb"

There's some info on how to get NI usb devices working with linux & I've tried a few of the suggestions but no dice. The strange thing is that it worked once for me but then after reboot, nothing. Its a bit of a head scratcher.

---

### Post by Peevy on 2011-09-04
OK I've made some progress. I updated the kernel to 3.1 & it worked, but (there's always a but) that kernel isn't very stable & my laptop was suffering from a lot of freezing so I'm gonna try kernel 3.0.1 as its supposed to be a stable build.

---

### Post by Peevy on 2011-09-04
I've tried kernel 3.0.1 & no go. I've just double checked & the KA6 definitely works with kernel 3.1. I just checked & its a daily build kernel, I'd probably be better of using an RC version. I'll do it tomorrow, I'm enjoying listening to some glitchHop through my KA6 right now...Don't wanna spoil it :)

---

### Post by jeremija on 2011-11-04
Is there any difference with the new Ubuntu 11.10? I plan to buy this card an would like to know if it is really supported as it says here:

[LIST]
[*][http://www.native-instruments.com/en/support/compatibility/linux/](http://www.native-instruments.com/en/support/compatibility/linux/)
[*][http://alsa-project.org/main/index.php/Matrix:Vendor-Native_Instruments](http://alsa-project.org/main/index.php/Matrix:Vendor-Native_Instruments)
[*][http://apps.linuxaudio.org/wiki/current_audio_gear#native_instruments_-_komplete_audio_6_usb-2](http://apps.linuxaudio.org/wiki/current_audio_gear#native_instruments_-_komplete_audio_6_usb-2)
[/LIST]

---

### Post by jeremija on 2011-11-11
@Peevy: have you had any luck lately? I bought this card and I can only use the four output channels for playback in Ubuntu 11.10 - it's the same with both 3.0 and 3.1 kernel. ALSA doesn't recognize any of the input channels.

[B]Edit: it works since kernel 3.0, but I had to manually write the pulseaudio profile set file.
aplay -l and arecord -l list all channels![/B]

---

### Post by shamaniac on 2012-08-05
@jeremija
Could you please share your custom pulseaudio profile. I spent couple of hours and couldn't make pulseaudio to accept anything other then 4.1 setup.
Thanks in advance.

---

### Post by jeremija on 2012-08-05
Sure, here it is:

```
[General]
auto-profiles = no
 
[Mapping main-stereo-out]
description = Main stereo output
device-strings = hw:%f,0
channel-map = front-left,front-right,aux0,aux1,aux2,aux3
direction = output

[Profile output:stereo]
description = Main Stereo Output
output-mappings = main-stereo-out
input-mappings =
priority = 80
skip-probe = false
```

Save it as ```
/usr/share/pulseaudio/alsa-mixer/profile-sets/native-instruments-komplete-audio6.conf
```

and create a new file for udev rules, for example ```
/etc/udev/rules.d/89-pulse-komplete-audio.rules
```

and paste the following (but replace the xxxx and yyyy with correct hardware ids, you can list them with lsusb):
```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", ENV{PULSE_PROFILE_SET}="native-instruments-komplete-audio6.conf"
```

From what I see the idVendor for Native Instruments is 17cc. You can see the existing configurations for other NI cards in /lib/udev/rules/90-pulseaudio.rules file. 

After you have created these two files, disconnect your card, run ```
sudo service udev restart
``` and reconnect it.

I can't check nowbecause I'm on vacation and don't have the KA6 with me, but IIRC some NI card like Traktor Audio 6 has the same idProduct, so if this doesn't work at first, try commenting out the card with the same idProduct in that file.

Note that this is only for playback. I didn't have the need nor nerves to map the input channels (I have a webcam with microphone input). Usually recording software uses jackd, so you can easily map the channels using qjackctl.

---

### Post by mortenc on 2013-01-11
It's been a while since the last answer to this thread. Any news about using the inputs of the NI Audio Komplete 6? I want to use this Audio Interface on Ubuntu 12.04 (Desktop and Server) for capturing purposes, but I didn't find out how to get the inputs working.

I would be glad to get a hint how to do alsa input mapping if this is the right place to get things work. It's the same situation like in the posts before: interface is detected correct and drivers are loaded, standard output is working but none of the inputs appear nowhere. Is there a way to map hardware adresses of the interface to alsa inputs?

Thanks in advance,
mortenc

---

### Post by jeremija on 2013-01-11
Jack detects the inputs fine. Try installing jackd2 along with qjackctl and you should see your inputs and outputs visually in qjackctl. Also, IIRC, I had to add my user to the 'audio' group to make jack work correctly.

---

### Post by ubu_dynamite on 2013-01-11
Jack detects the inputs and outputs just fine here to.
But pulseaudio needs better mapping and profiles it only shows 4.1, 5.0 and 5.1 sound profiles no stereo or inputs.

---

### Post by monstara on 2013-01-12
I just bought a KA6 a couple of days ago, but I haven't been able to get it to work.
My syslog fills with these:
```

Jan 12 13:01:09 recencyeffect-studio kernel: [ 1438.831683] xhci_hcd 0000:0b:00.0: ERROR: unexpected command completion code 0x11.
Jan 12 13:01:09 recencyeffect-studio kernel: [ 1438.831687] usb 3-2: Not enough bandwidth for altsetting 1
Jan 12 13:01:09 recencyeffect-studio kernel: [ 1438.831689] ALSA pcm.c:250 3:1:1: usb_set_interface failed

```If I try to start Jack with the card, it cannot initialize any inputs or outputs.
I built alsa from source, still no go. It seems that the correct driver is used snd-usb-audio.

Now I will either write on the Native Instruments forum, or to the linux-audio-user list.

---

### Post by jeremija on 2013-01-12
Which kernel are you using? IIRC, the system started to recognize the sound card correctly after I upgraded to kernel 3.0 - couldn't get it to work with 2.6.x.

---

### Post by monstara on 2013-01-12
At this moment I am running Ubuntu Studio 12.10, and I also tried on regular Ubuntu 12.10
kernel of this one is **3.5.0-21-lowlatency**

I could provide more information, but I suspect it might be a USB3 issue. I tried another laptop, also with 12.10, but got similar results.

I forgot to mention earlier, that alsamixer shows 4 things: a clock source, monitor control front, monitor control rear, and monitor control 1
The first is set to internal clock, the monitor controls are muted, showing [off] in the top left corner, and they cannot be changed.

---

### Post by jeremija on 2013-01-12
Oh, you don't have any USB2 ports on your PC? I think I have read somewhere on the NI forums that KA6 doesn't work correctly on a USB3 port, but that was a long time ago...

Edit: here is the [forum post]("http://www.native-instruments.com/forum/showpost.php?p=1036744&postcount=13")!

> Ok..here it is.official answer from NI support:

The problem is that out interfaces use a technology called 'isochronous streaming'
(this makes the drivers much faster).

The standard USB specifications cover this feature, and every USB2 controller
supports it.
But most USB3 controllers do not (yet) support 'isochronous streaming' (for
example the commonly used 'Renesas' chips do not support this).

Therefore you really need to use a USB 2 controller or a Esata/usb combo port.

There is nothing else you could do to bypass this problem.
As this is caused by the drivers of the USB3 controllers, it can only be fixed by
the manufacturers of these controllers.

But for all users that had a problematic USB controller, we found out that all of
them also had a 'SATA/USB' combo port, and on this port the interfaces worked fine. 

---

### Post by monstara on 2013-01-12
This is what I get from lspci
```
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```
I think the first two are USB 2.0. Tried plugging in each port, but...

---

### Post by jeremija on 2013-01-12
Looks like we have a similar chipset - this is my output:
```

$ lspci | grep USB
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

Does the USB LED on KA6 blink or is it permanently lit when you connect it?

---

### Post by monstara on 2013-01-12
wait, it just worked! In jack instead of hw:0 I selected hw:0,0 and it started.
Thank you very much for the help!

---

### Post by jeremija on 2013-01-12
You're welcome, I'm glad you got it working!

---

### Post by ubu_dynamite on 2013-01-13
Its not perfect but the following profile will get stereo output and all inputs working in pulseaudio.

Any better mapping ideas would be welcome.

Create a udev rules file.
```
sudo nano /lib/udev/rules.d/91-komplete-audio6.rules
```
Paste the following into the file and save.
```
SUBSYSTEM!="sound", GOTO="pulseaudio_end"
ACTION!="change", GOTO="pulseaudio_end"
KERNEL!="card*", GOTO="pulseaudio_end"

SUBSYSTEMS=="usb", ATTRS{idVendor}=="17cc", ATTRS{idProduct}=="1001", ENV{PULSE_PROFILE_SET}="native-instruments-komplete-audio6.conf"

LABEL="pulseaudio_end"
```
Create a profile.
```
sudo nano /usr/share/pulseaudio/alsa-mixer/profile-sets/native-instruments-komplete-audio6.conf
```
Paste the following into the file and save.
```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Native Instruments Komplete Audio 6
;
; Input1     mic/hi-z/line combo
; Input2     mic/hi-z/line combo
; Input3     line
; Input4     line
; Input5/6   stereo spdif
; Input      midi
;
; Output1    line main
; Output2    line main
; Output3    line
; Output4    line
; Output5/6  stereo spdif
; Output     midi
;
;//////////////////////////////////////////////////////////////////
; http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/Profiles
;
; sudo nano /lib/udev/rules.d/91-komplete-audio6.rules
;------------------------------------------------------------------
; SUBSYSTEM!="sound", GOTO="pulseaudio_end"
; ACTION!="change", GOTO="pulseaudio_end"
; KERNEL!="card*", GOTO="pulseaudio_end"
;
; SUBSYSTEMS=="usb", ATTRS{idVendor}=="17cc", ATTRS{idProduct}=="1001", ENV{PULSE_PROFILE_SET}="native-instruments-komplete-audio6.conf"
;
; LABEL="pulseaudio_end"
;------------------------------------------------------------------
; sudo nano /usr/share/pulseaudio/alsa-mixer/profile-sets/native-instruments-komplete-audio6.conf
; paste the content of this file in it
;
; pulseaudio -k
;
;//////////////////////////////////////////////////////////////////

[General]
auto-profiles = yes

[Mapping analog-main-stereo-out]
description = Analog Stereo
device-strings = hw:%f
channel-map = front-left,front-right,aux0,aux1,aux2,aux3
direction = output

[Mapping 6-channel-input]
description = Channel[1-6]
device-strings = hw:%f
channel-map = aux0,aux1,aux2,aux3,aux4,aux5
direction = input

```

After you have created these two files, disconnect your card, run
```
sudo service udev restart
```
and reconnect it.

You should now have 3 profile options in pulse
Channel[1-6] input
Analog stereo output + Channel[1-6] input
Analog stereo output

If you make any more changes to native-instruments-komplete-audio6.conf just restart pulseaudio
```
pulseaudio -k
```
and the changes should become active.

---

### Post by oscalypso on 2013-03-15
Hi everybody

Thanks to ubu_dynamite
this method worked for me.
Here's the code I added for people ,like me, whos use 2 pairs of speakers (you can choose 1/3 stereo out, 3/4 stereo out or 1/2/3/4 out in pulse audio settings)


# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Native Instruments Komplete Audio 6
;
; Input1 mic/hi-z/line combo
; Input2 mic/hi-z/line combo
; Input3 line
; Input4 line
; Input5/6 stereo spdif
; Input midi
;
; Output1 line main
; Output2 line main
; Output3 line
; Output4 line
; Output5/6 stereo spdif
; Output midi
;
;//////////////////////////////////////////////////////////////////
; [http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/Profiles](http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/Profiles)
;
; sudo nano /lib/udev/rules.d/91-komplete-audio6.rules
;------------------------------------------------------------------
; SUBSYSTEM!="sound", GOTO="pulseaudio_end"
; ACTION!="change", GOTO="pulseaudio_end"
; KERNEL!="card*", GOTO="pulseaudio_end"
;
; SUBSYSTEMS=="usb", ATTRS{idVendor}=="17cc", ATTRS{idProduct}=="1001", ENV{PULSE_PROFILE_SET}="native-instruments-komplete-audio6.conf"
;
; LABEL="pulseaudio_end"
;------------------------------------------------------------------
; sudo nano /usr/share/pulseaudio/alsa-mixer/profile-sets/native-instruments-komplete-audio6.conf
; paste the content of this file in it
;
; pulseaudio -k
;
;//////////////////////////////////////////////////////////////////

[General]
auto-profiles = yes

[Mapping analog-main-stereo-out]
description = Analog Stereo 1/2
device-strings = hw:%f
channel-map = front-left,front-right,aux2,aux3,aux4,aux5
direction = output

[Mapping analog-alt-stereo-out]
description = Analog Stereo 3/4
device-strings = hw:%f
channel-map = aux0,aux1,rear-left,rear-right,aux4,aux5
direction = output

[Mapping analog-quadro-out]
description = Analog Quadro 1/2/3/4
device-strings = hw:%f
channel-map = front-left,front-right,rear-left,rear-right,aux4,aux5
direction = output

[Mapping 6-channel-input]
description = Channel[1-6]
device-strings = hw:%f
channel-map = aux0,aux1,aux2,aux3,aux4,aux5
direction = input

---

### Post by Segasu on 2013-04-06
This is giving me a headache; it worked perfectly under ubuntu, but when I use the same lines for Arch Linux, I don't get any outputs at all.

Any ideas why this might be? My skills with Linux are quite limited, so it's more or less copy/paste behaviors for me at the moment. ^^

---

### Post by ubu_dynamite on 2013-04-07
It should work when you have pulseaudio installed adleast it does for me.
You say you dont get any outputs does that mean the card is recogniced and is visible in sound settings but you cant get any sound out?

---

### Post by Segasu on 2013-04-07
That is correct. I do, however, get the inputs, even my Blue Snowball microphone (god bless USB!), but the outputs are nowehere to be found.

---

### Post by ubu_dynamite on 2013-04-07
> **Segasu said:**
> That is correct. I do, however, get the inputs, even my Blue Snowball microphone (god bless USB!), but the outputs are nowehere to be found.

Did you set a profile in sound setting that has outputs + inputs?

---

### Post by Segasu on 2013-04-07
There are no profile at all, it's completely empty. I'll just throw out Gnome and reinstall it - it might help. ^^

...now, suddenly it's there...in stereo...as you config told it should be like. No restart, no reboot, no logout, no nothing...only the screensaver during night that kicked in. After that, the sound worked.

---

