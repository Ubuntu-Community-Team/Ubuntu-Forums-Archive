---
title: "How to use ndiswrapper and copy .inf and .sys file to ndiswrapper?"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by tom14 on 2013-08-30
Hello guys,being new in Ubuntu world I have some little problems from time to time,or something what seems to be a problem.In order to use my RTL8187 wi-fi with Ubuntu 13.04,I need to install windows driver for it,otherwise connection is terrible.I think,that now I have ndiswrapper installed,and ndisgtk,but I'm not 100%sure.This is the message I get from terminal:```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo modprobe ndiswrapper[sudo] password for tom: 
FATAL: Module ndiswrapper not found.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ ndiswrapper -l
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper.conf ...
sh: 1: cannot create /etc/modprobe.d/ndiswrapper.conf: Permission denied
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ ndiswrapper -v
ERROR: Module ndiswrapper not found.
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: Module ndiswrapper not found.

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get install ndisgtk
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ndisgtk
0 upgraded, 1 newly installed, 0 to remove and 217 not upgraded.
Need to get 0 B/16,9 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Selecting previously unselected package ndisgtk.
(Reading database ... 155993 files and directories currently installed.)
Unpacking ndisgtk (from .../ndisgtk_0.8.5-1ubuntu1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up ndisgtk (0.8.5-1ubuntu1) ...
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```
When I look in computer/usr/sbin I find ndiswrapper,ndiswrapper-1.9,and ndisgtk files but have no idea what to do with it now,and where to copy .inf and .sys winxp files to?I've found sites with instructions,but I still didn't reach that level and it's too complicated for me.Could someone please,give me (and others with the same problem)step by step instruction how to do it?

---

### Post by verymadpip on 2013-08-30
Hi there.
I had major problems with the RTL8187 driver.  Although people say use XP drivers with Ndiswrapper I found Win98 drivers worked much better with RTL8187.  Finding them was a bit of a pain though.
Looks like it's here:
[http://drivers.softpedia.com/progDownload/Realtek-RTL8187-51230-Download-17272.html](http://drivers.softpedia.com/progDownload/Realtek-RTL8187-51230-Download-17272.html)

I also had to use a downloaded version of Ndiswrapper from here:
[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/) - use the stable version.

Then look at answer 14 to install Ndiswrapper
[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)
Use "checkinstall" rather than "make-install".  I've never had a problem if the./configure returns an error.

I found this guide very helpful, regardless of the driver one is installing via Ndiswrapper:
[http://only4geeks.net/using-the-netgear-wpn111-with-ubuntu/](http://only4geeks.net/using-the-netgear-wpn111-with-ubuntu/) 
Just replace any WPN111 related stuff with the RTL8187 stuff.

You may find that you have to run through this process after kernel upgrades, but once you've done it a time or two it's less daunting.

Good luck, it'll all be fine :)

---

### Post by verymadpip on 2013-08-30
I see that in your thread from 4 days ago you've identified your chip as RTL8187L, so I've wasted my time trying to help here.
Good luck buddy.

---

### Post by grahammechanical on 2013-08-30
Have you tried looking for ndiswrapper in the Dash? I installed ndiswrapper through the Ubuntu Software Centre a few months ago as an experiment and I am sure an icon for it appeared in the Dash and clicking on it brought up a GUI that allowed me to browse to the location of the Windows drivers, which in my case were on a DVD.

Regards.

---

### Post by wildmanne39 on 2013-08-30
*Thread moved to **Networking & Wireless**.*

---

### Post by tom14 on 2013-08-30
> **verymadpip said:**
> I see that in your thread from 4 days ago you've identified your chip as RTL8187L, so I've wasted my time trying to help here.
Good luck buddy.
Yes,the chip really is RTL8187L,but driver I've received with it is for RTL8187 and it works just fine with Windows XP,so I presume it must be the same thing with or without L at the end.And as you say,the very same way could be used to install any other driver,same procedure,so I find your post very helpful,and I appreciate it....thanks...

---

### Post by verymadpip on 2013-08-30
Yes, it could well be the same thing as you suggest.
Nevertheless I've found RTL8187L drivers here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true)

The auto installation package contains an XP driver which may work.
As I say my experience with RTL8187 went well with Win98 drivers, which isn't in that bundle.

As an aside, I don't think I've ever had to use the .sys file for anything.

Good luck tom.

---

### Post by varunendra on 2013-08-31
ndiswrapper is usually our last resort, when no native drivers are available. If a native wireless driver is available, it will almost certainly work better than the ndiswrapper one. Please consider the fact that a windows driver installed with ndiswrapper will not and can not perform as good as it does when running on windows natively.

Besides, there is a proprietary driver available which *verymadpip* linked above. There is really no need to mess with ndiswrapper.

If you are not satisfied with the native driver's performance, the first thing you should try is to ask here for help on that, describing in details the problems you are having. If you already tried that and suggested solutions didn't work for you, try the proprietary driver instead. (if having compiling issues with that, please take a look at this post : [http://ubuntuforums.org/showthread.php?t=2170139&p=12768490#post12768490](http://ubuntuforums.org/showthread.php?t=2170139&p=12768490#post12768490)

Like I said, ndiswrapper is and should be the last resort.

---

### Post by tom14 on 2013-08-31
> **varunendra said:**
> ndiswrapper is usually our last resort, when no native drivers are available. If a native wireless driver is available, it will almost certainly work better than the ndiswrapper one. Please consider the fact that a windows driver installed with ndiswrapper will not and can not perform as good as it does when running on windows natively.

Besides, there is a proprietary driver available which *verymadpip* linked above. There is really no need to mess with ndiswrapper.

If you are not satisfied with the native driver's performance, the first thing you should try is to ask here for help on that, describing in details the problems you are having. If you already tried that and suggested solutions didn't work for you, try the proprietary driver instead. (if having compiling issues with that, please take a look at this post : [http://ubuntuforums.org/showthread.php?t=2170139&p=12768490#post12768490](http://ubuntuforums.org/showthread.php?t=2170139&p=12768490#post12768490)

Like I said, ndiswrapper is and should be the last resort.
You're right about ndiswrapper,first I will try to install proprietary RTL8187L driver for Linux which I've found,and downloaded.So now I have tar.gz file but don't know how to install it.Driver already installed was RTL8187 and doesn't work good at all with my RTL8187L chip.I can only hope that fresh driver,once I succeed to install it,shall work better.Could you,please,help me to install it?Thanks a lot...

---

### Post by varunendra on 2013-09-01
> **tom14 said:**
> So now I have tar.gz file but don't know how to install it.
Before attempting any other driver, you must uninstall ndiswrapper and its related files in /etc directory. To do so quickly, open a terminal (Ctrl+Alt+T), and run the following commands in it -
```
sudo modprobe -rfv ndiswrapper
sudo apt-get purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```

Now assuming you have downloaded the correct (RTL8187L) driver file - "**rtl8187L_linux_1041[1].0209.2012.tar.gz**", from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true) (approx 1.8 MB), here's how to compile it -

Before compiling the driver, make sure you have the required headers and libraries installed. To ensure that, get a temporary wired connection, open a terminal (Ctrl+Alt+T) and run the following command in it -
```
sudo apt-get install linux-headers-generic build-essential
```
*(if you can't get a wired connection, we can use a different method to install above)*
Let the command finish its job, then proceed to compiling the driver as follows :

[INDENT]**1)** Copy the downloaded driver file (rtl8187L_linux_1041[1].0209.2012.tar.gz) on your Desktop.

**2)** Right-click the copied file > click "Extract Here". This will extract a folder named "**rtl8187L_linux_1041.0209.2012**" on your desktop.

**3)** Open the file "**r8187.h**" from the "rtl8187" folder within the extracted folder, and insert the following lines after initial comments in it, that is, after line no. 24 (that ends with **....**/)-
```
#ifndef __devinit
#define __devinit
#define __devexit
#endif
```
Proofread, save and close the file.

**4)** Now in the terminal, run the following commands -
```
cd ~/Desktop/rtl8187L_linux_1041.0209.2012
make
sudo make install
```

**5)** Blacklist the native driver to avoid conflict -
```
echo "blacklist rtl8187" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

**6)** Reboot, or manually load the driver (removing the native one) with -
```
sudo modprobe -rfv rtl8187
sudo modprobe -v r8187l
```
Watch out for errors during the whole process, post back if there are any.[/INDENT]

If everything goes fine, please let us know how well it performs. Thank you.

---

### Post by tom14 on 2013-09-01
> **varunendra said:**
> [INDENT] Watch out for errors during the whole process, post back if there are any.[/INDENT]

If everything goes fine, please let us know how well it performs. Thank you.

Here I get some error messages,it probably should be fixed before proceeding?

```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get install linux-headers-generic build-essential
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-29-generic : Depends: linux-image-3.8.0-29-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.8.0-29-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.8.0-29-generic
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.8.0-29-generic
0 upgraded, 1 newly installed, 0 to remove and 214 not upgraded.
3 not fully installed or removed.
Need to get 0 B/12,2 MB of archives.
After this operation, 26,7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 185667 files and directories currently installed.)
Unpacking linux-image-3.8.0-29-generic (from .../linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by varunendra on 2013-09-01
As a routine step, please try the following first -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```
Then try installing the packages again, or "sudo apt-get -f install" if required again. If this doesn't solve the problem, we'll need some more clues.

> **tom14 said:**
> ```

Unpacking linux-image-3.8.0-29-generic (from .../linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb) ...
**[COLOR="#FF0000"]This kernel does not support a non-PAE CPU[/COLOR]**.

```

I'm not sure this should cause any issues, but does your CPU support PAE (Physical Address Extension)? Check your BIOS to see if there is some setting to enable/disable it. If there is, make sure it is enabled. If you can't find such a setting or if it doesn't help, please post the following outputs -
```
cat /proc/cpuinfo | grep model
cat /etc/modprobe.d/sources.list
ls -1 /etc/modprobe.d/sources.list.d
uname -mr
dpkg -l | egrep 'linux-image|linux-headers'
df -h
```

---

### Post by tom14 on 2013-09-01
> **varunendra said:**
> As a routine step, please try the following first -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```
Then try installing the packages again, or "sudo apt-get -f install" if required again. If this doesn't solve the problem, we'll need some more clues.



I'm not sure this should cause any issues, but does your CPU support PAE (Physical Address Extension)? Check your BIOS to see if there is some setting to enable/disable it. If there is, make sure it is enabled. If you can't find such a setting or if it doesn't help, please post the following outputs -
```
cat /proc/cpuinfo | grep model
cat /etc/modprobe.d/sources.list
ls -1 /etc/modprobe.d/sources.list.d
uname -mr
dpkg -l | egrep 'linux-image|linux-headers'
df -h
```OK,I did complete procedure you gave me,compiling went smoothly,but now I get error message in the upper right corner of the desktop (Error:BrokenCount >0).I haven't noticed any improvement with connection,and I'm not sure if fresh driver is installed now or not,because of errors.I think my HP nc8000 doesn't support PAE,I had to use windows and virtualbox in order to install Ubuntu.There is no PAE setting in f10/setup.Here are outputs you requested in your last post.There is so much to read here,and I hope you don't need to read everything,only what's important :-)```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get clean
[sudo] password for tom: 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-29-generic : Depends: linux-image-3.8.0-29-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-29-generic but it is not installed
E: Unmet dependencies. Try using -f.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get update
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring Release.gpg
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring Release
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/main Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/restricted Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/restricted Translation-en
Err http://archive.canonical.com raring Release.gpg                         
  Something wicked happened resolving 'archive.canonical.com:http' (-11 - System error)
Err http://archive.ubuntu.com raring Release.gpg                            
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Ign http://archive.canonical.com raring Release                             
Ign http://archive.canonical.com raring/partner i386 Packages/DiffIndex     
Hit http://archive.canonical.com raring/partner i386 Packages
Ign http://archive.canonical.com raring/partner Translation-en_US
Ign http://archive.canonical.com raring/partner Translation-en
Get:1 http://archive.ubuntu.com raring-updates Release.gpg [933 B]
Get:2 http://archive.ubuntu.com raring-backports Release.gpg [933 B]
Get:3 http://archive.ubuntu.com raring-security Release.gpg [933 B]
Hit http://archive.ubuntu.com raring Release
Get:4 http://archive.ubuntu.com raring-updates Release [40,8 kB]
Hit http://archive.ubuntu.com raring-backports Release
Hit http://archive.ubuntu.com raring-security Release
Ign http://archive.ubuntu.com raring/main Sources/DiffIndex
Ign http://archive.ubuntu.com raring/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com raring/universe Sources/DiffIndex
Ign http://archive.ubuntu.com raring/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com raring/main i386 Packages/DiffIndex              
Ign http://archive.ubuntu.com raring/restricted i386 Packages/DiffIndex        
Ign http://archive.ubuntu.com raring/universe i386 Packages/DiffIndex          
Ign http://archive.ubuntu.com raring/multiverse i386 Packages/DiffIndex        
Hit http://archive.ubuntu.com raring/main Translation-en                       
Hit http://archive.ubuntu.com raring/multiverse Translation-en                 
Hit http://archive.ubuntu.com raring/restricted Translation-en                 
Hit http://archive.ubuntu.com raring/universe Translation-en                   
Hit http://archive.ubuntu.com raring/main Sources                              
Get:5 http://archive.ubuntu.com raring-updates/main Sources [63,1 kB]          
Get:6 http://archive.ubuntu.com raring-updates/restricted Sources [14 B]       
Get:7 http://archive.ubuntu.com raring-updates/universe Sources [72,0 kB]      
Get:8 http://archive.ubuntu.com raring-updates/multiverse Sources [2.264 B]    
Get:9 http://archive.ubuntu.com raring-updates/main i386 Packages [158 kB]
Get:10 http://archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:11 http://archive.ubuntu.com raring-updates/universe i386 Packages [142 kB]
Get:12 http://archive.ubuntu.com raring-updates/multiverse i386 Packages [3.871 B]
Hit http://archive.ubuntu.com raring-updates/main Translation-en               
Hit http://archive.ubuntu.com raring-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com raring-updates/restricted Translation-en         
Hit http://archive.ubuntu.com raring-updates/universe Translation-en           
Hit http://archive.ubuntu.com raring/restricted Sources                        
Hit http://archive.ubuntu.com raring-backports/main Sources                    
Hit http://archive.ubuntu.com raring-backports/restricted Sources              
Hit http://archive.ubuntu.com raring-backports/universe Sources                
Hit http://archive.ubuntu.com raring-backports/multiverse Sources              
Hit http://archive.ubuntu.com raring-backports/main i386 Packages              
Hit http://archive.ubuntu.com raring-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com raring-backports/universe i386 Packages          
Hit http://archive.ubuntu.com raring-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com raring-backports/main Translation-en             
Hit http://archive.ubuntu.com raring-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com raring-backports/restricted Translation-en       
Hit http://archive.ubuntu.com raring-backports/universe Translation-en         
Hit http://archive.ubuntu.com raring/universe Sources                          
Hit http://archive.ubuntu.com raring-security/main Sources                     
Hit http://archive.ubuntu.com raring-security/restricted Sources               
Hit http://archive.ubuntu.com raring-security/universe Sources                 
Hit http://archive.ubuntu.com raring-security/multiverse Sources               
Hit http://archive.ubuntu.com raring-security/main i386 Packages               
Hit http://archive.ubuntu.com raring-security/restricted i386 Packages         
Hit http://archive.ubuntu.com raring-security/universe i386 Packages           
Hit http://archive.ubuntu.com raring-security/multiverse i386 Packages         
Hit http://archive.ubuntu.com raring-security/main Translation-en              
Hit http://archive.ubuntu.com raring-security/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-security/restricted Translation-en        
Hit http://archive.ubuntu.com raring-security/universe Translation-en          
Hit http://archive.ubuntu.com raring/multiverse Sources
Hit http://archive.ubuntu.com raring/main i386 Packages
Hit http://archive.ubuntu.com raring/restricted i386 Packages
Hit http://archive.ubuntu.com raring/universe i386 Packages
Hit http://archive.ubuntu.com raring/multiverse i386 Packages
Ign http://archive.ubuntu.com raring/main Translation-en_US
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring/restricted Translation-en_US
Ign http://archive.ubuntu.com raring/universe Translation-en_US
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://archive.ubuntu.com raring-security/main Translation-en_US
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US
Fetched 484 kB in 1min 24s (5.708 B/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch http://archive.canonical.com/dists/raring/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-11 - System error)

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ cat /proc/cpuinfo | grep model
model        : 13
model name    : Intel(R) Pentium(R) M processor 1.60GHz
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ cat 7etc/modprobe.d/sources.list
cat: 7etc/modprobe.d/sources.list: No such file or directory
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ cat etc/modprobe.d/sources.list
cat: etc/modprobe.d/sources.list: No such file or directory
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ cat /etc/modprobe.d/sources.list
cat: /etc/modprobe.d/sources.list: No such file or directory
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ ls -1 /etc/modprobe.d/sources.list.d
ls: cannot access /etc/modprobe.d/sources.list.d: No such file or directory
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ uname -mr
3.8.0-19-generic i686
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ dpkg -l | egrep 'linux-image|linux-headers'
ii  linux-headers-3.8.0-19                    3.8.0-19.29                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-19-generic            3.8.0-19.29                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-29                    3.8.0-29.42                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29-generic            3.8.0-29.42                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.29.47                            i386         Generic Linux kernel headers
ii  linux-image-3.8.0-19-generic              3.8.0-19.29                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-19-generic        3.8.0-19.29                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-29-generic        3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.29.47                            i386         Generic Linux kernel image
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ dg -h
dg: command not found
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        18G  3,5G   14G  22% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            367M  4,0K  367M   1% /dev
tmpfs            75M  792K   75M   2% /run
none            5,0M     0  5,0M   0% /run/lock
none            375M   76K  375M   1% /run/shm
none            100M   20K  100M   1% /run/user
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by varunendra on 2013-09-01
> **tom14 said:**
> ```

tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ **cat /etc/[COLOR="#FF0000"]modprobe.d[/COLOR]/sources.list**
cat: /etc/modprobe.d/sources.list: [COLOR="#FF0000"]No such file or directory[/COLOR]

```
My bad! It should have been "/etc/apt/sources.list" and "/etc/apt/sources.list.d". But nevermind now, the output of 'apt-get update' gave me sufficient info that I was expecting from these commands.

However, I don't think I fully understand the part about "error message in the upper right corner of the desktop (Error:BrokenCount >0)". Do you get it before or after loading of the GUI?

Also, your currently running kernel is 3.8.0-19-generic, but parts of an upgraded version (3.8.0-29) are also installed. I don't know why the linux-image package for that newer version is missing though. Please try the following -
```
sudo apt-get dist-upgrade
```
..then reboot and run the command -
```
dpkg -l | grep linux-image
```
Do you see "linux-image-3.8.0-29-generic" this time in the outputs? If yes, then you have successfully installed a newer kernel (which under normal circumstances should be done automatically), and then you will need to compile and install the driver again. This time, hopefully with better results.

Post back the situation after trying above, and we'll proceed accordingly.

---

### Post by tom14 on 2013-09-01
> **varunendra said:**
> 
Do you see "linux-image-3.8.0-29-generic" this time in the outputs? If yes, then you have successfully installed a newer kernel (which under normal circumstances should be done automatically), and then you will need to compile and install the driver again. This time, hopefully with better results.

Post back the situation after trying above, and we'll proceed accordingly.
This is what I get in output now:```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get dist-upgrade
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-29-generic : Depends: linux-image-3.8.0-29-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-29-generic but it is not installed
E: Unmet dependencies. Try using -f.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ dpkg -l | grep linux-image
ii  linux-image-3.8.0-19-generic              3.8.0-19.29                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-19-generic        3.8.0-19.29                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-29-generic        3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.29.47                            i386         Generic Linux kernel image
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 
```
The error sign I get is a small red circle with a horizontal white line in the middle.When I open it,it says:"An error occurred,please run Package Manager from the right-click menu or apt-get in terminal to see what's wrong.The error message was:Error:BrokenCount >0.This usually means that your installed packages have unmet dependencies"

---

### Post by varunendra on 2013-09-01
> **tom14 said:**
> ```

The following packages have unmet dependencies:
 linux-image-extra-3.8.0-29-generic : Depends: linux-image-3.8.0-29-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-29-generic but it is not installed
```

What happens if you try to manually try to install it -
```
sudo apt-get install linux-image-3.8.0-29-generic
```

If it fails, post the output of-
```
apt-get install --print-uris linux-image-3.8.0-29-generic
```

---

### Post by tom14 on 2013-09-02
> **varunendra said:**
> What happens if you try to manually try to install it -
```
sudo apt-get install linux-image-3.8.0-29-generic
```

If it fails, post the output of-
```
apt-get install --print-uris linux-image-3.8.0-29-generic
```I did,and this is what I get:```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ sudo apt-get install linux-image-3.8.0-29-generic
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.8.0-29-generic
0 upgraded, 1 newly installed, 0 to remove and 214 not upgraded.
3 not fully installed or removed.
Need to get 0 B/12,2 MB of archives.
After this operation, 26,7 MB of additional disk space will be used.
(Reading database ... 185667 files and directories currently installed.)
Unpacking linux-image-3.8.0-29-generic (from .../linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-29-generic_3.8.0-29.42_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ apt-get install --print-uris linux-image-3.8.0-29-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.8.0-29-generic
0 upgraded, 1 newly installed, 0 to remove and 214 not upgraded.
3 not fully installed or removed.
Need to get 0 B/12,2 MB of archives.
After this operation, 26,7 MB of additional disk space will be used.
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by varunendra on 2013-09-02
> **tom14 said:**
> ```

Need to get **[COLOR="#FF0000"]0 B[/COLOR]/12,2** MB of archives.

```

Doesn't look good to me. It means the required package is already downloaded and available in the cache. Did you run "sudo apt-get clean" command successfully? You can manually browse to **/var/cache/apt/archives** directory to make sure there are no .deb packages in it.

If it is already empty and still apt doesn't want to re-download it again, then the situation is worse and I don't exactly know how to get rid of the broken packages. We may try a few trivial things though.

If the /var/cache/apt/archives directory is already empty, try the following (assuming you are still running kernel 3.8.0-19) -
```
sudo apt-get purge linux-image-extra-3.8.0-29-generic linux-image-generic linux-headers-generic linux-headers-3.8.0-29-generic linux-headers-3.8.0-29
sudo apt-get -f install
sudo dpkg configure -a

```
If these complete without errors, then -
```
sudo apt-get update
sudo apt-get install linux-image-generic linux-headers-generic
```

If none of above fix the error, we may try manually downloading and installing the linux-image-3.8.0-29 package.

**PS:**
This may not be related to your wireless problem, but I suspect some broken packages may be interfering with it.
If you wish, we can directly try troubleshooting the wireless, leaving the rest of the system the way it currently is. Although I'd recommend a fresh install if the above issue doesn't get fixed, since a kernel is the core of the OS and any issue with it is an issue with the whole OS.

---

### Post by tom14 on 2013-09-02
> **varunendra said:**
> Doesn't look good to me. It means the required package is already downloaded and available in the cache. Did you run "sudo apt-get clean" command successfully? You can manually browse to **/var/cache/apt/archives** directory to make sure there are no .deb packages in it.

If it is already empty and still apt doesn't want to re-download it again, then the situation is worse and I don't exactly know how to get rid of the broken packages. We may try a few trivial things though.

If the /var/cache/apt/archives directory is already empty, try the following (assuming you are still running kernel 3.8.0-19) -
```
sudo apt-get purge linux-image-extra-3.8.0-29-generic linux-image-generic linux-headers-generic linux-headers-3.8.0-29-generic linux-headers-3.8.0-29
sudo apt-get -f install
sudo dpkg configure -a

```
If these complete without errors, then -
```
sudo apt-get update
sudo apt-get install linux-image-generic linux-headers-generic
```

If none of above fix the error, we may try manually downloading and installing the linux-image-3.8.0-29 package.

**PS:**
This may not be related to your wireless problem, but I suspect some broken packages may be interfering with it.
If you wish, we can directly try troubleshooting the wireless, leaving the rest of the system the way it currently is. Although I'd recommend a fresh install if the above issue doesn't get fixed, since a kernel is the core of the OS and any issue with it is an issue with the whole OS.Since it doesn't seem that I could overcome PAE issue with this HP nc8000,would lubuntu be a better solution for this pc?I didn't like Ubuntu installation with the help of windows at the first place.But it seemed the only solution for my non-pae pc.Please let me know what would be the best to do.I'd like to use Ubuntu,but if there's some other way to install it,not with the help of windows.Thanks a lot for your time and your wish to help me with this....

---

### Post by varunendra on 2013-09-02
I am not aware of any issues with non-pae CPUs, but then I haven't done any research on it, only speaking from my personal experience. I have run some not too old versions of ubuntu on machines that couldn't even run windows XP properly.

But given the fact that it is an old system, I'd suggest to try Lubuntu 12.04 on it using a live CD, or USB if it supports booting from USB. If having problems with Live booting, post a thread in Installation & Upgrade section of the forum and you'll get plenty of useful advice on troubleshooting that. If it works in live mode, there is no reason why it should have any problems after installation.

I didn't ask earlier, but the current issue maybe a result of the method you used to install it, especially since you mention using VBox for installing it. You should try the live session first, then directly install the OS on the laptop.

---

### Post by tom14 on 2013-09-05
> **varunendra said:**
> 
I didn't ask earlier, but the current issue maybe a result of the method you used to install it, especially since you mention using VBox for installing it. You should try the live session first, then directly install the OS on the laptop.
I was quiet for a few days because I was observing what is going on with my wifi.First of all,I installed xubuntu 12.04,it's just perfect for my non-pae CPU and my laptop.Wifi,most of the time works good for first 30 minutes,if I'm lucky maybe an hour.After that time connection breaks,and there's no way it'll get back,until I reboot.After reboot wifi works again for some time.And I was working also to improve reception,now the link quality  stays most of the time at 87% in accordance to windows xp realtek signal bar.RTL8187 just ain't  work good with linux,I see many others heaving exactly the same issue.I've purchased another wifi adapter with a RT5370 chip and we'll see the performance of this one,but I need to wait for a few weeks for it to arrive.I'll get back to you soon.Until then,thanks a lot for your help and your time....

---

### Post by verymadpip on 2013-09-07
I wouldn't bother trying this until someone else can tell you if this will cause more trouble than it's worth.

I'll say it once more: I had success with Win 98 RTL8187 drivers & ndiswrapper.
Maybe this is the time to try ndiswrapper as a last resort, just while you're waiting for your new adapter?
I was running a 32 bit Lubuntu when I did this, I'm not certain Ndiswrapper even works with 64 bit OSs.

Oh yeah, I wish I'd thought of trying the Realtek proprietary driver myself.  I swear I'm getting more stupid over time.

Good luck Tom, I hope it all comes together for you.

---

### Post by tom14 on 2013-09-07
> **verymadpip said:**
> I wouldn't bother trying this until someone else can tell you if this will cause more trouble than it's worth.

I'll say it once more: I had success with Win 98 RTL8187 drivers & ndiswrapper.
Maybe this is the time to try ndiswrapper as a last resort, just while you're waiting for your new adapter?
I was running a 32 bit Lubuntu when I did this, I'm not certain Ndiswrapper even works with 64 bit OSs.

Oh yeah, I wish I'd thought of trying the Realtek proprietary driver myself.  I swear I'm getting more stupid over time.

Good luck Tom, I hope it all comes together for you.

OK Verymadpip,if you had success with RTL8187 & ndiswrapper,it's about time for me to try it.Yes,I did install realtek proprietary driver to xubuntu in accordance to your instructions,but there was no change in performance after installation.I'm not sure if it tells us anything,but green led on the wifi adapter acts totally different while connected to windows.It goes on and off smoothly and it's very bright,while on ubuntu flashes constantly fast and it's very dim.Anyway,I'll try to install the driver with ndiswrapper.I already installed ndiswrapper,only don't know how to copy .inf file to ndiswrapper.I downloaded RTL driver for windows and extract it to Desktop.Please tell me how to copy .inf drivers file to ndiswrapper....

---

### Post by verymadpip on 2013-09-07
Hi tom, are you running a 32 or 64 bit OS?  I don't think ndiswrapper works with 64 bit systems.
To use the .inf file you need to cd to the extracted win98 drivers folder, or just right click on it & select  "open terminal here" & then run
```
sudo ndiswrapper -i name-of-the-driver.inf
```

However, I think first we need to check that ndiswrapper got installed properly.
Open a terminal & run
```
 ndiswrapper -v
```

If that returns any errors could you post them for us to see.
It may be necessary to install ndiswrapper manually from a downloaded file from here:

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

I'd use the "stable" version personally.
Let's see how we get on with this bit before we go any further.

---

### Post by tom14 on 2013-09-07
> **verymadpip said:**
> Hi tom, are you running a 32 or 64 bit OS?  I don't think ndiswrapper works with 64 bit systems.
To use the .inf file you need to cd to the extracted win98 drivers folder, or just right click on it & select  "open terminal here" & then run
```
sudo ndiswrapper -i name-of-the-driver.inf
```

However, I think first we need to check that ndiswrapper got installed properly.
Open a terminal & run
```
 ndiswrapper -v
```

If that returns any errors could you post them for us to see.
It may be necessary to install ndiswrapper manually from a downloaded file from here:

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

I'd use the "stable" version personally.
Let's see how we get on with this bit before we go any further.
I think I did all of it right,it was easy with your precise instructions.Only I don't know which driver is in use now,maybe I should turn off the driver that comes with linux in order to see some changes?Here is the lsmod,please take a look:```
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
usb_storage            39646  1 
r8187l                143406  0 
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733914  2 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39826  0 
ath5k                 145127  0 
rtl8187                56323  0 
ath                    19387  1 ath5k
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
mac80211              436493  2 ath5k,rtl8187
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  4 
bnep                   17830  2 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178877  4 ath5k,rtl8187,ath,mac80211
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
psmouse                96744  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
serio_raw              13027  0 
eeprom_93cx6           12687  1 rtl8187
smsc_ircc2             28358  0 
shpchp                 32265  0 
irda                  185517  1 smsc_ircc2
parport_pc             32114  1 
video                  19115  0 
crc_ccitt              12627  1 irda
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40180  0 
tg3                   141465  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tom@tom-HP-Compaq-nc8000-DU449EA-ABD:~$ 

```

---

### Post by tom14 on 2013-09-07
I forgot to tell you,it's 32 bit OS,and ndiswrapper -v was with no errors...

---

### Post by verymadpip on 2013-09-07
Hi tom.
I'm going to be honest with you here.  I'm out of my depth now.
It looks to me like there are are lot of wireless related modules there.  I don't know what damage fiddling with them might do.
Maybe you're just going to have to wait for the new adapter :(

I must have been lucky with ndiswrapper.

Good luck.

---

### Post by tom14 on 2013-09-08
> **verymadpip said:**
> Hi tom.
I'm going to be honest with you here.  I'm out of my depth now.
It looks to me like there are are lot of wireless related modules there.  I don't know what damage fiddling with them might do.
Maybe you're just going to have to wait for the new adapter :(

I must have been lucky with ndiswrapper.

Good luck.
You're right verymadpip,I'll just wait for my new adapter,and who knows if it'll work work any better,but if not,it's laptop anyway,it's not suppose to work at one place all the time.Linux is great,I just love it :-)

---

