---
title: "using l7 filter"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by mbuotidem on 2010-07-29
Hi all. im a linux newbie. I work at a cybercafe and am trying to prevent users from abusing my connection by running p2p software. 

after doing some googling, i stumbled upon l7 filters. as a newbie, i sought the most simple and easy to understand tutorial as to how to set it up but the only english tutorials i found were for other os's like centOS etc. but i did find a thread on this forum wherein someone was seeking a simple tutorial. [http://ubuntuforums.org/showthread.php?t=1042153](http://ubuntuforums.org/showthread.php?t=1042153). so i went to the page that was linked in the hopes of using google translate to help me get the meaning. 

i did and this is the output i got: 
> 

Mumet-mumet nyari ngblog way to make P2P, finally get a tutorial from the blog mas mantabs Andrew Pakpahan, edited as necessary

# Apt-get install build-essential
# Apt-get install linux-headers
# Apt-get install iptables-dev

grab the source from the kernel and iptables

# Apt-get install linux-source
# Apt-get source iptables

please adjust your kernel version you use. kernel-source apt-get results in / usr/src/linux-source-2.6.24.tar.bz2 please in extracts

# Cd / usr / src $ sudo tar xvjf linux-source-2.6.24.tar.bz2

and create a symbolic link / usr / src / linux to the results of earlier ekstract

# Sudo ln-s / usr/src/linux-source-2.6.24 / usr / src / linux

Source iptables apt-get results in the current folder. copy and extract it to / usr / src in order to find the folder / usr/src/iptables-1.3.8.0debian1 preparations are finished, please download the source from [http://ipp2p.org/downloads/ipp2p-0.8.2.tar.gz](http://ipp2p.org/downloads/ipp2p-0.8.2.tar.gz) ipp2p and also files patchnya! (This is important to avoid errors when compiling)
First download the file ipp2p

# Wget [http://ipp2p.org/downloads/ipp2p-0.8.2.tar.gz](http://ipp2p.org/downloads/ipp2p-0.8.2.tar.gz)

Next download the patch file

# Wget [http://sources.gentoo.org/viewcvs.py/](http://sources.gentoo.org/viewcvs.py/) * checkout * / gentoo-x86/net-firewall/ipp2p/files/ipp2p-0.8.2-kernel-2.6.22.patch
# Tar xvzf ipp2p-0.8.2.tar.gz
# Cd ipp2p-0.8.2

Before compiled, there should be edited first row in makefilenya

# Vi Makefile

Find this line:

ld-shared-o libipt_ipp2p.so libipt_ipp2p.o
Then replace it with this:
$ (CC)-shared-o libipt_ipp2p.so libipt_ipp2p.o
# Patch-p1 <../ipp2p-0.8.2-kernel-2.6.22.patch

Next compile ipp2p

# Make

Copy these files to compile the iptables library

Libipt_ipp2p.so # cp / lib / iptables
Ipt_ipp2p.ko # cp / lib / modules / `uname-r` / kernel/net/ipv4/netfilter

then run depmod

# Depmod-a

please test whether it can be used

$ Sudo iptables-m ipp2p - help

if already there, please read the manual to use it ^ ^ _ to say goodbye to paket2 p2p please type:

$ Sudo iptables-A FORWARD-m-ipp2p ipp2p-j DROP

pake day testdrive

# Iptables-L FORWARD-nv

weleh-weleh .. dah day ngdrop 156M, sadistic Bener


as you can see, it's not completely english. besides i barely understand linux, just starting to use it and i am hoping that u guys could help me put this in an easier to understand format so that i don't wreck anything.

i am also worried that this may be outdated given that i am using Lucid Lynx with the latest kernel version. 

or if anyone has an english tutorial link, i would appreciate it. 

thanks

---

### Post by mbuotidem on 2010-08-17
well, eventually, i didn't bother about that translated stuff. i just went to the sourceforge page for l7 filter and did my best to follow the instructions there. 

I did ok. it worked or at least I think so.

---

