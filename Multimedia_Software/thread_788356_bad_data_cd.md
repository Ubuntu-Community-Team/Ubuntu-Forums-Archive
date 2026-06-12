---
title: "bad data cd"
date: 2008-05-09
forum: Multimedia Software
---

### Post by claver on 2008-05-09
Hey, thank all of you out there providing support for us in here. Im basically new in ubuntu, been using it for a couple of months but im not new to computers. so here is my problem:

i have a old cd, im trying to recover the data since it cant be read. Now i tried dvdisaster to recover it, and basically the only bad sectors i have are right at the begining at the table of contents, and at the very end. About 96% of the data in the "middle" is readable. So, Im not able to repair the cd, since i never created an ecc file for this medium, but i know i cant mount the volume since it wont read the table of contents. My question is: Is there any other way to recover the data not accescible????:confused:

thanks in advance, any help would be greatly appreciated.

---

### Post by claver on 2008-05-09
the thing about this is that is not because of the os (ubuntu studio), it wont be read on xp or vista as well, is just a bad table of contents in the cd.

---

### Post by cariboo on 2008-05-09
You could try dd

```
dd if=/dev/hdc of=old_cd.iso
```

Where /dev/hdc is your CD-Rom drive, then mount the resulting iso

```
sudo mount -o loop old_cd.iso /mnt
```

I've had had some luck doing this.

Good Luck

Jim

---

### Post by claver on 2008-05-12
yes it did
aprecitated so much thank you

---

