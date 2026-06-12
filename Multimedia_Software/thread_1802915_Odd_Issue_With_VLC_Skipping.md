---
title: "Odd Issue With VLC Skipping"
date: 2011-07-12
forum: Multimedia Software
---

### Post by Lancelot59 on 2011-07-12
I just upgraded to 11.04 from Karmic, and I'm using VLC version 1.1.9. I noticed that when I go to play any kind of audio or video file in VLC (I've tested mp3, ogg, wav, flac, flv, avi, mp4, and mkv) that the track skips when it begins playing once at about 1 second in, and then again shortly after.  

After some more testing it also looks like in any video (I tested from 320x240 up to 720p) that the audio lags behind. This makes no sense. I was able to play higher resolution files without any issues on this machine while using Karmic, so I'm thinking it has something to do with the new OS. I'm currently running it using gnome 2.0. I can't think of anything that could be causing this to happen.

Has anyone else seen this problem? I haven't been able to find anything else similar.

---

### Post by ajgreeny on 2011-07-12
I get this sometimes when I open a file in vlc from nautilus but not when I open it  from vlc's own **Media->Open File** dialog.  Presumably this is something to do with vlc still initialising something or other after starting, but not quite quickly enough.

I'm still on 10.04 as you see from my User CP.

---

### Post by Lancelot59 on 2011-07-12
> **ajgreeny said:**
> I get this sometimes when I open a file in vlc from nautilus but not when I open it  from vlc's own **Media->Open File** dialog.  Presumably this is something to do with vlc still initialising something or other after starting, but not quite quickly enough.

I'm still on 10.04 as you see from my User CP.
Well this happens even after I've opened VLC, and I have it set to run only one instance. It happens even if I just pause and resume playing the file. I tried using the open file dialog and the issue persisted.

With a lot of the silly stuff that ubuntu is throwing my way I'm really considering dropping back down a few versions. I never had this issue with Karmic.

---

### Post by Lancelot59 on 2011-07-17
While trying to figure out what was going on I tried running files  in VLC with Totem sitting next to it idle, and the issue vanished. So  that explanation sounds reasonable. I'm bringing this to this forum  because I never had this issue while I was running Karmic.

Has anyone else noticed this? Is there anything that can be done to fix it?

---

