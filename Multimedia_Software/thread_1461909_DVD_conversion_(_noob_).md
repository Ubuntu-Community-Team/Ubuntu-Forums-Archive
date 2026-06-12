---
title: "DVD conversion ( noob )"
date: 2010-04-24
forum: Multimedia Software
---

### Post by jenova_skill on 2010-04-24
I have a 4 Year old and there's been alot of issues with her scratching all her DVD's.... So I'd like to Rip them to Mpeg or avi files or something So We can store these DVD's away so she can't get to them. And still be able to watch her movie's on a media computer. 
Im a complete noob when it comes to this sorta thing so could someone please point me in the direction or explain how I can do this.

---

### Post by andrea000 on 2010-04-24
There is all kinds of software to rip movies do you want
to rip the dvd or backup the dvd on to another dvd?

---

### Post by carl4926 on 2010-04-24
Not all DVD players will play data files. You might be best doing a copy. k9copy works really quickly. Or DVD95

---

### Post by taurolyon on 2010-04-24
**K9Copy** - it has the tools to rip and compress your DVDs or convert them to MPEG4

You must realize that most (if not all) DVD's are encrypted and might have some additional anti-copy measures installed. You will need the libdvdcss2 package to at least decrypt the DVDs.

---

### Post by Alan James on 2010-04-25
I think Handbrake ([http://handbrake.fr/](http://handbrake.fr/)) is the best DVD ripper. I have used it professionally when clients want to re-edit some of their old DVDs and have very rarely had a problem with it ripping a good video.

---

### Post by tobemem on 2010-04-28
I suggest you a tool like the one I wrote, ANDREW ([http://tobemem.memebot.com]("http://tobemem.memebot.com/")): all its dependencies are in Ubuntu repositories.

If you intend to play your transcoded movies on "a media computer", you don't have to worry about formats, so, if your PC isn't too slow, consider to use Matroska container file, x264 video and Vorbis audio (or AC-3, if you have a surround sound system); instead, if you want to be able to play your files on cheap or old stand-alone DivX/MPEG-4 players, too, use COMPATIBILITY_MODE=cheap in the configuration file.

You can even batch encode all your DVDs, if you copy them on your HD first (using vobcopy) and run ANDREW in non-interactive mode.

---

### Post by la Cafe on 2010-04-28
And a lot of time is occupied with similar converting?

[The Bravery is best selling artist]("abcmuzic.com")

---

### Post by tobemem on 2010-04-28
Yes, quite a lot.

Besides the power of your hardware, the speed of the whole process depends mainly on the video codec (H.264/MPEG-4 AVC is slower than MPEG-4 ASP), the video encoding options, and the target bitrate and resolution: in general, the better quality you want, the more time you have to wait.

For example, with the default options on my Core 2 Duo 2.26GHz, ANDREW took 7m39s to create a 2m24s clip using H.264/MPEG-4 AVC video encoding, while 4m34s using MPEG-4 ASP, but, with the «worst» options, only 1m39s using MPEG-4 ASP.

---

