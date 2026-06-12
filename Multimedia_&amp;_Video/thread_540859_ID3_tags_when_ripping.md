---
title: "ID3 tags when ripping"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by LianerGoist on 2007-09-02
Hi

When I use Sound Juicer to rip and create mp3 files, it add ID3 tags in version 2.4.0. I can see that in Kid3. My mp3 player (Philips GoGear) don't like that format. I have some mp3 files with ID3 tag ver. 2.3, and it reads them just fine. Okay, I don't want to convert the ID3 tags every time I have ripped a CD - it must be possible to tell Sound Juicer to use ver. 2.3 (or 1.x) ID3 tags. But how?

This is the GStreamer Pipeline I use:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=128 ! id3v2mux

BTW - I have used Linux less than 4 days...

---

### Post by FrankQuist on 2007-09-27
Welcome to Ubuntu.

I am having the same problem. It seriously got me frustrated when I discovered, one or two days before going on holiday and after ripping around 50 CDs, that such tags were not readable by most anything not-linux, including several mp3 players and most windows audio afreedb.freedb.orgpplications (foobar2000 supported them, I think). It seems like this behaviour should be documented or at least warned about for new users, with an option to use the more cutting edge tag format or the more compatible format. 

Solutionwise, this post provides more background information: [http://ubuntuforums.org/showpost.php?p=1184248&postcount=16](http://ubuntuforums.org/showpost.php?p=1184248&postcount=16), and this problem seems to not be around with the "Grip" cd-ripping program, available in the add/remove applications menu. Is there any other way that uses Soundjuicer?

---

### Post by petermarkab on 2007-10-17
I'm looking at tagging too and came across a program called eyeD3 which can convert id3v2.4 tags to 2.3 (and all the others). It is command line though...

Just
```
sudo apt-get install eyed3
```
```
man eyeD3
```
should get you started.

Not automatic I know but hope it helps!

---

### Post by clubsoda on 2007-12-25
I've just had a similar problem and have posted a poll regarding UTF support in portable players.

[Please vote if you are interested](http://ubuntuforums.org/showthread.php?t=649734).

---

### Post by chiefmanyrabbitguteat on 2008-01-18
There is a freeware windows program that converts all of the tags in your library in one foul swoop to ID3v2.3 regardless of what they were.  It's called MP3tag, and it works splendidly under WINE.  Just import your collection, hit Save Tags, and off ya go!

It can be downloaded here:

[http://mp3tag.de/en/index.html](http://mp3tag.de/en/index.html)

Now if somebody could just write a script for Amarok that would convert any 2.4 tagged files to 2.3 as it transferred to a media device...

---

