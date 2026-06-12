---
title: "A different &quot;no sound&quot; problem with flash player..."
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by saz on 2008-04-12
Hi there guys!

I'll try to explain my problem really clearly so you can help me out better. I don't think the problem is too complicated, someone who knows a bit about configuring the ~/.asoundrc file will probably catch it quickly, I know nothing about that so that's why I'm asking for some guidance! :)

My Sound Card:
```
Genius SoundMaker Value 5.1 (PCI)
``` 

The Chipset:
```
CMI8738
```

So I buy this card, fresh install Ubuntu, and it runs really smooths, but only the front speakers works, no problem, I went to *alsamixer* and turned on the "Four Channel" switch, now the front AND the rear speakers work, nice! But... the center speaker still quiet... so I googled about this and found that this was a "bug" that the card had that could easily be corrected with a little ~/asoundrc tweaking, so i found, in one of the threads about this problem, an asoundrc file that seemed to have solved the problem to everybody, so I decided to use it. It worked! My centre speaker was now playing loud and clear! :D So, why am I opening this thread? Because if I use that ~/asoundrc file i get no sound on Flash Player! Can you believe that? However if I don't use the asoundrc file i get normal sound on the flash player but no sound from the center speaker.. :-k I've tried adding/modifying things on the ~/asoundrc file that I've found but everytime I do that I get no sound from the center speaker... so I have to choose between *youtube* and a* 5.1 speaker system*... :confused:

Here is the ~/asoundrc file that I found and that I am, actually, using now:

```
# 6 channel dmix:
pcm.dmix6 {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 5120
    }
}

# upmixing: 
pcm.ch51dup {
    type route
    slave.pcm dmix6
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

pcm.duplex {
    type asym
    playback.pcm "ch51dup" # upmix first
    capture.pcm "hw:0"
}

# change default device:
pcm.!default {
    type softvol 
    slave.pcm "duplex"
    control {
        name "Software Master"
        card 0
    }
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"
```

I hope someone can help me with that :)

Thanks in advance!

---

### Post by saz on 2008-04-13
so anyone willing to help?

---

### Post by saz on 2008-04-13
this multimedia forum is always so full with new threads that most of then just don't get any attention... it must be hard for the mods =$

someone help pls!

---

### Post by saz on 2008-04-14
can someone at least tell another place where i can ask for help?

---

