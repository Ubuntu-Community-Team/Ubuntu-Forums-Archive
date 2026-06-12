---
title: "Multimedia Unclaimed"
date: 2015-01-02
forum: Multimedia Software
---

### Post by chrisgriffin2001 on 2015-01-02
Hi people 

Just installed Ubuntu latest version and all updates are up to date, the problem I'm having is my EMU 0404 sound card won't work. On boot up it says : 'emu0404.fw not found.err -2

in Terminal it shows the sound card but says MULTIMEDIA UNCLAIMED? 

ive tried everything from getting latest version of Alasa etc to a lengthy Google guide, and nothing? 

Im really looking for somebody who's had this problem and actually solved it, just from looking at different posts on various  forums nobody seem to have a clear answer.

any help would be much appreciated.

cheers

---

### Post by Yellow Pasque on 2015-01-03
Hmm, for some reason (legal?), Debian/Ubuntu does not distribute this file. You can install it yourself though. I think wget, linux-headers and build-essential packages are installed by default, but make sure they are if you encounter issues.

```
cd ~
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.28.tar.bz2
tar xjf alsa-firmware-1.0.28.tar.bz2
cd alsa-firmware-1.0.28
./configure --enable-buildfw
cd emu/
make
sudo make install
```
The emu0404.fw file (and other EMU firmware) should now be in /lib/firmware/emu, ready for next boot.

Oh, and please don't bump more than once a day (site policy).

---

### Post by chrisgriffin2001 on 2015-01-03
Thanks Temujin, will give that a try.

---

### Post by chrisgriffin2001 on 2015-01-04
Temüjin! you are life saver pal, the amount of  time I've spent trying to figure this out. Nearly bought a new sound  card as well so cheers for that.:smile::smile:.

If  you can be bothred could you give me a short discription on how you  figured it out? I'm new to Ubuntu so any knowledge would be greatly  appreciated.

---

### Post by Yellow Pasque on 2015-01-05
> On boot up it says : 'emu0404.fw not found.err -2

I googled emu0404.fw and came across this page [https://wiki.debian.org/snd-emu10k1](https://wiki.debian.org/snd-emu10k1) , which suggested this file should be part of alsa-firmware-loaders package, and had to be built if it wasn't included.

---

