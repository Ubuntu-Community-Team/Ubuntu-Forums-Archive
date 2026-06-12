---
title: "epson perfection with vuescan"
date: 2008-05-20
forum: Multimedia Software
---

### Post by derek_stnly1961 on 2008-05-20
I am trying to set up an epson perfection scanner (v500) on Ubuntu.  I have the scanner working fine but want to use vuescan.  I have seen other people have had no problem with vuescan at all but i can't seem to get vuescan running.   I have checked to make sure it is and executable file and it is.  I double click the icon or trying to start it from command line wont work.   I get no error messages.   It tries to start (i see the mouse pointer changes to a "working" icon) then after a minute nothing. no error messages or anything.

anyone have any ideas?

derek

---

### Post by rbmorse on 2008-05-20
If the scanner is working normally under something like iScan or xsane, you have encountered a pecular "shortcoming" in Vuescan. I can't call it a bug because the developer knows about it, but feels it is an issue external to Vuescan in which VueScan is unable to properly initialize certain Epson scanners. There are two workarounds I've found:

1. Make sure the scanner is connected and powered up before the Ubuntu session is booted, or

2. open a terminal and run some other application that will properly initialize the scanner like xsane or scanimage -L  (note the upper case "L") and then start Vuescan. Once you do this, you should not have to do it again until you reboot.

---

### Post by derek_stnly1961 on 2008-05-20
I must not have been clear in my question but thanks for your help.   the reason vuescan wouldn't run is because of GCC 4.3.  i had to install:
compat-libstdc++-33
compat-libstdc++-296

now it runs fine.   

again thanks for your help

derek

---

### Post by rbmorse on 2008-05-20
There's a libstdc++5 in respository that should have addressed the GCC compatiblity requirements under Ubuntu.

As far as I can tell, the compat-libstdc++ files you listed are from RedHat and not native to Debian/Ubuntu, but hey...if it works, it works!

---

### Post by John Catt on 2010-08-26
> **derek_stnly1961 said:**
> I am trying to set up an epson perfection scanner (v500) on Ubuntu.  I have the scanner working fine but want to use vuescan.  I have seen other people have had no problem with vuescan at all but i can't seem to get vuescan running.   I have checked to make sure it is and executable file and it is.  I double click the icon or trying to start it from command line wont work.   I get no error messages.   It tries to start (i see the mouse pointer changes to a "working" icon) then after a minute nothing. no error messages or anything.

anyone have any ideas?

derek

I'm trying to get the Epson Perfection V500 Photo to work in Ubuntu 10.04. Have tried various things that appear to relate to earlier versions. Please can you let me know how I should set this up?

---

### Post by John Catt on 2010-08-27
> **John Catt said:**
> I'm trying to get the Epson Perfection V500 Photo to work in Ubuntu 10.04. Have tried various things that appear to relate to earlier versions. Please can you let me know how I should set this up?
Managed to get it working.

Process is:
1. Check with Synaptic that sane is installed.
2. Down load the drivers from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do) (you need to put in some details to mover through to the drivers).
3. Files required are:
iscan-data_1.0.1-1_all.deb
iscan_2.25.0-1.ltdl7_i386.deb
iscan-plugin-gt-x770_2.1.1-2_i386.deb
4. Open a terminal and move to the directory where you downloaded the file (cd command).
5. Run these commands in sequence.
sudo dpkg -i iscan-data_1.0.1-1_all.deb
sudo dpkg -i --force-overwrite iscan_2.25.0-1.ltdl7_i386.deb
sudo dpkg -i iscan-plugin-gt-x770_2.1.1-2_i386.deb
6. Type in iscan and you should be underway. Not the greatest program but at least will show that you can scan

Edit - packages have been updated so files have changed and 
point 5 should now be:

sudo dpkg -i iscan-data_1.8.1-1_all.deb
sudo dpkg -i iscan_2.26.3-1.ltdl7_i386.deb
sudo dpkg -i iscan-plugin-gt-x770_2.1.2-1_i386.deb

---

### Post by mark bower on 2010-12-27
Using Ubuntu 9.10.  Epson Perfection V500

1) Downloaded VueScan vuex3290.tgz (VueScan 9.0.08 32 bit) from hamrick.com and extracted.

2) Icon will not execute.

3) Trying a cmd line execution (./vuescan) I get "./vuescan /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.11' not found (required by ./vuescan)

4) However, libc.so.6 (link to shared lib) _is located_ at /lib///cmov.  It is linked to libc-2.10.1.so (shared lib) which _is also located_ in /etc///cmov.

[Note:  using synaptic pkg mgr i cannot get either of the two libraries to show, even tho they appear in Nautilus?)

So what may be the problem?  My scanner works with Xsane and VueScan 8.6.08.  Unfortunately, Ed Hammrick is not able to support this type of question(library issues), though a nice application when the versions are compatible for Linux.


mark bower

---

### Post by mark bower on 2010-12-28
bump for response
mark bower

---

### Post by mark bower on 2010-12-30
bump for reply

---

### Post by mark bower on 2010-12-31
bump for reply

---

### Post by mark bower on 2010-12-31
bump again

---

### Post by mark bower on 2011-01-01
anyone else have an idea why VueScan 9.0.08 will not recognize libraries that are in fact present.

mark

---

### Post by mark bower on 2011-01-02
bumped again.  hoping someone knows how/why/what to do to get VueScan to recognize that a library it wants is in fact present.  that is, it is looking for libc.so.6, the library is where it is supposed to be, but VueScan does not see it.

mark bower

---

### Post by mark bower on 2011-01-02
bumped again.  hoping someone knows how/why/what to do to get VueScan to recognize that a library it wants is in fact present.  that is, it is looking for libc.so.6, the library is where it is supposed to be, but VueScan does not see it.

mark bower

---

### Post by mark bower on 2011-01-02
bumped again.  hoping someone knows how/why/what to do to get VueScan to recognize that a library it wants is in fact present.  that is, it is looking for libc.so.6, the library is where it is supposed to be, but VueScan does not see it.

mark bower

---

### Post by mark bower on 2011-01-02
From the top.

With Ubuntu 9.10, VueScan 9.0.08 will not execute.  When executed from the cmd line, it gives the error message: "./vuescan  /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.11' not found (required by ./vuescan)".  In fact, libc.so.6 is present in /lib/tls/i686/cmov/.

What can be done to get VueScan to see libc.so.6 at /etc///cmov/?  I would point out again, disappointingly, that Ed Hamrick (hamrick.com) does not provide support for this problem.

[Note:  An earlier version of VueScan, Xsane, Iscan, etc all work]

---

### Post by mark bower on 2011-01-02
o.k.  I believe I understand the problem, but not readily corrected.  

The version of libc.so.6 installed with Ubu 9.10 is 2.10.1.  Apps later than Oct 09 are looking for libc.so.6 in version 2.11.  Thus the error msg in my case:   "./vuescan  /lib/tls/i686/cmov/libc.so.6: version 'GLIBC_2.11' not found (required by ./vuescan).  The library is involved with security so is not obtained as one normally might.  Please see the link below which shows the exact parallel to the problem I encountered with VueScan.

[http://codetrips.blogspot.com/2010/12/latest-update-for-android-sdk-breaks.html](http://codetrips.blogspot.com/2010/12/latest-update-for-android-sdk-breaks.html)

From other inputs, an upgrade to 10.4 or 10.10 would solve the compatibility problem.  An inconvenience that the latest version of VueScan is not backwards compatible.

---

