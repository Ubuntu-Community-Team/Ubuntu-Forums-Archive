---
title: "No GUI"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Jormanks on 2007-03-21
Hi.

I was trying to make the driver for a MSI K8mm-V, vt8237, from... somewhere, i can't find the link (i have it in a tab in ubuntu's firefox) and in all the steps i had to erase the xserver to prevent some issues... and yes, i erased it and now i have issues. Since I have no GUI now just want to know how to install the previous drivers from the terminal.... and for me it's extremely painful.

How can i reset this drivers?

Thanks

---

### Post by dreadlord_chris on 2007-03-22
```
sudo dpkg-reconfigure xserver-xorg
```

and choose **vesa** for the driver should get you back to the default.

---

### Post by Jormanks on 2007-03-22
This doesn't work. It says something about the xserver being broken...
Maybe i have to load it from the live cd?

Any guess?

---

### Post by Jormanks on 2007-03-24
how i restore xserver?

I mean the defaults as typing sudo dpkg-reconfigure xserver-xorg displays something telling about the xserver being broken.... please...

---

### Post by r4ik on 2007-03-24
From  [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

You have a graphical environment, but it won't show the way I want it to
Well, what if you get a graphical environment you can't see? It's a black screen but your monitor's working, or you get that the monitor signal is out of range, or the screen resolution is just too low for your tastes.

Well, then press Control-Alt-F1 and try this:

sudo dpkg-reconfigure xserver-xorg

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Control-Alt-F7 to get back to graphical mode and then Control-Alt-Backspace to reset the X server (so your changes can take effect).

Next steps
In a lot of cases, these steps will get you all straightened out. If not (for example, if you are still unable to reach your optimum screen resolution), look here for other possible solutions.

Other variations
If you're using Kubuntu, it's the same deal--just replace ubuntu-desktop with kubuntu-desktop and replace
sudo /etc/init.d/gdm start
with
sudo /etc/init.d/kdm start

If you're using Xubuntu, it's the same deal--just replace ubuntu-desktop with xubuntu-desktop.
sudo /etc/init.d/gdm start
will stay as is.

Good luck !

---

### Post by Jormanks on 2007-03-24
As I early wrote.... a display message appears and sayd that the Xserver is damaged or broken...

---

### Post by r4ik on 2007-03-25
Please read the first section.

---

