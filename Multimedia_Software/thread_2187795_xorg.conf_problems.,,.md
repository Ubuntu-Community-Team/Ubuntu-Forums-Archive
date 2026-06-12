---
title: "xorg.conf problems.,,"
date: 2013-11-13
forum: Multimedia Software
---

### Post by Hvidemose on 2013-11-13
Hey


Can anybody help me toconfigure my xorg.conf file? I had a lot of problems to restore it. Now I got t restored, but it doesn't seem like its proper suited. I have a problem with my HDMI that I cant get to work. Im running the native intel video card, and a Nvidia optimus with Bumblebee.


```
[COLOR=#2e8b57][FONT=Monaco]00:02.0VGA compatible controller: Intel Corporation 2nd Generation CoreProcessor Family Integrated Graphics Controller (rev 09)[/FONT][/COLOR]
[COLOR=#2e8b57][FONT=Monaco]01:00.0VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT520M] (rev ff)[/FONT][/COLOR]
[COLOR=#2e8b57][FONT=Monaco]whiteboy@[/FONT][/COLOR]

```[COLOR=#000000]
[/COLOR]
[COLOR=#000000][FONT=Monaco]Ithink it might help if the video cards to run on the same "bus id", But Im not sure. Anyway, it would be nice to have the xorg.conf put together in a prober way.[/FONT][/COLOR]
[COLOR=#000000]
[/COLOR]
[FONT=Monaco][COLOR=#000000]Can any one help me with a fast, easy and functional setup?[/COLOR][/FONT]

---

### Post by Yellow Pasque on 2013-11-14
Unfortunately, it doesn't work seamlessly: [http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

---

### Post by Hvidemose on 2013-11-14
Aha, thanks. I guess im going to use windows for these things :-(

---

