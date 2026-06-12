---
title: "Ripping CD's to MP3"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2006-12-02
I see that Ubuntu comes with "Sound Juicer" installed so when I throw in a CD, it auto starts this program and I checked the "Preferences" window and I was looking for the highest quality MP3 setting to rip each track as however these are my only option...:confused: 

- CD Quality, Lossless (FLAC Audio)
- CD Quality, Lossless (OGG Multimedia)
- Voice, Lossless (WAV AUdio)
- Voice, Lossy (OGG Multimedia)

How do I get a high quality MP3 from the CD? I am missing something like MP3 support or should I be using a different utility for ripping as MP3?

---

### Post by munkyeetr on 2006-12-02
see if this helps you

[http://ubuntuforums.org/showthread.php?t=204203](http://ubuntuforums.org/showthread.php?t=204203)

---

### Post by CarlosinFL on 2006-12-02
I don't understand that thread. It list an apt-get command that does not work for me. It can't find it in my repo for some reason...:confused:

---

### Post by bapoumba on 2006-12-02
You need to enable multiverse repositories :
[https://help.ubuntu.com/community/CDRipping?highlight=%28non-free%29%7C%28mp3%29]("https://help.ubuntu.com/community/CDRipping?highlight=%28non-free%29%7C%28mp3%29")
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28non-free%29%7C%28mp3%29]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28non-free%29%7C%28mp3%29")
[https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28sources.list%29]("https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28sources.list%29")

---

### Post by CarlosinFL on 2006-12-03
I followed that thread linked above after I enabled "multiverse" and then installed the suggested g-streamer command via apt-get.

I am then completely lost with the following directions from that thread...

> edit Sound Jucier settings
Add a profile
For Gstreamerpipline have:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128

Save and exit Sound Juicer

Then restart Sound Juicer and select options and choose MP3

---

### Post by Swankyman on 2006-12-03
Hi

personally I always use automatix to install all the codecs for mp3 playing because its a point and click job and use grip for ripping. 

;) 

Rich

---

### Post by bapoumba on 2006-12-03
> **Carlwill said:**
> 
I am then completely lost with the following directions from that thread...

Do not worry, I have done it myself ;)

[That one]("https://help.ubuntu.com/community/CDRipping?highlight=%28non-free%29%7C%28mp3%29#head-5858e2c9611a0ff943630aa0bb03fd4f5b5ddf4c") ?
Forget about the preset thing for now.
Paste : audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux
as recommended in the GStreamer pipeline box.

---

### Post by CarlosinFL on 2006-12-03
Where is the gstreamer pipeline box? Is that in SoundJuicer or do I need to use VIM to paste that in? These directions are not clear.

Where do I put this?

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux
```

---

### Post by atoponce on 2006-12-03
> **Carlwill said:**
> I see that Ubuntu comes with "Sound Juicer" installed so when I throw in a CD, it auto starts this program and I checked the "Preferences" window and I was looking for the highest quality MP3 setting to rip each track as however these are my only option...:confused: 

- CD Quality, Lossless (FLAC Audio)
- CD Quality, Lossless (OGG Multimedia)
- Voice, Lossless (WAV AUdio)
- Voice, Lossy (OGG Multimedia)

How do I get a high quality MP3 from the CD? I am missing something like MP3 support or should I be using a different utility for ripping as MP3?

Unless you really need MP3, I would recommend using Ogg Vorbis.  That way, you don't need to check on the legality of whether or not you can use MP3 in your country, you don't have to change/enable repositories and you don't have to install extra software. Plus, it's Free Software. Finally, I think, personal opinion, that Ogg Vorbis sounds better than MP3.  But, then again, I don't have an MP3 player, or any reason to need MP3, so, by choice, I use Ogg.

---

### Post by bapoumba on 2006-12-03
@ atoponce : yes, I prefer ogg too, and for the same reasons. But ... I do have a MP3 player :/ (To be noted, one my sons got an ogg player, 512 Mo).

@ Carlwill : please check the link in post #7. 

[QUOTE=wiki]1- Enable the universe and multiverse repositories. Then, install the gstreamer0.8-lame package to encode mp3s, and the gstreamer0.8-mad package to play them back (in Ubuntu 5.10). For Ubuntu 6.06, you will need to install the package gstreamer0.10-plugins-ugly-multiverse

2- Open Sound Juicer, click "Preferences" from the "Edit Menu", click "Edit Profiles" and choose "New". Call your new profile "MP3 Encoding", or whatever else you feel like.

3- Edit this profile and set Gstreamerpipeline to audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

5- Finally, set File Extension to mp3, click the Active checkbox and then OK.

6- Restart Sound Juicer for the changes to take effect.
[/QUOTE]

There is a screen shot to help you out :)

---

### Post by radiobuzzer on 2006-12-12
Sorry, this didn't work and resulted to a disaster. I had been given two important CDs I had to rip within two hours.
I am on a AMD 64x2, having the 'ugly' package mentioned above installed.

I used the tutorial above, so the CD appeared being ripped. After some time, I realised that the .mp3s created were 700MB each, and that they couldn't be played. Even the audacity is unable to open them. Of course I gave back the CDs and now I have to try to find what has hapenned to these ruined Mp3 files, cause there are people waiting for me to make copies.

It's an awful situation. I wish I wouldn't have trusted linux for this job.
Edit/Delete Message

---

### Post by Myglaren on 2006-12-31
I appear to have the same problem.
MP3's ripped and played fine under Dapper although it wouldn't recognise my iRiver player (ogg/mp3).
Edgy won't play mp3s  It rips but the files are huge.
I just ripped a track to send to a friend and after half an hour it was still being sent, went out for an hour, on my return it was still sending.
Killed it and looked at the file size. 40Meg.
Same file in Ogg Vorbis is 3.4Meg.

the "Ugly" file won't install at all for me.

Tried Automatix and it trashed the filesystem (*twice - I hadn't worked out the first time what the cause was*) which prevented any further installs or uninstalls, had to reinstall Ubuntu from scratch (twice)

May be unrelated but Edgy doesn't work at all well with my camera, while Dapper was perfect.  Edgy recognises the iRiver but thinks it is a camera:confused:

---

### Post by MetalMusicAddict on 2006-12-31
Look through this thread: "[Create Mp3s with Grip and understand what you are doing]("http://www.ubuntuforums.org/showthread.php?t=183125hp?t=25151")"

---

