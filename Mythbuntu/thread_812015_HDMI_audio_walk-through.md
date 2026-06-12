---
title: "HDMI audio walk-through?"
date: 2008-05-29
forum: Mythbuntu
---

### Post by dsbw on 2008-05-29
OK, so, I have two different systems both stuck in the same approximate place: [No HDMI Audio coming out]("http://ubuntuforums.org/showthread.php?t=810928").

In one case all the signs point to the audio coming out, i.e., it should be working. alsamixer shows up the right device and it's un-muted (I've tried combos of muting and muting that seemed to be likely but no joy). In another case, the iec958 shows up in aplay but not in the mixer or in device options.

So, I guess what I need is a start-to-finish on how to make the HDMI audio work. I've found a bunch of disparate how-tos, some of which seem more relevant than others, but nothing like, say, the Firewire guide. The ALSA project site is pretty good but not necessarily completely relevant. (And is it a given that you're using or need to use ALSA? Are there are other options that would work in this case?)

Any thoughts?

---

### Post by Dewey_Oxberger on 2008-05-29
>So, I guess what I need is a start-to-finish

You and me both.  Audio over HDMI was fixed on many MB's with the 1.0.16 rev but I still don't have mine working yet.

---

### Post by Trollslayer on 2008-05-29
Hardware: Abit I-F90 motherboard with Radeon X1250 graphics, ALC883 audio and ATI SB600 south bridge.
First - if you do [FONT="Courier New"]aplay -l[/FONT] you should see a HDMI device listed, this means it is supported.
Second - install [FONT="Courier New"]asoundconf-gtk[/FONT] using Synaptic - this allows you to set the default sound card to HDMI
After you have done this, run [FONT="Courier New"]alsamixer[/FONT] and it should show the one output which will be muted. Unmute it.
I checked it with VLC and sound worked.
**Warning:** Mplayer uses an internal older version of ALSA (0.9.1) which will not recognise newer devices.
Let me know how this goes and if you could list your harware that would be useful.

---

### Post by dsbw on 2008-05-29
> **Trollslayer said:**
> Hardware: Abit I-F90 motherboard with Radeon X1250 graphics, ALC883 audio and ATI SB600 south bridge.
First - if you do [FONT="Courier New"]aplay -l[/FONT] you should see a HDMI device listed, this means it is supported.

Right.

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


> **Trollslayer said:**
> Second - install [FONT="Courier New"]asoundconf-gtk[/FONT] using Synaptic - this allows you to set the default sound card to HDMI

Right. Except it doesn't come up. The only option is NVIDIA.


> **Trollslayer said:**
> After you have done this, run [FONT="Courier New"]alsamixer[/FONT] and it should show the one output which will be muted. Unmute it.

This is an MSI-K9N6M3, on-board graphics (NVidia 7050) with Realtek ALC888 audio. Hmmm. aplay says 883, not 888.

I have another board that's got an ATI1250 and a Realtek ALC889A and it does everything like it's supposed to except actually produce sound through the HDMI. :(

---

### Post by Trollslayer on 2008-05-29
ALSA seems to mix up reports between the 883 and 888 etc. With some of these there are bus variatons etc. so they can use the same driver (I had the same with a Realtek network interface) so don't worry about that.
I've looked on MSI's websit and can't find the K9N6M3, can you provide a product link? How long has it been out?
On the other board can you provide the aplay -l output?

---

### Post by dsbw on 2008-05-29
> **Trollslayer said:**
> ALSA seems to mix up reports between the 883 and 888 etc. With some of these there are bus variatons etc. so they can use the same driver (I had the same with a Realtek network interface) so don't worry about that.
I've looked on MSI's websit and can't find the K9N6M3, can you provide a product link? How long has it been out?
On the other board can you provide the aplay -l output?

It's the K9NGM3, and they've stopped making it. :(

As far as this board goes, should I mess around with the snd-hda-whatever settings? Looking through the logs, I see: 

"hda_codec: Unknown model for ALC883, trying to auto-probe from BIOS..."

Sorta frustrating since I know others have the exact some model working.

Edit: Yeah, I'll get the aplay -l from other machine, too, just a sec.

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This one's frustrating because it looks *right*. Everything comes up in alsamixer. Not sure which device should be the defaul, though. I thought card 2, but that only has the iec958 setting and nothing else (and doesn't seem to change anything).

---

### Post by dsbw on 2008-05-29
Yeah, the ATI-based machine behaves *exactly* as you describe, but no sound (through the HDMI)!

---

### Post by Trollslayer on 2008-05-30
OK, install the asoundconf-gtk on the X1250 machine and try to select the HDMI out put as defualt, unmute with alsamixer and see.
The first board, it looks like it's not the sound chip which has been found but the south bridge which does the HDMI routing which is the problem, afraid you'll have to try and go through the ALSA wiki. I think they describe it as jack configurations.

---

### Post by dsbw on 2008-05-30
> **Trollslayer said:**
> OK, install the asoundconf-gtk on the X1250 machine and try to select the HDMI out put as defualt, unmute with alsamixer and see.

Did that. No joy. Began to wonder if TV was broken but...nope.

I'll try ALSA again.

---

### Post by Lampi on 2008-06-24
you can try the brandnew Nvidia closed source driver - according to a statement nvidia made some while ago Version 177.13 is supposed to ship hdmi audio on nforce chipsets for the first time:

[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)

try it - you might be lucky

---

