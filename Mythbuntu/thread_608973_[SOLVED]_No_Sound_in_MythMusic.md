---
title: "[SOLVED] No Sound in MythMusic"
date: 2007-11-10
forum: Mythbuntu
---

### Post by am_pcguy on 2007-11-10
I have MythTV set up with Mythbuntu 7.10.  I can play mp3's fine from Mplayer on the desktop.  When I open the mythfrontend and go to listen to music it appears to start playing but there is no sound.  

I have changed the output device in the setting to "default", "ALSA:default", "/dev/dsp" and "/dev/dsp1"  None of the changes made any difference

I tried running the frontend with verbose output.  There are no errors.

Sound on TV, DIVX, XVID, MKV, h.264, basicly any video file or recording is fine.  I can even get DTS or Dolby DIgital output via the optical connection.  Again with the optical connection Mplayer works fine playing MP3's outside of MythTV.

Any suggestions?  I'm lost at this point.

Thanks

---

### Post by napsilan on 2007-11-10
Have you tried turning the volume up in mythmusic?  Honest question, I'm not trying to be a smartass.

---

### Post by JBAlaska on 2007-11-10
You should check to see if both IEC958 and IEC958 playback are not muted. Also if IEC958 has a mixer, set it to zero. Some versions of alsa will not play audio though spdif if it is not.

If you can not get sound through spdif, set the sound device to ALSA:spdif, set the mixer to default, disable the internal volume controls and turn off both ac3 and dts passthru options. 

That should get default sound working thru the spdif link. Once that is working, turn the passthru's back on and verify you can play both audio formats. Also you may need to try a different asound.conf.

---

### Post by am_pcguy on 2007-11-10
Thanks guys,  There was no volume control under MythMusic nither [ ] or F10 F11 would work.  I checked the mixer and it IEC958 was muted... I've reinstalled recently to fix some problems I'm suprised I got sound at all... 

Anyway after unmuting IEC958 with alsamixer it worked just fine.

---

### Post by Offoffoff on 2008-08-12
In my case I just have to write ALSA:default. And everything comes right. Mythbuntu is REALLY great! I remember old HTPC-linux-programmes when I have to do all by my hands - now all is automated.

---

