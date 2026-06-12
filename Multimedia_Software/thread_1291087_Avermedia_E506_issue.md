---
title: "Avermedia E506 issue"
date: 2009-10-14
forum: Multimedia Software
---

### Post by JollyJohn on 2009-10-14
Hi

I have installed Ubuntu 9.04 on an Acer Aspire 3000 laptop.  All good.
I have installed MythTV and got it working - mostly.
I am having problems installing the driver for my Avermedia E506 cardbus tuner.  I have dowloaded the SUSE package but when I try and install it I get the following

john@scout:~$ cd Documents
john@scout:~/Documents$ cd AVerMedia-MTSA-SUSE10-0.36Beta-i386
john@scout:~/Documents/AVerMedia-MTSA-SUSE10-0.36Beta-i386$ ls
AVerMedia_Driver_Manager.sh                    dvbscan  tools
AVerMedia-MTSA-SUSE10-0.36Beta-1.i386.rpm      dvb-t
AVerMedia-MTSA-SUSE10-SMP-0.36Beta-1.i386.rpm  README
john@scout:~/Documents/AVerMedia-MTSA-SUSE10-0.36Beta-i386$ sudo  ./AVerMedia_Driver_Manager.sh --install
[sudo] password for john: 
./AVerMedia_Driver_Manager.sh: 8: RPMNAME[0]=AVerMedia-MTSA-SUSE10: not found
./AVerMedia_Driver_Manager.sh: 9: RPMNAME[1]=AVerMedia-MTSA-SUSE10-SMP: not found
./AVerMedia_Driver_Manager.sh: 110: Syntax error: Bad for loop variable
john@scout:~/Documents/AVerMedia-MTSA-SUSE10-0.36Beta-i386$ 

Any help gratefully appreciated.

---

