---
title: "Kino + Dazzle = ??"
date: 2007-12-07
forum: Multimedia Production
---

### Post by sPiN1 on 2007-12-07
I have Kino installed on my PC but I'm not sure how to work it, or if Dazzle is even compatible with anything besides studio 10. 

I'm just wondering this:

Is it possible for me to record using my Dazzle, on Linux.

If so:

Can I use Kino.

If not:

What can I use?

(i'm new to linux so bare with me here. :S)

Thanks for any help!!!!!!

---

### Post by Evil_Network on 2007-12-07
I am assuming you're discussing a USB Dazzle device correct? From what I can tell, Kino cannot address a USB capture device only a firewire device. I played with Kino today and after getting the 1394 library installe correctly I was able to capture video from a firewire camera. 

Concernign Kino itself, as a video editor, I cannot understand who would want to use it as it lacks a timeline. Seems to work well as a capture program though. 

--Evil

---

### Post by Unterseeboot_234 on 2007-12-08
The "Rosetta Stone" of video file formats appears to be DV(raw), which is a huge and spread out file. The Dazzle should be able to do the capture and probably have to use WIN to write to a DV file. After looking at the Pinnacle web site, their interface for the Dazzle is all about WIN.

In any event, anything you can write onto a memory stick or over a network as a DV file will make all the Linux tools available. If the current Dazzle hardware works like an external USB hard drive, then you should be able to transfer and later format with software such as ffmpeg, kdenlive and/or mencoder. The only video capture available is Firewire.

Kino is a subtractive process -- you clip away what you don't want. Kdenlive is a frontend for ffmpeg and has a timeliine and is maturing fairly well as a software.

---

### Post by sPiN1 on 2007-12-12
This is my capture card (Dazzle DVC 170)

[http://images.tigerdirect.com/skuimages/large/P121-8122-a1.JPG](http://images.tigerdirect.com/skuimages/large/P121-8122-a1.JPG)

From the programs you guys have listed it doesn't seem they detect it being plugged into my computer to my tv.

I really would like to capture on linux with this capture card any more help would really really be appreciated, thanks.

---

### Post by sPiN1 on 2007-12-12
I think it might be because I don't have the drivers installed (lost my discs) and I've looked EVERYWHERE and I can't find drivers for my Dazzle DVC 170 on linux and I don't even know if they exist. If anyone has any information on the drivers please post them!


Thanks!

---

### Post by alby7e7 on 2008-05-30
Maybe if you use a 1934sock adaptor... 
or maybe installing the bender.exe with WINE or others virtual machines... bender.exe has the libs for dazzle170,
you can get it by the url of pinnacle studio 10...
Somthing like this [IMG]http://www.1topstore.com/images/products_images/unfurl/usb-to-ieee-1394-converter-1108.jpg[/IMG]

---

