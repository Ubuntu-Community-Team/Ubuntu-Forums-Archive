---
title: "Asus P5Q Deluxe - sound problem"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Kandi07 on 2009-04-28
Hi guys,

I'm new here and I wonder if you could help me with my little sound problem.
I found in the web and in this forum nothing useful.
The sound general works fine, but always when I try to complete a command in the xterm with the tabulator key - there comes this very loud beep sound.
The specifications of my PC are: (or see below in my signature)
Mainboard: Asus P5Q Deluxe
Processor: Intel Core2 Quad CPU Q9550
Graphic: GeForce 9800+ GTX

the result of the command
```
aplay -l
``````
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I hope somebody could help me, because the sound drives me nuts.

the result of the command 
```
cat /proc/asound/card0/codec#* | grep Codec

``````
Codec: Analog Devices AD1989B
```Best regards,
Kandi07

---

### Post by Kandi07 on 2009-04-28
the easiest way with non root privileges to solve the problem:
add in the file
```
~/.bashrc
```the line
```
xset -b
```save and close the file.
And that's it.
I get the solution from this website here:
[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

---

