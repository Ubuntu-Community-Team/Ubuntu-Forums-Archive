---
title: "What is the latest on ATI Radeon X1250?"
date: 2010-07-13
forum: Multimedia Software
---

### Post by Struwelpeter on 2010-07-13
Hi there,

Newbie here. I've been looking for information on how to install a proper ATI Radeon X1250 driver on my Ubuntu Lucid Linux. All I can find is pretty old info that deals with previous versions of Ubuntu. I'd be very thankful if someone could direct me to a piece of up-to-date information about how to check what ATI driver Ubuntu has automatically installed, and how to choose a better one if possible.

Thanks!

S.p.

---

### Post by Yellow Pasque on 2010-07-13
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#The_Options](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#The_Options)

Your card is considered "legacy" by ATI, so Catalyst/fglrx no longer supports it. The default "radeon" driver is probably the best, though you can try the xorg-edgers PPA if you can live with possible breakage.

---

### Post by Struwelpeter on 2010-07-13
Ah, I see. Apparently installing such optional driver is what I had done, though I have no idea *how*!

Thanks for the reply!

---

### Post by Struwelpeter on 2010-07-16
I have new question. I have decided to give the X.org thing a try. The guide Temüjin has kindly pointed me to says:

<<Installing Open Source Edge Drivers

These packages are built regularly from the X.Org git repository, so they may not be fully stable. On Lucid, using this graphics stack now uses the r300g Gallium3D driver for 3D acceleration on Radeon R300-R500 (Radeon 9500 - Radeon X1950) class chips. It's probably a good idea to use the linux kernel provided by this repo if you go this route.
To install:
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
Now you can update your packages using Synaptic or Update Manager.>>

My questio nis... What exactly should I look for in the Synaptic? There are a lot of ATI things listed there, now, and none of them refers explicitly to my card.

---

### Post by Yellow Pasque on 2010-07-16
You don't need to do anything special (just upgrade your packages and restart). You can even do it from the command-line (close Synaptic first):
```
sudo apt-get dist-upgrade
```

---

### Post by Struwelpeter on 2010-07-16
Right. Thanks a lot!

Being a total newbie, I should also ask... if it doesn't work, how do I go back to the default drivers? Remove every X.org-related package from the Synaptic thingy?

EDIT: Alas, it indeed didn't work. 3D is obviously much faster, but I get a lot of buggy little squares across my screen... Incidently, when I was rebooting I could see an error report being displayed, which was too quick for my eyes; and next Ubuntu goes on to make a test in my HD...

---

### Post by Yellow Pasque on 2010-07-16
To revert to the regular packages:
```

sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers
```
You can then go into System -> Administration -> Software Sources and disable/remove the xorg-edgers PPA (under the 3rd-party software tab).

---

### Post by Struwelpeter on 2010-07-17
Worked. Thanks!

---

