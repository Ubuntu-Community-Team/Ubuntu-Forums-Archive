---
title: "dual monitors, displaying different workspaces at different resolutions"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by radradrobotanks on 2007-06-24
Okay, Ive got a different plan now. Im going to but a 7600gt 256 AGP nVidia graphics card. Since I'm doing this i might as well use Twinview. Is it possible with Twinview to use a widescreen screen and a normal aspect ratio screen together? Can I have both screens at the native resolution without without any black bars cutting my normal aspect ratio screen down to a wide screen aspect ratio? I don't want to display one program across both screen. I would like to display mythtv on my widescreen while displaying a normal desktop on the other normal aspect screen both using there native resolutions without any black lines. Is this possible?

Thanks

Old post (don't bother reading):

I have recently installed Myth tv (first challenge with Ubuntu (wasn't 2 hard)). Myth tv has proved very successful and I often find myself competing with my family for use of my pc. I have 2 screens the first is a 19 inch lcd monitor the second is a 42inch lcd monitor (both have DVI-I inputs). When the family wants to watch tv I start up Myth tv and connect my pc to the larger 42inch monitor. When I want to do work I connect the pc to the 19inch monitor. This is fine unless I want use the pc for work when my family is using my pc for Myth tv.

I've looked into a few solutions. Setting up a multi seat pc would be ideal but it seems very complicated. Another option would be to set up the 2 monitors as dual monitors. If possible I would have one display displaying workspace 1 with Myth tv running and the other display displaying workspace 2 containing my normal work apps (with one keyboard and mouse controlling both monitors (disadvantage compared to a multiseat setup)). To complicate things further the monitors have different native resolutions.

At the moment I have a 9700pro ATI card. I'm looking to upgrade my graphics card to accommodate more recent games and because nVidia cards are better supported to a 7600gt AGP 256MB Point Of View (this card has 2 outputs 1*D-sub and 1*DVI-I).

My questions:

Can you think of a better way to solve my problem (please explain)?
Are the above cards alright for dual monitor setups (both have 2 output 1*D-sub and 1*DVI-I)?
Is it possible to run a separate workspace in each screen with each workspace set at different resolution?
If possible how is it possible?

Thanks

---

### Post by radradrobotanks on 2007-06-24
I've had a look around it seems that Xinerama should do what i want (two screens in two separate X-windows). I will give it a go tomorrow!

Can Xinerama do what I want?

---

### Post by Ziox on 2007-06-24
You can do something similar to Xinerama.  If you are following any Xinerama guide, comment out the line

option "Xinerama" "true" or something equivalent to that.

The result would be 2 different X-sessions.  The difference would be that you cannot drag windows from one monitor to another, however, you would have 2 separate X-Windows.

Good luck!

---

### Post by radradrobotanks on 2007-06-24
deleted - added to top post

---

### Post by Ziox on 2007-06-25
> **radradrobotanks said:**
> Okay, Ive got a different plan now. Im going to but a 7600gt 256 AGP nVidia graphics card. Since I'm doing this i might as well use Twinview. Is it possible with Twinview to use a widescreen screen and a normal aspect ratio screen together? Can I have both screens at the native resolution without without any black bars cutting my normal aspect ratio screen down to a wide screen aspect ratio? I don't want to display one program across both screen. I would like to display mythtv on my widescreen while displaying a normal desktop on the other normal aspect screen both using there native resolutions without any black lines. Is this possible?

Thanks


Yes it is possible, and not only that, it is extremely easy (at least easier than Xinerama).  If you are using Twinview, simply configure it through nvidia-setting gui.

gksudo nvidia-settings

you should have no problem with Twinview.

---

### Post by dodgePT on 2007-06-27
Sorry to invade your thread, but i have exactly the same setup as you do radradrobotanks.
Only difference is i own an ATI 9600 pro (thankfully, not for long). What would be the best choice for me?

I'd prefer the Xinerama solution, i'm using open source drivers (radeon) and AIGLX and running compiz fusion.
_Anyone managed to do it_?

I tried it some months ago but gave up on it (always got the same resolution on both displays).

---

### Post by andersja on 2008-05-13
There's a brainstorm idea to make this easier: please check it out and vote it up if you think it's a good idea...

[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

