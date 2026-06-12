---
title: "NDISwrapper + win drivers"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by tp-owner on 2009-04-07
OK sorry I have read LOADS of posts to do with this but no luck...

I have a ZOOM wireless dongle 4410B which I have read is supported however all the links to the list DO NOT WORK so I can't check. 

I have found some windows drivers for it off a disc and I have found 2 .sys files. I have also downloaded the ndiswrapper file which is a .tar.gz which I extracted out to a file.

When I try multiple lines in the terminal it just says can't find Package :( I need help lol

(Note: I am on a thinkpad 600e which is running Ubuntu 8.10)

---

### Post by Ayuthia on 2009-04-07
> **tp-owner said:**
> OK sorry I have read LOADS of posts to do with this but no luck...

I have a ZOOM wireless dongle 4410B which I have read is supported however all the links to the list DO NOT WORK so I can't check. 

I have found some windows drivers for it off a disc and I have found 2 .sys files. I have also downloaded the ndiswrapper file which is a .tar.gz which I extracted out to a file.

When I try multiple lines in the terminal it just says can't find Package :( I need help lol

(Note: I am on a thinkpad 600e which is running Ubuntu 8.10)

You might first try using the liveCD to install ndiswrapper:
```
sudo apt-cdrom add
```Add the liveCD when requested.  Next:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

If you don't have the liveCD, you can try installing ndiswrapper by using the tar.gz file you downloaded.  You need to go to the directory where you downloaded the ndiswrapper*.tar.gz file.  You can then do the following:
```
tar -xvf ndiswrapper*.tar.gz
cd ndiswrapper*
make
```If there are no errors:
```
sudo make install
```and it should be installed.

If you do run into any error messages, just come back and let us know what the error message is displaying.

---

### Post by tp-owner on 2009-04-07
Thanks for that... I had the live CD and I now have the ndiswrapper installed. I will need to get this sys file installed now or something :S

Could you help me on what to put...

Ok I do not have an inf file :P do you have an upto date link?

---

### Post by tp-owner on 2009-04-07
**I have now got that installed using:**

```
sudo ndiswrapper -i [filename].inf
```

I can't get interent and I cant seem to find and sort of indication that its worked...

---

### Post by Ayuthia on 2009-04-07
In the Terminal try:
```
ndiswrapper -l
```
This will check and see if the driver is present.  If this looks ok, you can then check to see if the ndiswrapper module is loaded:
```
lsmod|grep ndiswrapper
```It it returns some information with ndiswrapper in it, then it is loaded.

Next you can check:
```
lshw -C network
```This will help us see if ndiswrapper is being used for your wireless card.

If all those things look right, you can also check:
```
dmesg|grep ndiswrapper
```This will help see if any error messages show up when it tries to use ndiswrapper.

---

### Post by tp-owner on 2009-04-07
When I tried:
```
lshw -C network
```

I got:
```
description: ethernet interface
Physical ID: 2
Logical name: Pan0
serial: 52:a0:17:91:70:d0
Capabilities: ethernet physical
configuration: Broadcast=yes driver=bridge diversion=2.3 firmware=N/A link=yes multicast=yes
```

Then I tried:
```
dmesg|grep ndiswrapper
```

From this I got a big page however 3 lines were of interest:
```
(load_sys_files:206): Couldn't prepare driver 'drivername'
(Load_wrap_driver:108):couldn't load driver 'drivername'; check system log for messsages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper
```

None of this makes sense to me... Thanks for the previous help as well :D

---

