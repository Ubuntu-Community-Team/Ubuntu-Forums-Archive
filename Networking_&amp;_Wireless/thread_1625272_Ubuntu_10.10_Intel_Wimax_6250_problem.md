---
title: "Ubuntu 10.10 Intel Wimax 6250 problem"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by faal on 2010-11-18
Hi,

I have an Intel Wimax 6250 and fresh Ubuntu 10.10 install. The wireless card works, however during startup I get an annoying message:

dmesg | grep 6050
[   16.118240] i2400m_usb 2-1.5:1.0: fw i6050-fw-usb-1.5.sbcf: cannot load file: -2

Anyone have this message and know how to get rid of it?

I think the file is supposed to exist in /lib/firmware/i6050-fw-usb-1.5.sbcf but it doesn't.

---

### Post by chili555 on 2010-11-19
Please see here:

[http://ubuntuforums.org/showthread.php?t=1508183](http://ubuntuforums.org/showthread.php?t=1508183)

---

### Post by faal on 2010-11-23
Thank you for your reply.

However, I don't think they are the same files? At least they don't have the same name.

The one I get an error about is:

i6050-fw-usb-1.5.sbcf

while the file mentioned in that thread is:

iwlwifi-6050-4.ucode

or are they actually the same file with different names?

---

### Post by chili555 on 2010-11-23
Oops! You are right. See if the attached helps.

---

### Post by faal on 2010-11-27
I guess it was supposed to be an empty file? Anyway, it solved the problem!

i2400m_usb 2-1.5:1.0: WiMAX interface wmx0 (00:1d:e1:37:aa:d9) ready

Thanks a lot!

I still get the message though during startup and not the ubuntu logo... Not a major issue but a little annoying.

---

### Post by chili555 on 2010-11-27
> I guess it was supposed to be an empty file? It's 140 bytes zipped. It may be slender, but it's not empty. I'm glad your Wimax is working.

---

### Post by faal on 2010-11-27
Ops, my bad.. Seems there still a problem. I get:

i2400m_usb 2-1.5:1.0: WiMAX interface wmx0 (00:1d:e1:37:aa:d9) ready

but further down it still complains

[   77.069348] i2400m_usb 2-1.5:1.0: fw i6050-fw-usb-1.5.sbcf: cannot load file: -2
[   77.069416] i2400m_usb 2-1.5:1.0: Could not find a usable firmware image
[   77.069482] i2400m_usb 2-1.5:1.0: cannot bootstrap device: -2
[   77.390239] i2400m_usb 2-1.5:1.0: cannot setup device: -2
[   77.390305] i2400m_usb: probe of 2-1.5:1.0 failed with error -2
[   77.390339] usbcore: registered new interface driver i2400m_usb

The zip file file is 140 bytes, but the extracted file is 0 bytes:

ls -l i6050-fw-usb-1.5.sbcf*
-rw-r--r-- 1 fabian fabian   0 2010-11-23 15:56 i6050-fw-usb-1.5.sbcf
-rw-r--r-- 1 fabian fabian 140 2010-11-27 15:29 i6050-fw-usb-1.5.sbcf.zip

---

### Post by chili555 on 2010-11-27
Well, I am not sure what happened. Please click here: [http://linuxwimax.org/Download?action=AttachFile&do=get&target=i2400m-fw-1.5.0.tar.bz2](http://linuxwimax.org/Download?action=AttachFile&do=get&target=i2400m-fw-1.5.0.tar.bz2)

Right-click the file and select 'Extract here.' Drop the two .sbcf files into /lib/firmware and give the files the correct ownership and permission:```
sudo chown root:root /lib/firmware/*.sbcf
sudo chmod 644 /lib/firmware/*.sbcf
```Unload and reload the driver module:```
sudo rmmod -f i2400m-usb
sudo modprobe i2400m-usb
```Check dmesg to see if the driver and the firmware fell in love and got married:```
dmesg | grep 2400
```

---

### Post by faal on 2010-11-27
i2400m_usb 2-1.5:1.0: WiMAX interface wmx0 (00:1d:e1:37:aa:d9) ready

Thanks a lot! No more errors. :-)

---

### Post by b16a2smith on 2011-01-05
Well if anyone can help, i can get any of this to work, I am willing to kick $20 to whoever helps me get this going so I can completely remove windows thanks, 

please send an email to b16a2smith @ gmail.com

Thanks to all who can help.

---

### Post by phoenixcor on 2011-01-05
I will chip in another 20 via paypal. i know just enough to really jam things up.  little help please

i got this going on

```
 laptop:~$ dmesg | grep 2400
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u524288
[    0.000000]   #41 [0002400000 - 000240e000]         BOOTMEM
[   17.112501] i2400m_usb 2-1.5:1.0: WiMAX interface wmx0 (00:1d:e1:38:dc:e2) ready
[   17.194839] i2400m_usb 2-1.5:1.0: fw i6050-fw-usb-1.5.sbcf: cannot load file: -2
[   17.194912] i2400m_usb 2-1.5:1.0: Could not find a usable firmware image
[   17.194977] i2400m_usb 2-1.5:1.0: cannot bootstrap device: -2
[   17.361475] i2400m_usb 2-1.5:1.0: cannot setup device: -2
[   17.361565] i2400m_usb: probe of 2-1.5:1.0 failed with error -2
[   17.361615] usbcore: registered new interface driver i2400m_usb
[  502.937944] usbcore: deregistering interface driver i2400m_usb
[  515.760340] i2400m_usb 2-1.5:1.0: WiMAX interface wmx0 (00:1d:e1:38:dc:e2) ready
[  515.764428] i2400m_usb 2-1.5:1.0: fw i6050-fw-usb-1.5.sbcf: cannot load file: -2
[  515.764442] i2400m_usb 2-1.5:1.0: Could not find a usable firmware image
[  515.764453] i2400m_usb 2-1.5:1.0: cannot bootstrap device: -2
[  515.787562] i2400m_usb 2-1.5:1.0: cannot setup device: -2
[  515.787592] i2400m_usb: probe of 2-1.5:1.0 failed with error -2
[  515.787648] usbcore: registered new interface driver i2400m_usb
```

---

### Post by faal on 2011-01-07
This should work:

1. Download [http://linuxwimax.org/Download?action=AttachFile&do=get&target=i2400m-fw-1.5.0.tar.bz2](http://linuxwimax.org/Download?action=AttachFile&do=get&target=i2400m-fw-1.5.0.tar.bz2)

2. Extract the two sbcf files into /lib/firmware/ using archive manager.

3. Start the terminal and run 
```
sudo chown root:root /lib/firmware/*.sbcf
```
```
sudo chmod 644 /lib/firmware/*.sbcf
```4. Restart.

5. Check output of ```
dmesg | grep 2400
``` it should be something like:

[   21.478041] i2400m_usb 2-1.5:1.0: WiMAX interface wmx0 (00:1d:e1:37:aa:d9) ready
[   24.948903] i2400m_usb 2-1.5:1.0: firmware interface version 9.3.2
[   24.956475] usbcore: registered new interface driver i2400m_usb

---

### Post by phoenixcor on 2011-01-13
Thanks faal! you rock, everything shows up now. Now to get connected.  when I run:

>  wimaxd -i wmx0 then  

> wimaxcu scani get the following

ERROR: You do not possess sufficient privileges to perform this action. 

I think I am just having trouble firing the wimax up... just a guess

---

### Post by faal on 2011-01-14
> **phoenixcor said:**
> Thanks faal! you rock, everything shows up now. Now to get connected.  when I run:

then  

i get the following

ERROR: You do not possess sufficient privileges to perform this action. 

I think I am just having trouble firing the wimax up... just a guess

Try

```
sudo wimaxd -i wmx0
```and

```
sudo wimaxcu scan
```If you type *sudo* infront of a command you will run it as superuser.

---

### Post by phoenixcor on 2011-01-17
error message 

Make sure wimax network service is running.  

someone on the boards made mention of a hardware switch,  when i right click network manager, it shows wimax enabled, but disconnected when i left click.  is the radio just not on? also ran rfkill and the wimax is not blocked

Thanks faal!

---

### Post by ericwwheeler on 2011-01-25
> **faal said:**
> Try

```
sudo wimaxd -i wmx0
```and

```
sudo wimaxcu scan
```If you type *sudo* infront of a command you will run it as superuser.

I am also trying to use the wimax side of the 6250.
1. what I did was disable wireless in Network Manager
2. ran code: 'sudo wimaxd -i wmx0' it returned: 'sudo: wimaxd: command not found'

Any ideas on where to go from here? I
 have rpms for the wimax, wimax-tools, wimax-lib, etc. but found Fedora forums to be not nearly as helpful as Ubuntu so I switched back to 10.10 on my Dell mini 1012 with Intel 6250. Can I use the alien package to change the rpms into debs and install them?

---

