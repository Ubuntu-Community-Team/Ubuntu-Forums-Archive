---
title: "[SOLVED] Master volume control help required"
date: 2008-08-11
forum: Multimedia Software
---

### Post by Chris Musampa on 2008-08-11
Hi all,
I added the lines below to my .asoundrc so Amarok uses my subwoofer when playing stereo mp3s, it does the trick.  The annoying thing is that the master control in Kmix only affects the PCM channel (my front speakers) so if I want to change the volume I have to I also have to change the LFE slider manually to match.

Can anyone give me a simple walkthrough of what I need to do to get Master to affect all channels, ie PCM(front speakers), Surround(TV speakers), Center and LFE.

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
}


Your help would be greatly appreciated.

---

### Post by cariboo on 2008-08-11
You have your pcm control setup wrong, it is basically the master volume control. See here for more on pcm:

[http://en.wikipedia.org/wiki/PCM](http://en.wikipedia.org/wiki/PCM)

Jim

---

### Post by Chris Musampa on 2008-08-11
> **cariboo907 said:**
> You have your pcm control setup wrong, it is basically the master volume control. See here for more on pcm:

[http://en.wikipedia.org/wiki/PCM](http://en.wikipedia.org/wiki/PCM)

Jim

Thanks for your reply but I don't quite see how that helps?

---

### Post by Chris Musampa on 2008-08-12
Anyone?

---

### Post by Chris Musampa on 2008-08-24
Sorted it :guitar:

.asoundrc looks like:```
pcm.!default {
    type             plug
    slave.pcm       "softvol"
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "ch51dup"
    }
    control {
        name        "All"
        card        0
    }
}

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
}

```

---

### Post by vrk1219 on 2009-02-04
Hi Could you give the config file for 4.1 speakers too.

Thanks
RK Veluvali

---

### Post by Chris Musampa on 2009-02-04
> **vrk1219 said:**
> Hi Could you give the config file for 4.1 speakers too.

Thanks
RK Veluvali

Hi RK,
The above is actually 4.1 as I don't include routing for the centre speaker, if that doesn't work for you then maybe change (or add) the last 2 lines to:

```
    ttable.0.4 0.5
    ttable.1.4 0.5

```

---

### Post by vrk1219 on 2009-02-04
Hi Chris,
Thanks for the quick reply.
But my speakers are not working yet. :(
Actuually the file is not existing in my home directory, so I had to crate it and add the above stated entries in it.
Still my 4.1 speakers are dumb....

One silly question... should I need to restart my system for changes to get affected..?

---

### Post by Chris Musampa on 2009-02-04
Yes I seem to remember I had to do something like:
Create the above file, reboot and play some sound, reboot again, now the extra slider (named 'All') appears in kmix/alsamixer.

---

### Post by Poalman on 2009-05-15
Hi,
Used the code plus the 0.4 and 1.4 lines to get my 5.1 working in Jaunty, but I was wondering if anyone knows how to fix this, previously before I upgraded from Intrepid and also now still if I boot into windows on this machine, my sub was/is a whole lot bassier than it is now. 5.1 is working currently (ie I have 6 channels) but the front left and right seem to be getting a lot of the low freq. sounds and my sub is a lot quieter and not playing what it does under windows.

Any ideas would be greatly welcome. I dont want to have to use windows to play my music! lol.

---

### Post by Chris Musampa on 2009-05-16
> **Poalman said:**
> Hi,
Used the code plus the 0.4 and 1.4 lines to get my 5.1 working in Jaunty, but I was wondering if anyone knows how to fix this, previously before I upgraded from Intrepid and also now still if I boot into windows on this machine, my sub was/is a whole lot bassier than it is now. 5.1 is working currently (ie I have 6 channels) but the front left and right seem to be getting a lot of the low freq. sounds and my sub is a lot quieter and not playing what it does under windows.

Any ideas would be greatly welcome. I dont want to have to use windows to play my music! lol.
Are channel the assignments the same as in windows, pretty sure mine were different, this should tell you 

speaker-test -Dplug:surround51 -c 6 -t wav

Other than that I have no idea.

---

### Post by Poalman on 2009-05-18
Thanks, yea all the channels are correct.
The woman sounds very quiet on my sub.. like she's underwater too.. like 30ft underwater.

It just sounds like the entire sound spectrum is played out each speaker when i play music, even on the sub so its like a muffled version of the song almost, and the bass in songs comes out the left right centre which they dont handle very well and it sounds a bit overloaded. never had to configure anything like this. always just seemed to work before.

thanks for your help, ill keep searching.

One thing Ive wondered though, a lot of people with my soundcard (External USB SB Live) seem to have channels like wave and sin in their alsamixer but i just have PCM and the 2 LEDs on the box which you can turn on and off.

---

### Post by bumperchaser on 2009-11-28
Hi,
I used the .asoundrc settings to try and fix the same problems on my 5.1 but now ubuntu doesn't detect the sound card at all! what have I done?

---

