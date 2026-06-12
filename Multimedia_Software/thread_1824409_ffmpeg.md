---
title: "ffmpeg"
date: 2011-08-13
forum: Multimedia Software
---

### Post by anuswara on 2011-08-13
Hi,  sorry my english. I have a file WAV (= WMAv2)  + video VC-1   I use: 1) mkvmergegui (> MKV)  or  2) Tsmuxergui (> M2TS or AVCHD).  ok the output is playable but not in sync.  I set the audio delay (+1000ms or -2200ms with other files) => at the beginning of the video it is in sync, but near the end not perfectly in sync.  At the moment I dont have permission to move the raw streams into the folder urs/bin/ffmpeg and from Terminal I am able to type ls and cd /Home (this works) but not cd /bin.... nor cd /Desktop (not found, very odd...)  so I witch to windows:  but WinFF seems not to remux (or I am wrong): input: audio.wav + video.vc1 => I become audio.mp4 + video.mp4 separately!  so, I was happy to install ffmpeg (not the gui version) command line for windows...but I dont have a compiler...do you have a ffmpeg for windows for download with a file setup.exe? this were easier for me... at this time I were able to type your code into cmd.exe ...  thanks a lot! best,   PS: You may want to suggest me a different process with Ubuntu, I'd be very happy if this will work fine. thank you.  PPSS: pehaps here the right code: ffmpeg -i input1.wav -itsoffset av_delay -i input2.vc1 output.mkv  perhaps the option -itsoffset av_delay ensure a goo A/V sync! this were wonderfull to do. but I have issues moving to the folders in Terminal, I am unable to get the  $ Desktop  with my raw streams and then $ ffmepg  to launch the code... thanks!

---

### Post by dniMretsaM on 2011-08-13
I'm not really sure what you're wanting here but I'll try my best at answering. If you're having trouble with the FFMPEG terminal commands, you can install WinFF which is a GUI for FFMPEG and may make it easier. Or you could use another converter like Sound Converter.

---

### Post by anuswara on 2011-08-14
Thank you for your reply. does WinFF remux the raw streams (in sync)? or it is a converter only?

---

### Post by dniMretsaM on 2011-08-14
WinFF is simply a graphical front end for FFMPEG, so it can do whatever FFMPEG can. I don't know if that includes what you want though, I don't have much experience with it.

---

### Post by anuswara on 2011-08-14
no, no, dont use ffmpeg please (for this purpose, for my purpose)! ( I tried -async.... -itsoffset...bad bad)  tsmuxergui is better.   thanks.

---

### Post by dniMretsaM on 2011-08-14
Oh ok. Sorry, I couldn't really understand what you wanted.

---

