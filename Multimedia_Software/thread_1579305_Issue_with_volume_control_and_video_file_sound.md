---
title: "Issue with volume control and video file sound"
date: 2010-09-21
forum: Multimedia Software
---

### Post by something_clever on 2010-09-21
Hi, long time linux user 1st time writer. I'm currently running Ubuntu 10.04 on my HP Pavilion dv7. everything was working fine for months and then suddenly i lost all control of my audio. its still there but i cant turn it up or down. the slider moves but nothing changes (also before anyone can say it, its not muted). my media buttons on my keyboard (vol up, vol down, and mute) all make the little box showing the volume settings show up in the corner but dont actually change the volume just like manually moving the slider.

at the same time that this happened i noticed that my start up sound stopped chiming when i logged in, and a couple days later i tried watching a movie and suddenly there was no sound. I've tried to open several video files in both gstreamer and vlc and the video starts fine and plays as usual but there is no sound (once again, no the programs aren't muted).

i assumed because this was all happening at the same time it was the cause of one problem, namely pulse audio, so i uninstalled pulse and installed alsamixer and it did in fact let me change my speaker volume but i cant figure out how to link to the indicator applet or my media buttons so i reinstalled pulse hoping maybe a fresh install would fix the issue, but it has not, also while using alsa the start up sound came back but video files were still muted.

I've searched extensively for the past week or so for a fix but i can't find any threads on any forums of my problem, or any fixes for it. this is driving me insane so if anyone can help me i would be forever grateful.

---

### Post by lkjoel on 2010-09-21
> **something_clever said:**
> Hi, long time linux user 1st time writer. I'm currently running Ubuntu 10.04 on my HP Pavilion dv7. everything was working fine for months and then suddenly i lost all control of my audio. its still there but i cant turn it up or down. the slider moves but nothing changes (also before anyone can say it, its not muted). my media buttons on my keyboard (vol up, vol down, and mute) all make the little box showing the volume settings show up in the corner but dont actually change the volume just like manually moving the slider.

at the same time that this happened i noticed that my start up sound stopped chiming when i logged in, and a couple days later i tried watching a movie and suddenly there was no sound. I've tried to open several video files in both gstreamer and vlc and the video starts fine and plays as usual but there is no sound (once again, no the programs aren't muted).

i assumed because this was all happening at the same time it was the cause of one problem, namely pulse audio, so i uninstalled pulse and installed alsamixer and it did in fact let me change my speaker volume but i cant figure out how to link to the indicator applet or my media buttons so i reinstalled pulse hoping maybe a fresh install would fix the issue, but it has not, also while using alsa the start up sound came back but video files were still muted.

I've searched extensively for the past week or so for a fix but i can't find any threads on any forums of my problem, or any fixes for it. this is driving me insane so if anyone can help me i would be forever grateful.
Try Fix your sound! in my signature.

---

### Post by something_clever on 2010-09-21
I looked into OSS before but the repository version is glitchy and the DEB packages i can find arent supported so they wont auto update with my system, and id like to avoid that.

---

### Post by lkjoel on 2010-09-21
> **something_clever said:**
> I looked into OSS before but the repository version is glitchy and the DEB packages i can find arent supported so they wont auto update with my system, and id like to avoid that.
You don't need to update OSS 4.x too often.
If your sound works, then the only reason you would update, is to be more compatible/get security fixes.
You can update OSS 4.x once a month if you would wish.
Try using the Mercurial Repository.

---

### Post by Crazedpsyc on 2010-09-21
How long have you used this computer? what kind is it? sometimes the speakers just stop working. Try some headphones. (you may have to adjust some settings in your volume control center for the headphones to work) also, did you tweak anything right before this happened? install any new updates? did it stop after a reboot? or just in the middle of a session?

woops, now I see the comp type, ok

---

### Post by something_clever on 2010-09-21
This computer is less than 6 months old so its not the speakers dying on me. the sound works fine, i just cant control the volume. and its an HP pavilion dv7 as i said in the OP. and i cant pin point exactly when i stopped being able to control the volume because i dont tend to change the volume on this computer that often, i can just say the i noticed it last week (thursday to be exact). and ive used my headphones a couple times on it and it has the same problem (that is, audio play, but i cant control the volume)

---

### Post by Crazedpsyc on 2010-09-21
Ok, about that time firefox got an update and I remember seeing something about sound problems, so if you're using firefox try something else, for example the sound testing utility (System>Administration>Multimedia Systems Selector) (try that even if you're not using firefox) if you hear a beep when you push test, that's good. Then install padevchooser (Pulse Audio Device Chooser).
Run it from Apps>S&V>PulseAudio Device Chooser and it's applet will open up. try tweaking some settings in it's Device manager and volume control there.

---

### Post by something_clever on 2010-09-21
FIXED! thank you so much psyc. i installed padevchooser and it turns out that my HDMI stereo was chosen even though sound preferences was showing my basic stereo options were in place. i switched it back and everything works like a charm, thanks again

---

### Post by Crazedpsyc on 2010-09-21
Wow, i didn't actually expect it to work like that, but that's basically the same problem I had on my ANCIENT desktop

---

