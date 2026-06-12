---
title: "About ati radon x1550"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by bacosmin on 2007-12-06
Hello, i have a problem -> I have installed ubuntu 7.10 and when it loads , after the preloader has finished preloading it appears a text that says it cannot open X server because there is no driver 
I have ati radeon x1550
what should I do??

---

### Post by bacosmin on 2007-12-07
No one can help me???

---

### Post by coskierken on 2007-12-07
Did you enable the restricted driver?  If not, do so and let it update itself and then try again.  You only need to run Xserver (with XGL) for the compiz to work.  Hope this helps :lolflag:

---

### Post by Yellow Pasque on 2007-12-07
In the terminal:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial --overlay-type=Xv
```
Reboot.

---

### Post by Afkpuz on 2007-12-07
*EDIT*  Use the method above.  It's alot smarter and easier.  My instructions are just a long way of doing the above.  






When booting up, press the escape key so you get into the bootloader.  Select recovery mode.  That should take you to a command line.

Back up you xorg file:
```
sudo cp /etc/X11/xorg.conf xorg.conf.backup
```

Then, you need to modify your xorg file.

```
sudo vim /etc/X11/xorg.conf 
```


Scroll down till you see the section labeled "Section 'Device' "
Where is says "driver", change it to "vesa" (You have to press the "insert" key to type in this particular text editor)
 
Now, press esc once.  Type ":wq" and push enter
That stands for write and then quit.

Hopefully, that should let you at least boot into a low graphics mode.  Once in ubuntu, goto system>administration>Restricted Drivers manager and install your graphics driver.  

If the vesa driver doesn't work, you can restore your xorg.conf to it's origina(not working form) with this command
```
sudo mv /etc/X11/xorg.conf.backup xorg.conf 
```

---

### Post by bacosmin on 2007-12-09
Thanx a lot ,it worked

---

### Post by nikio on 2008-06-20
Hi all, absolute beginner here!

Has anybody tried this with ubuntu 8.4?
Are these drivers any better than the "mesa" ones?

I've had quite a hard time recovering from black screens with other drivers...

---

