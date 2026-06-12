---
title: "USB Audio in Feisty - how to do it?"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by identitet5000 on 2007-04-19
Yes, how do I do it - is it possible? 

I've googled quite a bit, and it looks like some people are able to make their USB audio cards work in Linux by following the EZUSB guide found here:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=M-Audio+Sonica.&chip=&module=usb-audio](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=M-Audio+Sonica.&chip=&module=usb-audio)

However, following those instructions don't get me very far; when compiling, I get some errors. 

Might there already be a package ready for Ubuntu, containing a module for USB-audio ready to be loaded? Otherwise, is there perhaps someone who could take it upon himself to adapt the instructions found above to Ubuntu?

---

### Post by soze on 2007-04-19
Class-compliant USB audio devices should be "plug-and-play" with no additional drivers necessary (that's been my experience with several different devices from multiple vendors).

What sort of device are you having trouble with?

---

### Post by symera on 2007-04-26
Try System>Preferences>Sound and changing the "Sound Events" and "Music and Movies" dropdowns to USB Audio.  
This may get sound flooding back through your USB cans.  

As a slight aside, does anyone know how to get the volume control in the taskbar to control the USB audio volume?  In the volume control preferences (right click on the speaker icon in the taskbar>_P_references) I can choose between the ALSA mixer and the OSS mixer, but no mention of USB :(
I'm having the same trouble with the hardware vol +/- buttons. The hardware buttons change the volume of the Alsa PCM, but I'm not sure how to change that to control the USB audio. 
-r

---

