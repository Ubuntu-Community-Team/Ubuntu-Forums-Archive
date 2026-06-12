---
title: "VM-Builder stops internet only on Ubuntu"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by gobberpooper on 2009-11-02
So I upgraded to Karmic Koala and it's pretty nice. My brother is getting into cloud computing and so he wanted to set up Eucalyptus here. He went through a bunch of steps using this guide:
[https://help.ubuntu.com/community/Eucalyptus-Jaunty](https://help.ubuntu.com/community/Eucalyptus-Jaunty)
He left partly through it and then he asked me to start but I have absolutely no clue how to do this stuff. I got down to the "Creating a VM Image" which refers to the page:
[https://help.ubuntu.com/8.04/serverguide/C/ubuntu-vm-builder.html](https://help.ubuntu.com/8.04/serverguide/C/ubuntu-vm-builder.html)
I got down to ```
**sudo ubuntu-vm-builder kvm hardy --addpkg vim --mem 256 --libvirt qemu:///system**
```But it was taking forever and I had to switch to Windows because my parents wanted to watch a movie on the 360. So I did "Ctrl+C" or something like that to stop the process. The next day I boot into Ubuntu and the internet doesn't work. Restarted the router and it still doesn't work. I went into Windows 7 and I'm on the internet right now. How can I reverse what I did?

---

### Post by gobberpooper on 2009-11-03
Bump

---

### Post by gobberpooper on 2009-11-04
bump. I tried uninstalling eucalyptus because when I shut it down it said something about eucalyptus and the network bridge. But I don't think that worked. I went into 192.168.1.1 to check my router settings and those were fine. How can I fix this?

---

### Post by ant2ne on 2009-11-04
I don't know what eucalyptus is. But start with
```
cat /etc/network/interfaces
```

---

### Post by gobberpooper on 2009-11-05
k i'll try that and see what it says.

---

### Post by gobberpooper on 2009-11-07
Okay well I just completely removed eucalyptus from my system, and waited a day and my internet on ubuntu is back now!

---

