---
title: "I need help ASAP"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Kiriyama28 on 2008-02-03
I have a GeForce FX 5500 (NVIDIA), but i can't install the driver. I have ubuntu 7.10 currently and i can't find anyone to help me. Please post ASAP.

---

### Post by eye208 on 2008-02-03
Make sure the "restricted" repository is enabled in System-->Administration-->Software Sources. Go to System-->Administration-->Restricted Drivers Manager. Mark the checkbox next to the Nvidia driver. Confirm and restart the computer.

---

### Post by Kiriyama28 on 2008-02-03
Even when I do this i can't install the driver for the G card....any other ideas?

---

### Post by eye208 on 2008-02-03
> **Kiriyama28 said:**
> Even when I do this i can't install the driver for the G card....any other ideas?
What does "can't" mean? Your computer turns off without warning? Maybe even explodes?

Please _describe_ the problem in more detail. "Can't install" could mean pretty much everything.

---

### Post by Kiriyama28 on 2008-02-03
I'm not sure, but i thought i had to download the driver from NVIDIA's website. If thats not the case then why can't i play simple flash games?

---

### Post by eye208 on 2008-02-03
> **Kiriyama28 said:**
> I'm not sure, but i thought i had to download the driver from NVIDIA's website.
No. A precompiled version of the Nvidia driver is included with the Ubuntu distribution. If that one doesn't work (e.g. because your card is brand new and not yet fully supported), then you can grab the latest driver from Nvidia's website. But in most cases this is not required.

> If thats not the case then why can't i play simple flash games?
Maybe it's because the Flash plugin is not yet installed? What happens when you try to run Flash games? Please describe!

---

### Post by Kiriyama28 on 2008-02-03
the start up screen flickers and i'm not able to go further into the game. I DLed the plugins needed also i just noticed i cant watch any vid on youtube...

EDIT: Youtube started to work but the videos are in terrible quality and the video skips like 1 fps.


Edit: Would it help if i get adobe flash player?

---

### Post by eye208 on 2008-02-03
> **Kiriyama28 said:**
> the start up screen flickers and i'm not able to go further into the game. I DLed the plugins needed also i just noticed i cant watch any vid on youtube...
Which plugins did you download? How did you install them?

There are currently two plugins to view Flash content: The original Flash Player from Adobe, and Gnash. Gnash is still in development and not yet fully compatible with the original Flash. Both plugins are included with Ubuntu, i.e. they are in the repository, but you have to choose which one to install. From your description of the problem I suppose you have installed Gnash. If that is the case, please uninstall it and install the original Flash instead.

You can check which version of Flash is currently installed if you go to [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/). There should be a box labeled "Version Information" saying: "You have version 9,0,115,0 installed"

---

### Post by Kiriyama28 on 2008-02-03
How would i install adobe flash player because i dont know the commands to do so...and ill uninstall gnash asap.


EDit: it says i have 8,0,99,0

---

### Post by eye208 on 2008-02-03
> **Kiriyama28 said:**
> How would i install adobe flash player because i dont know the commands to do so...and ill uninstall gnash asap.
Go to [http://www.adobe.com/](http://www.adobe.com/) and click the button labeled "Get Adobe Flash Player". This will bring you to the download page. Choose option 1 (download .tar.gz) and save the file to disk. Close Firefox, go to the downloaded file, right-click it and select "Extract here" from the menu. This will create a new folder next to the .tar.gz file. Inside that folder you will find a file "libflashplugin.so" and an installer script. Run the script. Then restart Firefox and go to the Flash version info page again. It should now tell you that Flash 9,0,115,0 is installed.

---

### Post by Kiriyama28 on 2008-02-03
The vid's are working so im assumming the flash game should work but im going to chck just in case.

EDIT: Man thx a lot. Does this mean I can now put real games on my comp and they'll run smoothly? Like World of Warcraft or something?

---

### Post by Kiriyama28 on 2008-02-03
Thx a lot man. Can i run regular games smoothly like World of Warcraft or CS?

---

