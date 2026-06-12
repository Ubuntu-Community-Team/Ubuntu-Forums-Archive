---
title: "Bootable Ubuntu CD with pre-setup wireless?"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by BigBu on 2010-03-31
Is it possible to modify Ubuntu system files before burning my .ISO that will allow me to pre-setup my wireless network?
 
I am not planning on installing Ubuntu at this time to a drive partition, but instead booting directly from the CD.  I am hoping to setup my wireless SSID and key within the correct files so that when I boot to the CD it automatically connects to my wireless network.  Is this possible?  If so, which files do I modify, and what sections of those files (if they arent obvious)?
 
I searched this forum and others on the web, but can't find the answer to my question.  Thanks for any help!

---

### Post by chris0108 on 2010-03-31
Im no master at this but i dont think you can change an iso file because in effect its like a photo copy of the disc, but having said that i think if you did it on a usb stick you might be able to.
Maybe someone with more knowledge can help, plus i think it may make a difference as to what make your wireless card is

---

### Post by BigBu on 2010-03-31
Actually, you can use several tools available free or for trial to modify files within an .ISO, or extract all .ISO files, modify whats needed, then re-package the .ISO.  So that's not an issue.
 
And I do know that my wireless card works, as I have the .ISO burned to CD and to a USB thumb drive, and when booting to either, when I get to the Ubuntu desktop it shows wireless networks available, including mine, and I can manually enter my 28-character key and connect to the internet.
 
My hope is to modify the file(s) within the .ISO to store and keep my SSID and key so I don't have to try and memorize it or enter it every time I boot to the Ubuntu bootable media.
 
Any help appreciated!  :p

---

### Post by BigBu on 2010-03-31
This is what I know so far:  
 
In the ETC/NETWORK folder and in the INTERFACES file in Ubuntu is where the wireless networking information is stored.  I could use this file to setup my wireless.  
 
HOWEVER, this location is not accessible in the .ISO file, or in the extracted files on the USB drive - I can only find and access it when booted into Ubuntu itself, and even if I modify these files, they are loaded into memory only and therefore not static, so the changes I make are lost as soon as I exit Ubuntu.
 
Ideas?  Please?  Pretty please?

---

### Post by BigBu on 2010-04-09
No one?  Not even an inkling?  Is this just such a stupid question with an obvious answer that I'm missing somehow that my questions being ignored, or is it just so difficult no one knows?  Just curious.
 
But seriously, if you know the answer, feel free to post it, because I havent found it elsewhere.  And thanks!

---

### Post by chili555 on 2010-04-09
[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

By the way, if you want /etc/network/interfaces to operate correctly, you will probably need to remove Network Manager. On the other hand, you could connect with NM and set the network you connected to to connect automatically, supplying your WEP or WPA details, etc.

I have never remastered a CD with Remastersys, but I did a few remasters back a few years ago with Knoppix. It was a bit tedious, but it works.

---

### Post by BigBu on 2010-04-09
Chili555,
 
EXACTLY what I needed!  Thank you so much!  I knew the answer was out there somehwere, I just didn't know where to find it.
 
Thanks again!  I'm all over it!  :P
 
BigBu

---

### Post by chili555 on 2010-04-09
Just for the benefit of the searchers, I suggest you post your experiences after you *succeed*!

---

### Post by Megaptera on 2010-04-09
I use Remastersys. I install whatever live cd, set up wireless & mobile broadband; install apps that I want (eg gufw). Burn new .iso with Remasterys, format partition and then boot from and use my new live cd. It can all be done in an hour or so.
On Dell Inspiron 1545 laptop.

Richard

---

