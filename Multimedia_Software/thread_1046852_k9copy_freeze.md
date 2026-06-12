---
title: "k9copy freeze?"
date: 2009-01-21
forum: Multimedia Software
---

### Post by nixie21 on 2009-01-21
Trying to use k9copy in ubuntu 8.10, as soon as I click open dvd k9copy freezes and I have to kill the process??? Any ideas??

Thanks

---

### Post by mexiswede on 2009-01-23
I'm having the same issue in Ubuntu 8.10 and k9copy version 2.0.2.

---

### Post by vividia on 2009-01-24
I've got the same issue.  It is quite widespread.  Supposedly there is a bug involving k9copy 2.0.*.   Version 2.1.0 is supposed to resolve this issue but I'm stuck with tarball that won't install.  Isn't there an easier way to install this using apt-get?

---

### Post by vividia on 2009-01-24
Just passing this along.  I found a place with a .deb.  I didn't realize I was using a KDE4 version of k9copy.  I had both with Hardy.

Link: [http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy)

After doing this, remember to do the medibuntu updates.

---

### Post by nixie21 on 2009-01-24
ok, installed the newer version,,,now i get (when I click open) any ideas?

A Fatal Error Occurred
The application k9copy (k9copy) crashed and caused the signal 6 (SIGABRT).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc.

Application: k9copy (k9copy), signal SIGABRT
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb5eed920 (LWP 18343)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0xb80d8430 in __kernel_vsyscall ()
#6  0xb66a1880 in raise () from /lib/tls/i686/cmov/libc.so.6
#7  0xb66a3248 in abort () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7355795 in qt_message_output () from /usr/lib/libQtCore.so.4
#9  0xb7355872 in qFatal () from /usr/lib/libQtCore.so.4
#10 0xb73558cc in qt_assert_x () from /usr/lib/libQtCore.so.4
#11 0x080fd38c in ?? ()
#12 0x080b8230 in _start ()
#0  0xb80d8430 in __kernel_vsyscall ()

---

### Post by vividia on 2009-01-25
It will crash and register a signal 6 response until the proper libs and codecs have been installed.  Go to medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/)) and follow the repository how to marked at the top of the page. 

Or just enter this in your terminal:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Once thats done, you can enable the mulitverse and Universe repositories by putting this in:

sudo sed -i -e &#8220;s/# deb/deb/g&#8221; /etc/apt/sources.list && sudo apt-get update

Then install the libdvdcss2.

sudo apt-get install libdvdcss2

if you haven't done the w32codecs (or 64), do them while you're at it.

sudo apt-get install w32codecs (substitute 64 for 32 if you need to)

After doing all that, I found it helps to reboot.  This will hopefully solve the signal 6 problem.

Good Luck!

---

### Post by nixie21 on 2009-01-25
> **vividia said:**
> It will crash and register a signal 6 response until the proper libs and codecs have been installed.  Go to medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/)) and follow the repository how to marked at the top of the page. 

Or just enter this in your terminal:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Once thats done, you can enable the mulitverse and Universe repositories by putting this in:

sudo sed -i -e “s/# deb/deb/g” /etc/apt/sources.list && sudo apt-get update

Then install the libdvdcss2.

sudo apt-get install libdvdcss2

if you haven't done the w32codecs (or 64), do them while you're at it.

sudo apt-get install w32codecs (substitute 64 for 32 if you need to)

After doing all that, I found it helps to reboot.  This will hopefully solve the signal 6 problem.

Good Luck!

THANKS...ALl good now....

---

### Post by vividia on 2009-01-25
Glad to be of help!  :D

---

### Post by mexiswede on 2009-01-25
Looks like the 2.1 version works for me, as well. Thanks for the assistance!

---

### Post by rxbandit on 2009-01-25
How do you go about updating to 2.1? I downloaded the source but it uses cmake which I have never used and appears to have a lot of KDE dependencies and the install instructions are geared for KDE. I'm using gnome.

---

### Post by vividia on 2009-01-31
> **rxbandit said:**
> How do you go about updating to 2.1? I downloaded the source but it uses cmake which I have never used and appears to have a lot of KDE dependencies and the install instructions are geared for KDE. I'm using gnome.

That tarball is for KDE.  You'd need to install K environment for it to run properly.  

For Gnome users, go to this link: [http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy).  I posted it in a previous post.

After you do that follow these instructions. Open terminal and put this in (I feel no need to put myself in quotations):

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Once thats done, you can enable the mulitverse and Universe repositories by putting this in:

sudo sed -i -e &#8220;s/# deb/deb/g&#8221; /etc/apt/sources.list && sudo apt-get update

Then install the libdvdcss2.

sudo apt-get install libdvdcss2

if you haven't done the w32codecs (or 64), do them while you're at it.

sudo apt-get install w32codecs (substitute 64 for 32 if you need to)

Let me know if you have any problems.

---

