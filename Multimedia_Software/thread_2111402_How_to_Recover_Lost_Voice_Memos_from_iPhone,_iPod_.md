---
title: "How to Recover Lost Voice Memos from iPhone, iPod touch and other iDevices"
date: 2013-02-01
forum: Multimedia Software
---

### Post by lprofil on 2013-02-01
Hey folks,

i would like to share my experience on how to recover "lost" voice recordings from your Apple device. 

In a nutshell: use ffmpeg to convert the *.mov file in the Recordings folder to a *.mp3 file like:

```
ffmpeg -i yourfileinthe-recordingsfolder.mov recovered.mp3 
```


**Extensive explenation**

Plug your, for example, iPhone via USB-cable to your Ubuntu machine. After a few seconds your nautilus file-browser should pop up and shows two paths of you device. Here it is 
"Documents on '$devicename' and '$devicename'.

Navigate to the '$devicename' folder and further to "Recordings".

Here sort the files after date. You should now easily find your recorded file. The thing is that there is more than one file but all have almost the same timestamp.

In my example i have 4 files:

- timestampfilname.m4a
- Recordings.db
- CustomLabels.plist
- **timstamp.mov** <- this bugger is of our interest!

Copy this particular file to your homefolder.

Open a terminal window

Use ffmpeg to convert the *.mov file in the Recordings folder to a *.mp3 file like:

```
ffmpeg -i timstamp.mov recovered.mp3 
```

Voila! You now have successfully recovered your voice recording.


**Background**
Right now i am a little lazy to explain. I might write more about this issue later. Actually a *.m4a which is corrupt is shortly after stopping the voicemail recording into a *.mov file which is also not playable. By converting it to a *.mp3 file i now is playable and thatfor recovered. 
Why this happens? Ask Apple...

ps: i think that a lot of programs, by name

[LIST]
[*][http://www.drfone.org](http://www.drfone.org)
[/LIST]

---

