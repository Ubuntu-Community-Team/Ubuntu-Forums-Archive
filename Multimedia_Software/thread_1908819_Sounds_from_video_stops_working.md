---
title: "Sounds from video stops working"
date: 2012-01-14
forum: Multimedia Software
---

### Post by hartz on 2012-01-14
My problem seems to be related to Pulseaudio.  I had the same symptoms with Linux Mint 12.

Generally the first video I play works fine.  Then after a time if I 
a) resume from pause, or
b) close the video player and open a new video file
Then it plays with no sound.

The problem is intermittend.  Sometimes I can watch 4 of 5 videos in a day with no problems.

Sometimes (99% of the time) a reboot wil fix it.  Sometimes fiddeling with VLC audio settings, pavucontrol, alsamixer, etc will cause the audio to come back suddenly.

I don't yet have a magical workaround/solution.  With Mint Linux the problem went away when I installed VLC-pulse-plugins, but this is installed by default now in (k)ubuntu, at least it is in oneiric.

Should I switch to something other than pulse?  If so, how do I do so cleanly?

For what it is worth, this is on a new install (yesterday) with updates and a small amount of extra software, particularly firefox, numerous RAW photo conversion/manipulation apps, Virtualbox 4.0.6 (non OSE), and bluefish.  The system is a Lenovo T61.  The problem is not specific to VLC (dragon media player is also affected).

---

### Post by hartz on 2012-01-15
Further to this issue, today I noticed something else:  I did not close a VLC program window before I clicked on another file.  The file opened in a new vlc window and sound did not work.  I then closed that one and drag-n-dropped the file to the older, existing VLC app window, and it worked.

I watched numerous videos today, all by re-using the same original VLC window, and sound continued to work without any issues.  I'm too scared to close this window and start a new one now, though that would be the logical next thing to test.

---

### Post by thirdoptics on 2012-01-16
I'm also having the same problem, sound seems to come and go.  Fresh install of 11.10, updated alsa drivers, have tried the sound trouble shooting and several resources but nothing has worked.  

Using the following hardware:

celeron gt530
asus p8h61-m LE (onboard sound disabled in bios)
asus ent210, using the hdmi to pass audio

Very interested to hear anyone input on this, haven't encountered a problem like this in linux before.

---

### Post by carl4926 on 2012-01-16
You could check this
[http://dl.dropbox.com/u/10573557/SUSE%20Misc/vlc_audio_pause_resume_issue.png](http://dl.dropbox.com/u/10573557/SUSE%20Misc/vlc_audio_pause_resume_issue.png)

---

### Post by Murdoc_of_puts on 2012-11-24
> **carl4926 said:**
> You could check this
[http://dl.dropbox.com/u/10573557/SUSE%20Misc/vlc_audio_pause_resume_issue.png](http://dl.dropbox.com/u/10573557/SUSE%20Misc/vlc_audio_pause_resume_issue.png)



surprisingly this was quick and it worked.

---

