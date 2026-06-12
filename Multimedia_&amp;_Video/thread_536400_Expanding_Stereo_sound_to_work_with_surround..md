---
title: "Expanding Stereo sound to work with surround."
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by Face1 on 2007-08-27
I am using an external (USB) creative 5.1 SoundBlaster card, which came with Windows software to simulate surround sound for music, by basically copying the front speaker outputs to the back speakers.  To do this with alsa, I'd think to follow [this guide]("http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_%28Howto%29").  Unfortunately, I have no experience with editing .asoundrc, so I'm a little bit unclear on how to follow that guide.  

```
jacob@lappy:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0640000 irq 23
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:00:1d.7-4.3, full spee

```

I can currently play music (I'm using amarok) by using plughw:External.  If I then put this: ```
pcm.duplicate {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
``` into my .asoundrc, how do I use the plug?  would I put in plughw:duplicate ?  I wouldn't think so, because it isn't physical hardware.

Also: how do I make sure that this changes the correct device: my external soundcard.  (I'm on a laptop, so the internal soundcard has only 2 channels)

---

### Post by Face1 on 2007-09-01
Anyone..?  I've tried several things but I've been unsuccessful.

---

