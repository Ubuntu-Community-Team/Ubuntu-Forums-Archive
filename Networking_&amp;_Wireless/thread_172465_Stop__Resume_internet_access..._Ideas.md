---
title: "Stop / Resume internet access... Ideas?"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by Bukunut on 2006-05-08
Hi

After finally kicking the USB BT Voyager out the window, I finally got a new BT Voyager 220v ADSL VR. Set up the etho connection through KDE control module (Network Settings) and have access...sweet!
Now, I have searched the web/forum (bet ya I missed something!) but not found what I need. Is there a way to use a connection manager to stop or restart connection to the net? I used to use a programme set up through Fedora sometime ago, but can't find through Kubuntu what I need. Has anyone done this or have any ideas? :-k 
Thank you - Bukunut.

---

### Post by mzilhao on 2006-05-08
what about
```
sudo ifdown eth0
```
to stop, and then
```
sudo ifup eth0
```
to restart?

---

### Post by Bukunut on 2006-05-08
mzihao

Yeah thank you for that.... sounds daft, but I was looking for an app that would do that, easier to teach someone else who uses the computer (who does not like the console) to press this button to connect then when you finished press this than type, unless I put a postIT note on the side of the screen for them.. LOL
Bukunut

---

### Post by Bukunut on 2006-05-11
Anyone?

---

### Post by mips on 2006-05-11
Why would you wan't to disconnect a ADSL connection, just curious ?

I assume you are not using pppoe on the pc and it is straight ethernet ? Even if you disable the ethernet the adsl line still stays up.

Suppose you could have two scripts, create a on & off icon and them place them on the desktop somewhere and link them to the scripts.

---

