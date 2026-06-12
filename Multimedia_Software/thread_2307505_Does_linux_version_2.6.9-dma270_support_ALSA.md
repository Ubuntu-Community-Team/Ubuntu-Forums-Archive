---
title: "Does linux version 2.6.9-dma270 support ALSA ???"
date: 2015-12-25
forum: Multimedia Software
---

### Post by randa2 on 2015-12-25
I'm using a piece of hardware operating linux 2.6.9-dma 270. How can I know if it supports ALSA library? Given that ALSA is not installed.
PLUS ,, how can I install a library in an embedded system?

---

### Post by ian-weisser on 2015-12-25
What version of Ubuntu are you using?

---

### Post by matt_symes on 2015-12-25
Hi

What is the embedded device ? 

That looks like it may be a custom compiled kernel specifically for the device ?

Kind regards

---

### Post by Vladlenin5000 on 2015-12-25
> **ian-weisser said:**
> What version of Ubuntu are you using?

9.10 apparently -> [http://ubuntuforums.org/showthread.php?t=2306822](http://ubuntuforums.org/showthread.php?t=2306822)

---

### Post by QIII on 2015-12-25
In which case, randa2, I will echo basically what Bucky Ball said in your other thread:  With such an ancient release, you are liable to have trouble with just about everything and don't go on the web with it.

Please do a fresh installation of a supported release.

Don't ask the members of the forum to try to recall or dredge up anything that might apply to 6 year old release.

---

### Post by matt_symes on 2015-12-25
Hi

I don't think the 2.6.9-dma270 kernel is a Karmic kernel.

[http://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version](http://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version)

The OP's question may be unrelated to the other question or this may be a custom compiled kernel.

Kind regards

---

### Post by QIII on 2015-12-25
Looks like you have discerned something I did not, matt_symes.

Good catch!

---

### Post by ian-weisser on 2015-12-25
> **randa2 said:**
> How can I know if it supports ALSA library?
I think the actual answer to the question is not very helpful: You must see the source code and the kernel compile flags that created your kernel binary. It's unlikely you will get access to both, though a well-organized upstream might conceivably have them. Or, if reversible, simply try installing and see if it works.

 > **randa2 said:**
> how can I install a library in an embedded system?The simple answer is that you need root or sudo access to the device, and the very old, compatible ALSA library binary to install.

---

### Post by randa2 on 2015-12-28
Thanks All

---

