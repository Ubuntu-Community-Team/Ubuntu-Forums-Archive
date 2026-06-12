---
title: "Total newbie - can't figure out how to connect USB mixer"
date: 2007-11-12
forum: Multimedia Production
---

### Post by bartt on 2007-11-12
I was able to get Ubuntu Studio installed, but this PC does not have a sound card, it uses the onboard AC97 sound chip. I need to connect a USB mixer (Yamaha MW12), so I can use the excelllent (looking) programs that are installed with the studio. 

I have tried all sorts of combinations of settings in Jackctl, but have had no luck in getting anything to come in on the USB port. I am sure that I am missing a lot of knowledge about how this is all supposed to work.

Can anyone point me to a simple guide as to where to start? I need basic info here, most of what I read is over my head..

Thanks in advance.

---

### Post by bartt on 2007-11-13
Here's a bit more info. It appears that I need to use jackctl to manage the actual IO here. But I cannot find what settings I should use to ensure that the Motherboard USB port is used. There are settings for Alsa, Oss, and a few others. Which driver is the correct one for just plain old USB? 
I also see some harware settings below that, that seem to relate. What settings should be in there for USB?
Should Linux recognize the mixer (much like Windoze does)?
I'm confused...

---

### Post by prismatic7 on 2007-11-13
> **bartt said:**
> Here's a bit more info. It appears that I need to use jackctl to manage the actual IO here. But I cannot find what settings I should use to ensure that the Motherboard USB port is used. There are settings for Alsa, Oss, and a few others. Which driver is the correct one for just plain old USB? 
I also see some harware settings below that, that seem to relate. What settings should be in there for USB?
Should Linux recognize the mixer (much like Windoze does)?
I'm confused...

OK. The MW12 isn't listed in the ALSA Project [Supported Cards Matrix](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Yamaha), which is *often* but not always a reasonable guide. If it's a class-compliant device (usually meaning it will work without drivers) then you'll be able to use it - not necessarily with all the functionality that Windows can muster, though.

Importantly, you need to determine whether it's actually being recognized by the PC - issuing the command

```
lsusb
```

in a terminal should show a list of USB-connected devices.

If the USB subsystem can see your device, then try

```
cat /proc/asound cards
```

in your terminal, and pay attention to the output of that. Note the NAME that is given to your MW12.

The output will look something like this:

```
0 [Dummy      ]: Dummy - Dummy
                 Dummy 1

1 [VirMIDI    ]: VirMIDI - VirMIDI
                 Virtual MIDI Card 1

2 [AudioPCI   ]: ENS1371 - Ensoniq AudioPCI
                 Ensoniq AudioPCI ENS1371 at 0xe400, irq 11
```

That's a sample - my /proc/asound/cards doesn't loko like that, and yours probably won't either - the card names and hardware numbers will be different. If your card shows up there, it's supported by ALSA's snd-usb-audio driver and you can create an .asoundrc that sets it to be your default card:

```
gedit ~/.asoundrc
```

This file should be blank in a new install, so enter:

```
pcm.!default {
    type hw
    card <cardname>
}
ctl.!default {
    type hw
    card <cardname>
}
```

Where <cardname> is the name that you noted from the output of cat /proc/asound/cards

This ensures that when you log in, your device is set as the default. When it's disconnected, ALSA should default to the AC97 device for all your sound needs. 

This info can be found in the ALSA FAQ - although with more general detail - [here](http://alsa.opensrc.org/index.php?title=FAQ026).

You CAN do this using the major and minor numbers for the card (ie: 2,0 and so on) but these numbers are not respected over a reboot if you have multiple USB sound devices. But that's another life...

---

### Post by bartt on 2007-11-14
Thanks for your effort, 
I guess I was not clear previously. I don't have a sound card. The Yamaha MW12 is a small studio mixing box that connects to my PC via a USB port on the motherboard of the PC.

---

### Post by Stochastic on 2007-11-14
no, you do have a soundcard it's a USB soundcard that is built into your mixer.  the above instructions are accurate.

---

### Post by bartt on 2007-11-14
Ohh, I stand corrected. My apologies..
I guess it doesn't pay to read technical info before coffee in the AM.

here is what I got back from the above commands:

sharon@savant2:/proc/asound$ cat cards
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650F at irq 17
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.1-1, full s

So the name I am looking for is 'default' ?? Seems poorly named..
--------------
From the link to the alsa docs I infer that this is what my .asoundrc file should look like:
pcm.!default {
    type dmix
    card default
}
ctl.!default {
    type dmix
    card default
}
-------------------------

When I try jackctl it appears that I can see the mixer in both alsa and oss. Is this correct?

In any case thanks for your help and patience.

---

