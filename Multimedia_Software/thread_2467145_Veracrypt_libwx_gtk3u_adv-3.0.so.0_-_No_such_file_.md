---
title: "Veracrypt: libwx_gtk3u_adv-3.0.so.0 - No such file or directory."
date: 2021-09-16
forum: Multimedia Software
---

### Post by antonio-cpr on 2021-09-16
Hi! 
I'm using Ubuntu 20.04.2 LTS and I downloaded Veracrypt(veracrypt-1.24-Update7-Ubuntu-20.04-amd64.deb) from the following website.
[https://www.veracrypt.fr/en/Downloads.html](https://www.veracrypt.fr/en/Downloads.html)

The problem is when I try to run it I get the following error message:
> antonio@antonionote:~$ veracrypt
veracrypt: error while loading shared libraries: libwx_gtk3u_adv-3.0.so.0: cannot open shared object file: No such file or directory

What do I do now?

---

### Post by bobunderwood99 on 2021-09-16
[https://itsfoss.com/install-deb-files-ubuntu/](https://itsfoss.com/install-deb-files-ubuntu/)

---

### Post by Holger_Gehrke on 2021-09-17
According to [packages.ubuntu.com]("https://packages.ubuntu.com/search?searchon=contents&keywords=libwx_gtk3u_adv-3.0.so.0&mode=exactfilename&suite=focal&arch=any") that library is in the package 'libwxgtk3.0-gtk3-0v5'. A simple 'sudo apt install libwxgtk3.0-gtk3-0v5' will install it. If you had installed the veracrypt deb-file with 'sudo apt install *path-and-filename*' then apt should have seen the dependency and installed the needed libraries.

Holger

---

