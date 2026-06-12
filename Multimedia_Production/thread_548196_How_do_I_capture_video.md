---
title: "How do I capture video?"
date: 2007-09-11
forum: Multimedia Production
---

### Post by organizar on 2007-09-11
I recently converted to Ubuntu. I am happy with it overall except I CANNOT capture video. I have a PCMCIA firewire card which I plug into my box. Then In bI turn the camera on and it says Dv in but I cannot get the box to find the camera. Is there a way to configure it to recognize the firewire card and then the camera. Thanks for any advice of suggestions.

Greg

---

### Post by stmiller on 2007-09-11
Plug the camera in, and turn on, then start kino, and does it say anything in the preferences of kino, under the tab Preferences>IEEE 1394 ?

---

### Post by organizar on 2007-09-12
The bottom of the screen reads: raw1394 kernel module not loaded or failure to read/write/dev/1394

I am unsure how to correct this error

---

### Post by kayosiii on 2007-09-13
install and try to run gscanbus.... if it refuses to run...
try 

sudo gscanbus 

from the command line. let us know what worked and what did not.

Also could you let us know what the exact device it says might be having difficulties reading writing to.... (if it is raw1394 you might need to be a member of the disk group)

---

### Post by Amazona aestiva on 2007-09-15
See the first link in my signature!

---

### Post by eggdeng on 2007-09-15
> raw1394 kernel module not loaded or failure to read/write/dev/1394
This is a good sign as it means the camera is being detected. Type ```
sudo chmod 777 /dev/1394
``` You may need to restart kino.

---

