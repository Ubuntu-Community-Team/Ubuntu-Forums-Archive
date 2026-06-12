---
title: "Hoontech ST audio DSP24 value &amp; asound.conf"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by ÜbR on 2006-10-17
Hi,

If you've this card, please post your asound.conf here.
I try to find best configuration.

Here's something:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hoontech&card=Soundtrack+Audio+DSP+24.&chip=ICE1712+%28Envy24%29&module=ice1712](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hoontech&card=Soundtrack+Audio+DSP+24.&chip=ICE1712+%28Envy24%29&module=ice1712)

Thanx.

---

### Post by nantetokuma on 2007-02-11
Hello, I've the same sound-card. I've read the same ALSA site, so i've put this in .asoundrc :
```
# Asound.conf START

pcm.main {
        type hw
        card 0
        device 2
}

pcm.ice1712 {
        type hw
        card 0
        device 0
}

# adcdac 1&2
pcm.channel1 {
        type plug
        ttable.0.0 1
        ttable.0.1 1
        slave.pcm ice1712
}

# adcdac 3&4
pcm.channel2 {
        type plug
        ttable.0.2 1
        ttable.0.3 1
        slave.pcm ice1712
}

#adcdac 5&6
pcm.channel3 {
        type plug
        ttable.0.4 1
        ttable.0.5 1
        slave.pcm ice1712
}

# adcdac 7&8
pcm.channel4 {
        type plug
        ttable.0.6 1
        ttable.0.7 1
        slave.pcm ice1712
}

#SPDIF channels only
pcm.ice1712_spdif {
        type plug
        ttable.0.8 1
        ttable.1.9 1
        slave.pcm ice1712
}

# all HW outs set to PCM OUT in envy24
 pcm.hwout {
        type plug
        slave.pcm ice1712
}
# Asound.conf END
```

but I'm not shure it's the best thing... Reading ALSA site about asoundrc they say you need  
**ctl** definition to make Jack happy! :)  there's no **ctl** definition here...

But my DSP24 is working well with alsa jack and ardour, and everything.
I can do 10 channels reccording with 5ms latency.
Only MIDI input is not working as they say, so I use MPUART on the Game-port of the motherboard insted. Working very well...
If you've got ideas about asoudrc, i'm interested!

dawidbass : bass player!:guitar:

---

### Post by nuvolablues on 2007-05-23
Hi!
How do I get to edit the asound.conf ??

---

