---
title: "media and upgrade woes ubuntu 7.10 gutsy"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by apollofm on 2008-02-02
re ubuntu 7.10 
cannot install codecs downloaded or player i download to my desk top also my package handler wont download all translation english keeps failing causing it to hang 
please take it easy on me im really new ive spent one week trying to set up the dual boot and internet many installs on both but now i really need some help ive had everything running but i removed the ms drive and everything died so i had to reload and its been two days since ive had any luck
please help my freinds are worried for my health its been a week of many sleepless nights

---

### Post by RomeReactor on 2008-02-02
Hi. Please open Synaptic (System->Administration->Synaptic), there go to 'Settings->Repositories' and on the first tab (Ubuntu Software) check the top four boxes; close that window and, still in Synaptic, press the blue 'Reload' button. Then see if you're now able to install the packages.

The servers for your area might be having problems, so if you're still unable to install the packages, try going again to 'Settings->Repositories' in Synaptic, this time press the 'Download from' dropdown menu, select 'Other', and in the new window press 'Select best server'.

---

### Post by apollofm on 2008-02-02
thanks  for you quick responce
its down loading most of the the updates all except the 
well this is what im getting 

[http://ftp.debian.org/dists/sarge/Release.gpg:](http://ftp.debian.org/dists/sarge/Release.gpg:) Could not connect to ftp.debian.org:80 (32.1.8.56), connection timed out
[http://ftp.debian.org/dists/sarge/main/i18n/Translation-en_NZ.bz2:](http://ftp.debian.org/dists/sarge/main/i18n/Translation-en_NZ.bz2:) Could not connect to ftp.debian.org:80 (32.1.8.56), connection timed out
[http://packages.medibuntu.org/dists/gutsy/Release.gpg:](http://packages.medibuntu.org/dists/gutsy/Release.gpg:) Could not connect to packages.medibuntu.org:80 (32.1.8.56), connection timed out
[http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_NZ.bz2:](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_NZ.bz2:) Could not connect to packages.medibuntu.org:80 (32.1.8.56), connection timed out
[http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_NZ.bz2:](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_NZ.bz2:) Could not connect to packages.medibuntu.org:80 (32.1.8.56), connection timed out
[http://archive.canonical.com/ubuntu/dists/gutsy/Release:](http://archive.canonical.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  partner/binary-i386/Packages in Meta-index file 

hope this is helpfull

the packages are gpg and language packs

---

