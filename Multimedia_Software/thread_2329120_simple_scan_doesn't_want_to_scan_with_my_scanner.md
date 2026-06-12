---
title: "simple scan doesn't want to scan with my scanner"
date: 2016-06-28
forum: Multimedia Software
---

### Post by ardouronerous on 2016-06-28
My scanner is a Canon LIDE 110 and I'm running Xubuntu 16.04.

Simple Scan is giving me a "unable to scan" error and sometimes crashes.

I ran lsusb on the terminal;

```
~$ lsusb
Bus 001 Device 006: ID 04a9:1909 Canon, Inc. CanoScan LiDE 110
```

So my scanner is detected.

My scanner works on Virtualbox running Windows XP though, and I'm currently using that to scan.

---

### Post by ardouronerous on 2016-07-01
Anyone?

I've tried Xsane and gscan2pdf, but both gave a 'Error during device I/O'.

---

### Post by fdrake on 2016-07-01
did you check this  first? [http://ubuntuforums.org/showthread.php?t=1595801](http://ubuntuforums.org/showthread.php?t=1595801)

---

### Post by ardouronerous on 2016-07-01
Thanks for the reply.
So I have to add a PPA to get my scanner to work?

In Xubuntu 14.04, my scanner worked out of the box without any additional procedures, but in 16.04, it's not working.

---

### Post by X-RED_Tech on 2016-07-01
No, that PPA is no longer available and it's highly unlikely you would need solutions from 6 years ago, especially considering it was working in the previous LTS.
Do you remember installing something for the scanner before (14.04)?

---

### Post by ardouronerous on 2016-07-01
No, the scanner worked out of the box in Xubuntu 14.04, even in 12.04, didn't need to install anything else.

---

### Post by ardouronerous on 2016-07-02
I'm currently testing my scanner on Live CD sessions of both Xubuntu 14.04 and 16.04 on VirtualBox, let's see what happens, I'll be posting the results here after I'm done.

CanoScan LiDE 110 works on Xubuntu 14.04 Live CD session, but doesn't work on 16.04 Live CD session. There is clearly a bug.

---

### Post by ardouronerous on 2016-07-04
How do I report this bug? I have a launchpad account, but I'm not sure on how to do that.

---

### Post by Kenzo on 2016-08-19
Has this been fixed?  If so could you post the link please?
Thanks

---

### Post by ibod on 2016-10-06
Plus 1 for this fix as I have the same problem Canon Lide 110 working in 14.04 but not in 16.04 (32bit)

Thanks

---

