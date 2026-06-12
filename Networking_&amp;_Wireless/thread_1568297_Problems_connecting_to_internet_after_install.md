---
title: "Problems connecting to internet after install"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by vc0489 on 2010-09-05
Hi, I just installed Ubuntu 10.04 and I am a total newbie.

I am having trouble connecting to the internet - neither the wireless or cable connections work. I have no problems when I boot under windows 7.

When I try going to Hardware Drivers I get the message "Downloading package indexes failed, please check your network status. Most drivers will not be available". I have tried reinstalling Ubuntu to no avail.

Can anyone give me some help?

Thanks a lot!

---

### Post by Sonsum on 2010-09-05
Welcome to Ubuntu! Hopefully we can get this fixed for you.

First of all, what kind of computer is it? (make and model would be helpful!)

---

### Post by vc0489 on 2010-09-05
Thanks for your welcome!

My computer is a Acer ASPIRE 5745G laptop.

Also, my ethernet card is Atheros AR8151 PCI-E Gigabit and my wireless card is Broadcom 802.11n

---

### Post by Iowan on 2010-09-05
Right-click the Network Manager icon and verify Networking and Wireless are enabled. Otherwise, one of these links might be helpful:
[http://ubuntuforums.org/showthread.php?t=1564615]("http://ubuntuforums.org/showthread.php?t=1564615")
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")

---

### Post by vc0489 on 2010-09-05
Thanks for your reply.

When I right click the Network Manager icon I see that Networking is already enabled, however I don't see "Enable Wireless"

I went into the first link and then went into **Users and Groups** > **User Previleges** > **Change User Settings** and ticked **Connect to wireless and ethernet networks** but that didn't seem to solve the problem.

Then I saw this thread [http://newyork.ubuntuforums.org/showthread.php?t=1495123](http://newyork.ubuntuforums.org/showthread.php?t=1495123) but when I downloaded the AR81Family Linux driver and tried 
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz

I got this

```

./atl1e.7
./atl1e.spec
./at_osdep.h
./copying
./dkms.conf
./ldistrib.txt
./Makefile
./pci.updates
./readme
./release_note.txt
./src/
./src/atl1c.h
./src/atl1c_ethtool.c
./src/atl1c_hw.c
./src/atl1c_hw.h
./src/atl1c_main.c
./src/atl1c_param.c
./src/atl1e.h
./src/atl1e_ethtool.c
./src/atl1e_hw.c
./src/atl1e_hw.h
./src/atl1e_main.c
./src/atl1e_param.c
./src/at_common.h
./src/at_common_main.c
./src/at_osdep.h
./src/kcompat.c
./src/kcompat.h
./src/kcompat_ethtool.c

gzip: stdin: decompression OK, trailing garbage ignored
./src/Makefile
./src/Module.markers
./src/Module.symvers
./src/modules.order
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```Also when I type sudo lshw -C netowrk into the terminal I can see both the ethernet and wireless cards but they are both "Unclaimed"

What should I try now?

---

