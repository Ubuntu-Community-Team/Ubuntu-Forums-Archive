---
title: "Find all files by encoding method?"
date: 2015-07-12
forum: Multimedia Software
---

### Post by Rytron on 2015-07-12
Hi.

Is there a way to find all files in a directory that were encoded with a particular method(s)? For example, files that were encoded with AVC video and AAC audio?

Kind of like the MediaInfo program but instead lists all files with particular encoding methods.

Thanks.

---

### Post by dino99 on 2015-07-12
'file' command might help you

[http://unix.stackexchange.com/questions/172320/check-files-for-conventions](http://unix.stackexchange.com/questions/172320/check-files-for-conventions)
[http://stackoverflow.com/questions/805418/how-to-find-encoding-of-a-file-in-unix-via-scripts](http://stackoverflow.com/questions/805418/how-to-find-encoding-of-a-file-in-unix-via-scripts)
[http://unixhelp.ed.ac.uk/CGI/man-cgi?file](http://unixhelp.ed.ac.uk/CGI/man-cgi?file)

---

### Post by tgalati4 on 2015-07-12
*easytag* is a file browser that scans ID3 tags and shows encoding.  There may be a command line tool using ID3 tools, but I don't know the exact syntax.

> tgalati4@Mint17 ~/Music/Podcasts/FLOSS Weekly $ apt-cache search music ID3
dir2ogg - audio file converter into ogg-vorbis format
gimmix - graphical music player daemon (MPD) client using GTK+2
glurp - GTK+ frontend to the Music Player Daemon (MPD)
gmpc - Gnome Music Player Client (graphical interface to MPD)
gmpc-data - Gnome Music Player Client - data files
gmpc-dbg - Gnome Music Player Client - debugging symbols
gmpc-dev - Gnome Music Player Client (plugin development files)
id3 - Editor for ID3 tags
id3tool - Command line editor for id3 tags
id3v2 - A command line id3v2 tag editor
kid3 - KDE MP3 ID3 tag editor
kid3-cli - Command line audio tag editor
kid3-core - Audio tag editor core libraries and data
kid3-qt - Audio tag editor
puddletag - simple, powerful audio tag editor
python-tagpy - Python module for manipulating tags in music files
ripit - Textbased audio CD ripper
ruby-mp3tag - Ruby library for manipulating ID3V1.1 tags in MP3
xmms2-plugin-id3v2 - XMMS2 - ID3v2 plug-in


The simple *id3* tool does not do it:

> tgalati4@Mint17 ~/Music/Podcasts/FLOSS Weekly $ id3 -l *.mp3
FLOSS Weekly 319_ Fedora 21.mp3:
Title  : Fedora 21                       Artist: TWiT                          
Album  : FLOSS Weekly                    Year: 2014, Genre: Unknown (255)
Comment: [http://twit.tv/floss](http://twit.tv/floss)            Track: 0
FLOSS Weekly 320_ Fossil.mp3:
Title  : Fossil                          Artist: TWiT                          
Album  : FLOSS Weekly                    Year: 2015, Genre: Unknown (255)
Comment: [http://twit.tv/floss](http://twit.tv/floss)            Track: 0
FLOSS Weekly 321_ Marpa.mp3:
Title  : Marpa                           Artist: TWiT                          
Album  : FLOSS Weekly                    Year: 2015, Genre: Unknown (255)
Comment: [http://twit.tv/floss](http://twit.tv/floss)            Track: 0


Nor does *id3v2*:

> tgalati4@Mint17 ~/Music/Podcasts/FLOSS Weekly $ id3v2 -l *.mp3
id3v1 tag info for FLOSS Weekly 319_ Fedora 21.mp3:
Title  : Fedora 21                       Artist: TWiT                          
Album  : FLOSS Weekly                    Year: 2014, Genre: Unknown (255)
Comment: [http://twit.tv/floss](http://twit.tv/floss)            Track: 0
id3v2 tag info for FLOSS Weekly 319_ Fedora 21.mp3:
TIT2 (Title/songname/content description): Fedora 21
TPE1 (Lead performer(s)/Soloist(s)): TWiT
TPE2 (Band/orchestra/accompaniment): TWiT
TALB (Album/Movie/Show title): FLOSS Weekly
TYER (Year): 2014
TCON (Content type): Podcast (255)
COMM (Comments): ()[eng]: [http://twit.tv/floss](http://twit.tv/floss)
TCOP (Copyright message): These netcasts are released under a Creative Commons Attribution Non-Commercial Share-Alike license. TWiT and TWiT Logo are registered trademarks of Leo Laporte.
TPUB (Publisher): TWiT
APIC (Attached picture): (Front Cover)[, 3]: image/jpg, 216421 bytes
TRCK (Track number/Position in set): 319
id3v1 tag info for FLOSS Weekly 320_ Fossil.mp3:
Title  : Fossil                          Artist: TWiT                          
Album  : FLOSS Weekly                    Year: 2015, Genre: Unknown (255)
Comment: [http://twit.tv/floss](http://twit.tv/floss)            Track: 0
id3v2 tag info for FLOSS Weekly 320_ Fossil.mp3:
TIT2 (Title/songname/content description): Fossil
TPE1 (Lead performer(s)/Soloist(s)): TWiT
TPE2 (Band/orchestra/accompaniment): TWiT
TALB (Album/Movie/Show title): FLOSS Weekly
TYER (Year): 2015
TCON (Content type): Podcast (255)
COMM (Comments): ()[eng]: [http://twit.tv/floss](http://twit.tv/floss)
TCOP (Copyright message): These netcasts are released under a Creative Commons Attribution Non-Commercial Share-Alike license. TWiT and TWiT Logo are registered trademarks of Leo Laporte.
TPUB (Publisher): TWiT
APIC (Attached picture): (Front Cover)[, 3]: image/jpg, 216421 bytes
TRCK (Track number/Position in set): 320
id3v1 tag info for FLOSS Weekly 321_ Marpa.mp3:
Title  : Marpa                           Artist: TWiT                          
Album  : FLOSS Weekly                    Year: 2015, Genre: Unknown (255)
Comment: [http://twit.tv/floss](http://twit.tv/floss)            Track: 0
id3v2 tag info for FLOSS Weekly 321_ Marpa.mp3:
TIT2 (Title/songname/content description): Marpa
TPE1 (Lead performer(s)/Soloist(s)): TWiT
TPE2 (Band/orchestra/accompaniment): TWiT
TALB (Album/Movie/Show title): FLOSS Weekly
TYER (Year): 2015
TCON (Content type): Podcast (255)
COMM (Comments): ()[eng]: [http://twit.tv/floss](http://twit.tv/floss)
TCOP (Copyright message): These netcasts are released under a Creative Commons Attribution Non-Commercial Share-Alike license. TWiT and TWiT Logo are registered trademarks of Leo Laporte.
TPUB (Publisher): TWiT
APIC (Attached picture): (Front Cover)[, 3]: image/jpg, 216421 bytes
TRCK (Track number/Position in set): 321


There is *soxi* (part of sox) but I don't know if it will work with video files.  That you will have to test.

---

### Post by mc4man on 2015-07-12
With some fancy scripting would could use mediainfo cli very well here. 
A relatively simplistic  command that would produce a text file in that dir.  you can parse would be to cd to a dir., then 
```
for f in *.*; do mediainfo "$f" |grep 'Complete name\|AVC\|AAC' >> info.txt; done
```
Any Complete names that had a Format,  Codec id or both  below the name would either or both of the above (AVC AAC

---

### Post by Rytron on 2015-07-16
> **mc4man said:**
> With some fancy scripting would could use mediainfo cli very well here. 
A relatively simplistic  command that would produce a text file in that dir.  you can parse would be to cd to a dir., then 
```
for f in *.*; do mediainfo "$f" |grep 'Complete name\|AVC\|AAC' >> info.txt; done
```
Any Complete names that had a Format,  Codec id or both  below the name would either or both of the above (AVC AAC

Cheers mc4man. Your solution is excellent.

---

### Post by Rytron on 2015-07-24
> **mc4man said:**
> With some fancy scripting would could use mediainfo cli very well here. 
A relatively simplistic  command that would produce a text file in that dir.  you can parse would be to cd to a dir., then 
```
for f in *.*; do mediainfo "$f" |grep 'Complete name\|AVC\|AAC' >> info.txt; done
```
Any Complete names that had a Format,  Codec id or both  below the name would either or both of the above (AVC AAC

Hello again mc4man. Can you make that mediainfo cli command be recursive?

---

### Post by Keith_Helms on 2015-07-26
Do you mean recursive as in able to handle multiple subdirectories?  Try this:
```
for f in find ./ -type f; do mediainfo "$f" | grep 'Complete name\|AVC\|AAC' >> info.txt; done
```

---

### Post by Rytron on 2015-07-26
> **Keith_Helms said:**
> Do you mean recursive as in able to handle multiple subdirectories?  Try this:
```
for f in find ./ -type f; do mediainfo "$f" | grep 'Complete name\|AVC\|AAC' >> info.txt; done
```

You are awesome at coding.

The info.txt looks fine.

I got this output in the terminal. Not sure if it matters.

```
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
E: File read error
```

---

### Post by Keith_Helms on 2015-07-26
Yeah, I got some of those error messages too.  I looked it up and it appears to be some bug in mediainfo that isn't fixed yet.  If you don't want to look at them, you could change the command to:
```
for f in find ./ -type f; do mediainfo "$f" 2>/dev/null | grep 'Complete name\|AVC\|AAC' >> info.txt; done
```

---

### Post by Rytron on 2015-07-27
> **Keith_Helms said:**
> Yeah, I got some of those error messages too.  I looked it up and it appears to be some bug in mediainfo that isn't fixed yet.  If you don't want to look at them, you could change the command to:
```
for f in find ./ -type f; do mediainfo "$f" 2>/dev/null | grep 'Complete name\|AVC\|AAC' >> info.txt; done
```

Perfect, Keith, you are a CLI guru. :p

---

