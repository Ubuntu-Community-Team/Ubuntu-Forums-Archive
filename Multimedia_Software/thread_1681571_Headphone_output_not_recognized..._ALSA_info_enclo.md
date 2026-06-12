---
title: "Headphone output not recognized... ALSA info enclosed!"
date: 2011-02-04
forum: Multimedia Software
---

### Post by danyellenik on 2011-02-04
I've been getting the hang of ubuntu. It's been a good switch from windows 7.

I'm having a bit of an issue which right now is causing me to regret deleting my windows partition. It'd be nice to have my dual boot set up right now.

Ubuntu is not recognizing my headphone output on my laptop. 

I've been looking around but can't find a fix. Here's my alsa info script output. Thanks

Also, I'm running 64-bit ubuntu if that matters.

[http://www.alsa-project.org/db/?f=9b70ab0af420bbd4e3b1815751033a1e0bb0539f](http://www.alsa-project.org/db/?f=9b70ab0af420bbd4e3b1815751033a1e0bb0539f)

---

### Post by danyellenik on 2011-02-04
I've been tweaking things and playing around trying fixes all over the net. I need this working....i now have no sound at all, ubuntu wont recognize my sound card

NEW Alsa info file: [http://www.alsa-project.org/db/?f=b7a295e8f0aead1157912253e065a0ff7e887a0e](http://www.alsa-project.org/db/?f=b7a295e8f0aead1157912253e065a0ff7e887a0e)

---

### Post by Yellow Pasque on 2011-02-05
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)
BTW, your new alsa info shows that you borked your install somehow (no alsa kernel module loaded) :\

---

### Post by lidex on 2011-02-05
Probably a good idea to get alsa driver reset:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
Then add this to alsa-base.conf:
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` 
**Reboot.**
No joy? Check out linuxant as per Temüjin above. Reference:
[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

---

### Post by danyellenik on 2011-02-07
> **lidex said:**
> Probably a good idea to get alsa driver reset:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
Then add this to alsa-base.conf:
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` 
**Reboot.**
No joy? Check out linuxant as per Temüjin above. Reference:
[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

Lidex!! You my friend are a god. I've seen your solutions numerous times and knew I could count on these forums for an easy fix! Thank you so much. Headphone jack works great and mutes internal speakers when it's active.

Cheers

---

### Post by Su4p on 2011-03-08
Nice ! thank's a lot ! It worked for me too. ASUS k452

---

### Post by azeemj on 2011-03-09
I have the same problem but my machine is dell optiplex 380 optiplex
64 bit ubuntu 10.04 
problem is that sound on speaker hear but on headphone no sound

kindly if someone know help me plz!!!!!

regards
azeem

---

### Post by Yellow Pasque on 2011-03-09
@azeemj: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/588031](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/588031)

---

### Post by azeemj on 2011-03-12
> **Temüjin said:**
> @azeemj: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/588031](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/588031)
Dear [Temüjin]("http://ubuntuforums.org/member.php?u=327594")

very good reply and good help thank you very much so nice of you 


azeem

---

