---
title: "Scanner Epson v100 can not work on normal user account"
date: 2008-11-17
forum: Multimedia Software
---

### Post by ff1-ff1 on 2008-11-17
In former ubuntu editions (former to 8.10) there was not any problems with installation and configuration of epson v100 scanner. It was enough to download drivers and plugin from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)  and use procedure given (for example) here: [http://push.cx/2007/epson-perfection-v100-in-ubuntu](http://push.cx/2007/epson-perfection-v100-in-ubuntu)  .
   But in Ubuntu 8.10 something was changed. Now system recognizes internet camera on usb (which in fact doesn&#8217;t works correctly). Problem is that:
- (using normal user account) when I switch on xsane, software recognizes only this useless camera. Xsane informs me about that: ,,USB camera:video0 &#8220; and shows me black screen with some artifacts.
-(using root account) after starting xsane I have choice what source of signal to use: camera or (well recognized) scanner-that behavior is correct.

Additional infos:
-after installation of scanner and command lsusb I get:
Bus 005 Device 002: ID 04b8:012d Seiko Epson Corp. Perfection V10/V100 (GT-S600/F650)   < --- this is my scanner
Bus 004 Device 003: ID 0c45:612a Microdia PC Camera (SN9C110)  <-- this is camera

-after sane-find-scanner  command I get:
found USB scanner (vendor=0x04b8, product=0x012d) at libusb:005:002
found USB scanner (vendor=0x0c45, product=0x612a) at libusb:004:003

-after scanimage &#8211;L I get:
device `v4l:/dev/video0' is a Noname USB camera virtual device

-after unplugging camera and restart of system xsane (on normal user account) tells that:
. can not find any equipment to use (or something like that) 
. lsusb  tells that system has plugged scanner (like above)
.after scanimage &#8211;L I get info that ,, No scanners were identified&#8221; LOL!!!

On Polish forum I got recipes like that:
-to add normal user to group scanner: I did so but without results. I can mention  that root doesn&#8217;t belongs to group scanner and on root everything is OK !! ??

or

- in file /etc/udev/rules.d/45-libsane.rules to put manually info about my scanner with additional info about group of users: normal user should be add to group scanner and this text:
Seiko Epson Corp. Perfection V10/V100 (GT-S600/F650) SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012d", MODE="666", GROUP="scanner
Problem is that I don&#8217;t have such file like 45-libsane.rules!!! 

-closest to this file (in meaning) is iscan file (my driver to scanner)--- >  rules.d/60_iscan.rules  . I modyfied manually line: SYSFS{idVendor}="04b8" SYSFS{idProduct}="012d" MODE="0666"  to this one:
SYSFS{idVendor}="04b8" SYSFS{idProduct}="012d" MODE="0666"  GROUP="scanner" . Without expected results.



It looks like system takes bad equipment to scan on normal user account -how to change this ( I would like to have situation like on root: I can chose what to use)???????????????

---

### Post by ff1-ff1 on 2008-11-17
No one can help me??????????

---

### Post by glennph93 on 2008-11-18
I'm having the same problem with my Epson V200 scanner. I did have a backup of my libsane.rules and placed it back with no luck.

---

### Post by ff1-ff1 on 2008-11-19
i posted new thread at [http://www.linuxquestions.org/questions/ubuntu-63/scanner-epson-v100-can-not-work-on-normal-user-account-684645/](http://www.linuxquestions.org/questions/ubuntu-63/scanner-epson-v100-can-not-work-on-normal-user-account-684645/)   I hope that someone can help us....

---

### Post by Robert A. Matthews on 2008-12-27
I have also had this problem but got things to work by amending:

/etc/udev/libsane-extras.rules

to include:

# EPSON Perfection V100
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"

After a system restart, things worked OK.

Hope this helps,

Robert

---

### Post by e00878 on 2009-01-05
/etc/udev/libsane-extras.rules

is empty file on ubuntu 8.10

---

### Post by xc3RnbFO8P on 2009-01-05
> sudo gedit /etc/udev/libsane-extras.rules
Add this:
> # EPSON Perfection V100
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
save and restart the computer.

---

### Post by e00878 on 2009-01-05
thank you very much indeed! :popcorn:
very slowly but works!

---

### Post by oygle on 2009-04-20
The latest version now has the DEB package, so no need for the 'alien' part.

---

### Post by glennph93 on 2009-04-20
Did you try to install it that way oygle.I tried and had a library dependency problem.

---

### Post by oygle on 2009-04-20
I'm running 8.10 and downloaded the DEB's , expecting all to go okay, but had all sorts of problems with installing those DEBS. Then tried downloading the RPM's and using 'alien' but still no go.

Yes, there were dependency problems.

Then I saw the post at [http://ubuntuforums.org/showpost.php?p=7025264&postcount=13](http://ubuntuforums.org/showpost.php?p=7025264&postcount=13) , downloaded iscan_2.18.0-2_i386.deb , installed that version, then installed the iscan_plugins , and am now able to scan okay (after adding my user ID to the 'scanner' group of course).

---

### Post by glennph93 on 2009-04-20
Thanks for the info I'm also running 8.10. I'll probably wait to install 9.04 before installing those debs.

---

