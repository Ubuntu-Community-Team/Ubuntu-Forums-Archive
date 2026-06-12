---
title: "advice on swapping hard drive"
date: 2009-03-24
forum: Mythbuntu
---

### Post by 4dognight on 2009-03-24
I plan on swapping out my hard drive on my slave BE/FE, and using a CF card. 

This will allow me to run my FE silent, and cooler.

I currently have 2 160 gb drives in the FE.
1 drive is partitioned as /
the other as /var/lib/mythtv/storage.
So  I have 2 'recording' directories defined.

I plan on having my Master BE be the sole place for recordings.

What's the best to switch to the CF card, and still preserve my recordings.

---

### Post by 4dognight on 2009-03-25
No one ever swapped their hard drive?

---

### Post by rhpot1991 on 2009-03-25
You can move recordings around where ever you please, just as long as they end up in a storage group.  So you want to move these recordings or hard drives to your MBE and put them in a storage group there.  As far as your 2nd BE, you will want to launch Mythbuntu Control Centre and change its roll to a FE only.

---

### Post by jMon54 on 2009-03-25
what i did was i cloned my old drive to new then swapped - only thing i had to do after that was resize the partitions due to larger size of new drive.

---

### Post by 4dognight on 2009-03-25
> **rhpot1991 said:**
> You can move recordings around where ever you please, just as long as they end up in a storage group.  So you want to move these recordings or hard drives to your MBE and put them in a storage group there.  As far as your 2nd BE, you will want to launch Mythbuntu Control Centre and change its roll to a FE only.

If I move them to a storage group on the MBE, they  will still be accessible from the menu? Is it not stored in the database the server it resides on? I will still have a firewire tuner attached to the slave BE/FE. I am guessing I will have to define the storage group as the one on the MBE, and keep it defined as a slave BE/FE?

---

### Post by 4dognight on 2009-03-25
> **jMon54 said:**
> what i did was i cloned my old drive to new then swapped - only thing i had to do after that was resize the partitions due to larger size of new drive.

I am doing sort of the opposite. I am wanting to move the recordings off to the MBE, and have only the OS and mythtv reside on the SLave BE/FE. I figure a 4 GB flash drive should be sufficient. I will have to resize my partition down from 160 GB to 4GB, after having removed all of the recordings. But I agree, I figure once its shrunk to 4GB, I will take a drive image and restore it to the flash drive. Or at least Im hoping it works. :) And still have access to my recordings, which will now reside on the MBE.

---

