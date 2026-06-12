---
title: "daemon-tools like program for linux"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by at0mic on 2006-10-23
hi guys.

i really need something like daemon-tools for windows. I was wondering what you experienced people use? This application looks really good:

[http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)

---

### Post by Rzulf on 2006-10-23
*.iso files can be mounted with a mount command as a root.

---

### Post by taurus on 2006-10-23
```

sudo mkdir /media/iso
sudo mount -i iso9660 -o loop <filename>.iso /media/iso
(or <filename>.img>)

```

---

### Post by at0mic on 2006-10-23
cool! thanks. the power of linux is just amazing.

---

### Post by jawa83 on 2006-10-25
Can a .daa files be opened in a way like this? Actually this is the first time I ever run into this format and don't know many programs to open it even in Windows. As far as I know it means PowerISO Direct-Access-Archive.

---

### Post by taurus on 2006-10-25
> **jawa83 said:**
> Can a .daa files be opened in a way like this? Actually this is the first time I ever run into this format and don't know many programs to open it even in Windows. As far as I know it means PowerISO Direct-Access-Archive.
As far as I know, you are out of luck with .daa format in Linux!  You can install wine in Ubuntu and try to see if you can get PowerISO to work with it...  Otherwise, use PowerISO to convert it to .iso in Windows (](*,) ) and then mount it in Ubuntu!

---

### Post by richardward101 on 2006-11-12
poweriso now has a linux version from their site, works fine, though its fairly new afaik so there may be bugs. just google poweriso linux and its near the top!

---

### Post by Nikusan on 2006-11-13
[http://cdemu.org/](http://cdemu.org/) maybe?

---

### Post by frukt25 on 2007-10-15
But I need to mount a .nrg?

---

