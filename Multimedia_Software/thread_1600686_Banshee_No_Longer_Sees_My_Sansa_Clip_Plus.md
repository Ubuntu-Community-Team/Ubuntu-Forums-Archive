---
title: "Banshee No Longer Sees My Sansa Clip Plus"
date: 2010-10-19
forum: Multimedia Software
---

### Post by Luggy on 2010-10-19
Hello All,

Last week when I was still running Lucid I could get Banshee to read and write to my Sansa Clip Plus fine, but now that I have upgraded to Maverick Banshee can no longer see it.

I have it set in MSC mode with an .is_audio_player file (that worked back in Lucid) and Rhythmbox can see it and read and write to it fine.

Has anyone else encountered this problem or does anyone else know what might be causing it?

Banshee's version is 1.7.6 and the contents of my .is_audio_file are posted below:
```

audio_folders=MUSIC/,PODCASTS/,AUDIOBOOKS/
output_formats=application/ogg,audio/mpeg,audio/flac,audio/x-ms-wma,audio/aac,audio/mp4,audio/audible
input_formats=application/ogg,audio/mpeg,audio/flac,audio/x-ms-wma,audio/aac,audio/mp4,audio/audible
folder_depth=1
playlist_path=PLAYLISTS/%File
playlist_format=audio/x-iriver-pla

```

---

### Post by Luggy on 2010-10-19
I used Ubuntu Tweak to access the Banshee PPAs and upgraded Banshee to 1.8.0.

Now Banshee can see my Sansa Clip Plus.

---

### Post by waspbr on 2010-12-29
hmm, I haven't been able to have banshee interact with my sansa clip+ for a while.

In MTP mode ubuntu seems to detect it as a camera

and in MSC mode, it only works with Clementine. Any tips?

---

