---
title: "oss4-dkms (no audio) issue after lucid upgrade"
date: 2010-05-14
forum: Multimedia Software
---

### Post by misaelrod on 2010-05-14
Hi all,

I am running a 64-bit version of lucid that I just upgraded the other day. At first everything was working fine, but after some upgrades (don't remember which ones) I get an oss4-dkms error and I have no audio. 

I have tried a bunch of things that I found online, but nothing has seemed to work and at this time I am a little lost with this issue and would love some help.

Following is some information that will give you a few more clues

misaelrod@misaelrod-laptop:~$ ossinfo
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.

misaelrod@misaelrod-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Thanks in advance for the help

---

### Post by moondoggy2 on 2010-05-26
Bump

---

### Post by Bloemetjesgordijn on 2010-07-03
same issue here, did anyone solve it??

thx

Konsole output:

marc@HTPC:~$ sudo aptitude install oss4-dkms
[sudo] password for marc: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Uitgebreide statusinformatie aan het lezen      
Initialiseren van pakketstatussen... Klaar
Schrijven van uitgebreide statusinformatie... Klaar
De volgende gedeeltelijk geïnstalleerde pakketten zullen worden geconfigureerd:
  oss4-dkms 
0 pakketten opgewaardeerd, 0 nieuwe geïnstalleerd, 0 te verwijderen en 1 niet opwaarderen.
Heb 0B archieven nodig. Na uitpakken zal 0B worden gebruikt.
Schrijven van uitgebreide statusinformatie... Klaar
Instellen van oss4-dkms (4.2-build2002-2) ...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cp /lib/modules/2.6.32-23-generic/source/include/linux/limits.h /var/lib/dkms/oss4/4.2-build2002/build/core && make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/core modules && make -C /var/lib/dkms/oss4/4.2-build2002/build/drivers osscore_symbols.inc && make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/drivers modules....(bad exit status: 1)

Error! Bad return status for module build on kernel: 2.6.32-23-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/oss4/4.2-build2002/build/ for more information.
0
0
dpkg: fout bij afhandelen van oss4-dkms (--configure):
 subproces installed post-installation script gaf een foutwaarde 10 terug
Fouten gevonden tijdens behandelen van:
 oss4-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
Bevestigd! Er is iets ergs gebeurd bij het installeren van pakketten. Erwordt geprobeerd van te herstellen:
Instellen van oss4-dkms (4.2-build2002-2) ...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cp /lib/modules/2.6.32-23-generic/source/include/linux/limits.h /var/lib/dkms/oss4/4.2-build2002/build/core && make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/core modules && make -C /var/lib/dkms/oss4/4.2-build2002/build/drivers osscore_symbols.inc && make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/drivers modules....(bad exit status: 1)                                                                                                                                                 

Error! Bad return status for module build on kernel: 2.6.32-23-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/oss4/4.2-build2002/build/ for more information.
0
0
dpkg: fout bij afhandelen van oss4-dkms (--configure):
 subproces installed post-installation script gaf een foutwaarde 10 terug
Fouten gevonden tijdens behandelen van:
 oss4-dkms
Pakketlijsten worden ingelezen... Klaar            
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Uitgebreide statusinformatie aan het lezen      
Initialiseren van pakketstatussen... Klaar

---

### Post by misaelrod on 2010-07-03
I ended up reinstalling Ubuntu

---

### Post by Bloemetjesgordijn on 2010-07-03
well I just reinstalled KUbuntu last week. With all the applications and setting it is quite an effort. 

I am hoping for a better solution.

---

### Post by chudder on 2010-07-18
I'm having the same problem, I solved the no sound issue by reinstalling ALSA but I'm worried upgrades will do this again.

---

### Post by lkjoel on 2010-07-18
Check Fix your Sound! in my sig.
It will install OSS 4.x (the latest development release) for you.

---

### Post by chudder on 2010-07-18
I found an alternative solution here: [http://ubuntuforums.org/showthread.php?p=9606953#post9606953]("http://ubuntuforums.org/showthread.php?p=9606953#post9606953")

I just took out almost all of the oss components that weren't essential for me and then reinstalled alsa.

I'll look at your solution though, thanks!

---

