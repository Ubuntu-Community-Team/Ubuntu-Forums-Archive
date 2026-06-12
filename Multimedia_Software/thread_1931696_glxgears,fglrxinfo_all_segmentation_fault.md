---
title: "glxgears,fglrxinfo all segmentation fault"
date: 2012-02-26
forum: Multimedia Software
---

### Post by sanatkrtiwari86 on 2012-02-26
Hi all, 
Though I use ubuntu linux for long time, first time I am facing this problem,
After some updates taken from apt ...  When I write 
```
$glxgears 
```
it gives error   "Segmentation fault"
```
$fglrxinfo
```
"Segmentation fault"
```
$glxinfo
name of display: :0.0
Segmentation fault
```

I tried to check, what went wrong, many times removed fglrx etc. totally...
```
$ sudo apt-get remove --purge fglrx 
```
similartly i remove others like "xserver-xorg-video-ati" and "xserver-xorg-video-radeon" 
When I remove them and
```
$glxgears
```
It gives.............
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

again installed all of them fresh, but nothing happened.
Some other details what I think relevant are:
My ubuntu is:
Linux GHD 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:50:08 UTC 2012 x86_64 GNU/Linux
The result of command
```
lspci -nn | grep VGA
```
is
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
```
I don't want proprietary software, just want my old congiuration back what was fine.
How can I do a clean reinstall, after removing all such graphic drivers if this is solution?
The command
```
find /usr/lib -name libGL.so.1 -exec ls -al {} \; 
```
gives
```
lrwxrwxrwx 1 root root 12 2012-02-26 11:33 /usr/lib/mesa/libGL.so.1 -> libGL.so.1.2
lrwxrwxrwx 1 root root 8 2012-02-26 11:33 /usr/lib/libGL.so.1 -> libGL.so
lrwxrwxrwx 1 root root 12 2012-02-26 11:33 /usr/lib/fglrx/libGL.so.1 -> libGL.so.1.2

```

---

### Post by Yellow Pasque on 2012-02-26
Purge fglrx and do not install it again. You should not have fglrx installed for an intel GPU. Then, reinstall the proper versions of libGL and libglx:
```
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx
```
You will need to restart (at least X) for change to take effect.

---

### Post by sanatkrtiwari86 on 2012-02-28
Thanks a lot :)
problem solved exactly following your suggestions.

---

