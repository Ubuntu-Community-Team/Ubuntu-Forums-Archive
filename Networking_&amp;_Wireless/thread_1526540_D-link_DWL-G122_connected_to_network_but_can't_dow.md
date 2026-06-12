---
title: "D-link DWL-G122 connected to network but can't download"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by Mortesins93 on 2010-07-08
Hi,
I had Xubuntu 9.10 installed on my computer and everything worked fine, i could download and surf the net pretty fast, but all of a sudden i couldn't do this anymore. The adapter was still connected to the network but when i opened firefox it worked for 5 seconds and then it would not load any pages, and even synaptic couldn't download any packages, even though it was still connected to the network. So i tried to reinstall network manager but it didn't work, then something happened and i couldn't access my Xubuntu anymore so I decided to delete the partition and install Xubuntu 10.04. I still have the same problem. What should i do? I am sure it is not a problem with the adapter because it works on the Windows partition.
PLEASE HELP!!! I CAN'T TAKE USING WINDOWS ANYMORE.
Thanks in advance.

---

### Post by Mortesins93 on 2010-07-16
I managed to solve the problem. Thanks to Frankvw. I disinstalled Xubuntu and installed it again and the i just added a DHCP client ID in the IPv4 options.

---

### Post by Mortesins93 on 2010-08-09
IT DOESN'T WORK ANYMORE. WHY????????? I DON'T GET IT, it worked for like two months and now it doesn't work anymore. I AM SO TIRED OF THIS.
WHAT SHOULD I DO???

---

### Post by Mortesins93 on 2010-08-18
Now it works again, i just put in the MAC adress. But it does not work on my sister's Ubuntu 8.10 why?? I cannot put in the MAC adress there, if I do it doesn'ìt let me apply the changes, why??
Would switching to Ubuntu 10.04 solve the problem for good???
Please help, it is a big deal otherwise I will have to switch back to windows and I can't stand it.

---

### Post by Mortesins93 on 2010-08-21
Well I installed Ubuntu 10.04 and it still doesn't work!!! I can't stand it. Why?????l

---

### Post by heke on 2010-09-02
I seem to have  a similar non-functionality with my old laptop and a wireless usb stick

system:   xubuntu 10.04
wireless:  Dlink dwl-g122 rev. E1 (usb)

There seems to be a solution if I manage to compile the relevant ralink drivers. 
But when I try the compilation I get the following error message:
/lib/modules/2.6.32-24-generic/build: no such file or directory

So I need to get whatever files are there in that ../build directory.
What .deb package does contain those files? They are missing in the basic
xubuntu distribution. My searches for the said files have been unsuccesfull.

---

### Post by Mortesins93 on 2010-09-02
I don't know, since i installed ndiswrapper with its windows drivers I had no problems, but I'll never say my problem is solved because in the past it had worked fine for a long time and then all the sudden it didn't.

---

