---
title: "Recommend a PCIe x1 tuner card(s)?"
date: 2008-07-23
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-07-23
so im looking for 1 or 2 PCIe tuner cards. currently i have a PVR-150, and it works great, and i know hauppauge has great support but i really dont know how support is for other brands. i really want something like a PVR-500, but i dont think they make one in PCIe. i currently only have SD cable access, but i wont turn my nose at some digital/HD stuff either (for the future). i have 2 free x1 slots and i would like to populate them with dual tuners if possible. 

picture/audio quality is #1 importance. 

currently running Mythbuntu 8.04 64-bit.

---

### Post by gsrcrxsi on 2008-07-23
up

---

### Post by simonlesorcier on 2008-07-24
I;ve been using the PVR-500 for about 10 months. Dual tuner, works like a charm. The one I have is PCI. I also have limited number of slots. It's a no brainer.

cheers

Eduardo

---

### Post by gsrcrxsi on 2008-07-24
yea, i'll have 1 available PCI slot and i intend to replace my pvr150 with a 500 at some point. but right now im looking for PCI express x1 cards. as far as i know the 500 isnt made in a PCIe variant. im really liking the looks of the HVR-1800 or the HVR-1250, but it doesnt seem like either of them have analog support. so i was wondering if there are any cards similar to the 1250 or the 1800 made by some other brand that is supported?

---

### Post by gsrcrxsi on 2008-07-24
whats the word on analog for hvr-1800 or anything similar?

---

### Post by gsrcrxsi on 2008-07-25
so the 2.6.26 kernel is out. what does this mean for analog on the HVR-1250/1600/1800? from what i read, they were working on it with 2.6.25

---

### Post by tamoneya on 2008-07-25
i have the 1250 and I have had no luck with the analog.  Digital is nice though.

---

### Post by gsrcrxsi on 2008-07-25
do you have the newest kernel 2.6.26? it was released 10 das ago. if not would you mind trying it out?

what symptoms do you have with analog? just static?

---

### Post by tamoneya on 2008-07-25
The analog was not detected at all by myth.
```
tamoneya@tamoneyat61:~$ uname -r
2.6.24-19-generic

```

---

### Post by gsrcrxsi on 2008-07-28
mind trying to new kernel?

---

### Post by gsrcrxsi on 2008-07-31
bump

---

### Post by gsrcrxsi on 2008-08-01
up

---

### Post by gsrcrxsi on 2008-08-01
upity up

---

### Post by jaymode on 2008-08-05
> **gsrcrxsi said:**
> mind trying to new kernel?

I have an HVR-1800 and a few others have tried a newer Kernel without much success:
[http://ubuntuforums.org/showthread.php?t=785476&highlight=hvr-1800](http://ubuntuforums.org/showthread.php?t=785476&highlight=hvr-1800)

I am currently having issue with it on 8.04 and am considering upgrading to 8.10 alpha now to check it out.

---

### Post by Robstarusa on 2008-10-02
No luck with 2.6.26.5 for analog.  I also have the latest v4lb drivers pulled today.

I'm also interested in working pci-e tuners.

---

### Post by agamotto on 2008-10-08
> **gsrcrxsi said:**
> so the 2.6.26 kernel is out. what does this mean for analog on the HVR-1250/1600/1800? from what i read, they were working on it with 2.6.25

I can't speak to analog support with the new kernels/hacks that are not 'official' Mythbuntu patches.  I do know that on the two Mythboxen that I have at home the digital works quite well, save for a known issue with watching HD programming live.  Analog does not work for me currently, but Myth does detect the tuner as of 8.04.1 and the 'official' patches to date.  

Others with more patience/ability to experiment could tell you more, as I am no longer eager to play with things that can break my boxes.

---

### Post by gsrcrxsi on 2008-10-18
any dual digital tuners available in pcie x1? something like the pvr 500 but digital. 

i have a pvr 500 but would like a dual digital to even it out on the digital side.

---

