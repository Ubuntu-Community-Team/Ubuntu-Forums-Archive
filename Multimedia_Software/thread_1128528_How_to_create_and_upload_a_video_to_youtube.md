---
title: "How to create and upload a video to youtube?"
date: 2009-04-17
forum: Multimedia Software
---

### Post by BardSeed on 2009-04-17
I'm trying to make a video which is primarily audio but with a .Jpg image the whole way through. Sounds simple enough, but the audio file is .ogg and Kino won't accept that. I tried another editor, but it would close as soon as I tried to run it.
I've been looking all over these forums and I've google looking for an answer on how to upload to youtube from ubuntu, to no avail. I know somebody must have an answer, can you help me out or point me to a guide, please? I'm using ubuntu 8.04.

---

### Post by BardSeed on 2009-04-17
Shameless bump. Somebody must know.

---

### Post by cariboo on 2009-04-17
Go to System-->Administration-->Synaptic Package Manager and click the search button, don't use quick search, and in the text box type **slide show**

I found several applications to do what you need.

Jim

---

### Post by BardSeed on 2009-04-18
Thanks. I downloaded AVIdemux and it'll accept the .jpg fine. The problem is that it displays two error messages when I try to add any kind of audio; I've tried .mp3, .ogg and .m4a. I've edited my audio preferences to use ALSA, but it still won't work.

The error messages are:
1) Cannot open ~/Music/folder/file
2)Could not open file.

I'm going to bed now, but it would be nice if somebody could give me an answer by the time I wake up. :)

---

### Post by BardSeed on 2009-04-19
Anyone?

---

### Post by dale456654 on 2009-04-19
I have a useless suggestion of using Windows Movie Maker in Virtual box?

---

### Post by xc3RnbFO8P on 2009-04-19
Install **Ubuntu-restricted-exras**
Avidemux can not open m4a files, you can use Audacity to convert them.
You ca also install [medibuntu]("https://help.ubuntu.com/community/Medibuntu") if you haven't.

---

### Post by BardSeed on 2009-04-22
> **Ringi said:**
> Install **Ubuntu-restricted-exras**
Avidemux can not open m4a files, you can use Audacity to convert them.
You ca also install [medibuntu]("https://help.ubuntu.com/community/Medibuntu") if you haven't.

I installed the restricted extras and I used audacity to convert my .ogg file into .mp3 but avidemux still won't accept it.

---

### Post by babyjoker on 2009-04-22
i want to make a video on youtube but when i try my webcam doesnt show up. i tried everything but it doesnt work i even got another webcam n it doesnt show up on youtube to record...can u please help me thanks

---

### Post by B4RR13N705 on 2009-06-07
I did that with OpenMovieEditor

---

### Post by Tuvok41 on 2009-08-13
Did anyone successfully, split an .avi file into clips of less than 10 mins?
I am having problems to split the file, any help would be appreciated, thnx.

---

### Post by FakeOutdoorsman on 2009-08-13
> **Tuvok41 said:**
> Did anyone successfully, split an .avi file into clips of less than 10 mins?
I am having problems to split the file, any help would be appreciated, thnx.

FFmpeg can split video without re-encoding.  Here's a description of the command:
[http://ubuntuforums.org/showpost.php?p=7769578&postcount=4](http://ubuntuforums.org/showpost.php?p=7769578&postcount=4)

---

### Post by andrew.46 on 2009-08-13
Hi Tuvok41,

> **Tuvok41 said:**
> Did anyone successfully, split an .avi file into clips of less than 10 mins?
I am having problems to split the file, any help would be appreciated, thnx.

An alternative to the excellent solution that the Fakeoutdoorsman has suggested is to use avisplit which is part of the transcode package. For example the following splits off the first 10 minutes of episode 1, season 4 of battlestar galactica and names it *S04E01_Battlestar_Galactica.avi-0000*:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]avisplit -i S04E01_Battlestar_Galactica.avi -t 00:00:00-00:10:00[/COLOR]**
[avilib] V: 23.976 fps, codec=XVID, frames=61816, width=624, height=352
[avilib] A: 48000 Hz, format=0x55, bits=0, channels=2, bitrate=126 kbps,
[avilib]    107423 chunks, 40654080 bytes, VBR
[framecode.c] Range: 0:00:00.0 (0) - 0:09:59.23 (14385)

Processing 14385 frames    0 to 14385.
First Setting start frame to: 0
[S04E01_Battlestar_Galactica.avi-0000] (000000-014393)

Setting end frame to: 14393 | cnt(14394)

```

You can use multiple splits, split by size and a few other tricks. One of the more useful splits is quoted in the man pages:

```
avisplit -s 700 -i my_file.avi
```

which splits a big avi file into multiple 700meg chunks thus suitable for burning to cd. Lots of possibilities :-). I should probably mention that a good look at the man pages is a good idea as the command options have changed a lot between versions. The above examples are for:

```

andrew@skamandros~$ transcode --version
transcode v1.1.3 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team

```

So I suspect for your purposes you are after a command like:

```

avisplit -i myfile.avi -t 00:00:00-00:10:00,00:10:00-00:20:00,00:20:00-00:30:00

```

It looks a little ugly but it should work well.

All the best,

Andrew

---

### Post by Tuvok41 on 2009-08-14
> **andrew.46 said:**
> Hi Tuvok41,



An alternative to the excellent solution that the Fakeoutdoorsman has suggested is to use avisplit which is part of the transcode package. For example the following splits off the first 10 minutes of episode 1, season 4 of battlestar galactica and names it *S04E01_Battlestar_Galactica.avi-0000*:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]avisplit -i S04E01_Battlestar_Galactica.avi -t 00:00:00-00:10:00[/COLOR]**
[avilib] V: 23.976 fps, codec=XVID, frames=61816, width=624, height=352
[avilib] A: 48000 Hz, format=0x55, bits=0, channels=2, bitrate=126 kbps,
[avilib]    107423 chunks, 40654080 bytes, VBR
[framecode.c] Range: 0:00:00.0 (0) - 0:09:59.23 (14385)

Processing 14385 frames    0 to 14385.
First Setting start frame to: 0
[S04E01_Battlestar_Galactica.avi-0000] (000000-014393)

Setting end frame to: 14393 | cnt(14394)

```

You can use multiple splits, split by size and a few other tricks. One of the more useful splits is quoted in the man pages:

```
avisplit -s 700 -i my_file.avi
```

which splits a big avi file into multiple 700meg chunks thus suitable for burning to cd. Lots of possibilities :-). I should probably mention that a good look at the man pages is a good idea as the command options have changed a lot between versions. The above examples are for:

```

andrew@skamandros~$ transcode --version
transcode v1.1.3 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team

```

So I suspect for your purposes you are after a command like:

```

avisplit -i myfile.avi -t 00:00:00-00:10:00,00:10:00-00:20:00,00:20:00-00:30:00

```

It looks a little ugly but it should work well.

All the best,

Andrew

Thanks Andrew you are a Genuis lol. That work like a charm and it is pretty quick even; took about 10 secs at most(only a 23 min clip), just fantastic. If you were beside me I'd kiss you lol j/k.
Does this work for any type of video format? or only for avi files?


[quote=FakeOutdoorsman]
FFmpeg can split video without re-encoding. Here's a description of the command:
[http://ubuntuforums.org/showpost.php...78&postcount=4](http://ubuntuforums.org/showpost.php...78&postcount=4)
[/quote]
Thank you very much for the help
I did try ffmpeg but for some reason although I did have a different name for the output file it was trying to overwrite my original file!


The command I entered in terminal :
```

ffmpeg -t 00:08:00:00 The.xxxxx.xxxxx.avi -acodec copy -vcodec copy /temp/The.xxxxx.xxxxx.Part.1of3.avi

```

The result of the command :
```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:16:26, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
File 'The.xxxxx.xxxxx.avi' already exists. Overwrite ? [y/N] N

```

Maybe you could help me understand what is wrong here? I wouldn't mind having another way to split files especially if avisplit only works for avi file.

---

### Post by andrew.46 on 2009-08-14
Hi Tuvok,

> **Tuvok41 said:**
> Thanks Andrew you are a Genuis lol. That work like a charm and it is pretty quick even; took about 10 secs at most(only a 23 min clip), just fantastic. If you were beside me I'd kiss you lol j/k.
Does this work for any type of video format? or only for avi files?

Unfortunately as far as I know avisplit only works with avi files. And thanks for the kiss :-).

You may be interested to know that I have started writing a guide for transcode and the so-called *transcode-utils* that will come out when karmic arrives. Karmic packages avisplit in the transcode-utils package and includes:

[LIST]
[*]avifix   : Fix header of AVI-file.
[*]aviindex : Write and read text files describing the index of an AVI file.
[*]avimerge : Merge several AVI-files into one.
[*]avisplit : Split AVI-files into chunks of a maximum size.
[*]avisync  : Adjust audio synchronisation
[*]
[/LIST]

and I will be covering these as well. Fascinating stuff when you start digging into them!

Andrew

---

### Post by FakeOutdoorsman on 2009-08-14
> **andrew.46 said:**
> Hi Tuvok,

Unfortunately as far as I know avisplit only works with avi files. And thanks for the kiss :-).

You may be interested to know that I have started writing a guide for transcode and the so-called *transcode-utils* that will come out when karmic arrives. Karmic packages avisplit in the transcode-utils package and includes:

[LIST]
[*]avifix   : Fix header of AVI-file.
[*]aviindex : Write and read text files describing the index of an AVI file.
[*]avimerge : Merge several AVI-files into one.
[*]avisplit : Split AVI-files into chunks of a maximum size.
[*]avisync  : Adjust audio synchronisation
[*]
[/LIST]

and I will be covering these as well. Fascinating stuff when you start digging into them!

Andrew

Looking forward to this guide.  I may have been able to use *avifix* on that blasted broken huffyuv AVI!

---

### Post by Tuvok41 on 2009-08-14
> **andrew.46 said:**
> Hi Tuvok,



Unfortunately as far as I know avisplit only works with avi files. And thanks for the kiss :-).

You may be interested to know that I have started writing a guide for transcode and the so-called *transcode-utils* that will come out when karmic arrives. Karmic packages avisplit in the transcode-utils package and includes:

[LIST]
[*]avifix   : Fix header of AVI-file.
[*]aviindex : Write and read text files describing the index of an AVI file.
[*]avimerge : Merge several AVI-files into one.
[*]avisplit : Split AVI-files into chunks of a maximum size.
[*]avisync  : Adjust audio synchronisation
[*]
[/LIST]

and I will be covering these as well. Fascinating stuff when you start digging into them!

Andrew

Same here Andrew, looking forward to your guide, do not hesitate to pm me about it when it is up.

---

