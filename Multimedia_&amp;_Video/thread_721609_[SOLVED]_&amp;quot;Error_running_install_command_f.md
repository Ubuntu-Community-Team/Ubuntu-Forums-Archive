---
title: "[SOLVED] &amp;quot;Error running install command for nvidia&amp;quot;"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by abalone on 2008-03-11
Recently had to return to the generic kernel because Gutsy became wonky and crashed whenever using the sorely needed rt kernel on my new AMD X2 4800+. (Maybe I can forget about using Linux for music for now but that doesn't mean I want to trash it altogether.)

X failed to start and reinstalling **nvidia-glx-new** through apt-get didn't help. 

So I downloaded **NVIDIA-Linux-x86-171.06-pkg1.run** from Nvidia's site, ran it, and yay! I got Nvidia!... 

...until I rebooted.  X comlpained about some version not matching that of the kernel module. I ran the installer again - and again it worked...

...until I rebooted. I ran NVIDIA-Linux-x86-171.06-pkg1.run **--uninstall** and tried the **nvidia-glx-new package** again... but it's no use. Eventually switched over to **nvidia-glx**, but it didn't make a difference. (I have a GeForce 7600 GS (AGP) on an ASUS A8V Deluxe. The **-new **package had always worked.)

State of things right now:

[b]sudo modprobe nvidia
FATAL: Error running install command for nvidia[/b]

There's also no nvidia* anything in **/lib/modules/2.6.22-14-generic** - I don't know if there should or not. 

Right now I have apt-get installed (minus the packages specific to the rt-kernel): 
[b]
linux-generic
linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-headers-generic
linux-image-2.6.22-14-generic
linux-image-generic
linux-restricted-modules-2.6.22-14-generic
linux-restricted-modules-common
linux-restricted-modules-generic
nvidia-glx
nvidia-kernel-common
restricted-manager
restricted-manager-core
xserver-xorg-video-nv[/b]

I'm out of my league and have been confusedly fighting The Computer for days again. Anybody... please?

---

### Post by abalone on 2008-03-11
Okay. I don't know what it was, but whatever did the trick... did.

---

### Post by jordanfrank on 2008-03-14
any insight into what might have fixed things for you? I'm facing the same problem, have tried the same things you mentioned, and nothing seems to be working.

---

### Post by abalone on 2008-03-14
> **jordanfrank said:**
> any insight into what might have fixed things for you? I'm facing the same problem, have tried the same things you mentioned, and nothing seems to be working.

Sorry, I was being pretty random at that point... 

I'm not sure - but I think it started working again when I installed the drivers **before** reinstalling the kernel. (Both through apt)

And much earlier I had tried to delete everything looking like the nvidia installer (the NVIDIA-ladida-whatever.run file from their site) might have left it. 

Good luck

---

### Post by abalone on 2008-03-16
> **abalone said:**
> I'm not sure - but I think it started working again when I installed the drivers **before** reinstalling the kernel. (Both through apt)

Yep, same issue again when going back to nvidia-glx-new rather than just nvidia-glx. It worked when I installed nvidia-glx-new before reinstalling linux-generic.

---

