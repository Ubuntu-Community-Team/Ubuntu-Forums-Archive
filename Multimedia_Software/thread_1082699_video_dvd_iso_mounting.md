---
title: "video dvd iso mounting"
date: 2009-02-28
forum: Multimedia Software
---

### Post by damasio2009 on 2009-02-28
i just migrated from windows to linux..ubuntu that is :)

usually with windows..i had either alcohol or daemon tools to mount the iso's, either normal data..mp3..divx..xvid..you know..and also the dvd video iso's too..

but with linux i still can't quite find the way to mount the video iso's into a virtual drive, thus being able to watch them as a real dvd with MPlayer movie player for example..any help will be aprettiated :)

thanks!

---

### Post by binbash on 2009-02-28
sudo mkdir /mnt/iso
sudo mount -o loop ISOFILENAME.iso /mnt/iso

---

