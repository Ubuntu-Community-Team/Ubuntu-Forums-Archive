---
title: "Getting ALSA to play the same sound on multiple cards simultaneously"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by Tallmaris on 2007-02-04
I've got an USB headset for my PC with Linux (kubuntu 6.10) and I've managed to get them work nice.

Problem is I have to switch every time the settins in my applications to get the sound from one source or another.

I've tried with something like that:
```
pcm.!default {
type hw
card 0
}
```
and a script that changes the card number everytime I want to switch. It works fine for amarok, but it strangely hangs when using aMSN or simply aplay for a test.

The optimal solution would be to send the audio to BOTH devices, then I could just turn off the volume of the one I don't wanna hear and voila.

I've tried a bit of testing with the "multi" plugin, slaves and bindings in the .asoundrc file, but nothing worked. Any idea?

Thanks a lot in advance,
Leo.

---

### Post by pseudonym on 2007-02-04
Many people, including me, report success with the .asoundrc from the [MythTV]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly") website. I think it's easily customisable for use with multiple sound cards, but I've never tried using it like that.

[This]("http://alsa.opensrc.org/MultipleCards"), from the ALSA wiki, may also help you out.

---

### Post by Tallmaris on 2007-02-04
I've managed something copying this setup:

```
pcm.tanta {
type plug
slave {
pcm multi
}
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
}

pcm.multi {
type multi
slaves.a.pcm "hw:0,0"
slaves.a.channels 2
slaves.b.pcm "hw:1,0"
slaves.b.channels 2
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
}

ctl.multi {
type hw
card 0
}
```
That is; i get audio on both device at once and that is great :)

Problem is I lose the ability of mixing, so if I have two source playing (tipically tha aMSN message notice) I don't hear it.

I tried to put the dmixer in the chain, with a solution that seems the most logical, but it doesn't work:
```

pcm.tanta {
type plug
slave {
pcm multi
}
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
}

pcm.multi {
type multi
slaves.a.pcm dmixer1
slaves.a.channels 2
slaves.b.pcm dmixer2
slaves.b.channels 2
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
}

ctl.multi {
type hw
card 0
}

pcm.dmixer1  {
        type dmix
        ipc_key 1024    
        slave {
            pcm "hw:0,0"
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 32000
	}
        bindings {
            0 0
            1 1
        }
}

pcm.dmixer2  {
        type dmix
        ipc_key 1024    
        slave {
            pcm "hw:1,0"
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 32000
	}
        bindings {
            0 0
            1 1
        }
}
```

If i then write: ```
aplay -Dtanta test.wav
``` I get an error of Device Busy, and no sound (if amarok is playing, for example)

---

### Post by darck on 2007-11-17
does anyone know now how to make mixer, which could regulate volume of both sound cards?

ctl.multi {
type hw
card 0
card 1    ????
}

---

