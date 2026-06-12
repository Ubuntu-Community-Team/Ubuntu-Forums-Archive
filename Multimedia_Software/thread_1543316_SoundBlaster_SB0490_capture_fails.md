---
title: "SoundBlaster SB0490 capture fails"
date: 2010-07-31
forum: Multimedia Software
---

### Post by Graemej on 2010-07-31
Hello I would be grateful for some help on a problem with this USB external soundblaster SB4090 card.

The card will not pass audio through it in capture mode. It is fine on playback and enumerates normally as below

```

gvj@gvj-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 21
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:00:1d.0-1, full speed

```

This is the kernel I am currently using but I have also tried the current RC kernel

```

gvj@gvj-laptop:~$ uname -a
Linux gvj-laptop 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux

```

My OS is Ubuntu 10.04
As a test for the card I plug a microphone into the mic jack and attempt to record using gnome-sound-recorder 2.30.0

My internal SigmaTel card does this just fine
My SB0490 will not pass sound to the sound recorder app.
Monitoring the card with 'Sound Preferences' I can see the audio on the bar graph as expected but nothing on the input level meter on gnome-sound-recorder, so sound at least gets up the USB cable.
I tried using Fedora live CD and everything worked normally.
This being the case I then tried the Ubuntu 10.04 Live CD and again everything worked normally so it is something I have borked in my system.

I have installed Jack and pulseaudio-modulejack along with ffado. I suspect there is some kind of conflict or capture hijack occurred.

I have re-installed alsa using the install script by Lidex and am using ffado and jack from svn installs in my usr/local... directory

Another thing which may have messed with the USB sound is an installation of VirtualBox and VMPlayer but I am not very hopeful there. Problem existed pre- VMPlayer anyway and I can't remember about VB.

I would be so grateful for a solution to this.

---

### Post by cchhrriiss121212 on 2010-08-01
Checked your recording levels in alsamixer?

---

### Post by Graemej on 2010-08-01
Yes thanks, I have done that.

---

