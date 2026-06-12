---
title: "Uninstalling VIA Drivers, Installing NVIDIA Drivers Question"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by cf1709 on 2007-11-05
I just bought this 6200 card and I want to install it.

*Do I need to uninstall VIA Openchrome drivers (Former to-be video adaptor)? (I used Tuxcrafter's script). If so, how?
*Is the 6200 well supported in Ubuntu?
*Is Tseliot's script enough to make this card run well enough?

I hope you answer these questions of mine. Good day.

---

### Post by kwacka on 2007-11-11
Just add the nVidea card & switch on.

You'll find you won't get a GUI, just log in with your user name/password. 

Then type 'sudo sudo dpkg-reconfigure xserver-xorg'. and work through. When you get to graphics card select 'vesa'.

If you get an error that xserver-xorg is not installed, sudo apt-get install xserver-xorg-all and continue.

Type 'startx ' and (hopefully) Xwindows will start. 

If you are using 7.10 Gutsy a 'restricted drivers' applet will appear in the tray. Click on this and select nVidea drivers. Press ctr, alt and backspace to re-start xwindow.

---

