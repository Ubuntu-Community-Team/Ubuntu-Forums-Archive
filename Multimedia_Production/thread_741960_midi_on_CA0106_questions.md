---
title: "midi on CA0106 questions"
date: 2008-04-01
forum: Multimedia Production
---

### Post by Jean__ on 2008-04-01
Hello,

Are there any sound guru's around here? :)

Plain soundblaster live 24 bit, ubuntu 7.10. 

I have sound but no midi but I would like to play with stuff like rosegarden.

Tried to load a soundfont first with fsxload, it tells me 'No AWE synth device is found'.
I then discovered module snd_emu10k1 is not loaded, though it is listed in /etc/modprobe.d/alsa-base as:

install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }

loading the module by hand works though.

Then I read that in order to get midi working one has to insert a line like 'options snd-emu10k1 mpu_port=0x330' into the alsa-base file.

But after doing that, snd-emu101k1 refuses to load, complaining about some bad option in the driver, removing the options line fixes the error again.

Some exptertise insight would be very helpful as audio in linux resembles one big nightmare it seems. If I can provide more info, please say so.

Edit: hm, further investigations show that audacity does not play a wav file, so it's not only the midi part, though I have system sounds and can play mp3 and have sound in movies. Another weirdness is that only some volume sliders work, like the one in alsamixer. The slider on players is mostly useless, though I can live with that. But it might be an indication on what's fishy.


Thanks, Jean.

---

### Post by Jean__ on 2008-04-02
bump, the audacity problem is solved but no midi no matter what I try and search.
Only timidity works but it is an emulator which I don't want.

---

### Post by bobhenz on 2008-04-19
I have the exact same problem. I've been trying to use KMid and no love. aplayer -l shows ca0106 for me too. Anyone out there have an idea? Rosegarden sounds like exactly what I want. This problem is the only thing keeping me on a windows machine. In fact I bought a new sound card thinking that my old one was the problem. Different sound card, same problem. :-(

---

