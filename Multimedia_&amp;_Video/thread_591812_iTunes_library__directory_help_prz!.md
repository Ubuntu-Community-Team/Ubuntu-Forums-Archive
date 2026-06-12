---
title: "iTunes library / directory help prz!"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by thewretched on 2007-10-25
Howdy there! I'm pretty new to linux, and I recently installed songbird. I'm having issues trying to import my library. I'm running a dual boot system with linux on a small partition of my main drive. I also have a storage drive (labeled Storage, mounted as /media/sdb1) that has all of my Mp3s and movies and things.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=238328&highlight=itunes+library+xml+perl+script&page=5") and used the perl script there (thanks spin2cool!) to fix the file paths in my iTunes xml library file. Unfortunately, I seem to have hit a snag. My storage drive is formatted in NTFS, with spaces in folder names (for example, my music is under D:/My Music/*). However, Songbird wont play any of the songs in my library, and I *think* it's due to the space in the file name. Here is the script I am using:

#!/bin/bash
cp /media/sda1/Documents\ and\ Settings/Jared\ M/My\ Documents/My\ Music/iTunes/iTunes\ Music\ Library.xml /tmp/
perl -pi -e 's/file\:\/\/localhost\/D\:\/My%20Music\//\/media\/sdb1\/My\ Music\//g' /tmp/iTunes\ Music\ Library.xml
echo "Use File>Import Library to import the library (found at /tmp/iTunes Music Library)";

And this is an example of the file paths in my library.xml AFTER the script:

<key>Location</key><string>/media/sdb1/My Music/311/311/01%20Down.mp3</string>

I've tried changing the perl string a few times. For example, I tried \MyMusic\, \My_Music\, etc, but to no avail.

I could change the folder to MyMusic or My_Music, but then I would have to change the library in windoze, so i'm botched either way.

Any suggestions? Thanks!

---

### Post by thewretched on 2007-10-25
Hmm, snag. Okay, so i've figured out that if I enclose the folder with the space in quotes, the file directory works. However, most of my mp3's are in the file format "track# track-name", so the files come out in the format "01%20TrackName.mp3".

What can I do about the space placeholders (%20)? Anything?

Thanks.

---

### Post by thewretched on 2007-10-26
well, I wrote a second script to replace all "%20"'s with both empty quotation marks and with "\ ". In both cases, i could access the files in konsole (although they were permission denied), but in both cases the files did not show up in songbird. 

halp! :)

---

### Post by thewretched on 2007-10-26
Woo. I got this to work, for anyone interested.

Songbird looks for files as "file:\\\media\drive\etc", but with the original script it rewrites the library paths as "\media\drive\etc". All I needed to do was add the file:\\ to the beginning. Here is the final code I used:

#!/bin/bash
cp /media/sda1/Documents\ and\ Settings/Jared\ M/My\ Documents/My\ Music/iTunes/iTunes\ Music\ Library.xml /tmp/
perl -pi -e 's/file\:\/\/localhost\/D\:\/My%20Music\//file\:\/\/\/media\/sdb1\/My%20Music\//g' /tmp/iTunes\ Music\ Library.xml
echo "Use File>Import Library to import the library (found at /tmp/iTunes Music Library)";

---

