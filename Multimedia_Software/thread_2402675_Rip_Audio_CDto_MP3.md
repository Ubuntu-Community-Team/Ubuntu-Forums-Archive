---
title: "Rip Audio CDto MP3"
date: 2018-10-03
forum: Multimedia Software
---

### Post by oygle on 2018-10-03
I have a number of music CD's that I want to have the tracks as single MP3's on the hard drive. Have used VLC to rip from the CD, however it only does one file/track at a time. Some of the CD's have 15 tracks. Looking at [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping) and other articles, they mention Sound Juicer. So I installed that, but got a message ..

> Could not read the CD

Sound Juicer could not read the track listing on this CD.
Reason: Cannot access CD: The specified location is not mounted

If I use Dolphin, the CD is shown as "Audio CD", however if I navigate to that, nothing shows/displays. The files can't be displayed as normal fileset. Have read here and there that CD audio is usually just one big file.

Do I have to actually 'mount' the CD ? I'm able to play it okay with VLC and other multimedia tools. Here is what I have installed:

Sound Juicer
Brasero
K3b
VLC
Handbrake
mpv media player
Audacity
Dragon Player
Pulse Audio Volume Control

---

### Post by Autodave on 2018-10-03
Try XCFA. I have used it for years without a problem.

---

### Post by #&amp;thj^% on 2018-10-03
> **oygle said:**
> 

Do I have to actually 'mount' the CD ? I'm able to play it okay with VLC and other multimedia tools. Here is what I have installed:


Try mounting first with;
```
gvfs-mount cdda://sr0
```
while the CD is in the drive and sound-juicer not running, then try sound-juicer. This has been an ongoing problem for sound-juicer.
I have used abcde for a few years now, seems to be fine for my needs.
[https://abcde.einval.com/wiki/](https://abcde.einval.com/wiki/)

---

### Post by Dennis N on 2018-10-03
I have always used **grip** or **asunder** to rip CDs. 

grip is very customizable as to what it does, asunder is simpler to use. Both are in Ubuntu repositories. No need to mount the CD. Just put it in, and start the program and it will recognize it.

---

### Post by SeijiSensei on 2018-10-03
Install lame and flac.

```
sudo apt install lame flac
```

Now when you insert the CD in the drive, choose the "rip with K3b" option.  When you see the track list, choose the ones you want and hit "Start Ripping".  In the File Type drop-down, choose MP3 (or, better, FLAC if your players support it).

---

### Post by oygle on 2018-10-03
> **Autodave said:**
> Try XCFA. I have used it for years without a problem.

Thanks

> **1fallen said:**
> Try mounting first with;
```
gvfs-mount cdda://sr0
```
while the CD is in the drive and sound-juicer not running, then try sound-juicer. This has been an ongoing problem for sound-juicer.
I have used abcde for a few years now, seems to be fine for my needs.
[https://abcde.einval.com/wiki/](https://abcde.einval.com/wiki/)

Thanks. I did the **gvfs-mount** , but couldn't see any details after a **mount** command. Obviously a **gvfs-mount** is different. Anyway, then ran **sound juicer** and no error messages this time. Hit "extract' and it did all 11 tracks. As I had specified Artist, song title to Sound Juicer, it extracted all 11 OGG files under the Music path, and nicely structured paths under that with Artist, then song/track title.. Then used the following to convert to  mp3

```
ffmpeg -i 1\ -\ Track\ 1.ogg  -acodec libmp3lame audio.mp3
```

It sounds okay. Just wondering if there is anything additional I can do to ensure the sound quality is as good as the CD.

I did install **abcde** , but got stuck on which encoding to use for m3. Have PM'd the author of that to check.

> **Dennis N said:**
> I have always used **grip** or **asunder** to rip CDs. 

grip is very customizable as to what it does, asunder is simpler to use. Both are in Ubuntu repositories. No need to mount the CD. Just put it in, and start the program and it will recognize it.

Thanks. I had seen quite a few posts about **asunder,** but not heard of **grip**. I may try **asunder** and see what it is like to use.

> **SeijiSensei said:**
> Install lame and flac.

```
sudo apt install lame flac
```

Now when you insert the CD in the drive, choose the "rip with K3b" option.  When you see the track list, choose the ones you want and hit "Start Ripping".  In the File Type drop-down, choose MP3 (or, better, FLAC if your players support it).

Thanks. I do have **flac** installed for some reason, so could install **lame** and try that,as **k3b** is already installed. I didn't know that FLAC is better quality.

Have just done a test rip with **k3b**, taking the option *Rip Audio CD* and it ripped all 11 tracks to a path under downloads, all WAV files. They sound okay.

---

### Post by mc4man on 2018-10-03
> **oygle said:**
> 

I did install **abcde** , but got stuck on which encoding to use for m3. Have PM'd the author of that to check.

.
You need to set up a .conf file with desired parameters. See here
[http://www.andrews-corner.org/linux/abcde/index.html](http://www.andrews-corner.org/linux/abcde/index.html)

---

### Post by oygle on 2018-10-03
> **mc4man said:**
> You need to set up a .conf file with desired parameters. See here
[http://www.andrews-corner.org/linux/abcde/index.html](http://www.andrews-corner.org/linux/abcde/index.html)

Yes, that is where I got stuck. If I select [http://www.andrews-corner.org/linux/abcde/abcde_mp3.html](http://www.andrews-corner.org/linux/abcde/abcde_mp3.html) from the options , do I then just select option 1, which is *~/.abcde.conf for MP3: lame* ?

---

### Post by Yellow Pasque on 2018-10-04
^Yes. Read the description(s). The other mp3 encoder .conf's are there for historical purpose.

> Now when you insert the CD in the drive, choose the "rip with K3b" option. When you see the track list, choose the ones you want and hit "Start Ripping". In the File Type drop-down, choose MP3

Note: If you're going to use k3b for mp3, I think you still need the libk3b7-extracodecs package, even though mp3 patents have expired.

> but couldn't see any details after a mount command

You don't mount an audio CD. It doesn't have a filesystem like a data CD.

> As I had specified Artist, song title to Sound Juicer, it extracted all 11 OGG files under the Music path, and nicely structured paths under that with Artist, then song/track title.. Then used the following to convert to mp3

It does not make sense to rip to ogg and convert to mp3. You only lose sound quality that way. sound-juicer should be able to rip to mp3 directly, but to be honest, I haven't bothered with sound-juicer in years. It stopped being good when the devs ripped out important options.

> Just wondering if there is anything additional I can do to ensure the sound quality is as good as the CD.

Use FLAC if you have the disk space and you're paranoid about audio quality. Most people would struggle to hear any difference between a CD and a high bitrate mp3 though.

---

### Post by i7Fd-2sCB1 on 2018-10-04
Have you tried other Audio Rip software's on Ubuntu/Kubuntu? The one which I use is Asunder which does what I want but have you tried that software to rip audio?

---

### Post by Yellow Pasque on 2018-10-04
> **centralpython said:**
> Have you tried other Audio Rip software's on Ubuntu/Kubuntu? The one which I use is Asunder which does what I want but have you tried that software to rip audio?

Asunder was already suggested. I would suggest Audex as a GUI ripper for Kubuntu/KDE users since it's a Qt/KDE program.
I personally prefer abcde though. I feel the power surging through my fingers when typing 'abcde'!

---

### Post by ajgreeny on 2018-10-04
Another vote here for abcde; once you have chosen the right abcde.conf file for the output file-type you want it is almost a case of command **abcde** and nothing more may be needed.
If you need to you can output to many different file-types simultaneously, eg, flac, acc, mp3, ogg.

---

### Post by oygle on 2018-10-05
> **Temüjin said:**
> ^Yes. Read the description(s). The other mp3 encoder .conf's are there for historical purpose.

Okay, I will just use this one - [http://www.andrews-corner.org/linux/abcde/abcde_mp3.html#lame](http://www.andrews-corner.org/linux/abcde/abcde_mp3.html#lame)

> **Temüjin said:**
> Note: If you're going to use k3b for mp3, I think you still need the libk3b7-extracodecs package, even though mp3 patents have expired.

GUI's are easier, but I'm starting to like **abcde**

> **Temüjin said:**
> You don't mount an audio CD. It doesn't have a filesystem like a data CD.

Okay, I just wondered what the **gvfs-mount** was all about. I assume it was a Sound Juicer requirement.

> **Temüjin said:**
> It does not make sense to rip to ogg and convert to mp3. You only lose sound quality that way. sound-juicer should be able to rip to mp3 directly, but to be honest, I haven't bothered with sound-juicer in years. It stopped being good when the devs ripped out important options.

From memory, when I did get Sound Juicer to work, it ripped the 11 tracks as 11 seperate WAV files. The testing I did with **abcde** resulted in OGG files, but all I need is MP3, so they can be played on a mobile phone and a laptop.

> **Temüjin said:**
> Use FLAC if you have the disk space and you're paranoid about audio quality. Most people would struggle to hear any difference between a CD and a high bitrate mp3 though.

Well, I have hearing problems and very loud tinnitus in both ears, so I don't think I would notice the difference. I do notice echo and other poor quality though. Tried to use Audacity once to adjust that. Is it all worth the extra trouble ? Maybe !!

> **centralpython said:**
> Have you tried other Audio Rip software's on Ubuntu/Kubuntu? The one which I use is Asunder which does what I want but have you tried that software to rip audio?

No I haven't tried that one.

> **Temüjin said:**
> Asunder was already suggested. I would suggest Audex as a GUI ripper for Kubuntu/KDE users since it's a Qt/KDE program.
I personally prefer abcde though. I feel the power surging through my fingers when typing 'abcde'!

Yes I'm liking **abcde**. To rip the whole CD as one file it was just

```
abcde -1
```

and the output was an OGG file. Then I tried

```
abcde
```

and got 11 OGG files. I just have to try it, so that the ripped audio is MP3.

> **ajgreeny said:**
> Another vote here for abcde; once you have chosen the right abcde.conf file for the output file-type you want it is almost a case of command **abcde** and nothing more may be needed.
If you need to you can output to many different file-types simultaneously, eg, flac, acc, mp3, ogg.

Looks like **abcde** is very powerful. I need to keep up with my 'terminal' skills also. Thanks everyone for your replies.  :D

---

### Post by SeijiSensei on 2018-10-05
> **Temüjin said:**
> Note: If you're going to use k3b for mp3, I think you still need the libk3b7-extracodecs package, even though mp3 patents have expired.

I didn't.  I just installed lame on a system which had no MP3 decoding package.  When I restarted K3b, it offered the MP3 option.

---

