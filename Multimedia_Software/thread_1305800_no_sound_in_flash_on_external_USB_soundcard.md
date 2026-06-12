---
title: "no sound in flash on external USB soundcard"
date: 2009-10-30
forum: Multimedia Software
---

### Post by boomernang on 2009-10-30
||THIS HAS BEEN EDITED TO EXPLAIN WHAT HAPPENED - SOLVED||

Installed fresh Kubuntu 9.10.

I had one soundcard in my system and it was USB. /proc/asound/cards said that it was card1, and not card0. 
This was causing flash sound to not work because it was trying to play on a card0.

For some reason Kubuntu and Debian set snd-usb-audio to use an index of -2 in /etc/modprobe.d/alsa-base.conf by default.

So i had 2 options to get sound in flash.

Go into /etc/modprobe.d/alsa-base.conf and change

options snd-usb-audio index=-2    to    options snd-usb-audio index=-1

(restarted computer because alsa force reload didnt work, and now my card was INDEX0)

OR

for a hacky fix from alsa unofficial wiki

go into /usr/share/alsa/alsa.conf
and change

defaults.ctl.card 0    to    defaults.ctl.card 1
defaults.pcm.card 0    to    defaults.pcm.card 1

---

