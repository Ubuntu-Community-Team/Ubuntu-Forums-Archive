---
title: "volume controls are not working"
date: 2014-05-02
forum: Multimedia Software
---

### Post by cicada2 on 2014-05-02
I am new to Lubuntu, but it's so nice to be free from windoze xp. 

I fired up **Audacious** and the volume is over the top. I use headphones while working, but I still need to mute or reduce the sound to save my ears from time to time. Nothing seems to take the sound down , so what am I missing?
[LIST]
[*]There is an icon at the bottom of my desktop for volume, but it is not working (goes from too loud to extremely loud). Also "mute' does not work).
[*]The [manual] volume controls on my laptop are same as above (goes from too loud to extremely loud). Also "mute' does not work).
[*]The volume control in audacious is not working either.
[/LIST]

Thanks in advance.
******************************************
I found a solution by tweaking preferences. The "mixer element" needed to be switched to headphone. Once i changed that, the volume control could be changed in Audacious. And... I could also mute the speakers on the laptop with the volume control that's located on my desktop.

---

### Post by ronb19495 on 2014-05-03
try alsamixer my default seettings on alsamixer master was full on
just type alsamixer in terminal if its not installed sudo apt-get install alsamixer

---

