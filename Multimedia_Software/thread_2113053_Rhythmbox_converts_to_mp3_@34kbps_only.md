---
title: "Rhythmbox converts to mp3 @34kbps only"
date: 2013-02-06
forum: Multimedia Software
---

### Post by therieb on 2013-02-06
Hello everyone,

I believe this is a variation on the Rhythmbox CD ripping problem that already has a bug report.  

When I try to put an m4a file onto my Sansa mp3 player, Rhythmbox converts it to mp3, but only @34kbps.  I would like the option to convert @320, or in FLAC, which is available in Banshee.

If there is a way to choose the bit rate or format that Ryhthmbox converts to, I'd be much obliged if someone could let me know.

99% to full gapless music happiness,

Therieb

---

### Post by speartip on 2013-02-06
You might be best to use an external program like soundconvertor, then copy to your sansaclip.
 If the m4a file is already a lossy file, like the 256kbps ones you can get off iTunes, it would be pointless converting to flac, as all it would do is increase the file size, with no increase in quality.

---

### Post by shantiq on 2013-02-06
or even have some fun with your terminal:KS


>  cd   ~/Music/'here enter name of the folder where your files are'


then to convert  [256 can be what YOU wish it to be]
 
>  for f in *.m4a; do ffmpeg -i "$f"  -b:a 256k  "${f%.*}.mp3"; done

make a folder on desktop with your new files


> mkdir ~/Desktop/MP3 &&  mv *.mp3 ~/Desktop/MP3 


and drag files in this folder  to your Sansa

---

### Post by therieb on 2013-02-06
thank you for the reply Speartip,

I agree that Soundconverter works, but I'd prefer an all in one solution.  Banshee accomplishes the task just fine, but the database performance in Rhythmbox is so much better that I'd like to switch.  Perhaps I should be focusing on speeding up Banshee...

---

### Post by therieb on 2013-02-06
Thank you for your advice Shantiq,

I have used ffmpeg before, but perhaps you can help me with the syntax.  Here's what I would like: for some folder "x" please find all files in all sub-folders with the tag .m4a, convert these files to .mp3 @320 with LAME encoding, please do not delete the original .m4a files, also please ignore any other files (.flac, etc), and recreate the same file structure with subfolders in a new folder called "xmp3" or whatever.

Is all of this possible in one or more commands?  

The original folder is about 240 gigs, so I imagine my grandchildren may enjoy the new files an around 50 years time.

Thanks in advance, therieb

---

### Post by evilsoup on 2013-02-06
For recursiveness, you'd have to use find.

```

find . -mindepth 1 -type d -exec bash -c 'mkdir "$0"/mp3s' '{}' \;
find . -type f -iname "*.m4a" -exec bash -c 'ffmpeg -i "$0" -q:a 2 "$(dirname $(readlink -f "$0"))"/mp3s/"${0%.*}.mp3"' '{}' \;

```This is pretty compacted; if you really wanted to, you could probably squeeze it all into one command-line.

The first find command goes through all directories in the current directory & creates 'mp3s' as a directory within them (try saying that ten times fast).

The second find command finds every *.m4a or *.M4A, and uses ffmpeg to create an MP3 within the directory 'mp3s'. So an input of "/home/you/Music/some band/some song.m4a" will create an output file at "/home/you/Music/some band/mp3s/some song.mp3"

---

