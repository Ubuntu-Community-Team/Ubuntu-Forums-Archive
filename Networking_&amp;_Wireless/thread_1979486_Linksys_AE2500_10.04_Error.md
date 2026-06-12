---
title: "Linksys AE2500 10.04 Error"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by TB411 on 2012-05-13
Im using Ubuntu Studio 10.04 64-bit. Im trying to install ndiswrapper according to instructions (below).
----------------------------------------------------------------

tb411@ubuntu:/media/MYDRIVE$ cd ndiswrapper-1.57
tb411@ubuntu:/media/MYDRIVE/ndiswrapper-1.57$ make uninstall
rm -f /usr/share/man/man8/ndiswrapper.8
rm -f /usr/share/man/man8/loadndisdriver.8
make -C driver uninstall
make[1]: Entering directory `/media/MYDRIVE/ndiswrapper-1.57/driver'
Makefile:36: *** Cannot find kernel version in /lib/modules/2.6.32-21-preempt/build, is it configured?. Stop.
make[1]: Leaving directory `/media/MYDRIVE/ndiswrapper-1.57/driver'
make: *** [uninstall] Error 2
----------------------------------------------------------------

Im trying to install ndiswrapper according to these directions ([http://ubuntuforums.org/showthread.php?t=1805830&page=9](http://ubuntuforums.org/showthread.php?t=1805830&page=9))

Re: Linkys AE2500 USB Adapter Not Working
I had the exact same problem tonight but I was able to get it up and running...Below you will find how I did this

1) Go to [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/) and download the ndiswrapper-1.57.tar.gz
2) Download the AE2500 Driver for WINDOWS XP at [http://homesupport.cisco.com/en-us/s...dapters/AE2500](http://homesupport.cisco.com/en-us/s...dapters/AE2500)
3) UNZIP the AE2500 Driver ZIP package from CISCO and then transfer the unzipped folder and ndiswrapper-1.57.tar.gz to a thumbdrive
4) Mount said thumbdrive in your System, bring up terminal and find your thumbdrive (we will say it mounted as MYDRIVE)
*************************EXAMPLE****************** ********
*you@yourputer:/media/MYDRIVE$*********************
***************END EXAMPLE****************************
5) Extract your file ndiswrapper-1.57.tar.gz file
**********************************EXAMPLE********* ***************************
*you@yourputer:/media/MYDRIVE$tar zxvf ndiswrapper-1.57.tar.gz*
*********************************END EXAMPLE*******************************
6) Navigate to the new directory where ndiswrapper-1.57.tar.gz was unzipped to and run make uninstall followed by the make command, finally run the make install command
**********************************EXAMPLE********* ***************************
*you@yourputer:/media/MYDRIVE$cd ndiswrapper-1.57 *************
*you@yourputer:/media/MYDRIVE/ndiswrapper-1.57$make uninstall*
*******BLAH, BLAH, BLAH, BLAH********************************************
*******BLAH, BLAH, BLAH, BLAH********************************************
*******BLAH, BLAH, BLAH, BLAH********************************************
*you@yourputer:/media/MYDRIVE/ndiswrapper-1.57$make **********
*******BLAH, BLAH, BLAH, BLAH********************************************
*******BLAH, BLAH, BLAH, BLAH********************************************
*******BLAH, BLAH, BLAH, BLAH********************************************
*you@yourputer:/media/MYDRIVE/ndiswrapper-1.57$sudo make install**
*********************************END EXAMPLE*******************************
7) After this gets done executing we are ALMOST ready to make the driver work on Ubuntu we need to find the folder where the .inf and .sys files are (for the WINDOWS XP drivers)...lets assume on the Thumb drive under a folder named XP...navigate to that folder. Once there run the ndiswrapper -i driver.inf command. Then run ndiswrapper -l command, you should see your driver
**********************************EXAMPLE********* ***************************
*you@yourputer:/media/MYDRIVE$cd xp *************
*you@yourputer:/media/MYDRIVE/xp$sudo ndiswrapper -i bcmwlhigh5.inf*
*you@yourputer:/media/MYDRIVE/xp$ndiswrapper -l *
*********************************END EXAMPLE*******************************

FINALLY you will complete this last step to load your driver. Run the modprobe ndiswrapper command
**********************************EXAMPLE********* ***************************
*you@yourputer:/media/MYDRIVE/xp$sudo modprobe ndiswrapper****
*********************************END EXAMPLE*******************************

After completing step 8 my USB Adapter started working and I had a list of networks to connect to, connected to my home network and immediately posted my solution here for you to see. I hope this solution works for you, best of luck.
--------------------------------------------

Please help!
Please help with this error!

---

### Post by chili555 on 2012-05-13
> Cannot find kernel version in /lib/modules/2.6.32-21-preempt/build, is it configured?. Stop.In order to compile from source, you need the packages build-essential and linux-headers-generic. Do you have those? Why not install from the Ubuntu repositories. Can you get a temporary wired ethernet connection?

---

### Post by TB411 on 2012-05-13
> **chili555 said:**
> Can you get a temporary wired ethernet connection?

Nope. Should I just use Ubuntu 10.10 or Ubuntu studio 10.10 instead of 10.04? I only wanted studio for a couple programs I could get on Ubuntu vanilla easily.

---

### Post by TB411 on 2012-05-13
> **TB411 said:**
> Nope. Should I just use Ubuntu 10.10 or Ubuntu studio 10.10 instead of 10.04? I only wanted studio for a couple programs I could get on Ubuntu vanilla easily.

I think I solved my problem with my own question.

---

### Post by chili555 on 2012-05-13
> Should I just use Ubuntu 10.10 or Ubuntu studio 10.10 instead of 10.04?It makes no difference. Your AE2500 requires ndiswrapper in any version. Did you just install 10.04? I think ndiswrapper in on the install disk. Load it and look around in, I think, pool/n. If ndiswrapper-common and ndiswrapper-utils are there, right-click them and select Install...You may need to drag and drop them to your desktop and then, in a terminal:```
cd Desktop
sudo dpkg -i ndis*.deb
```Then proceed at step #7.

---

### Post by TB411 on 2012-05-13
Alright, Im on 10.10 Ubuntu (not studio). I installed ndiswrapper
but am having trouble installing the driver.
-------------------------------------------------------------------------------

tb411@DCP-Ad:/media/MYDRIVE/AE2500$ sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
couldn't find section "Linksys_AE1200.files.NTamd64" -
installation may be incomplete
couldn't find section "Linksys_AE2500.files.NTamd64" -
installation may be incomplete
--------------------------------------------------------------------------------

---

### Post by chili555 on 2012-05-13
Do you have a 64-bit system or 32-bit?```
arch
```

---

### Post by TB411 on 2012-05-13
> **chili555 said:**
> Do you have a 64-bit system or 32-bit?

64-bit Cpu and Ubuntu 10.10 64-bit

---

### Post by chili555 on 2012-05-13
Please see posts #55 and 56 here: [http://ubuntuforums.org/showthread.php?t=1805830&page=9](http://ubuntuforums.org/showthread.php?t=1805830&page=9)

---

### Post by TB411 on 2012-05-13
> **chili555 said:**
> Please see posts #55 and 56....

Thanks! But still no luck...

---

### Post by TB411 on 2012-05-13
Still no luck. After restart the system still wont even acknowledge its connected.

---

### Post by betterhands on 2012-06-17
same issue for me as well.  tried a few of the existing posted solutions, but not luck yet.

---

