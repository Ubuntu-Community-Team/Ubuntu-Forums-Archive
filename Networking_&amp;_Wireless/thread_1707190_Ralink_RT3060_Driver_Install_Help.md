---
title: "Ralink RT3060 Driver Install Help"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by PushRock on 2011-03-15
Hi,

I recently installed a Rosewill RNX-N150PCx which uses a Ralink RT3060 chipset. It seems to recognize the card but won't detect any networks. Is it a driver problem? If so can someone help me install one? I found linux drivers here 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

but I'm having trouble installing a .tgz. can anyone give me a stp-by-step process?

---

### Post by cbowman57 on 2011-03-15
Extract the file you downloaded and read the readme, it should walk you through it.

---

### Post by owiknowi on 2011-03-15
take a look at this post, looks like the same problem:
[http://ubuntuforums.org/showthread.php?p=10559827#post10559827](http://ubuntuforums.org/showthread.php?p=10559827#post10559827)

shriner came with a very plausible explanation: in order to make the rt3060 work you'll need at least a 2.6.34.xx kernel (and of course some drivers, but they're supposed to be installed by default).

tried several other penguins (pardus, kurumsal, mandriva, unity 2010.2, etc.) with newer kernels and wireless almost worked out of the box.

downloaded the latest kernel from [www.kernel.org](www.kernel.org) (linux-2.6.37.4) and going to try if i can hammer that into u10.04 (never compiled a thing since rh 6.x).

i'll post everything there, also if i decide to let an other penguin take over.
been at it since december 2010

---

### Post by randiroo76073 on 2011-06-02
I had the same problem, running kernel 2.6.37x, had to download and install drivers myself. I was under the impression that they were already embedded in the kernel but guess not ???

---

### Post by savoiu on 2011-11-09
How did you do it? I used the driver at
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
and after make/make install no other commands from the instructions worked.
I'm using Ubuntu 11.10-32bit and a Rosewill RNX-N150PCx card.
Thanks,
Nick

---

