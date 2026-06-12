---
title: "strange glitches with my USB soundcard"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by bYOndo on 2007-07-24
hello everybody!
I bought a "zoom H4 handy recorder", firstly for its recording ability (fantastic), then I discovered that this is also a real usb soundcard that works on linux. well...almost...
You can choose to connect it with 44.1 khz or 48Khz sampling rate. I tried 44.1K. everything is fine, it is recognized as "usb audio" and work with ALSA too, but it has glitches!
When I hit "test" on gnome-sound-properties, it plays the monofreq. tone and every 16 seconds it drops a glitch.ARGH! it's not casual, or related to any cpu overload, every 16 seconds here it is...
I'm going crazy, I don't know where even to start looking for any solution: everything else works flawlessly (audacity, softsynths, mp3&multimedia players, wine...)

every help is well accepted, thanks in advance!

Massimo

---

### Post by fredj on 2007-07-25
The gliches are caused by interruptions to the data being sent to the soundcard that are long enough for
the soundcard to run out of data. A more professional way to handle audio in Ubuntu is to load the low
latency kernel (or even better the real time kernel) and run all your audio programs through the jack audio
server. With the real time kernel you can run jack in real time and give it high priority.
Look in the mutimedia production forum.
You can run jack in the ordinary kernel and just by increasing jacks buffers to a large enough size you
should be able to get rid of the glitches.

---

### Post by bYOndo on 2007-07-25
Hey, thanks for suggestion! but I already have the low latency (now updated to real time) kernel, I come from ubuntu studio.
Even with jack (jackd w/ alsa driver)I have glitches, I tried any option combos; I can run it with as low as 5 ms latency, everything is working perfect, except this punctual glitch :( And w/o any xrun or any other error.
I discovered that this behaviour is only occuring when I connect the soundcard @ 44.1kHz, when I connect it @ 48 khz, this glitch magically disappears! but at 44.1 I can use a lot of programs that don't run w/ jack and are difficult to configure to work at 48 khz (I am veeery newbie w/ alsa programming). And the Zoom H4 has some pretty realtime effects on inputs that simply don't work at 48 khz... 
Ufff, can it be some sort of incompatibility with my hardware? i.e. motherboard (I have a Asus K8V-X SE)and its usb ports, I don't know.
Now I try to write to Zoom tech.service, maybe they have the solution...
I repeat: this would be a GREAT linux piece of hardware without these annoying glitches, so I want to see things clear.

Massimo

---

### Post by bYOndo on 2007-07-26
bump, 
nobody else?
However now I waIt for an answer from the japaneses :)

Massimo

---

### Post by bYOndo on 2007-07-26
...and here it is their not-so-exciting reply:
"Dear Massimo Carozzi,

Firstly, we are sorry for the inconvenience.
However, the ZOOM H4 doesn't support a Linux based computer.
Also, we do not have any specific plan to release firmware updates to support Linux at this time.
Please be kind to understand.

Anyway, we will forward your email to our R & D team for future reference.

Sincerely yours,
ZOOM Corporation.
"

uhm....
Massimo

---

