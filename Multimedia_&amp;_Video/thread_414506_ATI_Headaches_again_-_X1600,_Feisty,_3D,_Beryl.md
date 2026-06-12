---
title: "ATI Headaches again - X1600, Feisty, 3D, Beryl"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by grahams on 2007-04-19
I've have an hp nw8440 which is working great on feisty apart from a couple of issues, this being 1 of them.

The laptop has an ATI x1600 controller, the lspci output is
VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

I believe the nasty folks at ATI refuse to give out the specs of these new chips so the open source drivers can't work and I have to use flgrx. 

I've followed the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) but it still doesn't work correctly. 

My fglrxinfo output is :
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Which means no 3D rendering and no point even trying beryl. 

What am I missing?

---

### Post by grahams on 2007-04-20
If like me you get headaches due to ATI propriety drivers go to  [http://www.PetitionOnline.com/x200MLin/](http://www.PetitionOnline.com/x200MLin/) and let them know your frustration.

---

### Post by taipoh on 2007-04-20
> **grahams said:**
> I've have an hp nw8440 which is working great on feisty apart from a couple of issues, this being 1 of them.

The laptop has an ATI x1600 controller, the lspci output is
VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

I believe the nasty folks at ATI refuse to give out the specs of these new chips so the open source drivers can't work and I have to use flgrx. 

I've followed the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) but it still doesn't work correctly. 

My fglrxinfo output is :
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Which means no 3D rendering and no point even trying beryl. 

What am I missing?

That guide has poor organization.  Confirm that you performed the "pre-installation instructions" as well as the "post installation instructions."  These two instructions are in separate places.  If you didn't run the extra commands in those instructions before, just run them now and restart.

Also, find restricted drivers and confirm that fglrx is set to "enabled."

---

### Post by grahams on 2007-04-21
Thanks for the reply. I'll will look at the guide one more time. I wonder if my problems may be due to me breaking something in my xorg.conf file (can see anything obvious in the logs. Do you have a similar ATI driver working correctly on feisty?  If so any chance up could attached or xorg.conf file.

---

### Post by taipoh on 2007-04-21
> **grahams said:**
> Thanks for the reply. I'll will look at the guide one more time. I wonder if my problems may be due to me breaking something in my xorg.conf file (can see anything obvious in the logs. Do you have a similar ATI driver working correctly on feisty?  If so any chance up could attached or xorg.conf file.

Sure.

---

### Post by grahams on 2007-04-25
Thanks, I got around to trying your xorg.conf and fglrxinfo now looks good. 

do you have beryl working with fglrx?

---

