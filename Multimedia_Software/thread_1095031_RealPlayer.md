---
title: "RealPlayer?"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Peter Fjelstrup on 2009-03-13
I downloaded RealPlayer and it stored itself in 
Home/Peter/Desktop and then terminal couldn't find it.
There were no options as where to store it on the 
download site?
I was not allowed to copy it to Home.

My 3rd level (Alt Gr) button doesn't work here,
but it works in OpenOffice?

Regards Peter

---

### Post by squaregoldfish on 2009-03-13
The file you download from the RealPlayer site is an installer which must be run. As a security measure, this file won't have been given execute permissions when it was downloaded. To install the RealPlayer, do the following:

1. Go to /Home/Peter/Desktop in a terminal.
2. Give the file execute permission:
```
chmod +x RealPlayer11GOLD.bin
```
3. Run the installer as root:
```
sudo ./RealPlayer11GOLD.bin
```
4. Follow the instructions.

Hope this helps,
Steve.

---

### Post by martin roland smith on 2009-03-13
drag and drop the realplayer.bin file into the terminal. you may also need to check the permissions for this file (right click and select properties)

---

### Post by UbuntuNerd on 2009-03-13
follow this quick [GUIDE](http://my.opera.com/ubuntunerd1/blog/realplayer-in-linux)

---

### Post by Peter Fjelstrup on 2009-03-16
Totem plays DVDs with a lot of flickering and interruptions.
I managed to install RealPlayer, but it doesn't play DVDs.
Is there a better DVD player?
Or is the problem in my videocard. I think it said something about this card not being fully supported?

---

### Post by UbuntuNerd on 2009-06-03
no offense my "Totem" plays just about anything even HD from Yahoo and Apple, you can follow this quick [guide](http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem) :)

---

