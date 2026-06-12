---
title: "Problems with sound since Gutsy"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by Foo Fighter on 2007-11-17
Hello there...
Since I updated to Gutsy, my Creative SB Live 5.1 sound card doesn't work very well! I can hear sound, but if I'm listening to some music with Amarok, it crashes every 2 songs! Recording is also impossible!
I executed such a "ALSA Information Script". I got this output:
[http://pastebin.ca/769761](http://pastebin.ca/769761)

There I saw: No driver is installed, no sound cards are detected.

So I tried to compile the Alsa-Driver manually. I followed this guide:
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

But at the part of the ```
       modprobe snd-emu10k1 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
``` i'm getting this error:
[http://pastebin.ca/769778](http://pastebin.ca/769778)

The output of* ls -R /lib/modules/2.6.22-14-generic/kernel/sound/ *looks like this:
[http://pastebin.ca/769773](http://pastebin.ca/769773)

Installing Alsa using Synaptic doesn't work too.
Has anyone a Idea, what I could do to fix this problem?

Thank you very much!

---

### Post by Yellow Pasque on 2007-11-17
Your card is supported by OSS. I would use that instead. See my sig for details.

---

### Post by mushroomcloudwarrior on 2007-11-19
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

This seemed to help me

---

