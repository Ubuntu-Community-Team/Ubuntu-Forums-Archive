---
title: "HDMI Sound working - Aspire Revo R3610 - Ubuntu 10.10"
date: 2010-10-27
forum: Multimedia Software
---

### Post by xbmcoholic on 2010-10-27
Just wanted to post a solution that otheres with similar hardware may find helpful.  If you've got one of Acer's Revo units, check alsamixer and un-mute S/PDIF 1.

I wasted DAYS trying to fix this and it was so simple!

$alsamixer -> S/PDIF 1 <- un-mute by hitting m

What a horrible description in alsamixer!!!

So for my alsamixer screen
Master=100
PCM=100<>100
Front=100<>100
Mic=MM 0<>0
Mic Boos=0<>0
S/PDIF=00
S/PDIF D=MM
S/PDIF 1=00

---

### Post by ivr on 2011-02-07
After struggling with the HDMI sound on my Acer Revo 3610 with Ubuntu 10.10 for more than 3 weeks, I finally found the solution today.
Don't just change the settings in the alsamixer for those mixer controls, but press F6 and make sure you have selected the correct sound card!!!

In my case I kept enabling/disabling the mixer controls the onboard HDA Intel one and not the ones on the HDA NVidia card, so I never heard the sound through my Samsung telly.

One I changed to the correct sound card and muted all S/PDIFs on the NVidia card, and also changed to HDMI in the Ubuntu sound preferences dialog, I suddenly heard the music coming from Rhythmbox out from the speakers of the TV.

For ACER Revo 3610 users, you don't have to have any /etc/asound.conf or ~/asoundrc file in place, XBMC will work without them!

Please, just make sure you have the correct configuration in System -> System -> Audio Output.
In my case it's the following:

[FONT=Courier New]    <audiooutput>
        <ac3passthrough>false</ac3passthrough>
        <audiodevice>pulse:alsa_output.pci-0000_01_00.1.hdmi-stereo@default</audiodevice>
        <channellayout>0</channellayout>
        <customdevice>plughw:1,9</customdevice>
        <custompassthrough>plughw:1,7</custompassthrough>
        <dontnormalizelevels>false</dontnormalizelevels>
        <dtspassthrough>false</dtspassthrough>
        <mode>2</mode>
        <passthroughaac>false</passthroughaac>
        <passthroughdevice>alsa:iec958</passthroughdevice>
        <passthroughmp1>false</passthroughmp1>
        <passthroughmp2>false</passthroughmp2>
        <passthroughmp3>false</passthroughmp3>
    </audiooutput>[/FONT]

Good luck, I hope it helped and enjoy the great XBMC on ACER Revo 3610 running on Ubuntu 10.10!

---

### Post by ricey155 on 2011-02-19
worked a treat  :P

just about to watch a dl through my laptop and nothing, quick search and bingo sorted 

many thanks again to a great site keep the info coming :P

---

### Post by Skapunker on 2011-03-11
Thanks for this, worked perfectly with my asus at3iont-3 nvidia ion motherboard.

---

### Post by jainer123 on 2011-03-30
ivr,xmbcoholic - you guys are fantastic.  worked like a charm

---

### Post by drewuofu on 2011-07-17
hey guys, i am totally new to ubuntu, well, i understand some ideas about it, but, lets just say i am totally lost when i try to figure this out.  

i have the alasmixer but i....yeah, could you help me out a little more?  

how to do get this code to come up.  i couldnt find a "audio output" menu
-------------------------------------------------------------------------------------------------------------------------------

Please, just make sure you have the correct configuration in System -> System -> Audio Output.
In my case it's the following:

[FONT=Courier New]    <audiooutput>
        <ac3passthrough>false</ac3passthrough>
        <audiodevice>pulse:alsa_output.pci-0000_01_00.1.hdmi-stereo@default</audiodevice>
        <channellayout>0</channellayout>
        <customdevice>plughw:1,9</customdevice>
        <custompassthrough>plughw:1,7</custompassthrough>
        <dontnormalizelevels>false</dontnormalizelevels>
        <dtspassthrough>false</dtspassthrough>
        <mode>2</mode>
        <passthroughaac>false</passthroughaac>
        <passthroughdevice>alsa:iec958</passthroughdevice>
        <passthroughmp1>false</passthroughmp1>
        <passthroughmp2>false</passthroughmp2>
        <passthroughmp3>false</passthroughmp3>
    </audiooutput>[/FONT]

-----------------------------------------------------------------------------------------------------------------------------

attached is a screenshot of my alsa mixer, and i dont see anything that resembles what you guys talked about.

could you help out a newbie?

thanks!

---

### Post by jschlesinger on 2012-02-18
If this helps I just configured my Revo 3700 and the trick was to ssh to the device, run aplay -l to find the device (in my case card 1, device 3) and then update the custom device as plughw:1,3 on the system audio settings.

---

