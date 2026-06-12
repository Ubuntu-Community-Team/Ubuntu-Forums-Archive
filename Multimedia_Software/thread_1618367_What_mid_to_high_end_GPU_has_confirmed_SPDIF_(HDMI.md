---
title: "What mid to high end GPU has confirmed S/PDIF (HDMI audio) working?"
date: 2010-11-10
forum: Multimedia Software
---

### Post by ahorriblemess on 2010-11-10
I had an Nvidia GTS250 but I'm selling it. There were many problems with SPDIF in Ubuntu. It worked great in Windows. HDMI audio works perfectly through the motherboard's built-in HDMI port in Ubuntu without any modification of any configuration files.

I play games, so I will be getting another card sometime in the future. Can anyone recommend a GPU that performs equally or better that you've personally had success with outputting HDMI audio?

---

### Post by jocko on 2010-11-10
> **ahorriblemess said:**
> I had an Nvidia GTS250 but I'm selling it. There were many problems with SPDIF in Ubuntu. It worked great in Windows. HDMI audio works perfectly through the motherboard's built-in HDMI port.

I play games, so I will be getting another card sometime in the future. Can anyone recommend a GPU that performs equally or better that you've personally had success with outputting HDMI audio?
Well... I have a gts 250 (Gigabyte N250OC 1Gb) and its hdmi audio works perfectly... But it's not one of those video cards with a built-in sound card, so I connect a spdif connector from my sound card (integrated on the motherboard) to a spdif-in on the video card. So when I activate the hdmi by enabling my TV from the nvidia control panel, the audio is also sent to the TV through the hdmi cable.

---

### Post by ahorriblemess on 2010-11-10
> **jocko said:**
> Well... I have a gts 250 (Gigabyte N250OC 1Gb) and its hdmi audio works perfectly...

How did you get it to work? Unless there's a significant difference between my card (VCGGTS2501XPB) and yours, it wasn't even recognized. I tried a few things, couldn't get it going. 

I should note that I'm using 10.10.

---

### Post by efflandt on 2010-11-10
It would be nice if there was a central location where people could find out what works best with various cards, but the information is scattered and cluttered by earlier information about upgrading alsa, which for some did not go smoothly.

10.10 already has alsa 1.0.23, but still may require some configuration for newer hardware that does not seem to work automatically yet.  What shows up in the output of **dmesg | grep -i hda**, and what devices show up in **aplay -l**?  The latter used to show 8 devices, but the following information narrowed that down to:

```
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```For example for snd-hda-intel options many people suggested creating **/etc/modprobe.d/sound.conf** file containing something like:

```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```That probe_mask is a catch all for internal sound and HDMI sound,  which worked fine, but generated log errors about trying codecs that did not exist and disabling interrupts.  By experimenting I found out the following works just as well for my internal sound and HDMI on GT 220 with cleaner logs:

```
options snd-hda-intel enable_msi=0 probe_mask=1,2
```But then you also may need to create **/etc/asound.conf** which many sources say to configure for a specific hw card and slot.  But then some programs like flash tended to use the alsa default sound device instead of the Output device you select in Sound Preferences.  So instead of setting alsa to use a specific card and slot as default, I stumbled on this asound.conf that eliminates that and allows you to set Output device you want to use from Sound Preferences (which uses pulse):

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```But I have not done surround sound, I just wanted to be able to select analog stereo for my 2.1 PC speakers, or HDMI stereo.  And for that it works great.

NVIDIA says your GTS 250 has "Audio Input for HDMI" "SPDIF", whereas it says my GT 220 has "HDA, SPDIF", so maybe mine works through HDA Intel directly and yours needs a connector.

---

### Post by jocko on 2010-11-11
> **ahorriblemess said:**
> How did you get it to work? Unless there's a significant difference between my card (VCGGTS2501XPB) and yours, it wasn't even recognized. I tried a few things, couldn't get it going. 

I should note that I'm using 10.10.
I'm using 10.10 too, and I did exactly nothing to get it working.
Does your graphics card have it's own, built-in sound card (like the one efflandt describes above), or is it like mine that just passes the spdif signal from the normal sound card?
If it's like mine, all you should need to do is to make sure you have a cable between an spdif header on your motherboard (or sound card if you have a discrete one) and the spdif input on your graphics card.
If it got it's own sound card, its probably going to need some tweaking of the alsa configuration...

Edit: There actually is some thing I need to do...
I must set the sound hardware in pulseaudio to either digital stereo or analog stereo (both the normal spdif and the one in the hdmi is active in those modes).
I didn't know this, since I always use the digital stereo output anyway...
And then the normal problem with pulseaudio's lack of support for passthrough of surround sound, which forces me to bypass pulseaudio and use the hardware directly through alsa if I want to pass through dolby or dts to my reciever...

---

### Post by ahorriblemess on 2010-11-11
It has an SPDIF cable that plugs into the motherboard. Like I said, it worked fine in Windows, just not Ubuntu. I also mentioned that I'm not using the GPU anymore and that everything is fine with the built-in Intel graphics... so I can't troubleshoot it. 

I was hoping to just get some suggestions, or if maybe there's a hardware compatibility list somewhere that I couldn't find. Something similar to the OSx86 hardware compatibility list.

Thank you both for your time.

---

