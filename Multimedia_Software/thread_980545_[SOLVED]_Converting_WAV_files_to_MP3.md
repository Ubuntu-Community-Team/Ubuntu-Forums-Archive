---
title: "[SOLVED] Converting WAV files to MP3?"
date: 2008-11-12
forum: Multimedia Software
---

### Post by cybrsaylr on 2008-11-12
On Windows I used Nero.
What is the best app to use with Ubuntu to convert WAV to MP3?
I'm using both Hardy and Intrepid.

---

### Post by Tom_ZeCat on 2008-11-13
You could use Sound Converter by Lars Wirzenius.  If whatever you're playing the music on supports OGG files, you might consider converting to those instead of to MP3s.  OGGs can either create quality equal to MP3s while using less space or they can create better quality sound with the same amount of space.  Plus, Sound Converter by default supports OGGs, but not MP3s.  You can get it to support MP3s if you let it download and install an encoder.  

You can also convert to MP3 or OGG with Audacity.

---

### Post by cybrsaylr on 2008-11-13
I was just playing around with Audacity.
Got a 3 song clip off UTube using KeepVid then used Audacity to save the middle song I really wanted but that song was a WAV file. To save space I wanted to compress it to MP3 as always done in Windows. Will OGG play and be handled just as easily as MP3? I always used MP3s before.

I installed the MP3 'encoders' on Ubuntu so I can play MP3s with Rhythmbox, Movie player, etc on Ubuntu.

---

### Post by SuperSonic4 on 2008-11-13
OGG works well but is not as widespread as mp3 so you might have trouble putting it on a music player but since ogg need no non-free codecs they play out of the box on Linux (although not on windows when I had to install vlc before being able to play oggs)

If you install lame audacity should be able to export as mp3

```
sudo apt-get install lame toolame
```

---

### Post by sickgirl485 on 2008-11-13
I personally use Sound Converter. It's really easy; just load the songs you want to convert, change the settings, and hit the convert button. I have the encoder that allows the mp3 format, and it works like a charm. I prefer mp3s because they're widely used and almost every audio program plays them.

---

### Post by SuperSonic4 on 2008-11-13
> **sickgirl485 said:**
> I personally use Sound Converter. It's really easy; just load the songs you want to convert, change the settings, and hit the convert button. I have the encoder that allows the mp3 format, and it works like a charm. I prefer mp3s because they're widely used and almost every audio program plays them.

Doesn't soundconverter use lame as the mp3 backend? Unless it's installed automatically then it doesn't matter so much.

Personally I use soundkonverter but then I run Kubuntu and Mandriva so I'd agree with the soundconverter suggestion.

---

### Post by cybrsaylr on 2008-11-13
> **SuperSonic4 said:**
> If you install lame audacity should be able to export as mp3

```
sudo apt-get install lame toolame
```
I installed the above in terminal and it still won't convert to mp3.



[QUOTE=sickgirl485]I personally use Sound Converter. It's really easy; just load the songs you want to convert, change the settings, and hit the convert button. I have the encoder that allows the mp3 format, and it works like a charm. I prefer mp3s because they're widely used and almost every audio program plays them.[/QUOTE]
Just installed Sound Converter and the mp3 codec and it worked like a charm.
I also prefer mp3s because they're widely used and almost every audio program plays them.

Thanks sickgirl485.


If anyone else has any other useful suggestions feel free to post them.....

---

### Post by stinger30au on 2008-11-13
> **cybrsaylr said:**
> On Windows I used Nero.
What is the best app to use with Ubuntu to convert WAV to MP3?
I'm using both Hardy and Intrepid.

you can still use nero, install your copy of windows in to vitrual box and do it there too

---

### Post by Fir3chi3f on 2008-11-13
> **stinger30au said:**
> you can still use nero, install your copy of windows in to vitrual box and do it there too

Bah! I cannot allow the fight to be given up that easily to the devil OS!

[Try this link my friend, Linux will rule!]("http://ubuntuforums.org/showthread.php?t=323639")

---

### Post by alwayshere on 2008-11-13
soundKonverter is good find it in add/remove or put below in terminal

 
sudo apt-get install soundKonverter

then

sudo apt-get update

---

### Post by cybrsaylr on 2008-11-14
Thanks for all the help.

The easiest solution so far seems to be use KeepVid to download the mp4 file to HDD then use Sound Converter to convert mp4 to mp3 files. Have done it this way with a couple songs with no problems with very good results.

The more I use linux the better I like it.
If anyone has a better idea, feel free to post it.

---

