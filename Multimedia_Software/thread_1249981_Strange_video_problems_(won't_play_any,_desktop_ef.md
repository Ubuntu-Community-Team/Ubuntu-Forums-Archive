---
title: "Strange video problems (won't play any, desktop effects not working, etc)"
date: 2009-08-26
forum: Multimedia Software
---

### Post by hairlesshairball on 2009-08-26
I have Ubuntu 9.04 installed on my Compaq c303nr and today, after deciding to hook up my second screen for some work I was doing, my video settings kinda fizzled out. I am new with linux, so I apologize now if I ask ya to dumb something down or translate, but how do I make it work again? Desktop effects will not work (they worked perfectly before hooking up the second screen), videos will NOT play, scrolling with anything is horribly laggy. Its like there is no video driver installed or something like that.

I tried to search on the forums for something before I posted, but found nothing related (or at least I am unsure waht to search for). I ran 

lspci |grep VGA 

in terminal and that spat out 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I hope you understand what I am trying to say =/
I request assistance!

---

### Post by inobe on 2009-08-26
welcome to the ubuntu forums, sorry to hear of this.

go to system> preferences> display

what do you get there, is it showing your screen' or is it the external.

---

### Post by hairlesshairball on 2009-08-26
I forgot to mention this: I unplugged the extra screen a while ago, as it was not needed for casual internet browsing and what not. Not to mention I had to use the laptop somewhere else and I could not bring the screen with me. Anyhoo, it knows that its using the internal screen and that no other screens are attached

---

### Post by inobe on 2009-08-26
is the resolution correct at least ?

i am uncertain what went wrong, it sounds as if your internal monitor mirrored with the external...

it could have borked your xorg.conf

if you've rebooted since and are certain display shows your monitor' try reconfiguring xserver, you can do this by running

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

in terminal and hitting enter.

when done' reboot

you should then see improvement.

---

### Post by hairlesshairball on 2009-08-26
Aha! What you did fixed it! Thanks man! Now I can finish watching that monk episode tomorrow after class =)

---

### Post by inobe on 2009-08-26
the external monitor wrote some crap to your xserver/ xorg.conf file !

i don't know what' how it happened.

remember that command if it breaks again.

have fun

---

