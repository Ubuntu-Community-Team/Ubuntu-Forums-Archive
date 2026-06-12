---
title: "cinelerra or lives for 7.10"
date: 2008-08-08
forum: Multimedia Software
---

### Post by jnvta on 2008-08-08
[FONT="Courier New"][/FONT]I need to install either cinelerra, or lives ( any opininions on these much appreciated ) any how, when i look in synaptics, it shows all the other stuff that will need to be updated as well...and it is ALOT. I've had many problems with updates lately, so IM a little relutant...but question is: will cinelerra work with ubuntu 7.10 ? I just need very basic video editor...and after days of trying to get kino to work, it just cannot read my camera type codecs. thanks for any input.

---

### Post by mateuszbaranski on 2008-09-11
If you need "very basic video editor" cinelerra for sure is not for you. 
Cinelerra works fine in 7.10 (better than with 8.04)

Basic video editor is Kino  which works fine with camcorders but when you run kino in root mode. So just type in terminal sudo kino &
Why? - the /dev/ieee1394 needs super user mode in 7.10. I tried to use it in user mode but after several days I quit. So when I worked on 7.10 I run kino in super user mode, captured data from camcoredr. Then sudo chown -R whole folder with captured data and since then you can work in normal user mode.
In 8.04 this issue no longer exists  - I can work with kino in user mode.


That's it!

---

