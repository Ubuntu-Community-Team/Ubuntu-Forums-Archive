---
title: "ffmpeg upgraded, now it doesn't work..."
date: 2010-04-23
forum: Multimedia Software
---

### Post by HousieMousie2 on 2010-04-23
There was an upgrade for several ffmpeg packages yesterday...

Prior to the "upgrade" I had used this code to convert MP4 to MP3:

```
ffmpeg -i Some-File.MP4 -vn -ar 44100 -ac 2 -ab 192 -f mp3 Some-File.mp3

```

And it worked perfectly, zero complaints.

Today, after last night's upgrade of only ffmpeg packages, it no longer works... I tried it again on the same file it had successfully converted yesterday... no joy.

This is the output (along with an empty file):

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Apr  8 2010 20:06:58, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Some-File.MP4':
  Duration: 00:03:43.2, start: 0.000000, bitrate: 409 kb/s
  Stream #0.0(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(und): Video: h264, yuv420p, 320x240, 23.98 fps(r)
Output #0, mp3, to 'Some-File.mp3':
  Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0

```

Any ideas?

Thank you fro your time!

---

### Post by mc4man on 2010-04-23
see links here - should be updates to fix next week
[http://ubuntuforums.org/showthread.php?p=9161231#post9161231](http://ubuntuforums.org/showthread.php?p=9161231#post9161231)

(you may wish to add to that bug that hardy is also affected though I'd think that would be known...

---

### Post by HousieMousie2 on 2010-04-24
Thanks, mc4man.  I was beginning to feel alone with this issue.

I added my two cents to the bug you linked.

Thanks again!

---

### Post by FakeOutdoorsman on 2010-04-25
> **HousieMousie2 said:**
> There was an upgrade for several ffmpeg packages yesterday...

Prior to the "upgrade" I had used this code to convert MP4 to MP3:

```
ffmpeg -i Some-File.MP4 -vn -ar 44100 -ac 2 -ab 192 -f mp3 Some-File.mp3

```

And it worked perfectly, zero complaints.

Today, after last night's upgrade of only ffmpeg packages, it no longer works...

I see three potential issues.  First problem is that you may not have all of the encoders enabled in FFmpeg.  This can be remedied in a variety of simple ways:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

Secondly, your command is outdated.  Old FFmpeg versions used to use kilobits/s in the options that deal with bitrate (such as *-b* and *-ab*), but more recent FFmpeg versions use bits/s.  You can either change *-ab* to bits or just add a **k** to your bitrate, such as *-ab 192k*.  Now your command can look like:

```
ffmpeg -i Some-File.MP4 -ar 44100 -ac 2 -ab 192k Some-File.mp3

```
or you can use *-aq* instead of *-b* to create a Varible Bitrate File.  I believe these values correlate to the *-V* option in *lame* (this is my preferred method).  Here's a simplified version of the above, but with *-aq* instead of *-b*:
```
ffmpeg -i Some-File.MP4 -aq 4 Some-File.mp3

```

I'm not sure what version of Ubuntu you are using, so you may need to add *-vcodec libmp3lame* to get any of these examples to work.  That's the third potential issue.

---

### Post by HousieMousie2 on 2010-04-25
Thank you for the reply, FakeOutdoorsman, I followed the guide as much as I could... no change.  The libavcodec packages you listed are not available for Hardy Heron apparently, I just have libavcodec1d.

I was pretty sure I already had everything I needed... since it had worked perfectly earlier in the same day as the update, but not 12 hours later.  I guess they changed something.

I tried both versions of the new code you gave me too, still no love, but again, thank you for giving me less antiquated commands to use! :)

**Deep sigh** I await word from launchpad, I guess.

Thanks again!

---

### Post by FakeOutdoorsman on 2010-04-25
I forgot how old Hardy's FFmpeg is.  By default, Ubuntu's FFmpeg doesn't have a MP3 encoder enabled.  For Hardy you can fix this by compiling FFmpeg yourself, or by using packages from a third-party source such as Medibuntu.  These options are both covered in the link in my earlier post.  *Option C: Medibuntu* will be a faster way to do this for the impatient, but *Option A: Compile FFmpeg* will provide you with a much newer version of FFmpeg.

Using Medibuntu's FFmpeg, I don't remember if you need to use *-acodec mp3* or not (it's too old to use *-acodec libmp3lame* as I mentioned in my last post).  Perhaps I should re-install Hardy in Virtualbox so I don't have to rely on memory.

Another option is to install **lame** and then use FFmpeg to decode any audo and pipe it to lame for encoding:
```
ffmpeg -i input.foo -f wav - | lame -V4 - output.mp3
```

---

### Post by mc4man on 2010-04-25
@ HousieMousie2
FO's posts made me take a closer look,( my apologies there), while there is an issue with the updated ffmpeg libs, in your case I think it's a bit different.

As noted the repo ffmpeg doesn't support mp3 encoding, but medibuntu's  does.

If you had the medibuntu ffmpeg and shared libs then the update would have replaced them. (...7.4 vs ...7.3

If that's the case, (seems likely), then any forthcoming update will be of no use to you in this regard.

I'd assume at some point medibuntu will also update, but most likely not immediately.

Your best bet would be to see if in synaptic you can force the libs/ffmpeg back (if indeed you did have medibuntu.

Otherwise the pipe command w/ lame will work and may be better anyway.

( as an aside - you could use a same name batch command to do either multiple or a single file - will convert all mp4's in the dir.
cd to dir and 
```
for f in *.mp4; do ffmpeg -i "$f" -f wav - | lame -V3 - "${f%.mp4}.mp3"; done
```

---

### Post by HousieMousie2 on 2010-04-25
> **FakeOutdoorsman said:**
> I forgot how old Hardy's FFmpeg is.  By default, Ubuntu's FFmpeg doesn't have a MP3 encoder enabled.  For Hardy you can fix this by compiling FFmpeg yourself, or by using packages from a third-party source such as Medibuntu.  These options are both covered in the link in my earlier post.  *Option C: Medibuntu* will be a faster way to do this for the impatient, but *Option A: Compile FFmpeg* will provide you with a much newer version of FFmpeg.

Using Medibuntu's FFmpeg, I don't remember if you need to use *-acodec mp3* or not (it's too old to use *-acodec libmp3lame* as I mentioned in my last post).  Perhaps I should re-install Hardy in Virtualbox so I don't have to rely on memory.

Another option is to install **lame** and then use FFmpeg to decode any audo and pipe it to lame for encoding:
```
ffmpeg -i input.foo -f wav - | lame -V4 - output.mp3
```

Thanks, FakeOutdoorsman, for the reply.
As I said, I followed the guide as far as I could for Hardy.  I have had the Medibuntu repo in my list all along and for more than just the sake of ffmpeg. :biggrin:  Again I point out that ffmpeg worked perfectly less than 24 hours earlier, so enabled/disabled MP3 encoder does not seem like the issue here.

It is a little irritating to think I would have to employ a second program to do what one program was doing by it's self, just hours before the update (from Medibuntu,) but oh well... such is life.

Thank you for the suggestion about Lame and command line info!

---

### Post by HousieMousie2 on 2010-04-25
> **mc4man said:**
> @ HousieMousie2
FO's posts made me take a closer look,( my apologies there), while there is an issue with the updated ffmpeg libs, in your case I think it's a bit different.

As noted the repo ffmpeg doesn't support mp3 encoding, but medibuntu's  does.

If you had the medibuntu ffmpeg and shared libs then the update would have replaced them. (...7.4 vs ...7.3

If that's the case, (seems likely), then any forthcoming update will be of no use to you in this regard.

I'd assume at some point medibuntu will also update, but most likely not immediately.

Your best bet would be to see if in synaptic you can force the libs/ffmpeg back (if indeed you did have medibuntu.

Otherwise the pipe command w/ lame will work and may be better anyway.

( as an aside - you could use a same name batch command to do either multiple or a single file - will convert all mp4's in the dir.
cd to dir and 
```
for f in *.mp4; do ffmpeg -i "$f" -f wav - | lame -V3 - "${f%.mp4}.mp3"; done
```

The batch command is cool, not sure I am understanding how to use it though...

CD to the directory containing the target MP4s... then use this code, as is?
```
ffmpeg -i "$f" -f wav - | lame -V3 - "${f%.mp4}.mp3"
```
Will it preserve the file names?  Will it overwrite the MP4s?

I may see if I can revert to the previous ffmpeg version, sadly I did not use Synpatic to do the upgrade, since it has an easy-to-find history of downloads.  Poke and hope time!  :)

Thanks, mc4man!

---

### Post by mc4man on 2010-04-25
> then use this code, as is?
Yes but use** the whole command** 'as  is'

Ex
I have a folder with a couple of mp4's, so I cd to it and (command in blue
> doug@doug-desktop:~/Desktop/convert$ [COLOR="Blue"]for f in *.mp4; do ffmpeg -i "$f" -f wav - | lame -V3 - "${f%.mp4}.mp3"; done[/COLOR]


I happen to be on a new lucid install and only have 1 mp4, so for Ex. made a copy with a different name - results of command in screen - 2 same name mp3's, 2 orig mp4's

> I may see if I can revert to the previous ffmpeg version

If not there is an easy way do dl the .debs and use dpkg to downgrade - let me know

---

### Post by HousieMousie2 on 2010-04-25
> **mc4man said:**
> Yes but use** the whole command** 'as  is'

Ex
I have a folder with a couple of mp4's, so I cd to it and (command in blue

I happen to be on a new lucid install and only have 1 mp4, so for Ex. made a copy with a different name - results of command in screen - 2 same name mp3's, 2 orig mp4's



If not there is an easy way do dl the .debs and use dpkg to downgrade - let me know

Oops.  lol  Thank you!

An easy way, you say?  Do tell!  I'm always pleased to find easy ways!

---

### Post by mc4man on 2010-04-25
> An easy way..

Well I'm not on hardy so you'll need to do a little ground work yourself


A momentary  digression - ( see edit, I'll leave the below about forcing thru synaptic in case you decide to install it.)

First open synaptic and search ffmpeg
 
click on libavcodec1d and then at the top click on package -> force version and see if the previous ..7.3 is available. If so select, then go to libavformat1d, ffmpeg and any other of the ffmpeg libs you have installed. ( probably only  libavutil1d 

After all are set then  **click the 'apply' button**, when done close synaptic - synaptic will attempt to prompt you about marked changes, answer yes (you want to discard..) and close. 

(otherwise synaptic will update you right back to the current versions


If the above isn't possible or whatever then to continue - 

 go directly to medibuntu and download (don't let gdebi install)
the 4 packages - ffmpeg, libavcodec1d, libavformat1d, libavutil1d 

[http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

After downloading place all the .deb's in a folder (for instance create a folder in  home dir named revert)
Then in a terminal cd to the folder and run 
```
sudo dpkg -i *.deb
```
That should do it


Side note
when using dpkg like this all is well if all the dependencies are either installed or in the folder you are running dpkg on.

*In this case you should be fine* - if there was an issue (failed to install or broken package), no need to panic - easily fixed by - 
reading back thru the terminal to see the issue 
Then  going to synaptic and either find and remove the broken package, then install or add to the folder what was missing, then run the dpkg command again...
 or in most cases just going edit -> 'fix broken packages'


Edit: again my brain is not sharp today (if it ever was)
you're on kbuntu so I guess you don't use synaptic - not sure how you use whatever the package manager is - the few times I tried kubuntu I did end up installing synaptic, found it easier to use

---

### Post by HousieMousie2 on 2010-04-25
Sorry my previous post was not as clear as I would have liked.  I had Synaptic, I just didn't use it for the ffmpeg upgrade, or else Synaptic's History would have made life easy.  But I did use it to revert to the previous versions of the ffmpeg packages (libavutil1d, libpostproc1d,  libavformat1d, libswscale1d, ffmpeg, libavcodec1d) and all is well!  My files are converted and I am a happy camper!

As for hunting and fixing installation issues, lol, I no longer panic over those, I've had to do it too many times... but the first time I had to do it, oh yeah... I panicked!

Thanks again, mc4man, for all of your help and information!

---

