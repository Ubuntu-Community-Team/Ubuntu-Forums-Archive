---
title: "Sound drops in the middle of playing movie"
date: 2012-11-10
forum: Multimedia Software
---

### Post by PeterTaps on 2012-11-10
Folks,

We have about 40 computers configured exactly the same way. They all are running Ubuntu 11.10 and VLC 1.12. These computers play media via vlc throughout the day. The sound is configured to play from the motherboard output jacks. This is the default pulse audio setting.

Once in a while, in the middle of playing a video, the sound just disappears. This has happened twice on two different computers in the past one month. 

We haven't been able to figure out any pattern. The sound just disappears. Rebooting the machine fixes the problem.

I am wondering if anyone has any idea on what could be happening. Are there any log files I should look for?

I would appreciate any help.

Regards,
Peter

---

### Post by PeterTaps on 2012-11-13
Anyone? Any thought you have would be appreciated. I am running out of ideas on how to isolate this problem.

Regards,
Peter

---

### Post by BicyclerBoy on 2012-11-13
VLC could be outputting direct to alsa so would need to check the configuration settings..

Next time the audio stops I would:
- open terminal & run
dmesg
- look for any clues

aplay -l
speaker-test -l 2 -c 2 -r 44100 -D hw:0,0
- if no sound or fails
lsmod
- look for the snd drivers (e.g. snd-hda-intel)
- try re-load driver
sudo modprobe snd-hda-intel (for e.g.)
dmesg

Could install pavucontrol & try this to manipulate/monitor output.
Pulse audio normally re-spawns if it crashes..

Running 11.10 could be a bad idea long-term..10.04 LTS is supported until next year ?

---

### Post by PeterTaps on 2012-11-14
Thank you very much for your help. I will try your troubleshooting steps next time we have a problem.

Hoping to go to 12.04 soon.

Regards,
Peter

---

### Post by Polydorus on 2012-11-14
> **PeterTaps said:**
>  The sound just disappears

From your title I though the sound level was reduced but from the above it appears you have completely lost all sound.  Which is it?

---

### Post by PeterTaps on 2012-11-16
From what I understand, it just cuts off completely.

Regards,
Peter

---

### Post by Polydorus on 2012-11-17
I was thinking it might be the sound level of the media going up and down.

---

