---
title: "Audio playback timing is off"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by screw3d on 2007-09-16
Hey all,

Background: Feisty, Chaintech AV-710 (Envy) on ALSA, 2.6.20-16-generic. More importantly, it was working fine before.

I've recently noticed a weird slowdown with my audio playback. It's barely perceptible, but enough to be very annoying.

I know it's not perceived (e.g., i'm not crazy!). I can verify by hitting start on the player when the system clock is at 0 seconds -- then at the system's clock's 60 second mark, the player is still at 57-58 seconds.

I can reproduce it on rhythmbox, banshee and totem-xine, on either MP3 or FLAC audio files. I've tried switching to kernel 2.6.20-15-generic, and to OSS mixer, killed cpu-freq, and I still can't fix it.

I'm out of ideas. I've tried googling and searching within the forums but it looks like there are only a couple of unanswered threads that kinda describes my problem.

Help?

---

### Post by screw3d on 2007-09-20
Any ideas?

FWIW, here are a couple more threads describing the same problem:

[http://ubuntuforums.org/showthread.php?p=3377675](http://ubuntuforums.org/showthread.php?p=3377675)
[http://ubuntuforums.org/showthread.php?t=541894](http://ubuntuforums.org/showthread.php?t=541894)

I also did the kernel upgrade, but booting the older kernel doesn't seem to fix the problem either. So hmm...

---

### Post by screw3d on 2007-09-20
Installing gstreamer0.8-oss and using OSS instead of ALSA seem to have corrected the timing. I'm still curious what made ALSA do this though..

---

### Post by LonelyToaster on 2007-10-29
I just had a similar problem in my search for getting the rear output to work with the wolfson dac.

I'm not sure if this is available before having done this:
[http://techpatterns.com/forums/about932.html](http://techpatterns.com/forums/about932.html)
with the asound.state stuff.... but what I did do was change a line in the file under control.30 which has the name "Muli Track Internal Clock".

The line is value '44100' which i changed to value '48000' and all my sound is fine now. (Run alsactl restore after changing this line). You can find your asound.state file in /var/lib/alsa/asound.state in ubuntu

(Actually I did change it to 96000 as I thought that was the max supported by the wolfson dac but it reset the value back to 48000)

Hope this helps

---

### Post by screw3d on 2007-10-29
I've definitely tried that as well, but I don't think that was it. I did manage to fix it though, but I can't remember what I did exactly.. :(

I'll post back if I remember, once I get some time to poke around for a bit!

---

### Post by Jusaverage on 2008-01-18
Hey guys been having the same issue it so annoying because im a bit of a audiophile with a good ear lol, Anyway found out the the issue was the multi track internal clock on the card, this must be set from 44100 to 48000, if you go to terminal type in alsamixer, This will display your sound card with all the various values, scroll along the values with the arrow key just adjust the multi track value from 44100 to 48000. It may be the case that you need to adjust this further but none the less this was the fix for me.

Applications, Accessories, Terminal, at the prompt type alsamixer, Use right arrow to scroll across, Up arrow to adjust value from 44100 to 48000 to preferred value.

Cheers

---

