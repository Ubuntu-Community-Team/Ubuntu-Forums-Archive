---
title: "Configuring PPP on the shell"
date: 2006-05-13
forum: Networking &amp; Wireless
---

### Post by svetho on 2006-05-13
Hi to all. I have done a chroot'ed installation of the Ubuntu base system under SuSE 8.2. Even though I'm not exactly a Linux newby this low-level configuration work is a little beyond my skills.
My DSL modem is connected with my network card on eth0. Although the installation guide at [http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html) explains how to configure the network with DHCP this is quite useless for me. Can anyone point out which information has to go where (to which configuration files) and possibly if I can re-use any existing configuration files from my SuSE installation? I need to get my ADSL connection to work in order to proceed with the Ubuntu installation.

Any help will be greatly appreciated.
Thanks in advance

SveTho

---

### Post by cyracks on 2006-05-13
I configured my adsl with

```
sudo pppoeconf
```

---

