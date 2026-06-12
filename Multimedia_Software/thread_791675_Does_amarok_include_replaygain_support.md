---
title: "Does amarok include replaygain support?"
date: 2008-05-12
forum: Multimedia Software
---

### Post by mmcmonster on 2008-05-12
I'm planning on using mp3gain on my music collection to normalize the sound.  From what I understand, it adds metadata to the ID3 tags of the .mp3 files, and the music applications have to use that to adjust the sound level at playback.

Does amarok include replaygain support, or do I need to download a particular package?

Also, if it does support replaygain, does it normalize music that is synced to my ipod? (I think iTunes does something like this now with [soundcheck]("http://docs.info.apple.com/article.html?artnum=61655"))

---

### Post by jessika-kaos on 2008-05-12
From Amarok's script manager you can download a script that adds various replaygain functionalities. I don't know about getting it to work with your ipod, however.

---

### Post by Exakun on 2008-10-12
Amarok does not come with ReplayGain support by default. A script to give it this capability is available [COLOR="Blue"][here (link)]("http://www.kde-apps.org/content/show.php/ReplayGain?content=26073")[/COLOR]. In Amarok, open the Tools > Script Manager, click the install button, and navigate to the archive you downloaded. Amarok will then install the script. To add replaygain to MP3 files, you must additionally download the package "mp3gain", available via the Ubuntu repositories. As an aside, jessika-kaos: I could find no mention of a replaygain script using the download option in Amarok's script manager.

Your assessment of how mp3gain works is mostly correct. Any application that supports replaygain should operate as expected, however, not all applications handle volume levelling quite the same.

iTunes has (at least, last time I used it) its own method of applying gain to mp3 files by putting some sort of code into the mp3 comments tag that is recognized specifically by the iPod. To the best of my knowledge this functionality differs substantially from replaygain, and therefore replaygain tags will probably not work with your iPod in the same manner. I would love to see a PMP that properly supports replaygain, though I have yet to use one.

---

### Post by Artemis3 on 2008-10-17
mp3gain has 2 modes of operation, current default is what you say, just write replaygain tags and hope the player reads these tags to apply the volume changes at playback.

But there is another mode, where the global gain value of the mp3 file is modified (albeit in 1.5db increments), this works with all mp3 decoders, because mp3 global gain is part of the spec, so yes, works with ipods, chinese s1, amarok without replaygain support, etc.

I use this command for that effect:
```
mp3gain -r -d 3 musicfile.mp3
```

Default value for replaygain is usually -89db, but for a portable i consider this too low, so i add 3 db to reach -92db which very rarely peaks. If you do this to all your mp3 files, they will play with the same perceived volume.

It is possible to undo this (-u) because the needed information is stored in the tags.

---

