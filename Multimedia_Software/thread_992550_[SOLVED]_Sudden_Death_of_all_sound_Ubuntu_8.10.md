---
title: "[SOLVED] Sudden Death of all sound Ubuntu 8.10"
date: 2008-11-24
forum: Multimedia Software
---

### Post by iThinkergoiMac on 2008-11-24
So today my computer suddenly decided to stop playing any sounds at all. Like, nothing. I was watching YouTube videos earlier today just fine. Now, my computer won't play anything, whether on the built-in speakers or through the line out. I tried switching from pulseaudio to ALSA, tried uninstalling pulse and using esound (which resulted in a hung system). I've tried making sure I'm in the audio group, which I am, sending static to the speakers, which I can't. I even tried a different user, and still no luck. I'm at my wit's end about what to do about this. The only thing I haven't done is try booting into Windows, which requires a HD swap. I'll probably try it eventually, but I wanted to see if anyone had any ideas here.

The best part is, I leave on break tomorrow and I'll be where I don't have much internet at all (super slow dial-up, unless they've changed it in the past couple years). The only thing I can think of is that the system hung while shutting down earlier today and I had to force it off. That's the only thing I can think of that would have had any effect.

System specs:
Ubuntu 8.10
IBM R50 Laptop
60 GB 7200 rpm HD
Radeon Mobility 7500
Intel Pro Wireless
Intel audio card

Thanks!

---

### Post by psyke83 on 2008-11-24
Check your PCM mixer level (due to a bug in Intrepid, it sometimes gets muted):
```
$ alsamixer -Dhw
```

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by iThinkergoiMac on 2008-11-24
I just got through that thread. And I even had looked at the alsamixer but didn't realize that it was muted because I was unused to the interface... and then I realized that it was two "M"s at the bottom. So I'm good... and apparently must have pulseaudio set up better than before cause I ran through that whole thing too.

Thanks!

---

