---
title: "problem with sound AC'97 sis at 7.04"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by cyb3rm4n_pl on 2007-07-28
Hi all

i need help . i have ubuntu 7.04 . I install everything ( Alsa etc. ) . Today i don't have sound . I reinstall Alsa . Nothing . When i go to system -> administration - > sound and ubuntu stops . I have to turn off . i don know what to do . Please help me . 


Sory but my english is not so good like few years ago :/ 



ALSA lib setup.c:334:(snd_config_get_ctl_elem_value) bad value type
ALSA lib pcm_params.c:2152:(snd_pcm_hw_refine_slave) Slave PCM not usable


and cat /proc/asound/cards  output 


 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with CMI9738 at 0xdc00, irq 10

---

### Post by adrian.salceanu on 2008-04-27
Hi
I was having a similar problem with an AC 97 sound card. The sound worked for a while and then suddenly stopped. I searched around, but no answer. But after putting together various pieces of information, it turned out that the problem was caused by a kernel (or maybe some software update) which muted certain components for the sound system.
My solution: run "alsamixer" in terminal and search for any components displaying "MM" -> they are muted. Just click the key "m" on them, and they will be unmuted.
Problem solved!
I hope it will work for you too!

---

