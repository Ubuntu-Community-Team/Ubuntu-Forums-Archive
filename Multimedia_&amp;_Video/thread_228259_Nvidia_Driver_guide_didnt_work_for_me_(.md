---
title: "Nvidia Driver guide didnt work for me :("
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by kingvicious on 2006-08-02
ok well i read some of the threads of the people that cant get there nvidia drivers to work and well i couldnt find one with the same issue as me so here i go. 
 i went to wiki and searched nvidia found the how to for the install and followed it word for word untill about step ten where it asks to open the terminal and type sudo nvidia-glx-config enable. well when i do that i get the msg. 

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

and well to be honest i dont even know what my x config is i read allot about it on the other topics simliar to this one but being iam a linux noob i really dont know and well anywas anyone got any ideas on how to fix this?

---

### Post by kingvicious on 2006-08-02
i forgot to mention that my video card is a PCI-E nvidia 7600 GS 256MB if that helps any

---

### Post by tseliot on 2006-08-03
Next time you can follow my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)


If you want to solve your problem you have to:
```
sudo dpkg-reconfigure xserver-xorg
```

choose the "nvidia" driver (not "nv") and then you can press ENTER whenever you don't know the answer to the other questions.


then Log out and press CTRL+ALT+Backspace.

---

