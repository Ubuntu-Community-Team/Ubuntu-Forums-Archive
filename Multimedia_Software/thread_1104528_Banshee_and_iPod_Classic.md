---
title: "Banshee and iPod Classic"
date: 2009-03-23
forum: Multimedia Software
---

### Post by DeadlyAura on 2009-03-23
So, I can't figure it out for the life of me.

When I first installed Ubuntu 8.10, I plugged in my iPod classic, it asked to rebuild my iPod database, and from then on out I could manage all my music with Banshee. It was beautiful.

After F-ing things up and forcing me to reformat, this little buggy no longer works. The iPod is recognized by Ubuntu, but not in Banshee, and I can't manage any of my music.

It seems as if Banshee does not provide support for the iPod classic as of yet due to Apple's annoying checksum, but there MUST be a way to get Banshee to at least recognize the iPod and allow me to add/remove music.

Thanks in advance for any knowledge or tips you can provide!

---

### Post by rozbarwinek on 2009-03-23
Create a "**.is_audio_player**" file in your iPod main directory and paste this to that file -->

```
audio_folders=MP3/,MUSIC/,RECORDINGS/,AUDIO/
folder_depth=2
output_formats=audio/mpeg,audio/mp3,audio/x-aac
```

Now unmount iPod and mount it again :)

I don't have iPod so if Banshee will save files in wrong directory just change audio_folders and folder_depth in that file :)

---

