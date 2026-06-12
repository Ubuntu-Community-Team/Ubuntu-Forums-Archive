---
title: "not your typical nvidia issue (8800GT)"
date: 2008-05-04
forum: Multimedia Software
---

### Post by TwiStEr55 on 2008-05-04
Ok so I had a 7600GT under Gutsy .... worked flawlessly.

Now I got myself a 8800GT and switched to Hardy. I tried now for more than 3 weeks to get this card to work. It just does not. I cant count the google searches I did, I cant count the different methodes I have used ... I lost count of how many times I reinstalled ubuntu. Im desperate for help ...

I tried the repo install (hardware manager), envy and the nvidia binary (with every possibly tutorial on how to use it) ... i always get a black screen or my monitors enter power saving mode and the system hangs. 

Reading that many people got it work and that my card is slightly overclocked by default I bought another card (8800GT as well but other company) ... same outcome (can give it back though :) ) ... 

I read that its an ubuntu issue and got Suse installed on an extra partition and Surprise ... my card works there ... so its not the card and its not the driver, since its the exact same version I got work in Suse. Hence it must be an ubuntu or Kernel issue ... but how does everyone else get it to work???

I just tried again with the new kernel 2.6.24-17 .. same result ... the funny thing is, I just replaced the 8800 with my old 7600 and my system booted up into with the driver ... so it is installed right. I just dont get this ... 

I have one suspicion on what it could be .... I have 2 monitors and my 7600 card has one VGA and one DVI output .... when I boot with that card both monitors are on and once i get into gdm only the vga works, but after configuring it with the nvidia-settings the other does as well ....

so the 2 8800 cards have only DVI connectors ... I suspect it has something to do with that ... 

th nv drivers work by the way ... I get a clone output 

so that is it ... Iam sorta desperate in getting my ubuntu back to run. I dont wanna switch to suse or something and right now im almost back to using XP because I still ahve that installed for my games ....

Any help would be greatly appreciated .... Matt

EDIT: forgot to say, that I have tried to use one of my monitors with a DVI to VGA adapter on the 8800 card ... same result

---

### Post by Zorael on 2008-05-04
Did you upgrade or installed fresh?

Standard thing to do is to reset X configuration to default. Likely you've done this already but I thought I'd mention it.
```
$ sudo su
# aptitude purge nvidia-glx nvidia-glx-new nvidia-glx-legacy nvidia-settings
# aptitude update
# aptitude clean
# mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
# dpkg-reconfigure xserver-xorg
# nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Restart whole system, just in case drivers were changed.

---

### Post by TwiStEr55 on 2008-05-04
Ill give this a try .... even though it looks like something I have already done so many times. I installed fresh ... (many times btw)

I think that my 7600 worked is proof that the driver is indeed installed correctly

---

