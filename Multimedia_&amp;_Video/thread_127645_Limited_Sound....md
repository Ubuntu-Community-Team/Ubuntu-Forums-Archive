---
title: "Limited Sound..."
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by rockmanac on 2006-02-09
OK...  I've tried searching the forums, the help docs, the web and have not been able to come up with a solution.

I have a computer that's unfortunately based off that damn Intel 810 chipset for Audio and Video.  (Seriously, this thing has been my nightmare, even when the computer was running Win 98SE)

Anyway.. Here's the issue...  XMMS will every so often actually play a file, more often than not, all I get is some random distortion sounding noise or something that sounds like a 3D echo effect "thump... thump... thump...  thump..."  (similar to the start-up drum beats) This is with MP3s...  I also have some WAV files I dragged over from the other computer and I get no audio with those.  Additionally, the only way I was able to get GAIM to output a sound was setting the audio to "Command" with the following:

```
aplay  -D dsp0 %s
```

With this all it does is allow me to play the default sounds and will not even attempt to play a custom .WAV file that I'd like to use as the message notification.

I don't know if it matters or not, but following some directions to try and get all of this audio working I did disable the "system sounds" in the sound control panel.  Of course, when I had that enabled, I got the drum beats starting up but then got nothing else from anything except a 60hz hum.

Btw...  I ran a few things on the computer before making the post... Don't know what, if any of it, will help things out:

```

adam@sony:~$ cat /proc/asound/cards
0 [I82801AAICH    ]: ICH - Intel 82801AA-ICH
                     Intel 82801AA-ICH with STAC9744 at 0xe000, irq 10

adam@sony:~$ lspci -v | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97
Audio (rev 02)

adam@sony:~$ aplay -L
PCM list:
hw {
        @args.0 CARD
        @args.1 DEV
        @args.2 SUBDEV
        @args.CARD {
                type string
                default {
                        @func getenv
                        vars {
                                0 ALSA_PCM_CARD
                                1 ALSA_CARD
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.card'
                        }
                }
        }
        @args.DEV {
                type integer
                default {
                        @func igetenv
                        vars {
                                0 ALSA_PCM_DEVICE
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.device'
                        }
                }
        }
        @args.SUBDEV {
                type integer
                default {
                        @func refer
                        name 'defaults.pcm.subdevice'
                }
        }
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
}
plughw {
        @args.0 CARD
        @args.1 DEV
        @args.2 SUBDEV
        @args.CARD {
                type string
                default {
                        @func getenv
                        vars {
                                0 ALSA_PCM_CARD
                                1 ALSA_CARD
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.card'
                        }
                }
        }
        @args.DEV {
                type integer
                default {
                        @func igetenv
                        vars {
                                0 ALSA_PCM_DEVICE
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.device'
                        }
                }
        }
        @args.SUBDEV {
                type integer
                default {
                        @func refer
                        name 'defaults.pcm.subdevice'
                }
        }
        type plug
        slave.pcm {
                type hw
                card $CARD
                device $DEV
                subdevice $SUBDEV
        }
}
plug {
        @args.0 SLAVE
        @args.SLAVE {
                type string
        }
        type plug
        slave.pcm $SLAVE
}
shm {
        @args.0 SOCKET
        @args.1 PCM
        @args.SOCKET {
                type string
        }
        @args.PCM {
                type string
        }
        type shm
        server $SOCKET
        pcm $PCM
}
tee {
        @args.0 SLAVE
        @args.1 FILE
        @args.2 FORMAT
        @args.SLAVE {
                type string
        }
        @args.FILE {
                type string
        }
        @args.FORMAT {
                type string
                default raw
        }
        type file
        slave.pcm $SLAVE
        file $FILE
        format $FORMAT
}
file {
        @args.0 FILE
        @args.1 FORMAT
        @args.FILE {
                type string
        }
        @args.FORMAT {
                type string
                default raw
        }
        type file
        slave.pcm null
        file $FILE
        format $FORMAT
}
null {
        type null
}
cards 'cards.pcm'
front 'cards.pcm.front'
rear 'cards.pcm.rear'
center_lfe 'cards.pcm.center_lfe'
side 'cards.pcm.side'
surround40 'cards.pcm.surround40'
surround41 'cards.pcm.surround41'
surround50 'cards.pcm.surround50'
surround51 'cards.pcm.surround51'
surround71 'cards.pcm.surround71'
iec958 'cards.pcm.iec958'
spdif 'cards.pcm.iec958'
modem 'cards.pcm.modem'
dmix 'cards.pcm.dmix'
dsnoop 'cards.pcm.dsnoop'
snd_card {
        type hw
        card 0
}
dmixer {
        type dmix
        ipc_key 1024
        slave.pcm snd_card
        slave.period_time 0
        slave.period_size 1024
        slave.buffer_size 4096
        bindings {
                0 0
                1 1
        }
}
dsnooper {
        type dsnoop
        ipc_key 2048
        slave.pcm snd_card
        bindings {
                0 0
                1 1
        }
}
duplex {
        type asym
        playback.pcm dmixer
        capture.pcm dsnooper
}
dsp0 {
        type plug
        slave.pcm dmixer
}
default {
        type plug
        slave.pcm swmixer
}
swmixer {
        type dmix
        ipc_key 1234
        slave {
                pcm 'hw:0,0'
                period_time 0
                period_size 1024
                buffer_size 4096
                rate 44100
        }
}

adam@sony:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel
82801AA-ICH]  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In case you're wondering 'swmixer' is something that I tried from another forum, iirc, to try and get things working, but obviously with no luck.

Thanks for the help in advance!

-Adam

---

### Post by Jimmey on 2006-02-10
To improve the quality of sound from XMMS, controll the volume from your speakers ( assuming you have some ), and not through XMMS. When the XMMS' volume slider it turned all the way up, the sound distorts a little...If you want to hear it louder, as I've said, use the speakers :P

I'm not to sure about .wav files. You might want to try playing them in another player, or making sure that you've the correct XMMS plugin to play them ( if that's even necessary ). I'd suggest VLC, because the only experiece I've had with installing XMMS plugins isn't one that I enjoy talking about. It was faily oogly.

Regarding the system sound; It happens to me sometimes that when I try to play a file in XMMS, esd will be using the soundcard at the time, although god knows what for. A simple way to disable the system sound is to press F2, type > killall esd

I hope at least some of what I've said is of use...Sound problems are no fun.

---

