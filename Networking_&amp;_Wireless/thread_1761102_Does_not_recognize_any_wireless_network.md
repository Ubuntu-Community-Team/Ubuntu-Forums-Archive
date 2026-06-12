---
title: "Does not recognize any wireless network"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by kosmicman on 2011-05-17
Just installed ubuntu 11.04 by downloading the .exe application that installs it using windows. Now I cannot connect to the internet as ubuntu is not recognizing my wireless device, or any for that matter. When I click on network item at the top right the Wireless Networks section is blanked out. It reads in indented letters "Wireless Networks device not ready firmware missing". I have no idea what to do :confused:. Please help :(. Thank you :D.

P.S. I am LOVING ubuntu even without the internet for now. It is way faster than winxp which was almost making me abandon this netbook.

---

### Post by chili555 on 2011-05-17
> "Wireless Networks device not ready firmware missing". I have no idea what to doWhat we need to do is find out what kind of (Broadcom?) wireless device you have and download and install the firmware. Please open a terminal and run and post:```
lspci -nn
```Feel free to skip everything but the wireless line.

Are you able to use ethernet to grab the firmware if needed?

---

### Post by kosmicman on 2011-05-17
yes, I could connect with the cable to download it. How do I open a terminal though? Sorry, I just really know nothing about ubuntu.

---

### Post by chili555 on 2011-05-17
In Unity, with all the icons on the left side, click Applications; at the text box at the top, type 'term' and then click the icon for Terminal.

In classic Ubuntu, it's Applications > Accessories > Terminal.

---

