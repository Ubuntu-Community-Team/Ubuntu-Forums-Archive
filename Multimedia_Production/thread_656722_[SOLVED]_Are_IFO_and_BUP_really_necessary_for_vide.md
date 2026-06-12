---
title: "[SOLVED] Are IFO and BUP really necessary for video DVDs?"
date: 2008-01-02
forum: Multimedia Production
---

### Post by xfred on 2008-01-02
Well, are they :)?

I've just wasted a few days trying to rid a dvd of annoying non-skippable previews, and finally found that I can get exactly what I'm looking for by using dvd::rip to extract VOB files for just the movie, renaming them vts_01_0.vob, vts_01_1.vob etc, dumping them in a video_ts folder and creating an ISO.  The result plays fine in VLC, but before I burn to an expensive dual-layer dvd for the ultimate test, does anyone want to save me a coaster and tell me if this will fail in a real DVD drive due to lack of ifo and bup files?

---

### Post by yabbies on 2008-01-02
you need ifo files to tell the dvd player chapter, subtitles, audio, etc information. bup is just a backup file to the ifo.
when using a burning software they usually make new ifo files automatically for you.

with just a bunch of vob files in a folder the player doesn't know in what order to play the files without the ifo.

---

### Post by EXCiD3 on 2008-01-02
Thanks for the info on the IFO files. I've never really paid attention to what they did. I figured thats what they did since the vob files are always so large which meant they contained the audio/video.

I know with Windows i always saved my dvd rips to an iso and then mounted them to a virtual drive to make sure they worked correctly. How would you do this in Ubuntu?

---

### Post by ~LoKe on 2008-01-02
IFO is basically an index telling the DVD what to play and when.

**EDIT**: That's been answered, sorry.

---

### Post by xfred on 2008-01-03
Thanks, that makes sense.

I eventually tried burning what I had out of curiosity.  As you might expect on a real DVD player (not VLC, which is apparently too smart for its own good) it just threw up a list of titles, one per vob, that could be played independently, but not sequentially.

Anyhow, I've installed DeVeDe and am creating an ISO as we speak.  Fingers crossed it makes the IFOs for me.

---

### Post by xfred on 2008-01-03
> **EXCiD3 said:**
> I know with Windows i always saved my dvd rips to an iso and then mounted them to a virtual drive to make sure they worked correctly. How would you do this in Ubuntu?

You don't actually need to mount an ISO to play it if you have VLC installed - it can load and play ISO files directly.

If you need to mount ISOs for some other purpose try:

```
sudo mount -t iso9660 -o loop your_iso.iso /your/target/directory/
```

then just point your application at that directory instead of a drive.  To unmount the ISO once you're finished use:

```
sudo unmount /your/target/directory/
```

(on a related note, two things that would be really handy in the Ubuntu GUI:

1. when you right click on an ISO, how about adding a "mount" option to make things a little easier for us newbies?
2. when you right click on a directory with the "video_ts" / "audio_ts" (ie. DVD type) file structure, how about an option for "play this like you would play a DVD when autoplay is enabled"?

not vital, but would be nice to have, especially the first one).

---

### Post by ~LoKe on 2008-01-03
> **xfred said:**
> Anyhow, I've installed DeVeDe and am creating an ISO as we speak.  Fingers crossed it makes the IFOs for me.

I've used Devede back when I was a big newb and couldn't figure anything out.  I think it's time I gave it a second chance.

---

