---
title: "No sound with Dazzle DVC 100 in Natty"
date: 2011-05-15
forum: Multimedia Software
---

### Post by smd0665 on 2011-05-15
Hi all. Something went wrong during my upgrade to Natty two weeks ago and I had to do a fresh install. I've been trying to play Wii (using a Dazzle DVC 100) via VLC, which used to work just fine. Please refer to the attached screen print. Now, the video comes out okay, but there is no audio. I've tried playing around with the name of the audio device (hw:1,0 for example), but it still doesn't work.

I've also tried video capture with Lavrec, but it gives me this error:

[lavrec] Error initializing Audio: Audio task died. Reason: Error /dev/dsp - No such file or directory

Could this be related to my other problem? I've looked in the /dev folder and, indeed dsp is not there, nor is there a dsp0,1,2, etc. Sound is working fine for everything else, though. I've Googled and tried some suggestions, but nothing has worked for me. Any ideas? Thank you.

BTW, I did an Ubuntu minimal installation, so I might have missed or forgotten to install something. I have installed the gstreamer good, bad and ugly plugins.

---

### Post by smd0665 on 2011-08-16
Update: This still isn't working in Natty. I've tried it on another machine running a full Natty install and got the same results. So, apparently, it isn't that I don't have the right codec or plugin installed. Also, I tried it using VLC on a Windoze machine; both audio and video worked fine (using Dazzle DVC 100 as both the audio and video device).

---

### Post by djpurity on 2011-08-16
I was looking for info on sound and audio controls being displayed at the top on the top bar. I just did some Synaptic package fooling around stuff, and just noticed that the sound control is missing. I found on another thread to do this to get it to add:

```
apt-get install indicator-sound
```
I got the following reply:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I assume I have to throw in a su or sudo in there to make it work. But have you tried to install alsa or some other controller for sound and check all the settings? I did this once for a problem I had with my sound card not recording, despite it showing the mic was working visually. But no one on Skype or other service could hear me, although my mic bar showed it was reading sound, just not sending sound. I couldn't record it either with any apps. When I installed Alsa, which is not the command I quoted above, it had a GUI that showed my mic was muted in the system.

Just a thought.

---

### Post by djpurity on 2011-08-16
Wait I take that back, I must be having a separate problem than you, because even adding sudo to that command didn't fix it. I got:

```
apt-get install indicator-sound
```

And now get this output:

[sudo] password for djpurity: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by smd0665 on 2011-09-07
It looks like removing HAL must have also caused this to stop working. I installed Arch on one of my computers and tried it. Again, I got video, but no sound. Then, I installed HAL and sound worked. Is there a workaround for this in Ubuntu? I had tried the command "padsp vlc," but it didn't work for me. It's been a while since I tried it, though. Perhaps I should try again.

---

