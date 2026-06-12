---
title: "how to open/make a virtual drive on ubuntu 10.04"
date: 2010-12-05
forum: Multimedia Software
---

### Post by scott_tiger on 2010-12-05
i am not able to make virtual drive???how can i run .iso files in ubuntu 10.04??plz reply
also some files which are downloaded in html format in windows ie 8 is not able to run in chromium browser or firefox in ubuntu 10.04 ???any remedy for this?? plz reply

---

### Post by SeijiSensei on 2010-12-05
> **scott_tiger said:**
> i am not able to make virtual drive???how can i run .iso files in ubuntu 10.04??plz reply

You can mount an ISO image as follows:

```

sudo mkdir /media/myiso
sudo mount -o loop -t iso9660 /path/to/file.iso /media/myiso

```

You'll now be able to browse the contents of the image from the terminal or the GUI by looking in /media/myiso.

---

### Post by scott_tiger on 2010-12-09
thanx it worked........

---

