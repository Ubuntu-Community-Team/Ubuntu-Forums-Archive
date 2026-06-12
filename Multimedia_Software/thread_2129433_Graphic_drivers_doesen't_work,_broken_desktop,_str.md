---
title: "Graphic drivers doesen't work, broken desktop, strange resolution"
date: 2013-03-26
forum: Multimedia Software
---

### Post by firekage on 2013-03-26
I would like ask for your help.

Since the begining of using Ubuntu i can't use it with nvidia drivers - doesen't matter if i download it from nvidia website as a binary driver or from ubuntu repos either. PPA drivers from x-swat and xorg-eadgers also doesen't work.

I use Ubuntu with only one flat LCD screen. As soon as i install new drivers - for my nvidia graphic card, GTX260 - i have many problems with Ubuntu. Drivers detects that i have few screens, when in fact i have only one - HP228h. Also at almost every boot there is either black screen or after logging my monitor switches off. If i succesily boot and log into X, i have broken desktop. The resolution for my one flat LCD screen is divided for two screens that's been detected and randomly one of the fakes one acts as a primary. I should have 1680x1050 but when driver detects something that is not present...don't know how, resolution is set to 1024x768 for CRT screen - i don't have it.

Is there a fix for it? Don't understand why all drivers for Ubuntu with Unity doesen't work with my graphic card.

I have few screens, it shows how it looks like with this strange behaviour. Look at the purple screen - there is, nvidia drivers detected two screen, one "fake crt" and one flat lcd. I have only one, i don't use twinview, but it keeps turing on - i think that.

Maybe someone that is more advanced in linux could help me - i tried it on Slackware and it works. I tried it on Kubuntu - it works. I tried it on Ubuntu with Unity and on a fresh installation of 12.04.2LTS and 12.10 - it doesen't. 

I can't use ubuntu with nvidia because either i don't have screen at all, black screen, have to kill Xorg and restarting gdm/lightdm, after it either i could normally boot but then screen is broken just like on those screens, but most frequent behaviour is that after boot, log into X...screen goes black, monitor has "no input signal" and i have to switch to tty1, kill xorg, restaty gdm/lightdm and the problem happens from the beginnging.

Help. I'm frustrated. Don't know what to do in order to nvidia driver works. Don't know what to add, remove, change.



BTW - nouveau drivers work ok, but i want to have nvidia.

---

### Post by firekage on 2013-04-03
My problems are no more. Problem was solved thanks to Polish linux users from pclab.pl, i provided for english readers this topic and my final resolution to this:

[http://www.linuxquestions.org/questions/ubuntu-63/graphic-drivers-doesent-work-broken-desktop-strange-resolution-4175455637/](http://www.linuxquestions.org/questions/ubuntu-63/graphic-drivers-doesent-work-broken-desktop-strange-resolution-4175455637/)

---

