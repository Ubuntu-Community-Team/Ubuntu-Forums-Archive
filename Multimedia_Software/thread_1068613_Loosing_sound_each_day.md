---
title: "Loosing sound each day"
date: 2009-02-13
forum: Multimedia Software
---

### Post by GuiPoM on 2009-02-13
Hi !

I run an Ubuntu 8.10 (upgraded from a 8.04) on a Dell Precision T3400.

guipom@hal:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : AD198x Analog [AD198x Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0

It works correctly just after a fresh reboot. Each night I lock my computer (gnome screensaver) and each morning I loose sound (my computer beep instead of having a visual bell, and within sound from the preference panel, I get an error:
[[IMG]http://img172.imageshack.us/img172/8499/audiobugwb7.png[/IMG]](http://imageshack.us)
[[IMG]http://img172.imageshack.us/img172/audiobugwb7.png/1/w622.png[/IMG]](http://g.imageshack.us/img172/audiobugwb7.png/1/)

No more sound in software such as Firefox. I have to reboot ...

Any help to find out why sound fails each night ? (I guess this is not a powermanagement issue, my computer does not suspend during night).

Thanks for your help ;)

---

### Post by hordur on 2009-04-13
I'm having this exact same problem. I also have a Dell Precision T3400 and am running Ubuntu 8.10.

I am sometimes able to recover sound without restarting by doing 
```
killall pulseaudio
```
in terminal and then run
```
pulseaudio --daemonize
```

and then I have to restart Firefox to get audio working in it.

If anyone does know how to fix this properly, it would be greatly appreciated! :)

...otherwise I'm just hoping this will not be an issue anymore in the upcoming 9.04 :)

---

