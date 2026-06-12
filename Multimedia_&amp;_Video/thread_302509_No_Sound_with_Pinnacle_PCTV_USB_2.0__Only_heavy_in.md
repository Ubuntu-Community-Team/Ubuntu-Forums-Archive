---
title: "No Sound with Pinnacle PCTV USB 2.0  Only heavy interferences"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by ChimaeraGerm on 2006-11-18
Hello,

I'm using the Pinnacle PCTB USB2 Sound Card on my Laptop with Kubuntu 6.06 LTS. After a search for an instllation Howto I learned how to install the drivers it needed and so the picture already works.
Another thing is the sound. With this [http://www.pinnaclefanboard.com/showthread.php?t=6156]("http://www.pinnaclefanboard.com/showthread.php?t=6156") Manual i tired to get the sound working via SOX.

I know ich have to copy the sound with 
**sox -r 44100 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp [&tvtime --mixer=/dev/mixer:vol&**]
from DSP1 to DSP..


The Problem is just: Its no use doing. As soon as I enter teh commnd, I hear a very high, nerving and unbearable sound.
Changing dsp1 and dsp in the sox command does't work either. Just for fun, I disconnected my TV-Card and started sox again. Result: The same strange noise ???:-k :neutral: 

I thought it could maybe refer to the fact that my Laptop build in Soundcard works, as far is I know, with alsa and not oss:
But changing **ossdsp** to **alsa** in the sox command doesn't help either.


In the wiki of LinuxTV.org [http://www.linuxtv.org/v4lwiki/index.php/Em2820#USB_Audio]("http://www.linuxtv.org/v4lwiki/index.php/Em2820#USB_Audio")

I saw i had to make sure that the  alsa usb driver is loaded. Is this done automatically??

Thank you already in advance for your efforts. I just can't handle the problem alone.

---

### Post by ChimaeraGerm on 2006-11-19
Push....

---

### Post by Asraniel on 2007-03-30
same problem here. exactly the same.

the card worked yestarday after 4 hours, and i realy dont know why i had suddenly sound. After a reboot the sound was gone again.

Does anybody have a idea?

---

### Post by buntunub on 2007-07-15
According to the v4l site this device is currently not supported. I am having the same problems. I have seen that if you setup your sound to go to dsp2 that it works somewhat but thats the best there is atm.

---

### Post by Metropolo on 2007-09-17
Hallo, I also had the same sound problem like you.
Now it runs for me when i make the fallowing workaround: I plug the USB cable of the PCTV USB 2 out, while Ubuntu is loading. Then I plug it again. This way the udev loads the drivers for the card at last. And everything works!

Then I normally run:
tvtime
and in separate terminal
sox -r 44100 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp

Enjoy!:popcorn:

---

