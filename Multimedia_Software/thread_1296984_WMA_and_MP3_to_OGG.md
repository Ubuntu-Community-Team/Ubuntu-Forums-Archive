---
title: "WMA and MP3 to OGG"
date: 2009-10-21
forum: Multimedia Software
---

### Post by andycastille on 2009-10-21
What program can I use to convert WMA and MP3 files to OGG files?

---

### Post by RichardLinx on 2009-10-21
I don't have any wma files that I can test immediately, but I have used SoundConverter to convert MP3 to Ogg Vorbis previously. It's available in Synaptic, or alternatively you can just type into a terminal:
```
sudo apt-get install soundconverter
```

---

### Post by Koosti on 2009-10-21
> **RichardLinx said:**
> I don't have any wma files that I can test immediately, but I have used SoundConverter to convert MP3 to Ogg Vorbis previously. It's available in Synaptic, or alternatively you can just type into a terminal:
```
sudo apt-get install soundconverter
```

It should work if I remember correctly. SoundConverter can convert anything that Gstreamer can read unless I'm totally off track, WMA playback with Gstreamer is available.

---

### Post by vinutux on 2009-10-21
> **RichardLinx said:**
> I don't have any wma files that I can test immediately, but I have used SoundConverter to convert MP3 to Ogg Vorbis previously. It's available in Synaptic, or alternatively you can just type into a terminal:
```
sudo apt-get install soundconverter
```

+1 for that....
and there is oggconvert too 

```
sudo apt-get install oggconvert
```

---

### Post by andycastille on 2009-10-22
Thanks for the help. I will tell you if they work.
:-({|=

---

### Post by msayed2004 on 2009-10-22
[Mobile Media Converter]("http://www.miksoft.net/mobileMediaConverter.htm") is the best.

---

### Post by andycastille on 2009-10-22
When I type them into Terminal, I get this error message: ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by msayed2004 on 2009-10-22
Close other applications related to program installations (Synaptic, Update Manager, Add/Remove programs.......etc.)

---

### Post by vinutux on 2009-10-22
Lock beacause of you are using any apt front-ends like update manager /add remoove/synaptic/Aptitude ec ...close all of them and try again................

---

