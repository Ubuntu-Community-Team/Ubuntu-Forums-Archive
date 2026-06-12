---
title: "no errors but no sound"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by joan_vc on 2007-06-08
hi, and thanks

Sorry for very my bad English

I've a problem in my laptop. It's a Fujitsu Siemens amilo M3438G.

I've just installed ubuntu feisty in my laptop.

I've installed all i need, and all no have  errors, but the audio not sounds.

I searched and reading a lot of forums and I don't find anything. 

The earphone works correctly, but the laptop's loudspeaker don't word.

I tested $ alsamixer and I increase all of volumes.

if do comand $ aplay *.mp3:
Playing raw data 'XXX.mp3' :unsigned 8 bit , rate 8000 Hz , mono

I have restart, reset...  /etc/init.d/alsa-utils but it don't work....

in: $ ps ax | grep esd
5480   ?    Ss    0:00   /bin/sh/-c /usr/bin/esd    -terminate    -nobeeps    -as   1     -spawnfd 24
5481   ?    S      0:00   /usr/bin/esd/      -terminate    -nobeeps   -as   1   -spawnfd   24
10825  pts/1   R+   0:00  grep esd


I don't  know that I do. please, can someone help  me?

Thanks!

---

### Post by renzokuken on 2007-06-08
i had to update to a newer version of alsa to get mine working

```
sudo apt-get install build-essential
``` to get the necessary parts for compiling alsa-driver from source

go to [www.alsa-project.org](www.alsa-project.org) and download the latest **alsa-driver** file to your home folder

extract it with```
tar xjf alsa-driver-1.0.14.tar.bz2
```

now enter the folder you just extracted

```
cd alsa-driver*
```

now run the following 3 commands in order to install it

```
./configure
make
sudo make install

```

reboot and see if it works

---

