---
title: "Wireless Printing with an HP Photosmart c4500 series"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by jmwilli25 on 2010-09-02
I finally got around to setting up my HP Photosmart c4580 AIO printer today to print wirelessly so that I don't have to be tethered to it with a USB. I found there are many different ways of doing this, each with limited success. So I took a crack at it and this is how I got it to work. (Just an FYI, I don't think that it matters but I am running Ubuntu 10.04 64bit.)

In a terminal type
```
hpsetup
```
[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot.png[/IMG]

After pushing enter a GUI will pop open call "HP Device Manager - Setup". There are four radio buttons, I selected the "Wireless/802.11 (requires a temporary USB connection and is only available for select devices)" one and then clicked Next.

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot1.png[/IMG]
Clicking Next opens a new window for Wifi Configuration. Read what it says (Which is; after configuration setup will continue, this configuration may not work, and connect your printer to your computer by a USB cable!) Now click "Next".

Assuming you haven't forgotten to plug your printer into your computer (and turn it on) you will get a "Discovered Wireless Capable Devices" list with something on it. If you do not have anything listed under "Model" and "Device URI" check all your connections and the power to your printer and click refresh. If still nothing I am sorry but this setup has failed you, but if you are lucky and something shows up, click on it and then click next.

You have to have wireless internet to continue. The step you are on now has you select your wireless internet connection.

---

### Post by jmwilli25 on 2010-09-02
Sorry I accidentally posted this before I was done with it. Here is the final product.

[http://ubuntuforums.org/showthread.php?t=1566238](http://ubuntuforums.org/showthread.php?t=1566238)

---

