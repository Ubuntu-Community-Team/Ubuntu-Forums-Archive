---
title: "REMOVEING AMD FGLRX WATERMARK with flgrx driver with buildpkg command"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by puccaso on 2008-01-02
this is what you need to do

download [http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run ]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run") (or whatever the latest version is)
then extract and copy...see steps below.

copy somewhere sensible like /tmp
cd /tmp
wget -c [http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run ]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run")
sh ati-driver-installer-8.42.3-x86.x86_64.run --extract ati
sudo mkdir /etc/ati
sudo cp ati/common/etc/ati/control /etc/ati/
sudo cp ati/common/etc/ati/signature /etc/ati/

---

### Post by K.Mandla on 2008-01-03
Moved to Multimedia and Video.

---

