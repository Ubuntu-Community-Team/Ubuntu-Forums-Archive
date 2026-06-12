---
title: "Sound problem with HDA Intel AD1986A chip"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Turin Turambar on 2006-08-06
I have a sound when I enter Ubuntu... well, sort of. Sometimes a high pitched noise in the background with the login sound can be heard together.
However, what's worse, if I open any folders in nautilus or do something in Ubuntu, sound is gone.

I also noticed that in Volume, there's no "Master" or "General", it seems that "Headphones" control the main volume?! WTF? I don't have any headphones! But whatever, if I pull the lever up or down when the initial login sound is played, it will stop immediately.

Any solutions? Something's bad here.

---

### Post by Turin Turambar on 2006-08-07
Anyone? :confused:

---

### Post by muep on 2006-09-02
I have exactly the same problem on a computer I bought yesterday. It has an Asus P5LD2 SE motherboard with an Intel 945P chipset. The sound chip is similar to yours. I have tried a few different distros and the problem seems to be everywhere.

Does anybody have a solution to this?

If not, I think I'll need to get a separate sound card for my computer. Any help or another confirmation would be appreciated, though.

---

### Post by Turin Turambar on 2006-09-04
> **muep said:**
> I have exactly the same problem on a computer I bought yesterday. It has an Asus P5LD2 SE motherboard with an Intel 945P chipset. The sound chip is similar to yours. I have tried a few different distros and the problem seems to be everywhere.

Does anybody have a solution to this?

If not, I think I'll need to get a separate sound card for my computer. Any help or another confirmation would be appreciated, though.

Unfortunately, seems that the two of us are the only one with that problem. :( Sorry, I didn't find the cure.

However, Dapper seems to cause sound problems on many machines (at least from what I've read), yet Breezy is working fine. I didn't test Breezy on that PC though.
We can only hope that Edgy will have sound fixed.

---

### Post by fanta on 2006-09-26
Exactly the same problem, an ear-killing high pitched sound on the login sound and when I change the volume the sound is gone until next reboot.

Samsung R55 Chedsuma Notebook here. HDA Intel AD1986A Chip just like yours.

Anyone got a solution for this now? Or tried if it got fixed in an Edgy version?

---

### Post by mcmc on 2006-09-30
Try putting the following into a new file inside /etc/modprob.d/ folder (call is sound or something):
"options snd-hda-intel position_fix=1 model=3stack"

(without the quotes)

Then run 

```
sudo update-modules
```

and reboot

HTH

---

### Post by hegex on 2006-10-04
I think i have same thing on my laptop, but no sounds at all. But i found this and i hope this will help us. 
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by Max-B on 2006-10-17
> **Turin Turambar said:**
> Unfortunately, seems that the two of us are the only one with that problem. :( Sorry, I didn't find the cure.

I have exately the same problem. I tryed to open alsamixer and move some level with the result that the sound is gone (even after the reboot).

Does anybody tryed the solution of mcmc. I will try this afternoon and let you know.

Max-B

---

### Post by valmy on 2006-10-17
Ok, I just tried mcmc's advice and it works! Thank you!

---

### Post by gunavara on 2007-01-22
mcmc, you're the man!

---

### Post by daemonk on 2007-02-21
Thanks very much, sorted me out.

My Spec - Samsung M70 running Kubuntu Feisty

---

### Post by Tourmaline on 2007-04-01
I had exactly the same problem on an Asus P5PL2 SE mainboard with ADI1986A sound chipset. The solution given by MCMC worked great for my mainboard too. Thank you very much MCMC.

---

### Post by Dapman01 on 2007-12-02
> **mcmc said:**
> Try putting the following into a new file inside /etc/modprob.d/ folder (call is sound or something):
"options snd-hda-intel position_fix=1 model=3stack"

(without the quotes)

Then run 

```
sudo update-modules
```

and reboot

HTH

What do you mean by "call is sound or something"
are we suppose to create a completely new text file or modify an existing one

---

### Post by bobbybobington on 2007-12-21
:guitar:THANK YOU THANK YOU THANK YOU THANK YOU:guitar:

:KS:KS:KSupdated to newest version of alsa and worked like a charm :KS:KS:KS

---

