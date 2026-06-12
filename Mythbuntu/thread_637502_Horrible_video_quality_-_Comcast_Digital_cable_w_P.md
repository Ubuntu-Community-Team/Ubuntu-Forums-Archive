---
title: "Horrible video quality - Comcast Digital cable w/ PVR-150"
date: 2007-12-11
forum: Mythbuntu
---

### Post by ttyp0 on 2007-12-11
I have the coax cable from my comcast digital cable box going directly into the PVR-150. I'm using GeForce4 5700LE for S-Video out to the TV. I can play videos that are on the network or on the Mythbuntu box and the quality is excellent. However, when attempting to watch cable. The picture quality is REALLY fuzzy (If I plug the coax directly to the TV, the picture quality is great.

My first thought is it that it may be possible the splitter or cable needs to be replaced. I'm not quite sure if the picture quality to the TV is clear? There's a couple of threads with similar issues, but none of them provided a working solution.

Any thoughts or ideas?

Thanks in advance!

---

### Post by superm1 on 2007-12-11
> **ttyp0 said:**
> I have the coax cable from my comcast digital cable box going directly into the PVR-150. I'm using GeForce4 5700LE for S-Video out to the TV. I can play videos that are on the network or on the Mythbuntu box and the quality is excellent. However, when attempting to watch cable. The picture quality is REALLY fuzzy. 

My first thought is it that it may be possible the splitter or cable needs to be replaced. There's a couple of threads with similar issues, but none of them provided a working solution.

Any thoughts or ideas?

Thanks in advance!
1) Make sure you have the card set to be recording us-cable not ota or anything like that in mythtv-setup.
2) Replace that cable
3) Add an amplifier

---

### Post by ttyp0 on 2007-12-11
[ edit ]

Since the COAX goes from the wall -> Comcast STB -> PVR-150. The coax should work without using firewire.

[/edit]

---

### Post by ttyp0 on 2007-12-11
*UPDATE (new issue)* I changed the cable, which resulted in crystal clear reception on all channels for about thirty to ninety seconds. It went right back to being fuzzy and hasn't changed since.

Any ideas?

---

### Post by tgalati4 on 2007-12-12
Modern cable systems have extra communication signals that go through the cable.  It's possible that it's tripping up your PVR causing the tuner/decoder to go wonky.  

Also test your cable for any stray DC voltage.  It could be a ground loop issue causing the tuner to shut down.  

The weak reception is an indication that the tuner is shutting down for some reason.  You can by a 10, 20 or 30 dB attenuator that screws into the cable line.  Or use a 4-way splitter and terminate the unused ports.  It's possible that the signal is too strong for the tuner causing a safety relay disconnect the tuner.  An attenuator will lower the signal level with safe range of the tuner.

---

### Post by khaije1 on 2008-09-02
I'm wondering what people would recommend in my case, I am using comcast digital cable w/ a pvr-150 as well. 

I am able to watch tv with variable quality using vlc, but can't using Mythtv. 

That is probably a setup/config issue which i'm willing to work through independentl. The thing that I think is weird is that when using vlc i only get two channels... but nothing else! 

I'll typically change channels using: 

ivtv-tune -c <channel number> 

to view and change channels, but the only ones that work are 5 and 6. All other are static/noise/no signal. There is a tivo on a seperate branch of the same line (there is a 3 way split, pc, tivo, cable modem) and it gets the full range at reliably good quality. 

This is an area i don't know much about so I appreciate any and all help.

Cheers!

---

