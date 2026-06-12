---
title: "Karmic Koala 9.10"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by jrev on 2009-11-11
Hi all,
since I installed the 9.10 version on ext4, my documents folder cannot be copied to a USB Key.
Can you tell me why ? 
This USB key is formatted in ext3 and my system is ext4. 
Is that a possible reason for the trouble ?

the transfer script is :
> #!/bin/bash
SOURCE_DIRS=/home/jean/Documents/
TARGET_DIR=/media/disk/Documents/

# monter le repertoire disk
# mount /media/disk

sudo rsync -av --del --stats $SOURCE_DIRS "$TARGET_DIR"

# démonter /media/disk
 umount /media/disk

echo "Backup Terminé"

# arrêt PC 
# sudo halt

---

### Post by jrev on 2009-11-11
> **jrev said:**
> Hi all,
since I installed the 9.10 version on ext4, my documents folder cannot be copied to a USB Key.
Can you tell me why ? 
This USB key is formatted in ext3.

the transfer script is :

Thanks for your advice

---

