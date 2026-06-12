---
title: "No rip CD audio in Jaunty"
date: 2009-06-04
forum: Multimedia Software
---

### Post by elmohino on 2009-06-04
Hi all: 

I use Ubuntu 9.04.  

My problem: no rip CD audio. No SoundKonverter, no Sound-Juicer, no dBpowerAMP (with Wine), no ripperX (say "Error Code 31")

Only K3b rip audio CD, but not in MP3! (say "command fail: lame -h...")

Any idea?  

Thanks. Greetings.

---

### Post by infinitejones on 2009-06-04
> **elmohino said:**
> no Sound-Juicer

Have you tried ```
sudo apt-get install sound-juicer
```

> **elmohino said:**
> command fail: lame -h...
[URL="http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/118000424931"]
This post[/URL] seems to describe the same problem - is lame installed? Try entering ```
which lame
``` into a terminal - if there's no output (as in, it doesn't say anything), type ```
sudo apt-get install lame
```

---

### Post by elmohino on 2009-06-04
Hi, **infinitejones**.   

LAME it's already installed: 

```
user@user-desktop:~$ which lame 
 /usr/bin/lame  
user@user-desktop:~$ which ripperx  
/usr/bin/ripperx  
user@user-desktop:~$
```I was uninstall sound-juicer, because no rip...

Greetings.

---

### Post by khelben1979 on 2009-06-04
On [this page]("http://www.linuxlinks.com/Software/Multimedia/MP3/Tools/Rippers/index.shtml") you have some CD rippers. Personally I have used the console version of [Jack]("http://www.home.unix-ag.org/arne/jack/") with Debian a few years ago, no problems with using it.

---

### Post by elmohino on 2009-06-04
Thanks for the links, my friend, but i solved the problems:

In K3b: check both "swap byte order" and "write wave header" in LAME settings. Now rip perfectly.

In Sound-Juicer: select correct CD-ROM in 'Edit>Preferences>CD Unit', but... Sound-Juicer no rip in MP3! Only in FLAC, Ogg, MP2, WAV and .spx.

But I find other ripper called Grip. Run correctly and encode MP3 y Ogg Vorbis in command-line. And I can update Vorbis to last version (aoTuV).

Salute.

---

### Post by elmohino on 2009-06-05
Sound Juicer's problem solved: installing *gstreamer0.10-plugins-ugly-multiverse* package.  

Now Sound Juicer rip CD audio correctly in MP3.  

Salute.

---

