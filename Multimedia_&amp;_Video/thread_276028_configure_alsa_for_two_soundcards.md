---
title: "configure alsa for two soundcards"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by felixj on 2006-10-12
I have two soundcards, one crappy onboard card (ac97) and a better one (ice1712). Both cards work, but just one at a time. What I want to do is play all music etc. with the better pci-card that is connected to my stereo and use the onboard-card for a headset. I get both card to work by just running alsaconf, but - as I said - just one at a time.

Following modules are loaded (which should be sufficent):
```
lsmod | grep snd
snd_ice1712            54212  0
snd_ice17xx_ak4xxx      4064  1 snd_ice1712
snd_ak4xxx_adda         5920  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              8512  1 snd_ice1712
snd_ac97_codec         82720  1 snd_ice1712
snd_pcm_oss            35968  0
snd_mixer_oss          15872  1 snd_pcm_oss
snd_pcm                74532  3 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              20836  1 snd_pcm
snd_page_alloc          9512  1 snd_pcm
snd_ac97_bus            2368  1 snd_ac97_codec
snd_i2c                 5344  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         7520  1 snd_ice1712
snd_rawmidi            22560  1 snd_mpu401_uart
snd_seq_device          7756  1 snd_rawmidi
snd                    48100  12 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9216  1 snd

```

After searching a lot through forums etc. I found out that a .asoundrc-file might just be the solution, so I created one. This his how it looks like:
```
# Start ~/.asoundrc
pcm.ice1712 	{ 
		type  hw  
		card 0 
		}

ctl.ice1712 	{ 
		type  hw  
		card 0 
		}

pcm.ac97 	{ 
		type  hw  
		card 1 
		}

ctl.ac97 	{ 
		type  hw  
		card 1 
		}

# End ~/.asoundrc

```

Still, just one card at a time working. What I want is that skype lets me choose between my two cards.

Any help is appreciated.
felixj



EDIT
Solved the problem myself, should have read through the sound-guide.
A quick
```
cat /proc/asound/modules
```
showed me that other than I expected only one card was present. So I modprobed the other module and everything is fine.

---

