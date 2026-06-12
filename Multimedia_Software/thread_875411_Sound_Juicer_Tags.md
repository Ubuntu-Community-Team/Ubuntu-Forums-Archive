---
title: "Sound Juicer Tags"
date: 2008-07-30
forum: Multimedia Software
---

### Post by DownTown22 on 2008-07-30
I ripped some CD's in Sound Juicer and noticed that my MP3 player wasn't displaying tags.  So I checked them with "Audio Tag Tool" and noticed that there is no tag information for ID3V1 or 2.

So...what kind of tags is Sound Juicer writing?  I noticed that they display fine in Exaile or Rhythmbox.

Is there a way to to tell Sound Juicer what kind of tags to write?

If not...is there another CD ripper that is as straight-forward (well, minus that gstreamer pipeline garbage...) to use as Sound Juicer?

Thanks.

---

### Post by DownTown22 on 2008-08-25
Anybody?

---

### Post by mpecho on 2008-09-07
> **DownTown22 said:**
> 
So...what kind of tags is Sound Juicer writing?  I noticed that they display fine in Exaile or Rhythmbox.


I don't know anything about Exaile, but I think that Rhythmbox will display the song name from the file name if there are no tags present.  To see if that's what's going on, find a song in Rhythmbox that does not show tags on your mp3 player, try right clicking on it and select "Properties".  The "Basic" tab shows the tags and the "Details" shows the file info.  If you are not getting tags . . .


> 
Is there a way to to tell Sound Juicer what kind of tags to write?



You need to edit the mp3 profile in soundjuicer.  menu: Edit | Preferences.

At the bottom in the "Formats" section, Click "Edit Profiles" button, then select your mp3 profile and "Edit".

The following is my GStreamer pipline:

audio/x-raw-int,rate=44100,channels=2!lame name=enc vbr=0 bitrate=192 ! id3v2mux

I'm not sure what each part means, but setup seems to write tags ok as well as appropriate filenames.

If you have tags showing when displaying song properties in Rhythmbox, then I think you have something else going on that is over my head.

---

