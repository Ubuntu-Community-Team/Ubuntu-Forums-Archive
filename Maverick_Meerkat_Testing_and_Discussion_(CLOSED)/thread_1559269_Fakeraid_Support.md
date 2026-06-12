---
title: "Fakeraid Support"
date: 2010-08-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ronparent on 2010-08-23
Just out of curiosity, what is happening with fakeraid support? I noted that with Maverick a new set of symbolic links has been created duplicating the /dev/mapper/ ones setup and used by dmraid.

Also the naming convention seems to differ from that used by both dmraid and mdadm? I've noted the confusion in the boot up as well.

---

### Post by ronparent on 2010-08-24
bump

---

### Post by ronparent on 2010-08-26
I've additionally noted that the symbolic link to the raid is dm-1. dm-0 thru dm-10 represent the partitions (not including -1 and -2). Dm-2 is not created but would correspond to the extended partition. All of the dm-(n) links created can be substituted for their corresponding /dev/mapper/ links for execution of any operation on the raid or its partitions. It does simplify their designation for any operation requiring naming of the device. Wherever this is going I'm all for it!

---

### Post by ronparent on 2010-09-04
During the duration of the above comments, installing kpartx, which was needed in 10.04 for gparted to see raid partitions, caused gparted as well as the system in general to freeze up. This appears to be now fixed. Also gparted now uses the new symbolic links apparently created by the 10.10 kernel to display the raid partitions! The naming convention for these link differs between my beta install and the updated alpha 2 install? All in all, everything is more functional now.

---

### Post by ronparent on 2010-09-18
Disregard what I previously noted as a difference between the updated alpha2 and the beta. Gparted has regressed to using the /dev/mapper id's for all the raids. More ominously, grub probe fails in addressing the raids and subsequently grub-update now fails. Short of manually altering the grub menu either on boot or in grub.cfg, new kernels are now not bootable!

Also the beta updates to linux-image-2.5.36-22-generic, the alpha 2 updated only to 21.

---

### Post by ranch hand on 2010-09-18
Editing grub.cfg is kind of silly.

Put a menu entry in the /etc/grub.d/40_custom file and run update-grub.

---

### Post by ronparent on 2010-09-18
I agree. Just trying to make a point.

---

