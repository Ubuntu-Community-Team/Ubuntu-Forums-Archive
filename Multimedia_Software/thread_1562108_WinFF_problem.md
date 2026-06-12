---
title: "WinFF problem"
date: 2010-08-27
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2010-08-27
Lo all ,

I have a problem with WinFF. I first did the steps in the Comprehensive multimedia how to on this site. Then I also did these steps for ffmpeg and x264 install [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

My problem is that WinFF doesn't want to work. It keeps saying to me that it can't find ffplay as well as ffmpeg. When I run a search I can't even find the files so I can't go and point Winff to it in it's preferences. I did install ffmpeg and when I use ffmpeg in the terminal it works fine. Anybody know how to fix this issue ?

Ubuntu 10.04.1 64 bit

---

### Post by Linuxforall on 2010-08-27
> **Ghost_Mazal said:**
> Lo all ,

I have a problem with WinFF. I first did the steps in the Comprehensive multimedia how to on this site. Then I also did these steps for ffmpeg and x264 install [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

My problem is that WinFF doesn't want to work. It keeps saying to me that it can't find ffplay as well as ffmpeg. When I run a search I can't even find the files so I can't go and point Winff to it in it's preferences. I did install ffmpeg and when I use ffmpeg in the terminal it works fine. Anybody know how to fix this issue ?

Ubuntu 10.04.1 64 bit

Add WinFF ppa from their site and update to latest, then update the presets from their site as well. Finally edit the presets manually by removing 'b' from kb, the new ffmpeg and x264 use k for unit instead of kb. If WinFF can't find ffplay, point to /usr/bin/local via the preferences.

---

### Post by Ghost_Mazal on 2010-08-27
> **Linuxforall said:**
> Add WinFF ppa from their site and update to latest, then update the presets from their site as well. Finally edit the presets manually by removing 'b' from kb, the new ffmpeg and x264 use k for unit instead of kb. If WinFF can't find ffplay, point to /usr/bin/local via the preferences.

Have no idea how to do any of that and there is no /usr/bin/local on my system

---

### Post by Ghost_Mazal on 2010-08-27
> **Linuxforall said:**
> Add WinFF ppa from their site and update to latest, then update the presets from their site as well. Finally edit the presets manually by removing 'b' from kb, the new ffmpeg and x264 use k for unit instead of kb. If WinFF can't find ffplay, point to /usr/bin/local via the preferences.

Ok I got all that done. Except for two things. Their presets ffmpeg version is way outdated. The don't have presets for the current ffmpeg. I Create my own preset anyway.
The second thing is that there is no /usr/bin/local folder on my system. I removed the paths in the preferences and just added the words ffplay and ffmpeg. Now it is not complaining of a file not found , but nothing happens. It open a terminal and that's it.

---

### Post by andrew.46 on 2010-08-27
Hi Ghost,

You can search for the exact location of ffplay by pasting the following into a terminal:

```
sudo find /usr -iname 'ffplay'
```

The Fakeoutdoorsman's guide shuld have ffplay in /usr/local/bin.

Andrew

---

### Post by Linuxforall on 2010-08-27
> **Ghost_Mazal said:**
> Ok I got all that done. Except for two things. Their presets ffmpeg version is way outdated. The don't have presets for the current ffmpeg. I Create my own preset anyway.
The second thing is that there is no /usr/bin/local folder on my system. I removed the paths in the preferences and just added the words ffplay and ffmpeg. Now it is not complaining of a file not found , but nothing happens. It open a terminal and that's it.

If you can't find ffplay in /usr/local/bin that means checkinstall hasn't installed it, redo FO's guide for x264 and ffmpeg.

---

### Post by Ghost_Mazal on 2010-08-28
> **Linuxforall said:**
> If you can't find ffplay in /usr/local/bin that means checkinstall hasn't installed it, redo FO's guide for x264 and ffmpeg.

If it's not installed why is it working 100% in a terminal encode and Handbrake encode ?

---

### Post by Ghost_Mazal on 2010-08-28
Ok I re-installed x264 and FFmpeg using FO's guide , but it's still the same. It doesn't complain about not finding files , it opens a terminal window and then nothing happens further. Still a fail (the ffplay and ffmpeg files are in /usr/local/bin now) But Winff just dooesn't work.

---

### Post by Linuxforall on 2010-08-28
> **Ghost_Mazal said:**
> Ok I re-installed x264 and FFmpeg using FO's guide , but it's still the same. It doesn't complain about not finding files , it opens a terminal window and then nothing happens further. Still a fail (the ffplay and ffmpeg files are in /usr/local/bin now) But Winff just dooesn't work.

Remove the b from kb in the presets.

---

### Post by Linuxforall on 2010-08-28
> **Ghost_Mazal said:**
> If it's not installed why is it working 100% in a terminal encode and Handbrake encode ?

If it works in terminal then its installed but FO's version only installs in /usr/local/bin

Handbrake uses its own x264 and ffmpeg.

---

### Post by Ghost_Mazal on 2010-08-28
> **Linuxforall said:**
> Remove the b from kb in the presets.

Ok done that , still the same. Nothing happens , just a terminal that opens.

---

### Post by Linuxforall on 2010-08-28
> **Ghost_Mazal said:**
> Ok done that , still the same. Nothing happens , just a terminal that opens.

What presets are you using? Are you converting movie formats or extracting audio from youtube flv?

---

### Post by Ghost_Mazal on 2010-08-28
> **Linuxforall said:**
> What presets are you using? Are you converting movie formats or extracting audio from youtube flv?

Mpeg2 to mp4 (x264 and aac) as well as mpeg2 to mp3 audio extraction.

Both does that.

I even tried my own preset with my own command. Same thing , just a terminal window

---

