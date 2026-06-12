---
title: "Evite ETV-7131 TV &amp; Capture Card on 10.04"
date: 2011-06-09
forum: Multimedia Software
---

### Post by ario on 2011-06-09
Hi,
I recently bought an Evite ETV-7131 TV & Video Capture card based on Philips 7130 Chipset. The card wasn't working on Windows 7 with it's provided Windows Vista driver. I mean the quality was too bad (I needed to fine tune a lot of brightness and contrast controls in the provided software with the driver to see the picture) and it used to crash and thus restart the whole system every 5 to 10 minutes!
On Linux (Ubuntu 10.04) it detected but the dmesg output, the saa7134 module told me that it can't detect the card number automatically and suggested me to select a card number from a list it contained in its output.
I ran:
```
sudo su
rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=17
modprobe saa7134_alsa card=17
```
It's a little hard to me to describe you how I selected the number 17 but anyway,for making those two last commands permanently, run:
```
nano /etc/modprobe.d/alsa-base.conf
```
Find the line "options saa7134-alsa index=-2" and if you sure that it isn't exist, add one, then change it to:
```
options saa7134-alsa card=17 index=-2
```
Also add the line below before previous line:
```
options saa7134 card=17
```
Close file using Ctrl+O then Enter, then Ctrl+X and install tvtime using:
```
aptget install tvtime
```
I then restarted my system completely. Ran tvtime, right-clicked on the black screen of tvtime and from Input Cofiguration menu selected "Change Video Source" to Television to see the Video Input! (I don't know why but Television works as Video Input and Video works as the Television!).
Powered on my satellite receiver (You say any kind of video player device) and it was all there! :)
Hope this helps.

---

