---
title: "[SOLVED] How to converter theora ogg video files to avi/mpeg/mp4 or any other video f"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by philidox on 2007-06-07
This has been the most frustrating task by far.  For something so simple I thought ubuntu would be able to do this easily.  I have been googling for days now and still no perfect solution.  To keep someone else from googling for days like I did, I am going to give you some of near victories in dealing with this "Mission Impossible".  Here are the list of programs I have attempted to use but failed one way or another.  Try to pick up where I have failed or introduce something new please!!! I have also included the links with them

VLC=Converts the video perfectly but NO AUDIO: [http://gentoo-wiki.com/HOWTO_Convert_Video](http://gentoo-wiki.com/HOWTO_Convert_Video)
ffmepg(command line)=converts audio but NO VIDEO(its just a blank screen): [http://gentoo-wiki.com/HOWTO_Convert_Video](http://gentoo-wiki.com/HOWTO_Convert_Video)
PiTiVi= All I have been able to do is import the video.  All the options to "save as" or export video are not selectable.  I look at its options and it seems to be a complete package but I cant get passed the basics. [http://www.pitivi.org/wiki/Main_Page](http://www.pitivi.org/wiki/Main_Page)
Kino= Just does not work
Cinelerra= CANT EVEN GET IT TO INSTALL, no read me file!!! wtf.  I got this download from softpedia.com


The closest I got was using VLC.  It would be nice if someone could post how to extract audio from a Theora Ogg video and paste it to another video file.  Half the battle is won with VLC I just need to learn how to get the audio on there and I'll have an effective way of convertering video.  By the way,  once I successfully converter theora ogg video files I'll make a online video tutorial so that this NEVER becomes a frustrating issue again.

---

### Post by Gwasanaethau on 2007-06-07
I used ffmpeg to encode several videos and they were all pretty good, though one or two did have some artefacts in the video after conversion. What command did you use?

> **philidox said:**
> &#8230;It would be nice if someone could post how to extract audio from a Theora Ogg video and paste it to another video file.  Half the battle is won with VLC I just need to learn how to get the audio on there and I'll have an effective way of convertering video&#8230;

I've just been thinking, do you have a video file with no sound and a separate audio file? If you you should be able to merge them with ffmpeg - now if only I can remember how to do it&#8230;

---

### Post by Gwasanaethau on 2007-06-07
OK, I think I've worked it out. Assuming you've managed to get the video into the format you want (without audio) using VLC…

Use:
```
ffmpeg -i "[INPUT VIDEO FILE].ogg" -vn "[AUDIO FILE].wav"
```
…replacing [INPUT VIDEO FILE] with name of the video you want to convert and [AUDIO FILE] with a suitable name for the audio. This will take the audio from your video.

Then use:
```
ffmpeg -i "[INPUT VIDEO FROM VLC]" -i "[AUDIO FILE].wav" "[OUTPUT VIDEO FILE]"
```
…this will combine the video that you gleaned from VLC and the audio you got from the first command. Of course you can play around with the quality and stuff, but as I'm neither a video nor audio editor I haven't got a clue what any of it means!:D

Hopefully that will get you some way on your journey…;)

---

### Post by philidox on 2007-06-08
This is the error i got when i tried to use ffmpeg to combine the video and audio file thru the command line.  ffmpeg worked great to extract the audio file from the orginal theora video file. I tried to combine the video file made with VLC with a .wav, .ogg. mp3 and i got the same error every time.  Does anyone know of another program perhaps with a GUI interface that will allow me to combine the video and audio files.

user@user-desktop:~/Desktop$ ffmpeg -i hellx1.mp4 -i hellx1.wav hellx2.mp4 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)

Seems that stream 0 comes from film source: 1001.00 (1001/1) -> 50.08 (601/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'hellx1.mp4':
  Duration: 00:06:18.1, start: 0.000000, bitrate: 1035 kb/s
  Stream #0.0(eng): Video: mpeg4, yuv420p, 800x592, 50.08 fps(r)
Input #1, wav, from 'hellx1.wav':
  Duration: 00:06:18.0, start: 0.000000, bitrate: 1411 kb/s
  Stream #1.0: Audio: pcm_s16le, 44100 Hz, stereo, 1411 kb/s
File 'hellx2.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'hellx2.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 800x592, q=2-31, 200 kb/s, 50.08 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Unsupported codec for output stream #0.1

---

### Post by crispy_420 on 2007-06-08
avidemux

Tried that yet?

---

### Post by Gwasanaethau on 2007-06-08
> **philidox said:**
> …Unsupported codec for output stream #0.1…

Yeah, I get that too. Hmm, it seems to be a problem with the output format being MP4 rather than the input audio format. It seems to work OK with MPG or AVI as an output though, so if those formats are OK you might want to give them a try. As for getting the output video into MP4, I'm afraid I can't help you there. Sorry. :(

---

### Post by philidox on 2007-06-09
I do not care about it being .mp4 I'll use .avi or .mpg  I just need to get it away from theora. What blew me away was that there was a FREE and easy to use converter for Windows(of all the os's).  Its called SUPER.  I cannot believe that is not in the ubuntu repos to download because the program is unbelievable.  How do I talk to the software ppl and get SUPER for ubuntu?

There is the url SUPER: [http://www.erightsoft.com/S6Kg1.html](http://www.erightsoft.com/S6Kg1.html)

---

### Post by Gwasanaethau on 2007-06-11
Hmm, I'm not sure that's possible unless the writers make a Linux version of it. Have you tried running it in Wine to see if it works there? (I haven't tried anything in Wine myself, so I haven't a clue if that's even possible). Again, I'm sorry I'm not much help to you!

---

### Post by philidox on 2007-06-13
Two steps ahead of you on that.  I tried to install it with wine and it was not a success.  I use wine extensively for playing my video games.  I would love nothing more then to see a linux version of super.  Man I just feel so small in this world of linux and free software!

---

### Post by yagood on 2007-06-20
Sorry for bumping this old thread, but I just needed to convert OGG to AVI and it worked perfectly with mencoder (it's in the repositories).

Like this:

```
mencoder input_file.ogg -ovc lavc -nosound -o output_file.avi
```

I didn't need sound in my file, but it should work just as good with no "-nosound" option.

For more info on the subject see mencoder documentation:

[http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html](http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html)

---

### Post by kelvin spratt on 2007-06-20
i use Cinelerra the Dapper version as it uses the correct codecs works a treat the feisty version if you can get it to work is no good its gone backwards, i wrote how i got Cinelerra to work correctly for me. 
[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)
[http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)
I think DEVEDE will do the job as well you can encode to DVD, or Divx MPEG4, if the files don't need editing if you go to their site you can download a patch for mencoder if you have trouble with the sound, there is a bug in the latest mencoder

---

### Post by philidox on 2007-06-28
FINALLY I GOT IT!!!

Ok this is how it goes, simply use mencoder to converter the ogg video to an avi format.  This is an example of how to do it

**mencoder input_video.ogg -o output_video.avi -ovc lavc -oac lavc**

No need for me to reinvent the wheel here is the link that explains it all:
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

thats right no need for vlc, pino, ffmpeg or any of that other stuff just get familiar with the command line and your good to converter videos into a format that everyone, mostly those slave to Windows, can use and see.  Enjoy and I'll make a youtube video with link in just a sec

---

### Post by yagood on 2007-06-28
Congratulations :)

---

### Post by reckless2k2 on 2007-06-29
i've got an istanbul ogg i created but can't seem to convert it to avi using ffmpeg or mencoder. i used this command in ffmpeg:

ffmpeg -i file.ogg file.avi

did not work.

i tried the following command with mencoder:

mencoder file.ogg -o file.avi -ovc lavc -oac lavc

did not work. is there a package i'm missing in order to code it correctly?

---

### Post by yagood on 2007-06-29
What do you mean by "didn't work"? Is there some error message or output AVI is unreadable?

---

### Post by reckless2k2 on 2007-06-29
sorry...i get an error reading the file in linux and in windows. so the file is unreadable.

edit: avi file created from mencoder was readable in kaffeine in linux but not readable in windows using windows media player.

still having issue playing the file in windows.

edit2: i was able to play the avi using k-lite codec pack in windows. it will not play in native WM11.

any ideas?

---

### Post by philidox on 2007-06-30
Are you trying to play the video or convert it?  Playing it is just a matter of codecs or the right media player.  VLC has NEVER let me down in either Windows or Linux, and when you said mencoder did not work you gotta say why because it does require command line use and if your not familiar with it I can point you to some websites that will help get you going.  Lastly do you have mencoder installed?  Use your Synaptic Package Manger or command line to install/verify you got it.

---

### Post by yagood on 2007-06-30
> **reckless2k2 said:**
> sorry...i get an error reading the file in linux and in windows. so the file is unreadable.

edit: avi file created from mencoder was readable in kaffeine in linux but not readable in windows using windows media player.

still having issue playing the file in windows.

edit2: i was able to play the avi using k-lite codec pack in windows. it will not play in native WM11.

any ideas?

Actually I had the same problem - I encoded a show-off video of my Compiz desktop \\:D/ and sent it to a friend of mine who wasn't then able to play it on Windows with only standard codecs. I didn't really try to find out what's causing that though. :-k

---

### Post by philidox on 2007-06-30
does your friend have vlc install on his comp. thats the quickest way to him playing your show-off videos

---

### Post by yagood on 2007-06-30
Yeah, I know, but it's not that important and moreover he's very reluctant to install any new software, he uses some random player and claims that it suits his needs so I don't want to force anything on him. I tried to use different codecs with mencoder, but that didn't work either. When I have some free time, I'll look into it and maybe post some sort of solution in this thread for future reference.

---

### Post by sk8dork on 2007-06-30
> **yagood said:**
> Sorry for bumping this old thread, but I just needed to convert OGG to AVI and it worked perfectly with mencoder (it's in the repositories).

Like this:

```
mencoder input_file.ogg -ovc lavc -nosound -o output_file.avi
```

I didn't need sound in my file, but it should work just as good with no "-nosound" option.

For more info on the subject see mencoder documentation:

[http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html](http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html)

this worked beautifully for me. i was trying to convert a .ogg from GTKRecordMyDesktop to .avi so i could edit it in cinelerra without crashing. 

edit: actually, cinelerra is not liking the avi... need to try something else. maybe convert to dv somehow.

---

### Post by reckless2k2 on 2007-06-30
after i installed the avi condec in windows, i was able to play the avi in WM11. my goal was not to add any additional packages of any kind because the work windows machines are on a domain with active directory and these users can not install software. the easy solution would be to install the ogg or avi codec in windows but i don't have that luxury. i wonder if i can successfully convert to wmv with ffmpeg or mencoder. i believe stock WM11 can play mpegs as well but i don't remember which ones. i keep testing conversion with not much luck as far as windows playback.

---

### Post by reckless2k2 on 2007-06-30
using ffmpeg with the command:

ffmpeg -i file.ogg file.mpg

give me error and syas can not write this. using the following

ffmepg -i file.ogg file.wmv

gives me a file but it won't play in linux or windows. 

using mencoder and the following:

mencoder file.ogg -o file.mpg -ovc lavc -oac lavc

or

 mencoder file.ogg -o file.wmv -ovc lavc -oac -lavc

both give me usable files in linux but require a codec in windows media player 11. even the wmv is not read correctly which should not need a codec. 

any ideas?

---

### Post by philidox on 2007-07-02
did you look at the hyper link I posted when I found how to do it because it explained it all.  For example in the command line when you typed lavc that was telling mencoder which codecs to use.  Look at the hyper link and see what other codecs you can use like xvid.  O btw death to windows stay with linux!

---

### Post by reckless2k2 on 2007-07-05
hahaha..i appreciate the "death of windows" chant but in my work environment they use windows. i'm not going to be able to shake that. i'm just trying to make the file readable in the standard WM10 or WM11 in windows as my company would have it. these are training videos and i don't have the luxury of installing additional codecs on each desktop that plans to use these videos ever.

---

### Post by tefflox on 2008-04-04
Thanks !

---

