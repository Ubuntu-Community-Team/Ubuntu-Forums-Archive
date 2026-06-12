---
title: "No Front Headphones Audio - Ubuntu 12.04"
date: 2012-09-15
forum: Multimedia Software
---

### Post by zax0rz on 2012-09-15
Hello,

I am a total Ubuntu newbie, running 12.04 exclusively.

There is no headphones audio in the front port of my desktop. Interestingly, when I unplug my speakers from the back and plug my headphones in, audio works fine.

I'm not sure what logs or other diagnostic information is necessary, but I could use some help.

Thanks!

---

### Post by JHAx86 on 2013-02-16
EDIT: Maybe you want to try this first, as does not require a restart

Install the alsamixer gui
$ sudo apt-get install alsamixergui

Then launch the alsamixer (Note: is not a typo, you want to launch alsamixer, not alsamixergui)
$ alsamixer

Set INDEPENDENT HP to OFF if not already
Set Loopback to ON

The reason to use alsamixer and not alsamixergui is because the later won't show these controls.

Note, you probably won't see these controls I'm talking about, pay attention to the right border of the alsamixer window, to highlight controls you use the left and right arrows of the keyboard, but the showing controls are not the only ones, continue to the right and new controls will appear. When "Independen HP" is highlighted, press "Q" to turn it off. When "Loopback" is highlighted press "Y" to turn it on.

[IMG]http://img845.imageshack.us/img845/1694/capturadepantallade2013q.png[/IMG]
Image source (in case you can't see the image: [http://imageshack.us/photo/my-images/845/capturadepantallade2013q.png/](http://imageshack.us/photo/my-images/845/capturadepantallade2013q.png/))

---

