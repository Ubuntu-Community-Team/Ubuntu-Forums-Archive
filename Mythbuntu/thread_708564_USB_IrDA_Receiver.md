---
title: "USB IrDA Receiver?"
date: 2008-02-26
forum: Mythbuntu
---

### Post by JPurdy on 2008-02-26
I got a remote control from my KWorld ATSC 115 card, along with a remote sensor.  I was thinking I could use that remote and a generic USB IrDA adapter and then use LIRC to hook into the adapter and listen for the remote and then relay the button presses to Myth commands.

Is this doable?  I've tried installing LIRC, but I'm not sure what kind of driver would work w/ the USB IrDA adapter.  I tried **usbx **and **igorplugusb **and in both situations, when I tried **irw**, it told me it couldn't connect.

Thanks!

---

### Post by JPurdy on 2008-03-03
Hmm - I think I found [my answer]("http://www.lirc.org/faq.html"):

> Is my USB IrDA dongle supported by LIRC?

No, it's technically not possible to use USB IrDA dongles (as specified by the Infrared Data Association) with LIRC. This does not apply to USB receivers in general.

Oh well.... :(

---

### Post by newlinux on 2008-03-03
Yeah, IrDA Is a different standard than you need for receiving remote signals. You just want a regular old infrared receiver... So you could use it with a working IR receiver, just not IrDA

---

### Post by clw3388 on 2009-01-01
I got my "generic" usb irda and remote to work using lirc...
run
 sudo apt-get install lirc lirc-x 

once installed just run irw in terminal and push buttons on your remote to see if it is reading the keys... if it is install 

sudo apt-get install mythbuntu-lirc-generator this will create some links for your user and all should be well.. 

(I am running ubuntu 8.10 btw.. )

---

### Post by newlinux on 2009-01-01
> **clw3388 said:**
> I got my "generic" usb irda and remote to work using lirc...
run
 sudo apt-get install lirc lirc-x 

once installed just run irw in terminal and push buttons on your remote to see if it is reading the keys... if it is install 

sudo apt-get install mythbuntu-lirc-generator this will create some links for your user and all should be well.. 

(I am running ubuntu 8.10 btw.. )

What model? is it IR or IRDA?

---

