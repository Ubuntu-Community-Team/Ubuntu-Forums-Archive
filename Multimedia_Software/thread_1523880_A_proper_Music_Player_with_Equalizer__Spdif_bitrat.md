---
title: "A proper Music Player with Equalizer ? Spdif bitrate ?"
date: 2010-07-04
forum: Multimedia Software
---

### Post by TruebaseB on 2010-07-04
Hello.

Since a year now i'm Windows user again because linux (Ubuntu) was sucky on a few things,and mostly on this thread's question.

Well,does anybody know any proper Music Player for Mp3,Wav,Flac that has Sound Equalizer like WMP and sounds as good as Winamp/Foobar on Windows?

I was using a Winamp clone,i think XMMS2 or something,but it was really buggy and the sound was getting distorted when i was tweaking the Equalizer,and really,i don't want to listen to music with this again.

And since i'm using a proper A/V Receiver with a proper Home Theater setup instead of multimedia speakers,i need to have full control of the SPDIF's Bitrate but i cannot find anywhere such settings.

Any idea would be appreciated!

---

### Post by Linuxforall on 2010-07-05
Banshee has eq which works well, also vlc, there are ways to set system wide equalizer via Pulse.

---

### Post by cchhrriiss121212 on 2010-07-05
You should find bitrate control in alsamixer from the terminal. If you are using a decent receiver I would not recommend using any kind of software EQ.
> 
Well,does anybody know any proper Music Player for Mp3,Wav,Flac that has Sound Equalizer like WMP and sounds as good as Winamp/Foobar on Windows?
I would recommend Quod Libet.

What sound card do you use BTW, onboard?

---

### Post by TruebaseB on 2010-07-05
Thanks for the suggestions guys,i appreciate the help. :)

I'm using the onboard (ALC888 ) with the DAC of my amplifier.

The problem is that the amplifier has an equalizer but not a full band one,it can control the frequency from -12 to +12 on 100hz and 1khz.

I found a semi-vintage equalizer at decent price but i didn't bought it because it wasn't digital,so it could do job only with stereo and analog connection. :o

---

### Post by xzero1 on 2010-07-06
I could be wrong, but I don't think you can equalize a spdif formatted signal without first converting it. One of the most configurable players for linux is Sox*. Although it is a command line program you can define a chain of filters to apply to your signal. Note that for mp3 support it must be recompiled with the proper libraries.

* [http://sox.sourceforge.net/](http://sox.sourceforge.net/)

---

### Post by jocko on 2010-07-06
> **TruebaseB said:**
> I was using a Winamp clone,i think XMMS2 or something,but it was really buggy and the sound was getting distorted when i was tweaking the Equalizer,and really,i don't want to listen to music with this again.
Well, xmms was outdated and abandoned years ago.  If you want a similar, but modern and still maintained player, try audacious. It's in the repos.
You can set bitrates in the preferences (16, 24, 32 or floating point), and it has an equalizer that works well.
It's my favourite music player, and I like it even more now that they are making an alternative gui (gtkui) as well as the old winamp 2 skinnable interface (but unfortunately the gtkui is still lacking a few important pieces, unless you build it yourself from a very recent development snapshot).

---

### Post by TruebaseB on 2010-07-07
Thanks for everything,i'm going to check those!

It is possible to equalize a sound that's traveling into digital signal... The work is getting done by tweaking the level of the frequency amplification before the player output the signal. :)

I have used Audacious once,it was a really good player but i didn't knew it had such features.

---

### Post by xzero1 on 2010-07-08
> **TruebaseB said:**
> 

It is possible to equalize a sound that's traveling into digital signal... 

That is not the question.

---

### Post by jocko on 2010-07-08
> **xzero1 said:**
> That is not the question.
?

---

### Post by TruebaseB on 2010-07-09
^^
I have the same question. :biggrin:

---

