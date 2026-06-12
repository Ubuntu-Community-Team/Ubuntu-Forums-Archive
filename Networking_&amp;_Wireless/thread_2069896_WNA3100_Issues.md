---
title: "WNA3100 Issues"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by chief30 on 2012-10-11
Hi, I have read the stickies and have searched the forum and tried a few methods as to getting this wireless card to work.  I have had no luck.

I have 12.04 64 bit installed.

If anyone would have enough patience to help me through this, I would really appreciate it since I know it has been asked multiple times.

Thank you.

---

### Post by dark2099 on 2012-10-28
Used the attached drivers myself.  Extract them where ever, then in terminal navigate to that folder and follow the codes below.

```
sudo ndiswrapper -i <DRIVERNAME>.inf
```

This will install the driver.

```
ndiswrapper -l
```

This will list the drivers installed and related hardware, should get an out put that looks like:

```
Installed ndis drivers:
{name of driver} driver present, hardware present
```

or

```
{name of driver} : driver installed
device ({Chipset ID}) present
```

If you see one of those messages, the driver should be successfully installed.  Now load the driver module using:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

From there you should be able to connect, use the icon in the upper right hand corner.

---

