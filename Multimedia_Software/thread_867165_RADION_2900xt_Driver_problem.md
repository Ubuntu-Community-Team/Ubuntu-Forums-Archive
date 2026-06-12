---
title: "RADION 2900xt Driver problem"
date: 2008-07-22
forum: Multimedia Software
---

### Post by Georgiou on 2008-07-22
problem: 
Can't activate my radion 2900xt. i download the correct driver off ati's web site, but when i attempted to execute in Ubuntu, gedit open and say can't read the coding??:confused:

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

if anyone can help it would be appreciated

---

### Post by soxs on 2008-07-22
```
sudo chmod 755 -vf /where/your/ati/driver/is/ati_blah.run
```
This will allow you to execute your code

---

### Post by Georgiou on 2008-07-23
> **soxs said:**
> ```
sudo chmod 755 -vf /where/your/ati/driver/is/ati_blah.run
```
This will allow you to execute your code

sorry i'm and absolute beginner. i  pasted this code in a terminal and this is the out put.(see below)

xxxxxx@linex:~$ sudo chmod 755 -vf /where/your/ati/driver/is/ati_blah.run
[sudo] password for stephen: 
chmod: cannot access `/where/your/ati/driver/is/ati_blah.run': No such file or directory
failed to change mode of `/where/your/ati/driver/is/ati_blah.run' to 0000 (---------)

(I'm assuming that doing something wrong. where exactly do i enter this code?)

THX

---

### Post by Georgiou on 2008-07-23
However, how do get the root directory address. The Ati driver is on my desktop?

i think i know what you mean.
within a terminal i past something like.....

 sudo chmod 755 -vf ati-driver-installer-8-7-x86.x86_64.run??

---

### Post by kajillin on 2008-07-23
right click the ati.run go to properties click the permissions tab, there is a check box that says execute, check it. the file is now an executable

and when people say stuff like "sudo chmod 755 -vf ati-driver-installer-8-7-x86.x86_64.run" in the forums they usually expect u to know to put your files location eg.. /home/georg/desktop/ati-driver-installer-8-7-x86.x86_64.run in the line which they usually dont tell you same goes for most tutorials youll find on the site or the internet. this is why you get the "no such file or directory" error because u need to specify the  file location within the line. an easier way to find your exact file location is to switch to the show location as text in nautilus. its the little pencil on paper in your file browser beside the "address bar", or just right click the file got to properties and the files location will be listed.

hope that made sense

---

### Post by Georgiou on 2008-07-23
Hi kajillin
i was able to make the ati driver file executable. When executing, i see the ati driver going through the extracting process. It reaches a point where a window pops up saying"**You need to run this installer as the Super-user**" any ideas how to do this??

now regarding the terminal input of

xxxxxx@linex:~$ sudo chmod 755 -vf /home/stephen/Desktop/ati-driver-installer-8-7-x86.x86_64.run

the out put i get is 

mode of `/home/stephen/Desktop/ati-driver-installer-8-7-x86.x86_64.run' retained as 0755 (rwxr-xr-x)
(^^not sure what the above means??)

Is it necessary i do both the terminal and the desktop way?

thanks

---

### Post by Georgiou on 2008-07-23
I'm assuming  that the command “sudo” gives me the superuser authority. If this true I feel that I might be entering the directory wrongly...

ie (this what I have, maybe I missing a space or dash or something)
xxxxxx@linex:~$ sudo chmod 755 -vf /home/stephen/Desktop/ati-driver-installer-8-7-x86.x86_64.run

---

### Post by soxs on 2008-07-23
> **Georgiou said:**
> I'm assuming  that the command &#8220;sudo&#8221; gives me the superuser authority. If this true I feel that I might be entering the directory wrongly...

ie (this what I have, maybe I missing a space or dash or something)
xxxxxx@linex:~$ sudo chmod 755 -vf /home/stephen/Desktop/ati-driver-installer-8-7-x86.x86_64.run
Yes, you get superuserricgths for that single command.
For useing linux properly, you will have to know certain comands: like cd, ls, cp, rm, chmod, chown, sh ./programname(tu execute files). Type "man %command%" (replace %command% with one of the list above) to get more info on parameters and howto use.

---

### Post by Georgiou on 2008-07-23
> **soxs said:**
> Yes, you get superuserricgths for that single command.
For useing linux properly, you will have to know certain comands: like cd, ls, cp, rm, chmod, chown, sh ./programname(tu execute files). Type "man %command%" (replace %command% with one of the list above) to get more info on parameters and howto use.

i appreciate your advice, the exact definitions of the commands are a bit complex at the moment. It will take about week or 2  to research and implement.

However, i am unable to execute my ati driver **"ati-driver-installer-8-7-x86.x86_64.run"** using the **"sudo chmod 755 -vf"** at the start. If you could tell me specifically what to type in it would be much appreciated.

---

### Post by Georgiou on 2008-07-23
please help.............

This is as far as i can get. i know i have the right root directory but the problem is i can't run as super user???

stephen@linex:~$ /home/stephen/Desktop/ati-driver-installer-8-7-x86.x86_64.run
Created directory fglrx-install.mu9106
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.512........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.1 and later releases 64-bit
Removing temporary directory: fglrx-install.mu9106

---

### Post by soxs on 2008-07-23
Did you allready install the build dependencies?
If not post (as is):
```
sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
```
afterwards make shure the driver is executable:
```
cd ~/Desktop/
chmod 755 -vf ./ati
``` press tab to komplete the name

run the driver in terminal with su rigths it requires:
```

cd ~/Desktop/
sudo sh ./ati
``` press tab to komplete the name


further steps can be obtained from [http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide) **_(METHOD 2)_**

---

### Post by Georgiou on 2008-07-23
Finally installed:

it was simple 
1. open terminal 
2. type sudo(and your paste your root directory of the installation file)

ie: sudo /home/stephen/Desktop/ati-driver-installer-8-7-x86.x86_64.run
 
however,its not over......](*,)
the ati driver isn't working. i get the following message when attempting to open catalyst control center

[I](there was a problem initizing catalyst control center linux. it could be caused by the following.
-No Ati driver installed, or the ATI driver is not functioning properly
-Please install the ati driver appropriate for ur hardware, or configure using aticonfig)[/I]

any ideas?

Extra info 
-i have the latest version of Ubuntu (the 64bit version)
-graphics card is hd 2900xt 
-obtain the driver from (link bellow)
[http://ati.amd.com/support/drivers/l...64-radeon.html](http://ati.amd.com/support/drivers/l...64-radeon.html)

---

### Post by Georgiou on 2008-07-23
sox, should i uninstall and start again and do it your way. i was typing when u posted your comments. lol

---

### Post by Georgiou on 2008-07-23
> **soxs said:**
> Did you allready install the build dependencies?
If not post (as is):
```
sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
```
afterwards make shure the driver is executable:
```
cd ~/Desktop/
chmod 755 -vf ./ati
``` press tab to komplete the name

run the driver in terminal with su rigths it requires:
```

cd ~/Desktop/
sudo sh ./ati
``` press tab to komplete the name


further steps can be obtained from [http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide) **_(METHOD 2)_**

ok
1. i installed those updates for the build dependencies.
2.next installed ati driver. "(yes with superuser rights executes and installs)

Results: Ati driver not installed properly

..extra info for possible solution........
during the installation process i am given the following options.

option 1. Install driver 8.512 on X.Org 7.1 and later release 64 bit

option 2. Generate distribution specific driver package

should try the generic driver???

---

### Post by soxs on 2008-07-23
Didi you tryy to follow method 2 of the link I posted?

Short explenation of changedirectory aka cd:
cd ../  changes into a dir of higher level
cd ./ changes into the current dir, read: does nothing
cd folderx changes into folder <folderx>.
eg. if you are currently in /home
cd stephen changes your working dir into /home/stephen
you can change multiple dirs at once
being in /home
and typing ./stephen/Desktop
will change to /home/stephen/Desktop
cd /home/stephen/Desktop does the same
now you can work in that directory
like executing your ati driver:
sudo sh ./ati.blah.blah.blah.run


How I got the drivers to work is:
```
sudo apt-get install dkms
cd /blah.blah. (you know how to change dir now)
sudo apt-get install envng-gtk #use this tool to remove the ati driver
sudo sh ./ati.... --buildandinstallpkg Ubuntu/hardy
```
This will create driver packages and in case everything goes fine, it will install them.
If you've done that, plx post the copied configfile your currently using, which will be copied to your desktop with this command(s):
sudo cat /etc/X11/xorg.conf > ~/Deskktop/xorg.conf.txt; sudo chmod 755 ~/Desktop/xorg.conf.txt
I will adjust this for you as far as I can, so you won't run into black/whitescreens(unless there are further problems.)

if you run accross any errors, plx post again.

---

### Post by Georgiou on 2008-07-23
i will deficiently give this a go tonight after i come home from uni. However, before i attempt this, should i uninstall the 
**"non-working"** driver and if so how? thx

---

### Post by soxs on 2008-07-24
Yes you should. Try to remove them with envyng-gtk. And if you are sur to install the latest fglrx driver (8.6 or 8.7) I would suggest you to remove the following things:
DO IT ON YOUR OWN RISK, I AM NOT RESPONSIBLE FOR ANY DAMAGE, but it worked for me more than one time:
```
sudo rm -Rvf /var/lib/dkms/fglrx
```
```
sudo updatedb;locate fglrx.ko
```
remove any fglrx.ko you can find, with:
```
sudo rm -vf /path/to/fglrx.ko
```

---

### Post by Georgiou on 2008-07-25
I stuffed up something socking. I couldn't even boot into Ubuntu and had to reinstall and start fresh.
1.I executed the ati driver file on my desktop (ati-driver-installer-8-7-x86.x86_64.run)
2.chose the option :- Generate distribution specific driver package
3.chose something like  red hat 64...
4.seemed to have install, as catylse was working. However when I went to change the visual effects to Normal. A window popped up saying: "*do you want to replace so and so with the new package"*. I pressed replace everything. Then I rebooted as it ask me too and.....well just a black screen. .........So I reinstalled 
I also installed ennyng and uninstalled the drivers................

ok so now I have a fresh copy of Ubuntu with all the automatic updates

so what should I do 1st  please correct me if I'm wrong:

step 1: Download the 64 bit driver for my 2900xt from the ati website and save to desktop
step 2: install the build dependencies by 
sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
step 3: make sure the file is excutable (ati-driver-installer-8-7-x86.x86_64.run)
 install the drivers......dont know what option to choice........Options are....
[B]
option 1. Install driver 8.512 on X.Org 7.1 and later release 64 bit

option 2. Generate distribution specific driver package
 [/B]
 

[B]

How I got the drivers to work is:
Code:
sudo apt-get install dkms
cd /blah.blah. (you know how to change dir now)
since its a freah install I dont need to remove drivers using envyng
sudo sh ./ati.... --buildandinstallpkg Ubuntu/hardy[/B]

in regard to the above coding should I just attempt to use this if im installing for the first time?
If so the only thing I dont understand is the final line  

“sudo sh ./ati.... --buildandinstallpkg Ubuntu/hardy”

or should I just use enyng to install the drivers.....


I feel I might be overlapping steps could u please clarify. So I can give this anther shot thanks

---

### Post by Georgiou on 2008-07-25
ok this what ive done so far............

**sg@ubn:~$ sudo apt-get update**
[sudo] password for sg: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
**sg@ubn:~$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debconf is already the newest version.
dkms is already the newest version.
linux-headers-2.6.24-19-generic is already the newest version.
linux-headers-2.6.24-19-generic set to manually installed.
The following extra packages will be installed:
  autoconf automake1.7 autotools-dev dpkg-dev fdupes g++ g++-4.2 gcc-3.3-base
  gettext html2text intltool intltool-debian libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev m4 patch po-debconf
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc devscripts
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  cvs gettext-doc glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
Recommended packages:
  automaken libmail-sendmail-perl libcompress-zlib-perl libmail-box-perl
The following NEW packages will be installed:
  autoconf automake1.7 autotools-dev build-essential cdbs debhelper dh-make
  dpkg-dev fakeroot fdupes g++ g++-4.2 gcc-3.3-base gettext html2text intltool
  intltool-debian libc6-dev libstdc++5 libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev m4 patch po-debconf
0 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.9MB of archives.
After this operation, 51.9MB of additional disk space will be used.
**Do you want to continue [Y/n]? y**
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main m4 1.4.10-1 [250kB]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main autoconf 2.61-4 [448kB]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main autotools-dev 20070725.1 [61.9kB]
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main automake1.7 1.7.9-9 [391kB]      
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.36 [696kB]
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [2538kB] 
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]  
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1450B]
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main patch 2.5.9-4 [97.8kB]          
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]
Get:14 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main html2text 1.3.2a-3build2 [91.3kB]
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main gettext 0.17-2ubuntu1 [2067kB]  
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:17 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main po-debconf 1.0.10 [232kB]       
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main debhelper 6.0.4ubuntu1 [516kB]  
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main fdupes 1.40-4build1 [15.5kB]    
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main intltool 0.37.1-1ubuntu1 [85.8kB]
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main cdbs 0.4.51ubuntu1 [964kB]      
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main dh-make 0.44ubuntu1 [37.0kB]    
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main fakeroot 1.9ubuntu1 [116kB]     
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe gcc-3.3-base 1:3.3.6-15ubuntu6 [151kB]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe libstdc++5 1:3.3.6-15ubuntu6 [292kB]
Fetched 13.9MB in 18s (736kB/s)                                                
Selecting previously deselected package m4.
(Reading database ... 95534 files and directories currently installed.)
Unpacking m4 (from .../archives/m4_1.4.10-1_amd64.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070725.1_all.deb) ...
Selecting previously deselected package automake1.7.
Unpacking automake1.7 (from .../automake1.7_1.7.9-9_all.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.36_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_amd64.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_amd64.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_amd64.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package fdupes.
Unpacking fdupes (from .../fdupes_1.40-4build1_amd64.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.37.1-1ubuntu1_all.deb) ...
Selecting previously deselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.51ubuntu1_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../dh-make_0.44ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.9ubuntu1_amd64.deb) ...
Selecting previously deselected package gcc-3.3-base.
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu6_amd64.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu6_amd64.deb) ...
Setting up m4 (1.4.10-1) ...

Setting up autoconf (2.61-4) ...

Setting up autotools-dev (20070725.1) ...
Setting up automake1.7 (1.7.9-9) ...

Setting up linux-libc-dev (2.6.24-19.36) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up html2text (1.3.2a-3build2) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up fdupes (1.40-4build1) ...
Setting up intltool (0.37.1-1ubuntu1) ...
Setting up cdbs (0.4.51ubuntu1) ...

Setting up dh-make (0.44ubuntu1) ...
Setting up fakeroot (1.9ubuntu1) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu6) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu6) ...

Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
sg@ubn:~$ sh ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/hardy
sh: Can't open ati-driver-installer-8-7-x86.x86_64.run
sg@ubn:~$ sh ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/hardy
sh: Can't open ati-driver-installer-8-7-x86.x86_64.run
sg@ubn:~$ sudo sh ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/hardy
sh: Can't open ati-driver-installer-8-7-x86.x86_64.run
sg@ubn:~$ 
**(what am i doing wrong here)**

---

### Post by markbuntu on 2008-07-25
Follow the directions here VERY CAREFULLY:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

It has just been updated for the 8.7 driver. There are special instructions for the amd64. Read them through before you do anything. 

These guys have never let me down. I have been following this guide since 8.4 and it works for both my 32 and 64 bit installs.

---

### Post by Georgiou on 2008-07-27
i give up this is just to hard and I've wasted too much time. I'm going back to windows for a while.............:(

---

### Post by soxs on 2008-07-29
> **Georgiou said:**
> i give up this is just to hard and I've wasted too much time. I'm going back to windows for a while.............:(

Did you cachnege via cd ~/Desktop to your Desktop where the installer should be?

Did you make it executable (after changing dir) via ```
chmod 755 -vf ./ati..
```

---

