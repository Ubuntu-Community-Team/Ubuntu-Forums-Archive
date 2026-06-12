---
title: "Can't transfer .ogg with Banshee"
date: 2009-12-17
forum: Multimedia Software
---

### Post by N00b-un-2 on 2009-12-17
No, I'm not trying to sync an iPod.  I have a cheap flash media player made by some company named Aikolo.  I found out by doing drag and drop that it is .ogg compatible (the manual it came with was in Chinese when I bought it in Kuwait about two years ago).
I like using Banshee to manage my devices, but I find it odd that as soon as I try syncing my media player with banshee that it starts to convert the files to MP3 and doesn't give me the option not to convert.  This worries me because I am getting a Sansa Fuze for Christmas and want to use Banshee to manage my Fuze.

---

### Post by N00b-un-2 on 2010-01-01
Okay, so for anyone else who is running into issues with mp3 players other than iPods, this tutorial should help.
All you have to do to make Banshee or Rhythmbox be able to sync music to an otherwise unsupported player is create a file in the root of the device called

```
.is_audio_player
```

Yes, it is a hidden file.  To view and edit this file, simply press ctrl+h.

To direct Banshee as to what types of files the player can handle (the default would be .mp3) and where to put them you can add a few lines to this file.  the '.is_audio_player' file for my Sansa Fuze looks like this.

```

name=Ryan's\ Fuze\ (8GB)
audio_folders=MUSIC/,RECORDINGS/,VIDEO/,PODCASTS/
folder_depth=2
output_formats=audio/ogg,audio/flac,audio/x-ms-wma,audio/mpeg,audio/aac,audio/x-wav,audio/avi

```

There doesn't seem to be a whole lot of documentation on this workaround despite the fact that it is very useful for anyone who is limited to using their music player in MSC mode (pretty much anything that's NOT an iPod).
While this is somewhat of a hack and not the most automated way of getting things to work, it is effective and will allow you to sync which is a very nice improvement over drag and drop.
My only complaint about adding music to my Fuze this way is that it does not copy the .jpg files that accompany my music which show up in the menus on the fuze (but the art attached to the ID3 tags shows up just fine, which is a HUGE advantage over the iPod on Linux).
You can try playing around with the arguments on this file.  That's how I figured out how to get Banshee to sync videos to my Fuze, and how to prevent it from transcoding my .ogg files to .mp3 when syncing.  hmmm... I wonder if I could write a plugin for Banshee that would automatically transcode video to the proper format when syncing to the Fuze (DivX5 224x176, 20fps w/ mp3 audio 128kbps as AVI) or do the same for iPods (mpeg4 with aac audio as mp4).
Now if only there was a way to sync photos to the Fuze using Banshee, it would be absolutely perfect.  Until then I guess I can still drag and drop those.

---

### Post by monstrosity on 2011-03-14
Thank you!!

---

