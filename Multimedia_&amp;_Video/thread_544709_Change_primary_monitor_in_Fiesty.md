---
title: "Change primary monitor in Fiesty"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by criddell on 2007-09-06
I just installed Fiesty on a Dell with an NVIDIA card that has a DVI port and an analog port. I connected two monitors, installed the NVIDIA driver and things have mostly been working. I'm using Twinview.

My main irritation is that the OS seems to prefer what I would consider my second monitor (the one on the analog port). I say prefer because this is where gdm displays its prompt, its where the gnome splash screen displays, and is where a bunch of applications seem to want to open (especially java apps). The Ubuntu splash screen (the one that shows during boot) does display on my main monitor.

Can anybody tell me how I tell the os that my dvi monitor is my primary monitor?

Thanks,
Cory

---

### Post by criddell on 2007-09-07
Of course the first search I did after posting the question yielded the answer (and I did 50 searches before posting!!).

The answer was on this page:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9625/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9625/README/appendix-d.html)

I added 
    Option "TwinViewXineramaInfoOrder" "DFP,CRT"
to my xorg.conf file and all is well again. 

Sorry for the noise.

Cory

---

