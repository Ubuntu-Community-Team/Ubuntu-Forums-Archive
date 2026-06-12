---
title: "Avermedia H826 in Ubuntu 11.04"
date: 2011-06-23
forum: Multimedia Software
---

### Post by Ranger198 on 2011-06-23
I have the Avermedia AVERTVHD Volar Max (H826) USB TV tuner.  It worked great in 10.10 using the linux drivers available on the Aver site.

I can't however get it to work in 11.04

The farthest I've been able to troubleshoot is the output of lsusb but recognition beyond that point is not working.

Bus 001 Device 003: ID 07ca:1826 AVerMedia Technologies, Inc. 

Any help would be appreciated.

---

### Post by jwevandijk on 2011-07-05
I got it working with the help of a few published patches. I kept track of what I did  (unfortunately an exception with me) in the attached file. I packed this together with the patched *.c files for convenience.

The problem that remains with me is that I have to do the insmod commands:
sudo insmod ./averusbh826d.ko
sudo insmod ./h826d.ko

after each boot. If somebody could teach me how to make it permanent that would be of great help.

Please keep in mind in using my files and in answering my questions that I am quite out of my depth in these matters. So please be careful!

---

