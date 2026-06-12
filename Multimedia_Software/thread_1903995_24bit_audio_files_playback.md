---
title: "24bit audio files playback"
date: 2012-01-03
forum: Multimedia Software
---

### Post by Yahoé on 2012-01-03
My Asus motherboard uses an ALC892 sound chip. The built-in DAC supports 16/20/24-bit PCM format. I am using Precise Alpha1.

Can I play 24bit audio files without having them converted down to 16bit? I read that Pulseaudio wouldn't let me do that with the default settings, and using Alsa with Audacious 3.1, Audacious returns "snd_pcm_hw_params_set_format failed: Argument invalide." when setting the flow depth to 24, but works fine on 16.

---

### Post by BicyclerBoy on 2012-01-03
Yes you should be able to play 24bit..with alsa & the right applications..

Don't trust pulse audio to work yet..

Clementine 1.0 can play 24bit 96/192KHz.
But test with:
speaker-test -c 2 -r 48000 -F xxxx -D hw:0,1

where xxxx =[S8, S16_LE, S16_BE, FLOAT_LE, S32_LE, S32_BE]
try FLOAT_LE & S32_LE & S32_BE
& where hw:0,1 could be other devices..

Post back 
aplay -l

IMO Pointless playing 24bit with on-board soundcard using **analogue** output.

---

### Post by Yahoé on 2012-01-05
Thank you for taking the time to answer [BicyclerBoy]("http://ubuntuforums.org/member.php?u=816321").

Here are the results for speaker-test -c 2 -r 48000 -F xxxx -D hw:0,0:

[LIST]
[*]S8, FLOAT_LE and S32_BE all fail. Here is the message in French:"Le format d'échantillonage est indisponible à la lecture: Argument invalide. Échec de la configuration des paramètres matériel: Argument invalide"
[*]S6_Le, S32_LE and S32 tested OK and pink noise was heard.
[/LIST]
** aplay -l**
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: SB [HDA ATI SB], périphérique 0: ALC892 Analog [ALC892 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: SB [HDA ATI SB], périphérique 1: ALC892 Digital [ALC892 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 7: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 8: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: NVidia [HDA NVidia], périphérique 9: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0



So Audacious (Alsaand hw:0,0 ) returns "snd_pcm_hw_params_set_format failed: Argument invalide." when 24 and and "Foalting point" are selected, but works for 16 and 32.


What do you make of this? Why do you think 32bit playbacl works but not 24bit or floating?

---

### Post by BicyclerBoy on 2012-01-05
From my understanding..this means that the audio codec/driver interface only accepts 32bit data for 24bit audio.
The driver/codecs do not always support all data formats.

S/PDIF 24bit audio data stream is 32bit with zero padding bits..

I seriously doubt the onboard soundcard will 'sound' any better with 24 bit &/or rate up-sampling unless you use S/DPIF connection to external DAC/amp.

The best you can achieve is using HDMI audio (discrete 8x 192KHz/24bit + HDA formats)

If you can not use HDMI then S/PDIF is the only option..
For example.. hw:0,1 is mobo S/PDIF with amp max 96KHz
```

#/etc/asound.conf
# best SQ alsa re-sampler  package libasound2-plugins
defaults.pcm.rate_converter "samplerate_best"

# force max clock 32 bit spdif
pcm.iec958_32 {
type plug
slave {
pcm "hw:0,1"
format S32_LE
rate 96000
}
}

```
Clementine 1.0 audio config is set to alsa pcm.iec958_32

---

### Post by Yahoé on 2012-01-05
Great, thanks for the info.

It seems that an external DAC is the way to go, now I have some researching to do since there are so many products available.

Merci beaucoup!

---

### Post by BicyclerBoy on 2012-01-05
You just need to get your audio as digital data out of the PC..

I would not waste money on an external DAC. Most are worse than mobo soundcard because they are:
- USB
- only 96KHz or less
- some can not do 24bit.
- only 2 ch stereo
- you need linux support..
- worse design than mobo soundcard
- expensive (over priced)

Your HDMI video card (with AVR HT amp) will dance all over any external DAC less then US2K.

Reclocking in the amp is the key.

You have to have a good amplifier so why not get one with HDMI & ethernet

This is adequate..
Marantz SR7005
Sadly I didn't get one for Xmas..

---

### Post by Yahoé on 2012-10-17
I forgot about this thread, sorry.

Thanks for your input on the Marantz SR7500, but at 1850 CAD...

Anyhow after much Web searching I bought 6 months ago a GrantFidelity TubeAC-11 D/A Converter[SIZE=2] that is a very fine piece [SIZE=2]of electronics indeed. Multiple inputs and outputs[/SIZE], and [SIZE=2]for only [/SIZE]350 USD, you could [SIZE=2]easily pay 2000 $ for a similar product.
[SIZE=2]It works out of the box with Ubuntu using the digital ou[SIZE=2]t.

[SIZE=2]http://shop.grantfidelity.com/Grant-Fidelity-TubeDAC-11-D-A-Converter.html

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

