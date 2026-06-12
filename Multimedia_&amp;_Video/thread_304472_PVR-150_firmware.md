---
title: "PVR-150 firmware"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by k5corral on 2006-11-21
Hello.
This is my first post as a new (delighted) Ubuntu user.  I have configured my system (dual boot separate hard drives) and learned some of the basics, xorg.conf edits for my dual monitors, adding repositories, etc.  (such fun!) Now I'm trying to get mythtv to work with my pvr-150 and learned that I need to update the firmware on my card.  

My question is this:  If I install the pvr-150 linux firmware, will my card remain usable in WinXP?  Or will it now only work in Ubuntu?
Sorry if this has been asked before but I've been "Googling" for an hour with no answer! 

Thanks in advance.

---

### Post by k5corral on 2006-11-29
Come on guys!  I'm chomping at the bit to finish setting up mythtv but cannot find out if updating the firmware on my Hauppauge PVR-150 with the linux firmware will ruin the card for use in Windows.  I dual boot, although I am enjoying my new Ubuntu experience and rarely go into Windows lately... (except to webcam or record on my pvr-150).

ANYONE???

---

### Post by Johan! on 2006-11-29
When you shutdown or reboot your computer, the firmware will be gone.

The Windows driver does exactly the same: it uploads some firmware every time you boot to use the card.

---

### Post by Yorn on 2006-11-29
The answer you are looking for is no, it doesn't actually overwrite the firmware. I'm still trying to figure out why they even call it that.

I have a similar problem with my PVR 150, only it is that I've followed the guide, trying all three installation options and it does not install ivtv.

The following is a log of what I'm doing for each option and the errors I get:

**Debian Archive from ivtvdriver.org (Option 1)**
[INDENT]myth@mythtv:~$ sudo nano /etc/apt/sources.list
myth@mythtv:~$ wget [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg) -O- | sudo apt-key add -
--20:47:42--  [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg)
           => `-'
Resolving dl.ivtvdriver.org... 130.133.35.30
Connecting to dl.ivtvdriver.org|130.133.35.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,690 (1.7K) [text/plain]

100%[========================================>] 1,690         --.--K/s             

20:47:42 (36.63 MB/s) - `-' saved [1690/1690]

OK
myth@mythtv:~$ sudo apt-get install ivtv-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ivtv-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 120kB of archives.
After unpacking 164kB of additional disk space will be used.
Get:1 [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) edgy/firmware ivtv-firmware 20061007 [120kB]
Fetched 120kB in 6s (18.0kB/s)                                                     
Failed to fetch [http://dl.ivtvdriver.org/ubuntu/pool/edgy/firmware/ivtv-firmware_20061007_all.deb](http://dl.ivtvdriver.org/ubuntu/pool/edgy/firmware/ivtv-firmware_20061007_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
myth@mythtv:~$ 
[/INDENT]

**Build Debian Archive (Option 2)**
[INDENT]myth@mythtv:~$ wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip) 
--20:49:05--  [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
           => `pvr_1.18.21.22254_inf.zip.2'
Resolving ftp.shspvr.com... 216.234.188.64
Connecting to ftp.shspvr.com|216.234.188.64|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /download/wintv-pvr_250-350/inf ... done.
==> PASV ... done.    ==> RETR pvr_1.18.21.22254_inf.zip ... done.
Length: 593,441 (580K) (unauthoritative)

100%[========================================>] 593,441      191.92K/s    ETA 00:00

20:49:19 (191.45 KB/s) - `pvr_1.18.21.22254_inf.zip.2' saved [593441]

myth@mythtv:~$ export DEBFULLNAME="Mario Limonciello" 
myth@mythtv:~$ export DEBEMAIL="superm1@ubuntu.com"
myth@mythtv:~$ sudo ivtv-make-fwpkg pvr_1.18.21.22254_inf.zip 
ivtv-make-fwpkg: Extracting firmware from pvr_1.18.21.22254_inf.zip
ivtv-make-fwpkg: Firmware is .zip variety
ivtv-make-fwpkg: Firmware version is 1.18.21.22254
ivtv-make-fwpkg: Maintainer: Mario Limonciello <superm1@ubuntu.com>
ivtv-make-fwpkg: package directory "ivtv-firmware-1.18.21.22254" already exists.
ivtv-make-fwpkg: please remove it to continue.
myth@mythtv:~$ sudo dpkg -i ivtv*firmware*deb 
(Reading database ... 93734 files and directories currently installed.)
Preparing to replace ivtv-firmware 1.18.21.22254 (using ivtv-firmware_1.18.21.22254_all.deb) ...
Unpacking replacement ivtv-firmware ...
Preparing to replace ivtv-firmware 1.18.21.22254 (using ivtv-firmware_20061007_all.deb) ...
Unpacking replacement ivtv-firmware ...
dpkg: error processing ivtv-firmware_20061007_all.deb (--install):
 trying to overwrite `/lib/firmware/v4l-cx2341x-init.mpg', which is also in package ivtv-utils
Setting up ivtv-firmware (1.18.21.22254) ...
Errors were encountered while processing:
 ivtv-firmware_20061007_all.deb
myth@mythtv:~$ wget [http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw](http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw) 
--20:49:49--  [http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw](http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw)
           => `v4l-cx25840.fw'
Resolving home.eng.iastate.edu... 129.186.23.45
Connecting to home.eng.iastate.edu|129.186.23.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,264 (14K) [video/unknown]

100%[========================================>] 14,264        --.--K/s             

20:49:49 (259.07 KB/s) - `v4l-cx25840.fw' saved [14264/14264]

myth@mythtv:~$ sudo mv v4l-cx25840.fw /lib/firmware 
[/INDENT]

**TGZ Archive (Option 3)**
[INDENT]myth@mythtv:~$ cd /lib/firmware/
myth@mythtv:/lib/firmware$ sudo wget [http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)
--20:50:56--  [http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)
           => `firmware.tar.gz'
Resolving dl.ivtvdriver.org... 130.133.35.30
Connecting to dl.ivtvdriver.org|130.133.35.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 119,775 (117K) [application/x-gzip]

100%[========================================>] 119,775      158.30K/s             

20:50:58 (157.90 KB/s) - `firmware.tar.gz' saved [119775/119775]

myth@mythtv:/lib/firmware$ sudo tar zxvf firmware.tar.gz
v4l-cx2341x-dec.fw
v4l-cx2341x-enc.fw
v4l-cx2341x-init.mpg
v4l-cx25840.fw
v4l-pvrusb2-24xxx-01.fw
v4l-pvrusb2-29xxx-01.fw
myth@mythtv:/lib/firmware$ sudo rm firmware.tar.gz
[/INDENT]

Option 3 appears to work, then I do the next step:
[INDENT]myth@mythtv:/lib/firmware$ sudo m-a update,prepare

Updated infos about 83 packages
Getting source for kernel version: 2.6.17-10-generic
Kernel headers available in /lib/modules/2.6.17-10-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Done!
myth@mythtv:/lib/firmware$ 
[/INDENT]

Then lastly:
[INDENT]myth@mythtv:/lib/firmware$ sudo modprobe ivtv
FATAL: Module ivtv not found.
[/INDENT]

So of all 3 options, none of them are working. Any advice?

---

