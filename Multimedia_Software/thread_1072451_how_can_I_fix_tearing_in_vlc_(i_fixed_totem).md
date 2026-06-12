---
title: "how can I fix tearing in vlc (i fixed totem)"
date: 2009-02-17
forum: Multimedia Software
---

### Post by mishkin on 2009-02-17
in totem I had to do gstreamer-properties 

and under video select "X window system (X11/Xshm/xV)" and then as a sub selection "intel textured video"

I can't find no similar option to this  textured video in vlc... 

I'm running 8.10 unr eee ubuntu on a 1000H eee asus laptop

Thanks to anyone who can help, because I'd really love vlc so my subs work and I can actually fix sync issues on the go in realtime

the sync fixes that the scene release don't' want to work on linux even with wine and extra windows codexs installed :(

thx again a million

---

### Post by mishkin on 2009-02-18
anybody?

---

### Post by binbash on 2009-02-18
There is , go to preferences and it is under video section

---

### Post by BwackNinja on 2009-02-22
Tools > Preferences

Change "Show settings" (at the bottom left) from simple to all.

Go to Video > Output Modules > XVideo

Change XVideo Adapter Number to 1

Enjoy

---

### Post by mishkin on 2009-02-28
thx for the help but i don't see that option (not simple)

maybee because my screen is 1024 x 600 (not tall enough)

any idea how I can shrink vlc's menu or move it above the screen itself to see the bottom?? (I already moved out the menu bars)

see pic here 

[http://personal.nbnet.nb.ca/eliakd/dammit.jpg](http://personal.nbnet.nb.ca/eliakd/dammit.jpg)

-------------

edit: I fliped my screen left and that way I coudld see it :)

my god  is it hard to naivgate the mouse like that, you go down it goes left

----------

edit: BwackNinja I did what you said, it was -1 I changed to +1 (without the +)

will test it out

-------

edit: changes wern't saved couldn't see save button went back and did it again, thi time i flip screen left then put the laptop on it's side turned left so I could use the mouse lol, so much easier to use the mouse

---

