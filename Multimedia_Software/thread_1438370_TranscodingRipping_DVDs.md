---
title: "Transcoding/Ripping DVDs"
date: 2010-03-24
forum: Multimedia Software
---

### Post by deamon_knight on 2010-03-24
I've just started ripping DVDs and I'm trying to save the subtitles. I'm using DVD::RIP and its nice, it allows me to rip the episode I want and saves it to a smaller file I can watch on my media system, but I can't seem to understand the section on subtitles. Normally, if I'm watching a TV show or a DVD and I Mute the volume, the Subtitles are displayed, and this is what I want to happen when I watch the files I've ripped. However, in DVD::RIP, selecting the subtitles stream seems to add the subtitles overlaid the main video whether the audio is muted or not. Can I change something to get the results I want? I've also seen suggestions to use K9Copy and Handbrake instead of DVD::RIP, is one of these program better suited to what I want to do?

Thanks

---

### Post by JohnAStebbins on 2010-03-25
What you want are called soft subtitles.  They are separate tracks in the file that can be enabled and disabled at will.  Whether they are automatically displayed when you mute the audio is a function of the playback software.  I don't know if any playback software does this.  HandBrake can create soft dvd subtitle tracks (aka vobsubs) in mkv files.  It can also add closed captions and import external SRT files as soft subtitle tracks.  If you require the mp4 file format, this format does not support vobsubs, so you would be limited to CC and importing SRT files.  A good source of SRT subtitles is [http://www.opensubtitles.org](http://www.opensubtitles.org).

---

### Post by deamon_knight on 2010-03-27
Well, I'm planning on playing these files on a Windows Media center machine (I'm still tinkering with Mythbuntu but Media Center works for me now), and I know that can play closed captioning from DVDs and Recorded TV when the audio is muted.

Using handbreak and selecting the colsed caption in the subtitles menu seems to be what i want. it adds the CC track and doesn't show them by default. If I play this file in VLC I can activate or deactivated the subtitles track, but when played through Media Center the subtitles don't show up when the audio is muted.

---

### Post by tobemem on 2010-04-28
Just to say that also ANDREW ([http://tobemem.memebot.com]("http://tobemem.memebot.com/")) is able to create Matroska and MP4 files with multiple soft subtitle tracks from DVD and/or SRT files (I don't know what Windows players can show subtitle tracks contained in MP4 files).

---

