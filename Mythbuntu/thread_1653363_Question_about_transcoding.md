---
title: "Question about transcoding"
date: 2010-12-26
forum: Mythbuntu
---

### Post by GuiGuy on 2010-12-26
After a system hardware failure and rebuild I am having a [nightmare]("http://ubuntuforums.org/showthread.php?t=1647740") of a time trying to archive recordings. I cannot get any of the scripts (nuvexport, mythnuv2mkh) to perform at reasonable speed to such an extent that it would take several days to transcode 30 minutes of recording. The resulting file is usually much bigger than the original, irrespective of the "quality" setting. MythExport doesn't work at all. But then, it never has for me. 

Having spent two weeks now to try and solve the issue without luck it is time to consider my sanity and give up.

However, I noticed that if I do a "Transcode" using mythtranscode the result is an mkv file of good quality, acceptable size and, above all, transcoding happens fairly swiftly. Unfortunately the transcoded result stays in the recording directory and retains a cryptic name. 

My question is, is there a script or interface that facilitates the copying of the cryptically named file to something in more human readable form?  I know I can do this manually, but that's tedious.

---

### Post by BicyclerBoy on 2010-12-31
There are 3rd party scripts that do stuff like this linked to on the MythTV website.

Have not used any of them only used mytharchive native format.

What format are your recordings in ?

The some off the transcoding/cutlist stuff does not seem work with dvb-t mpeg2-ts sourced h264 material.
Cutlists are not honoured  for mpeg-4 h264 material.
I believe the transcoding part of MythTV is to be removed & the functionality replaced by other methods.

---

