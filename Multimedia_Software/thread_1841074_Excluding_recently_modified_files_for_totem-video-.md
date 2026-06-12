---
title: "Excluding recently modified files for totem-video-thumbnailer"
date: 2011-09-08
forum: Multimedia Software
---

### Post by W3ird_N3rd on 2011-09-08
Well the title says it already. When I'm either encoding, recording or downloading a video and Nautilus is showing the file, totem-video-thumbnailer is behaving like a dog chasing a car: it'll generally never catch it, and even if it does, it soon realises it can do nothing but let it go again, and continue the chase.

It would be nice it totem-video-thumbnailer would not try to create thumbnails (and thus eating resources) for files modified less than a minute ago. (imho that should even be default behaviour)

Is that possible?

---

### Post by dniMretsaM on 2011-09-08
You could disable automatic thumbnailing and run the thumbnailer manually. You also might try [ffmpegthumbnailer]("http://code.google.com/p/ffmpegthumbnailer/"). I think it uses less resources than totem-video-thumnailer, so it would be less of an issue. It's also faster.

---

### Post by W3ird_N3rd on 2011-09-09
> **dniMretsaM said:**
> You could disable automatic thumbnailing and run the thumbnailer manually. You also might try [ffmpegthumbnailer]("http://code.google.com/p/ffmpegthumbnailer/"). I think it uses less resources than totem-video-thumnailer, so it would be less of an issue. It's also faster.
I don't really want to disable the thumbnailer altogether, running it manually isn't pretty either.

ffmpegthumbnailer would only be a partial solution or could even be worse, every time the thumbnailer (be it totem or ffmpeg) writes a thumbnail it's another write to my SSD. Totem appears to be generally to slow to thumbnail files that are being modified, but if ffmpeg would be fast enough, that would mean god-knows-how-many thumbnails per minute to my SSD for a video that's being recorded/encoded/downloaded.

Really, the thumbnailer should just leave files that were modified less than a minute ago alone.

[edit]In a test, it appears totem-video-thumbnailer doesn't actually run.. Just somewhat annoyingly the file flickers between the watch and the no-thumb icon, but video-thumbnailer does not appear to be running.

---

