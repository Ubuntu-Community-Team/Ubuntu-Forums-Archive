---
title: "CD, DVD Permissions"
date: 2009-04-04
forum: Multimedia Software
---

### Post by dokdoom on 2009-04-04
Ok, when I installed a game onto my system there was some mounting issues it had. It involved changing some settings which I just copied and pasted not really knowing what they did. I saved all of this so when I wanted to change them back it wouldn't be a problem. I deleted said file and now when I insert a CD it doesn't show up in /media/cdrom and nothing shows up on my desktop. Here is my /etc/fstab. I tried to chmod my /media/cdrom and /media/cdrom0 but it still doesn't show up. 

My question is what permissions do I need to change to get this working again?

Thanks

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=59c82e23-e110-42f9-a84a-a1f23effe555 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/vg-home
UUID=6a0fdcbd-11a7-43a9-be4f-d7521dc799e3 /home           xfs     relatime        0       2
# /dev/mapper/vg-tmp
UUID=0dd6ff4e-303a-4777-b238-ee7db3cf44f3 /tmp            xfs     relatime        0       2
# /dev/mapper/vg-usr
UUID=953a2b55-724e-4c83-9b90-f69d169bc6c8 /usr            xfs     relatime        0       2
# /dev/mapper/vg-var
UUID=942df03d-327c-48f6-b160-8a621bd221eb /var            xfs     relatime        0       2
# /dev/mapper/vg-swap
UUID=70fdc6af-b4c4-46f8-b46a-c0f08c44e081 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

