---
title: "Installation failure: boot error: pae cx8"
date: 2012-11-17
forum: Mythbuntu
---

### Post by rswennen on 2012-11-17
I want to install Mythbuntu on a system with a Via mainboard but the boot even fails, when booting the error meesage says

This kernel requires pae cx8, please use a kernel appropriate for your CPU.

Where can I find the right kernel ? I downloaded the most recent installation ISO.

Thanks in advance, posted this in wrong section first

---

### Post by nickrout on 2012-11-17
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/105)

---

### Post by matt_symes on 2012-11-17
Hi
 
That sounds like you have some old hardware there. An old Pentium chip maybe ?
 
The cx8 cpu flag specifies that the cpu has the command cmpxchg8b (compare and exchange 8b) as part of its instruction set.
 
The pae cpu flag specifies that the cpu has physical address extension capability.
 
These commands below can be used to interogate various information about the processor from the command line.
 
```
sudo apt-get install dmidecode
```
 
```
 
sudo lshw -C processor
sudo dmidecode -t processor
cat /proc/cpuinfo
 

``` 
 
You could install Ubuntu using the net boot non pae mini iso and then install all the packages required for mythbuntu after installing the core Ubuntu packages.
 
From forum member kanasnoob.
 
[http://ubuntuforums.org/showpost.php?p=11847760&postcount=103](http://ubuntuforums.org/showpost.php?p=11847760&postcount=103)
 
You could also download and try to install an older version of mythbuntu. 
 
These may fix the pae issue but i am unsure about the cx8 issue as i have no hardware without that instruction.
 
Unforutunalty your hardware is now getting to the stage where it is considered obsolete and Ubuntu is not the only distro to turn its back on the non pae kernel.
 
Kind regards

---

### Post by nickrout on 2012-11-17
> **matt_symes said:**
> Hi
 
That sounds like you have some old hardware there. An old Pentium chip maybe ?
 
The cx8 cpu flag specifies that the cpu has the command cmpxchg8b (compare and exchange 8b) as part of its instruction set.
 
The pae cpu flag specifies that the cpu has physical address extension capability.
 
These commands below can be used to interogate various information about the processor from the command line.
 
```
sudo apt-get install dmidecode
```
 
```
 
sudo lshw -C processor
sudo dmidecode -t processor
cat /proc/cpuinfo
 

``` 
 of course this assumes you can get some form of linux booted at all.> 
 
You could install Ubuntu using the net boot non pae mini iso and then install all the packages required for mythbuntu after installing the core Ubuntu packages.
```
sudo apt-get install mythbuntu-desktop
``` should get everything needed to make it just like mythbuntu :)>  
From forum member kanasnoob.
 
[http://ubuntuforums.org/showpost.php?p=11847760&postcount=103](http://ubuntuforums.org/showpost.php?p=11847760&postcount=103)
 
You could also download and try to install an older version of mythbuntu. 
 
These may fix the pae issue but i am unsure about the cx8 issue as i have no hardware without that instruction.yes that doesn't seem to be dealt with in the thread I pointed to on launchpad. It's probably best to read the whole thread though [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)> 
 
Unforutunalty your hardware is now getting to the stage where it is considered obsolete and Ubuntu is not the only distro to turn its back on the non pae kernel.
 
Kind regardsyes I see "VIA" and shudder!

---

### Post by rswennen on 2012-11-19
Thanks a lot, is indeed quite old (obsolete hardware).  My objective was to try things out on the extisting hardware I have, see if I can make it working, get the Belgian EPG date etc and then go for more powerfull hardware. 
 
But think I need to consider buying some new hardware to test.  This was a mini-itx case, so I might just buy a new mini-itx motherboard.
 
What do you think about this one ?
[http://www.mini-itx.com/store/~GA-D525TUD](http://www.mini-itx.com/store/~GA-D525TUD)
 
I want to use the system as a backend and play to use XBMC front ends.
 
Is the above a good choice ? It will allow me to re-use my case and IDE hard disk.  My only concern is I will be limited to one slot for analoge cable tuner, plan to add one or 2 HD-PVR boxed and probably a DVB-T USB dongle.
 
Or is ther any other good hardware you suggest.  I am looking for something that works out of the box, am not experienced enough to tweak with drivers etc.  Just want to run the MythBuntu cd and go :-)

---

