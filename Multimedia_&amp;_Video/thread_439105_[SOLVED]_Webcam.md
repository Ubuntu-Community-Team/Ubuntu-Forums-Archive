---
title: "[SOLVED] Webcam"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by Dave Otter on 2007-05-10
I have a PC Line 300k webcam When I try to use camorama I just get message cannot connect to video device (/dev/video 0) Please check connection;seems to be connected.

    Any ideas would be appreciated.

                         Thanks

---

### Post by edemark on 2007-05-10
hi you may need to download and compile a driver. The main cuestion is wich. You need to find out the driver that supports your cam (it can happen that there is none). So get some more info about your cam 1st: is it paralel or usb? supposing that it is usb you may run lsusb from the command line to get more info about connected devices. Than search for your webcam in google with that information.

Other idea what results you get using ekiga or camstream?

good luck

---

### Post by arsolto on 2007-06-22
I am placing topical as this for the first positions of the page number 1 of this section so that the Community sees that the related problem the integration of *webcam* and the operational system is a very common case enters the users of the Ubuntu since the launching of its new version, the **Feist Fawn**. In the topic that I initiated here to treat the same on subject, I received the following reply below:

> **codeworrier said:**
> Try using EKIGA with updated driver V4L2 and not V4L (video for linux 2 driver).   Worked for me.

Have not yet figured out how to switch driver plug in with Camorama. Waiting for next Camorama updates.

Mine they always *webcam* was detected automatically by the operational system by means of softwares related to the management of it in the previous versions to the **Feist Fawn**. I do not understand because of the regression!

---

### Post by dabl on 2007-06-22
Viva Brasil!

:D

If your webcam does not work "out of the box" with Feisty, check your webcam against the chips supported here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

You might need to make a gspca driver for your specific webcam.  :)

---

