---
title: "MSI Wind - Wireless Card"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by ihaveshoes on 2010-04-25
I apologize if this has already been resolved somewhere on this forum. On my searching I have seen this issue posted numerous times, but the links for solutions are all broken or the solution does not work for me.

My issue is that Ubuntu 8.1 will not recognize my wireless card. I am connected currently through a wired connection.

These are the commands I have tried:

wget [http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz](http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz)
tar xvfz rtl8187se_linux_26.1023.0928.2008.tar.gz
cd rtl8187se_linux_26.1023.0928.2008/
./makedrv


I then get an error: Build of the package rt2860-source failed! I have an option to look at the log and it outputs the following: 

```
 &#9474; dh_testdir                                                                 &#8593;
 &#9474; dh_testroot                                                                &#9646;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     &#9618;
 &#9474; make[1]: Entering directory `/usr/src/modules/rt2860'                      &#9618;
 &#9474; dh_testdir                                                                 &#9618;
 &#9474; dh_testroot                                                                &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; dh_clean: Sorry, but 6 is the highest compatibility level supported by     &#9618;
 &#9474; this debhelper.                                                            &#9618;
 &#9474; make[1]: *** [kdist_clean] Error 1                                         &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/rt2860'                       &#9618;
 &#9474; make: *** [kdist_build] Error 2                                            &#9618;
 &#9474; ^Y       
```I'm not sure at all what I am doing wrong and any help or guidance would be much appreciated. Obviously I am a newb at this and am rather confused.

---

