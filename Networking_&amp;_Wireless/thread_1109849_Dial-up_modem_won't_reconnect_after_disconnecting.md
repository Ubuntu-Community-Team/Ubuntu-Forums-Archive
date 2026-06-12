---
title: "Dial-up modem won't reconnect after disconnecting"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by luzy on 2009-03-29
Hi!

I am (unfortunately) connecting to Internet via dial-up on my laptop. I use gnome-ppp. The first time after booting my laptop, everything works fine. (The only strange thing is that I can't hear the modem although I chose volume high in the gnome-ppp configuration.)

But when I disconnect and try to reconnect later, I get a message "Can not open modem". When I open the log, it says "device or resource busy". So far, I found no other solution than a reboot :(

Could you please help me to figure out, what's going on?! I'm not an expert :(

Thank you!!!

Luzy

P.S.: I don't know what information you need, here is some info:

lspci:
...
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
...

lsmod:
...
snd_intel8x0           37532  3 
snd_ac97_codec        111652  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
p54pci                 17408  0 
battery                18436  0 
snd_rawmidi            29824  1 snd_seq_midi
p54common              20096  1 p54pci
evdev                  17696  10 
tifm_7xx1              13824  0 
mac80211              216820  2 p54pci,p54common
...

---

### Post by _duncan_ on 2009-03-29
There is a known bug with the sl-modem-daemon package with Ubuntu 8.10 (Ibex). The workaround is to enter the following code in a terminal before reconnecting:

```
sudo /etc/init.d/sl-modem-daemon restart
```

---

### Post by luzy on 2009-03-29
Thanks for your fast answer and the easy solution, _duncan_ !! :) You are saving me lots of time, now I won't have to restart my laptop every time I want to reconnect!!! Thanks!!!

If I wanted to avoid having to restart the sl-modem-daemon manually, is there a way to add it to some script or so?

Since you seem to be an expert, do you have maybe any idea why I can't hear my modem? I know the dial-up sound is annoying, but at least I would hear if it connects at a decent speed without having to look at the log...

Thanks again!

Luzy

---

