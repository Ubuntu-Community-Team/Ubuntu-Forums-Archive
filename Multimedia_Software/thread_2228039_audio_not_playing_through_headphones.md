---
title: "audio not playing through headphones"
date: 2014-06-05
forum: Multimedia Software
---

### Post by jitendra8911 on 2014-06-05
Hi all,

I am using DELL alienware m14x. I have installed ubuntu 14.04 on my laptop. The problem that I am facing is that the audio plays only through speakers all the time even I though i plugin my headphone. When I go to sound settings it is showing me headphones in the "play sound through" which means that my system is able to detect the headphones but just the audio doesn't play through the headphones, instead it still plays through speaker. Can anyone one help me to figure it out please !

Thanks and Regards,
Jitendra

---

### Post by soodvarun78 on 2014-06-06
In alsamixer command is  it showing headphones ?
have you tried with another headphone. This can happen if your headphone is not detected.

---

### Post by jitendra8911 on 2014-06-06
Hi Varun,

No. alsamixer is not showing the headphones. Yes I have tried with other headphones as well but no luck.

---

### Post by soodvarun78 on 2014-06-07
Hi Jitendra,

Which codec is there on you setup. 
Give the command aplay -l, which will display the codec type on your system.
There could be some problem with codec software on your system.
Just see if the correct codec software is installed on your system 
you can do 
lsmod | grep snd 
to see the codec module installed and match it with codec in aplay -l, if correct codec and software is installed.

---

### Post by stjake92 on 2014-08-06
I've been having this same exact problem, I have an Alienware M14x R2 running Windows 8,1 and Ubuntu 14.04 and I've tried everything to get my headphone jack to work. Plug in my headphones and nothing, not recognized, nothing. I typed in the terminal commands you mentioned and heres the information on my machine:

> jackson@jackson-Ubook:~$ lsmod | grep snd
snd_hda_codec_ca0132    36082  1 
snd_hda_intel          43885  3 
snd_hda_codec         188649  2 snd_hda_intel,snd_hda_codec_ca0132
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97609  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61519  0 
snd_seq_device         14497  1 snd_seq
snd_timer              29427  2 snd_pcm,snd_seq
snd                    73602  14 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_ca0132
soundcore              12680  1 snd
jackson@jackson-Ubook:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jackson@jackson-Ubook:~$ 



I'm dying to fix this problem because I love Ubuntu 14.04 running on my laptop, it works great now that I've fixed the battery drain issue.

---

### Post by Johnathan_Blasquez on 2014-08-06
I have had a really similar problem. It was actually the headphones that I was using. [Try using other seo headphones, I hope that]("https://www.learnseoclass.com") fixes the problem.

---

