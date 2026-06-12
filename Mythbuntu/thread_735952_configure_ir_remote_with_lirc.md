---
title: "configure ir remote with lirc"
date: 2008-03-26
forum: Mythbuntu
---

### Post by Kreker on 2008-03-26
Hi. I found a nomark ir remote. It's similar to whe windows media center edition, but htere isnt any type of model or mark, only OVO 4001. The system recognize it and I able to use a few buttons, but what about the other one? How can I map all the keys?There is any type of scanner?
Thanks

---

### Post by majoridiot on 2008-03-26
> **Kreker said:**
> Hi. I found a nomark ir remote. It's similar to whe windows media center edition, but htere isnt any type of model or mark, only OVO 4001. The system recognize it and I able to use a few buttons, but what about the other one? How can I map all the keys?There is any type of scanner?
Thanks

open mythbuntu-control-centre and click on remote.  in the pane to the right, try setting it up as a
windows mce remote (either new usb or older style) in the dropdown list and make sure the dynamic
button mapping box is ticked.  after you apply it, it will have generated an .lircrc file in your home 
directory with default button mappings for the remote.  you can edit this (as sudo) to make whatever
changes you need.

---

### Post by Kreker on 2008-03-27
yes, already do that.
btw not all the buttons of the remote are mapped, only a few.
I try to the jump editing but the button arent recognized at all!
how to map these?

---

### Post by laga on 2008-03-27
Use 'irrecord' to generate a new lircd.conf. Then submit it to [https://bugs.launchpad.net/ubuntu/+source/lirc](https://bugs.launchpad.net/ubuntu/+source/lirc)

---

### Post by majoridiot on 2008-03-27
> **Kreker said:**
> yes, already do that.
btw not all the buttons of the remote are mapped, only a few.
I try to the jump editing but the button arent recognized at all!
how to map these?

open a terminal window and run **irw**.

press each remote button one at a time, and see if all of the buttons report a keypress.  if they do, then
all you need to do is edit your .lircrc file to assign the buttons with the functions you want.  if some of the 
buttons do not register with irw, then do as laga recommended.

the default mappings are just that- defaults- and do not suit every remote in the family or the tastes of the 
user.  you can find more info on how to edit the .lircrc to assign buttons to functions, here:

[https://help.ubuntu.com/community/InstallLirc/Gutsy#head-5f86c6eebe85acb0155aa33e44f3d18015210f3d](https://help.ubuntu.com/community/InstallLirc/Gutsy#head-5f86c6eebe85acb0155aa33e44f3d18015210f3d)

and 

[http://mythtv.org/wiki/index.php/LIRC#LIRCRC](http://mythtv.org/wiki/index.php/LIRC#LIRCRC)

---

