---
title: "sound doesn't &quot;go through&quot; JACK to JACK Rack"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by zweistein on 2006-06-27
Hi folks!

First of all, I think it's brilliant we have a project like Ubuntu Studio. I'm sure it makes hordes of bedroom (and other, of course!) musicians really happy.

I'm currently trying to set up the system to process my electric guitar input, because I don't own an amp or any pedal effects. I installed JACK, JACK Control and JACK Rack and it seems everything went fine. But, when I load JACK Rack and apply some effects, instead of hearing the effects applied, I get the same ol' sound I had in the first place, without JACK Rack. I've connected JACK Rack and ALSA output, as well as ALSA Input and JACK Rack - alsa_pcm capture_1 with jack_rack in_1 & in_2, and jack_rack out_1 & out_2 with alsa_pcm playback_1. 

The weird thing is - in the Volume Control panel, I have two devices - an ALSA device (VIA 8237), which is my actual soundcard, and an OSS device (CMI9761). I have the ALSA driver selected in the JACK Setup. I'm not really sure about the input/output channels I selected, but I've tried all possible combinations without any luck.

I'm running Ubuntu 6.06 - any help? :) If you need some other information, I'll be glad to post them.

Thanks for your time!
Nikola

---

### Post by zettberlin on 2006-06-27
can you play anything (like alsapayer or zynaddsubfx) via jack?

---

### Post by zweistein on 2006-06-27
[QUOTE=zettberlin]can you play anything (like alsapayer or zynaddsubfx) via jack?[/QUOTE]

Zynaddsubfx plays just fine. I can hear the sound when I'm in JACK Rack, but I just don't hear the effects.

---

### Post by zettberlin on 2006-06-27
OK, so you have connected alsa_pcm in (that is: your guitar) to jackrack_in and then  jackrack_out to alsa_pcm out (that is, the same port. zynadd works with) ?

BTW: maybe there is trouble with jackrack? what about ecamegapedal, creox or ams?

---

### Post by zweistein on 2006-06-27
[QUOTE=zettberlin]OK, so you have connected alsa_pcm in (that is: your guitar) to jackrack_in and then  jackrack_out to alsa_pcm out (that is, the same port. zynadd works with) ?[/QUOTE]

Yup, that's right.

> BTW: maybe there is trouble with jackrack? what about ecamegapedal, creox or ams?

Tried it with Creox, too... Couldn't get it to work, either. I hear the sound, but with no effects. It's like the sound isn't running through JACK (or ALSA) at all. Kinda frustrating, ain't it? ](*,) :) 

The one thing I noticed, which may be interesting, is that I can't mute the microphone input from the Volume Control panel. I tried it in both OSS and ALSA, but it still pays if I mute it. Output (playback) control works from ALSA Volume Control panel, though.

---

### Post by zettberlin on 2006-06-27
[QUOTE=zweistein]
The one thing I noticed, which may be interesting, is that I can't mute the microphone input from the Volume Control panel.[/QUOTE]

Yeah - sounds like a mixer/routing/hardware - thing. Maybe the input is hardwired to the output (though this apeares quite stupid...)

---

### Post by sinpalabras on 2006-09-20
i have the same problem,exactly.Some times i can plug the guitar and ear something but if i reboot i have to play around on alsamixer or gmixer to be able to ear it. creox never worked (just ear the delay effect when i press play,  butt the guitar did not make it though)(pop effect)jack rack is what i want,but no sound whatsoever. my machine is:
athon64 2800+ s754
mother asrock upgrade
768 mb ram 
80gb hd sata western d
via 8237 buil in sound card
ubuntu 6.06 amd64 bit
 I wonder if there is a how-to on jack and jack-rack?
tanks in advance, and sorry for my english
saludos
 from argentina

---

