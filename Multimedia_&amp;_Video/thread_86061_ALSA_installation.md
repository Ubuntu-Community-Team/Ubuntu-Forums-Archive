---
title: "ALSA installation"
date: 2005-11-04
forum: Multimedia &amp; Video
---

### Post by callia on 2005-11-04
I would like to recompile mine ALSA for SoundBlaster Live! 5.1
For now I can hear all sounds from all six channels, but it's a bit crappy (comparing it with how it sounds in Windows).. MP3 music with 256kbps sounds like 96kbps.. May be it would be possible to configure it better with installed ALSA, but first of all I want to install the latest clean ALSA.. 

I'm beginning with alsa-driver and it's seems it compiles perfectly. I compile it in this way:
> $ sudo  ./configure --with-cards=emu10k1 --with-sequencer=yes
  $ sudo make
  $ sudo make install

At the end after "make install", it throws:
> /sbin/depmod -a 2.6.10-5-386
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /usr/src/alsa/alsa-driver-1.0.8/include/sound /usr/include/sound; \
else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
                install -m 644 -g root -o root $f /usr/include/sound; \
        done \
fi
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.



It's nor saying compilation was successful, but there is also no errors.
After it.. I'm trying to install alsa-lib and ./configure script throws such error:
> checking for alsa-driver package... not found
Fatal error: Install alsa-driver package at first...


I analysed almost all readmes and tutorials I found, but it seems, that nobody had such simple problem.. or I'm doing something in wrong way :???:

---

### Post by John.Michael.Kane on 2005-11-04
this may guide you [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

you may need Build essentials from synaptic.

---

