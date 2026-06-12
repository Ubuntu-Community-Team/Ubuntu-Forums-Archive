---
title: "nvidia 210 hdmi audio issues with TV"
date: 2012-02-24
forum: Mythbuntu
---

### Post by peskygnat on 2012-02-24
Ok, so I think I have done my home work.  I bought this card for price, because it is silent, and to add HDMI.   

I have not had any video issues, just audio.
I disabled the onboard audio.  So my only audio device is the hdmi.
I looked in [FONT="Courier New"]/proc/asound/card0[/FONT] to see eld#1.0 is the valid EDID.
So I added 
[FONT="Courier New"]options snd-hda-intel enable_msi=0 probe_mask=0x102[/FONT]
to /etc/modprobe.d/alsa-base.conf.  
This changed my default 4 muteable options in mixer to 1.  

Still no sound.

Then just through trial and error I was able to get sound testing: 
aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav

Why?

okay, so moving on.  Now I have audio, but not on boot.  There is still some sync issue with the tv/hdmi.  Sometimes if I do the above aplay command before starting mythfrontend I am good, sometimes not.  When it doesn't work, muting and unmuting the spdif in the mixer app will then allow it to work.  But running noise through the aplay command seems to work more often IF the tv is already on the HDMI input for the mythtv.  

I finally created a script and added it to the mythtv frontend so I can do the mute/umute/aplay again in one step.

But why the work around?  any thoughts?

---

### Post by nickrout on 2012-02-24
What version of mythtv are you using?

Have you scanned for audio devices in the frontend setup?

---

### Post by BicyclerBoy on 2012-02-24
The GT210 really only has price as a feature..

Your probemask (which is out-of-range) causes the real hdmi audio codecs to be ignored by alsa when it allocates the logical device names.

Your GT210 has 4 pin codecs #0-3, alsa labels them hw:0,3 - hw:0,[7,8,9]
Using probemask of 0x02 causes pin codec#1 to now be labelled hw:0,3.

So fix your probemask to be in range (0x02) or do not use it.
Remove the enable_msi option; this is needed for nVidia MCP67 77 78 etc  chipset & the alsa driver automatically enables it.

You will have a lot less trouble if you let MythTV scan the audio devices & then use an alsa device (pulse server will be stopped)

---

