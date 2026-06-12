---
title: "No sound and only dummy sound adapter after update this morning"
date: 2014-07-09
forum: Multimedia Software
---

### Post by chris259 on 2014-07-09
Seems a recent update this morning has botched up Alsa and all audio on my system. No sound and the unity-control center shows only the dummy sound adapter now where I had my Intel built in and my USB sound interface previously.

running ubuntu 14.04 on a Lenovo T61 laptop. 
3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686 i686 i686 GNU/Linux

Alsa utils also no longer work. Cannot use the alsamixer. 

(example)
: alsamixer 
cannot open mixer: No such file or directory
alsa utils will run as root. 

[B]More info: sound interfaces do show up in lspci
Alsa utils work as root and I can see both the sound interfaces that used to show up in sound-settings[/B].

Tried some common things suggested. Removed alsa base and pulseaudio then re-installed. still no sound and cards do not show in sound settings.

Maybe something to do with the new kernel thats running, however I do not know how to run a previous kernel on this system because I chose to use disk encryption and there is no grub menu on boot. 

So, not sure what to do. Any help apprecaited.

I have the alsa-info.sh script output here
[http://www.alsa-project.org/db/?f=4bb64e388b13ba2f2eda3235646061e3a83c696d](http://www.alsa-project.org/db/?f=4bb64e388b13ba2f2eda3235646061e3a83c696d)

---

### Post by chris259 on 2014-07-09
Update: figured out how to get to the grub menu and booted with the 3.13.0-29-generic kernel and vola ---- back in business. So problem with this 3.13.0-30 kernel.  alsa utils and pulse audio don't work properly with it. Hopefully fixed in the next kernel release. ... bummer.

---

