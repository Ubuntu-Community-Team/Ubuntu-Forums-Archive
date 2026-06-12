---
title: "Canon EOS 30D"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by wisdoms on 2006-06-06
hi guys, 

since I want to get rid of windows at all, I need to use my camera with my Kubuntu 6.06 as well. So that the question is this: how can I connect and see the pictures of my camera (Cnon EOS 30D) and download them on my pc?
At the moment I can plug it, but I can't reach/see the files inside!!! :(
Do you know any good HowTo?

Thanx!

---

### Post by Vati-Khan on 2006-06-06
I don't have an d30 but gThumb lists it as a supported model

have you ever tried the gthumb-import-tool?

---

### Post by bluenova on 2006-06-06
I have the 350D which is probably simlar, you need to set 'communication' in the camera menu to 'Print/PTP' then programs like gthumb will pick it up, but you won't be able to browse it like a directory. I would suggest buying a cheap card reader, and then you can just browse the files, which is what I do. Transfers are also quicker from the card reader than from the camera.

---

### Post by wisdoms on 2006-06-06
I've not tried it yet, but also the "Control Center" tools seem to support it, but I cannot download the pics :(
Anywas I'll test your advice soon, 

cheers

---

### Post by Zhukov on 2006-06-06
30D or 300D?

---

### Post by wisdoms on 2006-06-09
30d

---

### Post by barc on 2006-08-20
The d30 is an old digital camera from canon while the 30d is their newest semi professional model (released 2006).

Dapper includes libgphoto2-2.1.6 and libgphoto2-port0-2.1.6.
The 30d support was added in libgphoto2-2.2.0 afaik and is therefore not included in Dapper. 

I (a linux n00b) own the same camera and tried to upgrade libgphoto manually but failed terribly. I have a cardreader so I can avoid the problem, but when I visit my parents (who use ubuntu) and don't wan't to carry my cardreader, I run into the same problem. 

Windows XP SP2 did not work out-of-the-box either. ;)

---

### Post by feap on 2006-10-12
This is still unresolved? I have the same problem with my 30D: can't access the camera as a file system and gtkam or gthumb can't download the files. The latest version of libgphoto has drivers for Canon 30D but I can't find it on Synaptic and I don't know how to install it via terminal (tried with the instructions).

And yes, XP SP2 works fine after you install the files that came with the camera. I don't want to buy a card reader just for this as it should work in Ubuntu, as well.

---

### Post by jetronic on 2006-12-09
I got it to work:

I just bought a EOS 30D and having the same trouble getting gThumb to recognize the camera.  When the USB cable is connected and you power the camera on, an "Import photos" dialogue window automatically launches but it says under the camera icon "No camera detected" and displays some error. 

Out of frustration, I kept clicking the camera icon over and over and it finally connected!  Another import window appeared showing thumbnails of all of the photos on the camera.  I clicked import and bingo, it imported the photos to the specified folder.  I've tried it several more times and it seems to need exactly 6 clicks on the camera icon befoer anything happens.

I don't know if this will work for any of you since this isn't exactly a scientific fix but rather the equivalent of a slight love tap on the side of an appliance which isn't working correctly.  Its worth a try. 

HTH

---

