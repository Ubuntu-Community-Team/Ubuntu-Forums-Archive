---
title: "Camcorder will not mount"
date: 2011-05-24
forum: Multimedia Software
---

### Post by anthony2010 on 2011-05-24
Hi All

I installed Ubuntu Studio because Im interested in film making. (Social commentary / Social Psychology)

The thing is, I can't seem to get my camcorder which is a Sony trv 620 e to be even seen by the system. It doesnt appear on lspci, when its switched on, Ive started both Kino and Kdenlive as root and not as root, nothing.

Ive trawled the forums and am still in the same boat. In Synaptic, Ive ticked everything to do with IEEE 1394 too!

So in the end, Ive had to post this appeal for help.

Any suggestions anyone? (I cant afford a new camcorder and this one, whilst old takes beautifully clear moving images on digital8tapes.)

Ant.

---

### Post by no2498 on 2011-05-25
this may or may not help
with the cam pluged in an turned on 
open a terminal type dmesg click enter
i do not know if this finds fire wire or not
after dmesg stops type lsusb click enter


dmesg should install a cam graber

---

### Post by anthony2010 on 2011-05-26
Hi there.

Thanks for the idea. Sadly it didn't solve it.

Ive learned that the usual dv programs wont work as my camcorder uses a cassette and that its the AV/C method that's needed. I wish this was simpler!

Iv'e been at this for weeks!

Ant

---

### Post by no2498 on 2011-05-27
you try looking in your package manager for webcam 
if you click on a program it tells you what it uses
ive not looked for av yet

---

### Post by j_the_bear on 2011-06-27
Actually Kdenlive makes it simple.... your camera may not show up in on the computer like it is mounted. the same thing happend to me and I thought that I needed some special software or something. turns out I just needed to press the correct buttons.

1:simply start up kdenlive click the "Record Monitor" tab underneath the clip monitor.
2:turn on your camera (if thats what you normally need to do)
3:click the "connect" button with the little green check mark.
**no mounting neccesary**. (as long as your using firewire then it probably should work that easily.)

---

