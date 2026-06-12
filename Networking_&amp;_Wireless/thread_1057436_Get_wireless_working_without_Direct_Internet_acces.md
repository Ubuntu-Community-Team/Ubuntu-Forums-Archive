---
title: "Get wireless working without Direct Internet access."
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by Bleumunkie on 2009-02-01
Here is the problem - 

I'm at a hotel for the next month - so I brought my desktop to setup in the room, At home it was networked with a cable, In the hotel they just have wireless.

Here is the situation, I have a Broadcom BCM4318 wireless card - Stupidly I never installed the restricted driver.

I have a laptop that I can download and do whatever I need to do. (also has Ubuntu 8.10 on it.)

How can I get / Install the packages I need to get wireless internet on my desktop?

---

### Post by Bleumunkie on 2009-02-01
solved it myself, 

downloaded b43-fwcutter.deb from packages.ubuntu.com

moved to desktop by way of USB thumbdrive

installed b43-fwcutter.deb onto desktop.

opened /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

downloaded the two files mentioned in the script on my laptop, moved to desktop with thumb drive

installed following steps outlined in the script.

restarted to let system re-initialize the services and such 

bingo - wireless internet!

---

