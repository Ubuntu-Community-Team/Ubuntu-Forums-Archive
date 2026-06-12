---
title: "Turning stereo input to 5.1 output"
date: 2011-06-24
forum: Multimedia Software
---

### Post by jvlomax on 2011-06-24
Here is my problem:
I have my HTPC hooked up to my tv with hdmi and the sound is going through hdmi, and this bit works perfectly. The tv has a stereo output, which i have connected to the input on my htpc. On the same soundcard as where the input goes, i also have an 5.1 system hooked up on the output

There are two ways i can get the pc to give sound both on the tv and the speakers, and each has it's flaws. One solution is to use the pulse loopback module, and then i get sound on all 5 speakers, but the latency makes it very bad when the sound is on the tv aswel.

The other way of getting sound on both tv and pc, is to go into alsamixer and raise the volume on the input. This gives prefect sound, but only on the 2 front speakers.

I have tested and confirmed that both hdmi and the 5.1 sound work fine.

I'm running 9.10(karmic) with alsa version 1.0.23.

Anyone have any experience with this, or know if it's still an issue on lucid (or later)

---

### Post by BicyclerBoy on 2011-06-24
Had to read your post several times to get what you have done..

PC(hdmi-pcm) --> TV --> TV(2ch analogue out) --> PC(mic) --> PC(ana 5.1).

Mad but ingenious.

You should only get 2ch stereo out of surround5.1 because you only have 2ch input.
You could mangle the surround5.1 to upmix, to me this is a bad idea.

IMO the best solution is PC dual output using alsa.
You should feed the HT amp/AVR directly with digital S/PDIF coax not analogue 5.1.

Is the 5.1 system you refer just a analogue connected collection of 6 speakers ?

---

### Post by jvlomax on 2011-06-25
That is exactly what i'm doing :D Can't believe you were actually to get that out of my ramblings. I'm not very good at explaining these things. 

Unfourtunetly my speakers only has analogue inputs, it's one of those creative/logitech pc systems. If only they could make the amp in the systems upscale stereo to 5.1 automaticly......It would make life a whole lot easier and actually make the 3.5 stereo aux input on the be usefull...

I have thought of using dual output, but one of the big benifits of running the whole loop through the tv is that i can controll the volume of both the tv and speakers using the remote from the tv. 

Anyone know how to make also route the sound from input to a spesific output?  I have messed around with the .asoundrc file, but i don't know how to map inputs....

---

### Post by BicyclerBoy on 2011-06-25
You can not make stereo into real 5.1 audio. You can upmix with alsa (simple) or alsa plugin (complex).

Your TV will downmix any multi-channel to 2ch stereo.
It will also add time delay.
Does you TV have S/PDIF output ?
Some have digital pass thru' but most only have 2 ch PCM.

If you are using the TV as a monitor then you could route the audio front channels FL FR only to the TV HDMI as PCM.
This same config could route 4 channels only out to logitech speakers.

An alt setup (plug) would have only 5.1 analogue out with hdmi off.

Each program can have different playback plug.
i.e.
For music Clementine/Amarok can use a a specific plug surround5.1
For MythTV can use custom plug (hdmi 2 ch FR FL + other out analogue) 

Use an IR Rx & remote with the PC to control volume. Could use existing remote if you have programmable buttons.
Just leave the TV sound turned up.

---

### Post by jvlomax on 2011-06-25
I know i can't make it into real 5.1 surround, i just want the sound to come out on all speakers. It doesn't add any time delay to route it through the tv though. Right now my setp is this: HDMI->TV(output through TV speakers)->pc input->output to speakers. This is working fine, i just don't have sound from rear channels. I don't really need it, it's just one of those things :p

The tv does have optical output, but the computer does not have any optical inputs. I'm thinking about getting a soundcard with optical inn, but money is very tight for me at the moment.

The optimal solution for me would be: Defualt all *output* from the pc through HDMI. Upmix the *input* signal to 5.1 and send to the speaers. I just don't know how to get alsa to do the last part.

---

### Post by BicyclerBoy on 2011-06-25
You can get S/PDIF brackets ($10) for PC slot that connect to your mobo soundcard.
Some are optical (TOSLink), some are coax.
I think they can do input & output...

Don't waste your money on a soundcard, they're pointless & you are better to spend the money on a HT Amp/AVR.

Configuring alsa to upmix is not hard.
```

#/etc/asound.conf
# Expand stereo to all channels including LFE
pcm.20to51 {
  type route
  slave.pcm surround51
  slave.channels 6
  ttable.0.0 1
  ttable.1.1 1
  ttable.0.2 1
  ttable.1.3 1
  ttable.0.4 0.33
  ttable.1.4 0.33
  ttable.1.5 0.33
  ttable.0.5 0.33
}

# Create the SoftMaster mixer device that controls *all* channels 
pcm.!default {
    type             softvol
    slave.pcm       "20to51"
    control {
        name "SoftMaster"
        card 0
    }
}

```The above overwrites the default alsa plug on card0
The master volume control only changes the FL FR so a new SoftMaster is created to control all.

---

### Post by jvlomax on 2011-06-25
Thanks for the tip, I'll look and see if i can find one of those brackets,  it would be sweet to have true 5.1 :D

Now we are getting down to what i'm looking for. This is what i have tried using in my .asoundrc:

pcm.!default {
    Type hw
    card 0
    Device 3 #hdmi
}


pcm.20to51 { 
    insert identical code to what you wrote above
}

pcm.route_input->output {

    This is what i have no clue how to do
}

I might be slightly off with the above, i'm just paraphrasing.

I'll try the softMaster mixer tomorrow and see if it helps any.
Thanks for the help so far :D

---

### Post by BicyclerBoy on 2011-06-25
You are overwriting default to be hdmi...
My asound.conf fragment would apply to card 0 as mobo & card 1 the hdmi GPU device..

Are you using i3, i5 IGP hdmi audio ? 

Can you post the output of
aplay -l

I have just realised you do not have any HDMI audio devices, you are using mobo soundcard S/PDIF pass thru' over HDMI (jumper cable)..

---

### Post by jvlomax on 2011-06-25
Yeah, setting hdmi as default was my intention :)

I'm using a motherboard with the gforce 8200 chipset. here is the output of aplay


*** List of PLAYBACK Hardware Devices ****
Card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
 Subdevices: 1/2
 Subdevice #0: subdevice #0
 Subdevice #1: subdevice #1
Card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
Card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
 Subdevices: 1/1
 Subdevice #0: subdevice #0

---

### Post by BicyclerBoy on 2011-06-25
I was wrong again..you are using one soundcard device..
I did not know the 8200 chipset could do HDMI anything..

I don't even know how you got your existing setup to work. 
You must have configured 2 independent paths thru' the audio codec.

The virtualised world of alsa coupled with no usable documentation means I have no idea.

If you are serious about HTPC you might be interested in new graphics card GT430 or GT220 both only PCI-express.
Two independent audio devices could make your required setup possible ? (or more complicated).

The MCP78 8200 8300 chipset graphics was a real odd-ball (very good).
Do you use VDPAU ?

---

### Post by jvlomax on 2011-06-25
Hehe. It all works with some cogs, levers and a crankshaft :p. I just realised that the .asoundrc i wrote above is wrong. It should be:

Pcm.!default {
    type hw
   card 0
   device 0
   
}

Then in xbmc/vlc/etc. I set the program to output to HDMI

 I'm thinking of upgrading to an amd fusion itx board sometime before christmas, so i won't be buying anything for the current serup.

Xbmc runs 1080p video using VDPAU like a dream :D

---

### Post by BicyclerBoy on 2011-06-25
Conrods & pistons I can handle..
Harmonic dampers & piezo-electric knock sensors is starting to sound like alsa tho'..

That makes sense..select hw0:3 (hdmi) in the applications.

I don't think the AMD zacate/fusion is really good enough, it is cheap.
The CPU is better than an atom but the GPU...
It could/should have been a ION beater but it fails in shader performance just like ION, ION2, AMD 5450, nVidia GT520 & GT210.
The shader performance limits the post decode filters scaling, de-interlace, denoise & sharpening.
Some of these are very good for SD material like DVD.

The AMD drivers+ can get you VA-API with a struggle..
So still not perfect & it is 2-3 yrs after nVidia had it sorted.

I'll wait for the bulldozer chip & see if AMD fix the GPU..

---

