---
title: "Mic records with scratchy sound"
date: 2012-12-05
forum: Multimedia Software
---

### Post by paradoja on 2012-12-05
Hi, I have an Asus Eee Pc 1005PEB wih Xubuntu 12.04, and it's been a while since I started having problems with my microphone. When I record my voice with Sound Recorder, or when I talk to somebody in Skype, I hear a scratchy sound besides my own voice, as if there was someone next to me making fried potatoes or something. Updating the ALSA driver ([https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)) improved sound quality and the scratchy sound has diminished, but it is not completely gone. I thought about changing my OS, but I tried other distros in its live version (Linux Mint, EasyPeasy, Debian, an older Ubuntu release) and it makes no difference. What can I do???

Thanks a lot.

---

### Post by silverhaze06 on 2012-12-07
could you possibly upload a sample piece of audio recorded from the mic? And is it always scratchy sounding even when the record volume is set low?

---

### Post by paradoja on 2012-12-10
Yes, even when the input volume is set low... Here is the sample: [http://www.mediafire.com/?eo5f17783w2lvtt](http://www.mediafire.com/?eo5f17783w2lvtt)
Thanks!!!!

---

### Post by AstroLlama on 2012-12-10
it could be that the mic volume is low, but the mic boost is very high. 

If this is the case try lowering the mic boost and raising the mic volume. this is possible through the volume settings, or through the command
```
alsamixer
```

---

### Post by silverhaze06 on 2012-12-10
> **paradoja said:**
> Yes, even when the input volume is set low... Here is the sample: [http://www.mediafire.com/?eo5f17783w2lvtt](http://www.mediafire.com/?eo5f17783w2lvtt)
Thanks!!!!

It actually sounds pretty average for a little built in microphone. So if lowering the boost or gain doesn't work, I wouldn't get too upset about it. The built in mic on my computer does the same thing i've noticed. They're not built for sound quality, but just so they work for voice and video chat and stuff like that.

---

### Post by paradoja on 2012-12-11
Thanks for your help. Yes, the mic boost is in zero, and the mic is high... 

Yes, you are right, it's not a great microphone, but anyway it's annoying to videochat with anyone with that scratchy bothering sound, and not even changing my OS seems to do the trick.

---

### Post by silverhaze06 on 2012-12-11
> **paradoja said:**
> Thanks for your help. Yes, the mic boost is in zero, and the mic is high... 

Yes, you are right, it's not a great microphone, but anyway it's annoying to videochat with anyone with that scratchy bothering sound, and not even changing my OS seems to do the trick.

Well if switching OS's doesn't solve the problem, then I would say the mic diaphragm might be slightly damaged, or something inside is causing static discharge. By other OS do you mean windows? Or another flavor of linux?

---

### Post by paradoja on 2012-12-23
Another flavor of linux, of course. I tried with Linux Mint, EasyPeasy, Ubuntu 10.10, Debian, Fedora (XFCE), and I think that's it...

Thank you for your help. After trying to solve the problem in so many ways I ended up thinking it IS a hardware problem.

---

