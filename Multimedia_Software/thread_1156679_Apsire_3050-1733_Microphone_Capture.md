---
title: "Apsire 3050-1733 Microphone Capture"
date: 2009-05-12
forum: Multimedia Software
---

### Post by bobpaul on 2009-05-12
In alsa-base.conf, I've tried "options snd-hda-intel mode=acer", "options snd-hda-intel mode=acer-aspire", and plain "options snd-hda-intel". With the prior 2 my volume control settings are better named, but with the latter I get louder audio. (The prior two remove the "Surround" volume slider, which can be used to give an extra boost to the built-in speakers).

On all of them I can *hear* audio through both the internal Mic (Front Mic) and a headset plugged into the mic jack on the laptop (Mic or Microphone). I can do this by entering the Playback Tab and setting the Mic Boost control up full, setting the Mic vol up relatively high, and unmutting both Mic Boost and the Mic itself.

In the recording tab I have 2 sliders, Capture and Capture 1. I have both set on full. Each slider has a "Mute/Unmute" and "Toggle Audio recording" button. I have both unmuted but I can't turn capture on. Whenever I open volume control, capture is off. I can click the icons to turn capture on for Capture and Capture 1, but when I close and re-open Volume Control they're always off again. :(

In the Options tab I have 2 options both titled "Input Source". I have both set to "Mic".

If I go to System->Preferences->Sound, the Sound Capture test generally fails with "Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'". Sometimes a "Testing ... Click ok to finish" dialog appears, but nothing comes out of the speakers as I talk into or tap on the microphones.

```
lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
```

```
sudo lshw -class multimedia
  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
```

This is really irritating, as the microphones obviously work since I can unmute them on the playback tab and hear them. What could be holding back audio capture? I seem to remember this working pre-pulse audio (7.10?), but I had no need for capture back then. I have not tested line input, but I'd assume that also fails.

(For those searching, it's my understanding that the 3050 w/Sempron and the 5050 w/ Turion x2 are the same computer except for the processor.)

---

### Post by sindrejh on 2009-05-13
I've had the exactly same problem, with the same internal sound chip, for some years now.

Believes that the problem is really common.

Still got no solution, thou...

---

