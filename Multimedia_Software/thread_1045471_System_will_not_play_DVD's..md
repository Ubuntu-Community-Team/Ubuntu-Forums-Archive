---
title: "System will not play DVD's."
date: 2009-01-20
forum: Multimedia Software
---

### Post by somavirex on 2009-01-20
The system will not play DVD's - I can read data DVD's, play .avi files, and burn DVD's, but payback is not working. 

When I attempt playback I get this from MPlayer (fatal error):
Error opening/initializing the selevted video_out(-vo) device.

I'm running the 64-bit version of Ubuntu. 

If you need more info, please let me know. I appreciate any help!!
Also, I'm very new (2 days) to Ubuntu, so please excuse my ignorance...

Thanks!

~jaime

P.S.  The system is a Compaq Presario V5210US laptop.

---

### Post by dougfractal on 2009-01-20
You might need to install some software to read comercial DVD's
There are legal reasons why Linux doesn't distribute it by default.
One method is this 

```

sudo "echo activate sudo"
```
```
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get -y --force-yes install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdread3 libdvdcss2 vlc

sudo apt-get install ubuntu-restricted-extras
```


vlc is an excellent media player.

---

