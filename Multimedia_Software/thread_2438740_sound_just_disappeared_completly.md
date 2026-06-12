---
title: "sound just disappeared completly"
date: 2020-03-17
forum: Multimedia Software
---

### Post by sapinski on 2020-03-17
Hello, I have just installed the new set of updates (with kernel 5.3.0-42-generic) on my Lenovo X1Yoga (version 4). Two things stopped working:
1. laptop either does not go to sleep anymore or does not wake up
2. I get no sound anymore (only dummy output)

This is not good. I kind of hoped that I some point, after software update, the microphone will start working, but instead there is less things working... Please help.

Mariusz

---

### Post by TheFu on 2020-03-17
Does the mic show up in **pavucontrol**?  

Getting the HW, input/output setup always takes me a few minutes. PulseAudio wants to switch to new hardware, even if we don't want that switch to happen. Sometimes a microphone gets tagged as ny output device by Pulse incorrectly or it gets marked as input AND output.

I don't know much more.  The smart people will need the **audio troubleshooter** output. They know how to read it and have an uncanny way of saying exactly the needed solution. That's been my experience.

---

### Post by jongudm on 2020-03-19
It seems we have more or less the same problem, see [https://ubuntuforums.org/showthread.php?t=2438828](https://ubuntuforums.org/showthread.php?t=2438828).

---

### Post by Yellow Pasque on 2020-03-19
So if the problems appeared right after a kernel update, has anyone tried booting into the previous kernel>

---

### Post by jongudm on 2020-03-24
The solution seems to be here: [https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061](https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061) This next kernel version does not seem to be quite ready yet but must be coming soon.

---

### Post by hzdl on 2020-03-25
I think I've also been having this issue ([https://ubuntuforums.org/showthread.php?t=2439096](https://ubuntuforums.org/showthread.php?t=2439096)). Is there really nothing to do but wait until the next kernel version is ready? As I noted in the post there is this interesting feature where the audio works during a live session, so I thought that was promising. This probably just means I don't understand how the live session works though.

---

### Post by TheFu on 2020-03-25
> **hzdl said:**
> I think I've also been having this issue ([https://ubuntuforums.org/showthread.php?t=2439096](https://ubuntuforums.org/showthread.php?t=2439096)). Is there really nothing to do but wait until the next kernel version is ready? As I noted in the post there is this interesting feature where the audio works during a live session, so I thought that was promising. This probably just means I don't understand how the live session works though.

Why not just boot one of the 2 prior kernels? They should still be in the grub menu.

---

