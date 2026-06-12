---
title: "updated pkgs to 2.6.32-33 from 32-28 and it disabled wireless"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by sanmanx on 2011-09-05
Greetings all,
10.04 LTS.  Asus USB N13 adapter.
Viewing various posts, I successfully got the wireless working with 2.6.32-28-generic.  Kudos to all, especially chili555.  I then ran the Update Manager and took everything it suggested.  Now with 2.6.32-33-generic, the wireless no longer works.  There are some things I just don't understand, even how it is working in 2.6.32-28.

Here is the 2.6.32-28 setup, which is working:
ken@ken-hp:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ken@ken-hp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"sanman_net"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 7C:4F:B5:D0:9C:5E   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-45 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ken@ken-hp:~$ lsmod | grep -i rt2
ken@ken-hp:~$ lsmod | grep -i rt3
rt3070sta             517351  1 
ken@ken-hp:~$ dmesg | grep -i rt2
[    9.210316] usbcore: registered new interface driver rt2870
[   13.174370] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
ken@ken-hp:~$ dmesg | grep -i rt3
ken@ken-hp:~$ 
ken@ken-hp:~$ ll /etc/Wireless/RT2870STA/
total 12
drwxr-xr-x 2 root root 4096 2011-09-04 21:56 ./
drwxr-xr-x 4 root root 4096 2011-09-04 21:53 ../
-rwxr-xr-x 1 root root 1016 2011-09-04 21:56 RT2870STA.dat*
ken@ken-hp:~$ ll /etc/Wireless/RT3070STA/
total 12
drwxr-xr-x 2 root root 4096 2011-09-04 21:46 ./
drwxr-xr-x 4 root root 4096 2011-09-04 21:53 ../
-rwxr-xr-x 1 root root 1016 2011-09-03 20:53 RT2870STA.dat*
ken@ken-hp:~$
ken@ken-hp:~$ more /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070sta
root@ken-hp:/home/ken#

I'm confused about the lsmod output showing rt3070sta, yet everything else points to RT2870STA.  I don't really understand what is going on here.

Here is the same output for 2.6.32-33, which does not work:
root@ken-hp:/home/ken# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ken-hp:/home/ken# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ken-hp:/home/ken# lsmod | grep -i rt2
rt2870sta             461843  0 
root@ken-hp:/home/ken# lsmod | grep -i rt3
root@ken-hp:/home/ken# dmesg | grep -i rt2
[    8.937591] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.422406] usbcore: registered new interface driver rt2870
root@ken-hp:/home/ken# dmesg | grep -i rt3
root@ken-hp:/home/ken# more /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070sta
root@ken-hp:/home/ken# 

The lsmod output shows rt2870sta here, seems significant compared to the other version.
I tried a "sudo modprobe rt3070sta", but to no avail.
Do I need to do another "make" and "make install" in my driver folder(2009_1110_RT3070_Linux_STA_v2.1.2.0)?
It seems like I need to somehow make the Kernal recognize this?

And is there a way to make this permanent, so I don't have to do this everytime?  Even though, if I understand what is happening, then it won't be that big of a deal to do whatever is needed.

Thanks in advance for any assistance,
Ken

---

### Post by praseodym on 2011-09-05
Hi,

did you install the metapackage for your kernel headers or "only" the header files for the (at that time) current kernel 2.6.32-28?

```
sudo apt-get install --reinstall linux-headers-generic dkms build-essential
```
reboot and check again.

---

### Post by ajgreeny on 2011-09-05
It may also be worth enabling the "Proposed" repos in your software sources and installing the 2.6.35-30-generic kernel along with the linux-headers and linux-headers-generic for that kernel.  There are usually improvements in drivers in newer kernels, but I have no idea if it will help in your specific case.

---

### Post by sanmanx on 2011-09-05
I used the GUI: System->Update Manager to do the updates.  So I don't know how that deals with the kernal headers and header file stuff that was mentioned.
But I then ran:  sudo apt-get install --reinstall linux-headers-generic dkms build-essential
and it ran fine, but didn't seem to effect anything.  
2.6.32-28 still has wireless, 2.6.32-33 does not.

When logged into the 2.6.32-28 and I run the Update Manager, it says everything is up to date now.
So now my question may be changing:  Why do I need 2.6.32-33, and why did the Update process create it in the first place, if Update Manager says all is well with 2.6.32-28?  I can't check what Update Manager would say if I ran it in the 2.6.32-33 kernal, since that kernal does not have wireless.

---

### Post by praseodym on 2011-09-05
Updates do not depend on the kernel number. If it is up-to-date, then it is up-to-date. You can install the package "startupmanager" to choose 2.6.32-28 as default boot-kernel in Ubuntu.

Another hint: Try this driver:

[http://forum.ubuntuusers.de/post/2809590/](http://forum.ubuntuusers.de/post/2809590/)

Just copy/paste the commands into the terminal, its a newer one which worked there, version **2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO**

---

### Post by nm_geo on 2011-09-05
Kem 

If I understand correctly.

Try the following

```
sudo modprobe -r rt3070sta
```

That removes the rt3070sta temporarily

Then 

```
sudo modprobe rt2870sta
```

That should tell us if it will work the way you wanted.

---

### Post by sanmanx on 2011-09-05
I downloaded startupmanager and have 2.6.32-28 set as the default, with wireless.

I'll try the other ideas and the newer driver when I load Natty Narwhal and do some testing.

Thanks all!

---

