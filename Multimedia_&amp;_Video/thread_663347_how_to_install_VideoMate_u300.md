---
title: "how to install VideoMate u300??"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by taekr on 2008-01-10
hi, all 

I just found out that Compro Videomate U300 can be installed for Ubuntu. 

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/800534.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/800534.html)

This guy said that U300 is supported in the latest V4L drivers and it is detected as U500. 

Well, when I plug it into my laptop, my computer screen go blank. 

Anyone using U300???   know how to install it??

cheers,

---

### Post by jwatsonoz on 2008-07-01
I have it working by doing the following:

1) Install V4Linux

- download mercurial via synaptic
  (a source code management system)

- Obtain latest v4l-dvb source code from LinuxTV
  hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
  (This should create a directory called v4l-dvb in the current working directory)

- Compile and install V4l-dvb source code
  cd v4l-dvb
  make
  sudo make install

- reboot system

2)make sure you've got the demux codecs (so you can decode MPEG streams)
   sudo apt-get install libxine1-ffmpeg

3)Watch TV with 'correct' software:
This dtv card does not have a hardware MPEG encoder (hence /dev/video0 does not appear) so only certain players will work that have the software equiv. I use Kaffeine which is great.

problems:
If it doesn't work it could be because you do not have the firmware installed.

search for dvb-usb-dib0700-1.10.fw on the web and place a copy in /lib/firmware and reboot. I had to do this a while back but not lately - I think they updated V4L


good luck

---

