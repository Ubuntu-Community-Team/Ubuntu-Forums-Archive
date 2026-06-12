---
title: "wrt54g, wireless netbook cant ssh."
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by eppo on 2009-01-03
i just got a hp mini. i have it connected via wireless to a wrt54g router. i'm basically just using the router for the wireless and as a switch. my current network is a ubunutu server which acts as my gateway server. its connected to a switch which is connected to my other computers. so what i did with the wrt54g is connect one of the ethernet ports to my current switch. the wireless part works fine, i can get on the internet, connect to my internal webserver, even see my samba shares and connect to em. but for some reason when i try to  ssh to my server, it will connect, ask me for my password, and then just hang. you cant even control-c to stop it. if you type in a wrong password it will tell you it is wrong and have you type it again. if i check the logs on my server it opens the connection. same thing happens if i try to ssh to my netbook from a computer in my home network.
anyone know how i can fix this problem? it is my belief that the wireless is on the same network as the ethernet ports on the router, which would require no routing.
please help me out.
thanks

---

### Post by Ayuthia on 2009-01-03
> **eppo said:**
> i just got a hp mini. i have it connected via wireless to a wrt54g router. i'm basically just using the router for the wireless and as a switch. my current network is a ubunutu server which acts as my gateway server. its connected to a switch which is connected to my other computers. so what i did with the wrt54g is connect one of the ethernet ports to my current switch. the wireless part works fine, i can get on the internet, connect to my internal webserver, even see my samba shares and connect to em. but for some reason when i try to  ssh to my server, it will connect, ask me for my password, and then just hang. you cant even control-c to stop it. if you type in a wrong password it will tell you it is wrong and have you type it again. if i check the logs on my server it opens the connection. same thing happens if i try to ssh to my netbook from a computer in my home network.
anyone know how i can fix this problem? it is my belief that the wireless is on the same network as the ethernet ports on the router, which would require no routing.
please help me out.
thanks

Which kernel version of Ubuntu are you using?  You can find out by going into the Terminal and typing:
```
uname -a
```
It sounds like you are using an early version of Hardy where ssh does not work.  The updated version should work better if you are using Hardy.  The original module for the wireless card did not work with ssh, but the updated version should.

---

### Post by eppo on 2009-01-03
2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux
is there a repository i need to use to upgrade the kernel?

---

### Post by Ayuthia on 2009-01-03
Have you tried updating within Synaptic or the Terminal?  If you do it from the Terminal:
```
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by eppo on 2009-01-03
yes, it is up to date with the repositories i have now. i'm running the netbook remix version of ubuntu, can i use the ppa kernel?

edit: how do i find out what the most up to date kernel is out there for -lpia ?

---

### Post by Ayuthia on 2009-01-03
I forgot about the netbooks.  You might try using the drivers that Broadcom just released.  You will need to compile them:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by eppo on 2009-01-03
was thinking about upgrading to 8.10, looks like i cant do it the same way as it is done with the desktop version. when i do do-dist-upgrade it cant find any new releases. i might just try installing that version on here.
unless i can just upgrade.

---

### Post by Ayuthia on 2009-01-03
I am not for sure about how easy it is to upgrade to 8.10 with a netbook.  You might try compiling the wireless module first.  The instructions at the site are pretty decent.  I am not 100% sure if it will compile with 2.6.24 kernels yet though.  I plan to test that out within the next few days.  It does pass with 2.6.28.

---

### Post by eppo on 2009-01-03
did you compile it using the readme file on that page? when i get to the make step, first of all there is no /lib/modules/2.6.24-19-lpia/build directory. so i created it, but when i do the make command, i get:
make: Entering directory `/lib/modules/2.6.24-19-lpia/build'
make: *** No targets specified and no makefile found.  Stop.
make: Leaving directory `/lib/modules/2.6.24-19-lpia/build'
what file is it looking for in there?
any help would be great
thanks

---

### Post by Ayuthia on 2009-01-03
> **eppo said:**
> did you compile it using the readme file on that page? when i get to the make step, first of all there is no /lib/modules/2.6.24-19-lpia/build directory. so i created it, but when i do the make command, i get:
make: Entering directory `/lib/modules/2.6.24-19-lpia/build'
make: *** No targets specified and no makefile found.  Stop.
make: Leaving directory `/lib/modules/2.6.24-19-lpia/build'
what file is it looking for in there?
any help would be great
thanks

It looks like you might be missing the linux-headers.  Can you do the following search:
```
aptitude search 2.6.24-19-lpia
aptitude search build-essential
```There should be package called linux-headers.  Make sure that is installed for your kernel version (2.6.24-19-lpia).  I am not for sure if build-essential is installed or not, but that might be needed for compiling also.

---

### Post by Catalyst2Death on 2009-01-03
it would also be useful to post the result of:

```
ssh -vvv (username)@(server)
```

This will tell us exactly where ssh is hanging...

---

### Post by eppo on 2009-01-04
looks like the updated driver did the trick. but how do i make it permanent?
after i got it compiled, i did:
rmmod wl
modprobe ieee80211_crypt_tkip
and while in the dir that i compiled the driver i do, sudo insmod wl.ko
this will load the .12 version of driver. the one currently loaded is .9
if i reboot, it will reload the .9 version.
what do i have to do to make it permanent?
thanks

---

### Post by Ayuthia on 2009-01-04
> **eppo said:**
> looks like the updated driver did the trick. but how do i make it permanent?
after i got it compiled, i did:
rmmod wl
modprobe ieee80211_crypt_tkip
and while in the dir that i compiled the driver i do, sudo insmod wl.ko
this will load the .12 version of driver. the one currently loaded is .9
if i reboot, it will reload the .9 version.
what do i have to do to make it permanent?
thanks

The easy way would be to replace the driver in /lib/modules then run depmod -a to update the dependencies.  The wl.ko file from Ubuntu is found in /lib/modules/`uname -r`/volatile.  I would make a backup copy of the Ubuntu one before copying it over with the new one.  So if the new wl.ko file is on your desktop:
```
cd ~/Desktop
cp /lib/modules/2.6.24-19-lpia/volatile/wl.ko wl.ko.backup
sudo cp wl.ko /lib/modules/2.6.24-19-lpia/volatile
sudo depmod -a

```

---

