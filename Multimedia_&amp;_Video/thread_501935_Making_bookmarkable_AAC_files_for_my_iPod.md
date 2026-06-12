---
title: "Making bookmarkable AAC files for my iPod"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by apastuszak on 2007-07-15
For various reasons I can't get into in this post, I can't use my Mac to create bookmarkable AAC files.

What I am trying to do is the following:

Take a bunch of MP3 files and join them together.
Convert the massive MP3 file to AAC
Rename the .m4a file to .m4b

And I want to do this on my Ubuntu box.  I found the mpgtx command line tools while did a wonderful job of joining all the MP3s and joining them quickly.

What I need to do now is find a way to convert the MP3 file to AAC from the command line.  I thought ffmpeg might be able to do something, but all the command line options I find just show how to convert an AAC file to MP3.

If anyone has a way to convert MP3 files to AAC, I would appreciate it.

Andy

---

### Post by tblain on 2007-08-01
Well, I can get you most of the way there.  I have had terrible luck converting large mp3s to aac/m4a format.  I end up getting problems and sections getting cut out as well as it taking forever to complete.   Pops and cracks that aren't in the large mp3 are put in the m4a file, and finally it would sometimes cause strange things to happen on my iPod.  I've had no issues yet converting many small files (seems to have a smaller chance of failure) and joining them together for the large file.  So I hope this gets you most of the way there:

Let's pretend we have an audiobook with 100+ tracks

I use SoundKonverter (find it in Add/Remove...), this is better than SoundConverter because it handles more codecs.  (I'm not sure why you require it to be a command line run item though...you could try vlc, but you'll have to work through the output options yourself)

Using Synaptic or apt-get, install faac

Now I can set SK to convert all 100+ files to aac.  I get an error everyone in a while but I just re-add them to convert and it goes through no problem.  I use aac because it's raw and has no headers.

Now use the cat command from the command line to join all the files together.  This is like the copy /b command in DOS.  

Now you have one big aac file.  Here's where I stop.

You said you want a m4a or m4b file.  You cannot just rename these files because the raw aac is missing the necessary headers for the m4a/m4b enclosure.  I've used dbPowerAmp in  Windows and it works great to simply add the headers without running it though another conversion process degrading quality.  But I have yet to figure out how to do that in ubuntu, had to use a VirtualBox Windows install to do it.

If you feel like you'll have better luck than me in converting a large mp3 file, then you can simply place it into SoundKonverter and convert directly to a m4a.

Hope that helps.

---

### Post by rflight79 on 2008-03-01
Try out this handy script that converts an entire directory of MP3's. The biggest thing I have found when using faac, is you need to specify the "-w" option (says to wrap it in m4a), and actually specify the output filename with "-o" and m4b extension, otherwise it does not seem to work.

```
#!/bin/bash
# mp3tom4b.sh
# bulk mp3 to m4b converter to generate bookmarkable aac files for ipod

mp3files="*.mp3"
wavend=wav
aacend=m4b
GENRE=Podcast
tmpdir=~/.backup_podcasts/ #change this depending on what you want to do with the old files

for file in $mp3files
do
  
  basenam=${file%.*3} # Get the first part of the filename, without the mp3 part

# Then run mplayer on the file, generating a wav file, using the mp3 file
  mplayer -vo null -vc null -ao pcm:fast:file=$basenam.$wavend $file

  id3v2 -C $file

  TITLE="`id3v2 -l $file | grep TIT2 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
  ARTIST="`id3v2 -l $file | grep TPE1 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
  ALBUM="`id3v2 -l $file | grep TALB | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
  TRACK="`id3v2 -l $file | grep TRCK | awk '{ORS=" "} {for (i = 6; i <= NF; i++) print $i}'`"
  YEAR="`id3v2 -l $file | grep TYER | awk '{ORS=" "} {for (i = 3; i <= NF; i++) print $i}'`"
  
  faac -b 32 -c 44100 --title "$TITLE" --artist "$ARTIST" --year "$YEAR" --album "$ALBUM" --track "$TRACK" --genre "$GENRE" -w -o $basenam.$aacend $basenam.$wavend

  rm $basenam.$wavend
  mv $file $tmpdir
  #echo "$basenam.$wavend"
  #echo "$basenam.$aacend"
  #wavnam="`echo $file | sed 's/mp3/wav/g'`"
  #echo "$wavnam"

done
```

---

