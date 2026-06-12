---
title: "AR5523 Chipset TP Link TL-WN620G driver problem on ubuntu 11.04 desktop 32 bit"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by naczu on 2011-08-17
Hi Ubuntu users and developers. I am newbie in here. I need help. I was trying to install driver for TP Link TL-WN620G wireless adapter..... On my pc installed ubuntu 11.04 32 bit desktop edition. I tried this steps But it doesnt work

1) I tried all in this page but it doesn't work. The adapter is not flashing.
[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29)




2) and I tried this
[http://wiki.debian.org/ar5523](http://wiki.debian.org/ar5523)
 
for step 3 and 5 I followed this steps
[http://ubuntuforums.org/showpost.php?p=10499585&postcount=10](http://ubuntuforums.org/showpost.php?p=10499585&postcount=10)
there is an error when I run this command  ```
dpkg-buildpackage -us -uc
```Error is like this
```
Applying patch kcompat-2.6.34.patch
patching file ar5523.c
Hunk #4 FAILED at 1117.
Hunk #5 FAILED at 1137.
Hunk #6 FAILED at 1154.
Hunk #7 FAILED at 1170.
Hunk #8 FAILED at 1190.
Hunk #9 FAILED at 1208.
Hunk #10 FAILED at 1223.
7 out of 10 hunks FAILED -- rejects in file ar5523.c
Patch kcompat-2.6.34.patch does not apply (enforce with -f)
make: *** [debian/stamp-patched] Hata 1
dpkg-buildpackage: hata: debian/rules build gave error exit status 2

```Please Help me... I cant install the driver.

---

### Post by naczu on 2011-08-17
it has solved. I loged as root. And then tried this steps again
[https://help.ubuntu.com/community/Wi...ndiswrapper%29]("https://help.ubuntu.com/community/Wi...ndiswrapper%29")

But I have still trobule... When I reset the pc, I have to uninstall driver and reinstall again... it is strange...

---

