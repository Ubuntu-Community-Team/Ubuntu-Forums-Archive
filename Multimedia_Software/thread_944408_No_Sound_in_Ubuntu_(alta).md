---
title: "No Sound in Ubuntu (alta?)"
date: 2008-10-11
forum: Multimedia Software
---

### Post by jizam on 2008-10-11
Hello...

I'm very new to Ubuntu (and linux in general) and having one hell of a time trying to get my sound working.  I've searched google and there's many suggestions but I get nothing but errors.

Tried this link:  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

but can't get beyond:

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa

all of these give me errors:

sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

None of the other codes work.

I've also tried this:

apt-get install alsa-base
apt-get install alsa-source
cd /usr/src/
tar xvfj alsa-driver.tar.bz2
cd modules/alsa-driver
./configure
make
make install
/etc/init.d/alsa start

But when I get to the 4th line I get a tone of errors like:

"Cannot open: No such file or directory"

In volume controls, the device is Intel ICH5 (Alsa mixer)
Under preferences, I've checked Master, Master Surround, PCM, Surround, Center, Line-in, and CD - they're all unmuted.

Would anyone be kind enough to give me step by step installation directions?  Is there something easier than what I've listed?  I made sure to add just about every alsa related thing from my repositories but for the life of me cannot get a bit of sound.  Any help would be greatly appreciated (and please assume I know verrrrrry little about Linux commands but can follow directions.)  Thanks!

---

