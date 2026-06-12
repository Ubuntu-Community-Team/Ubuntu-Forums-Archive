---
title: "RPM packages"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by NemoPaice on 2005-10-14
I have been trying all day to find these elusive w32codecs, the site mplayerhq has been down. I finally found them but it's a RPM. I can open them but seeing as I am still new to linux how do I install the w32codec-all-20050412-0.pm.0.i586.rpm? any help is VERY much appreciated

BTW they are SuSe packages. I can extract them but have no idea where they go And I am on Hoary 5.04

---

### Post by Pablo_Escobar on 2005-10-14
It's better for You to get :
[W32Codecs]("ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb")
instead of aliening the rpm :)

Hope this helps.

---

### Post by NemoPaice on 2005-10-14
#-o  That made no since to me. Sorry I am as "Lehman" as they come

---

### Post by Pablo_Escobar on 2005-10-14
Sorry, look above for link, missed it :)

Dowload it, get into terminal, cd to the directory You've downloaded it to and then type 
"sudo dpkg -i w32codecs_20050412-0.0_i386.deb"
And voila, codecs installed :)

---

### Post by manicka on 2005-10-14
You can get the deb package here

[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

download it then run 

sudo dpkg -i w32codecs_20050412-0.0_i386.deb

---

### Post by NemoPaice on 2005-10-14
Thanks a million I appreciate it

---

