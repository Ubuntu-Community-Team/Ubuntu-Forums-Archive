---
title: "USB Audio PCM Not Increasing/Decreasing Correctly"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by nSTER on 2007-10-21
Whenever I try to increase or decrease the volume using the pcm module on USB Audio it is as if I am wrestling with it. It unlocks the left and right channel by it self and it won't let me increase them. It has a tendency to keep skipping and going on the bottom when I try to increase it. It randomly mutes it self when I get to the top of the volume. In other words it has a mind of its own. Any help is appreciated, this never had happen with 7.04 only with 7.10.

---

### Post by vsviridov on 2007-10-22
It did the same thing for me too,,, What you can do to set your volume is this.

Remove volume-applet from the panel, then adjust volume with alsamixer

---

### Post by nSTER on 2007-10-22
Thanks for the advice vsviridov works perfectly. But is there anyway to completely replace volume-applet with it? For example increase and decrease the volume using the laptop volume keys or the built in keys in the headset?

---

### Post by Danyl on 2007-10-22
I'm having this exact same problem.

I too am wondering how I can still use my volume up and down keys on my multimedia keyboard.

---

### Post by nSTER on 2007-10-23
Bump, seems like a couple of people are having the same problem.

---

### Post by logreeval on 2007-10-25
Bump, I have the same problem. I found Gnome Alsa mixer easy to use, but still an looking for an alsamixer applet that I can use...

---

### Post by nSTER on 2007-10-27
Just found out something in GConf the /desktop/gnome/sound/default_mixer_device
key shows you what mixer is being changed. It was set on alsamixer:hw:1 which is my headset. This makes me wonder if it uses alsamixer, why is it that alsamixer increases/decreases the volume correctly but when you use shortcuts or use the volume applet that it does not? Can anyone confirm on this?

---

### Post by gdi2k on 2007-10-28
I'm having the same issue, very annoying. But using alsamixer exhibits the same behavior. I'm using a standard Logitech USB headset (I think it's called Premium).

---

### Post by Squench on 2007-10-28
I am also using the Logitech Premiun usb headset and having the same problems. Bump!

---

### Post by Danyl on 2007-10-29
The problem doesn't exist in Feisty....what have they included in Gutsy that's different/causing this problem I wonder? (hint: someone with more knowledge about Ubuntu than me should answer this). :)

p.s. I'm using the volume keys on a Logitech Cordless (USB) Keyboard (hopefully this isn't a problem with just Logitech hardware).

---

### Post by nSTER on 2007-10-29
It is not just Logitech, I am having issues with my Plantronics headsets keys and the ones on my laptop.

---

### Post by tranqy on 2007-10-30
There is a bug submitted, this happens with different devices:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109)

---

### Post by tranqy on 2007-10-30
This may be gstreamer related, 'cause closing volume applet and using alsamixer seems to work fine.
I submitted this bug to gstreamer buglist:
[https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/158590](https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/158590)

---

### Post by Lord C on 2007-10-31
I also get this problem with my USB Plantronics DSP400.

---

### Post by james9876 on 2007-11-05
Same problem too....

Anyone had any joy in either fixing gnome-volume-control or remapping to another program (being able to control using the keyboad rather than having to open everytime)?

---

### Post by plush_cthulhu on 2007-12-14
simple workaround:

use ccsm to bind 2 keyboard shortcuts to the commands:

"amixer sset PCM,0 5dB+"
"amixer sset PCM,0 5dB-"

;)

---

### Post by Danyl on 2008-01-08
> **plush_cthulhu said:**
> simple workaround:

use ccsm to bind 2 keyboard shortcuts to the commands:

"amixer sset PCM,0 5dB+"
"amixer sset PCM,0 5dB-"

;)

Interesting. How do you accomplish this? Which plugin allows you to create keyboard shortcuts?

---

### Post by Danyl on 2008-01-09
> **Danyl said:**
> Interesting. How do you accomplish this? Which plugin allows you to create keyboard shortcuts?

Anyone?

---

### Post by james9876 on 2008-01-28
mmmmmm.... nice try, but no joy, still the same result really...

for example, with my card, the command to decrease is
amixer -c 1 sset PCM,0 5dB-

and similar to increase, the problem still occurs unfortunately :(:(

---

### Post by Danyl on 2008-01-29
I decided to install Gutsy 64bit on my system yesterday and guess what? This volume problem doesn't exist!

I now have perfect volume control using my multimedia keys!

No idea why.

---

### Post by jhallward on 2008-04-04
I'm getting this issue with a Koss USB doggle (technically a sound card, but more of a USB to audio jack adapter).  Any update in the past two months?  I've looked at both bug reports listed in this thread and both seem to have reached a dead end without anyone really even knowing the application at fault.  Both bug reports seem to have latched on to this to relieve their respective developers of responsibility for the bug, so I don't see any more progress being made in those threads.

---

### Post by Vanadaar on 2008-07-01
Logitech USB 250. Same gnome mixer problem. dropping to console and using alsamixer works. annoying, but works.

---

### Post by Danyl on 2008-07-09
The problem still exists in Hardy.

Has anyone got a work around?

---

