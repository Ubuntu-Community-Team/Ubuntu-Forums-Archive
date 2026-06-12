---
title: "PHP FTP on ubuntu"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by unavenged on 2010-03-04
Hi,

I'm just want to know how i could enable FTP for PHP on a ubuntu system... I found a few links but they mostly say that when you install it you have to run ```
./configure --enable-ftp
```
How can i enable it if PHP was installed when we set up the server the 1st time?

Thanks

---

### Post by unavenged on 2010-03-04
Ok so i found that Net_ftp ([http://packages.ubuntu.com/intrepid/php-net-ftp]("http://packages.ubuntu.com/intrepid/php-net-ftp")) should work and i did 

```
sudo apt-get install php-net-ftp
```

But how do i configure it?

---

