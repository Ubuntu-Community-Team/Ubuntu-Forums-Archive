---
title: "UDF Patch from Strapp"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by addisor on 2008-02-09
I've just tried installing a UDF 2.5 patch to my gutsy install so that I can play Blu-ray DVD's with DumpHD and now apperar to have made a mess of my /etc/fstab file.

I did this 
wget http://www.strapp.co.uk/files/udf-$( uname -r ).ko
sudo mv udf-$( uname -r ).ko /lib/modules/$( uname -r )/kernel/fs/udf/udf.ko and followed the rest of the text, 

dmesg grep | UDF reveals nothing, I fiddle with my /etc/fstab and now have this

/dev/hdc        /media/cdrom0   auto 0       0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto 0 0

Now really struggling to get basic dvd's to play. Any help would be great?

P.S anyone got DumpHD working?

---

### Post by addisor on 2008-02-11
sorry desperate bump

---

