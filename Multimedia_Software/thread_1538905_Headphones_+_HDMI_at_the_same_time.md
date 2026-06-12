---
title: "Headphones + HDMI at the same time"
date: 2010-07-25
forum: Multimedia Software
---

### Post by TheMiz on 2010-07-25
Hi, I tried getting an answer to this in the Mythbuntu section, but I think I might have better luck over here in the Multimedia section.

I would like to have sound come out of my Headphone jack and my HDMI cable. 

I found this asound.conf file at the ALSA wiki, and I think it will do  what I want as long as I figure out the right values to plug in at the  right locations:

```
pcm.ttable4 {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default 0
    }
    type route;
    hint {
        show {
            @func refer
            name defaults.namehint.basic
        }
        description "4 channel multi route"
    }
    slave.pcm {
        type multi;
        slaves.a.pcm {
            type hw
            card $CARD
            device $DEV
            subdevice $SUBDEV
        }
        slaves.a.channels 2;
        slaves.b.pcm {
            type hw
            card $CARD
            device $DEV
            subdevice { @func iadd integers [ $SUBDEV 1 ] }
        }
        slaves.b.channels 2;
        bindings.0.slave a;
        bindings.0.channel 0;
        bindings.1.slave a;
        bindings.1.channel 1;
        bindings.2.slave b;
        bindings.2.channel 0;
        bindings.3.slave b;
        bindings.3.channel 1;
    }
    ttable.0.0 1;
    ttable.1.1 1;
    ttable.2.2 1;
    ttable.3.3 1;
}
# sometimes apps need matching ctl device
ctl.ttable4 {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default 0
    }
    type hw;
    card $CARD;
}

```Here is the output of aplay -L:

```
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

```What I really need is the "default" output and the "HDMI" output  merged so that they output the same thing at the same time.  I can only  get one or the other, but not both.

Thanks for any advice.  I'm pretty sure a properly configured  asound.conf file is what I need, I am just having trouble getting there.

---

