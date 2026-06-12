---
title: "Digital (toslink) Problem with X-fi Titanium in 10.04"
date: 2010-09-22
forum: Multimedia Software
---

### Post by tekgeek on 2010-09-22
Hi, all,

I currently run Ubuntu 10.4 on my desktop.  I have an X-fi Titanium card hooked up to Yamaha receiver via optical connection, and am currently getting sound in one speaker only.  This problem is not present in Windows.  The balance is set correctly.  What should I do?

Thank you in advance,
Tekgek

---

### Post by tekgeek on 2010-09-23
bump.

Nobody else is having this problem?

---

### Post by Piotr Mazur on 2010-09-23
I'm also having this issue on Lucid x64 with Sound Blaster Titanium PCI-e. Cannot find any resolution though.

---

### Post by tekgeek on 2010-09-25
Bump.

Perhaps I should ask this:  Is there any way I can reinstall the X-fi driver in 10.04 32 bit?

Tekgek

---

### Post by tekgeek on 2010-09-26
Okay, I got a little closer (sort of).  I followed this guide here: [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound") and installed OSS.  I can now load ossmix, but it only shows my motherboard's audio.  I run ossdetect, and OSS sees my X-fi card, but when I try to restart OSS, the system freezes.  

Has anyone here used OSS before on 10.04?

---

### Post by davrosuk on 2010-09-26
I'm using SP/DIF optical out direct off of my motherboard. I'm using a pretty vanilla install - ie PulseAudio is still installed.

PA does not as yet support passthru, but ALSA, which is still exposed does. I use smplayer and vlc which have to be set to ALSA 0:1. I don't know what applications you're using or how the soundcard is presenting to the OS in your case.

---

### Post by Piotr Mazur on 2010-09-30
I've tried debugging the ctxfi alsa driver in alsa 1.0.23 and still no luck. Could not find anything wrong with the spdif output.

So far i have also noticed that when using optical out the sound can play only from left or right speaker, it really depends on your "luck". The best way to test it is by running mplayer and skipping forward/backward many times - sometimes the sound will be played by left speaker and from time to time it will switch to right.

So i guess the data is being transmitted via both spdif channels but why only one of them is playing remains a mystery to me.

I have also found out that restarting alsa "alsa force-reload" sometimes fixes the speaker out completly (all speakers play at the same time, it doesnt happen on every alsa reload though). But after running few apps that use sound the problem with the left/right speaker surfaces again.

Maybe some collaboration with alsa developers could help with this issue.

---

### Post by Piotr Mazur on 2010-10-02
I created a patch for alsa 1.0.23 which fixes this issue for me. Check [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5147](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5147)

---

### Post by Nisuspi on 2010-10-10
Hi Piotr,

Did you manage to get that patch to compile with 2.6.35-22 (default Maverick kernel)? I keep getting an error that '@CONFIG_SND_KERNEL_SRC@/include/linux/pci_ids.h' is missing when I try to run the makefile. 

Adam

---

### Post by Piotr Mazur on 2010-10-10
I think that it may be related with other alsa issue, my patch should have nothing to do with it. I remember that there are some issues related to ctxfi driver on alsa bug tracking system, you may check there.

---

### Post by Nisuspi on 2010-10-10
Indeed - nothing to do with your patch, I think it's a common problem compiling Alsa for any recent kernel. I just wondered if you'd more success than most (who end up using an older kernel) trying it on Maverick.

---

### Post by tekgeek on 2010-10-11
Hi, all,
I finally got a chance to compile the alsa-drivers package with the patch provided (a HUGE thanks to Piotr Mazur for the code.  I don't know any C, so I never would have found the issue by my lonesome), and both speakers seem to work. However, the audio output does seem excessively bassey. I'll have to check the settings on my receiver.  

I hope this fix is merged into the code soon.  I bet there are a lot of people waiting for this fix!

Thanks again to all,
Tekgek

---

