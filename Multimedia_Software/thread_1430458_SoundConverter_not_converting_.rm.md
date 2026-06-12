---
title: "SoundConverter not converting .rm"
date: 2010-03-15
forum: Multimedia Software
---

### Post by BlueGene1402 on 2010-03-15
[SIZE=3]I can *play* Real audio using various applications but not convert them.

I installed SoundConverter which works great for other formats into mp3 but does not seem to support Real media. It freezes up every time I try to add a .rm file. I've tried looking for plugins & stuff with no success. What do I need to do?

I'm a complete beginner, please help!
[/SIZE]

---

### Post by ron999 on 2010-03-15
Hi
ffmpeg should convert Real Audio files to mp3 using a command like this:-
```
ffmpeg -i inputfile.rm output.mp3
```
If that works OK then use a program such as WinFF.
From here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by BlueGene1402 on 2010-03-17
[FONT=Verdana][SIZE=2]Nope, the ffmpeg thingie didn't work.. Keeps saying "Error while opening file" for some reason whichever one I choose.

I do seem to have this ffmpeg installed & everything.. so it says! Any more suggestions anyone? Thank you for your time.
[/SIZE][/FONT]

---

### Post by andrew.46 on 2010-03-17
Hi Blue,

> **BlueGene1402 said:**
> Nope, the ffmpeg thingie didn't work.. Keeps saying "Error while opening file" for some reason whichever one I choose.

Could you post the full command and terminal output? 

Andrew

---

### Post by BlueGene1402 on 2010-03-20
[SIZE=3]In  between my last post & this one I installed soundKonverter, uninstalled & reinstalled SoundConverter (neither of which are yet supporting Real audio) which must have changed something because this *ffmpeg* command line now works for converting to & from wav, mp3, flv, etc (thanks for that ron999, it's come in handy!) but still not for .rm

[SIZE=2]bluegene@Orion:~/Documents$ ffmpeg -i 672.rm 672.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[rm @ 0x91af2c0]sub_packet_size is invalid
672.rm: Error while opening file[/SIZE]

I have no idea what any of that means.. Am I missing a package or plugin or something?
[/SIZE]

---

### Post by ron999 on 2010-03-20
Hi
Which media player will play that **672.rm** file?

---

### Post by BlueGene1402 on 2010-03-20
[SIZE=3]I can play all of my .rm files in MPlayer & GNOME MPlayer.[/SIZE]

---

### Post by ron999 on 2010-03-22
Hi
I don't know what's causing your problem.
But here's a workaround till you get it solved:-

If you can play the rm files in mplayer then you can use mplayer to convert the rm files to wav files.
Then use SoundConverter to convert the wav files to mp3.

This is a command to use:-
```
mplayer inputfile.rm -quiet -vo null -vc dummy -ao pcm:waveheader:file=output.wav
```

---

### Post by BlueGene1402 on 2010-03-23
[SIZE=3]Thanks, that worked. I'm still hoping to get this thing figured out but for now this is really good & will keep me going for some time. Much appreciated :)

Can this command line be modified to convert all Real files existing in a folder?
[/SIZE]

---

### Post by ron999 on 2010-03-23
Hi
Well I suppose somebody might write you a script something like:-
```
for i in *.rm
...
...
...
```

But I don't know how to do this without doing a lot of googling.
;)

---

### Post by BlueGene1402 on 2010-03-23
[SIZE=3]No problem.. I thought it was straightforward. I'm just happy it's converting at all lol

So yeah don't google it, this is fine & thank you for your time!
[/SIZE]

---

### Post by andrew.46 on 2010-03-23
Hi BlueGene1402,

It is a pity that FFmpeg has choked on these files but perhaps something like the following might serve your needs:

```

for f in *.rm
do 
mplayer "$f" -vo null -vc null -ao pcm:waveheader:fast:file="${f%.rm}.wav" && \
lame --preset standard "${f%.rm}.wav" "${f%.rm}.mp3" && \
rm "${f%.rm}.wav"
done

```

It is more than a little clumsy, but it will convert a directory full of .rm files to .wav, then to .mp3 and finally clean up the .wav files. Feel free to clean it up a little, or replace *--preset standard* with your own lame settings...

All the best,

Andrew

---

### Post by BlueGene1402 on 2010-03-26
[SIZE=3]This is so cool. It worked perfectly. And no wav leftovers lol!!

I wouldn't know how to 'clean it up' or replace any settings but I don't think I need to.. This is great for all those dozens & dozens of small sized files AND Ron's suggestion is so handy for other tasks so thanks everyone for all your help ):P

~ BlueGene
[/SIZE]

---

### Post by andrew.46 on 2010-03-26
Hi BlueGene,

> **BlueGene1402 said:**
> This is so cool. It worked perfectly. And no wav leftovers lol!!

Excellent news :). I might save this loop in my own small 'recipe book' for media conversion!

All the best,

Andrew

PS If you are happy with the result could you dig out the [Solved] tag?

---

### Post by BlueGene1402 on 2010-03-28
[FONT=Verdana][SIZE=3]At first I thought to leave it open in case anyone reading it might need to ask or add.. Been there, done that! But you guys offer multiple solutions & I hope that at least one works for anybody who might come across this.

So, SoundConverter itself still not working but YES happy with result cuz does the job :O)
[/SIZE][/FONT]

---

