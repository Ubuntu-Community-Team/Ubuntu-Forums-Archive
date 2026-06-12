---
title: "Video Files Pixelated and Blurry : W rork fine in Quicktime in Windows"
date: 2011-01-15
forum: Multimedia Software
---

### Post by excetara2 on 2011-01-15
I have videos that I recorded ages ago on my camera. They don't play right in Ubuntu. I have ones with a newer camera that were converted to .mp4 from Matroska which are fine.

These were natively in the .mp4 format from the camera. I'm not sure what codec they use but play fine in Windows. Is there an alternative quicktime codec or can I check which it is using??

Cheers

---

### Post by BicyclerBoy on 2011-01-16
The file extensions can be misleading..

Use 
ffmpeg -i recording.ext

or
mediainfo

to discover the container codecs streams data rates etc...

Then someone will find a soln...

---

### Post by excetara2 on 2011-01-16
Updated to the bleeding edge version of vlc from Lucid-bleed.

Then also installed mplayer. Now works fine on all media players so not sure what the solution was but assuming one of these updated the codec information that may have been corrupted or wrong on my system. I can post the mediainfo info later if someone interested. Shouldn't have posted that with this but actually half the files had to different codecs which was weird.

Thanks for the help anyway

---

### Post by BicyclerBoy on 2011-01-16
Found your own solution..

I have not found a media file that does not play with VLC if you have a recent version..
Same applies to MythTV internal player.

---

