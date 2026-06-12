---
title: "install digivox a/d II tv- tuner on ubuntu 7.04?"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by macgywer on 2007-05-08
hello!

anyone managed to get this tuner working?
i got the picture without sound in xavtv once, but in the meantime i lost it. 
does the tv-tuner have to be attached to the pc during installation?

this is what i did:

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install mercurial
sudo apt-get install dvb-utils libxine-extracodecs
cd /usr/src
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)
cd /lib/firmware/`uname -r`
sudo wget [http://konstantin.filtschew.de/v4l-firmware/firmware_v2.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v2.tgz)
sudo tar xvzf firmware_v2.tgz
cd /usr/src/v4l-dvb-experimental/
sudo make
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/media
sudo make install

#now i rebooted the machine

sudo modprobe em28xx
sudo modprobe em28xx-audio
sudo modprobe em2880-dvb
dmesg
sudo gedit /etc/modules

#and i added the last three lines to modules

em28xx
em28xx-audio
em2880-dvb

the tutorial is taken from: [http://doc.ubuntu-fr.org/pctv_hybrid_pro_stick]("http://doc.ubuntu-fr.org/pctv_hybrid_pro_stick")
and here are some more: [http://mcentral.de/wiki/index.php/Em2880]("http://mcentral.de/wiki/index.php/Em2880") (english, german, french, spanish)

---

### Post by calagan on 2007-05-29
Hello,

I followed the same procedure as you did and I have the error in dmesg described in the link below: [http://mcentral.de/pipermail/em28xx/2007-April/000286.html](http://mcentral.de/pipermail/em28xx/2007-April/000286.html)
Maybe Markus Rechberger will come up with a fix. 

In the next few days I'll also try other firmware versions, since firmware_V2.tgz was recommended for the older MSI digivox a/d, and might not necessarily apply to the MSI digivox a/d II, which is a newer model.

---

