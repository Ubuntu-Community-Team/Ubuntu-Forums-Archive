---
title: "Alsa - five sound cards and multiple dmixes"
date: 2014-08-12
forum: Multimedia Software
---

### Post by andzejp on 2014-08-12
Hi

I've got problem. I have 5 sound cards installed as follow :

```

 0 [Juli           ]: ICE1724 - ESI Juli@
                      ESI Juli@ at 0x10e0, irq 22
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x88320000 irq 49
 2 [Live           ]: EMU10K1 - SB Live! Value [CT4832]
                      SB Live! Value [CT4832] (rev.8, serial:0x80271102) at 0x10c0, irq 18
 3 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1d.1-2, full speed
 4 [S51            ]: USB-Audio - SB X-Fi Surround 5.1
                      Creative Technology SB X-Fi Surround 5.1 at usb-0000:00:1d.0-1, full speed

```

Audio 3 and 4 are  USB cards. Now, i would like to play on each cards from multiple sources in one time.
I read, that i should use dmix. So, i confgured /etc/asound.conf for dmix :

```

pcm.mixusb { 
    type dmix 
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0666                       # mixing for all users
    slave { 
        pcm "hw:3,0" 
        period_time 0 
        period_size 1024 
        buffer_size 8192
        rate 44100
    }
    bindings { 
        0 0 
        1 1 
    } 
} 

pcm.dsp0 { 
    type plug 
    slave.pcm "mixusb" 
} 

pcm.!default { 
    type plug 
    slave.pcm "mixusb" 
} 

pcm.default { 
   type plug 
   slave.pcm "mixusb" 
} 

ctl.mixer0 { 
    type hw 
    card 3
}


```

It works as ia expected, on hw:3,0 i can play from some sources in the same time.
So, i wanted to add another card with this configuration.
There is my config file after changes  :

```

pcm.mixusb {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0666                       # mixing for all users
    slave {
        pcm "hw:3,0"
        period_time 0
        period_size 1024
        buffer_size 8192
        rate 44100
    }
    bindings {
        0 0
        1 1
    }
}

pcm.dsp0 {
    type plug
    slave.pcm "mixusb"
}

pcm.!default {
    type plug
    slave.pcm "mixusb"
}

pcm.default {
   type plug
   slave.pcm "mixusb"
}

ctl.mixer0 {
    type hw
    card 3
}


pcm.mixjulia {
    type dmix
    ipc_key 2048
    ipc_key_add_uid false
    ipc_perm 0666                       # mixing for all users
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 8192
        rate 44100
    }
    bindings {
        0 0
        1 1
    }
}

pcm.dsp0 {
    type plug
    slave.pcm "mixjulia"
}

pcm.!default {
    type plug
    slave.pcm "mixjulia"
}

pcm.default {
   type plug
   slave.pcm "mixjulia"
}

ctl.mixer0 {
    type hw
    card 0

```

And now, all my sources plays on mixjulia , although some sources are configured to play on mixusb
I remove from config file sections pcm.default ( i dont want to play as default ), and ctl.mixer ( i read
that this section is not needed). It doesnt help.

Any idea ?  I will be grateful for any help.

regards

aP

ps. My system is Ubuntu 12.04.4 LTS server edition.

---

