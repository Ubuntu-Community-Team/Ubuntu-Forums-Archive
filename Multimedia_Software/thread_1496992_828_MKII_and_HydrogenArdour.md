---
title: "828 MKII and Hydrogen/Ardour"
date: 2010-05-30
forum: Multimedia Software
---

### Post by Christopher Walker on 2010-05-30
I am new to Ubuntu and trying to figure out how to get my 828 MKII to talk to Hydrogen and Ardour. 

Does anyone have any experience with this? 

Thanks!

Chris

---

### Post by cchhrriiss121212 on 2010-05-30
Do you have jack installed and running? Jack is the low latency sound server for linux which is designed for audio production. You will need to use the ffado (which means firewire) driver in jack setup.

---

### Post by Christopher Walker on 2010-05-30
I have Jack installed but it seems my system cannot "see" the MOTU devise at all. Also, the drum sounds in Hydrogen pop and fizz terribly. Any thoughts on that?

---

### Post by cchhrriiss121212 on 2010-05-30
In order to use firewire devices you need to do a few changes which you should find [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation"). It may require a bit of patience if you are new to this. Notably it mentions this:
> ***With the new Firewire stack in Ubuntu Kernel, at the moment, it is not possible to run FFADO sound cards nor use Firewire for DV capture with -generic and -lowlatency kernels. Please see instructions on this page to install -rt kernel on this page, wich has old working stack. Until the new firewire stack works well with FFADO et DV capture, this section needs a complete rewrite.***
Once you have the rt kernel installed from the ppa listed lower down the page, you then need to have ffado and put this in a terminal:
```
echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |
sudo tee /etc/udev/rules.d/50-raw1394.rules
&& sudo restart udev
```
You can then check if it is recognised under the interface options in jack setup window.

Regarding Hydrogen, how are you using it? With jack and your onboard sound? If you are planning on using this 828 device then I wouldn't worry about what is going on now.

---

