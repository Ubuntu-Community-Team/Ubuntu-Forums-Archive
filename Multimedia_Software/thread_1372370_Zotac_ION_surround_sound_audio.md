---
title: "Zotac ION surround sound audio"
date: 2010-01-04
forum: Multimedia Software
---

### Post by wardy277 on 2010-01-04
Hi,

I have got a zotac ion setup as my htpc. I have got it all working fine, but i cant seem to get the surround sound working. I am trying to use the 3 analogue ports, but only the green one is producing sound. I was told this had a 5.1 surround sound output so i am confused to why it hasnt picked it up. 

Anyone got any ideas?

Are there any good audio tests like the realteck one, where u click on the speaker to hear that speaker?

Chris

---

### Post by santhony on 2010-03-25
I'm having the same issues here, actually using the SPDIF ports... My Kenwood receiver picks up only stereo ports..  I understand that this Azalia codec uses port reassignment and wondering if that is causing the issues.

One can see from the WINDOWS instructions how the audio configuration works.. all via software...

---

### Post by Sputnik82 on 2010-03-29
Well, I don't know which Zotac HTPC do you have but it sounds that you are trying to use the microphone analog input as output.
Surround in Zotac Zbox is provided by the HDMI connector.

---

### Post by Lin_Mast on 2010-08-18
I have a Zotac Ion 330 HTPC running Mythbuntu 0.23/Ubuntu 10.04 hybrid (AMD64).  I also rebuilt the most current Realtek ALSA driver from their website.

I get fine HDMI surround or 2 channel stereo through the analog port (green) (dependeing on ALSA), BUT like the others I can't get the other jacks to output the rear and center/sub channels.  The ION manual on p. 7 clearly states that 6-channel sound is possible and even lists the jack color output scheme.  The Ion manual HDA driver instructions for (Win 7 and Vista) also shows how to reprogram the driver jack sensing settings from Mic input jack to speaker output jack. Hmmm.  I can't find the settings/widget to make the ALSA volume control sense the jacks.

Here's what I get from probing settings:
Codec: RealTek ALC662 rev 1
Codec: Nvidia    MCP79/7A HDMI

From lspci: MCP79 (rev b1)

aplay -L
shows all of the modes from 2.0 though 5.1 and HDMI

I am NOT seeing the sliders for "Rear" "Center" and "LFE" on the volume mixer either (and they aren't available to add).  I think the system knows it has 5.1, but the driver isn't setting up the jacks correctly.

Has anyone got the Zotac Ion to give analog outputs for 5.1 sound????   I'd appreciate any troubleshooting leads.

---

### Post by lidex on 2010-08-19
The OP of this thread managed to get working surround on an ion2:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by tjones00 on 2010-08-19
Please post the output from aplay -l and aplay -L as well as 

/etc/asound.conf  
/home/user/.asoundrc
/usr/share/alsa/alsa.conf <--it's probably best to attach this one it's kinda big

that you may have.

[http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture](http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture) 

^^great reference btw I love those Arch guys

It might be as simple as telling the system what pcm alias you want it to use.

Or it might be as complex as needing to create a custom mixer and alias for your device.

---

