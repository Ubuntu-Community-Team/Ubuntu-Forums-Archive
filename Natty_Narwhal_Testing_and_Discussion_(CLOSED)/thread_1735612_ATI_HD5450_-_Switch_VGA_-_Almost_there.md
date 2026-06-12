---
title: "ATI HD5450 - Switch VGA - Almost there"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tembares on 2011-04-21
Thank you for reading my post. I hope you help me with the final touch.

I am a little bit confused about getting my ATI HD5450 work.

- Do I have to activate the ATI prop driver or the open source one ([http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)).

Now with the ATI prop driver de-activated and un-checked Sync to VBlank in CCSM - OpenGL I get a text mode on my HDMI device (my TV).

If I use 'sudo switch_between_cards' and follow what happened in dmesg I get the following error:

[ .. ] vga_switcheroo: client 1 refused switch
[ .. ] vga_switcheroo: setting delayed switch to client 1

I have to use 'sudo ' to get 'switch' and 'switch_between_cards' work.

If I restart the Ubuntu splash is visible on my monitor and HDMI-device (my TV).

---

### Post by Starks on 2011-04-21
Use the 10.4 Catalyst. It has switching.

---

### Post by tembares on 2011-04-21
Thank you for your answer.

I red on several places not to use Catalyst :-s

In addition to my previous post I get the text mode on HDMI when I have a terminal opened on my laptop screen and when opened press ALT+CTRL+F1 or ..+F2.

By pressing ALT+CTRL+F7 I come back in the graphic mode on my laptop screen.

Thank you in advance

---

### Post by cariboo on 2011-04-21
> In addition to my previous post I get the text mode on HDMI when I have a terminal opened on my laptop screen and when opened press ALT+CTRL+F1 or ..+F2.

You'll get the same result even without a terminal open, Ctrl-Alt-F1 - F6 are consoles.

---

### Post by tembares on 2011-04-21
> **cariboo907 said:**
> You'll get the same result even without a terminal open, Ctrl-Alt-F1 - F6 are consoles.

Thank you for your answer.

But do you also know how I can get the graphic mode on my HDMI :-)

---

