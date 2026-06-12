---
title: "install ubuntu on LG BD390?"
date: 2009-07-30
forum: Multimedia Software
---

### Post by OneEyedBobby on 2009-07-30
Hi all,

My apologies if I'm posting this in the wrong section of the forum...

I just purchased the BD390 blu-ray player from LG and was surprised to find that it is running a Linux operating system, which immediately got me wondering if it would be possible to install Ubuntu in order to extend it's functionality.

Initial thoughts - the unit already contains wireless networking so it would be cool to add Firefox for internet access.  Would also be great to add VLC to handle video formats which are not natively supported.  And audio support for ogg.  The possibilities go on and on...

Following is a list of the pre-loaded software from the Owner's manual.

GPL Executables:

[INDENT]Linux kernel 2.6
bash
busybox
dhcpcd
mtd-utils
net-tools
procps
sysutils
tinylogin
[/INDENT]

LGPL Libraries:

[INDENT]uClibc
DirectFB
iconv
cairo
gnutls
libcrypt
libgpg-err
libusb
[/INDENT]
gSOAP Public License 1.3 Library

[INDENT]gsoap
[/INDENT]
The product also includes:

[INDENT]Freetype library
libpng library
Zlib compression library
Expat library
OpenSSL library
libcurl library
boost C++ library
UPnP SDK
Libnet
Libpcap[/INDENT]

LG also offers to provide a copy of the source code - I'm in the process of getting a copy though not completely sure how helpful this will be.

So, the big question:  is it possible that Ubuntu could be loaded onto this hardware?

If "yes" - where to start?

A big thanks in advance for all thoughts & feedback on my question.

Cheers,
Bob

---

### Post by igorzwx on 2009-07-30
Google tolt this:
[http://www.google.com/search?q=install%20ubuntu%20on%20LG%20BD390%3F&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=install%20ubuntu%20on%20LG%20BD390%3F&ie=UTF-8&oe=UTF-8)

---

### Post by OneEyedBobby on 2009-07-30
Thanks - I've googled this from every angle but can't find anything that addresses the topic...

---

### Post by igorzwx on 2009-07-30
"I just purchased the BD390 blu-ray player from LG and was surprised..."

If you have the thing, why not try?

book:

Ubuntu Linux for Dummies.chm

read some 20 pages (with pictures),
and give it a try.

---

### Post by OneEyedBobby on 2009-07-30
"I just purchased the BD390 blu-ray player from LG and was surprised..."

If you have the thing, why not try?  

[INDENT][COLOR="Red"]I very much would like to try, not sure where to start and was hoping for some help.[/COLOR][/INDENT]

book:

Ubuntu Linux for Dummies.chm

read some 20 pages (with pictures),
and give it a try.

[INDENT][COLOR="red"]My assumption is that this is a complicated topic.  I also assume that reading 20 pages in the dummies guide would not address the issues that I might face in getting Ubuntu loaded.[/COLOR][/INDENT]

---

### Post by martinbaselier on 2009-07-30
Why don't you try to find out what kind of linux is installed and see if you can extend it within that system. Chances are there that part of the hardware is handled by closed source drivers. This would propose a problem. Maybe you can install rpm packets on it?

---

### Post by OneEyedBobby on 2009-07-30
To provide additional details around the challenges that I'm facing:

[LIST=1]
[*]Not sure how to launch the Ubuntu installer
[*]Not sure how to get to a command line
[*]Upon powering up the BD390 goes directly to a "home" screen allowing the user to launch different features (play disc, stream netflix, view pics, etc.).  If I was able to load Ubuntu I would need to find a way to toggle between the Ubuntu desktop and the native home page for the player
[/LIST]

Hope that this helps to clarify the issues that I'm currently thinking about.  I'm sure that there are others that would need to be considered which just haven't occurred to me yet...

All thoughts and suggestions appreciated.

---

### Post by OneEyedBobby on 2009-07-30
Great idea.  I'll keep digging to find out and hoping that the disc containing the source files can help in this area...

---

### Post by igorzwx on 2009-07-30
That "dummy book" is not so dummy

---

### Post by OneEyedBobby on 2009-07-30
> **igorzwx said:**
> That "dummy book" is not so dummy

Cool - I'll give it a shot.

---

### Post by fdemmer on 2009-11-30
has anyone succeeded in a) getting the source from lg, b) compiling it and c) installing it?

---

### Post by fdemmer on 2009-12-04
so i bought this thing now... a lot of stuff works just fine regarding streaming/sharing media. with an ubuntu server & mediatomb.

i have more details on a blog page [here]("http://demmer.ipax.at/blog/lg-bd390/")

i also requested the source from lg and got a 250MB tgz with this content:

```
total 261360
-rwxr--r-- 1 1000 100  78157835 2009-04-27 03:31 crosstools-linux-2.6.18.0-uclibc-nptl-0.9.29-20070423-4.2-9ts.src.rpm
-rwxr--r-- 1 1000 100    154836 2009-03-30 07:40 gsoap-2.7.12.tar.gz
-rwxr--r-- 1 1000 100   4558248 2009-03-30 08:15 libgnutls_bcm7601_src.tgz
-rwxr--r-- 1 1000 100  21496687 2009-04-27 03:41 libs-2624.7.tar.bz2
-rwxr--r-- 1 1000 100  47234100 2009-04-27 03:35 stblinux-2624.7_221_gpl.tar.bz2
-rwxr--r-- 1 1000 100 115723761 2009-04-27 03:50 uclinux-rootfs-2624.7_221_gpl.tar.bz2
```

so... it's relatively old. the latest firmware update was in November. also the whole gui/menu stuff seems to be missing and obviously there are no easy to use build or flash instructions :P

---

### Post by OneEyedBobby on 2009-12-17
I ordered the source files from LG as well, but unfortunately I was unable to make progress towards my goal of loading ubuntu.  Still interested but hopelessly stuck...

---

### Post by Ghost09 on 2010-03-08
Hi,

can anyone upload the stblinux-2624.7_221_gpl.tar.bz2 to a webserver/webhoster/ftp .. or whatever?

I would try gladly some things out.

It would be very friendly if someone could do this!

Thanks!

---

### Post by pkozul on 2010-05-12
Hi there,

Did anyone get hold of the source code for the LG BD390? I was wondering if you could find out which formats are supported for streaming, i.e. the mime types, file extensions, etc.

Thanks,
Petar

---

### Post by fdemmer on 2010-05-23
i had the source. deleted it by accident, i guess. cannot find i anymore. i found no useable build environment in the package, so i gave up on the idea of building it myself very quickly... but i am no expert in this. also i could not find anything that looked like the actual gui application.

it was easy to get though, if anyone wants to give it a shot just email lg at the address given in the manual (at the very end al sw components and their license are listed incl that address). they sent me a dl link within about a week.

btw: here is a discussion about whether a build environment must be included to be gpl compliant: [http://yro.slashdot.org/story/10/05/23/2018220/Do-Build-Environments-Give-Companies-an-End-Run-Around-the-GPL?art_pos=2](http://yro.slashdot.org/story/10/05/23/2018220/Do-Build-Environments-Give-Companies-an-End-Run-Around-the-GPL?art_pos=2)

---

### Post by fdemmer on 2010-07-23
here is the source package from lg:

[http://rapidshare.com/files/408707293/BD390.tgz](http://rapidshare.com/files/408707293/BD390.tgz)

---

### Post by pkozul on 2010-09-12
Hi,
 
Thanks for the information and the link.
 
In the meantime, I was looking at various media servers to use with my LG BD390. I came across and installed Mezzmo ([www.mezzmo.com]("http://www.mezzmo.com")) on my machine.
 
It works really well with my LG BD390, so I have decided to stick with Windows. It was easy to install and worked out-of-the-box with my LG player. What I like most is that I can also use my iPhone to access all of my music and videos, since Mezzmo has support for many devices.
 
Anyway, thanks again for the link. I will have a look at the code.
 
Regards,
Petar

---

### Post by pkozul on 2010-09-14
Hi again,
 
I got this response from LG:
 
"Thank you for choosing LG product.  
You can download the source code from [http://opensource.lge.com]("http://opensource.lge.com/") 
Maybe you can get it from Audio/Video Category."

I downloaded the code, and at first glance, I can't really tell where the LG-specific code is located...
 
Will have a better look when I get some more time.
 
Regards,
Petar

---

### Post by abzze on 2011-02-05
Any one cracked this yet?

---

