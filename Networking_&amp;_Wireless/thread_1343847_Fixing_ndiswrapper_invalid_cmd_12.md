---
title: "Fixing ndiswrapper invalid cmd 12"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by W. Irving on 2009-12-02
The latest ndiswrapper will not work with WEP or WPA due to (as I understand) this bug:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)
[*][http://sourceforge.net/tracker/?func=detail&aid=2907179&group_id=93482&atid=604450](http://sourceforge.net/tracker/?func=detail&aid=2907179&group_id=93482&atid=604450)
[/LIST]

If dmesg returns several lines like these:

> [  227.277096] ndiswrapper (iw_set_auth:1602): invalid cmd 12

then you're affected.

I got it to work on Karmic by building my own ndiswrapper - here's a brief howto for those who, like me, are new to the compiling business. It requires that you know how to use a terminal.

I used these instructions, slightly modified:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling%20the%20latest%20version%20of%20ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling%20the%20latest%20version%20of%20ndiswrapper)

First off, if the computer (computer A) does not have the internet connexion required to install the various tools for building ndiswrapper, the required packages can very easily be downloaded on a different computer (computer B from now on) and transferred by means of USB memory, CD, Bluetooth, avian carrier..
This assumes both computers are running exactly the same version of Ubuntu. If not, you shall have to find another way of downloading the required packages. In theory, I presume this method would also work in that case:
1. copy /etc/apt/sources.list from the computer A, to computer B (back up the current sources.list on computer B!)
2. run sudo apt-get update on computer B
3. download the packages as instructed below
4. restore the old sources.list on computer B

If computer A has indeed a working connexion, just run
```
sudo apt-get install linux-headers-$(uname -r) dh-make fakeroot gcc-4.4 build-essential
```

and skip to step 5.

On computer B:

1. Empty your /var/cache/apt/archives directory. This seems to be where aptitude keeps installation files, so emptying it appears harmless, but you must be root:

```
sudo rm /var/cache/apt/archives/*.deb
```

Do not delete *, as this dir contains the file lock and the dir partial!

2. Find out which kernel computer A has by executing..

```
uname -r
```

which will return something like..

> 2.6.31-15-generic

3. Download the packages required to install the build environment. Insert computer A's kernel version into the linux-headers- package name, as below:

```
sudo apt-get -d --reinstall install linux-headers-2.6.31-15-generic dh-make fakeroot gcc-4.4 build-essential
```

The -d switch will instruct aptitude to just download the files, and not install them. Not sure whether --reinstall is actually needed, but I assumed that if computer B already has any of these packages or dependencies installed, then it wouldn't download them again. The wiki instructions says to use gcc-3.4, but this is not available so 4.4 will have to do.

4. When apt is done downloading, transfer all the .deb files in /var/cache/apt/archives to computer A. To install, run this from within the directory you placed the .deb files:

```
sudo dpkg -i ./*
```

Once done, you will have your build environment set up.

5. Get ndiswrapper 1.55 (currently the latest exhibiting the aforementioned bug) here: [http://sourceforge.net/projects/ndiswrapper/files/stable/1.55/ndiswrapper-1.55.tar.gz/download](http://sourceforge.net/projects/ndiswrapper/files/stable/1.55/ndiswrapper-1.55.tar.gz/download) 

6. Unpack the downloaded tar on computer A and change directory:

```
tar xvfz ndiswrapper-1.55.tar.gz
cd ndiswrapper-1.55/driver
```

7. Get the patch by Rene van Paassen:
[http://sourceforge.net/tracker/?func=detail&aid=2907179&group_id=93482&atid=604450](http://sourceforge.net/tracker/?func=detail&aid=2907179&group_id=93482&atid=604450)
(click Attached file and download iw_ndis.c.diff)

Place this file in ndiswrapper-1.55/driver and run:

```
patch < iw_ndis.c.diff
```

8. I encountered yet another bug with this version, which prevented me from compiling, with the error:
> error: implicit declaration of function 'cmpxchg8b'
*Perhaps it would be wise to try steps 9 and onwards and see if it works, and only apply this patch if you encounter the same bug!*
There's a patch though.. [http://bugs.gentoo.org/show_bug.cgi?id=280057](http://bugs.gentoo.org/show_bug.cgi?id=280057)
Right click and save ndiswrapper-2.6.31.patch and place this in ndiswrapper-1.55/driver as well and run:

```
patch < ndiswrapper-2.6.31.patch
```

9. Clean up your current system (cd out of drivers!):

```
cd ..
sudo make uninstall
```

As it instructs you, keep running it until it does not output any more lines beginning with "removing".

10. Then:

```
sudo make
```

followed by

```
fakeroot
```

and

```
sudo make install
```

11. The wiki instructions aren't clear on this, but I believe you need to run exit at this point to get out of fakeroot, so run:

```
exit
```

You should now have a working version of ndiswrapper.
Have I missed anything?

---

### Post by clausfse on 2009-12-03
Thanks for this excellent description. Everything worked like described. Even the error in step 8 occured and could be fixed.

/Claus

---

### Post by W. Irving on 2009-12-07
> **clausfse said:**
> Thanks for this excellent description. Everything worked like described. Even the error in step 8 occured and could be fixed.

/Claus

Glad it worked! Hope the repo version will patched soon.

---

### Post by foxy123 on 2009-12-08
Strangely enough it has fixed the problem with cmd 12, but I still could not connect to the network which uses WPA encryption :(

---

### Post by hellomoto on 2009-12-09
i did the following patch on two ubuntu PCs that have the dmesg error. 

Following your tutorial (which installed perfectly) the dmesg error went. 

However this did not solve the issue of ndiswrapper not working correctly on secured networks. :(

Hopefully a patch will come out soon!

---

### Post by W. Irving on 2009-12-09
Thanx to all for posting back your results!

While the procedure worked for me, I could not, as you, get my device to work with encrypted networks. I attributed this issue to wpa_supplicant instead, but now it would seem ndiswrapper is in fact to blame after all..

Has anyone actually got ndiswrapper 1.55 to work with WEP or WPA?

---

### Post by hellomoto on 2009-12-09
Update: I have got my WPA connections to work after reading this:

[http://ubuntuforums.org/showthread.php?t=1284891]("http://ubuntuforums.org/showthread.php?t=1284891")

So in short if you are using ndiswrapper with WPA connection and are unable to connect. Follow the above tutorial.


However if you are still unable to connect. Then try running the command below when trying to connect.

```
 sudo renice +19 $(pidof wpa_supplicant) 
```

worked for me on x2 computers.

---

### Post by W. Irving on 2009-12-09
After a bit more fiddling about, I've tried compiling ndiswrapper versions 1.53 & 1.54.
My conclusions are as follows..

**1.53** and earlier will not work, due to the switch to a more recent kernel which drops support for some ancient network API:
> /home/elias/Skrivbord/ndiswrapper-1.53/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:
/home/elias/Skrivbord/ndiswrapper-1.53/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’

> 
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c: In function ‘notifier_event’:
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1693: error: ‘struct net_device’ has no member named ‘open’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c: In function ‘ndis_start_device’:
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1749: error: ‘struct net_device’ has no member named ‘open’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1750: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1751: error: ‘struct net_device’ has no member named ‘stop’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1752: error: ‘struct net_device’ has no member named ‘get_stats’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1753: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1754: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1758: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1759: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/elias/Skrivbord/ndiswrapper-1.53/driver/wrapndis.c:1774: error: ‘struct net_device’ has no member named ‘poll_controller’


(required patching with [http://connie.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch](http://connie.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch))

**1.54** is will not compile unless line 1747 of driver/wrapndis.c is changed from
```
.poll_controller = ndis_poll_controller;
```
into
```
.ndo_poll_controller = ndis_poll_controller,
```

While make succeeds, this happens:
> /home/elias/Skrivbord/ndiswrapper-1.54/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:
/home/elias/Skrivbord/ndiswrapper-1.54/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’

And the results are the same as with 1.55.

While I can't be certain ndiswrapper is actually at fault, and not wpa_supplicant, the number of reports here pointing to ndiswrapper being the culprit makes it seem likely.

---

### Post by W. Irving on 2009-12-09
> **hellomoto said:**
> Update: I have got my WPA connections to work after reading this:

[http://ubuntuforums.org/showthread.php?t=1284891]("http://ubuntuforums.org/showthread.php?t=1284891")

So in short if you are using ndiswrapper with WPA connection and are unable to connect. Follow the above tutorial.


However if you are still unable to connect. Then try running the command below when trying to connect.

```
 sudo renice +19 $(pidof wpa_supplicant) 
```

worked for me on x2 computers.


Didn't work for me, but thanx for the suggestion! Might be of use to someone else.

---

### Post by bkratz on 2009-12-09
> **W. Irving said:**
> Didn't work for me, but thanx for the suggestion! Might be of use to someone else.




The cmd 12's are gone, but that patch didn't work for me either with WPA2.

---

### Post by hellomoto on 2009-12-10
> **W. Irving said:**
> Didn't work for me, but thanx for the suggestion! Might be of use to someone else.

When I have used this command it still takes network manager up to 3 goes to connect but its better than not at all. I don't see it as a 100% fix but it might get some people connected as a temporary solution. :)

---

### Post by gumshore on 2009-12-10
I tried W.Irving's suggestion to compile, but even so, I still get the invalid cmd 12 error. I will try to compile again, since I changed some other things related to the kernel. I will post back with the results.

---

### Post by PeteLee on 2009-12-11
I have, at best, rudimentary knowledge of UNIX/Linux overall, so please pardon my ignorance.

I did run dmesg and am not seeing cmd 12.  However, the wireless connectivity on a Dell Inspiron 1150 (Broadcom chipset) was not working and wasn't seeing ANY access points and my wireless adapter appeared to be disabled, so I tried the instructions noted in this thread, but to no avail.

I did notice, however, that the dmesg output made a reference to needing something from here:
[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)

I installed the drivers recommended by the kernel.org instructions after running: "lspci -vnn | grep 14e4" (my PCI-ID is 14e4:4320).  After installing these and rebooting, things are mysteriously working just fine with WPA-Personal, and without needing to renice wpa_supplicant.

Perhaps what I'm mentioning is already obvious, but I thought I'd put it out there.

---

### Post by hellomoto on 2009-12-11
> **PeteLee said:**
> 

I did run dmesg and am not seeing cmd 12.  However, the wireless connectivity on a Dell Inspiron 1150 (Broadcom chipset) was not working and wasn't seeing ANY access points and my wireless adapter appeared to be disabled

If you do not get the pre mentioned error from dmesg the above tutorial will not help you. :)

---

### Post by W. Irving on 2009-12-11
> **gumshore said:**
> I tried W.Irving's suggestion to compile, but even so, I still get the invalid cmd 12 error. I will try to compile again, since I changed some other things related to the kernel. I will post back with the results.

Remember to get rid of the old, repo ndiswrapper first: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling%20the%20latest%20version%20of%20ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling%20the%20latest%20version%20of%20ndiswrapper)

And sudo make uninstall (several times, if necessary) before you sudo make.

---

### Post by W. Irving on 2009-12-11
> **PeteLee said:**
> I have, at best, rudimentary knowledge of UNIX/Linux overall, so please pardon my ignorance.

I did run dmesg and am not seeing cmd 12.  However, the wireless connectivity on a Dell Inspiron 1150 (Broadcom chipset) was not working and wasn't seeing ANY access points and my wireless adapter appeared to be disabled, so I tried the instructions noted in this thread, but to no avail.

I did notice, however, that the dmesg output made a reference to needing something from here:
[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)

I installed the drivers recommended by the kernel.org instructions after running: "lspci -vnn | grep 14e4" (my PCI-ID is 14e4:4320).  After installing these and rebooting, things are mysteriously working just fine with WPA-Personal, and without needing to renice wpa_supplicant.

Perhaps what I'm mentioning is already obvious, but I thought I'd put it out there.

This thread is about ndiswrapper. You do not use ndiswrapper, you use a native driver and are therefore (luckily) not affected.

---

### Post by foxy123 on 2009-12-12
> **hellomoto said:**
> Update: I have got my WPA connections to work after reading this:

[http://ubuntuforums.org/showthread.php?t=1284891]("http://ubuntuforums.org/showthread.php?t=1284891")

So in short if you are using ndiswrapper with WPA connection and are unable to connect. Follow the above tutorial.


However if you are still unable to connect. Then try running the command below when trying to connect.

```
 sudo renice +19 $(pidof wpa_supplicant) 
```

worked for me on x2 computers.

using the patches and the command above I have finally managed to connect with WPA. I wonder if it is possible to make it automatic?

---

### Post by W. Irving on 2009-12-12
> **foxy123 said:**
> using the patches and the command above I have finally managed to connect with WPA. I wonder if it is possible to make it automatic?

Have a look at [http://manpages.ubuntu.com/manpages/karmic/en/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/karmic/en/man5/interfaces.5.html)
Adding a pre-up command (i.e. renice +19 $(pidof wpa_supplicant)) to your wifi interface might make it work automatically. I presume network manager does use /etc/network/interfaces....

---

### Post by foxy123 on 2009-12-12
> **W. Irving said:**
> Have a look at [http://manpages.ubuntu.com/manpages/karmic/en/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/karmic/en/man5/interfaces.5.html)
Adding a pre-up command (i.e. renice +19 $(pidof wpa_supplicant)) to your wifi interface might make it work automatically. I presume network manager does use /etc/network/interfaces....
I am not sure that NM uses /etc/network/interfaces

---

### Post by W. Irving on 2009-12-12
> **foxy123 said:**
> I am not sure that NM uses /etc/network/interfaces

Try it. Add "pre-up logger test", do /etc/init.d/networking restart and cycle the interface using network manager. Then tail /var/log/syslog and look for the test message.

---

### Post by foxy123 on 2009-12-12
> **W. Irving said:**
> Try it. Add "pre-up logger test", do /etc/init.d/networking restart and cycle the interface using network manager. Then tail /var/log/syslog and look for the test message.

no test message... 

I have found a few mentioning of editing functions.sh in wpa_suppliment (like [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=471905#30") , but it does not work either :(

---

### Post by W. Irving on 2009-12-12
> **foxy123 said:**
> no test message... 

I have found a few mentioning of editing functions.sh in wpa_suppliment (like [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=471905#30") , but it does not work either :(

Stick it in /etc/rc.local and make it executable. Should make it permanent, presuming wpa_supplicant is never restarted..

---

### Post by foxy123 on 2009-12-12
> **W. Irving said:**
> Stick it in /etc/rc.local and make it executable. Should make it permanent, presuming wpa_supplicant is never restarted..

thanks a lot, it worked. Unfortunately it takes a significant amount of time and often a few attempts to connect using ndiswrapper. So I am not going to make it may primary connection. I can always change it manually if I need more bandwidth. 

Overall the whole problem is strange. I tried a few other distributions and ndiswrapper works fine with the same driver and router using Slackware and Gentoo based distros. Even with Sidux, which is based on Debian Sid, it works fine.

---

### Post by W. Irving on 2009-12-13
> **foxy123 said:**
> Overall the whole problem is strange. I tried a few other distributions and ndiswrapper works fine with the same driver and router using Slackware and Gentoo based distros. Even with Sidux, which is based on Debian Sid, it works fine.

I suppose it's down to the differences in kernels used - versions and compile options. New kernel installed yesterday, perhaps time to give it another go, although the changelog doesn't look too inspiring.. [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.31-16.53/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.31-16.53/changelog)

---

### Post by sumadartson on 2009-12-19
Issuing the 
```
sudo renice +19 $(wpa_sup_pid)
```
command during a connection attempt worked for me to get the connection up and running. Kernel version 2.6.31.16, ndiswrapper 1.55 . Good hack, hurray for a working connection, but not exactly grandmother-proof...

---

### Post by Marcelo Ruiz on 2009-12-20
Thank you so much for this how to. It solved a problem that was driving me crazy!

---

### Post by sumadartson on 2009-12-20
> **sumadartson said:**
> Issuing the 
```
sudo renice +19 $(wpa_sup_pid)
```
command during a connection attempt worked for me to get the connection up and running. Kernel version 2.6.31.16, ndiswrapper 1.55 . Good hack, hurray for a working connection, but not exactly grandmother-proof...

To issue the renice command in one go:
```
sudo renice +19 $(ps axu | grep wpa_supplicant | head -1 | sed 's/root\s\+\([0-9]\{3,\}\).*/\1/g')
```

---

### Post by residualflash on 2009-12-31
Sorry to bump this thread, but is there any fix for this problem?

I'm new to Linux and this is a major problem for me :(

---

### Post by sonali11 on 2009-12-31
Thank you very much I have now successfully installed ndiswrapper1.55 , hurrrayy

---

### Post by brocie on 2010-01-09
I followed the instructions from the original post and that fix the "invalid cmd 12 error", but I still was unable to connect to my access point.

I also tried the following command, but was still unable to connect.
sudo renice +19 $(pidof wpa_supplicant)

After some searching I found another thread pointing to the kernel as the problem [http://ubuntuforums.org/showthread.php?t=1284891](http://ubuntuforums.org/showthread.php?t=1284891)

In short it was stating that kernel 2.6.31-10 was working and kernel 2.6.31-11 + was not. I thought that I would just downgrade to the older kernel, but I was unable to locate the headers for 2.6.31-10. I looked in the ubuntu repository to see was was available and found 2.6.32-10. This kernel isn't seen by the update manager, so I thought that I would try this newer kernel first.

I downloaded and installed the kernel and headers for 2.6.32-10 manually.

After installing 2.6.32-10 I rebooted and was connected to my wireless network without the need to renice. I have rebooted several times to make sure it wasn't a one off, so far so good.

I hope this helps those that are still having problems connecting.

---

### Post by foxy123 on 2010-01-10
> **W. Irving said:**
> Stick it in /etc/rc.local and make it executable. Should make it permanent, presuming wpa_supplicant is never restarted..

for some reason the command in /etc/rc.local stopped working :( I have now issue it manually.

---

### Post by srf21c on 2010-01-11
Installed ndiswrapper 1.55 w/both patches on a Karmic 9.10 system w/Belkin F5D8010 card but no change.  Still get the invalid command cmd 12 errors and no dice connecting to WEP encrypted networks either, even using the renice command.  2 hours of my life down the toilet trying to get Windows-centric hardware to work, why don't I ever learn.

---

### Post by IceCap on 2010-01-17
> **brocie said:**
> In short it was stating that kernel 2.6.31-10 was working and kernel 2.6.31-11 + was not. I thought that I would just downgrade to the older kernel, but I was unable to locate the headers for 2.6.31-10. I looked in the ubuntu repository to see was was available and found 2.6.32-10. This kernel isn't seen by the update manager, so I thought that I would try this newer kernel first.

I downloaded and installed the kernel and headers for 2.6.32-10 manually.

After installing 2.6.32-10 I rebooted and was connected to my wireless network without the need to renice. I have rebooted several times to make sure it wasn't a one off, so far so good.

I hope this helps those that are still having problems connecting.

Brocie,

  Where did you find the kernel and how did you install it?  I have the same problem and I'd like to try this method.  But I couldn't find the kernel anywhere.  This is on MythBuntu 9.10 so I'm hoping everything will work with the new kernel.

  Thanks

 IceCap

---

### Post by foxy123 on 2010-01-18
> **IceCap said:**
> Brocie,

  Where did you find the kernel and how did you install it?  I have the same problem and I'd like to try this method.  But I couldn't find the kernel anywhere.  This is on MythBuntu 9.10 so I'm hoping everything will work with the new kernel.

  Thanks

 IceCap

i guess you can find it _**[here]("http://security.ubuntu.com/ubuntu/pool/main/l/linux/")**_. If you are going to install it please let us know if it works for you.

---

### Post by brocie on 2010-01-20
> **IceCap said:**
> Brocie,

  Where did you find the kernel and how did you install it?  I have the same problem and I'd like to try this method.  But I couldn't find the kernel anywhere.  This is on MythBuntu 9.10 so I'm hoping everything will work with the new kernel.

  Thanks

 IceCap


Hi IceCap,

I did get the kernel from a Mythbuntu repository as I was having the problem on my mythbuntu box.

As far as I am aware there isn't shouldn't make any difference.

Any way these are the commands I ran.

wget [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-10-generic_2.6.32-10.14_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-10-generic_2.6.32-10.14_i386.deb)
wget [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-10-generic_2.6.32-10.14_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-10-generic_2.6.32-10.14_i386.deb)
wget [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-10_2.6.32-10.14_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-10_2.6.32-10.14_all.deb)

sudo dpkg -i linux-image-2.6.32-10-generic_2.6.32-10.14_i386.deb linux-headers-2.6.32-10-generic_2.6.32-10.14_i386.deb linux-headers-2.6.32-10_2.6.32-10.14_all.deb

Regards
Brocie

---

### Post by foxy123 on 2010-01-20
> **foxy123 said:**
> i guess you can find it _**[here]("http://security.ubuntu.com/ubuntu/pool/main/l/linux/")**_. If you are going to install it please let us know if it works for you.

I installed this kernel yesterday and had no problem connecting to my WPA protected network using ndiswrapper. I wonder if 2.6.32 kernel will make into backport repositories.

Thanks a lot brocie for the tip!

---

### Post by IceCap on 2010-01-26
OK here is what I did and my results.

  I was searching for the kernel (before I saw the replies here) and found these directions [here]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/").  Followed them (looks like this is not the same kernel as listed above).  Rebooted and it complained that ndiswrapper module wasn't loaded (so nothing worked) and I couldn't get it to work.
  Also, it looked to me that there was some error message in the startup (maybe lirc, its a Mythbuntu box) but I didn't check it out since I couldn't get ndiswrapper to work.

  I'll try Brocie's method right now (thanks for the info).

  Icecap

---

### Post by IceCap on 2010-01-26
Yes!  It works. Finally.

  Followed Brocie's directions here above, disconnected the ethernet cable, rebooted and got immediately connected with my wireless (TEW-643PI card from Trendnet using ndiswrapper and the drivers on the CD that came with the card).

  Given the nature of the original posts I'm wondering if someone should make a new post with a proper title to advertise this.  Given the number of posts here describing problems with wireless (most of them ndiswrapper) this is going to help a lot of people.  Making it a sticky would be even better.

  Well, anyway.  Thanks a lot Brocie, nice job.

  Icecap.

---

### Post by Benic on 2010-01-27
I had the same problem. I tried several things, including those posted in this thread, unsuccessfully.

I plugged the cable in, reinstalled ndiswrapper (1.54), the latest kernel (2.6.31-17), rebooted and now it's all working again. No more invalid cmd 12.

Maybe it will be of some help...

---

### Post by IceCap on 2010-01-28
I may have started celebrating a bit too early.  Although the wireless network now works every time, my PVR-350 remote does not work.  Looks like lirc is not compatible with the new kernel.  I haven't dug into it yet since I can just boot into the old kernel for the remote to work.

  Anyone have information about what might have caused this?

  IC

---

### Post by Schiaparelli on 2010-02-06
hey all - tried to find these files mentioned on the AU server but it appears that they have been moved. Got any other links to them? I could find the one (the 10.14_all one), but the other two seem to be awol. Could someone point me in the right direction?

---

### Post by bkratz on 2010-02-06
> **Schiaparelli said:**
> hey all - tried to find these files mentioned on the AU server but it appears that they have been moved. Got any other links to them? I could find the one (the 10.14_all one), but the other two seem to be awol. Could someone point me in the right direction?

I think I found them here please check about 1/2 way down

[https://launchpad.net/ubuntu/+archive/primary/+sourcepub/924073/+listing-archive-extra](https://launchpad.net/ubuntu/+archive/primary/+sourcepub/924073/+listing-archive-extra)

---

### Post by foxy123 on 2010-02-07
> **Schiaparelli said:**
> hey all - tried to find these files mentioned on the AU server but it appears that they have been moved. Got any other links to them? I could find the one (the 10.14_all one), but the other two seem to be awol. Could someone point me in the right direction?

you can also try version 2.6.32.12-17 from [http://security.ubuntu.com/ubuntu/pool/main/l/linux/](http://security.ubuntu.com/ubuntu/pool/main/l/linux/) It may work too.

---

### Post by Schiaparelli on 2010-02-10
many thanks bkratz..... downloaded and installed all of them.... still nothing. I spied a usb package a bit further down - so thought I might try install that too. although now with reboot the machine puts garbled stuff on the machine when I move the mouse and locks up after about a minute. so perhaps I did something wrong heh.... think I might have to reinstall....

---

### Post by noshi on 2010-02-24
I'm not sure how much this applies to others, but I ran into this problem when I installed a new router. I upgraded from an old Netgear-G to a Netgear-N wireless.  My connection seemed good at first but then failed and I ran into the same problems you guys have listed. I tried multiple solutions, short of uninstalling the Network Manager; I'm a Linux newbie.

Out of frustration, I plugged the old router in and was able to connect to its network with no trouble.

I haven't been able to find anything on the web that addresses this, though.  -- If any of this is applicable to you, what ideas do you have for handling it?

---

### Post by IceCap on 2010-02-24
The mainline kernels are here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

  Pick a kernel version and then use Brocie's directions in one of the previous posts.  Also note which mainline kernel is used as a basis in each Ubuntu kernel.  That conversion can be found here:

[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html]("http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html")

  Note that I found that using the 2.6.32-10 kernel that I installed, the ACPI (automatic wakeup) doesn't work (apparently a known bug).  So right now I boot into the latest Karmic kernel (now 2.6.31-19) in order for my Mythbuntu center waking up and recording and then I boot into the Lucid 2.6.32-10 kernel to get wireless working and get my listings data.

  Hope this helps

  IceCap

---

### Post by foxy123 on 2010-02-24
> **noshi said:**
> I'm not sure how much this applies to others, but I ran into this problem when I installed a new router. I upgraded from an old Netgear-G to a Netgear-N wireless.  My connection seemed good at first but then failed and I ran into the same problems you guys have listed. I tried multiple solutions, short of uninstalling the Network Manager; I'm a Linux newbie.

Out of frustration, I plugged the old router in and was able to connect to its network with no trouble.

I haven't been able to find anything on the web that addresses this, though.  -- If any of this is applicable to you, what ideas do you have for handling it?

It could be very well a some obscure router incompatibility problem. It is difficult to assess how many people are affected by this issue. Maybe not that many as this thread is not really overcrowded.

---

### Post by jp.hendrix on 2010-03-01
I think I have the same problem test driving Kubuntu 10.04 i686 (2.6.32-14) with a ndiswrappers powered USB wlan card. 

The strange thing is that I am perfectly able to connect to the wlan using the KDE network manager (KNetworkManager) in my system tray. The card connects every single time without any problem. It even properly connected before both patches described in this thread.

When trying to set up wpa_supplicant, to enable wlan at boot, it fails every single time.

Not sure where wpa_supplicant and KNetworkManager differ.

Hope this helps.

---

### Post by ampedforay on 2010-03-12
Thanks,
This got ndiswrapper installed correctly, which I was having major problems with.  
The only other thing I had to do was;
sudo update-initramfs -k all -u
and reboot.
This came from [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847).
Thanks again!

---

### Post by foxy123 on 2010-03-18
After a couple of months using the 2.26.32-10 kernel mentioned earlier in the thread I booted today into the current 2.26.31-20 and ndiswrapper seems to work fine. I wonder if the problem has been finally fixed or it is just I am being lucky. The thing is that it had happened to me before when ndiswrpper worked for me for a couple of time to stop connecting quickly. Can anyone confirm that ndiswrapper works with the current Karmic kernel? Also what about Lucid, has anyone tried it with ndiswrapper?

---

### Post by bkratz on 2010-03-18
> **foxy123 said:**
> After a couple of months using the 2.26.32-10 kernel mentioned earlier in the thread I booted today into the current 2.26.31-20 and ndiswrapper seems to work fine. I wonder if the problem has been finally fixed or it is just I am being lucky. The thing is that it had happened to me before when ndiswrpper worked for me for a couple of time to stop connecting quickly. Can anyone confirm that ndiswrapper works with the current Karmic kernel? Also what about Lucid, has anyone tried it with ndiswrapper?

Just out of curiosity I did try Lucid with ndiswrapper and it worked fine.  I did finally go back to 9.10 and upgraded the kernel to ...32-9 and built my own ndiswrapper version ( it is new ) 1.56 and got everything working on 9.10.

---

### Post by dgaud on 2010-05-13
Thanks a lot for this thread. I got my D-LINK USB adapter (2340) working by downloading the ndiswrapper-1.56.tar.gz file from SourceForge and compiling it as describe here (without the patch). First I uninstalled the default ubuntu version in 9.10 (1.54) and the NetworkManager gnome applet. Then got it working with Wicd and the WPA_SUPPLICANT driver set to WEXT.

strange thing is that ndiswrapper -v says is version 1.55 not 1.56?

Anyway 5 reboots so far and is still working... I'll keep my fingers crossed...

---

### Post by jarnett on 2010-06-11
Interesting...
Lucid
Trendnet N Router
3 laptops with a variety of wireless cards one of which uses ndiswrapper (All using Lucid)
Stuck using wep because a netgear router in repeater mode only supports wep.

I had the same problem of not connecting on the machine using wep and ndiswrapper. In my flailing about trying to troubleshoot the issue I noticed that the trendnet router required me to use a pass-phrase 14 char. long and lucid required me to use a pass phrase 13 char. long 
(128 bit encryption) 

Changed to 64 bit, problem solved.

---

### Post by nightdarkness on 2010-08-29
If someone gets the MUTEX function error on compiling -> create file named loader.c.diff in ndiswrapper-1.55/driver and paste ```
diff --git a/ubuntu/ndiswrapper/loader.c b/ubuntu/ndiswrapper/loader.c
index e1be090..5c231c7 100644
--- a/ubuntu/ndiswrapper/loader.c
+++ b/ubuntu/ndiswrapper/loader.c
@@ -847,7 +847,7 @@  int loader_init(void)
 
 	InitializeListHead(&wrap_drivers);
 	InitializeListHead(&wrap_devices);
-	init_MUTEX(&loader_mutex);
+	sema_init(&loader_mutex, 1);
 	init_completion(&loader_complete);
 	if ((err = misc_register(&wrapper_misc)) < 0 ) {
 		ERROR("couldn't register module (%d)", err);
```
and another file named wrapndis.c.diff including the following ```
diff --git a/ubuntu/ndiswrapper/wrapndis.c b/ubuntu/ndiswrapper/wrapndis.c
index 3de1fbd..404e1e3 100644
--- a/ubuntu/ndiswrapper/wrapndis.c
+++ b/ubuntu/ndiswrapper/wrapndis.c
@@ -2064,8 +2064,8 @@  static wstdcall NTSTATUS NdisAddDevice(struct driver_object *drv_obj,
 	}
 	nmb->next_device = IoAttachDeviceToDeviceStack(fdo, pdo);
 	spin_lock_init(&wnd->tx_ring_lock);
-	init_MUTEX(&wnd->tx_ring_mutex);
-	init_MUTEX(&wnd->ndis_req_mutex);
+	sema_init(&wnd->tx_ring_mutex, 1);
+	sema_init(&wnd->ndis_req_mutex, 1);
 	wnd->ndis_req_done = 0;
 	initialize_work(&wnd->tx_work, tx_worker, wnd);
 	wnd->tx_ring_start = 0;
```
After it, from ndiswrapper-1.55/driver do ```
 patch < loader.c.diff 
``` and ```
 patch < wrapndis.c.diff 
```.
Now you will be able to compile version 1.55

---

### Post by AmpersUK on 2011-06-17
I have looked through this thread and have come to two conclusions.

1. Ubuntu doesn't always work out of the box!

2. But if you do have problems, there are many who will go out of their way to help.

I long for the day when everything works out of the box so we can grow more into the mainstream, although we are doing well at the moment.

My 1015P which I think is superb has 11.04 on it, and the wifi connection to my Netgear works perfectly.

I came across this site looking to see if anyone had any problems with coming out of Hibernate, but as nobody has, I guess the problem is with my particular netbook.

Before I send it back, I will reload 11.04 again though. Just in case.

---

