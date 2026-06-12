---
title: "no sound from zynaddsubfx on ubuntu 10.10"
date: 2011-11-30
forum: Multimedia Software
---

### Post by tru infini on 2011-11-30
for quite awhile I've had issues with this and the old thread about it seems to be filled with cobwebs.
I was running just fine with 10.04 and I could open up zynaddsubfx, pop open the virtual keyboard and jam away on my real keyboard. I press "Q" and I get middle C (and so on so forth) quite a lovely setup if you ask me.
Now I've never had to run Jack or any modulation of Jack to get sound out of my precious zynadd. When I bumped the wrong thing on my computer, it has updated me to 10.10 and for some strange reason, it decides to not let zynadd put out any sound. no matter what I do, try or plead with it, no sound at all. Every other thread anywhere else out there on the internet dealing with zynadd and sound problems like this have not worked. Here is a list of my zynadd settings:
sample rate 44100Hz
Buffer? size 256
append box [x]
dump notes box [ ]
dump file: zynaddsubfx_dump.txt
XML compression level [3]
OSS Wave Out Device: /dev/dsp (file location doesn't exist)
OSS Sequencer Device: /dev/sequencer (file location doesn't exist)
These are the exact same settings I had when running 10.04 and it played sound just fine
When I press a key on the virtual keyboard, the key limit indicator shows sound going from zynadd but I don't know how to get that sound to the speakers.
I don't want to deal with Jack if at all possible but right now, I am willing to try Jack to get this working like it was before.
(also I can't get any sound from my front panel headphone jack but that's an issue I can live with)
Please someone help. if you have any questions or comments, please please please, I need your input

[http://xkcd.com/979/](http://xkcd.com/979/)

---

### Post by xodus99 on 2013-04-24
Hey,
 Were you able to figure out the problem?
I'm seeing the same issue. Please do let me know if you've figured it out.

---

### Post by tru infini on 2013-04-24
I actually have found a solution albeit a temporary one that needs to be done each and every time.
open up your Terminal and type in "padsp zynaddsubfx" and that will do it. but you must open it every time this way and your terminal must stay open as well.
I'm not a programmer so I don't know how to make so it will open that way automatically from just clicking on the Icon. If you have any suggestions that work then please let me know. If not then I can live with it being how it is. It's better then nothing.
This fix works for 12.04 (Precise)

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

