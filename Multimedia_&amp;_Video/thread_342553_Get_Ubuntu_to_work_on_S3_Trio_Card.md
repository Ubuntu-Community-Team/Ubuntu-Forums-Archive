---
title: "Get Ubuntu to work on S3 Trio Card"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by chinocracy on 2007-01-20
My Inno3d MX400 card seems to have conked out (and I never got the Nvidia driver to work yet). I might get a new one to replace it. Meanwhile, I use an S3 Trio V2 4MB PCI card as backup. However I'm back to using the "virus" (Win XP), because I can't run Ubuntu. The screen goes blank after the Ubuntu startup progress bar. 
I just wonder, is the S3 Trio below the system requirements for Ubuntu Dapper? Or is there a way to make it work? Thanks.

---

### Post by Markkreuzz on 2007-02-15
Hello, i also have the same card and the same problem... (and well what do you know, same nationality...) 
Well the card certainly isn't  below the system requirements. it just doesn't work properly.  i had a little rant about this before...  Luckily for you i have found a way around the problem, but i doubt it is a true fix*... i havent (...did not try hard enough) found the actual fix yet.. and well you could try this one....

Step 1: boot into recovery(safe) mode during startup.
Step 2: login to your main password or root. 
Step 3: type dpkg-reconfigure xserver-xorg
Step 4: now make sure you select "vesa" not s3 on the options mmmkay... vesa is a standard video driver but does not have all the features of the actual driver...
Step 5: if you  happen to find any other solution post back here... okay...  ;)

*(cncia n pards pro mdyo bc ako noon at tnmad nko mghnap n hehe. at least gumagana 2... goodluck... mabuhay si Pooh quiao!!!!!!!!)*

---

### Post by chinocracy on 2007-04-21
Hi Mark,
Saw your reply late, but thanks. I've copied the solution so I could try it out in case of emergency. I got a newer Geforce MX400 card to replace it and it runs well. At least I know what to do in case it happens again. 

Babylos go! :P

---

### Post by chinocracy on 2007-04-21
Why is it that we seem to be the only country that insists on using the S3 Trio for the latest operating systems.... :-S

---

