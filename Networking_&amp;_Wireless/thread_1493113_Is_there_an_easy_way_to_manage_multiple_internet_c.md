---
title: "Is there an easy way to manage multiple internet connections with different cards?"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by morph_89 on 2010-05-25
Hello,

I'm running ubuntu lucid and i was thinking in purchasing one or more extra wifi cards to try to configure my computer to manage different conections at the same time, with different isp's. The thing is that I'm not quite sure if what i want to do is actually possible.

The easiest way that crossed my mind was to try to configure a / multiple virtual machines that are redirected threw proxies to ubuntu and try to configure that each proxie port goes threw a different internet gateaway. This way i might be able to divide threw different sessions of JDownloader, installed on each virtual machine, the things i want to download.  The negative aspect of this idea is having multiple jdownloader sessions will make my laptop work to almost 100% for sure...

Another thought i have was to make JDownloader manage its downloads in only one session redirecting them to my internet conections; the negative thing is that i think i will have to try to modify its source and learn java...

And well my last possible configuration i had in mind was to try to make ubuntu directly add up all my internet conections manage as if it was one. the negative thing here is that i might not be able to get multiple downloads from some sites

Well, all this where just thoughts, im struggling whether to buy another card or not to try to setup any of this configurations but im not really sure if any of them are actually possible. Is there an easy way to manage this? 

I just want to take the most out of my internet conections... if i'm at college i have to options that are quite slow, adding them up with two cards would be great, i might also be able to add a third and a fourth conection. Also if i'm on a coffe and i need some bandwith i could try to make it go with an open network arround, etc.

I'm not expecting a step by step tutorial answer, though it or a tutorial link would be welcomed; I will be more than happy with just some hints on what to do


Thanks

---

### Post by morph_89 on 2010-05-26
Well i coudn't hold myself and bought a second wifi card today :P. Its a tp link tl-wn422g. At first it was not recognized by ubuntu, googled a bit and found an installation method of the drivers, i installed a file named compat-wireless-2010-04-24 and a library in /lib/firmware. 

It appeared in the network editor and i could easily connect to more than one network at a time.

With some messing in the vmware's virtual network editor i select to bridge the connection threw the device wlan1 and it was done :D 

Though got to say that i have some trouble with the installation of the drivers, after i did make load, system completely froozed, i coudn't even go to the terminal by doing cntrl alt f1. When i restarted everything seemed ok. I started wlan1 as monitor and run airodump-ng mon0. It was working. After some time i realised that my second wifi card was also connected to the same network. I didn't bother to change it. It didn't took longer than a half hour for a complete freeze just like the one before.

The third time i started i disconected manually the second card from the same network. Its being almost four hours and counting and the system didnt frooze up. I used airodump for a while, worked fine, same with vmware handling the second conection, downloading with 2 jdownloaders in dif virtual machines :).

I'm hoping that the freezing was about being connected to the same network and maybe some communication between the hardware got messed up. Anyone knows?

could there be a way of managing this connections without having to use virtual machines in the middle? or at least say to some programs to run on wlan1 instead of wlan0?

---

