---
title: "No Digital Input Source"
date: 2009-04-24
forum: Multimedia Software
---

### Post by K3N8 on 2009-04-24
Hi,

Since installing Jaunty I am not able to set my microphone settings to "digital mic". It is just gone?!

It all worked out of the box on Intrepid?!

My system is:

HP dv-7 1120 ed
STAC92xx soundcard

Does anybody have a solution?

Gr, Alexander

---

### Post by mavk84 on 2009-04-24
> **K3N8 said:**
> Hi,

Since installing Jaunty I am not able to set my microphone settings to "digital mic". It is just gone?!

It all worked out of the box on Intrepid?!

My system is:

HP dv-7 1120 ed
STAC92xx soundcard

Does anybody have a solution?

Gr, Alexander

same problem... mine is HP dv-7 1130el

---

### Post by drmaas on 2009-04-26
Same problem here, same system specs except I have dv5-1120us.  The only options available to me in the "options" tab for setting input are "Mic" and "line", neither of which allow me to capture sound with gnome-sound-recorder.

---

### Post by drmaas on 2009-04-26
My alsa-info.sh output can be found here: [http://www.alsa-project.org/db/?f=ab1dbbed0f65b74579ef9ff3aa2790ed55e7a494](http://www.alsa-project.org/db/?f=ab1dbbed0f65b74579ef9ff3aa2790ed55e7a494)

card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 

Shows up under APLAY, but not ARECORD.  This might be why I do not have a digital input field available in gnome-volume-control.  Frustrating, since the digital input worked fine in intrepid.

---

### Post by mavk84 on 2009-04-28
I tried adding options to alsa config but it didn't work; well it partially worked: now I have digital mic 1 in the options tab but I stil don't have Digital mic 1 as recording source... so that wasn't a good solution I think. (just for the record I set mode=ref to obtain this)

---

### Post by drmaas on 2009-04-29
I tried upgrading to alsa 1.0.19, and that did not solve the problem.  I also uninstalled pulse audio.  So, I began to suspect that the problem was in the way ubuntu loads the 2.6.28.11 kernel, or the kernel itself.  

Sure enough, I booted into 2.6.27-11, and my sound settings magically resolved to what I was using in version 8.10!  The digital microphone settings reappeared, and everything worked perfectly.  I even reinstalled pulseaudio, and everything still worked.

Does anyone know how to go about logging this as an issue with kernel 2.6.28-11?

-Dan

---

### Post by mavk84 on 2009-05-02
> **drmaas said:**
> I tried upgrading to alsa 1.0.19, and that did not solve the problem.  I also uninstalled pulse audio.  So, I began to suspect that the problem was in the way ubuntu loads the 2.6.28.11 kernel, or the kernel itself.  

Sure enough, I booted into 2.6.27-11, and my sound settings magically resolved to what I was using in version 8.10!  The digital microphone settings reappeared, and everything worked perfectly.  I even reinstalled pulseaudio, and everything still worked.

Does anyone know how to go about logging this as an issue with kernel 2.6.28-11?

-Dan

that would be a problem for me because I have set my root partition to ext4 so i have to use the new kernel. I hope that with an update the problem will be solved. Thanks anyway:)

---

### Post by drmaas on 2009-05-05
I posted a bug for this on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369648](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369648)

---

### Post by K3N8 on 2009-05-08
> **drmaas said:**
> I posted a bug for this on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369648](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369648)
Hi,

Thanks a lot for all your input! Now lets hope that the bugreport helps. In the meantime we can at keast use the "old" kernel.

Gr. Alexander

---

### Post by mavk84 on 2009-07-02
Hi guys I solved this problem adding to alsa-base.conf 

options snd-hda-intel model=hp-dv5 enable_msi=1

Now it works perfectly. I hope it helps. 
:p

---

### Post by K3N8 on 2009-07-02
Thankx! It worked.

---

