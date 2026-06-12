---
title: "HOWTO: Ripping audio from encoded flash files (aka: make mp3's from myspace songs!)"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by DNAspark99 on 2007-04-19
I don't surf myspace, don't have a page. But when someone linked me to one of my favorite music artists' page, there was a new unreleased song from a forthcoming album playing in the embeded player that I just *had* to have in mp3 form for my Ipod. (I fully intend on buying the full album when it comes out, i just can't wait right now!)

SO I figure it should be a simple matter of using mplayer to rip the sound. I was wrong. 
As it turns out,  it's an encoded format that only the flash plugin can decode. I began looking at how to rip the audio from flash files through the browser, and didn't find much info. It began to look like I may need to use some proprietary program on a different platform. Then I realized, "hey wait a minute, this should be easy!", As it turns out, it was - amazingly easy!

So here's how I did it, using nothing more than Ubuntu Linux and a few freely available tools: (will require flash plugin, mplayer, and lame encoder)

1: Close any IM programs that make random sounds. Basically shutdown anything that may interrupt the audio stream.

2: Go to 'Applications -> Sound&Video -> Sound Recorder' (I always figured there'd be a use for this, just never needed it until now!)

3: Set the following: "Record from input: Mix", "Record as: CD Quality, Lossless (FLAC)"

4: Start recording a new file and start playing the desired audio clip in the browser. (I actually tore apart the page src to isolate the flash file, and loaded that URL directly, but this may not be necessary)

5: When audio is done, stop recording. Save your new file! (we'll just call it 'file.flac' for now)

6: Use mplayer to convert the flac to wav. I found that recording the file as a flac, converting to wav, then encoding that to mp3 resulted in a much better audio quality than just recording straight to wav and encoding from there. 
```
mplayer -vo null -vc null -af lavcresample=48000,channels=2,format=s16le -ao pcm:file=file.wav file.flac 
```

7: Now convert the resulting wav file to mp3 using lame. I prefer high quality bitrates, but feel free to adjust the bitrate with the "-b" option. ```
lame -b 256 -h file.wav file.mp3
```

8: Rename your new mp3, load it up in player of your choice, and tag as desired. Bingo!

---

### Post by ahaslam on 2007-04-19
You could have set a different audio profile in Sound Juicer (these are availabe in SR) that records directly to mp3.
[http://ubuntuforums.org/showthread.php?t=189140&highlight=rip+mp3](http://ubuntuforums.org/showthread.php?t=189140&highlight=rip+mp3)

---

### Post by DNAspark99 on 2007-04-19
wow, see, it's even EASIER than the method i thought was already really easy! dizzam!

---

### Post by H.E. Pennypacker on 2007-05-03
For me, the answer was in selecting "Capture," and not "Mix."  I also recorded the file as OGG, not FLAC.  This should allow me to burn the file right away, but I am not too sure on this.

---

### Post by olavjunior on 2008-01-18
Hm, I don't have the MIX channel in sound recorder. And even though I choose PCM-2, wich seems to control the stream audio, I get no sound when recording. :(

---

### Post by tj111 on 2008-04-03
I seem to have a lot of overhead "noise" in my recordings when using this method.  Any thoughts what might cause that?

---

### Post by warp99 on 2008-04-03
I use a program called Kwave sound editor which works well with Kubuntu (KDE):

[http://kwave.sourceforge.net/features.html](http://kwave.sourceforge.net/features.html)

Kwave can capture the sound off the ALSA or oss output real time. I then edit the file and save it as a wav or export it to .ogg or flac. If I choose to convert  the file later to an mp3 I just use ffmpeg. 

This for me is the easiest way I can think of for capturing sound. I even use it to capture sound from a VMware session of XP to work around a DRM file.

---

