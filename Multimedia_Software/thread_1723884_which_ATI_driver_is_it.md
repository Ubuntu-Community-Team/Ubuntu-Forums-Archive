---
title: "which ATI driver is it?"
date: 2011-04-07
forum: Multimedia Software
---

### Post by srlake314 on 2011-04-07
ok so the steps that the pdf file from ati says :

[B]To install the ATI Proprietary Linux driver using the Automatic option, follow
these steps:
1 Launch the Terminal Application/Window and navigate to the ATI Propri-
etary Linux driver download.
2 Enter the command sh ./ati-driver-installer-8.573-x86.x86_64 to launch the
ATI Proprietary Linux driver installer.[/B]

The ATI Proprietary Linux Driver Setup dialog box is displayed
It shows the ati with the penguin.  Mine doesnt show that for the file:
"ati-driver-installer-11-3-x86.x86_64.run

This is the driver that I got from the website.  But Im still having  issues with Wow not working or recognizing that I have a great card (XFX  HD 4770).

Please, I am sick of scrolling through hundreds of pages trying to get functions to work.

Sean

---

### Post by Revolutionary101 on 2011-04-08
Are you having difficulties installing the driver?

or

You successfully installed it, but Wow isn't recognizing the card.

---

### Post by srlake314 on 2011-04-12
Hey Rev, 
sorry for the delay in the answer.  I am having issues with installing the driver, as well as WoW not working correctly.  As you can read in my post, the driver, I think is the current one from the vid card site, doesnt show a penguin, so Im not sure if it is the correct one even though it says something to that extent when I download it.
Next, when it is activated, not to repeat myself, Ubuntu Studio doesnt load in the beginning on boot, however if I disable the proprietary driver, Ubuntu Studio loads(not the standard vanilla ubuntu).

wow sort of works with the prop driver, other than Most of the character isnt even drawn, the background is, but not the toons.  Im not sure what to do?

---

### Post by Yellow Pasque on 2011-04-12
Purge your current driver install:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

Then follow this: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by srlake314 on 2011-04-13
sean@NZXT59PC:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
sh: Can't open /usr/share/ati/fglrx-uninstall.sh
sean@NZXT59PC:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx


thats what happened when I tried that line of code.

---

### Post by Yellow Pasque on 2011-04-13
Ok. Now install the driver like this: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by srlake314 on 2011-04-13
Ok,

so i followed those instructions down to the line:
Create .deb packages.
$ sh ati-driver-installer-11-3-x86.x86_64.run --buildpkg Ubuntu/maverick

and guess what, my screens went black, except for a tiny white "[" that didnt blink, or I couldnt type.  The whole computer didnt do anything.  Now when i restart, the ubuntu studio splash screen comes up with the letters that fill with the white, but then the screen goes black.  Nothing at all....

I guess I will have to start ALL over again now.

---

### Post by srlake314 on 2011-04-13
Yup, it's definitely dead now.  It boots to the Ubuntu studio splash screen all pretty, but then the monitors dont detect a signal and it dies.  I both enabled and disabled the vid card in bios, and still no change.

Windows 7 here I come, I really dont have the patience after 3 weeks of trying to figure this out.

Thank you for your help though.

Sean

---

### Post by srlake314 on 2011-04-13
Im taking my Ubuntu Studio dvd and rebooting with it, and reformating and such..we will see.

---

