---
title: "NovaTD 500LNA"
date: 2010-02-13
forum: Mythbuntu
---

### Post by tonycollinet on 2010-02-13
OK

Mythbuntu 9.10

There now seems to be three files where it may be necessary to enable the LNA's

Options
Options.conf
dvb-usb-dib700.conf

All in /etc/modprobe.d?

Which must I use - and should I not use the others? And more importantly, how do I confirm that the LNA's are actually doing something?

Thanks all.
Tony

---

### Post by ianc on 2010-02-13
In Karmic I have:
> /etc/modprobe.d/dvb-usb-dib0700.conf

Containing:
> #enable LNA
options dvb-usb-dib0700 force_lna_activation=1
#disable 2nd tuner suspend
options usbcore autosuspend=-1

To check the LNA is activated:
> more /sys/module/dvb_usb_dib0700/parameters/force_lna_activation
should return "1".

---

### Post by tonycollinet on 2010-02-13
Thanks for the tip, especially for the "more" command.

I setup /etc/modprobe.d/dvb-usb-dib0700.conf
Got a 0 result

Then put the same into options.conf
Got a 0 result

Then put it into options.
Got a 1 result

Then I checked my options file - but in there it was specified to set to 0. Huh? (I'd previously renamed the files with a .old on the end while experimenting. I've also  been experimenting with trying to turn it off)

So I still don't know which file is turning it on.


So go figure - this is one of the problems I find in general with linux - lack of consistency.

---

