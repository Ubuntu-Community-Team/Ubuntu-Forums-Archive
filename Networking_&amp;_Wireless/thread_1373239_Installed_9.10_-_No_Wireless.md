---
title: "Installed 9.10 - No Wireless"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by donsabi on 2010-01-05
I install 9.10 dual boot on a vista pc.  I am also new to Ubuntu.
Ubuntu appears to be running however it is not seeing wireless networks.  I have the pc icon with an x.  I tried help and was directed to Terminal where I thought I followed the instructions and ended up with information about my adapter displayed.  
When I run Vista I have all wireless networks listed and can connect.  Ubuntu does not show any wireless networks available.
I tired going back over the install but do not see that I missed anything.  I get the sense that this may be something simple.
Any help is appreciated, thanks.
don

---

### Post by mocoloco on 2010-01-05
Need more info before anyone can help.  What kind of wireless card?  What are the other instructions you followed at the terminal?  What kind of output/errors did that give you?

---

### Post by Kevbert on 2010-01-05
Please go to Applications-Accessories-Terminal and enter the following commands
```
lspci
lsusb
```
Post back the output by highlighting the text with the mouse and selecting Ctrl+Shift+C (to copy) and paste here with Ctrl+V.
You will need to install a firmware driver for the wireless adapter.

---

