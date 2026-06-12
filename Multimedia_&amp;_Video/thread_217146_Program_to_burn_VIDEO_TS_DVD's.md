---
title: "Program to burn VIDEO_TS DVD's"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by Pootas on 2006-07-16
Hi,

I have got a DVD which I need to burn... Normally this wouldn't be a problem as I would just use Gnomebaker to burn the .ISO image...


However on this occasion the DVD files are in the format of VIDEO_TS and AUDIO_TS folders rather than an .ISO. I can't find any program that will burn a DVD in this format and I have tried burning these folders as a Data DVD within Gnomebaker but this doesn't work...

Any ideas what I need to do to burn the DVD correctly so it will play in a DVD player... 

Thanks in advance...

---

### Post by Dubbayoo on 2006-07-16
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

The page is only Opera-friendly.

---

### Post by chollis888 on 2006-07-23
Hey don't know if you found your answer yet but here you go.

"mkisofs" is the key and here's the code:

```
mkisofs -dvd-video -o ~/moviename.iso /path/todvd/filesystem/
``` 
that code will make you a moviename.iso in your home folder which can then easily be burnt or mounted.Goodluck!:KS

---

### Post by bvanaerde on 2008-05-06
> **chollis888 said:**
> Hey don't know if you found your answer yet but here you go.

"mkisofs" is the key and here's the code:

```
mkisofs -dvd-video -o ~/moviename.iso /path/todvd/filesystem/
``` 
that code will make you a moviename.iso in your home folder which can then easily be burnt or mounted.Goodluck!:KS
Thanks for the info!
I'm using Brasero (in Hardy), and didn't find an option to write a Video-DVD. I don't want to write it as a data DVD, as this might not always work.

---

### Post by alejandro.mc on 2008-05-22
I could really use a program to burn this VIDEO_TS folders. I downloaded things in this format and don't know how to burn them..

Can anyone help me?

---

### Post by bvanaerde on 2008-05-23
Read chollis888's post ;)

---

### Post by Mze on 2008-05-23
Or just grab [IsoMaster]("http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/") if you don't want to use command line

Deb files available for AMD64 and i386 (ubuntu 7.10) or install from tar.bz2

---

