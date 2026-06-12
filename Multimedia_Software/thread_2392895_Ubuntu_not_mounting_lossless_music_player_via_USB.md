---
title: "Ubuntu not mounting lossless music player via USB"
date: 2018-05-26
forum: Multimedia Software
---

### Post by jbh54enwiler on 2018-05-26
I recently purchased a FiiO X1 (G2) lossless music player, and plugged it into my laptop's USB port, and the desktop icon nor filesystem browser list item for it appeared.  I used lsusb in the terminal and got a result I presumed to be the device as this listing:
[B]Bus 002 Device 015: ID 0525:a4a7 Netchip Technology, Inc. Linux-USB Serial Gadget (CDC ACM mode)
[/B]For now I'm going to use a microSD card to move music to it but I'd like to know if there's any way I can still sync directly to it.  (Also, Rythymbox did not detect it either.)

---

### Post by kazakore on 2018-05-27
Even in their own manual they don't seem to want to let you know what USB mode the device uses! I assume there are no options to change this....

Seems it's being picked up as a USB Serial device. This may help with combing serial with mass storage if so. Never tested this stuff myself though.
[https://developer.ridgerun.com/wiki/index.php/How_to_use_USB_CDC_ACM_and_MS_composite_Linux_gadget_driver](https://developer.ridgerun.com/wiki/index.php/How_to_use_USB_CDC_ACM_and_MS_composite_Linux_gadget_driver)

Most music players use MTP mode and you need to install a package called gmtp to use them. Whether this correctly integrates with your file manager or not I've had varied results with. More lately on the whole positive and just working once installed....
sudo apt-get install gmpt

I've just read a fair few reports from Windows owners that even they have been removing the card and transferrin music externally as it is unbearably slow when done within the device, so it may not even be worth it anyway....

---

