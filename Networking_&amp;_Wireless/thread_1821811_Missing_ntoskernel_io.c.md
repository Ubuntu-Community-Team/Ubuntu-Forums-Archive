---
title: "Missing ntoskernel_io.c"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by Kimse73 on 2011-08-09
Dear all.
 
This is my fourth night trying to solve problems through already posted similar situations; now I have to try this forum in stead of discontinuing Ubuntu.
 
First: I'm a newbie on Linux - please bare with me if reposting.
 
I have an old Win XP (Dell Dimension 8300); the physical place of installation makes a wired connection impossible. I decided to get the PC airborne, and bought a Netgear N300 (WNA3100). The Win OS has not been updated for some time, and there were a missing 'something' to connect with WPA2-personal - and hey why not try Linux.
 
Now - I finally got to the point where I was ready to try and follow some of the workarounds described on the net. One of them was to add some lines to [COLOR=red]*ntoskernel_io.c*[/COLOR] and then compile it. I don't have that file on my system... 
When I in desperation try to run different options with [COLOR=red]*ndiswrapper*[/COLOR] - just to get a result, the results are erroneous.
 
Please help - next move is to bow down and return to some win OS; the same, that I try to get away from...
 
BR Kim

---

### Post by chili555 on 2011-08-09
Before we re-compile ndiswrapper, a scary process but fun nonetheless, let's check one thing first. Ndiswrapper requires the Windows XP driver .inf and, probably, .sys files. Are you certain that's the files you used? 7, Vista, 95 or 3.1 just won't work.

Second, in order to re-compile ndiswrapper, you need to download the source code and start from scratch. The version installed on your system now is already compiled for Ubuntu and your exact kernel version. The .c file you mentioned therefor doesn't appear on your system.

If it comes down to re-compiling, you'll need the packages build-essential and linux-headers installed. I think they're either already installed or available on the install CD. Please open Synaptic Package Manager and have a look.

There are several versions of this device; please plug it in and run and post:```
lsusb
```

---

### Post by Kimse73 on 2011-08-09
Dear Chili555 - thank you for reposting.
 
The output for lsusb:
 
.....
Bus 001 Device 004: ID 0846:9020 NetGear, Inc.
.....
 
In Synaptic Package Manager (under Networking) there is no 'ndiswrapper' present. Is this what i'm looking for?

---

### Post by chili555 on 2011-08-09
> In Synaptic Package Manager (under Networking) there is no 'ndiswrapper' present. Is this what i'm looking for? Nope. Under All, you are looking for the packages build-essential and linux-headers-generic. If they are not installed, drop the Ubuntu install CD in the tray and go to Settings > Repositories and add the CD as a source. Press Relaod so that Synaptic re-indexes the packages on the CD and then see if build-essential and linux-headers-generic are available and install them.

Were your .inf and .sys from Windows XP?

Post #71 here is approximately what we're going to do: [http://ubuntuforums.org/showthread.php?t=1549190](http://ubuntuforums.org/showthread.php?t=1549190)

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

---

### Post by Kimse73 on 2011-08-09
Thanx for your patience.
 
The 'build-essential' is **not** present
The 'linux-headers-generic' is present.
 
The system returns: [COLOR=red]*'E:Failed to mount the cdrom' *[/COLOR][COLOR=black]when trying to add install-CD as source.[/COLOR]

---

### Post by chili555 on 2011-08-09
> The system returns: 'E:Failed to mount the cdrom' when trying to add install-CD as source.When you inserted the CD, did a little icon appear on the desktop indicating it automounted? Right-click the icon and select Unmount. Let Synaptic try again. I think it wants to look for and mount the CD, not automount.

I just followed the steps at post #71 I linked and it makes and installs oh so perfectly! I will need to guide you a bit, so don't get too far ahead of yourself. I know you are anxious to earn your geekhood, but please be patient.

---

### Post by chili555 on 2011-08-09
So, did you find build-essential?

---

### Post by Kimse73 on 2011-08-09
Only way of unmouting is through 'Disk Utility' - but now unmounted and added.
 
When marking build-essential for installing, it (the system) markes 8 packages in total for installation:
 
build-essential
dpkg-dev
fakeroot
g++
g++-4.4
libstdc++6-4.4-dev
patch
xz-utils
 
24,6 MB to be used; none to be downloaded. So I hit apply, and...
... it comes with a message: "Some of the files could not be retrieved from the servers... ... contonue? (YES - of course)
 
.. and 8 packages failed :-( 
Where did I fail?

---

### Post by chili555 on 2011-08-09
If those packages are on the CD, it ought to have found them and installed them. Did you press Reload? If you search for each of the packages individually, do you see them? Can you install them one by one? If we get down to missing just one or two, we can go to the package site and put them on a USB drive.

---

### Post by Kimse73 on 2011-08-09
I can't install one at the time.. 
 
When hitting the 'reload' the system comes with errors: " ... could not resolve 'dk.archive.ubuntu.com' and 'security.ubuntu.com' " 
 
Since it also told me that nothing was to be downloaded I felt home safe.... 
Aparently I wasn't ;)
 
I will make another try tomorrow - including making another installation disc. I'd prefer downloading instructions if there is alternatives to ubunto.com - or if there's checkmarks that I need to pay attention to. 
 
It's way past midnight here, so I have to get some sleep. Thanks for your patience - I will not give up on Ubuntu just yet; now you got me into geek-mode :P. I will do as instructed, repost and wait for further instructions. 
 
Thanks again for now.
 
/ Kim

---

### Post by chili555 on 2011-08-09
I will post instructions. Look for complete HOWTO tomorrow.

When I awake, I hope I read: SOLVED.

Have a great evening!

---

### Post by chili555 on 2011-08-09
I believe all the needed packages are on the install CD except one. Load the CD in the tray and allow it to automount. Click the icon and open the CD. Double-click Pool and, for g++, double-click Main and G. g++ and libstdc++-dev are in there. Right-click each and select Open with Software Center and install. Continue for the other packages until everything except xz-utils is installed. Grab a USB key and on another computer go here: [http://packages.ubuntu.com/natty/xz-utils](http://packages.ubuntu.com/natty/xz-utils) 

Download either the i386 version or 64-bit version as appropriate. Next, go here and download ndiswrapper-1.56: [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/) Drag and drop it to your desktop. Right-click it and extract Extract Here. Open the folder and then open the folder *driver*. Add these lines to the end of the file "ntoskernel-io.c"
```
wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
    (void *tag)
{
    TRACE2("%p", tag);
    TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
    IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
}
```
Proofread carefully, save and close the text editor. Download these patches and drag and drop them into the ndisrwpper -1.56 folder:

    [http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch](http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch)
    [http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1](http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1)

Now open a terminal and do:```
cd Desktop/ndiswrapper-1.56
patch -Np0 < ndiswrapper-suse.patch
patch -Np0 < ndiswrapper-1.56-2.6.35.patch?revision=1.1
```
In order to get no errors during compiling, you need to change a few lines in "wrapndis.c".
Change this:
```
#include "ndis.h"
#include "iw_ndis.h"
#include "pnp.h"
#include "loader.h"
#include "wrapndis.h"
#include <linux/inetdevice.h>
#include <linux/ip.h>
#include <linux/tcp.h>
#include <linux/udp.h>
#include <linux/in.h>
#include "wrapper.h"

```
to this:
```
#include <linux/inetdevice.h>
#include <linux/ip.h>
#include <linux/tcp.h>
#include <linux/udp.h>
#include <linux/in.h>
#include "ndis.h"
#include "iw_ndis.h"
#include "pnp.h"
#include "loader.h"
#include "wrapndis.h"
#include "wrapper.h"
```

It is easiest to copy and paste the latter text below the earlier text and then remove the earlier text. Proofread carefully, save and close the text editor.

Now compile it:

```
make
sudo make install
```

Install the bcmwlhigh5.inf, do:
```
sudo ndiswrapper -i bcmwlhigh5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Now the WNA3100 should work.

Post back if you get an error or get stuck.

---

### Post by Kimse73 on 2011-08-10
I've had a really hard time installing the packages - but now I succeeded (i guess :-)
 
There is no such thing as a software center - and when trying to install through GDebi Package installer it failed.
 
Disk won't mount in Synaptic - claiming CD is not present. Then I found, that the system was looking for a drive E - but in Disk utility it was mounted at /media/apt (first /media/Ubuntu 10.04...) but system changed its name suddently. 
 
Could it have something to with the CD/DVD connection (SCSI !) 
 
Anyway...
I then found, that i could instal it in reverse order by checking only one (maybe two) in symantec, and manually point out "Add downloaded packages" from the file menu in Synaptic.. 
 
Took some time, but now I'm there. 
 
You told me to download from 'Natty' - but I'm in 10.04, so I downloaded from Lucid instead - but then again... Found it on the CD, so i used that one.
 
I will continue tomorrow (if the family lets me ;-) - and then repost and wait 'till you have the time for further support. If you run out of tolerance with me I understand :P
 
Best regards from Denmark
 
/ Kim

---

### Post by chili555 on 2011-08-10
> I will continue tomorrow (if the family lets me - and then repost and wait 'till you have the time for further support. I will look forward to your posts. We have quite a time zone difference, so I will respond as soon as I can.

I'm glad you got the packages installed by whatever means. I'm sorry I misinterpreted and thought you were on Natty! I'm confident you will succeed.

---

### Post by Kimse73 on 2011-08-11
To me you're an ubuntu god - so far ;-)
 
Everything turned out good - no errors... But...
 
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] sudo ndiswrapper -i bcmwlhigh5.inf
couldn't open bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

I then found the .inf & .sys file for bcmwlhigh5 in the WinXP-section of the hard drive, dragged them onto the desktop, and dropped them in the ndiswrapper-1.56 folder, and started again:
 
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] sudo ndiswrapper -i bcmwlhigh5.inf
[sudo] password for kpw: 
installing bcmwlhigh5 ...
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper.conf ...
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL]
 
Warnings - but no errors...
Restarted system (several times - with different physical locations of the USB module), and I'm still not able to connect to the network.
 
Now I leave the physical setup as it is, and wait for further instructions...
 
The configuration output, I think you might ask for, is as follows:
 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh5 : driver installed 
device (0846:9020) present
 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] 
 
So far so good.
 
All the best - I'm really looking forward to your reply. 
 
/ Kim

---

### Post by chili555 on 2011-08-11
Well, you have done very well so far. The warnings are trivial and easily fixable. Let's troubleshoot the connection first. Do you see networks when you click the Network Manager icon? Do you have a wireless interface, wlan0, possibly?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```Are there any interesting clues here?```
dmesg | grep ndis
```I feel like you are very close!

---

### Post by Kimse73 on 2011-08-12
Hi again chili555
 
First: No I don't see any wireless networks in the 'Network Connections' window (is it called windows here?)
 
Last night I tried to configure manually. Th results were disappointing ;-)
 
 
The outputs you asked for + bonus:
 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] dmesg | grep ndis
[ 2089.034421] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 2089.352836] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[ 2089.353108] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[ 2089.353755] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[ 2089.353808] usbcore: registered new interface driver ndiswrapper
 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-33-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL]

Checked /var/log/messages for loadndisdriver:
 
Aug 12 21:37:00 kpw-ubuntu loadndisdriver: loadndisdriver: load driver(358): couldn't load driver bcmwlhigh5
 
*_Date and time is not correct._*
 
Somewhere else in the log it states: 
 
kpw-ubuntu kernel: [    41.396017] usb 1-3: new high speed USB device using ehci_hcd and address 4
kpw-ubuntu kernel: [    41.531362] usb 1-3: configuration #1 chosen from 1 choice
 
*_- just because I stumbled over it in curiosity ..._*
 
 
Lokking forward to your reply..
 
 
Best regards
 
/ Kim

---

### Post by Kimse73 on 2011-08-12
353755] ndiswrapper (load_wrap_driver:10:cool:: couldn't 
 
should be read as **... load_wrap_driver: 1 0 8 ): couldn't ....**
 
load driver(35:cool:: couldn't 
 
should be read as **... load driver( 3 5 8 ): couldn't ....**
 
 
- without spaces of course...

---

### Post by chili555 on 2011-08-12
> unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'I'm fairly confident that's the source of the error.

I also notice in my instructions:> Next, go here and download ndiswrapper-[COLOR="Red"]**1.56**[/COLOR]: [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)However, your syslog says:> ndiswrapper version [COLOR="Red"]1.55[/COLOR] loaded (smp=yes, preempt=no)Did the compile process not go as expected? Are you sure you completely removed the old version?

---

### Post by Kimse73 on 2011-08-12
I don't know what to say...
 
I did download from your instructions, transferred first to a USB memory stick and then to the Ubuntu desktop and extracted - to do the alterations as you described.
 
If I'm sure, that I removed the old one? Nope... 
How should I do this? I can't figure out what i have missed from your instructions?
 
The compile process did go well - and no errors... Thought the new one would overwrite the old.
 
If I should remove the old one manually before installing, could you then please tell me how to? - and then where to start over from...
 
Best regards
 
/ Kim

---

### Post by chili555 on 2011-08-12
I'd open Synaptic and look for ndiswrapper and mark for removal all items that show version 1.55 only. Then do:```
cd Desktop/ndiswrapper-1.56
make
sudo make install
```Then check the version:```
ndiswrapper -v
```On my Natty system, it *did* over-write the defauly Ubuntu version. I was myself surprised to see the result from your syslog.

---

### Post by Kimse73 on 2011-08-12
I will - of course - do as you say, but one question first.
 
I opened the change log of ndiswrapper-1.56, where it says to use /etc/modprobe.d/ndiswrapper.conf, not /etc/modprobe.d/ndiswrapper
 
Both files are present in /etc/modprobe.d/
 
Is it as simple as to remove the one we shouldn't use - and the recompile?

---

### Post by Kimse73 on 2011-08-12
In Synaptic there are two items:
 
ndiswrapper-common
ndiswrapper-utils-1.9
 
For both files is the shown installed version **1.54-2ubuntu1**
 
Now I'm really confused...

---

### Post by chili555 on 2011-08-12
> Both files are present in /etc/modprobe.d/I think I'd compare them with sudo gedit. I suspect they are identical. If so, remove the one without .conf.> ndiswrapper-common
ndiswrapper-utils-1.9

For both files is the shown installed version 1.54-2ubuntu1
Yikes! I think I would mark both for complete removal and click Apply. Then install from the file you downloaded. After I did that, I get:```
$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.38-10-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
[COLOR="Red"]version:        1.56[/COLOR]
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 

```

---

### Post by Kimse73 on 2011-08-12
Comparison:
 
/etc/modprobe.d/ndiswrapper  **is empty**
 
/etc/modprobe.d/ndiswrapper.conf   **only contains: **alias wlan0 ndiswrapper
 
I tried to remove the one without .conf - but I'm not allowed to do anything from the file browser. How do I remove it correctly from terminal?
 
Both ndiswrapper... files are uninstalled now (from Synaptic)
 
I suppose that I install the new ones with the make / make install you told me earlier ?

---

### Post by chili555 on 2011-08-12
> I tried to remove the one without .conf - but I'm not allowed to do anything from the file browser. How do I remove it correctly from terminal?Please do:```
sudo rm /etc/modprobe.d/ndiswrapper
```> Both ndiswrapper... files are uninstalled now (from Synaptic)

I suppose that I install the new ones with the make / make install you told me earlier ? Yes, please proceed.

---

### Post by Kimse73 on 2011-08-12
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] sudo rm /etc/modprobe.d/ndiswrapper
sudo: timestamp too far in the future: Aug 12 21:38:10 2011
[sudo] password for kpw: 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] cd desktop/ndiswrapper-1.56
bash: cd: desktop/ndiswrapper-1.56: No such file or directory
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] cd desktop
bash: cd: desktop: No such file or directory
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] cd desktop/
bash: cd: desktop/: No such file or directory
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] cd Desktop/ndiswrapper-1.56
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] make
make -C driver
make[1]: Entering directory `/home/kpw/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.32-33-generic M=/home/kpw/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make[1]: Leaving directory `/home/kpw/Desktop/ndiswrapper-1.56/driver'
make -C utils
make[1]: Entering directory `/home/kpw/Desktop/ndiswrapper-1.56/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/kpw/Desktop/ndiswrapper-1.56/utils'

[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] sudo make install
make -C driver install
make[1]: Entering directory `/home/kpw/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.32-33-generic M=/home/kpw/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
echo /lib/modules/2.6.32-33-generic/misc
/lib/modules/2.6.32-33-generic/misc
mkdir -p /lib/modules/2.6.32-33-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.32-33-generic/misc
/sbin/depmod -a 2.6.32-33-generic -b /
make[1]: Leaving directory `/home/kpw/Desktop/ndiswrapper-1.56/driver'
make -C utils install
make[1]: Entering directory `/home/kpw/Desktop/ndiswrapper-1.56/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo
NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/kpw/Desktop/ndiswrapper-1.56/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8

[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-33-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
[EMAIL="kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$"]kpw@kpw-ubuntu:~/Desktop/ndiswrapper-1.56$[/EMAIL] 

 
From a quick view in Synaptic - there is no ndiswrapper-files installed... 
 
.... Still confused ;-)

---

### Post by chili555 on 2011-08-12
I am working a hunch here, so please bear with me. Reboot and do:```
ndiswrapper -v
dmesg | grep ndiswrapper
```Thanks.

---

### Post by Kimse73 on 2011-08-12
Ok - I'll do, but a question first..
 
 
I just went through the earlier posts - and in #12 the last thing you told me to do was 
 
sudo modprobe ndiswrapper
 
Should I run 
 
sudo modprobe ndiswrapper**.conf** instead?

---

### Post by chili555 on 2011-08-12
> **Kimse73 said:**
> Ok - I'll do, but a question first..
 
 
I just went through the earlier posts - and in #12 the last thing you told me to do was 
 
sudo modprobe ndiswrapper
 
Should I run 
 
sudo modprobe ndiswrapper**.conf** instead?No. When you modprobe, you load a driver module. Many drivers need a configuration file that tells it what to do now that it's loaded. Many driver modules have the devices written into the module itself, for example:> $ modinfo e100
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/net/e100.ko
firmware:       e100/d102e_ucode.bin
firmware:       e100/d101s_ucode.bin
firmware:       e100/d101m_ucode.bin
version:        3.5.24-k2-NAPI
license:        GPL
author:         Copyright(c) 1999-2006 Intel Corporation
description:    Intel(R) PRO/100 Network Driver
srcversion:     CA8851CBD54453A98F5FAB4
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]27DC[/COLOR]sv*sd*bc02sc00i*
alias:          pci:v00008086d0000245Dsv*sd*bc02sc00i*
alias:          pci:v00008086d00002459sv*sd*bc02sc00i*
alias:          pci:v00008086d00002449sv*sd*bc02sc00i*However, since ndiswrapper can use, I'd guess, any wireless device, the vendor and product id must be declared in ndiswrapper.conf; in your case, 0846:9020. That way, when the computer boots, the device starts ndiswrapper.

The driver module and the .conf file are two separate but related items.

---

### Post by Kimse73 on 2011-08-12
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-33-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] dmesg | grep ndiswrapper
[EMAIL="kpw@kpw-ubuntu:~$"]kpw@kpw-ubuntu:~$[/EMAIL] 
 
*[COLOR=red]... and I didn't remove any lines....[/COLOR]*
[COLOR=black][/COLOR] 
First a simple reboot - and then a complete system shutdown. Same result...
 
In Synaptic there is still no ndiswrapper installed. The only visible is the two previously installed versions (1.54-2ubuntu1). They are still uninstalled...

---

### Post by Kimse73 on 2011-08-12
I opened a File Browser, and searched for 'ndiswra'
 
There are two 'ndiswrapper' folders with location
 
**/lib/modules/2.6.32-33-generic/kernel/ubuntu **
with content of only: ndiswrapper.ko
 
**[COLOR=red]and[/COLOR]**
 
**/usr/src/linux-headers-2.6.32-33/ubuntu**
with content of:
Kconfig
Makefile
mkexport.sh
mkstubs.sh
 
Both of the above were shown with a lock-symbol when opened in file browser. The symbol disappeared after first open.
 
**Besides that**, there is a 'ndiswrapper' folder with location
 
**/etc/**
with content of a
**bsmwlhigh5 folder**, containing 
0846:9020.F.conf
bcmwlhigh5.inf
bcmwlhigh5.sys
 
**... and then, there is the folder ndiswrapper-1.56**
on the **D**esktop...
... containing all the files mentioned yesterday - including the .inf and .sys that i dragged and dropped into the folder to compile / make.
 
This might be good information to you - in order to figure out what's happening on my PC, which seem to be juvenile all over ;-)
 
 
Please don't work too hard for me - it's not a matter of life and death...
 
Best regards
 
/ Kim

---

### Post by Kimse73 on 2011-08-13
Dear Chili555.
 
Since I had nothing to lose, i tried to follow your instructions from post #12 when booting in Natty (which I started from).
 
I downloaded the ndiswrapper-1.56 from the Lucid desktop to the Natty desktop, and did what you told me to.
 
**BANG - SOLVED ;-)**
 
I'm networking now.... I don't know what went wrong and why, and actually - I don't really care. Your post really helped me, and I bow to you in honour ;-)
 
**BUT....**
 
Now I need to re-partition the disk. I now have 3 partitions on the disk- the original WinXP, Natty & Lucid. I'd like to remove Lucid and hand over the disk-space to Natty. Can you help me with that - or could you help me to the right forum for this type of question.
 
If I can help you in any way by keeping Lucid for a while I'll do so!!! 
 
And if I could - I'd share my cold beer with you... I'm really looking forward to your reply. Have a great weekend.
 
/ Kim

---

### Post by chili555 on 2011-08-14
> **BANG - SOLVED**Aside from, "May I offer you a beer?" those are my favorite words in the whole world! I am very glad it's working, by whatever means. First of all, I think it may just be that the latest version of ndiswrapper works best with Natty 64-bit and without the errors you fought. I wonder if you'd be kind enough to summarize the exact solution for the benefit of the searchers. I assume you used ndiswrapper 1.56 and added patches (??) and then used the bcmwlhigh5.inf and accompanying .sys file. 

Also, I wonder if you'd use the thread tools at the top and Mark Solved.

Since you are using a compiled version of ndiswrapper, whenever a newer kernel version, or linux-image as it's known in Ubuntu, is installed by Update Manager, you'll need to recompile against the newer kernel:```
cd Desktop/ndiswrapper-1.56
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
```

As for removing Lucid, it involves using a live CD and re-sizing the partition containing your Natty /home directory right over the entire Lucid partition. Then you redo GRUB so that the boot sequence no longer looks for the non-existent Lucid. The process is well over my pay grade, as several frequent repliers term it, so I suggest you search and post in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Mrs. Chili and I have a Sunday tradition involving beer, chips and salsa. We shall toast your great luck and skill today!

Have fun!

---

### Post by Kimse73 on 2011-08-14
I can't really summarize - but...

Apparently you ask for trouble if you want Netgear WNA3100 to work with Ubuntu 10.04.

**Post #12** in this thread solved mu problems completely **when booting in 11.04**.

During the 'make install' process it came with some errors:

kpw@kimdell8300:~/Desktop/ndiswrapper-1.56$ make install
make -C driver install
make[1]: Entering directory `/home/kpw/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-8-generic M=/home/kpw/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
echo /lib/modules/misc
/lib/modules/misc
mkdir -p /lib/modules/misc
install -m 0644 ndiswrapper.ko /lib/modules/misc
install: cannot remove `/lib/modules/misc/ndiswrapper.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/kpw/Desktop/ndiswrapper-1.56/driver'
make: *** [install] Error 2
kpw@kimdell8300:~/Desktop/ndiswrapper-1.56$


I'm still networking though.... :popcorn:

Is this critical errors - or can I mark as complete and forget the errors?

---

### Post by Kimse73 on 2011-08-14
Error nr. 40 (a user-related error)

Remember the **sudo** before 'make install'

Installed with no errors.


Thanks again - have a great sunday with mrs. Chili - and cheers :D


All the best from Denmark

/ Kim

---

