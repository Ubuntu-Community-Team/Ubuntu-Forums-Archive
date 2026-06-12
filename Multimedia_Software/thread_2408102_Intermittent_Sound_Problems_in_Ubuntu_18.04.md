---
title: "Intermittent Sound Problems in Ubuntu 18.04"
date: 2018-12-13
forum: Multimedia Software
---

### Post by Yardstick on 2018-12-13
I updated/upgraded from 12.04 to 18.04 about two months ago and have been fighting sound problems since.  None of the troubleshooting guides for sound problems have worked so far.  This seems like something different.  I do get sound... sometimes.  

Netflix and Amazon videos play with no issue.  YouTube usually plays okay.  Frequently the first couple of seconds of sound are cut out while the video starts, but I can live with that.  Occasionally YouTube will play a video without sound.  Music streaming services are also intermittent.  With music services the sound comes and goes on a song-by-song basis.  This is consistent across Firefox and Chrome browsers.  While a video or song is playing I can see that there is output happening in PulseAudio, but there is no output at the speakers.  AThe output device is the HDMI port on my Intel NUC hooked up to my TV.  Additionally, I have found that if a music service starts this muted audio bug then videos on YouTube that are known to play with audio also play without sound.  

I have tried the troubleshooting guides as mentioned above -enabling, disabling, reloading ALSA, PulseAudio, etc.  I thought it could be a licensing issue, but I verified that the latest version of the restricted extras is installed.  

What else can I do to try to fix this problem?

---

### Post by Autodave on 2018-12-14
Upgraded from 12.04 to 18.04?  Wow.  I rarely have any luck upgrading from one release to the next.  I would suggest that you save yourself a lot of headaches and time and do a clean install of 18.04.  Make sure that you backup everything first.

---

### Post by Yardstick on 2018-12-14
I can do a clean install if there is no other solution.  It would be disappointing to go through that process and have the same problem though.  I've probably wasted so much time searching for solutions and  troubleshooting this problem that I could have done a few clean installs  by now.  :rolleyes:

I did find an odd workaround.  If I start a video that is known to play sound and then start one in another window that is known to not play sound, the no-sound video will play with sound!  That doesn't help the streaming music problem where sound seems to come and go depending on the song playing.

---

### Post by Yellow Pasque on 2018-12-17
It almost seems like an issue with 44.1kHz audio. I'd try forcing everything to 48kHz. You can edit /etc/pulse/daemon.conf and find this line
```
; default-sample-rate = 44100
```
and change to the following (making sure to remove the leading semicolon):
```
default-sample-rate = 48000
```

Log out/in (or just restart) and see if it makes a difference. If not, you can restore the original line.

---

### Post by Yardstick on 2018-12-20
I did a clean install of 18.04 today.  So far it seems like one thing has improved.  YouTube videos start the audio and video at the same time instead of having that slight audio delay at the start.  I have not had enough of a chance to find out if there are YouTube videos that will not play sound.  There is still a strange effect happening with Pandora.  If I start Pandora alone it will not play the sound of the track being played.  I can see that the track is being played by the timeline but there is no sound.  If I open YouTube and play a video, the video plays with sound but it does have an audio delay at the start.  If I pause Pandora and then start a YouTube video, the YouTube video plays with no perceptible audio delay.  If I go back to Pandora while the YouTube video is playing and play the existing track, then the Pandora track's audio plays.  

I tried to edit that daemon.conf file but couldn't get it to save anywhere.  I always have problems trying to edit files like that.  I need to look up the procedure again.

---

### Post by Yardstick on 2018-12-20
Quick update:  I just ran across a video on YouTube exhibiting the original behavior of no audio output.  Seems like there's a bug with 18.04.

---

### Post by hassleq on 2019-06-02
> **Yellow Pasque said:**
> It almost seems like an issue with 44.1kHz audio. I'd try forcing everything to 48kHz. You can edit /etc/pulse/daemon.conf and find this line
```
; default-sample-rate = 44100
```
and change to the following (making sure to remove the leading semicolon):
```
default-sample-rate = 48000
```

Log out/in (or just restart) and see if it makes a difference. If not, you can restore the original line.

Thankyou so much for this suggestion. 

It's been driving me mad for two days not least because Firefox always works with sound where as Chromium Browser mutes everytime until I run alsamixer and mute/demute the sound. Even though the sound is already unmuted I guess the mute/demute must force the sound system to renegotiate the sample rate. Having set the sample rate at 48000 it now works every time, at least with my now aging 40" Samsung TV.

---

