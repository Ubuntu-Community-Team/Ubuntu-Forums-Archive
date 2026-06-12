---
title: "Guys i am so sorry for asking this again (E-MU 0404 PCI) how do i get it to function?"
date: 2010-10-09
forum: Multimedia Software
---

### Post by Akiranawasaki on 2010-10-09
Hello guys and girls of course......

I have searched high and low for an answer to my question but i just cannot figure this thing out......

I have ubuntu 64 bit (the latest) installed and it does not recognize my E-MU 0404 PCI card, i am a complete noob when it comes to using ubuntu´s terminal thus making it hard for me to understand how to install this card accordingly. 

It does however recognize my onboard ati which is useless to me seeing as my speakers are connected to the jack outputs of my E-MU card, so i would have to plug in and out the whole time to use ubuntu. 

I have tried several tips and tricks to get it to work, but then i stumbled on this post here:
[COLOR=Green]
[http://jg234.co.uk/articles/getting-the-e-mu-0404-pci-to-work-in-ubuntu/](http://jg234.co.uk/articles/getting-the-e-mu-0404-pci-to-work-in-ubuntu/)[/COLOR] 

I did all the things described with the latest drivers etc, it gives an error when trying to install Alsa utilities? Also it has the nasty side effect of deleting any trace of hardware/options in **sound preferences**.

It also disables alsamixer! When i type the command in the terminal it **says no such file or directory!** I was literally pulling the hair out of my scalp yesterday trying to figure out what i am doing wrong. ( At least the little i still have on my head lol).

I managed to find a fix which basically reverts all the settings back to normal following this guide:

[COLOR=Red][http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)[/COLOR]

But i still cannot get my card to work or even get it to be recognized by ubuntu...... I really hope that someone can explain and help me fix this problem in a noob-friendly manner. 

**Guys and girls thanks in advance!**

:confused:

---

### Post by cchhrriiss121212 on 2010-10-09
Try putting aplay -l into a terminal, if that does not find your card, try lspci -v.

---

### Post by Akiranawasaki on 2010-10-09
> **cchhrriiss121212 said:**
> Try putting aplay -l into a terminal, if that does not find your card, try lspci -v.


Thanks i did the first command and the following showed up:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Then i did the second command and my card  showed up alongside other hardware:

```
03:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
    Subsystem: Creative Labs Device 4002
    Flags: medium devsel, IRQ 21
    I/O ports at e400 [size=32]
    Capabilities: <access denied>
    Kernel modules: snd-emu10k1

```What should i do next? Thanks in advance......


EDIT i did some searching and i found out i have firmware version 1.0, of the E-MU card, guess it's not supported yet by ALSA???

---

