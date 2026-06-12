---
title: "No sound: audigy 4"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by freek sanders on 2006-02-17
Recently I bought the Creative Audigy 4 (non-pro) sound card. Everything worked fine under windows xp. However, under ubuntu it doesn't. 

I have a customized kernel, so I turned on two of the drivers, which were possibly related to my sound card (a.o. emu10k1). I rebuild the kernel, and rebooted to my new kernel.

The problem is, that I don't know how to make Ubuntu use my new 5.1 sound card instead of the one that was in there during installation (a onboard sound card).

Do I need to reconfigure ALSA, and how?:confused: 

extra info:
lspci:
0000:01:09.0 Multimedia audio controller: Creative Labs: Unknown device 0008

---

### Post by jeremytaylor on 2006-02-17
you could try 
```
sudo alsaconf
```
and see if your card shows up. 

However I'm not sure the version of alsa that comes with breezy supports your card yet... they don't support my audigy 2 sz notebook either. 

You could give the following a try, 
[https://wiki.ubuntu.com/HowToSetupSoundBlasterAudigyInBreezy?highlight=%28audigy%29](https://wiki.ubuntu.com/HowToSetupSoundBlasterAudigyInBreezy?highlight=%28audigy%29)
again you'll need to run alsaconf afterwards to select that card and not the onboard one. 

hope you get it working (I'm still struggling with mine)

Jeremy

---

### Post by freek sanders on 2006-02-17
Thanks for the reply.

I looked into the wiki, and am sure I must use the snd-emu10k1 module.
However, 'modprobe snd-emu10k1' gives me:
FATAL: Module snd_emu10k1 not found.
FATAL: Error running install command for snd_emu10k1

(this means he can be found, since 'modprobe non-existant-driver' only gives:
FATAL: Module non_existant not found (without the second line)

find /lib/modules/`uname -r`/ | grep emu10k gives:
/lib/modules/2.6.12-audigy-hibernate/kernel/drivers/input/gameport/emu10k1-gp.ko

Can anyone help?

PS: I have emu10k1 turned on in the kernel
PS2: alsamixer shows up my old ac97 card
PS3: I do not have alsaconf, and am unsure how to install it

---

### Post by jeremytaylor on 2006-02-17
I think alsaconf might be in the alsa-utils package. Should be in the repos. 

The driver you need is the emu10k1 as you suggest (at least according to the alsa site). Try following the wiki instructions but in the reconfigure step select the emu10k1, or if that doesn't work use all. 


jeremy

---

### Post by alexal on 2006-02-19
i have buyed a audigy 4 non pro too and i dont have sound i have done what the how to soundblaster audigy says but i have no sound. If you have any ideas how to make it work please post.It recognizes my audigy 4 as audigy 2 value[unknown] and its not muted.thx

---

