---
title: "Installing 'Patch' package without internet connection.(ACX 100 wireless chipset)"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by RHub787 on 2012-01-12
HI, I am trying to install my wireless card with Ubuntu 11.10.

It is an older HP wireless card with the TI ACX 100 chipset.

I found this helpful thread here : [http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303)

which states:
> I´m glad to announce that there is a patch to compile acx 100/111 driver in kernel 2.6.31 
Just follow this instructions:

1. mkdir acx
2. cd acx
3. wget [http://downloads.sourceforge.net/acx...080210.tar.bz2]("http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2")
4. tar xjvf acx-20080210.tar.bz2
5. wget [http://cc.oulu.fi/~rantalai/acx_karmic.patch]("http://cc.oulu.fi/%7Erantalai/acx_karmic.patch")
6. patch -p0 < acx_karmic.patch
7. cd acx-20080210/
8. make -C /lib/modules/`uname -r`/build M=`pwd`my problem is when I get to step 6.  I recieve the error:
> The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
Problem is, I don't have an internet connection yet to use apt-get!

How can Install the program 'patch' without an internet connection?

Thanks!
[COLOR=Olive]

[/COLOR][COLOR=DarkOliveGreen][COLOR=Olive][for any other inexperienced user(like myself) who is also trying to do what I am doing, skip steps 3 and 5 (since you don't have an internet connection).  instead use a internet connected OS and save the files mentioned in steps 3 & 5.  When you open Ubuntu move the two files to the acx folder you created in step 1.(/home/<username>/acx)][/COLOR]
[/COLOR]

---

