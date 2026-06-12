---
title: "no sound"
date: 2009-10-16
forum: Multimedia Software
---

### Post by Bliksimpie on 2009-10-16
hey

I have no sound in tv time and even on xawtv and also not in gnomeradio. I do get display, but no sound. I have Google around and nothing helped me so far. I do have sound in audacious. 

I had writen the following in a text file:

[php]#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/audio1 -t ossdsp -w -r 32000 /dev/dsp &
gnomeradio --mixer=/dev/mixer:pcm
wait gnomeradio
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80% unmute[/php]When i run this file in the terminal it gives me the following error: Chould not open device dev/radio.

any help on this please. I have been trying to fix this for weeks now.

---

### Post by Bliksimpie on 2009-10-18
please someone help me. It sucks to watch tv without sound. My line in is maxed and unmuted. I don't have a panel for my audio from my tuner card. Only from my motherboard. 

Everything worked fine on XP. Please any advice will help

---

### Post by kkady32 on 2009-10-30
see maybe u need to edit in gnomeradio-general seting-radio device: /dev/radio0
and after update to 9.10 i must change the driver from any to v4l2 with:
alt+f2  type gconf-editor  go to apps and after gnomeradio and change value here

---

### Post by Bliksimpie on 2009-10-30
Hey!

Thanx for the advice but Im still not getting any sound and the same error pops up(Device dev/Radio Could not open).

---

### Post by kkady32 on 2009-10-31
because u not have /dev/radio u need /dev/radio0,then must edit in gnomeradio
maybe check first in /dev what u have and when u find radio0 or radio then set in gnomeradio

---

