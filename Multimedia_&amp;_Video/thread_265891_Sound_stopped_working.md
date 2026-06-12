---
title: "Sound stopped working"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by zileas on 2006-09-26
Hi I installed Ubuntu last week and I don't understand Linux very much but I'd love to learn it :) my problem is that my sound has gone, it worked when I intalled Ubuntu and some days later but now it doesn't work... I followed the sticky guide but...

I'm on an Aspire 1690 series laptop and everything has been working fine except the sound.

Thanks :)

---

### Post by raphha on 2006-09-26
Hi there and
well... not much information from your side so far, so maybe just try the most common things:
[LIST]
[*]check that the speakers aren't muted (software, maybe hardware switch)
[*]check the volume position, turn it up
[*]check that you are a member of the audio group by entering
[INDENT]"cat /etc/group | grep 'audio.*<yourusername>' [/INDENT]
You should see a line starting with "audio" and your name should there.[/LIST]
If nothing helps, come back with more info, what did you change? when exactly have you lost your sound?

good luck,
raph

---

### Post by mwtoews on 2006-09-30
No sound here either. It stopped after an updated, which I recall loaded a new kernel image. My uname -a give me:
Linux hal 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686 GNU/Linux
My sound card had to be manually configured, many months ago, but worked great. I had to add: snd_es18xx to /etc/modules and create a /etc/modprobe.d/snd_es18xx.modprobe file with "options snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=0 irq=5 fm_port=0x388"

Yes, speakers are turned on, cables connected. Also 'alsaconf' and 'alsamixergui' don't see any sound device. What did the new kernel do? Can I retrograde? There are other related threads in the past few days, is there a main thread/solution?

Many thanks!

---

### Post by mrhelpman on 2006-09-30
I may not be any help but are there any other devices in the machine that could be defined as sound cards?  On my machine I have a sound blaster live and a web cam with a microphone and I had a problem where the kernel would sometimes assume that the web cam, with its microphone, was the sound card. I fixed this by putting the following file in the /etc/modprobe.d directory. I don't think the name of the file is important as long it is in  the directory.

file: sound-conf:
# set the sound blaster live to be default sound card

alias snd-card-0 snd_emu10k1
alias sound-slot-0 snd_emu10k1
options snd_emu10k1 index=0

# set the web cam to be the secondary sound card

alias snd-card-1 snd_usb_audio
alias sound-slot-1 snd_usb_audio
options snd_usb_audio index=1

---

