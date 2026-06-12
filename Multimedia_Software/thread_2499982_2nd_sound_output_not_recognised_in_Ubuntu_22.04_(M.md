---
title: "2nd sound output not recognised in Ubuntu 22.04 (MSI A520M-A PRO board)"
date: 2024-08-17
forum: Multimedia Software
---

### Post by Robbyx on 2024-08-17
I have an a520M-a-pro MSI mother board. It has a built in sound card. I wish to plug in both a head set and a set of desktop speakers. I want to be able to choose in software which output source is used.

I put the headset into the green audio jack for line-out
Desktop speakers are plugged into the orange audio jack.

Only one item is being recognised when two are plugged in. 

In the settings sounds, output device only "line out -family 17h... is showing as an option. The second device is not showing as an output device. 

In ALSA mixer no channels appear muted.

I have tried reinstalling ALSA and pulseAudio. Made no dif.

I have added " load-module  module-alsa-sink" to pulseaudio as it was not present. Made no dif.

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 0: ALC897 Analog [ALC897 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

What else can i do?

---

### Post by Robbyx on 2024-08-22
Would it be possible to have some help with  a 2nd sound input not being recognised?

---

### Post by Yellow Pasque on 2024-08-23
You need to retask the orange jack with hadjackretask. Then, [https://wiki.archlinux.org/title/PulseAudio/Examples#Having_both_speakers_and_headphones_plugged_in_and_switching_in_software_on-the-fly](https://wiki.archlinux.org/title/PulseAudio/Examples#Having_both_speakers_and_headphones_plugged_in_and_switching_in_software_on-the-fly)

---

### Post by Robbyx on 2024-08-27
Thank you for your response. I followed the link to find this warning:

> 
.This article or section is out of date.

Reason: /usr/share/pulseaudio/alsa-mixer/paths has been replaced by /usr/share/alsa-card-profile/mixer/paths (Discuss in Talk:PulseAudio/Examples#Having both speakers and headphones plugged in and switching in software on-the-fly)

going to the new location 

[HTML]https://wiki.archlinux.org/title/Talk:PulseAudio/Examples#Having_both_speakers_and_headphones_plugged_in_and_switching_in_software_on-the-fly[/HTML]

You will see the revision says to ensure that the element front complies with the extract shown here::

[HTML][Element Front]
switch = off
volume = off

in the [Element Front] section. [/HTML]

My MB has only rear socket connectors for the audio . I do not know which element to alter as there is no exact match to the insruction, especially as all the elements have both the switch and volume switched off . Can you suggest some appropriate changes I could make?

This is my analog-output-headphone.conf

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
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

; Path for mixers that have a 'Headphone' control
;
; See analog-output.conf.common for an explanation on the directives

[General]
priority = 99
description-key = analog-output-headphones

[Properties]
device.icon_name = audio-headphones

[Jack Dock Headphone]
required-any = any

[Jack Dock Headphone Phantom]
required-any = any
state.plugged = unknown
state.unplugged = unknown

[Jack Front Headphone]
required-any = any

; HP EliteDesk 800 DM Headset
[Jack Front Headphone Front]
required-any = any

[Jack Front Headphone Phantom]
required-any = any
state.plugged = unknown
state.unplugged = unknown

[Jack Headphone]
required-any = any

[Jack Headphone Phantom]
required-any = any
state.plugged = unknown
state.unplugged = unknown

# This jack can be either a headphone *or* a mic. Used on some ASUS netbooks.
[Jack Headphone Mic]
required-any = any

[Jack Headphone - Output]
required-any = any

[Element Hardware Master]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Master]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Master Mono]
switch = off
volume = off

[Element Speaker+LO]
switch = off
volume = off

[Element Headphone+LO]
required-any = any
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Headphone]
required-any = any
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

; This path is intended to control the first headphones, not
; the second headphones. But it should not hurt if we leave the second
; headphone jack enabled nonetheless.
[Element Headphone,1]
switch = mute
volume = zero

[Element Headset]
required-any = any
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Line HP Swap]
switch = on
required-any = any

; This profile path is intended to control the first headphones, not
; the second headphones. But it should not hurt if we leave the second
; headphone jack enabled nonetheless.
[Element Headphone2]
switch = mute
volume = zero

[Element Speaker]
switch = off
volume = off

[Element Desktop Speaker]
switch = off
volume = off

; On some machines, the Front Volume Control is shared by Headphone and Lineout,
; or Headphone and Speaker, but they have independent Volume Switch. Here only
; use switch to mute Lineout or Speaker.
[Element Front]
switch = off
volume = zero

[Element Rear]
switch = off
volume = off

[Element Surround]
switch = off
volume = off

[Element Side]
switch = off
volume = off

[Element Center]
switch = off
volume = off

[Element LFE]
switch = off
volume = off

[Element Bass Speaker]
switch = off
volume = off

[Element Speaker Front]
switch = off
volume = off

[Element Speaker Surround]
switch = off
volume = off

[Element Speaker Side]
switch = off
volume = off

[Element Speaker CLFE]
switch = off
volume = off

[Element Speaker Center/LFE]
switch = off
volume = off

.include analog-output.conf.common
```

---

### Post by Robbyx on 2024-09-01
I hope that I get a reply soon. 

R

---

### Post by 1fallen on 2024-09-05
I use a script for that, unless your talking about simultaneously to both.
my script
```

if [[ $(pactl list | grep "Active Port: analog-output") == *"headphones"* ]]; then
    pactl set-sink-port 0 analog-output-speaker
else
    pactl set-sink-port 0 analog-output-headphones
fi
```
To find the correct findings use:
```
pactl list 

```


To switch the default sink, you can use "pactl set-default-sink <sink_name>"

---

### Post by Robbyx on 2024-09-10
Thank you very much for your helpful reply:

---

### Post by Robbyx on 2024-09-16
How can I set up two devices to receive the sound? I use a desktop Voip app in a browser. If I do not use simultaneous output I think  I will not realise calls are coming in to  computer.

---

### Post by 1fallen on 2024-09-16
First I have no idea how this will work with your  Voip app I've never used one.

First direct your sound to both:
```
pactl load-module module-combine-sink
```

You should control your audio through PAV

And I seem to remember It always defaulted to any incoming calls on my phone.

I'm curious how this will work with your Voip

---

### Post by Robbyx on 2024-09-17
When I entered your code it responded with 29.

My voip service rings on my phones, and also on my computer provided I have the browser open at my portal  page at the voip service's web site. The sound in and out goes to my headset through the sound card, but because I need it to also  go to the loud speakers on the desk I also need it to go through a the sound card. 

The headset has one jack for both sound and mic. 

The speakers also only have one jack.

Therefore two sockets are needed.

---

### Post by 1fallen on 2024-09-17
Did you actually look in your volume control? That is where you should be able to handle that.

Mine:
```
[FONT=monospace][COLOR=#000000]pactl load-module module-combine-sink[/COLOR]
536870916

[/FONT]
```
Now like I asked you to do is look at PAV, see screenshot.

```
[FONT=monospace][COLOR=#000000]pactl list|grep combined  [/COLOR]
        Name: combined
        Description: combined
        Monitor Source: combined.monitor
                node.name = "combined"
                device.description = "combined"
        Name: combined.monitor
        Description: Monitor of combined
        Monitor of Sink: combined
                node.name = "combined"
                device.description = "combined"
                media.name = "combined output"
                device.description = "combined output"
                node.name = "output.combined_alsa_output.pci-0000_05_00.6.analog-stereo"
                module-stream-restore.id = "sink-input-by-media-name:combined output"
                media.name = "combined output"
                device.description = "combined output"
                node.name = "output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.ana
log-surround-41"
                module-stream-restore.id = "sink-input-by-media-name:combined output"

[/FONT]
```
OR
```
[FONT=monospace][COLOR=#000000]pactl set-sink-port 0 analog-output-speaker && pactl set-sink-port 0 analog-output-headphones[/COLOR]
[/FONT]
```[FONT=monospace]
and
[/FONT]```
pactl list|grep -e analog-output-speaker -e analog-output-headphones 
                analog-output-speaker: Speakers (type: Speaker, priority: 10000, availability group: Legacy 3, not available)
                analog-output-headphones: Headphones (type: Headphones, priority: 9900, availability group: Legacy 4, available)
        Active Port: analog-output-headphones
                analog-output-speaker: Speakers (type: Speaker, priority: 10000, availability group: Legacy 2, available)
        Active Port: analog-output-speaker
                analog-output-speaker: Speakers (type: Speaker, priority: 10000, availability group: Legacy 3, not available)
                analog-output-headphones: Headphones (type: Headphones, priority: 9900, availability group: Legacy 4, available)
        Active Port: analog-output-headphones
                analog-output-speaker: Speakers (type: Speaker, priority: 10000, availability group: Legacy 2, available)
        Active Port: analog-output-speaker
                analog-output-speaker: Speakers (type: Speaker, priority: 10000, latency offset: 0 usec, availability group: Legacy 2, available)
                analog-output-speaker: Speakers (type: Speaker, priority: 10000, latency offset: 0 usec, availability group: Legacy 3, not available)
                analog-output-headphones: Headphones (type: Headphones, priority: 9900, latency offset: 0 usec, availability group: Legacy 4, available)

```

---

