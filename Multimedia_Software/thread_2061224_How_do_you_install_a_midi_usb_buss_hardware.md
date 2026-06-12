---
title: "How do you install a midi usb buss hardware"
date: 2012-09-22
forum: Multimedia Software
---

### Post by Acepony on 2012-09-22
I have ubuntu 12.04 and have bought the EMU XMidi 2x2 for three reasons. One is because of a great check I got from work. Two I have a EMU keyboard. Three I read that some one on here did it successfully.

I read it had something to do with a kernel and fixing the IRQ's. I would be very appreciative if some one can layout some simple directions on how to install it. It is on two day shipping and handling. It will be here next Tuesday(9/25/12) 

SO there is plenty of time for talking me through how to set it up.

Again I will be very appreciative for your help. Also thanks for clicking on this thread because I know life can be busy.  ):P

---

### Post by Acepony on 2012-09-22
(Bump)

I know I said there is plenty of time I would like to know ahead of time what I need to do to install this thing. Please;)

---

### Post by BicyclerBoy on 2012-09-22
Midi support comes from alsa

[http://alsa.opensrc.org/USBMidiDevices#E-MU_Xmidi_series](http://alsa.opensrc.org/USBMidiDevices#E-MU_Xmidi_series)

You don't need to install any drivers..& your device does not need firmware package..

If the interface is USB I don't see IRQ being relevant..That sounds like an old soundcard issue (soundcards were commonly midi adapters).

Plug it in then run (terminal)
lsusb
(do you see the brand)
dmesg | tail -n 10
amidi -l

Plug in the midi device - hit some keys with this in terminal:
cat /dev/midi01
( see random characters on screen?)

There are loopback debugging cmds you can send/receive using amidi but hopefully this is not necessary..

---

### Post by Acepony on 2012-09-22
Thank you:D

I know I ask some dumb questions sometimes. I am just so use to programming integrated circuits which require you to write the program to get it to do anything. I forget that plug and play exists. 

You would not believe all the lines of code you need to write to get an LCD to work on a 16F877A just to tell it how to run before you tell it what words to display.

---

