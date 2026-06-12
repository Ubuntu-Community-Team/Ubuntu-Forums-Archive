---
title: "Rename audio files with media information"
date: 2015-09-09
forum: Multimedia Software
---

### Post by oygle on 2015-09-09
Have a lot of audio files in a path, but the name of the file does not describe the audio content. I need to rename these audio files with the media information.

Title and artist to be the new name. Seems to be a bash script thing. Does anyone know how to do this please ?

---

### Post by shantiq on 2015-09-10
[puddletag]("http://puddletag.sourceforge.net/screenshots.html") or [easytag]("https://wiki.gnome.org/Apps/EasyTAG/Screenshots")    both in repo and  very good

if editing the info is what you are after

---

### Post by Lars Noodén on 2015-09-10
mediainfo is in the repository and good at extracting metadata from audio files.  Which format are they in?

```

mediainfo --Inform="General;%Track%" *somefile.flac*
mediainfo --Inform="General;%Album/Performer%" *somefile.flac*

```

---

### Post by MartyBuntu on 2015-09-10
Kid3-qt is a good tagger.

---

### Post by SeijiSensei on 2015-09-11
It sounds like you want to extract the track's title and make it into a filename?

How about something like this?
```

#!/bin/sh

FILES=/path/to/the/music
TYPE=flac

cd $FILES

for f in *.$TYPE
do
     TITLE=$(mediainfo $f | grep 'Track name ' | awk -F': ' '{print $2}')
     mv $f "$TITLE.$TYPE"
done

```

The space following "Track name" keeps grep from matching other lines like "Track name/Position".

Only minimally tested; YMMV.

---

### Post by oygle on 2015-09-14
Thanks for those replies everyone. I installed easytag first, and even though there was a function to use the Title and make it the filename, it didn't work, even though easytag log said it had changed the filename. Even made sure and pressed 'save', but filename was not changed. So installed puddletag, and it worked just fine. It's a bit easier to drive than easytag also. Now have all those audio filenames changed to reflect the Title from the tag.  :)

"SeijiSensei" thanks, I will try that script another time.

---

### Post by shantiq on 2015-09-15
Puddletag is better in my view simpler to use than easytag ...   glad to hear you concur :]

---

