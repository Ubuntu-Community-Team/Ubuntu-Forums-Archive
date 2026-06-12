---
title: "Realtek R8168/8169 problem"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by Ulrich74 on 2012-08-15
Hi altogether,

I hope, someone can help me with my problem with Realtek network card and my Ubuntu Server 12.04.
I know the problem with the WOL, and I managed to install the Realtek r8168 driver successfully. WOL works and everything is fine.
But, I have enabled the automatically security updates for the server (in the night), and sometimes, the next day, the server doesn't work anymore, because he is not connected to the network anymore (so no ssh connection)
If I look at the console, I register, that the old r8169 driver is again loaded, so i must reinstall the r8168 driver again, then it works.
I think, that this happens every time, some kernel-"updates" or something like this causes a "reset" and the original kernel driver is loaded again.
I blacklisted the driver, but this does not work.

The problem is, that this is a real servre, so no keyboard or display, only network cable is connected. So, to install the driver everytimes, I have to unplug the server from server-bay, go to my workstation, connect keyboard and display and so on.

Now my question: How can I disable the loading of the old r8169 network driver completely, even if some kernel-security update is installed and avoid the loading of the kernel-r8169-driver?

Thank you very much for any help.
Bye,
Ulrich

---

### Post by chili555 on 2012-08-15
> I think, that this happens every time, some kernel-"updates" or something like this causes a "reset" and the original kernel driver is loaded again.
I blacklisted the driver, but this does not work.Whenever you  compile a driver from source code, you compile it against the running kernel _only_. When an updated kernel is installed by Update Manager and the machine is rebooted into the new kernel, the compiled driver no longer exists.

Why doesn't the blacklist work? May we see:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```If it were me, I'd turn off automatic updates altogether and update periodically by hand from your workstation. In fact, I'd probably remove Update Manager altogether and use apt-get.

How is it set to reboot automatically?? Even if the blacklist was working correctly, it doesn't seem very helpful for the server to update, reboot and go off-line unexpectedly.

---

### Post by Ulrich74 on 2012-08-15
> **chili555 said:**
> Whenever you  compile a driver from source code, you compile it against the running kernel _only_.  When an updated kernel is installed by Update Manager and the machine  is rebooted into the new kernel, the compiled driver no longer exists.

Thank you very much for your response, this sounds comprehensible.

> **chili555 said:**
> 
Why doesn't the blacklist work? May we see: cat /etc/modprobe.d/blacklist.conf | tail -n5


Here is the end of the blacklist-file:
```

# old RealTek network driver
blacklist r8169

# deactivate bluetooth
blacklist btusb

```> **chili555 said:**
> 
If it were me, I'd turn off automatic updates altogether and update periodically by hand from your workstation

I use only apt-get (I think I have no Update Manager, I use the server without any GUI), the automatically updates comes via cron-job, I configured 
/etc/apt/apt.conf.d/50unattended-upgrades, so that nothing is updated, and also changed /etc/apt/apt.conf.d/20auto-upgrades in this way, that "unattended-Upgrade is 0" (I think, this was responsible for the kernel update last night to 3.2.0-29-generic... and I saw, that I now have Ubuntu Server 12.04_**.1**_)

Because the server does not have any display (I totally rely on ssh), would it be possible to install the network-driver right after the kernel-update, if I use "apt-get"? I think then my problem is solved (if I could disable the automatic updates), so that I don't need to plug the server of and carry it to other rooms and plug display and keyboard to it and back again.

Thanks again and bye,
Ulrich

---

### Post by chili555 on 2012-08-15
> # old RealTek network driver
blacklist r8169That looks perfect and I don't understand how it could *not* work. I assume there is no contravening lines in /etc/rc.local or /etc/modules.>  would it be possible to install the network-driver right after the kernel-update, if I use "apt-get"? I think then my problem is solvedIt would depend on whether the 8168 code allows compiling for a different kernel than the running kernel. In other words, if you've done an update that installs 3.2.0-**30**-generic and you are still running in -29, can we compile the driver against -30 so that when you reboot, it's there. We might just examine the Makefile to see about that.

Of course, since a server is rebooted very infrequently, you could make up some kind of script to run on *every* boot; something very roughly like:```
cd Realtek/8168file
make clean
make
make install
modprobe r8168
service networking restart
ifdown eth0 && ifup eth0
```

---

### Post by Ulrich74 on 2012-08-15
> **chili555 said:**
>  I assume there is no contravening lines in /etc/rc.local or /etc/modules.


/etc/rc.local just contains "exit(0)"
/etc/modules contains:
```

loop
lp
rtc
r8168

```


The tip for always compiling and building and installing the driver after every reboot sounds very interesting. I will try that.

Thanks and bye,
Ulrich

---

### Post by chili555 on 2012-08-15
> /etc/modules contains:
```
loop
lp
rtc
r8168
```It all looks perfect. If r8169 continues to load, you could add to your script:```
rm /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8169.ko
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by Ulrich74 on 2012-08-15
Thanks for the help, I mark  the thread "solved"

---

