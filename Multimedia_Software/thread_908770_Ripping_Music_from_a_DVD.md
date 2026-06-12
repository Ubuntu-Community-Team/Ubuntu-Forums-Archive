---
title: "Ripping Music from a DVD"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Seventh Reign on 2008-09-02
Is it possible to rip the music from an Audio/Video DVD?  Like Audioslave's Live in Cuba or Linkin Park's first Live DVD for example.

---

### Post by Avoozl on 2008-09-02
Legal issues aside, there's probably an easier way to do it, but you could always rip the dvd to video file(s) (I like acidrip) and then extract audio from the videos (I like avidemux)

---

### Post by Seventh Reign on 2008-09-02
I've used Acidrip alot .. I'll look into avidemux tomorrow.

---

### Post by wolfen69 on 2008-09-03
i hear dvd::rip does this very thing :)

---

### Post by mc4man on 2008-09-03
> i hear dvd::rip does this very thing

That it does

> if you just want to have a WAV file from your music DVD, e.g. to burn it on a traditional audio CD: select the correspondent audio track and select the Create WAV from selected audio track item in the Operate menu. If the audio track is PCM already, it will be passed through, otherwise a correspondent conversion resp. downmix will be applied. 
Alot of concert dvds will have a lpcm track, obviously that's the best to use if available

---

### Post by Seventh Reign on 2008-09-04
I found a program in Windows called iSofter DVDtoMP3.  It works beautifully except its not free.  It has a 5:01/song limit unless you buy it.  Any chance for a Linux Equiv before I shell out $30?

---

### Post by mc4man on 2008-09-04
If your going to buy a prog. then test this also, works very well (I have it)
[http://www.castudio.org/dvdaudioextractor/](http://www.castudio.org/dvdaudioextractor/)

---

### Post by mmcmonster on 2008-09-04
As per [this reply on /.]("http://slashdot.org/comments.pl?sid=193124&cid=15846642"), mplayer should be able to do this.

I just tried the following line, and it seems to work. (It rips the audio from the first track of the DVD and creates a .wav file.)

```
 mplayer -ao pcm:file=yourfilename.wav -vo null dvd://1
```

---

### Post by Seventh Reign on 2008-09-05
CAS worked brilliantly with no limitations during the 30 day trial TY!  

Not sure which one I'd get if I was gonna buy one tho.  Both "work" and are basically the same price.

I've printed the mplayer command out.  I'm going to try that on my other PC and see how it works.

---

### Post by mc4man on 2008-09-05
this is what I've found works well with mplayer  - basic com. for track by chapter
```
mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -ao pcm:fast:waveheader:file=[COLOR="Red"]foo1[/COLOR].wav dvd://[COLOR="Red"]1[/COLOR] -chapter [COLOR="Red"]1-1[/COLOR]
``` red are variables
Once you get a system going it goes by pretty fast
Better explanation here
[http://ubuntuforums.org/showthread.php?p=5454243#post5454243](http://ubuntuforums.org/showthread.php?p=5454243#post5454243)

did you try dvd::rip, it sounded pretty straight forward

Cas's dae does offer a lot of choices though for output, If you combine it with this there are alot of possibilities. (I make 5.1 and or stereo audio dvd's for use on the ht. - album/artist = title, tracks = chapters, up to IIRC 99 of each per dvd depending what you want and space ( up to 99x99 tracks per dvd (though you'd never approach that that number with any quality

[http://www.audio-dvd-creator.com/](http://www.audio-dvd-creator.com/)

---

### Post by Seventh Reign on 2008-09-06
Everything works except for one DVD.  As soon as I stick the disc in any PC DVD Drive my entire system slows almost to a halt.  Windows, Ubuntu, OpenGEU, Sabayon, Fedora, and OpenSUSE all slow down.

---

### Post by mmcmonster on 2008-09-09
Probably a damaged disc.

There are ways to clean discs cheaply, that you may want to search the forum for (I hear using toothpaste works well, but I never tried it personally).

Of course, attempting to clean the disc should be done as a last resort, prior to throwing it away.

---

### Post by Seventh Reign on 2008-09-09
Disc is brand new ... not a visible scratch on it.

---

### Post by mc4man on 2008-09-09
> Everything works except for one DVD.

Be interesting to know the title

---

### Post by Seventh Reign on 2008-09-09
Audioslave's Live In Cuba

---

