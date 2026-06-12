---
title: "Fix flash fullscreen playback nvidia (Solved)"
date: 2009-05-17
forum: Multimedia Software
---

### Post by jack0rlando on 2009-05-17
This problem was annoying me for so long and I eventually found the fix. 
if you type in "glxgears" into the terminal and get the line 
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
then this fix will work for you. Just type "sudo chmod 0666 /dev/nvidia* " into the terminal. 

This fix doesn't work when you reboot your computer so type in "sudo gedit /etc/rc.local" and add the line "chmod 0666 /dev/nvidia*" to get it to run at startup

This should make anything involving the graphics card work better. Tell me how it worked for you.

---

