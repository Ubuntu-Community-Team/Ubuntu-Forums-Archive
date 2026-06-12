---
title: "Second Modeline"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by daught on 2008-01-07
I have an extended dual-head set-up. They are two identical projectors. I want them each to run at 1400x1050. For 1400x1050 I need to send a Modline. I am tryong to set a Modeline for each projector but only the first one receives it. The second one does not get the modeline and runs at 1280x1024. 

Here is my xorg log. You can see the second modeline is not received.
[http://pastebin.com/m11074f84](http://pastebin.com/m11074f84)

Here is my xorg config.
[http://pastebin.com/m230a5c36](http://pastebin.com/m230a5c36)


If I use 
Screen "Screen 1" 0 0   
Screen "aticonfig-Screen[1]" Leftof "Screen 1" 

The second modeline is received but the second projector is not accelerated.

---

### Post by daught on 2008-01-07
If I use two video card for dual-head can I get acceleration on both if I use two screens in xorg.conf and xorg's internal xinerama.

---

