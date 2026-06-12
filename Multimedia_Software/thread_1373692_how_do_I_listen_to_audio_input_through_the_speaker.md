---
title: "how do I listen to audio input through the speakers"
date: 2010-01-06
forum: Multimedia Software
---

### Post by ksheyman on 2010-01-06
Okay guys, im someone who has dabbled in linux for a while but just recently finally decided to make the permanent change. one of the main functions i use my computer for is watching TV through a video capture card (dazzle dvc100). the video component works great using TVtime but i am having mega problems getting the audio working right. I remember when i tried 9.04 it was EASY to enable an audio input to play through the speakers (the normal way I have done it on windows). however, the sound controls are way different in 9.10 and i'm unable to figure it out. ive been searching around for hours and ive found a couple of options, mainly a terminal command to enable a input-output module. it does work, but the audio has major lag! too much to be useful. there was no lag when i did this in 9.04, and there is no lag when i do it in windows 7. i believe the difference is that 9.10 uses pulseaudio while 9.04 used alsa. i might be wrong (am I??).

so here is my question: how can i enable an audio input to play through the speakers without lag? i know it is possible since i've done it before in multiple situations (windows and earlier distros). do i need to get rid of pulseaudio? if so, how do I do that? what would I install instead? is there an easier way?

thanks to anyone who replies!!

---

### Post by markbuntu on 2010-01-06
Try this, post number 3.

[http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

---

### Post by ksheyman on 2010-01-07
"To add the loopback module to the running instance of Pulse Audio I used the command:
$ pactl load-module module-loopback

To make the module automatically load in the future, I used the command:
$ sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '"

thanks for the reply. yes, that is what I was referring to in my post. it does work but like I said, the audio is badly delayed. it seems to be more than a full second late. any other ideas?

---

### Post by cg` on 2010-01-10
I am also experiencing ~1 second delay after performing the above loopback commands.

Am using an ALC1200 Realtek onboard chip, with a guitar pedal board via Line-In.

Any help would be greatly appreciated, thanks :)

---

### Post by cg` on 2010-01-15
Bump.

Its just getting rid of the 1-2 second delay from the pulseaudio loopback, if anyone knows how to :)  Thanks.

---

### Post by markbuntu on 2010-01-15
I have been thinking about this for a while now and I think one of you should file a bug report at launchpad to get someones attention. It looks like a basic problem with how pulseaudio implements its buffering algorithm and the real time components (rtkit). 

You could also try bringing it up at the pulseaudio mailing list or on the IRC channel.

This may already be fixed in recent versions so IRC may be the fastest way to find out.
If you do find out anything, please let us know.

---

### Post by cg` on 2010-01-19
This may be related, of sorts? Just a function to be able to reduce latency or similar might help our cause?

[MailArchive Discussion]("http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg04950.html")

Funnily enough changing doing the following;

cg@elmo:~$ pactl load-module module-loopback latency_msec=1

does reduce the latency a lot, but i still have enough latency to annoy me when playing guitar via line-in. It'd be nice to have it virtually zero.

---

### Post by cg` on 2010-02-06
Bumping - has anyone had any further luck with this?
I've been trying all sorts, but still can't get line in -> digi out loopback working without a delay :(

---

### Post by wirespot on 2010-06-30
Bump. Any news on this one? I'm the same situation. Trying to listen to myself playing harmonica over headphones and I'm getting some delay even with latency_msec=1.

LE: Seems there's [a bug open](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/566381) for it but no solution so far.

---

### Post by bobbysmith007 on 2010-09-15
An easy alternative to pulseaudio is to enable it through alsa:
   * go the terminal
   * Type "alsamixer" and hit enter
   * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
   * make sure you turn the volume up and press m to unmute (if necessary)
   * you should hear your guitar / tv / game console etc (with no lag)

---

### Post by Shaggin Shea on 2011-03-24
```
pacat -r --latency-msec=1 -d  alsa_input.pci-0000_00_1b.0.analog-stereo | pacat -p --latency-msec=1 -d  alsa_output.pci-0000_00_1b.0.analog-stereo 
```
where 'alsa_input.pci-0000_00_1b.0.analog-stereo' is your input  device  and 'alsa_output.pci-0000_00_1b.0.analog-stereo' is your output  device.  Use paman to find these device names.

Hope that helps

---

### Post by daqron on 2011-09-14
> **Shaggin Shea said:**
> ```
pacat -r --latency-msec=1 -d  alsa_input.pci-0000_00_1b.0.analog-stereo | pacat -p --latency-msec=1 -d  alsa_output.pci-0000_00_1b.0.analog-stereo 
```
Wow, that's not overly complicated or anything. Why doesn't it just f**king work when you turn up the mic volume in Alsamixer?

Anyway, thanks for the solution. Worked flawlessly.

---

