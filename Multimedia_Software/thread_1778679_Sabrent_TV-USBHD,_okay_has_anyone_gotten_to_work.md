---
title: "Sabrent TV-USBHD, okay has anyone gotten to work?"
date: 2011-06-09
forum: Multimedia Software
---

### Post by bgmomof2 on 2011-06-09
I made an impulse buy on a USB TV tuner that doesn't have Linux support. I can use on my Windows PC but was hoping I could get it to work on my Linux Laptop for travel. I've been searching for a driver, and found lots of references to LinuxTV.org & v4l-dvb (WOW, that was educational), so honestly it's all way to technical for me.  I was hoping to find a linux driver for this device.  Anyone...

---

### Post by jerrrys on 2011-06-09
there is a very little bit here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Sabrent+TV-USBHD&sa=Search&cof=FORID:9#506](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Sabrent+TV-USBHD&sa=Search&cof=FORID:9#506)

and a little more here

[http://www.google.com/search?client=ubuntu&channel=fs&q=Sabrent+TV-USBHD+linux&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Sabrent+TV-USBHD+linux&ie=utf-8&oe=utf-8)

---

### Post by bgmomof2 on 2011-06-09
After searching and learning, this looks like a fix.  But, I don't know what to do. I have the file listed (ua0828-card.c)  I added the line listed.  Saved it. Now what?  How do I use the file? 


Talk:Sabrent TV-USBHD
From LinuxTVWiki
Jump to: navigation, search

I'd like to mention here after much struggle with this I was able to get it to work by adding two simple lines to a file (in Ubuntu 10.10).

Get the current release as described on this site (the easy way) run the following commands: make -C linux/ download make -C linux/ untar

the edit ~/media_build/linux/drivers/media/video/au0828/au0828-cards.c

At the very end of the file you will see { USB_DEVICE(0x2040, 0x8200), .driver_info = AU0828_BOARD_HAUPPAUGE_WOODBURY },

Add this to the line immediately following:

       { USB_DEVICE(0x05e1, 0x0400),
               .driver_info = AU0828_BOARD_HAUPPAUGE_WOODBURY },

{ },

then type make.

Note, this only works on the Sabrent card with the tda18271 chipset but it works now flawlessly after messing around for 2 years.

---

### Post by bgmomof2 on 2011-06-09
Thanks for the links.  I have been across those in my search, and they have gotten me this far.  I'm at a point of trying to understand what to do with a file I edited that I believe will be the driver.  I need to 'make' the file? then 'make install' I'm really not sure the exact commands to enter.

---

