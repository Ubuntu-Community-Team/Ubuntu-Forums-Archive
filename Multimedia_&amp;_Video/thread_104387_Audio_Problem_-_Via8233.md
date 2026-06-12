---
title: "Audio Problem - Via8233"
date: 2005-12-16
forum: Multimedia &amp; Video
---

### Post by pherseu on 2005-12-16
Hi, I have an onboard soundcard VIA 8233 and I can hear all sounds, but can't hear/record MIC. 

My mic device is not mute (max. vol), Mic Boost is activated at alsamixer.
In alsamixer, when I hit <TAB> to see the capture controls, I can note that something is weird:
Above < Mic > I have:
[COLOR="Red"]L[/COLOR][COLOR="White"]..........[/COLOR][COLOR="Red"]R[/COLOR]
[COLOR="Red"]CAPTUR[/COLOR]



I have no more ideas, All mixers are showing that 'mic' is activated but I still can't record. Obs: my mic is OK and connected ;)

I'm using UBUNTU 5.10 kernel 2.6.12-10-386

a part of my lsmod:

[COLOR="SlateGray"]snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  1
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  2 snd
i2c_viapro              7696  0
i2c_core               19728  2 i2c_acpi_ec,i2c_viapro[/COLOR]


ANY HELP IS WELCOME.
Well, sorry the spelling, that's all folks.

---

### Post by cvmostert on 2005-12-30
hi there, you are lucky, i can not even get a sound out of my via vt8233 onboard soundcard!

i have a question; did your sound work from the beginning after installing ubuntu or did you have to set it up?

---

### Post by kingzasz on 2005-12-31
I had the same problem.

Move over to capture after you press tab, and press the up arrow key to turn up the volume.  Then press Space so you see L  R Capture thingy next to the volume level.

See this page:

[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

---

### Post by cvmostert on 2005-12-31
i also tried the capture thingy, and still nothing... dunno... dont want to install win to check it...

---

### Post by anil_robo on 2006-03-11
I was able to record sound in Breezy after much effort. It took me almost 3 months but finally I was able to record sound successfully and predictably well in Breezy.

Come dapper, and no sound! Again! :(

I'm muted again! Could someone tell me why this again? :(

---

### Post by xplode_me on 2006-03-24
I have the  VT8233 chipset, and sound on dapper, right from the beggining. I just can't record anything from the MIC input, cause it records the mic sound, AND lots and LOTS of "static" noise ... :( someone has an answer?

---

### Post by xdonut on 2006-04-05
I can't hear any sound at all, and Ubuntu says I don't have any sound devices, although the vt8233 shows up in the device manager. :/
Any help appreciated.

---

