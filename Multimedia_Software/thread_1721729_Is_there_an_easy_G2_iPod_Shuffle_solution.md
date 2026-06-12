---
title: "Is there an easy G2 iPod Shuffle solution"
date: 2011-04-04
forum: Multimedia Software
---

### Post by sgtsearoy on 2011-04-04
Hello,

I'm new and ignorant, I admit it, and I don't remember as much about Unix/Linux as I wish I did, so I'm fumbling through Ubuntu 10.10 as best as I can.

I'm about 2 weeks into Ubuntu and trying to load up programs that my family needs and wants on a brand new NewEgg DIY AMD system.

My wife poses the biggest challenge, as one might expect.  She only needs Internet Explorer, Office and iTunes.  Firefox and OpenOffice.org have fulfilled the first two requirements but her iPhone and G2 iPod Shuffle holding me at gunpoint.

There are songs on both that I want to pull off, so as to not have to purchase them again.  Then I would like to emulate or duplicate the look and feel of iTunes as much as possible.  Rhythymbox seems to take care of the latter requirements, but it doesn't recognize or operate the Shuffle, so I am really hoping there is a non-hacker, wife-friendly solution.

Yes, I looked through the forum and archive and most of it is Greek to me, and the ones I did understand seem to imply that I will lose the songs that are currently loaded on the iPods, which is not cool.

---

### Post by wolfen69 on 2011-04-04
Don't be put off by this, you only have to copy and paste all of the following into a terminal and press enter.

```
sudo apt-get install ipheth-utils
```
then
```
mkdir /tmp/packages && cd /tmp/packages
```
then
```
wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb
```
then
```
sudo dpkg --install *.deb && sudo apt-get install aptitude
```
then
```
sudo aptitude hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```
then
```
sudo apt-get install gtkpod
```

Now, go to applications>multimedia>gtkpod and see if your ipod is recognized. It worked for me.

---

### Post by sgtsearoy on 2011-04-04
Thank you for the quick reply.  The commands you listed definitely did something, but I got this error:

Extended info will not be used.
iPod Database Import Failed: 'iTunesStats File: entry length smaller than expected (0<32).'
Newly mounted iPod at 'media/MANDY' could not be loaded into gtkpod.

users note: the iPod is named MANDY.

The iPod is mounted and recognized by Ubuntu, and I can play the music by accessing the file system, but it's not user friendly, and the filenames are encoded by iTunes, and I can't access the DB, so it's a little aggravating.

Anyone else can help?

---

