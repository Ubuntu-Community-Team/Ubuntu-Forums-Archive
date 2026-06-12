---
title: "Strange video problem [read full post please]"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by amgeex on 2007-04-29
The overall experience with Feisty has been great, but for some really strange reason I cannot play four (4) .avi video files that played just fine on edgy, the sound is fine, but I get no image. The files also play fine on my girlfriend's laptop with edgy. I thought that the files got corrupted or something, so I deleted and downloaded them again, but the same problem arose.

These video files are the first four episodes of an anime series called Serial Experiments Lain. Now the really weird thing is that all 13 episodes from the series are encoded with the same codec, which is wmv9, but for some reason the first four episodes won't play (just sound, no image) and I get a codec error, although all the codecs are properly installed and the episodes 5 to 13 play without problems.

Anyone got any idea about how to fix this? I've tried playing them with totem-gstreamer, totem-xine, xfmedia player, and vlc player, but all fail with the same issue.

Thanks in advance,
amgeex

---

### Post by mrpaco on 2007-04-30
I seem to remember when I installed feisty that it uses a different restricted format package than edgy (I think, I could be wrong).  Perhaps this could be the issue, and installing the codecs from edgy could fix it?

---

### Post by konungursvia on 2007-04-30
Yes, it sounds like you either have not downloaded restricted video format drivers, or if you have, your video players have not been set up to recognize or use the codecs in question. Are they avi files, or matroska, or wmv? Or other unusual formats?

---

### Post by amgeex on 2007-04-30
Ok, the files are four AVI files encoded with wmv9. I've got 9 other files that are encoded with the same codec and are also AVI, those files play ok. The first four files don't display any image, just sound. All the codecs are properly installed and all my videos play fine, except those four. Anyone has any clue?

---

