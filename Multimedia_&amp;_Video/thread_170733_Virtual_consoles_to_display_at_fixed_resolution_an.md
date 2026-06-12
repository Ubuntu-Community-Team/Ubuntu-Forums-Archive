---
title: "Virtual consoles to display at fixed resolution and frequency"
date: 2006-05-05
forum: Multimedia &amp; Video
---

### Post by Rasitiln on 2006-05-05
I have a Sun GDM 20D10 moniter its really nice and has a crisp display the only issue is that its fixed frequency. So it will only do certain resolutions at a fixed refresh rate. As it stands now Ive got gnome working great with it. The only issue is when I ctrl+alt+f1 to my first virtual console i get gibberish on the screen because its not displaying at the right refresh rate/resolution. Id like to make my vitrual consoles display at 120x1024@75hz does anyone know how I would go about doing that?

Thanks in advance

---

### Post by Rasitiln on 2006-05-07
anyone?

---

### Post by aarbear26 on 2006-05-13
just a gues but i think if you set your refresh rate in x to that fixed refresh, you should be ok

you need to run:

sudo dpkg-reconfigure xserver-xorg

Most of the blanks you can breeze through becuase you probably won't need them, but when it gets to the moniter settings, put and asterik next to the modes you need.
Then you'll get another screen about moniter stuff, answer no to the auto detect and then use advanced when the Simple, medium, advanced prompt comes up.   
Input the refresh rate you need.  

then type

sudo /etc/init.d/gdm restart

(you may have to login in text mode, if it doesn't start the GUI environment, just type gdm at the prompt again)

you may need to reset the rate when you get into the GUI but this should work since i think the terminals are still ran by Xorg.

hope that helps

---

