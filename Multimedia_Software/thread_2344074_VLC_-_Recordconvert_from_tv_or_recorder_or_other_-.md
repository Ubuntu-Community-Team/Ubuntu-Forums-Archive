---
title: "VLC - Record/convert from tv or recorder or other - some findings"
date: 2016-11-22
forum: Multimedia Software
---

### Post by xinuzi on 2016-11-22
The topic has been on the Ubuntu forums before, but still, some findings of mine concerning recording video with sound from a tv or vhs-dvd-hdd recorder with a (scart-to-)composite/s-video-to-usb kabel, and that with the VLC mediaplayer (gui).

Video origin:

- raw PAL stream.

Used/tested hardware: 

- A newer laptop with 6 GB ram and a ten year old one tuned up with 4 GB ram.
- EasyCap composite/AV/s-video to usb(2) stick.

Software/platform:

- Videolan's VLC Mediaplayer (newest versions) in its gui form.
- Ubuntu 16 64bits on the newer machine.
- Linux Mint Rosa 32bits on the older machine.

First of all, I'm not talking about using the record button in Advanced VLC settings as the resulting files 
are unacceptably large in that case - but, about immediately recording/converting to let's say the x264-aac-mp4 format.

Open Media - Convert/Save in VLC, and choose e.g. Video Camera and then /dev/video0 for video and hw:0,0 or hw:0,1 or hw:0,2
for audio (depending on what works when playing the stream).
Important to select the correct video standard. Just PAL for PAL or otherwise NTSC. Don't do anything with the advanced settings.
Just push the play button to test the signal first.
Afterwards push the arrow button right of the 'Play' button and then 'Convert'.
(I use the Dutch version of VLC so names could slightly differ.)

Conversion settings:

I my case I created/named my own mp4 profile with mp4 container containing h264 video 2500 to 6000 kb/s, 25fps (or leave as is), 128kbps/44100 Hz dual channel AAC.
Leave the rest as is. Try not to use too many filters. preferably none.

1) Newer machine:

Problem of sound not converting to AAC.
Solution: use the regular Mpeg.
Possibly convert afterwards by stream copying the video stream and converting just the audio to AAC.

2) Older machine:

Problem of sound well converting but picture halting after one third of the recording.
Solution: go to VLC general preferences, Input/codecs and set x-264 on 'ultrafast' and preferably 'fast decode' (+ x264 profile high 0, less important).
It seemed that the convert video stream could litterally not keep up with the input video stream.
Setting x-264 on ultrafast can make the recorded video stream less sharp.
You can compensate this by pumping up the video bitrate under 'Convert'. In case of 'ultrafast' x264 I wouldn't go too much
lower than 2500 kb/s.

The recording starts by pushing 'Start' and stops/saves when pushing the 'Stop' button.
It is alas not possible to record this way and pushing the pause button and then continuing recording another fragment to a new file as you 
can when you use the record button (once again, that button generates enormous files...).
After pushing 'Stop' you'll have to redo the whole conversion setting process first to record/convert another fragment.
(At least, I don't get the impression there is an easier recording-immediate-converting way).

For the rest: keep the standard VLC settings as much as is as possible.

One more thing: VLC seems to have a problem with presetting the file saving location when that location
has a symbol in its name. E.g. the "Video's" folder in Ubuntu and Mint. Better to give VLC its own folder
without accents or spaces under your personal space e.g.

---

### Post by deadflowr on 2016-11-22
Video's?
Where is that?

---

### Post by xinuzi on 2016-11-23
As you ask the question I understand the answer.

"Video's" is of course the Dutch plural of "video" on my Dutch language version system.
It will probably be "/home/usr/Videos" on English systems.

I mean presetting the saving location in the General Preferences -> Input/codecs of the VLC mediaplayer.

Tweaked it in the meantime.

---

### Post by xinuzi on 2017-02-06
Tried 'Cheese' too, but, too limited in settings and rarely any sound.

And mencoder with mtvcgui. Sound Delay trouble.

There always seems to be sth going wrong when capturing.

This works best for me today: [https://ubuntuforums.org/showthread.php?t=2354678](https://ubuntuforums.org/showthread.php?t=2354678)

---

