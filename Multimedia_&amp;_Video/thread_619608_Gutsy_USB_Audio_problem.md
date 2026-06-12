---
title: "Gutsy USB Audio problem"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by danmiddle2 on 2007-11-21
Hi there,

I am having soundcard woes with GUTSY. I have an HDA-INTEL card onboard, which I have frankly given up with. It worked fine on edgy; then on Feisty I had to manually recompile ALSA with the appropriate options set and on GUTSY I have had to recompile ALSA, disable ACPI and then only get very crackling audio. So I have given up on that.

I have no free expansion slots, so I purchased a USB sound card which works pretty much out of the box in Xine movie player. Unfortunately nothing else plays sound.

I have done some digging and I believe the problem is that the card is not assigned as card0:

cat /proc/asound/cards
 0 [CX8811_1       ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xf9000000
 1 [CX8811         ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xfc000000
 2 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:00:13.0-1, full speed

How do I make it card0?

I think I need to edit: /etc/modprobe.d/alsa-base

I have tried various settings, but it currently looks like this (well, the relevant part, anyway):

#options snd-usb-audio=-2
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
#options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2
#options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



Many thanks

Dan

---

### Post by danmiddle2 on 2007-11-21
a little more info:

every time I set 
options snd-usb-audio index=0

then it fails to load the usb sound card at all!?

if I set;
options cx88-alsa index=2

then I get 1 of my cx88 as card 2, the usb as card 1 and cx88_1 as card 0.

how do I implicitly set cx88 to be both 1 & 2 ? I have tried adding:

options cx88-alsa index=1
options cx88-alsa index=2

that doesn't work at all.

any ideas welcome

Many thanks

Dan

---

### Post by danmiddle2 on 2007-11-21
ok; changing the entry to;

options cx88-alsa index=1,2

and #ing out the ones for usb-audio seems to have done the trick. as below;

cat /proc/asound/cards
 0 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:00:13.0-1, full speed
 1 [CX8811         ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xfc000000
 2 [CX8811_1       ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xf9000000

Unfortunately it still isn't working. Sound seems to be really low quality again (fuzzy). alsamixer will not let me adjust the volume.

alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by kessaris on 2008-07-02
Hi, have you managed to work out your problem?

I'm also trying to get a cx88 card working.

Where did you add these settings? in /etc/modprobe.d/alsa-base and just restart?

Sorry to be repeating what you may have already written like two years ago, but desperate times..

---

### Post by danmiddle2 on 2008-07-02
> **kessaris said:**
> Hi, have you managed to work out your problem?

I'm also trying to get a cx88 card working.

Where did you add these settings? in /etc/modprobe.d/alsa-base and just restart?

Sorry to be repeating what you may have already written like two years ago, but desperate times..

I did get it working. I still have problems with adjusting the audio... but the quality is good and I got it to a level that was fine. As it's a mythtv box, I adjust the volume of the TV to bypass that issue.

I honestly can't remember where I added those settings, but I will have a dig around tonight when I am in front of that computer and will post here later.

---

### Post by kessaris on 2008-07-03
I'd really really appreciate it.

I'm recompiling my kernel tonight to ensure it's got the latest ALSA driver support for this module.

To be perfectly honest, I'll be over the moon if it works.  That means the only thing that's not operational will be my card reader!

---

