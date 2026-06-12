---
title: "Access repos from company network"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by Happy Days on 2009-04-21
Hi.

I am teaching at a school and trying to set up my ubuntu properly.  I cannot update or install anything from the repos as they fail to fetch.  I believe that the Proxy Server is running Fedora.  I am fairly computer literate and can access the Domain server (know the passwords etc) but could someone please help me to find out how to get the repos accesible.

Thanks in advance

---

### Post by chili555 on 2009-04-21
I suggest amending your */etc/resolv.conf* to use the OpenDNS servers, instead of the internal company servers the DHCP server undoubtedly handed you. Please check here: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by Happy Days on 2009-04-21
Thanks Chili, will try it when I go back to school on Thursday - we are voting for a new president tom.

---

### Post by Happy Days on 2009-04-24
No Luck with that I'm afraid:

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/libm/libmikmod/libmikmod2_3.1.11-a-6ubuntu3_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/libm/libmikmod/libmikmod2_3.1.11-a-6ubuntu3_i386.deb)
  Could not resolve 'za.archive.ubuntu.com'


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2_i386.deb)
  Could not resolve 'za.archive.ubuntu.com'


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.8-4_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.8-4_i386.deb)
  Could not resolve 'za.archive.ubuntu.com'


Any other ideas???

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/universe/a/abe/abe-data_1.1-3_all.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/a/abe/abe-data_1.1-3_all.deb)
  Could not resolve 'za.archive.ubuntu.com'


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/universe/a/abe/abe_1.1-3_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/a/abe/abe_1.1-3_i386.deb)
  Could not resolve 'za.archive.ubuntu.com'

---

### Post by jimv on 2009-04-24
If you know the proxy address/login info, you can set that in System>Preferences>Network Proxy.  Then open the terminal and try updating again.

---

### Post by Happy Days on 2009-04-24
THANKS!  that did it.  Now that I think about it, it was soooo obvious.  Now, onto another forum and another problem...

---

