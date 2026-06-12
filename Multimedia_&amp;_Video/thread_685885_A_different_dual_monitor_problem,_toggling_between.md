---
title: "A different dual monitor problem, toggling between single and dual display?"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by lewcid on 2008-02-02
Hi everyone,

I'm a long time Windows user switching to Ubuntu 7.10 (Gnome) and have almost made a successful transition but need a little help. I have successfully got dual monitors working, where one is the built in display of the laptop and the other an external 22" LCD. The LCD is connected when the computer is docked.

The problem:
[LIST]
[*] Most of the time the computer is used while docked, with the external LCD connected. However, if I boot the computer while undocked without the external LCD, Ubuntu still maintains the combined resolution for both monitors and it pans across the laptop screen. I cant reduce the resolution to 1200x800 when this happens. Is there some way to switch between two 'profiles', one dual display and one single? A bash script perhaps?
[*] Similarly, if I undock the laptop while it is switched on, I'd like to easily be able to switch to single monitor, and then back again later.
[/LIST]

So far I have a clean install of Ubunty 7.10, fully updated with proprietary Nvidia drivers installed. I'm using TwinView configured with nvidia settings. The built in Gnome display applet seems to disrupt any display settings whenever used so I am trying to steer clear of it.

The hardware: Nvidia GeForce 8400M GS, laptop LCD 1280x800, 22" HP 2207 LCD 1690x1050.
In TwinView the external LCD is on the left and used as the main screen.

I'd really appreciate any help with this. Many thanks,

Saq

---

### Post by paneves on 2008-03-27
Hi:

I don't know if you've solved your problem yet, but in case you didn't here goes some ideas.
- I think the nvidia driver should automatically detect what setup do you have and adjust accordingly. I don't thinks there's a need for a script

- can you post you xorg.conf (/etc/X11/xorg.conf)? I'd like to see what settings you have

Regards:

Pedro

---

