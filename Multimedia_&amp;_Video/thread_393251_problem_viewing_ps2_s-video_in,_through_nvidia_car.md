---
title: "problem viewing ps2 s-video in, through nvidia card in Ubuntu Edgy"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by felicity on 2007-03-25
Hi,

On winXP I'm able to connect my ps2 s-video cable into a composite adapter and plug this into my nvidia geforce7 7800gt graphics cards tv-out. I can then use software like Media Player Classic to play ps2 through my computer and LCD monitor (since I have no tv).

But since I ditched winXP and am now running Ubuntu Edgy, I haven't yet found a way to accomplish this. ](*,)

Software like VLC has an option for Open Capture Device which should work, but it seems as if the device needs to be mounted first. (?) I'm new to linux so I'm not sure what the process is in mounting the device, if that's what the problem is.

Using software like tvtime, it shows No Such Device, videoinput: Cannot open capture device /dev/video0: No such device. :-k

Any advice on this issue is greatly appreciated!

---

### Post by felicity on 2007-03-26
As an alternative, does anyone know if win4lin or vmware would be efficient in displaying  video from a winXP install to Ubuntu?

---

### Post by reclusivemonkey on 2007-03-26
> **felicity said:**
> 
On winXP I'm able to connect my ps2 s-video cable into a composite adapter and plug this into my nvidia geforce7 7800gt graphics cards tv-out. I can then use software like Media Player Classic to play ps2 through my computer and LCD monitor (since I have no tv).

Any advice on this issue is greatly appreciated!

Are you *sure* about that? I'm a little confused at how you manage to get a s-video signal IN through a s-video OUT socket. I do exactly the same as you with various consoles only with a PCI TV card which has a S-Video in socket. I then use TV Time to view the incoming signal.

---

### Post by felicity on 2007-03-26
Yup I'm sure, I know it sounds weird, and I'm not sure how it works myself, but it *does* work.

But I did forget *something*, that I have to install the nvidia WDM driver on winXP to be able to view the incoming video stream. And I can't seem to find any information about it for linux, so I'm guessing there isn't one or any way around it. <sniffs sadly> :? 

Thanks for your input though reclusivemonkey! :)

---

### Post by reclusivemonkey on 2007-03-27
> **felicity said:**
> Yup I'm sure, I know it sounds weird, and I'm not sure how it works myself, but it *does* work.

But I did forget *something*, that I have to install the nvidia WDM driver on winXP to be able to view the incoming video stream. And I can't seem to find any information about it for linux, so I'm guessing there isn't one or any way around it. <sniffs sadly> :? 

Thanks for your input though reclusivemonkey! :)

No problem :-) I am not aware of this being possible in Linux with the NVIDIA drivers but someone else may know.

I managed to get a digital tv card with a s-video input socket for about £7 here in the UK so you may be able to pick up something cheap that will allow you to achieve your goal. Good Luck.

---

