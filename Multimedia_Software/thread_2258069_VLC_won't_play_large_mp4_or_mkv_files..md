---
title: "VLC won't play large mp4 or mkv files."
date: 2014-12-24
forum: Multimedia Software
---

### Post by A.O._Stanley on 2014-12-24
14.10 fully upgraded.

Files over about 3gb will stop 80mins into play back. 

Any idea how to fix this?

Thanks.

---

### Post by kerry_s on 2014-12-24
try gnome-mplayer, always been good with movies for me.

---

### Post by A.O._Stanley on 2014-12-24
Thanks but no difference with mplayer.

The files I'm trying to view are large screen captures done with kazam.Maybe this is part of the problem. I have used Simple Screen Recorder in the past, but the audio has cracks and pops so is unusable.

BTW, I have googled this to death and haven't found any solution.

---

### Post by andrew.46 on 2014-12-24
Are these avi files? There are problems with big avi files, not sure how vlc deals with the limitations...** Edit:** Mind you I have just read properly and I see you mention mp4 and mkv :)

---

### Post by monkeybrain20122 on 2014-12-24
Do you have hardware acceleration enabled? If you do try to disable it. I don't know why but the .mp4 files created by Kazam are not playable in mplayer or vlc if vdpau is enabled on Nvidia machines(in addition vlc seems to have a problem with some long files with vaapi enabled on intel machines, symptom is video stops but audio continues.)

---

### Post by A.O._Stanley on 2014-12-25
Maybe this issue is related to hardware acceleration. Don't know. Wasn't able to find a way to disable that and I am using an nvidia card. Tried one of the files on my wife's Windows laptop and files wouldn't play in Windows Media so tried her laptop with VLC and had the same problem. 

I did discover a work around. I have been doing these captures of a fairly large part of my screen so I shrunk the size of the capture area and this seems to work. At least on the first try. I'm not ready to mark this as solved yet but if I do a couple more of these captures using a smaller capture size and this works then I will mark it solved. Not a real solution but it does suit my needs and that's all I care about.

Thanks for the various suggestions.

---

### Post by monkeybrain20122 on 2014-12-30
To disable hwacceleration open vlc go to Tools > Preferences then Videos and uncheck the hwacceleration overlay box and go to input/codecs and choose 'disable' from the dropdown for the box hwaccelerated decoding and save.

---

