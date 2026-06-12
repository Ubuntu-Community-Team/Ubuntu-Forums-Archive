---
title: "[HELP] Getting sound card Ensoniq 1370 to work"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by TheEdge2 on 2005-11-02
G'Day,

- I installed Ubuntu 5.10 and only then discovered that I actually wanted KDE instead of Gnome so I followed the instructions on the Kubuntu site and everything seemed to work except the sound card
- Now each time I log into KDE I get the following from artsmessage - "Error while initializing the sound driver device:default can't be opened for playback"
- And yes there is no /dev/default however parts of this are working.
- For instance lspci reports:

0000:00:13.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]

so the sound card is being detected

- lsmod reports that the modules are there:

snd_ens1370            17632  0 
snd_rawmidi            22816  1 snd_ens1370
snd_pcm                78344  2 snd_ens1370,snd_pcm_oss
snd_page_alloc         10120  2 snd_ens1370,snd_pcm
snd_ak4531_codec        7808  1 snd_ens1370
snd                    48644  8 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
es1370                 29228  2 
gameport               14472  3 snd_ens1370,es1370
soundcore               9184  4 snd,es1370

the modules are being loaded

- I have ensured that my speakers are on and that sound is enabled ;) 
- However I am getting no joy when going to the Hardware tab in"Sound & Multimedia - System Settings" and selecting Autodetect or ALSA
- Can anyone point me in the right direction please?
- I would be more than happy to provide any other debugging information required

TIA

---

### Post by jgibson on 2006-03-05
Have you had any luck with this? I have the same problem with an ES1370 running breezy. Everything looks fine (modules etc.), the tests run in the multimedia systems selector, but I get nothing out of the speakers or in through line-in.

---

