---
title: "Samba system installation"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by dagobert39 on 2008-12-26
I am new to Ubuntu. I am using VMware Fusion on an Intel Imac and recently installed Ubuntu on my virtual machine. Before switching to VMware/Ubuntu I was using Parallels/SuSe also on my Imac. The latter system included all  features of the Samba system. I now noticed that only some features of Samba were available on the VMware/Ubuntu combination. Can I download a complete version of Samba into Ubuntu from somewhere and install it in a simple way?

I would be greatful for any advice.

---

### Post by joebeasley on 2008-12-26
You can install samba in ubuntu.  Use the package manager or run 'sudo apt-get install samba' from the command line.

---

### Post by superprash2003 on 2008-12-26
does the ubntu machine have internet access?? if so you could setup samba like this [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by dagobert39 on 2008-12-28
Dear Superprash2003,

your reply was most helpful. Even more helpful would be if you could send me a smb.config file which I could start using and later modifying as I gain experience. My situation is:

virtual Ubuntu machine sitting on iMac sharing the latter's network
an eMac connected to the iMac by cable network
a PC running Windows XP also connected to the iMac by cable network
a Mac notebook communicating via WLAN.

Sounds complex doesn't it? I am a retired ex-Shell petroleum engineer doing some computing.

Best regards from snow-covered Austria.

---

### Post by jonandrews on 2008-12-28
Since Ubuntu 8.04, you can configure a working samba installation without having to directly edit the samba config file.  Have a look a my Ubuntu - XP networking guides:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

