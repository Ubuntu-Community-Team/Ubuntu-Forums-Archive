---
title: "WUSB54GSC and ndiswraper for usb linksys card"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by Suff on 2009-08-02
I am not sure at all how to get around this problem with WUSB54GSC CD and ndiswraper.
This is what i get when i try to run this code:

```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```

suffice@suffice-desktop:~$ sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
[sudo] password for suffice: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpp is already the newest version.
gcc is already the newest version.
linux-headers-2.6.28-11-generic is already the newest version.
linux-headers-2.6.28-11-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6270kB of archives.
After this operation, 21.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive '/cdrom/' and press enter

Failed to fetch cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/pool/main/g/gcc-4.3/g++-4.3_4.3.3-5ubuntu4_i386.deb Hash Sum mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

I have downloaded ndiswraper but i do not know where to get the files from the usb wifi CD.


I have also tried to use the installation disk to get ndiswraper but this error occurs:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Not at all sure what to do now, been trying to solve this problem for a few hours now. Help on this issue would be great!

---

### Post by Crafty Kisses on 2009-08-02
I'm really not sure about the question. You can download the Windows drivers right **[here.]("http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download")** Then you need to find the "**WUSB54GSC.inf**" file first, then you can install ndiswrapper by running as root:
```
apt-get install ndiswrapper-common
```
Once you have ndiswrapper installed, you can run:
```
ndiswrapper -i WUSB54GSC.inf
ndiswrapper -m
```
Then make sure the driver installed by running:
```
ndiswrapper -l
```
Then make sure the ndiswrapper module is in place by running:
```
modprobe ndiswrapper
```
Then you can run the following:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
That should technically get your card up and running.

---

### Post by Suff on 2009-08-02
> Then you need to find the "**WUSB54GSC.inf**" file first, then you can install ndiswrapper by running as root:I downloaded the wrong drivers before, i was wondering why the model number was wrong, thanks.
But i can't find the **WUSB54GSC.inf file, ** its not in the drivers i downloaded[B]. Could it be ndiswdm.inf in the driver folder?


Okay, i have run this code[/B]:
```
apt-get install ndiswrapper-common
```[B]
Then says ndiswrapper-common is already the newest version when i try to run it again.



And it says its installed but when i try to run this code it says: ndiswrapper-utils 1.9-not installed!
[/B]```
ndiswrapper -i WUSB54GSC.inf
```[B] 
Also is "sudo" root?

[/B]

---

### Post by Suff on 2009-08-02
Hello

---

### Post by Suff on 2009-08-03
Bump again.

---

