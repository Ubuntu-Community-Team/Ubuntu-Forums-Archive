---
title: "Fixing mp3"
date: 2009-08-11
forum: Multimedia Software
---

### Post by miguelesquirol on 2009-08-11
I have problems with my mp3 because every audio software i use (music player, songbird, etc.) can't recognize all my music and a lot seem lost, even VLC can't play it. The error text says: "can't recognice type of stream". Is a way to fix that?

---

### Post by rainwalker on 2009-08-11
Have you installed the codecs to play restricted formats?

---

### Post by miguelesquirol on 2009-08-12
Yes, all the codecs are installed, I think. How could I check that?

---

### Post by rainwalker on 2009-08-13
I believe all you need to install is the "ubuntu-restricted-extras" package, but just to be safe I would add the Medibuntu repos and install the restricted codecs from there too (if you haven't already): [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by miguelesquirol on 2009-08-13
Everything is installed, and i still get the "Could not determine type of stream.", in an album that some songs works and not others.

---

### Post by rainwalker on 2009-08-13
Hm...even the "w32codecs"?

---

### Post by sblunix on 2009-08-13
To download all codecs just go ahead and [Click Here]("apt:non-free-codecs")

---

### Post by Crunchy the Headcrab on 2009-08-13
Fluendo offers an mp3 codec on their website.  You have to register to download the .deb file.  They've worked great for me so it's the codec that I use on any gnome distro.

---

### Post by mc4man on 2009-08-13
> in an album that some songs works and not others. 
That would seem to indicate a problem with the 'bad' files, not a codec or lack of. (assuming that you can play .mp3's otherwise

If thats true then you could try to develop some info on the files

Apps that can do so are mediainfo; sox; mplayer; ffmpeg

For mediainfo go here, pick your ubuntu version and download/install 3 packages in order from bottom to top (libzen0, libmediainfo0, GUI.

[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

Open mediainfo (applications -> sound & video and drag and drop a 'bad' mp3 into,
If anything shows up switch the view to html for extended info, text if something interesting to copy & paste back.

You could also open a 2nd instance of mediainfo and drop one of your 'good' mp3's into to cross compare

For sox, search in synaptic and install alomg with the sox .mp3 library ( I use a built version that's all inclusive, seems likely you'd need the mp3 lib.

First try to play in sox (command is play. -V# is verbose level (replace blue., if spaces in path and or name then put quotes around or just rename

```
play -V4 /path/to/[COLOR="Blue"]whatever.mp3[/COLOR]
```

or if at dir. prompt where .mp3 is or .mp3 is loose in home folder, then just
```
play -V4 [COLOR="Blue"]whatever.mp3[/COLOR]
```

for ffmpeg the same thing, try to play or input to
```
ffplay /path/to/[COLOR="Blue"]whatever.mp3[/COLOR]
```
```
ffmpeg -i /path/to/[COLOR="Blue"]whatever.mp3[/COLOR]
```

Same for mplayer or add a -v to comand
mplayer -v /path/to/[COLOR="Blue"]whatever.mp3[/COLOR]

(( easier to either  put a 'bad' mp3 loose in home folder or cd to dir. where mp3 is - eliminates needing path in command

Both sox and ffmpeg can covert back to wav if they can recognize and if there's no other way

Did you encode these 'bad'mp3's or acquire by other means?

---

### Post by miguelesquirol on 2009-08-13
Ok, here are the information. I installed SoX. The two songs are in the same folder, and I made them at the same time (long time ago, in windows, I don remember what software did I use).

here is the information for a song that doesn't play


play: SoX v14.2.0
time:  Dec  1 2008 10:12:25
issue: Ubuntu jaunty (development branch)
uname: Linux miguel-laptop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686
gcc:   4.3.3 20081130 (prerelease)
arch:  1248 48 44 L
play formats: no handler for file extension `mp3'


Here for the song that does play


play: SoX v14.2.0
time:  Dec  1 2008 10:12:25
issue: Ubuntu jaunty (development branch)
uname: Linux miguel-laptop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686
gcc:   4.3.3 20081130 (prerelease)
arch:  1248 48 44 L
play formats: detected file format type `audio/mpeg'
play formats: no handler for detected file type `audio/mpeg'


I might be doing something wrong here. I think i installed all de codecs.

---

