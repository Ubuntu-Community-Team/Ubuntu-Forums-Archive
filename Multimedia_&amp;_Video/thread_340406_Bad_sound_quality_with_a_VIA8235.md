---
title: "Bad sound quality with a VIA8235"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by LarsKongo on 2007-01-17
I have a VIA 8235 integrated soundcard. My sound works, but the quality isn't very good. When I listen to something I hear a crackling, popping, scratchy sound in the background. The strange thing is that when I choose some of the sound options i have in System > Preferences > Sound it may start to work just fine for a while until the crackling noises comes back when I listen to something the second time. It's very random. I can get a good sound if I choose OSS or 1 of my 2 VIA8235 options, but it's very random and doesn't always work.

And I can say that alsamixer doesn't fix this problem for me. And the card works fine in Windows.

I'm wondering if there's some fix for this? Maybe a config file that needs some extra configuration? I've searched but haven't found anything that solves my problem. :(

Update: I seem to have fixed this problem by adding this to my .asoundrc (if you don't have that file you can create it in your home directory.)
```
pcm.!default {
    type plug
    slave.pcm "dmixer"
}
   
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,1"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 48000
    }
    bindings {
        0 0
        1 1
    }
}
   
ctl.dmixer {
    type hw
    card 0
}
```
There's some more info here about the bad sound quality problem: [http://alsa.opensrc.org/Via8233](http://alsa.opensrc.org/Via8233)

---

### Post by Geff on 2007-09-20
Hello.

I've tried your fix and I think there is some increase in quality, or more accurately, less cracks and shee-shees...

However I put a dedicated PCI Sound Card - a Creative Audigy 2 ZS and it has the same symptoms...

I've tried to replace *pcm "hw:0,1"* with *pcm "hw:1,3"* (the "multichannel playback device" that corresponds to the Audigy card) and *card 1* instead of *card 0* but nothing happened.

I'm afraid I'm just changing stuff randomly as I don't really understand what these setting do, so is there any way to put in two cards? Or some documentation on how to make my own config?

Thank you for your time.

---

