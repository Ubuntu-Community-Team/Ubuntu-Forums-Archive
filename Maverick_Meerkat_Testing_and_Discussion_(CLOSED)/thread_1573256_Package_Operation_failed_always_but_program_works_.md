---
title: "Package Operation failed :always but program works fine ?"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by binarylife on 2010-09-12
I'm using 10.10 .
Everythime I try To Update or install a program I get like this msg :
Package Operation failed 
The Installation or removal of a software package failed .

for example I tried to install CodeBlocks ,but I get this: 


Details :
nstallArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 240197 files and directories currently installed.)
Preparing to replace gcc-4.4 4.4.4-14ubuntu1 (using .../gcc-4.4_4.4.4-14ubuntu2_amd64.deb) ...
Unpacking replacement gcc-4.4 ...
Preparing to replace cpp-4.4 4.4.4-14ubuntu1 (using .../cpp-4.4_4.4.4-14ubuntu2_amd64.deb) ...
Unpacking replacement cpp-4.4 ...
Preparing to replace gcc-4.4-base 4.4.4-14ubuntu1 (using .../gcc-4.4-base_4.4.4-14ubuntu2_amd64.deb) ...
Unpacking replacement gcc-4.4-base ...
Selecting previously deselected package libwxbase2.8-0.
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.11.0-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libwxgtk2.8-0.
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.11.0-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libcodeblocks0.
Unpacking libcodeblocks0 (from .../libcodeblocks0_10.05-0ubuntu1_amd64.deb) ...
Selecting previously deselected package codeblocks-common.
Unpacking codeblocks-common (from .../codeblocks-common_10.05-0ubuntu1_all.deb) ...
Selecting previously deselected package codeblocks.
Unpacking codeblocks (from .../codeblocks_10.05-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.4-dev.
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.4-14ubuntu2_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.4-14ubuntu2_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.4-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up gloobus-preview (0.4.5-ubuntu7~ppa245) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up gcc-4.4-base (4.4.4-14ubuntu2) ...
Setting up cpp-4.4 (4.4.4-14ubuntu2) ...
Setting up gcc-4.4 (4.4.4-14ubuntu2) ...
Setting up libwxbase2.8-0 (2.8.11.0-0ubuntu4) ...
Setting up libwxgtk2.8-0 (2.8.11.0-0ubuntu4) ...
Setting up libcodeblocks0 (10.05-0ubuntu1) ...
Setting up codeblocks-common (10.05-0ubuntu1) ...
Setting up codeblocks (10.05-0ubuntu1) ...
Setting up libstdc++6-4.4-dev (4.4.4-14ubuntu2) ...
Setting up g++-4.4 (4.4.4-14ubuntu2) ...
Setting up g++ (4:4.4.4-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gloobus-preview
Setting up gloobus-preview (0.4.5-ubuntu7~ppa245) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127


?help? P.s : The program works fine.  
Thanks

---

### Post by cariboo on 2010-09-12
Code::blocks isn't your problem, 

> Errors were encountered while processing:
gloobus-preview
Setting up gloobus-preview (0.4.5-ubuntu7~ppa245) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
subprocess installed post-installation script returned error exit status 127

Your problem is gloobus-preview, go to Synaptic and use the broken packages filter to remove it.

---

### Post by binarylife on 2010-09-12
> **cariboo907 said:**
> Code::blocks isn't your problem, 



Your problem is gloobus-preview, go to Synaptic and use the broken packages filter to remove it.

Thanks, It worked.

---

### Post by jastonas on 2010-09-22
I ve got the same problem. Seems gloobus-preview is installed but cannot be found in synaptic. When sudo apt-get remove gloo-tab.. nothing shows up, yet cover-gloobus works on my pc!

Every time though I ran synaptic or apt-get I get
> 
1 not fully installed or removed.

Setting up gloobus-preview (0.4.5-ubuntu7~ppa245) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 gloobus-preview
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by AvidChronos on 2010-09-28
I Get the same problem. It happens on every program that I install. I think I closed software center while i had to reboot or something and it then stopped working properly. I couldnt install anything. Then I tried to install readpst and it kept timing out on trying to download the third party windows fonts. Now I got it to install, but this error is a pain!

I tried to install sudo apt-get install fglrx from another forum post and got this at the end:


DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up fglrx-amdcccle (2:8.780-0ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic-pae
Processing triggers for python-support ...
Errors were encountered while processing:
 wine1.2
 man-db
 wine
 playonlinux
 ttf-mscorefonts-installer
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by binarylife on 2010-09-28
> **AvidChronos said:**
> 
Errors were encountered while processing:
 wine1.2
 man-db
 wine
 playonlinux
 ttf-mscorefonts-installer
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

As I've learned from this problem that u need to remove these packages from Synaptic package manager:
wine1.2
man-db
wine
playonlinux
ttf-mscorefonts-installer
winbind

because the errors came from them 
but wait for experts confirm ! .. 
Or open a new Post...

---

### Post by cariboo on 2010-09-28
It would probably be better to fire up synaptic and check the broken packages filter, and remove what it suggests before trying to fix the problem.

---

