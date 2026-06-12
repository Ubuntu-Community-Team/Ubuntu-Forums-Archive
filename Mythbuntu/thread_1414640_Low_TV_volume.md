---
title: "Low TV volume"
date: 2010-02-23
forum: Mythbuntu
---

### Post by bcgrown on 2010-02-23
My audio volume for LiveTV and recorded TV is very low.

MythMusic's volume is at least twice as much and seems to go up about as high as the sound card should.

I've cranked the speaker volume, MythTV volume, Alsa Mixer volume, and the "Recording profiles" volume all to 100%,  and disabled the XFCE mixer.

Hardware is Intel G41 / ICH7 chipset using the analog output straight to amplified speakers.

The low volume is not tuner specific as it affects my Hauppauge PVR-USB2 as well as FireWire recordings from a Motorola DCT6200.

The same recordings have full volume in VLC when VLC's volume is set to 100% and all other settings are the same.

I've found lots of similar problems on the forums but nothing exactly the same,  and no solutions either.

Anyone have any ideas?

---

### Post by azmyth on 2010-02-24
I use ladspa to normalize the TV volumes not perfect but it keeps from blasting everyone out of the house when you go from TV to Music. You don't want to run mythmusic through ladspa as it'll sound crummy.

[http://mysettopbox.tv/phpBB2/viewtopic.php?t=18346](http://mysettopbox.tv/phpBB2/viewtopic.php?t=18346)

---

### Post by bcgrown on 2010-02-25
> **azmyth said:**
> I use ladspa to normalize the TV volumes not perfect but it keeps from blasting everyone out of the house when you go from TV to Music. You don't want to run mythmusic through ladspa as it'll sound crummy.

[http://mysettopbox.tv/phpBB2/viewtopic.php?t=18346](http://mysettopbox.tv/phpBB2/viewtopic.php?t=18346)

Hmm,  that could work using the amplifier plugin.  However it seems like more of a hack than a solution.

I really would like to find out what the cause of the low volume is in the first place.

---

### Post by azmyth on 2010-02-25
I use OTA for HD and the broadcast signal that comes across has low volume thus the volume mismatch between my analog tuner, HD tuner, and mythmusic. There's been talk of myth allowing individual volume control for each tuner in the setup but it hasn't happen. The solution I provided is a hack but there's no other way around it.

---

### Post by the_pod on 2010-02-25
I have similar problems.  I think it's silly that I need to have the volume at 80% - 90% just to have basic sound.  If I tried that with the CD player plugged in through the same system I'd blow my speakers.

One minor tweak I did that made things more tolerable was in relation to the sound setup for the system. Don't recall where in the setup menus it was, but a change from "Dolby 5.1" to "Stereo" made things somewhat better.

Still, a permanent solution would be ideal. I've heard Mythdora doesn't have this issue but I haven't had the stomach to redo my system just to find out.

---

