---
title: "Low resolution no support for my chipset?"
date: 2008-08-18
forum: Multimedia Software
---

### Post by KindredCharles on 2008-08-18
I cannot get higher than 800x600

it's on board video ati rage XL

super micro p4sci

Intel Pentium 4

When I type
sudo dpkg-reconfigure xserver-xorg

I get the error

xserver-xorg postinst warning: overwriting possiby-customised configuration file; backup in /etc/X11/xorg.conf.20080818104105

lspci | grep VGA is

03:09.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

no driver selected under devices for video in xorg.conf I cannot get ati driver selected by model to work or generic to work

this is a fresh install of 8.04 ix86 desktop /w updates


Thanks for any help you can give me.

---

### Post by overdrank on 2008-08-18
> **KindredCharles said:**
> I cannot get higher than 800x600

it's on board video ati rage XL

super micro p4sci

Intel Pentium 4

When I type
sudo dpkg-reconfigure xserver-xorg

I get the error

xserver-xorg postinst warning: overwriting possiby-customised configuration file; backup in /etc/X11/xorg.conf.20080818104105

lspci | grep VGA is

03:09.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

no driver selected under devices for video in xorg.conf I cannot get ati driver selected by model to work or generic to work

this is a fresh install of 8.04 ix86 desktop /w updates


Thanks for any help you can give me.

Hi and you can try and use the command with the alt, F2 keys enter ```
gksu displayconfig-gtk
``` and adjust your resolution there.

---

### Post by tuxxy on 2008-08-18
How did you install the drivers for your card?

---

### Post by KindredCharles on 2008-08-18
Yes I tried this the ati drives by model and vesa doesn't seem to work, also I tried envyng it did not recognize my hardware or it's not supported. 


sudo gksu displayconfig-gtk
on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-RzT3Ml7159/xauthority
Got pid 7181
(0, 0)
checkpoint 1
<xf86misc.XF86Server object at 0x8484c4c>
False

on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-RqqxvE7159/xauthority
Got pid 7220
(0, 0)
checkpoint 1
<xf86misc.XF86Server object at 0x84961ec>
False

---

### Post by cdtech on 2008-08-18
Go to "System > Administrator > Synaptic Package Manager" select search and type in "envyng". Select "envyng-core and envyng-gtk". Also search for "linux-restricted-modules" and select to reinstall the one for your current kernel.

After these are installed type in a terminal:
```
sudo envyng-gtk
```
and select "ati" this will install the drivers for your video.

---

### Post by KindredCharles on 2008-08-18
> **cdtech said:**
> Go to "System > Administrator > Synaptic Package Manager" select search and type in "envyng". Select "envyng-core and envyng-gtk". Also search for "linux-restricted-modules" and select to reinstall the one for your current kernel.

After these are installed type in a terminal:
```
sudo envyng-gtk
```
and select "ati" this will install the drivers for your video.

[IMG]http://img65.imageshack.us/img65/3071/envyngtc6.png[/IMG]

---

### Post by KindredCharles on 2008-08-20
ATI's website says theres linux support for rage xl, but under there dirver downloads it does not show under linux, only windows, It also mentions how it's discontinued under windows. 

selecting my chip via gksu displayconfig-gtk gives me a driver that does not work.

Can anyone confirm that there is no driver for the Rage XL or otherwise?

---

### Post by arj446 on 2008-08-20
> **overdrank said:**
> Hi and you can try and use the command with the alt, F2 keys enter ```
gksu displayconfig-gtk
``` and adjust your resolution there.

Hi 


I tried this after many unsuccessful attempts to change my screen resolution and it actually worked fine. Great and thanks a lot.

The issue I'm having now, though, is that the log in screen is not displayed properly : I only see it partially, approx 3/4 of the usual full screen from the top left corner. This is not a big issue, as I still can select a user and enter the password but... How do you want me to convince my GF we should use Ubuntu is she has a good reason to criticize it as soon as the login screen ? :lolflag:

---

### Post by KindredCharles on 2008-08-20
> **arj446 said:**
> Hi 


I tried this after many unsuccessful attempts to change my screen resolution and it actually worked fine. Great and thanks a lot.

The issue I'm having now, though, is that the log in screen is not displayed properly : I only see it partially, approx 3/4 of the usual full screen from the top left corner. This is not a big issue, as I still can select a user and enter the password but... How do you want me to convince my GF we should use Ubuntu is she has a good reason to criticize it as soon as the login screen ? :lolflag:

you should create a thread about this and post your hardware and software settings

ubuntu ver
xorg.conf
lspci | grep VGA
Hardware specs

And then someone might be able to help you

---

### Post by KindredCharles on 2008-08-21
used sudo gksu displayconfig-gtk to change by monitor to LCD panel 1024x768

using vesa driver

running test with vesa driver doesn't seem to work but it boots fine with minor graphics glitches and runs desktop fine.

I'll get by with these settings enless anyone thinks I should try a different driver for my chip.

[http://ati.amd.com/products/server/ragexl/features.html](http://ati.amd.com/products/server/ragexl/features.html)

---

