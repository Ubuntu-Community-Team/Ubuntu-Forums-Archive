---
title: "usb audio help"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by jludeman on 2008-02-10
I can't turn the usb audio card on as default. lsusb -v shows the device. System-Preferences-Sound does not show it. The device is a Turtle Beach audio advantage micro. 

Sudo lsusb -v shows it as a C-Media audio adapter at Bus 002 Device 004.
I've tried Audacity, VLC, XMMS and a few other applications and none show the usb device as an output option.

There is no bios setting to disable the onboard card.

The reason I'm doing this is so I can cut off the onboard speakers and listen via the headphones.

There are lot's of posts on the web where people have problems with Intel IHC6 on board audio card and the headphones not disabling the main speakers.
However I have yet to find a solution that works.

So I got the Turtle Beach usb card hoping to bypass the problem.

The sad thing is the same setup works perfectly in Windows 2000.

Since 99% of all my computer tasks are done under Linux it seems a shame to have to use Windows to listen to music or watch videos on the laptop without violating the public space.

I'd sure appreciate any help on this. Even a pointer to a web page would be great.

---

### Post by jludeman on 2008-02-10
Quick update.

Out of curiosity I booted from the live cd. System-Preferences-Sound shows the usb device as an option. XMMS output configure lets's me choose the usb device and it works.

Since I did a command line install of Gutsy I''m guessing some file or library did not get installed that is automatically used by the live cd.

Naturally the on board sound did not work. I already knew about that. 

I had to add some lines to /etc/modprobe.d/alsa-base about the intel card in order for the onboard sound and speakers to work.

Looking over that file I notice some strange usb entries. These were added by the system during install.

I'm kind of lost at the moment. I don't know if the onboard card **has** to **not** work or if I'm missing some files or if the configuration file is incorrect.

Anyway thanks in advance for any help.

---

### Post by jludeman on 2008-02-15
I'm outa here. No more Ubuntu forums. No more Ubuntu.

It's just a deviant Debian anyway.

So long and thanks for all the fish.

---

