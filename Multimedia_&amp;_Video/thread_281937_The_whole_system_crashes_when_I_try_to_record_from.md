---
title: "The whole system crashes when I try to record from a MIDI keyboard with Rosegarden"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by crazybrit4967 on 2006-10-21
I'm trying to make techno with my MIDI keyboard for a school project, so I installed Rosegarden.  Everything works fine until I actually plug in the MIDI interface - an "Eridol USB MIDI interface UM-2x" (translation: cheap POS) at which point Ubuntu just freezes - I can't move the mouse, and the music I'm listening to starts skipping.  I have to reboot to get it to unfreeze.  I thought Linux wasn't supposed to crash! :p 

Anyway, anyone know what's causing this?

---

### Post by crazybrit4967 on 2006-10-22
Anyone?

---

### Post by zettberlin on 2006-10-23
> **crazybrit4967 said:**
> Anyone?

OK try to do this:

1.) start the system and start jackd - alsamidi-seq must be loaded obviously
2.) open a terminalwindow and enter this:
   
:~$ tail -f /var/log/messages

3.) connect the edirol and watch the terminal. What does it say?

(should be something like this:

Oct 23 10:44:55 zettberlin-edgybox kernel: [ 3170.026428] usb 2-2: new full speed USB device using uhci_hcd and address 2
Oct 23 10:44:55 zettberlin-edgybox kernel: [ 3170.174350] usb 2-2: configuration #1 chosen from 1 choice
Oct 23 10:44:55 zettberlin-edgybox kernel: [ 3170.366059] usbcore: registered new driver snd-usb-audio

)

if the system freezes fetch a so-called pencil and write down the last messages in the terminal on a piece of "paper" (if in doubt, what this could be - ask a person that has exceed the age of 30 already - such zombies have ancient knowledge of mysterious forgotten technologies... :twisted: ;) )

If it is not an issue with alsa-seq it could be some weired usb-problem, anyway: most USB-Keyboards work right away, so there shoud be a way to fix this.

good luck :-)

---

### Post by crazybrit4967 on 2006-10-23
Thanks!  I should note, though, that it's not actually a USB keyboard, I just connect the keyboard to a USB midi interface.  Does that make any difference?

---

### Post by crazybrit4967 on 2006-10-24
Okay, I tried that and I get:

Oct 24 00:01:23 localhost kernel: [17179872.624000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Oct 24 00:01:24 localhost kernel: [17179873.104000] usbcore: registered new driver snd-usb-audio

Also, excuse the noobiness, but I have no idea what alsamidi-seq is.  Is there any way I can check if I have it/if it's working?

---

### Post by zettberlin on 2006-10-24
alsa midi seq is the lowlevel-driver, that provides connection and routing of midi-ports in linux. It runs in the background. If you connect a mididevice - be it hard or soft - the sequencer must be running to transport and interchange data.

Regarding your foremost mention: if i get you right, you first connect a USB-Midiinterface and then the keyboard to it with a conventional midi-cable.right?
So then only the USB-Mididevice must be supported afaik, some of them need a firmwareupload to work, what device is that?

---

