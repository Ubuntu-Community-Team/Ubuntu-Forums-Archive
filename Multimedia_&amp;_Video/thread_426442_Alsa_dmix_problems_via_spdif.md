---
title: "Alsa dmix problems via s/pdif"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by ikari88 on 2007-04-28
Hi to everybody. This is my first post and I am italian, so please excuse me for my english...

I am no more able to hear any sound from my speakers. I use the s/pdif output to my 5.1 amplifier and I set up my .asoundrc file to enable the dmix plugin. One day I played a file with ac3 audio with xine, enabling the pass through mode, and from that moment I was not able to hear any non-ac3-passed-through file. I tried almost everything with kmix, but I got no results. I only hear some very distorced sound switching from dmix to spdif mode.

Here it is my .asoundrc file:

> pcm.!default {
type plug
slave.pcm "dmix"
}

pcm.dsp0 {
type plug
slave.pcm "dmix"
}

pcm.!dmix {
type dmix
ipc_key 34543
slave {
pcm "hw:0,1"
period_time 0
period_size 1024
buffer_size 8192 # settare a 4096 se ci sono problemi
rate 48000 # settare a 44100 se ci sono problemi
}
bindings {
0 0
1 1
}
}

ctl.mixer0 {
type hw
card 0
}

I need your help.
Thank you in advance.

---

### Post by ikari88 on 2007-04-28
And my soundcard is an integrated via chipset (8235, I think), as I forgot to say.

---

### Post by Drew Woodard on 2007-04-28
I think I may be in a similar situation, I did a clean install of Feisty and sound was working through the spdif connector just fine (I didn't even have to edit my .asoundrc file).

Then I tried to play a file using ac3 passthrough via xine and now I get no sound through the spdif connector.

(motherboard)
msi p6n sli-fi

(sound processor)
realtek alc888

---

### Post by Mrfinn on 2008-03-03
I had the same problem PCM is somehow muted on s/pdif after using AC3 pass through command "iecset  audio on"  in terminal should fix the problem.

---

### Post by BetterSense on 2008-07-02
I have the same problem, and it's the most annoying thing in the entire universe. After doing AC3 passthru, I cannot use my spidf until I do a restart. Most annoying thing I have ever encountered in linux and I don't know what to do.

---

### Post by lefthand on 2008-07-10
I'm having the same issue. I've found that if I just log out and back in, it will work again. Still annoying but better than a full reset.

I've also found that if I pause and restart music in amakok as soon as it cuts out, it will often start working again. 

It seems like there should be a simple solution to fix this permanently but I'm yet to find it.

---

