---
title: "Searching for rogue MP2 files"
date: 2008-01-07
forum: Multimedia Production
---

### Post by RobMBaker on 2008-01-07
I'm having slight issues with mpeg layer 2 files.

My phone won't play them, neither will other mp3 players in my house, so I want to find all the *.mp3 files that are actually layer 2 only.

I can't seem to find any way of locating by audio codec type - I tried to pipe some files to gst-typefind-0.10 but then realised that I don't want the mimetype, I want to search for audio codec types.

Does anyone know how to do this? I really don't want to have to go through my entire music collection one-by-one, doing Right-Click-->Properties-->Audio to see which ones are mp2.

Thanks.

---

### Post by Creative2 on 2008-01-07
mmm **maybe**... if, for ONE file, this works for you

ffmpeg -i INPUT  

OR 

file -i INPUT 


you could use a interface to do that...let me know if that command is usefull or not

good luck

---

### Post by RobMBaker on 2008-01-09
Well, I'm not sure where you're going with that - ffmpeg just returns its standard "You need to supply an output file" error message.

---

### Post by Creative2 on 2008-01-09
of couse not.....
example.....

Fmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
invalid new backstep 1008
[B]Input #0, mp3, from '/media/sda7/a/Audio/aaa.mp3':
  Duration: 00:01:39.0, start: 0.000000, bitrate: 320 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 320 kb/s
Must supply at least one output file[/B]


as you can see if you look at the end you see


[B]Input #0, mp3, from '/media/sda7/a/Audio/aaa.mp3':
  Duration: 00:01:39.0, start: 0.000000, bitrate: 320 kb/s
***_  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 320 kb/s_***


so if you want : 

so I want to find all the *.mp3 files that are actually layer 2 only.

you want mp2

so ffmpeg.... will say 

[B]Input #0, mp3, from '/media/sda7/a/Audio/aaa.mp3':
  Duration: 00:01:39.0, start: 0.000000, bitrate: 320 kb/s
***_  Stream #0.0: Audio:[COLOR="Red"] mp2[/COLOR], 44100 Hz, stereo, 320 kb/s_***

---

### Post by RobMBaker on 2008-01-09
right, thanks, but do you know how to put that together in a pipe, starting with "find" or "locate" and ending with a "grep mp2"?

Thanks for ur help so far - I hadn't even thought of using ffmpeg!

---

### Post by RobMBaker on 2008-01-09
I've tried using:-

find . -print | file -

To check the file type of each file in the directory where I'm working, which I was hoping to grep for mp2 ... but I don't know how to get 'file' to see a list of filenames, to be tested one at a time - it just seems to be seeing the whole stdin and stating that it's a text file!

---

### Post by Creative2 on 2008-01-09
#create a file with  path of the file 
echo INPUT >>/tmp/mp2.txt 
#add what ffmpeg about INPUT
ffmpeg -i INPUT 2>&1 | sed -n "10 p"  >> /tmp/mp2.txt
#this should delete  the line immediately before       Audio: mp3
```
sed -n -e '/Audio: mp3/{=;x;1!p;g;$!N;p;D;}'  >/tmp/temp1.txt
```

mmm this is only theory....unluckly i have no time now i will try tomorrow 
if you want try by yourself try to watch here 
[http://www.student.northpark.edu/pemente/sed/sed1line.txt](http://www.student.northpark.edu/pemente/sed/sed1line.txt)

or man sed  
or man awk 

cheers

---

### Post by Creative2 on 2008-01-10
my idea was this :

create a file txt where there is only mp2 file with path

to do this i thinked :

add mp3 file and mp2 without difference and write what ffmpeg said about that in another line

```
echo INPUT >> /tmp/filemp2.txt; ffmpeg -i INPUT 2>&1 | sed -n "10 p" >> /tmp/filemp2.txt
```


so filemp2.txt shoudl be like this

[I]/path/file.mp3
 Stream #0.0: Audio: **mp3**, 44100 Hz, stereo, 320 kb/s
/path2/file.mp3
 Stream #0.0: Audio:** mp2**, 44100 Hz, stereo, 320 kb/s[/I]

now with this  should delete the line immediately before Audio: mp3 so if mp2 it doesn't delete 

```
sed -n -e '/Audio: mp3/{=;x;1!p;g;$!N;p;D;}'   /tmp/filemp2.txt >>/tmp/filemp2.txt
```

so the files should be this

 Stream #0.0: Audio: **mp3**, 44100 Hz, stereo, 320 kb/s
/path2/file.mp3
 Stream #0.0: Audio:** mp2**, 44100 Hz, stereo, 320 kb/s[/I]




after that you could delete every starts with :
** Stream**


so to  do that  maybe 

```
 sed -n '/Stream/d' /tmp/filemp2.txt >>/tmp/finishedmp2listtxt
```

well if it works...you should use something to do loop....unluckly i have tried to force my interface but xD no work...ù.ù 
sorry i can't do more of this...maybe the idea can work
cheers

---

### Post by RobMBaker on 2008-01-12
Thanks very much!
I'll certainly give it a go - I'll see if I can get it to work how I want.

---

### Post by RobMBaker on 2008-01-12
Don't worry any more - I just worked out a really easy way of doing it, with your earlier suggestion of using 'file'.

I just didn't know how to make file read the stdin properly, turns out this works:-

find . -iname *.mp3 -print | file -f - | grep MP2

That seems to find all *.mp3 files in and below the working directory, print them to the stdout, one per line; then file reads the stdin, one file per line, and then I grep for MP2.

After all that effort, it turns out there were no mp2s left - I've already found them all at some time or other!!!

Thanks for all your help, all the same. :)

---

### Post by Creative2 on 2008-01-12
:)
nice =)) i like it

---

### Post by RobMBaker on 2008-01-13
Doh! I thought it had worked, but 'file' isn't good enough - it reads all the files with *.mp3 extensions as MP3-encoded.

Is there another function that can read the stdin properly and do a codec check?
I've looked at ffmpeg and gst-typefind; but neither of them can read from the stdin for a list of files to check.

---

### Post by RobMBaker on 2008-02-07
Bump! Anyone?

---

