---
title: "How to Enable 5.1 Audio on Ubuntu Studio 24.04"
date: 2024-08-30
forum: Multimedia Software
---

### Post by wmichaelb2 on 2024-08-30
Hi, I'm missing something very basic here. I'm running Ubuntu Studio 24.04, standard KDE desktop, and would like to run a 5.1 speaker setup so that I could have a two channel output with a  subwoofer.  It's a home built machine with an Asus Prime B450M-A II motherboard and a Ryzen 5 5600 GT processor. The motherboard manual only refers to sound settings from the Windows sound driver. I've picked through any number of audio settings, found lots of references to MIDI connections, installed Kmix, but I cannot find anything referencing a 5.1 setup. Is there a way to do this with the built in Radeon audio, or do I have to get a separate sound card? Thanks in advance.

---

### Post by bobunderwood99 on 2024-08-30
From your motherboard manual:
Realtek 7.1 Surround Sound High Definition Audio CODEC*

* A chassis with an HD audio module in the front panel is required to support 7.1
Surround Sound audio output.

See if you can select a surround sound profile from System Settings>Audio or the PulseAudio Volume Control (pavucontrol).

Do you have any sound st all?

Are there any UEFI/BIOS settings that pertain to sound?

---

### Post by wmichaelb2 on 2024-08-31
bobunderwood99: thanks for your prompt response!

1.) There are two connectors for audio included with this case. Only the one labeled "HD Audio" would fit the header on the motherboard, so that's what I used.

2.) I had carefully checked the UEFI before posting, but there is no reference there to audio. 

3.) I do have regular stereo sound from the system, and it's actually pretty  good. But the mother board has only three audio ports, Line In, Line  Out, and Microphone. I'm driving my speakers from Line Out through a  stereo receiver and speakers. From the users' manual for the  motherboard, the Microphone port can be set to Bass/Center, but the only  way that is mentioned to do that is via the Windows driver.

4.) On my system (Ubuntu Studio 24.04 with KDE), there is no audio setting in System Settings. Pavucontrol shows only two entries, HDMI (which I have muted, since my monitor has only video) and HD Audio Analog Stereo. The "Port" banner only gives me two choices, speakers and headphones. 

This all leads me to ask:

A.) Do I need a separate sound card to get access to the *.1 audio channel for a subwoofer? Or..

B. qpwgraph is attached. Nowhere do I see anything about 5.1 or 7.1, only left and right. 

Thanks in advance for any insight you can offer.

---

### Post by bobunderwood99 on 2024-08-31
I would think that if the Microphone port was set to Bass/Center you would have an "Analog Surround 5.1 Output" profile available in pavucontrol. 

I don't how it could be set with Linux (doesn't mean it can't be).

---

### Post by Yellow Pasque on 2024-08-31
> **bobunderwood99 said:**
> I would think that if the Microphone port was set to Bass/Center you would have an "Analog Surround 5.1 Output" profile available in pavucontrol. I don't how it could be set with Linux (doesn't mean it can't be).

With Realtek codecs, there is usually a 'Channel Mode' setting in alsamixer to change between 2.0, 4.0, and 5.1 modes
For 5.1, you want the setting to be '6ch'

---

### Post by wmichaelb2 on 2024-09-01
I finally figured it out; knew it was something very basic! "Alsamixer" isn't named "alsamixer" in this distro; it's named "Qasmixer".  "Qasconfig" and "QasHCtl" are configuration clients for "Qasmixer", and that last package has the configuration choices for 2, 4, and 6 channel mode. It's the functional equivalent of the Windows driver mentioned in the motherboard documentation, and gives the user 18 choices of inputs, outputs, and adjustments. I can now proceed.

Thanks very much to both you folks for your time and effort!

---

### Post by Yellow Pasque on 2024-09-01
'alsamixer' is run from the command line. It's probably available on your distro, even if it has fancier-looking GUI's like Qasmixer.
If the thread is solved, please mark it as such (thread tools menu above first post).

---

