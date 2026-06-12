---
title: "New ATI driver install help"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by Heyday on 2007-07-26
I am trying to install the new ati driver version 8.39.4 on my HP laptop with ati xpress 200m video.  I have followed the instructions on the ati driver wiki site,  and I can't get the 3D acceleration to work.  When I do the fglrxinfo command it returns this:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

It should be the ATI and not the mesa.

Can anyone help me with this?

Also, when I try to run sudo aticonfig --initial --overlay-type=Xv, it returns this:

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

---

### Post by colsandurz on 2007-07-27
I'm having the same problem... If I can find a solution I'll let you know

When you try to install does it tell you you already have the driver?

---

### Post by malocite on 2007-07-27
Forgive me, I am very new to linux as well, but I am working on a similar issue.  I have a radeon 9000 and it did NOT work with the 8.39.4 driver, are you sure your card will work with that driver?  My computer requires the 8.28.8 driver if I want to use ATIs.  I also had to downgrade my X.org to 7.1 from 7.2 in order to install it.  

I eventually had to remove the driver because I have a dual view setup.  One 26" lcd monitor and my 32" television that is connected via s-video.  When I had the television connected the tv displayed properly, however the monitor brightness went nuts, super bright, I couldn't adjust it or anything to fix the problem.

If someone knows how to get around THAT problem then I can get my dual view running.  Now I am using the open source drivers, picture is fine, but no tv out support works so far.  

If someone can help I would really appreciate it.

--malocite

---

### Post by botulismo on 2007-07-27
If you check out the release notes [there]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.39.4.html") you will see which cards are supported. Essentially everything above the 9500 "should" work.

Also, I don't believe the Mesa drivers support TV out. I had a Radeon 9250 and I couldn't get TV out to work even with the proprietary drivers, where they are supported! Way to make it easy, ATI.

---

### Post by Heyday on 2007-07-27
No, it didn't tell me I already had the driver.

My TV out or VGA out also don't work with the current Mesa drivers, this is the main reason I want the Ati drivers to work.

---

### Post by xxdeusxx on 2007-07-29
I am experiencing the same problem...
but when i run 
sudo aticonfig --initial --overlay-type=Xv
it returns
Found fglrx primary device section
Nothing to do, terminating.


any ideas?

---

### Post by redhat24 on 2007-07-29
On Kubuntu Feisty i've installed successfully the latest ATI driver ( 8.39.4 for X700 ) following the Method 1: Install the Driver the Ubuntu Way.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

fglrxinfo says ATI not MESA, so it works great (but don't have ATI Control Center/Panel, so I'm looking for solution for this problem, if you have one pls post/email to me)

---

### Post by Skukfas on 2007-07-30
> **Heyday said:**
> I am trying to install the new ati driver version 8.39.4 on my HP laptop with ati xpress 200m video.  I have followed the instructions on the ati driver wiki site,  and I can't get the 3D acceleration to work.  When I do the fglrxinfo command it returns this:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

It should be the ATI and not the mesa.

Can anyone help me with this?

Also, when I try to run sudo aticonfig --initial --overlay-type=Xv, it returns this:

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

i had the same problem and fixed it by just going to System > Administration > Restricted Drivers Manager and enable "ATI accelerated graphics driver"

don't know if this was supposed to be already enabled but here it wasn't.

edit: with the x700

---

### Post by Heyday on 2007-07-30
> **Skukfas said:**
> i had the same problem and fixed it by just going to System > Administration > Restricted Drivers Manager and enable "ATI accelerated graphics driver"

don't know if this was supposed to be already enabled but here it wasn't.

edit: with the x700

mine is enabled, but it says not in use.

Anyone know what to do about this?

---

