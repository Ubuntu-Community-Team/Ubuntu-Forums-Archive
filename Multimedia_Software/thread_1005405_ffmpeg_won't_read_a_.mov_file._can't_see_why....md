---
title: "ffmpeg won't read a .mov file. can't see why..."
date: 2008-12-08
forum: Multimedia Software
---

### Post by wetinwales on 2008-12-08
Hi All
Getting the error message:- " *Usually that means that input file is truncated and/or corrupted* "  when I try to convert a .mov file to an .mpg using ffmpeg in Terminal.

Using Hardy Heron. 
Medibuntu, Universe and Multiverse are installed - as is Mplayer, Xine, Mencoder. Kaffeine etc. - all from Synaptic. 

The ONLY application which will play the .mov video is Kaffeine...! Mplayer runs images with broken error messages - " *AVC: nal size 0* ".

The mov file in question .." [http://s3.amazonaws.com/movies.dpreview.com/CanonEOS5DMarkII/MVI_5500.MOV](http://s3.amazonaws.com/movies.dpreview.com/CanonEOS5DMarkII/MVI_5500.MOV) " (Canon 5DMKII video ) is downloaded and stored in my 'Videos' directory.
Permissions allowed to read write on the file.

Here is the command I used in terminal. (I started with '*ffmpeg -i input.mov output.mpg*' as a simple start, then used this suggested line as shown....

user@computer:~$ ffmpeg -i /home/user/Videos/5DMKII.mov -acodec mp2 -abitrate 128 -ac 2 -vcodec mpeg1video -qscale 3 -vbitrate 2048 -mbd 2 /home/user/Videos/5DMKII.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/home/user/Videos/5DMKII.mov: I/O error occured
Usually that means that input file is truncated and/or corrupted.
user@computer:~$

Both lines in terminal deliver exactly the same error in terminal.
 
Can anyone help here?

Thanks
Daf

---

### Post by FakeOutdoorsman on 2008-12-08
There is probably something wrong with the video file.  I've only seen this error in two instances: if the video file is corrupted or if the path to the file is wrong.  I would ask someone on the dpreview forums if they have trouble playing or converting this video and if they could get the md5sum of the file (Windows users can use the free [md5summer]("http://www.md5summer.org/")).

Perhaps the download didn't finish correctly.  You can use wget to continue to download the rest (you might want to make a copy of the file first before trying this):
```
cd ~/Videos
wget -c http://s3.amazonaws.com/movies.dpreview.com/CanonEOS5DMarkII/MVI_5500.MOV
```

---

### Post by wetinwales on 2008-12-09
Re downloaded two files from their site with wget.
Both files won't convert.

Will try their forum.

Thanks
Daf.

---

### Post by FakeOutdoorsman on 2008-12-09
Do you get the same error with some of the other 5D Mk.II videos?  I didn't have any trouble with [this example](http://s3.amazonaws.com/movies.dpreview.com/CanonEOS5DMarkII/Video1.MOV) [22.5 MB], but I'm using a recent self-compiled ffmpeg.

---

### Post by wetinwales on 2008-12-09
Just managed to convert both the Canon 5DMKII files with this syntax:-
ffmpeg -i input.mov -r 25 output.avi

can't fathom what I did different apart from the -r 25

Kaffeine and Mplayer now play at correct speed with no errors except that the picture is artefacted - rather like a .gif on a website showing poor graduation in tone changes.

Perhaps this is the players in Hardy ??

Thanks for your help and interest.

Daf

---

### Post by FakeOutdoorsman on 2008-12-09
> **wetinwales said:**
> ...
Kaffeine and Mplayer now play at correct speed with no errors except that the picture is artefacted - rather like a .gif on a website showing poor graduation in tone changes.

Default bitrate in ffmpeg is low and often results in low-quality videos.  What is the converted movie going to be played on?  I can try to come up with a ffmpeg command.

---

### Post by wetinwales on 2008-12-10
I found the bitrate variable in ffmpeg documentation and propose experriment.
Would welcome a clue....?
 
Want the highest possible image quality to apraise the canon 5DMKII camera in its video mode. (HD I believe) Playing in any Ubuntu compatible player - eg. Kaffeine - on a high res screen with Nvidia 5900 graphics card 8yrs old.

I converted the Canon .mov via ffmpeg to .avi to run the files on Premiere Pro7.....aghast!!....I know I know, but I've tried for four months to get Cinelerra and Open Movie Editor to play anything at all  properly. They just will not... in hardy or in Ibex.

All my .avi files work well in Pro7... except these two I converted in ffmpeg (Ubuntu Hardy)
The error message is:-

"*unsupported compression in this file*" when loading into Pro7.

So I must learn about different compression types for ffmpeg in order to play in Premiere Pro7 and Linux. 

Can you throw me any clues?

many thanks for your help.

Daf

---

### Post by wetinwales on 2008-12-10
Latest info.. in case anyone is reading..!

Getting much better quality by using:-

ffmpeg -i input.mov -r 25 -b 7500000 output.avi

Daf

---

