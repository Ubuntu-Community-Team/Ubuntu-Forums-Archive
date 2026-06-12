---
title: "No /dev/dsp ? ALSA @ 50% ?"
date: 2006-02-03
forum: Multimedia &amp; Video
---

### Post by xplode_me on 2006-02-03
Hi!

I guess this is my first post @ UbuntuForums.

I followed this post, [http://ubuntuforums.org/showthread.php?t=44753&highlight=alsa+duplex](http://ubuntuforums.org/showthread.php?t=44753&highlight=alsa+duplex) , to try and get my Audacity / Skype audio workin. Hasnt worked.

I already had sound using ESD, and i have sound using ALSA...

On the Select Audio Device @ Sound and Multimedia settings on KDE i've set ALSA, and it works, it does is thing :)

Now, the problem is... I have no /dev/dsp... Isnt it supposed for ALSA to work that I have  a DSP device? :|
As a consequence i get an error starting audacity and cant get to select ALSA on the programa preferences....

Can someone please help?

lsmod | grep snd

```

joel@supernova:~$ lsmod | grep snd
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm                78344  2 snd_via82xx,snd_ac97_codec
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  14 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  1 snd
joel@supernova:~$

```

---

### Post by FarEast on 2006-02-03
Hi,
Try loading the module 'snd-pcm-oss'.
Then '/dev/dsp' will appear.

---

### Post by xplode_me on 2006-02-05
yup it worked...

Thanx!

---

