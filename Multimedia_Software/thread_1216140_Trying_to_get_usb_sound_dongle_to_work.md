---
title: "Trying to get usb sound dongle to work"
date: 2009-07-17
forum: Multimedia Software
---

### Post by nihilum on 2009-07-17
I have a usb sound dongle that I'm trying to get to work. I followed instructions on another page, and the following command works, and I get sound out of my headphones plugged into the usb dongle:
aplay -D hw:1,0 test.wav
Now how do I get it to work in the volume control applet? It shows up as C-Media USB Headphone Set, but no applications playing sound go to the headphones. Any help will be appreciated.

---

### Post by kostkon on 2009-07-17
Assumiong that you have Ubuntu 9.04, you need the *PulseAudio Device Chooser* utility. More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by nihilum on 2009-07-17
Awesome, solution in about 60 seconds. Thank you very much.

---

