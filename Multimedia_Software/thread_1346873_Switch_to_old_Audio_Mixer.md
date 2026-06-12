---
title: "Switch to old Audio Mixer?"
date: 2009-12-05
forum: Multimedia Software
---

### Post by Kdar on 2009-12-05
Maybe the new audio setting is ok... but it would be nice to have more control like in the Audio Mixer in Ubuntu 9.04

Anyone know if I can get it back on Ubuntu 9.10?


(I know I can do settings on alsamixer in terminal, but it would be nice to have old gui audio mixer as well.)

---

### Post by Lyon on 2009-12-05
You can install gnome-alsamixer from apt

---

### Post by robusat on 2009-12-06
I also want to use the old mixer, the new is not as good. Have tried all of the mixer in the program installer (including the mentioned gnome alsa mixer) and its none of them. So what was the name of the mixer in 9.04 :confused::confused::confused::confused::confused:

---

### Post by robusat on 2009-12-06
Might as well reinstall 9.04 cant find any way of getting the sound control back :frown:

---

### Post by Kdar on 2009-12-10
Yes... gnome-alsamixer is a little different. I think.

Mixer in 9.10 just sucks.

---

### Post by chillicampari on 2009-12-10
I'm not using Alsa, Pulse, 9.10 *or* the Gnome desktop right now, but I'm wondering if something like this would work (I saw it mentioned on an OSSv4 board and am using it in place of the ossxmixer):

[http://www.xfce.org/projects/xfce4-mixer](http://www.xfce.org/projects/xfce4-mixer)

Ideally, I think it would display all of the options available with the Alsa command line mixer (you may have to set it up a bit in options, at least I did with OSSv4 to see what I wanted).

It does pull in some elements from the Xfce desktop, but not to where I've noticed (I'm using Crunchbang 9.04 with Openbox). And I don't know if the xfce4 panel it brings with it could conflict with Gnome. Have no idea. It might not work with Pulse at all, or might just break everything, but I'm just tossing the idea out there for those who might be looking to play with things to see if it works. I think it's in the 9.10 repos but not totally sure.

If you're not comfortable with possible breakage I wouldn't try it. ;)

---

### Post by cbl016 on 2009-12-10
With 9.04 and the old mixer I had mic pass through working and with 9.10 and the new mixer I can't get it to work. Has anyone found out how to do this with 9.10?

---

