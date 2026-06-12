---
title: "Problem installing latest ATi driver"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by james016 on 2006-11-04
I have downloaded the latest driver from ATi's website. However when I run it I get the following message:

./ati-installer.sh: 991: Syntax error: Bad substitution

Has anyone else had this? If you did, how did you fix it?

Thanks

J

---

### Post by Wise Ferret on 2006-11-04
I encountered the same message after downloading it twice.

---

### Post by jocko on 2006-11-04
[SIZE=3]According to this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"), you'll have to do it like this:
[/SIZE] [SIZE=3]```
sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.30.3.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
```

(Check out the guide before you start, to avoid problems)
[/SIZE]

---

### Post by james016 on 2006-11-04
I followed the guide to the letter but it didn't work. Still loading the MESA driver.

lsmod shows fglrx loading up.

dmesg | grep fglrx
[17179585.348000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179585.348000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179585.348000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179611.392000] [fglrx:firegl_unlock] *ERROR* Process 4077 using kernel context 0

Even added fglrx to etc/modules and it still wont load. 

Any more ideas? :-|

---

