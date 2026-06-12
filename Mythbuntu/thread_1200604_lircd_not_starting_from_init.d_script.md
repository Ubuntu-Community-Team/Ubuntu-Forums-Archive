---
title: "lircd not starting from init.d script"
date: 2009-06-30
forum: Mythbuntu
---

### Post by daehenoc on 2009-06-30
Hi everyone,

OK, I've got my Compro DVB-T300 card working, now to get the IR receiver working.

I've got the correct lircd.conf file with the buttons etc defined.

I can't for the life of me figure out how to configure the hardware.conf file, I know the correct input device and driver, and can get lircd to run with the following line:
```
sudo /usr/sbin/lircd --device=/dev/input/event7 --driver=dev/input /etc/lirc/lircd.conf
```This runs and I can use 'irw' to see the keypresses and everything!

I'm about to have a nervous breakdown about the hardward.conf file, I reduced it down to the following lines:
```
START_LIRCD="true"
DEVICE="/dev/input/event7"
DRIVER="dev/input"
```AND LIRC STILL WON'T START FROM /etc/init.d/lircd - waaahahah :(

What happens is that I get a [[COLOR="Red"]fail[/COLOR]] message when I run```
sudo /etc/init.d/lircd start
```Can anyone help me?

---

### Post by ian dobson on 2009-07-01
Hi,

Don't forget the / infront of the dev line for DRIVER=

Regards
Ian Dobson

---

