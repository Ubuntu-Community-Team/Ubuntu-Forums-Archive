---
title: "[SOLVED] How to convert mp3 to wma."
date: 2008-06-09
forum: Multimedia Software
---

### Post by thefirstone on 2008-06-09
I was able to convert mp3 files to wma.
First you need to have Wine([http://www.winehq.org/](http://www.winehq.org/)) installed which lets you install and run a host of windows application in Ubuntu. I'm using Ubuntu 804.
Use Wine to install and run JetAudio.Plus v7.1.0.3100.([http://www.cowonamerica.com/products/jetaudio/](http://www.cowonamerica.com/products/jetaudio/))Maybe another version of Jet Audio will also work(I don't know).
Once in Jet Audio open the playlist and go to 'add files\add files in folder' and load the folder with the mp3 files you want to convert.
Once you have all the files in the playlist you 'select all'(Ctrl+a)\right click on the files and select 'Export', type in a file name and save. Close the playlist window. Now open the Convert Audio in Jet Audio and Import the .pls file you created of the files you want to convert. Note that this was the only way I found to import many files at once into the convert audio window. For 'Output format' chose WMA Windows Media Audio 7 (9 didn't work for me), configure your bitrate and your good to go.
Have fun.

---

### Post by roccivic on 2008-06-20
Why would anyone even want to convert OGG/MP3 to WMA????
It's like swapping gold for lead...

Rouslan

---

### Post by thefirstone on 2008-06-21
Wma at 64 kbps is acceptable quality for most portable players and it takes up half the space. If you convert an mp3 at 128 kbps to wma at 64 kbps and listen to both files you will not notice any significant change in quality (if any). If your portable player has limited capacity this is the best way to maximize the amount of files you can carry. For general storage of all my music files I use mp3 128 kbps or higher but for my portable players I use wma 64 kbps in order to carry the most files possible. My cell phone holds 2gb max. By converting mp3's to wma's I have doubled the the amount of music I can carry around in it.

---

### Post by cozmicharlie on 2008-06-21
> **thefirstone said:**
> Wma at 64 kbps is acceptable quality for most portable players and it takes up half the space. If you convert an mp3 at 128 kbps to wma at 64 kbps and listen to both files you will not notice any significant change in quality (if any). If your portable player has limited capacity this is the best way to maximize the amount of files you can carry. For general storage of all my music files I use mp3 128 kbps or higher but for my portable players I use wma 64 kbps in order to carry the most files possible. My cell phone holds 2gb max. By converting mp3's to wma's I have doubled the the amount of music I can carry around in it.

Interesting way to go about it but if it works for you then great.  FYI - alternatively, you can convert to wma in Linux (without using wine) with pacpl ([http://pacpl.sourceforge.net/](http://pacpl.sourceforge.net/)).

---

### Post by jverga on 2008-06-21
or you could do it the easy way and use soundKonverter.....

---

### Post by gandaran on 2008-06-22
and ffmpeg/winff too!

---

### Post by M4rotku on 2008-06-25
Hello all,

I need to convert mp3's to wma's to save space on my Sansa player.

I have downloaded Sound Konverter, but I can't make heads nor tails of it.

Can anyone give me watered down instructions on converting from mp3 to wma?  I don't even care which application it will take.

---

### Post by prabath_fun on 2008-06-25
Nice thread. Usefull. I have 256MB Creative player. Now I can able to save more songs.
Thanks,

---

### Post by cozmicharlie on 2008-06-26
> **M4rotku said:**
> Hello all,

I need to convert mp3's to wma's to save space on my Sansa player.

I have downloaded Sound Konverter, but I can't make heads nor tails of it.

Can anyone give me watered down instructions on converting from mp3 to wma?  I don't even care which application it will take.

Give us more info:
What OS are you using (Hardy, Gutsy ??).
What codecs have you installed (gstreamer, Ubuntu restricted extras, ???)?  In general - you don't have to list them all.

Once you provide that info, we can walk you through the process.  It is really fairly simple (once someone shows you how of course).

In general if for example we want to convert music.wma to music.mp3 - the basic commands are:
[LIST=1]
[*]Open SoundKonverter
[*]There are tabs right under the menu that say "Simple" and "Detailed" (start with the Simple).
[*]In the "Simple" dialog box you set the output format - mp3 in this example.
[*]The next line in the dialog box (Source Directory) you set the output location (where you want your converted files to be saved).  You will see an empty dialog space with a folder icon next to it.  Click on the folder and set your output directory.
[*]Next, add (see the add button on the bottom left)or just drag and drop the music files you want to convert (your music.wma file for example) to the main part of SoundKonverter (where it says 'File List").  
[*]Then hit start and wait.
[/LIST]

For it to work though you need all the codecs installed first.

---

### Post by chuyler1 on 2008-06-26
I've been trying to do the same thing.  It appears that ffmpeg is supposed to handle encoding wma but it doesn't actually do it, instead it uses the mp2 codec.

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  **Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839
```

If you try to force the wma codec, it still uses mp2.

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma **-acodec wmav2**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  **Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839%
```

I need true wma format for my cell phone to play the files.  Looks like I may have to revert to using windows for this task unless someone can chime in with some tips.

---

### Post by gandaran on 2008-06-26
> **chuyler1 said:**
> I've been trying to do the same thing.  It appears that ffmpeg is supposed to handle encoding wma but it doesn't actually do it, instead it uses the mp2 codec.

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839
```

If you try to force the wma codec, it says it isn't found:

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma -acodec wma
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Unknown codec 'wma'
```

I need true wma format for my cell phone to play the files.  Looks like I may have to revert to using windows for this task unless someone can chime in with some tips.

it does handle wma, but you have to install ffmpeg from the medibuntu repository, ffmpeg from the normal synaptic repository's is a bit short on codecs, winff is a nice frontend for ffmpeg [http://www.winff.org/](http://www.winff.org/)

---

### Post by flytripper on 2008-06-26
roccivic .... /signed

---

### Post by teaumaz on 2008-06-26
I can understand why you would want to rip your cds into wma. However, converting existing mp3s (which by nature already are lossy) into another lossy format (wma) does not make sense to me at all. You're then better off putting less music on your media player.

---

### Post by cozmicharlie on 2008-06-26
> **chuyler1 said:**
> I've been trying to do the same thing.  It appears that ffmpeg is supposed to handle encoding wma but it doesn't actually do it, instead it uses the mp2 codec.

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  **Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839
```

If you try to force the wma codec, it still uses mp2.

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma **-acodec wmav2**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  **Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839%
```

I need true wma format for my cell phone to play the files.  Looks like I may have to revert to using windows for this task unless someone can chime in with some tips.


You should be able to convert to wma.  After you do the conversion, what file type is listed in Properties?  I assume you tried to play these and they don't play - is that correct?  What ffmpeg are you using (the one from medibuntu or ??)?

---

### Post by chuyler1 on 2008-06-26
I installed ffmpeg using 'apt-get install ffmpeg'.  Is that correct or should I get it from somewhere else.

When I right-click a converted file and choose properties, under the basic tab it says **"MIME type: audio/x-ms-wma"** which is the same as the WMAs I have on my phone that were put there by WindowsMediaPlayer prior to my Linux install.  However, when I click the audio tab it says **"Codec: MPEG 1 Audio, Layer 2"** while my real WMAs say **"WMA Version 8"**.

As a quick test, I tried converting a real WMA to MP3 using ffmpeg and that worked perfectly fine.  It just won't convert MP3 to WMA properly.

As for teaumaz's comment, my phone will only play WMAs thanks to Verizon locking out the MP3 feature (some deal they made with Micro$oft I guess).  The phone support MP3 but to get to the feature you have to jump through 2 hidden menus and then once you start playing you can't close the phone.  So that's why I'm looking for a way to convert them to WMAs.  The WMAs will just go on the phone and I intend to keep the original mp3 files on my computer.  The quality on the phone is **** to begin with and I just want some tunes during my morning jog w/o forking out $200 for an iPod.

---

### Post by gandaran on 2008-06-26
> **chuyler1 said:**
> I installed ffmpeg using 'apt-get install ffmpeg'.  Is that correct or should I get it from somewhere else.

When I right-click a converted file and choose properties, under the basic tab it says **"MIME type: audio/x-ms-wma"** which is the same as the WMAs I have on my phone that were put there by WindowsMediaPlayer prior to my Linux install.  However, when I click the audio tab it says **"Codec: MPEG 1 Audio, Layer 2"** while my real WMAs say **"WMA Version 8"**.

As a quick test, I tried converting a real WMA to MP3 using ffmpeg and that worked perfectly fine.  It just won't convert MP3 to WMA properly.

As for teaumaz's comment, my phone will only play WMAs thanks to Verizon locking out the MP3 feature (some deal they made with Micro$oft I guess).  The phone support MP3 but to get to the feature you have to jump through 2 hidden menus and then once you start playing you can't close the phone.  So that's why I'm looking for a way to convert them to WMAs.  The WMAs will just go on the phone and I intend to keep the original mp3 files on my computer.  The quality on the phone is **** to begin with and I just want some tunes during my morning jog w/o forking out $200 for an iPod.

don't install ffmpeg using the command apt-get install ffmpeg, remove this ffmpeg, then in synaptic navigate to the medibuntu repository and install ffmpeg there.
if you haven't added medibuntu to synaptic run these commands on the terminal

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by chuyler1 on 2008-06-26
Thanks for the detailed instructions.  However, this version of ffmpeg still does the same thing:

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma -acodec wmav2 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  **Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839%
```

---

### Post by chuyler1 on 2008-06-26
Thanks for the detailed instructions.  However, this version of ffmpeg still does the same thing, or perhaps I did something wrong.

```
$ ffmpeg -i 02_-_Shoot_to_Thrill.mp3 02_-_Shoot_to_Thrill.wma -acodec wmav2 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  **Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead -99.983839%
```

---

### Post by cozmicharlie on 2008-06-26
I tried it on my version of ffmpeg also (I have a compiled version so it is the most recent) and I got the same results as chuyler1.  Digging in the ffmpeg site it does not look like this is possible (mp3 to wma).  I tried playing my converted wma file in Windows Media Player and it will not play.  It gives a message that it could be a tagging issue and wants you to download some program to remove the tag headers.  You may be stuck with Windows on this one.  If you really want to use Linux you can install foobar in Wine and do the conversion.  Or, maybe there is a Rockbox alternative for your phone.  Aren't proprietary codecs fun!

---

### Post by gandaran on 2008-06-26
> **cozmicharlie said:**
> I tried it on my version of ffmpeg also (I have a compiled version so it is the most recent) and I got the same results as chuyler1.  Digging in the ffmpeg site it does not look like this is possible (mp3 to wma).  I tried playing my converted wma file in Windows Media Player and it will not play.  It gives a message that it could be a tagging issue and wants you to download some program to remove the tag headers.  You may be stuck with Windows on this one.  If you really want to use Linux you can install foobar in Wine and do the conversion.  Or, maybe there is a Rockbox alternative for your phone.  Aren't proprietary codecs fun!

well, I have just converted a mp3 file to wma for testing, using winff (ffmpeg frontend) then I booted into windows xp, and guess what, the wma file plays just fine in windows media player! so whats the problem?

---

### Post by cozmicharlie on 2008-06-26
> **gandaran said:**
> well, I have just converted a mp3 file to wma for testing, using winff (ffmpeg frontend) then I booted into windows xp, and guess what, the wma file plays just fine in windows media player! so whats the problem?

That is what we are trying to figure out - for whatever reason chuyler1 and I both get the same results using ffmpeg and ours don't play.
It is obviously possible since yours plays fine so something must be different in your set up.
What version of ffmpeg are you using gandaran?
When you go to properties>audio what does it list for codecs?

---

### Post by gandaran on 2008-06-26
> **cozmicharlie said:**
> That is what we are trying to figure out - for whatever reason chuyler1 and I both get the same results using ffmpeg and ours don't play.
It is obviously possible since yours plays fine so something must be different in your set up.
What version of ffmpeg are you using gandaran?
When you go to properties>audio what does it list for codecs?

Version:ffmpeg 3:0.cvs20070307-5ubuntu7+medibuntu1
File properties » codec WMA Version 8 /stereo/44100 hz
windows media audio - audio/x-ms-wma

---

### Post by cozmicharlie on 2008-06-26
In winff what setting are you using for the "convert to" after you add your mp3 file?  I don't see an option for wma.

---

### Post by chuyler1 on 2008-06-27
Ok, I figured it out guys.  I had the order of the command switches incorrect.  I installed winff to see if that would work and it in fact did work.  I snooped the command using 'ps -eflw' and saw how it was executing ffmpeg.  Here's how to do it:

```
$ **ffmpeg -i 02_-_Shoot_to_Thrill.mp3 -acodec wmav2 02_-_Shoot_to_Thrill.wma**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2522kB global headers:0kB muxing overhead -99.982810%
```

So basically the -acodec wmav2 goes BEFORE the output file, not after.

Now I've got to see if I can get pacpl to execute the right command so I can do things directly from Amarock!

---

### Post by BeBoBli on 2008-06-27
> **thefirstone said:**
> If you convert an mp3 at 128 kbps to wma at 64 kbps and listen to both files you will not notice any significant change in quality (if any).

I'm not sure I can swallow that easy as my personal experience has said otherwise. Is there any proof of this?

Not only that, but I imagine there are better ways of dealing with this. Converting to OGG would be the best option since it's around 1/3 the size of MP3 that I notice little difference still at that point. Sometimes portable players don't support OGG. In such cases I would actually recommend just halving the kbps in the MP3 long before recommending WMA if any reason due to increased loss.

---

### Post by cozmicharlie on 2008-06-27
> **chuyler1 said:**
> Ok, I figured it out guys.  I had the order of the command switches incorrect.  I installed winff to see if that would work and it in fact did work.  I snooped the command using 'ps -eflw' and saw how it was executing ffmpeg.  Here's how to do it:

```
$ **ffmpeg -i 02_-_Shoot_to_Thrill.mp3 -acodec wmav2 02_-_Shoot_to_Thrill.wma**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2522kB global headers:0kB muxing overhead -99.982810%
```

So basically the -acodec wmav2 goes BEFORE the output file, not after.

Now I've got to see if I can get pacpl to execute the right command so I can do things directly from Amarock!

I will forward this to the pacpl developer and see what he can do to make this work in pacpl.  I will post back with his response.

---

### Post by chuyler1 on 2008-06-27
I experimented this morning with Amarok and transKode and it handles the -acodec wmav2 appropriately, I should have never bothered with pacpl.  I was able to configure my cell phone memory card as a device and automate transferring and encoding to wma.  

...only issue is that there is a noticeable reduction in quality in certain types of music (combination of encoding, bitrate, cellphone DAC, and ear buds) but its fine for my morning jog.  Vocals sound normal but electric guitar gets muddy along with cymbals...but I wasn't expecting audio nirvana from a cellphone anyway.

:guitar:

---

### Post by cozmicharlie on 2008-06-27
Glad you got it working.  I did get a response from the pacpl developer (see below).  Looks like future versions will handle this better.

This is from the pacpl developer:
As for the OPs request, pacpl already has the ability to convert to WMA.  It doesn't use the -acodec wmav2 option though.  This could be added from the command line using the following:

pacpl --to wma his_file.mp3 --eopts="-acodec wmav2"

In fact, in the 4.0.3 release I'm currently working on I've added the ability to remove all hardcoded encoder/decoder options which will allow you to replace them entirely using the --eopts command.

---

### Post by chuyler1 on 2008-06-27
So here is the full solution.

1. Configure synaptic to use medibuntu

[INDENT]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update[/INDENT]

2. Launch synaptic

[INDENT]sudo synaptic[/INDENT]

3. Under settings, make sure medibuntu is checked.

4. Select ffmpeg for installation and install it.

5. Run ffmpeg from the command line or your favorite app.

[INDENT]ffmpeg -i input.mp3 -acodec wmav2 output.wma[/INDENT]

---

### Post by cozmicharlie on 2008-06-27
Nice job summarizing - please mark the thread "solved"

---

### Post by chuyler1 on 2008-06-27
I didn't start the thread and I'm not sure how to mark it solved.

---

### Post by cozmicharlie on 2008-06-27
Only the OP can do it

---

### Post by thefirstone on 2008-06-27
I installed ffmpeg and then winff as gandaran and chuyler1 recomended. Converted nicely from mp3 to wma. Almost half the size and good quality.It was about 50% slower than using JetAudio through Wine. Maybe with some settings it'll speed up.Besides that it was easy and worked smoothly. Thanks to all for the great help.
[http://www.winff.org/](http://www.winff.org/)

---

### Post by GUnit on 2009-01-07
> **gandaran said:**
> Version:ffmpeg 3:0.cvs20070307-5ubuntu7+medibuntu1
File properties » codec WMA Version 8 /stereo/44100 hz
windows media audio - audio/x-ms-wma
I think you actually have to convert the file to a different rate, and possible to mono.  I remember reading somewhere that the software included for Verizon phones converts all files into wma of a lower quality.  I also remember reading that when you pay for an MP3 verizon sends you two verison and the one your phone is of lower quality.  Hope that helps.

---

### Post by GUnit on 2009-01-07
> **chuyler1 said:**
> Ok, I figured it out guys.  I had the order of the command switches incorrect.  I installed winff to see if that would work and it in fact did work.  I snooped the command using 'ps -eflw' and saw how it was executing ffmpeg.  Here's how to do it:

```
$ **ffmpeg -i 02_-_Shoot_to_Thrill.mp3 -acodec wmav2 02_-_Shoot_to_Thrill.wma**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mp3, from '02_-_Shoot_to_Thrill.mp3':
  Duration: 00:05:23.4, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, asf, to '02_-_Shoot_to_Thrill.wma':
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       0kB time=323.3 bitrate=   0.0kbits/s    
video:0kB audio:2522kB global headers:0kB muxing overhead -99.982810%
```

So basically the -acodec wmav2 goes BEFORE the output file, not after.

Now I've got to see if I can get pacpl to execute the right command so I can do things directly from Amarock!
This solved the problem on my Verizon SCH-U900. Thanks a lot!!!

---

