---
title: "Configuring sound input source through ALSA"
date: 2010-05-03
forum: Multimedia Software
---

### Post by mikau16 on 2010-05-03
I am using a program that takes microphone input, but I instead want the input to come from a WAV file. I read about the 'file plugin' for alsa, that lets you create virtual devices that input/output from files. So I attempted to implement a 'virtual microphone' device that takes its input from a file, and made this the default device. (using .asoundrc and asound.conf) think I did it correctly because when I use 'arecord' and don't specify a device, it records from the wav file as if it were playing through the microphone. However, the program I'm using still insists on reading its input from the built in microphone hardware. 

So am I not setting up the ALSA configuration files correctly? Or is it possible for the program to ingore ALSA entirely?

---

