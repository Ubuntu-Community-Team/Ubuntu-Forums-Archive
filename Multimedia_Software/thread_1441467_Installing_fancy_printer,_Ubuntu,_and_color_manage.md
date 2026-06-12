---
title: "Installing fancy printer, Ubuntu, and color management"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Rocket J Squirrel on 2010-03-28
...so my last experience with Unix was in the '80s, and it was  plain-vanilla CLI, none of this fancy GUI stuff. Between then and now,  I've been running Windows. 

For fun, I decided to wubi Ubuntu onto this little netbook I got for  $350 and take it for a test drive. There's been a bit of a learning  curve, not too bad. Ubuntu broke itself with a failed update (I had to  strip off the Ubuntu partition and start fresh), and the wireless card  took some work to get working dependably. 

But all and all, it words as advertised. 

One of the tasks I set out to do today was to connect Ubuntu to an Epson  Stylus Photo R2400 printer which is networked on a Windows computer.  Out of the box, Ubuntu did not seem to know about this printer. Googling  around, I learned about the _Gutenprint_ project which provides  high-quality drivers for printers in the Unix/Linux operating system. 

I downloaded the tarball, studied the documentation and followed the  instructions. Terminal was very busy for a while. (I probably could have saved myself some trouble by using  the Synaptics Package Manager to install the drivers.)

But here's the bottom line: when I went to add a new printer, Ubuntu  found the shared printer, and (via Gutenprint) had a driver ready to go.  A few clicks later, the R2400 was connected and ready to go.

Very rewarding!

_Next step_: Copy my custom R2400 printer profiles from my Windows machine onto the Ubuntu  machine, and learn how to do color management in  GIMP -- I'm a Photoshop guy.

---

