---
title: "Ubuntu on HDTV possible with component cables?"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by Dekunuts on 2007-01-04
Hi, I want to use my computer on a 1366x768 Philips HDTV. I am using a radeon X700pro, the card came with component cables and it actually works for the most part. Except for the fact that I can only choose 640x480 resolution. Now, using a normal screen via VGA or DVI-I you have to change the xorg.conf file so it knows the horizsync etc of your screen. I do not want to break the file and my question actually is if I need to edit the same file and if those settings will then be used for the component output by default.

Although my question ends here, I would like to say I'm really pleased with the fact that Ubuntu immediately used the component output, that's great and I didn't expect it !

---

### Post by Dekunuts on 2007-01-04
Since once again I'm not getting any answers I decided to go ahead and modify the xorg.conf anyway. I could not find the correct values for my tv (philips 42PF7621D/10) anywhere so I used one of those websites that give you the information when you enter the resolution and refresh rate. Maybe those values are wrong, but I can't get the resolution any higher then 640x480. It is as if my entered values are being ignored because the choices in the screen resolution options never change. Does anyone know what I need to do ?

---

### Post by seuaniu on 2007-01-04
Hi!

I can't answer anything about output over component cables, since I don't know - my tv has a vga adapter :)

Regarding your xorg.conf, making sure that you back it up before you edit it will ensure that you can restore later if you mess up the config.  As far as your edit goes, did you know that you need to restart the X server when you make changes to its configuration?  This can be accomplished by either 

a) rebooting your computer, or 
b) logging out and using the key combo ctrl-alt-backspace.


according to [this page]("http://uk.insight.com/apps/productpresentation/index.php?product_id=PHIDI7621D"), your tv supports 1280x1024 and the vga that your stuck with.  I couldn't tell from your post, but attempting to set it at its native resolution (1366 x 768) could cause it to throw an error and revert to vga.

---

### Post by Dekunuts on 2007-01-04
it does not give an error, but I'll try setting it up using the 4:3 resolution right away..and thanks

---

### Post by Dekunuts on 2007-01-04
Ok, so I did sudo dpkg-reconfigure xserver-xorg after booting in command line mode and set everything up again to make sure the xorg.conf was 'clean'. I chose 1280x1024 as the default resolution there and left the 1280x768 (closest to 1366x768)  out. Then I rebooted and now, the screen runs in widescreen 720x480 by default. So that's not 16:9 but a 1.5 ratio. The only other option is 640x480. This is an improvement but still far  from optimal. What also bothers me is that this just happened and I do not know why exactly. So, any further advice ?

As said before, I can't find the correct values for this screen that need to go in the xorg.conf file. I'm probably a bad searcher :-? (horizsync and vertrefresh is what i mean). Maybe that is the only problem but I don't know.

---

### Post by seuaniu on 2007-01-04
Unfortunately, I don't have much else to suggest :???: 

I did find a spec sheet on your tv that might shed some light on things a bit.  According to [this pdf]("http://www.p4c.philips.com/files/4/42pf7621d_10/42pf7621d_10_pss_eng.pdf") you have a refresh rate of 60Hz.   

One thing that I do find wierd though, is that phillips gives you a 4:3 desktop resolution on a 16:9 television.   My tv suggests a desktop resolution of 1280x768.  setting up odd screen resolutions can mess up your screen though, so if you try it out and break it, you get to keep both pieces.

Wish I had a magic bullet answer for ya.  Good luck.

---

### Post by Dekunuts on 2007-01-04
Thank you for your troubles, unfortunately i had that spec sheet (in my own language but it has the same content) and it didn't help me. 
Hn, I'll just leave it then, it's not like I absolutely need it, although it would have been nice. Maybe it has something to do with the 1366x768 resolution screen that is, if I'm not mistaken, only used in Europe. 
Maybe newer versions of ubuntu or drivers will automatically handle this kind of things in the future...

---

### Post by NT4usB on 2007-01-04
fwiw...
To make my TV work via component out, I had to add an option to screen in xorg ```
Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVStandard" "HD480i"
    bla bla bla
EndSection
```
Mind you, this is for a nvidia card and pos 4:3 tube but might give a new direction to look...
ymmv.

---

### Post by Dekunuts on 2007-01-05
Hn, my holiday is almost over so I can't begin working on it right now, but I'll check it out soon, thank you, it could help !:)

---

### Post by Zer0Nin3r on 2007-01-14
> **seuaniu said:**
> Hi!

I can't answer anything about output over component cables, since I don't know - my tv has a vga adapter :)

Regarding your xorg.conf, making sure that you back it up before you edit it will ensure that you can restore later if you mess up the config.  As far as your edit goes, did you know that you need to restart the X server when you make changes to its configuration?  This can be accomplished by either 

a) rebooting your computer, or 
b) logging out and using the key combo ctrl-alt-backspace.


according to [this page]("http://uk.insight.com/apps/productpresentation/index.php?product_id=PHIDI7621D"), your tv supports 1280x1024 and the vga that your stuck with.  I couldn't tell from your post, but attempting to set it at its native resolution (1366 x 768) could cause it to throw an error and revert to vga.

Thanks for the tidbit.

---

