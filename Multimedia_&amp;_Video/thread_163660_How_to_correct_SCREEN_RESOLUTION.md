---
title: "How to correct SCREEN RESOLUTION?"
date: 2006-04-21
forum: Multimedia &amp; Video
---

### Post by quincyjones on 2006-04-21
Hi, I'm new to Linux.
I'm running Ubuntu and I can't get my screen res correct (1200x800). In system>preferances>screen-res I only have a 1024x768 option. Ideally I think I need to install the drivers for my intel 910GML chipset but the intel site seems to have them for red hat, suse, mandrake but not ubuntu or debian! Why is that?

Anyway, I mostly just want my res correct!
Please help :-k 
Oh yes, if you can help, please tell me as simply as possible, I really am a newbi

---

### Post by Robgould on 2006-04-21
You need to edit your /etc/X11/xorg.conf file.  This file controls what screen resolutions you have available.  Open this file and scroll down till you find where the resolutions are listed.  Add the resolution you want in front of the others, in the same format.  ( "1024x768" ).  Restart x or reboot.

---

### Post by quincyjones on 2006-04-21
Hey Robgould, 
Thanks for the reply but how do I edit the file!! Told you I'm new!

---

### Post by Robgould on 2006-04-21
you should use the text eidtor that in included with gnome - gedit
 
from a console type
 
sudo gedit /etc/X11/xorg.conf
 
This will open another window....the file in the program gedit.  Modify the file and then save it.  
 
remember what you change!
 
If it causes problems, edit your changes back out and save it again.  Everytime you change this file you need to reboot or re-start x to see the changes.  You can restart x byt hitting ctrl-alt-backspace.
 
Hope this helps.

---

### Post by quincyjones on 2006-04-23
Hey, Thanks for all the replies!
This (from Peacepunk) sorted me out:
[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)
but clearly other ways will work too!

:KS

---

