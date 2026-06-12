---
title: "[solved] Using VLC to rip DVDs and compression"
date: 2008-09-05
forum: Multimedia Software
---

### Post by uberdonkey5 on 2008-09-05
Got a DVD you want to make into a file? This is how to use VLC to copy (rip) a DVD:

VLC allows data streaming i.e. if you can watch it you can record it. You may have to download additional codecs (mediubuntu) if you are new to VLC and haven't done so previously.

Steps:
1. insert DVD
2. start VLC and File/open disk
3. select DVD (not DVD menus)
4. select the title number (maybe default of zero for whole film, or for series, you can select each episode. Check by just clicking OK and you can watch the episode. Start from step 1 once you know the title number)
5. select stream/save and press settings
6. select file, then browse (where file is to be saved). Name file and REMEMBER to give it extension .mpg so that it is recognised as mpg file when you click on it. Click 'save'
7. select MPEG TS
8. select video codec as h264. This is an excellent compression with good quality (though it is slower than e.g. mp4v). You may want to increase bitrate from 1024, to 2048 or higher if you want v.high quality, though I find 1024 suitable for general use
9. select audio codec as fl32. This is lossless compression (type of FLAC). You can also try FLAC, though I couldn't get the sounds to play back. Alternatively you can use mp3, though this is not lossless. Set extra channels if there are more than 2 (stereo) audio channels (e.g. surround sound).
10. press ok, then ok on 'open disk' page
11. if you want different audio or subtitles, you have to do this at this point by clicking on audio, or video in the VLC toolbar as it is recording. We are recording by STREAMING therefore we are just recording whatever is there. If you didn't click on 'play locally' on stream output tab previously you will not actually see the film as you are recording. It is recommended not to select this, as it makes ripping faster.

The progress is shown by the advancement of the bar at the bottom of VLC.

30 minutes of DVD (1 GB) compressed to 167 MB using h264 at 1024 bit rate
the same compressed to 206MB with MP1V. I'd say quality was slightly better with h264 even at same bit rate and with smaller file size.Thus, for high quality use h264 but go for much higher bit rate.

Of course, this is not for pirating DVDs, but for backing up your DVDs or playing on other devices (I am using it to stick 'family guy' episodes on data pen so I can watch them on my Eee PC :D)

Hope this is of use.

---

### Post by theacoustician on 2008-09-06
> **uberdonkey5 said:**
> Got a DVD you want to make into a file? This is how to use VLC to copy (rip) a DVD:

VLC allows data streaming i.e. if you can watch it you can record it. You may have to download additional codecs (mediubuntu) if you are new to VLC and haven't done so previously.

Steps:
1. insert DVD
2. start VLC and File/open disk
3. select DVD (not DVD menus)
4. select the title number (maybe default of zero for whole film, or for series, you can select each episode. Check by just clicking OK and you can watch the episode. Start from step 1 once you know the title number)
5. select stream/save and press settings
6. select file, then browse (where file is to be saved). Name file and REMEMBER to give it extension .mpg so that it is recognised as mpg file when you click on it. Click 'save'
7. select MPEG TS
8. select video codec as h264. This is an excellent compression with good quality (though it is slower than e.g. mp4v). You may want to increase bitrate from 1024, to 2048 or higher if you want v.high quality, though I find 1024 suitable for general use
9. select audio codec as fl32. This is lossless compression (type of FLAC). You can also try FLAC, though I couldn't get the sounds to play back. Alternatively you can use mp3, though this is not lossless. Set extra channels if there are more than 2 (stereo) audio channels (e.g. surround sound).
10. press ok, then ok on 'open disk' page
11. if you want different audio or subtitles, you have to do this at this point by clicking on audio, or video in the VLC toolbar as it is recording. We are recording by STREAMING therefore we are just recording whatever is there. If you didn't click on 'play locally' on stream output tab previously you will not actually see the film as you are recording. It is recommended not to select this, as it makes ripping faster.

The progress is shown by the advancement of the bar at the bottom of VLC.

30 minutes of DVD (1 GB) compressed to 167 MB using h264 at 1024 bit rate
the same compressed to 206MB with MP1V. I'd say quality was slightly better with h264 even at same bit rate and with smaller file size.Thus, for high quality use h264 but go for much higher bit rate.

Of course, this is not for pirating DVDs, but for backing up your DVDs or playing on other devices (I am using it to stick 'family guy' episodes on data pen so I can watch them on my Eee PC :D)

Hope this is of use.
Please, if you want to transcode a DVD, there are a ton of programs out there that can do it for you and do so in a standards based way.  Handbrake can be compiled from source fairly easily and its wonderful for making H.264 mp4 files.  If you search my user name and Handbrake you can find step by step instructions on how to check it out using svn and compile it.  There's even a list of dependencies in a bit later post after that instructional.  If you need help, just ask.  dvd::rip, acidrip, k9copy, and ogmrip are all available in the repositories and all provide easy GUIs for transcoding DVDs to standard file types and containers.

We appreciate you trying to help the newbs, but instructing them to do crazy, non-standards based transcodes just leads to frustration and confusion down the line.

---

### Post by masterofthemelee on 2008-09-07
Couldn't get it to work.  DVD start spinning, then quickly stops.  VLC provides no progress bar at the bottom, with "play locally" or without.

---

### Post by uberdonkey5 on 2008-09-08
thanks, didn't know about handbrake (I am a newbie myself really, but I spent along time working out how to rip dvd effectively). Not sure how it works, but what I like about vlc is that if you can watch it you can rip it, which isn't true in many cases with other software. As for second question, can you watch the dvd you are trying to rip? If not, maybe appropriate codecs need to be downloaded. Feel free to mail me if further problems as didn't encounter any problems when I did it.

---

### Post by jalirious on 2008-09-12
I find the best way to be using dvd decrypter and dvd shrink on wine. K9copy is not quite as effective as some might have you believe.

---

### Post by gb5757870 on 2008-09-14
Thanks for the fantastic guide. I get terrific video inthe rip but no audio whatsoever. I do get audio when playing it, so presume it's something codec related?

I've tried virtually every audio codec available for the ripping.

Any ideas anyone?

---

### Post by uberdonkey5 on 2008-09-15
oops, yeh.. it is the codecs. Pretty much on my main computer I have codecs coming out my ears, but same thing happens on Eee PC. If you need to rip, but not as bothered about quality use MP1v (vid) and mp3 (audio) and should work on most things. I will update this when I get chance for higher quality rips. Ideally would be good to always use lossless formats.

---

### Post by uberdonkey5 on 2008-09-15
PS. test recording a few minutes only if you are worried it won't play back before you do a massive DVD

---

### Post by gb5757870 on 2008-09-15
Thanks for the suggestions. I have tried mp3 and possibly mp1v,  honestly I think every possible codec.

To test I did a recording of about 1 minute each time with no joy :(

Will definately try mp1v and let you know. Is there anywhere I can confirm/download audio codecs from?

---

### Post by schmindy on 2008-09-15
Very helpful thankyou. BTW. Go to file, wizard in VLC, much easier:)

---

### Post by uberdonkey5 on 2008-09-23
> **gb5757870 said:**
> 

Will definately try mp1v and let you know. Is there anywhere I can confirm/download audio codecs from?

you have the multiverse/universe repositories activated in synaptic? 'medibuntu' has loads of codecs, but I must have downloaded others elsewhere.

---

### Post by gb5757870 on 2008-09-24
Well Mp1v did the trick. A 2 hour movie comes at about 1GB and the sound is a bit low but that's okay. Perhaps with Ibex it will be better with codecs etc.

thanks for your help

---

### Post by uberdonkey5 on 2008-11-05
> **gb5757870 said:**
> Thanks for the suggestions. I have tried mp3 and possibly mp1v,  honestly I think every possible codec.

To test I did a recording of about 1 minute each time with no joy :(

Will definately try mp1v and let you know. Is there anywhere I can confirm/download audio codecs from?

Sorry for late reply. For codecs read:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

also lots of help on these pages. Well, if you are struggling with codecs maybe best to stick to MPEG4 TS, mp4v, mp3 selections.

---------

For subtitles in VLC, choose select all 'elementary streams' at the bottom of the tab you get when you select to stream dvd. I don't bother with subtitles encoding. If all the subtitles don't come up when you play it may be because all the subtitle streams are only available at certain points in the movie (this is a way movie is encoded, not something you've done). What you have to do is get to a point where all subtitles are available (usually where there is some speaking) and select the appropriate subtitles. For me this has worked all the way through the movie, but there have been reports for some movies of having to turn it on at every section! (if the subtitles are not the MAIN subtitle selections i.e english is usually fine).

VLC is useful for ripping DVDs when you have problems ripping with other DVD rip software because, if you can play it in VLC you can rip it (because really it is streaming the data, not directly ripping it). HOWEVER if you wan't more options and a proper rip (and if you have no problem with copyright protection preventing the rip) 'dvd::rip' is great software (look in repositories and use 'add/remove'). I know people will suggest others - biggest problem is that copyright protection on different films interferes with all the (free) ripping software that I have looked at. So, maybe best option for ripping is have a couple of good rippers and vlc. if your rippers don't work, use vlc.

---

