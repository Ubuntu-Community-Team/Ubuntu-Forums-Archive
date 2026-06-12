---
title: "Netgear N300 driver no wlan on Precise 12.04"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by AliBrown on 2012-05-07
Hi,
I have been searching forums and trying various solutions for days, but I am still having no luck - hopefully someone can help me!

I have 12.04 server edition with the gnome gui and webmin.  I am currently connected to the internet using ethernet.  I have a Netgear wireless USB adapter (WNDA3100) which I understand uses the Broadcom 43xx driver.

I have used ndiswrapper to install the driver and I can see both the driver and hardware.

```
ali@BrownServer:/$ ndiswrapper -l
bcmn43xx32 : driver installed
	device (0846:9011) present

```

```
ali@BrownServer:/$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]**Bus 001 Device 010: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]**[/COLOR]
Bus 002 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 006: ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD

```

```
ali@BrownServer:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Can anyone point me in the right direction?

---

### Post by chili555 on 2012-05-07
Are there any interesting messages here?```
dmesg | grep ndis
```

---

### Post by AliBrown on 2012-05-08
Yes, it appears there is some interesting stuff!

```
ali@BrownServer:~$ dmesg | grep ndis
[   15.042858] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   16.383200] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   16.383225] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmn43xx32'
[   16.383464] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmn43xx32'
[   16.383634] usbcore: registered new interface driver ndiswrapper
[  661.207001] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  661.207015] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmn43xx32'
[  661.207209] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmn43xx32'
[ 1524.931647] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1524.931661] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmn43xx32'
[ 1524.931867] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmn43xx32'
[ 3086.404408] usbcore: deregistering interface driver ndiswrapper
```

Have tried both 32 bit and 63 bit drivers, but I think the 64 bit version might have been a bit funny in the download.

Hmmmm.  Any thoughts on next steps?

---

### Post by chili555 on 2012-05-08
> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BYou might uninstall it:> sudo ndiswrapper -e bcmn43xx32And then try the 64-bit .inf file here.

You might also read post #14 here: [http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2](http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2)

Also post #28 here: [http://ubuntuforums.org/showthread.php?t=1946875&page=3](http://ubuntuforums.org/showthread.php?t=1946875&page=3)

bcmn43xx32 and -64 are slight variations of bcmwlhigh5.inf.

---

### Post by AliBrown on 2012-05-08
Ok, that didn't work.
```
ali@BrownServer:~$ ndiswrapper -l
bcmn43xx64 : invalid driver!
```

I gather from your other threads that you haven't really come across a solution for this yourself.  I take it I can't use the 32bit driver on my 64bit server install either?

Hmmm. Guess I'm stuck with ethernet for the time being.

---

### Post by chili555 on 2012-05-08
> I take it I can't use the 32bit driver on my 64bit server install either?No.> I gather from your other threads that you haven't really come across a solution for this yourself. Not for 64-bit. I can get a 32-bit PAE kernel to work just fine.

---

