---
title: "Sound system is a mess... Please help with configuring HDA-Intel onboard card"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by SergeiFranco on 2007-12-18
Hello there, I am in condition of pulling hair and biting elbows, only problem is that my hair is very short, and biting elbows seem to be an impossible task similar to what I am struggling with.
My problem is Linux sound system in general. It is in complete mess.
Why do I come to this conclusion...
Let me tell you what I have and try to do to explain my situation.
I have 2 sound cards, 1 external - Sound Blaster Extigy, it is an USB sound card that uses usb-audio driver, another is internal/onboard HDA-Intel soundcard, that uses hda-intel driver. As all of the internal and onboard sound cards come with really horrible DAC I have bought Extigy and then later I have bought an digital graphics equalizer (again partially because of linux sound system was mess and I could not have a good global equalizer) that obviously uses digital out
My biggest problem that with both of the sound cards I am unable to have hardware mixing by default. It took me long hours to find that to have hardware mixing I have to use alsa with the following config:
```
pcm.!default {
    type plug
    slave.pcm "dmixer"
}
pcm.dsp1 {
    type plug
    slave.pcm "dmixer"
}
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:1,0"
        period_time 0
        period_size 1024
        buffer_size 8192
        #periods 128
        rate 44100
     }
     bindings {
        0 0
        1 1
     }
}
ctl.mixer1 {
    type hw
    card 1
}
```
This only works (obviously) with second sound card. I partially understand what is happening there, but nowhere I could find proper examples and documentation on how to use asoundrc config file.
For some reason by default (again why?) the digital out is OFF, to switch it on on the  second sound card (trying to remove the need for Extigy in first place) and pathetically try to enable hardware mixing on on-board sound by modifying the original asoundrc I get this:
```
pcm.!default {
    type plug
    slave.pcm "dmixer"
}
pcm.dsp0 {
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
        buffer_size 8192
        #periods 128
        rate 44100
     }
     bindings {
        0 0
        1 1
     }
}
ctl.mixer0 {
    type hw
    card 0
    device 1

}
```
This config obviously has some error in it, as the hardware mixing still does not work! Although with this config I get digital out.
My other big problem that asla mixer/kmix does not control volume for hda-intel at all when using TOSLINK out.
I am using Kubuntu 7.10, with alsa v1.0.14.
Obviously I am stuck with alsa, because unlike ESD/OSS/some other half baked sound system I can configure it more or less to make things partially working, which bring another issue - there is no unified sound system with joint effort to make hardware to work with full potential and fully featured, in other words there are plenty half-working buggy systems that only support basic features (and some times not even properly).
It seems to me that sound in linux is stuck in 1992.

here is the list of the stuff that is broken, unimplemented or unfinished:
1) HARDWARE MIXING!!! very important, or at least turn on software mixing on the sound cards that have no other option.
2) TOSLINK/SPDIF output is not working out of the box
3) No multichannel support by default (not important to me, I am stereo man, but I bet it is very important for DVD people)
4) NO SOFTWARE EQUALIZER (multiband that is, eg more than 10, like 31 band would be sweet, but not important to me any more, I have bought a digital 31 band pro-audio equalizer)
5) NO per application volume control
6) Volume controls are inconsistent in alsa mixer and other mixers, some of the devices get lots of sliders that do not do anything (in my case with onboard audio none of the sliders do anything), also the range is completely out of wack - ie usable range is only top 30%, anything below 70% is equivalent to Mute.
7) With lots of modern sound cards there is a feature - multiplexing I/O - you can choose which jack does what, this feature is nowhere to be found
8) Whole load of different sound systems that do not work properly, can we have one unified sound system that is backward compatible with ALSA/OSS/ESD/etc?
9) Non-existent MIDI support, not very important to me, but I bet very important to a lot of other people.

Since the motto of ubuntu being for humans, how can we expect normal humans to trawl through forums to configure their sound cards in some obscure scrip that makes no sense to a non-programmer, just to make some sound to come out?
Please note: I am not comparing to Windows, although Windows has an upper hand in this matter, my point is that if you want for people to embrace Linux please make it better than windows, as windows is becoming something restricted by design while Linux is even more restricted by lack of the design, even if the idea is free. If you implement very good sound and video system a lot of professional audio/video people might reconsider using Windows/Mac in favour of more advanced system.

---

### Post by lincolnlad on 2007-12-18
I've no idea if it will help, but have you looked at Pulse Audio?
[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

### Post by SergeiFranco on 2007-12-18
I'll give it a try, but I remember trying it couple of month ago, which got me nowhere - I could not even start the bloody thing.
As far as I understand it is just another layer, I could not find list of hardware it support, and the features I am after are at hardware level (like Digital out control).

---

### Post by SergeiFranco on 2007-12-18
End of the day I need help in fixing two issues for HDA-Intel:
1) Hardware/Software mixing to work with Digital Out
2) Volume control to work with Digital Out.

Thanks.

Sergei.

---

### Post by SergeiFranco on 2007-12-19
Right I got it working, I mean software mixing and volume control:
```
pcm.!default {
    type            plug
    slave.pcm       "softvol"   #make use of softvol
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "dmixer"
    }
    control {
        name        "Master"
        card        0
    }
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,1"
      #format S32_LE
      period_time 0
      period_size 1024
      buffer_size 8192

     #rate 96000
   }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
   device 1
}
pcm.dsp {
    type plug
    slave.pcm "dmixer"     # use our new PCM here
}
ctl.mixer {
    type hw
    card 0
}
```

What this does: it creates a dmix software mixer and softvol software volume control.
Now can anyone suggest how to add mute button to my software control please?

---

### Post by deloptes on 2008-02-13
I have
> lspci | grep  Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

and

> cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 20


and 

> cat /proc/asound/card*/codec* | grep Codec
Codec: SigmaTel STAC9200
Codec: Conexant HSF


I use kernel 2.6.20 with debian on dell d520 notebook and do not have any problems with the sound system.

There are problems with different chipsets that are covered by the snd-hda-intel driver.

You have to look at the codec and version and find support for this chip. For example a friend has a notebook with realtek and surprise surprise - on the site of realtek there is a driver for linux for this chip.

I have also a custom .asoundrc that looks like this:

> pcm.snd_card0 {
     type hw
     card 0
}

pcm.snd_card1 {
     type hw
     card 1
}

pcm.snd_card2 {
     type hw
     card 2
}


pcm.dmixer {
     type dmix
     ipc_key 1024
    slave {
        period_time 0
    }
    bindings {
    }
}

pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "hw:0"
     bindings {
          0 0
          1 1
     }
}

pcm.dsnooper1 {
     type dsnoop
     ipc_key 4096
     slave.pcm "hw:1"
     bindings {
          0 0
          1 1
     }
}

pcm.dsnooper2 {
     type dsnoop
     ipc_key 8092
     slave.pcm "hw:2"
     bindings {
          0 0
          1 1
     }
}

pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}




pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}



pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

pcm.dsp1 {
     type plug
     slave.pcm "hw:1"
}

pcm.dsp2 {
     type plug
     slave.pcm "hw:2"
}


ctl.mixer0 {
    type hw
    card 0
}

ctl.mixer1 {
    type hw
    card 1
}

ctl.mixer2 {
    type hw
    card 2
}


I hope this information helps somehow.

regards

---

