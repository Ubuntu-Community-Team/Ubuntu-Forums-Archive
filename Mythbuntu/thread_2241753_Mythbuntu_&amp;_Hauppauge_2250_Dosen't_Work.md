---
title: "Mythbuntu &amp; Hauppauge 2250 Dosen't Work"
date: 2014-08-28
forum: Mythbuntu
---

### Post by Walter_Robinson on 2014-08-28
I purchaed the Hauppauge WinTV 4 days ago.  I've invested at leaset 10 hours trying to get it work.  I've followed the instructions on various pages, but I still can't get it to work.  The pages I've copied / pasted include:

[http://ubuntuforums.org/showthread.php?t=751719&page=5&p=7429560#post7429560](http://ubuntuforums.org/showthread.php?t=751719&page=5&p=7429560#post7429560)
[http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490)
[http://askubuntu.com/questions/308695/help-with-hauppauge-wintv-hvr-2250-on-ubuntu-13-04](http://askubuntu.com/questions/308695/help-with-hauppauge-wintv-hvr-2250-on-ubuntu-13-04)

I've attempted it with 12.04 & 14.04, but neither work.  I have a prefernce for 12.04, because I have to backup several DVDs.  What I need is some step by step instructions that i can follow.  Here is my output:

dmesg | grep saa7164
[    4.643553] saa7164 driver loaded
[    4.643974] saa7164[0]: Your board isn't known (yet) to the driver.
[    4.643974] saa7164[0]: Try to pick one of the existing card configs via
[    4.643974] saa7164[0]: card=<n> insmod option.  Updating to the latest
[    4.643974] saa7164[0]: version might help as well.
[    4.643983] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[    4.643986] saa7164[0]:    card=0 -> Unknown
[    4.643988] saa7164[0]:    card=1 -> Generic Rev2
[    4.643990] saa7164[0]:    card=2 -> Generic Rev3
[    4.643993] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[    4.643995] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[    4.643997] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[    4.643999] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[    4.644009] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[    4.644011] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[    4.644013] saa7164[0]:    card=9 -> Hauppauge WinTV-HVR2200
[    4.644016] saa7164[0]:    card=10 -> Hauppauge WinTV-HVR2200
[    4.644555] CORE saa7164[0]: subsystem: 0070:f111, board: Unknown [card=0,autodetected]
[    4.644558] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb400000
[    4.644568] saa7164_initdev() Unsupported board detected, registering without firmware

---

### Post by khPWXxF on 2014-08-29
I have no experience of this card but have used other Hauppauge devices so this is a stab in the dark.
It doesn't need a 'cold boot' does it?  ie clean closedown, remove plug from power socket, press start button to discharge PSU, plug back in then start up.  The T500 only reloads firmware after this procedure and maybe yours is the same.
Phil

---

### Post by uteck on 2014-08-29
Did you try adding any of the configs to the driver as the output recomended?
If you are not sure how, you have to unload the module; modprobe -r saa7164
then load it with the options; modprobe saa7164 card=3

once you find one that works you can add that /etc/modules to make it loads when the system boots.

---

### Post by mikitz on 2014-09-16
I had the exact same dmesg output as you and Gary Buhrmaster over at mythtv.org suggested the card is actually a Hauppauge HVR-2255. It seems that Hauppauge is shipping these under the name 2250 now. Not very nice for those of us who spent all that cash on the card.

Does anyone know if someone is working on an updated driver? The 2255 is not supported yet. Is Steve Toth still around?

---

### Post by Kris_Masker on 2014-10-09
> **mikitz said:**
> I had the exact same dmesg output as you and Gary Buhrmaster over at mythtv.org suggested the card is actually a Hauppauge HVR-2255. It seems that Hauppauge is shipping these under the name 2250 now. Not very nice for those of us who spent all that cash on the card.

Does anyone know if someone is working on an updated driver? The 2255 is not supported yet. Is Steve Toth still around?


I emailed Steve two days ago.  He replied telling me there is a commercial driver available for the 2255 but he's not ready to release anything publicly yet.  So he has done some work on it.

---

### Post by ken41 on 2014-10-10
Hmmmmm......if he's looking for any beta testers or anything I can try on my system.  I orders a 2250 and got a 2255 and can't get it working.  Not happy as I was really needing the additional tuners.

---

### Post by bilkay on 2014-12-09
Any update on the 2255?

---

### Post by bilkay on 2015-01-08
I just received "driver and firmware files" for the hvr-2255 (Beta) from Hauppauge after signing a non-disclosure agreement. This is what I got (after extraction):

hvr-955q-19x5-2255-kernel-3.16-2014-09-16.patch
NXP7164-2010-04-01.1.fw

No README file, no instructions.

I have no idea what to do with the .patch file.

---

### Post by bilkay on 2015-01-09
I tried running (as root) the *.patch file through patch from the directory I downloaded it into. That gave me nothing but errors and questions I didn't know how to answer:

 > $ patch -p1 < *.patch

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/media/common/tveeprom.c b/drivers/media/common/tveeprom.c
|index c7dace6..44d6290 100644
|--- a/drivers/media/common/tveeprom.c
|+++ b/drivers/media/common/tveeprom.c
--------------------------
File to patch:

> $ cat *.patch|patch -p1 -

patching file -
Hunk #1 FAILED at 286.
Hunk #2 FAILED at 351.
Hunk #3 FAILED at 371.
Hunk #4 FAILED at 548.
Hunk #5 FAILED at 696.
5 out of 5 hunks FAILED -- saving rejects to file -.rej
patching file -
Hunk #1 FAILED at 552.
Hunk #2 FAILED at 658.
2 out of 2 hunks FAILED -- saving rejects to file -.rej
patching file -
Hunk #1 FAILED at 49.
Hunk #2 FAILED at 106.
2 out of 2 hunks FAILED -- saving rejects to file -.rej
The next patch would create the file -,
which already exists!  Assume -R? [n]

I'm thinking I should cd to /usr/src/{headers directory} (current is linux-headers-3.13.0-43-generic) to run patch. I'm also thinking it might be better to cd to the next previous kernel (linux-headers-3.13.0-40-generic) in case there's a problem.

I'm just a bit uneasy about doing this and would like confirmation if I'm on the right track.

p.s. I tried running patch from /usr/src/linux-headers-3.13.0-40-generic and it still doesn't find the file to patch. I'm wondering about the "a/" and "b/" in lines 1, 3 & 4 and elsewhere in the .patch file. Should I edit them out before attempting to patch? I tried using -p0, -p1, -p2 and -p3 (as well as --strip=[1-3] and that gave me the same result. There is no file named tveeprom.c anywhere. Could that be the problem? If so, how to correct it?

---

### Post by Henk Poley on 2015-01-10
The "linux-headers" files are only the *.h files. They do not contain any kernel or driver code, header files only describe for other code how to talk with the kernel and driver modules.

You need the kernel sources:
```
sudo apt-get install linux-source-3.13.0
```

They will also be located in /usr/src

---

### Post by bilkay on 2015-01-11
> **Henk Poley said:**
> The "linux-headers" files are only the *.h files. They do not contain any kernel or driver code, header files only describe for other code how to talk with the kernel and driver modules.

You need the kernel sources:
```
sudo apt-get install linux-source-3.13.0
```

They will also be located in /usr/src

Thanks, Henk!

I now see that the actual source code is in a bzipped tar file located in two directories via link. Does it matter from which directory it's untarred?

> $ cd /usr/src
$ ls -l
[other stuff]
drwxr-xr-x  4 root root 4096 Jan 11 06:57 linux-source-3.13.0
lrwxrwxrwx  1 root root   47 Dec  8 15:35 linux-source-3.13.0.tar.bz2 -> linux-source-3.13.0/linux-source-3.13.0.tar.bz2

I would have thought that there'd be separate source code for each version of the 3.13.0 kernel (I have -39, -40 and -43). Obviously, my understanding is sorely lacking. If I untar all the source code and install the patch, what (generally) will I be patching? Can I limit the changes to a particular kernel version?

---

### Post by uteck on 2015-01-11
You have to untar the kernel source, then run the patch to inject the new driver into it, then you have to compile the new patched kernel, then install the new kernel.
There is probability a kernel config in /boot, so you can use reuse that and don't have to worry about how to configure a kernel.

If you've not built a kernel on your system before, there are some packages needed before you can successfully build. You can get these installed with:
sudo apt-get build-dep linux-image-$(uname -r)

It's been awhile since I built a kernel and I am too tired to write up coherent instructions, but I think
the next steps are;
make oldconfig
make deb-pkg

then install the .deb files

---

### Post by bilkay on 2015-01-12
[**[COLOR=#000000]uteck[/COLOR]**]("http://ubuntuforums.org/member.php?u=89580"),

Actually, I have built kernels before - but that was back when it was the only way to get one - and the were only a few megabytes (or was it kilobytes?). I think the whole process was more understandable back then.

Thanks, and get some rest.

---

### Post by rheaj2 on 2015-02-08
bilkay,

Did you get the patch to work?  I now have this card and would very much like to get it working instead of returning it.  If you got it to work, I'll reach out to Hauppauge and see if I can sign the same agreement and get the patch.  How did you go about getting it from them, just using the standard contact form?

Thanks!

---

### Post by bilkay on 2015-02-09
> **rheaj2 said:**
> bilkay,

Did you get the patch to work?  I now have this card and would very much like to get it working instead of returning it.  If you got it to work, I'll reach out to Hauppauge and see if I can sign the same agreement and get the patch.  How did you go about getting it from them, just using the standard contact form?

Thanks!

I haven't had a chance to work on it. I've been away on winter vacation and won't be back for a couple more days. I still haven't nailed down the proper procedure for applying the patch. That's my first order of business when I get back.

Yeah, I used the standard contact form on Hauppauge's site and got a reply telling me about the beta release. They sent a PDF of the vendor's NDA and I had to sign it and send back a scanned copy of the signed form (or I could have faxed it). I let them know I was ticked off about the way they switch models and that I had already returned an unsupported 1265 and "upgraded" to what I thought was a supported 2250.

If you have any success, please post what you did and I'll do the same.

---

### Post by rheaj2 on 2015-02-10
I submitted a request to Hauppauge this morning.  I'll keep you posted on my progress.

---

### Post by bilkay on 2015-02-12
Attempting to follow instructions here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

$ sudo apt-get install dpkg-dev
$ sudo apt-get source linux-image-`uname -r`

I now have the directory linux-source-3.13.0 in /usr/src with the tar file linux-source-3.13.0.tar.bz2.

In the instructions, it says, "If you need to install a patch, read the instructions from the patch provider to learn how to apply it." I asked the Hauppauge rep. if any instructions were provided, and he basically said that I should know how to do it without instructions. I wish I did.

---

### Post by rheaj2 on 2015-02-12
I just sent to NDA back.  I'll let you know what I can figure out.

---

### Post by bilkay on 2015-02-13
Well, I managed to screw things up.

```
 $ cd /usr/src
```

First, I extracted the source from the tar file.

```
$ sudo tar -xf linux-source-3.13.0.tar.bz2
```

Then I attempted to install the patch

```
$ cd linux-3.13.0
$ patch {path to download directory}/hvr-955q-19x5-2255-kernel-3.16-2014-09-16.patch
```

This ran and ran for a long time with no output and no apparent change in anything, so I eventually stopped it thinking maybe I should have added the "-p" option to patch. Also, maybe I should have added the "verbose" option to give a better indication if it was doing anything.

Then I figured I'd just delete the linux-3.13.0 directory and reinstall it from the tar file (forgetting that the tar file was actually a link into the directory I was deleting - majorly stupid).

So next I re-tried:

```
$ sudo  apt-get source linux-image-`uname -r`
```

This time I got a different result. Instead of getting linux-source-3.13.0.tar.bz2, I now have three new files:

linux_3.13.0-45.74.diff.gz
linux_3.13.0-45.74.dsc
linux_3.13.0.orig.tar.gz

Now I'm totally confused.

Correction: In addition to the three files mentioned above, I also got the linux-3.13.0 directory tree.

---

### Post by bilkay on 2015-02-14
Update: I finally got the patch to work:

```
$ cd /usr/src/linux-3.13.0
$ sudo cat {path to downloads directory}/hvr-955q-19x5-2255-kernel-3.16-2014-09-16.patch|patch -p1 --verbose
```

or:

```
$ cd /usr/src/linux-3.13.0
$ xzcat {path to downloads directory}/hvr-955q-19x5-2255-kernel-3.16-2014-09-16.patch.tgz |patch -p1
```

Looks good so far.

It seems that the patch man page is misleading.

---

### Post by rheaj2 on 2015-02-14
I'm working on this today too.  (U/Myth)btuntu ships with the 3.13 kernel, but the documentation from Hauppauge indicates that the patches requires a 3.16 kernel.  Let me know if you get the card to work using the 3.13 kernel you patched.  I'm compiling the 3.16 one now.  I'll let you know my results.

---

### Post by rheaj2 on 2015-02-14
OK, I got the patched kernel installed.  Here what I did.

The 2255 driver apparently requires kernel 3.16.  Ubuntu and Mythbuntu ship with 3.13, so we have to download 3.16, tweak it and compile it.

First, create a starting point to unpack and patch/build everything. This makes for easier cleanup later on.
```
cd ~
mkdir HVR-work
cd HVR-work
```
Create a folder for the Hauppauge patches
```

mkdir H-patches
cd H-patches
```
Put the zip file from Hauppauge into it and uzip it

Download the 3.16 kernel and untar it:
```
cd ~/HVR-work
mkdir linux-3.16
cd linux-3.16
wget https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.16.tar.xz
tar -xvf linux-3.16.tar.xz
```
The kernel does need a few patches, but they are not from Hauppauge.  Download them now. While still in the linux-3.16 directory:

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/0001-base-packaging.patch
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/0002-debian-changelog.patch
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/0003-configs-based-on-Ubuntu-3.16.0-7.12.patch
```

Now apply these patches:

```

patch -p1 < 0001-base-packaging.patch
patch -p1 < 0002-debian-changelog.patch
patch -p1 < 0003-configs-based-on-Ubuntu-3.16.0-7.12.patch

```

You should see a bunch of "patching file debian...." lines of output

Now we need to apply the patch file from Hauppauge.  It shoud be in the ~/HVR-work/H-patches/Linux/Patch directory.  Untar it to get the plain text hvr-{...}.patch file.  

```

cd ~/HVR-work/H-patches/Linux/Patch/
tar -xvf hvr-{....}.xz

```

Copy it to the linux-3.16 directory

```

cd ~/HVR-work/linux-3.16
cp ~/HVR-work/H-patches/Linux/Patch/*.patch .

```

Now try applying the patches:

```

patch -p1 < hvr-{....}.patch

```

You should again see a bunch of "patching file...." lines of output.

Now compile the patched kernel:

```

make olddefconfig

#Adjust the parameter -j with amount of CPUs you have. 
sudo make -j2 INSTALL_MOD_STRIP=1 LOCALVERSION=-hvr-test deb-pkg

```

The build process should have created 5 installation packages.  In my case (32), I got the following files in the ~/HV-work/linux-3.16 directory:

linux-firmware-image-3.16.0-hvr-test_3.16.0-hvr-test-3_i386.deb
linux-headers-3.16.0-hvr-test_3.16.0-hvr-test-3_i386.deb
linux-image-3.16.0-hvr-test_3.16.0-hvr-test-3_i386.deb
linux-image-3.16.0-hvr-test-dbg_3.16.0-hvr-test-3_i386.deb
linux-libc-dev_3.16.0-hvr-test-3_i386.deb

Find yours and change to that directory.  Install them:

```

sudo dpkg -i  *.deb 

```

Copy the firmware file to your firmware directory

```

sudo cp ~/HVR-work/H-patches/Linux/Firmware/HVR\ 22x5/NXP7164-2010-04-01.1.fw /lib/firmware/

```

Reboot, and choose the new kernel.

When I booted up the system was indeed able to find the 2255 card and initalize it.  It showed up in MythTV backend config, but I could not get it to actually tune any channels.  I'll have to look more into that another time.  I've spent too much of Valentine's Day working on this (at least according to my wife, LOL).

---

### Post by bilkay on 2015-02-16
> **rheaj2 said:**
> I'm working on this today too.  (U/Myth)btuntu ships with the 3.13 kernel, but the documentation from Hauppauge indicates that the patches requires a 3.16 kernel.  Let me know if you get the card to work using the 3.13 kernel you patched.  I'm compiling the 3.16 one now.  I'll let you know my results.

You received documentation from Hauppauge? I got nothing.

I think I'll go your route. It looks more promising. Did /var/log/dmesg indicate that the firmware loaded OK?

---

### Post by bilkay on 2015-02-16
Quick question: How did you find the 3.16 kernel? I can't find any reference to it on the kernel.org website.

---

### Post by rheaj2 on 2015-02-17
> **bilkay said:**
> Quick question: How did you find the 3.16 kernel? I can't find any reference to it on the kernel.org website.

All the 3.x kernels are available here:
[https://www.kernel.org/pub/linux/kernel/v3.x/](https://www.kernel.org/pub/linux/kernel/v3.x/)

---

### Post by rheaj2 on 2015-02-17
I did get some documentation from Hauppauge, which led me to the path I posted earlier.  I think I'm still missing something though, as the tuner is not actually working.  I stil have more to look into.  Here is the related output of my dmesg (grepped on "7164"):
```
[    0.201068] pci 0000:03:00.0: [1131:7164] type 00 class 0x048000
[   25.648884] saa7164 driver loaded
[   25.648974] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=11,autodetected]
[   25.648978] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xf8c00000
[   25.806903] saa7164_downloadfirmware() no first image
[   25.807299] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-04-01.1.fw)
[   27.321641] saa7164_downloadfirmware() firmware read 3283792 bytes.
[   27.321643] saa7164_downloadfirmware() firmware loaded.
[   27.321648] saa7164_downloadfirmware() SecBootLoader.FileSize = 3283792
[   27.321654] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   27.321655] saa7164_downloadfirmware() BSLSize = 0x0
[   27.321656] saa7164_downloadfirmware() Reserved = 0x0
[   27.321657] saa7164_downloadfirmware() Version = 0x1d21
[   33.140997] saa7164_downloadimage() Image downloaded, booting...
[   33.244691] saa7164_downloadimage() Image booted successfully.
[   35.638762] saa7164_downloadimage() Image downloaded, booting...
[   37.301368] saa7164_downloadimage() Image booted successfully.
[   37.345253] tveeprom 11-0000: audio processor is SAA7164 (idx 43)
[   37.345254] tveeprom 11-0000: decoder processor is SAA7164 (idx 40)
[   37.345256] saa7164[0]: Hauppauge eeprom: model=151061
[   42.147594] DVB: registering new adapter (saa7164)
[   42.147598] saa7164 0000:03:00.0: DVB: registering adapter 2 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   46.883170] DVB: registering new adapter (saa7164)
[   46.883175] saa7164 0000:03:00.0: DVB: registering adapter 3 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   46.883517] saa7164[0]: registered device video2 [mpeg]
[   47.112425] saa7164[0]: registered device video3 [mpeg]
[   47.321094] saa7164[0]: registered device vbi2 [vbi]
[   47.321137] saa7164[0]: registered device vbi3 [vbi]
[   47.322918] saa7164_api_set_debug() error, ret = 0x13

```

---

### Post by bilkay on 2015-02-17
Completed compiling and re-booted to new kernel. Everything looks OK except I can't get it to work with MythTV. I've only tried with us-cable. I'll try an antenna when I find the time.

---

### Post by bilkay on 2015-02-17
Steve Toth's website has some more files for HVR-22XX. I'm wondering if the 2255 needs them too. It won't hurt to install them, will it?

[http://www.steventoth.net/linux/hvr22xx/](http://www.steventoth.net/linux/hvr22xx/)

---

### Post by bilkay on 2015-02-18
I just can't get the card to work with mythtv. Here's the mythbackend.log after startup:

```
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I Logger logging.cpp:315 (run) Added logging to the console
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_CA.UTF-8
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Jupiter
Feb 18 13:02:07 Jupiter mythbackend: mythbackend[2069]: E CoreContext configuration.cpp:107 (Save) Could not create /home/mythtv/.mythtv
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Feb 18 13:02:08 Jupiter mythbackend: mythbackend[2069]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[3]: Problem finding starting channel, setting to default of '3'.
Feb 18 13:02:09 Jupiter mythbackend: mythbackend[2069]: E CoreContext recorders/channelbase.cpp:944 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Feb 18 13:02:09 Jupiter mythbackend: mythbackend[2069]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Feb 18 13:02:09 Jupiter mythbackend: mythbackend[2069]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 3failed init
Feb 18 13:02:09 Jupiter mythbackend: mythbackend[2069]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[4]: Problem finding starting channel, setting to default of '3'.
Feb 18 13:02:09 Jupiter mythbackend: mythbackend[2069]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[4](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: Device or resource busy (16)
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2069]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[4](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2069]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2069]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 4failed init
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2069]: W CoreContext main_helpers.cpp:214 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2069]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2069]: E CoreContext scheduler.cpp:224 (VerifyCards) Scheduler: No channel sources defined in the database
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I Logger logging.cpp:315 (run) Added logging to the console
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_CA.UTF-8
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Jupiter
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: E CoreContext configuration.cpp:107 (Save) Could not create /home/mythtv/.mythtv
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[3]: Problem finding starting channel, setting to default of '3'.
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Feb 18 13:02:10 Jupiter mythbackend: mythbackend[2091]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Feb 18 13:02:11 Jupiter mythbackend: mythbackend[2091]: E CoreContext recorders/channelbase.cpp:944 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Feb 18 13:02:11 Jupiter mythbackend: mythbackend[2091]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Feb 18 13:02:11 Jupiter mythbackend: mythbackend[2091]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 3failed init
Feb 18 13:02:11 Jupiter mythbackend: mythbackend[2091]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[4]: Problem finding starting channel, setting to default of '3'.
Feb 18 13:02:11 Jupiter mythbackend: mythbackend[2091]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[4](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: Device or resource busy (16)
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2091]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[4](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2091]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2091]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 4failed init
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2091]: W CoreContext main_helpers.cpp:214 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2091]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2091]: E CoreContext scheduler.cpp:224 (VerifyCards) Scheduler: No channel sources defined in the database
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I Logger logging.cpp:315 (run) Added logging to the console
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_CA.UTF-8
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Jupiter
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: E CoreContext configuration.cpp:107 (Save) Could not create /home/mythtv/.mythtv
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[3]: Problem finding starting channel, setting to default of '3'.
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Feb 18 13:02:12 Jupiter mythbackend: mythbackend[2141]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Feb 18 13:02:13 Jupiter mythbackend: mythbackend[2141]: E CoreContext recorders/channelbase.cpp:944 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Feb 18 13:02:13 Jupiter mythbackend: mythbackend[2141]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Feb 18 13:02:13 Jupiter mythbackend: mythbackend[2141]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 3failed init
Feb 18 13:02:13 Jupiter mythbackend: mythbackend[2141]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[4]: Problem finding starting channel, setting to default of '3'.
Feb 18 13:02:13 Jupiter mythbackend: mythbackend[2141]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[4](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: Device or resource busy (16)
Feb 18 13:02:14 Jupiter mythbackend: mythbackend[2141]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[4](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Feb 18 13:02:14 Jupiter mythbackend: mythbackend[2141]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Feb 18 13:02:14 Jupiter mythbackend: mythbackend[2141]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 4failed init
Feb 18 13:02:14 Jupiter mythbackend: mythbackend[2141]: W CoreContext main_helpers.cpp:214 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Feb 18 13:02:14 Jupiter mythbackend: mythbackend[2141]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Feb 18 13:02:14 Jupiter mythbackend: mythbackend[2141]: E CoreContext scheduler.cpp:224 (VerifyCards) Scheduler: No channel sources defined in the database
```

Here's the output from grep 7164 /var/log/dmesg :
```
[    0.087164] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.168559] pci 0000:03:00.0: [1131:7164] type 00 class 0x048000
[    9.887896] saa7164 driver loaded
[    9.888014] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=11,autodetected]
[    9.888019] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xf7800000
[   10.047731] saa7164_downloadfirmware() no first image
[   10.047738] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-04-01.1.fw)
[   11.048227] saa7164_downloadfirmware() firmware read 3283792 bytes.
[   11.048229] saa7164_downloadfirmware() firmware loaded.
[   11.048234] saa7164_downloadfirmware() SecBootLoader.FileSize = 3283792
[   11.048239] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.048240] saa7164_downloadfirmware() BSLSize = 0x0
[   11.048241] saa7164_downloadfirmware() Reserved = 0x0
[   11.048241] saa7164_downloadfirmware() Version = 0x1d21
```

---

### Post by rheaj2 on 2015-02-20
> **bilkay said:**
> Steve Toth's website has some more files for HVR-22XX. I'm wondering if the 2255 needs them too. It won't hurt to install them, will it?

[http://www.steventoth.net/linux/hvr22xx/](http://www.steventoth.net/linux/hvr22xx/)
These files are the ones used to get the 2250 to work, before they came out with the 2255.  The code to make the 2250 work has since been incorporated into the linux kernel, and now works out of the box. The firmware that Hauppauge provided to you should be the only one you need.

---

### Post by rheaj2 on 2015-02-20
> **bilkay said:**
> 
Here's the output from grep 7164 /var/log/dmesg :
```
[    0.087164] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.168559] pci 0000:03:00.0: [1131:7164] type 00 class 0x048000
[    9.887896] saa7164 driver loaded
[    9.888014] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=11,autodetected]
[    9.888019] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xf7800000
[   10.047731] saa7164_downloadfirmware() no first image
[   10.047738] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-04-01.1.fw)
[   11.048227] saa7164_downloadfirmware() firmware read 3283792 bytes.
[   11.048229] saa7164_downloadfirmware() firmware loaded.
[   11.048234] saa7164_downloadfirmware() SecBootLoader.FileSize = 3283792
[   11.048239] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.048240] saa7164_downloadfirmware() BSLSize = 0x0
[   11.048241] saa7164_downloadfirmware() Reserved = 0x0
[   11.048241] saa7164_downloadfirmware() Version = 0x1d21
```
If this is all you get from dmesg for "7164" then you're definitely not getting the card up and running.  In my dmesg I get several more lines after the last one you posted here.  See my ealier post for my dmesg output.  I'm not sure why it just stops there for you, everything up to that point looks the same as mine.  In particular, these important lines seem to be missing:
```

[   42.147594] DVB: registering new adapter (saa7164)
[   42.147598] saa7164 0000:03:00.0: DVB: registering adapter 2 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   46.883170] DVB: registering new adapter (saa7164)
[   46.883175] saa7164 0000:03:00.0: DVB: registering adapter 3 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   47.321094] saa7164[0]: registered device vbi2 [vbi]
[   47.321137] saa7164[0]: registered device vbi3 [vbi]

```
This might explain why your MythBackend is getting these particular errors:
```

Could not get inputs for the capturecard
...and...
Failed to open device /dev/dvb/adapter0/frontend0
...and...
Opening DVB frontend device failed.

```

I haven't had much chance to work on my setup.  My card is recognized by Myth and shows up as a pair of tuners.  The problem is when I try to switch input to one of them, all I get is a black screen, and I have to kill mythfrontend.  I don't see any useful output from mythfrontend on it, back haven't looked at the backend logs yet.  I'll let you know what I find when I get some work into it.  It's just hard to find the time.  MythTV is pretty heavily used in my house, so even when I have time to work on it, it is often is use by someone.

---

### Post by bilkay on 2015-02-20
> **rheaj2 said:**
> I haven't had much chance to work on my setup.  My card is recognized by Myth and shows up as a pair of tuners.  The problem is when I try to switch input to one of them, all I get is a black screen, and I have to kill mythfrontend.  I don't see any useful output from mythfrontend on it, back haven't looked at the backend logs yet.  I'll let you know what I find when I get some work into it.  It's just hard to find the time.  MythTV is pretty heavily used in my house, so even when I have time to work on it, it is often is use by someone.

How is MythTV in use if the card doesn't work? Please clarify. Have you tried vlc?

I think I'm going to go back to ragging on Hauppauge.

Here's to hoping you have some success to report soon.

---

### Post by rheaj2 on 2015-02-20
> **bilkay said:**
> How is MythTV in use if the card doesn't work? Please clarify.
I used to record both from an antenna and from a cable box.  When I moved last fall, I cut the cord and cancelled the cable.  I was left with only one recorder and needed to be able to record multiple shows simultaneously, so I bought the 2255 to allow more inputs.  My cable box recorder couldn't record from the antenna.  I still have the ability to record on my old KWorld card, but have to make choices about which shows to record.  Not a terribly common problem now that I have fewer channels to choose from, but it does happen.  I also have lots of recorded shows that have accumulated over the past 10+ years that my kids like to go back and watch from time to time.

---

### Post by rheaj2 on 2015-02-20
OK, I have some good news and some bad news.  The good news is -> I got the card to work!  The bad news is -> it doesn't work in MythTV, at least no yet and not for me.  I was able to tune the card and watch NBC in avplay outside of Myth.  So, the kernel patches and firmware do work.  Now I just have to figure out why MythTV can't use it.  But, there is a scheduled recording coming up soon.

So, I tried to use dvb-fe-tool to list my DVB cards, but I got an error that said */dev/dvb/adapter0/frontend0 is already in use*.  That's not even the HVR-2255 card, that's different card I hav ein the system.  I had to stop the mythtv-backend service to get past that.  Then I got output from dvb-fe-tool that reflected the HVR2255 tuners.  You use the -a{x} parameter to specify which adapter you want dvb-fe-tool to work with.  In my case the HVR-2255's dual tuners came in as *adapter2/frontend0* and *adapter3/frontend0* which translated to -a2 and -a3 respectively.  The output for my adapter3, the second tuner in my 2255 is:
```
$ dvb-fe-tool -a3
INFO     Device LG Electronics LGDT3306A VSB/QAM Frontend (/dev/dvb/adapter3/frontend0) capabilities:
INFO          CAN_8VSB
INFO          CAN_INVERSION_AUTO
INFO          CAN_QAM_64
INFO          CAN_QAM_256
INFO     DVB API Version 5.10, Current v5 delivery system: DVBC/ANNEX_B
INFO     Supported delivery systems: 
INFO         [DVBC/ANNEX_B]
INFO          ATSC
```

Using dvb-fe-tool to set it to ATSC for my antenna input gave me this:
```
$ dvb-fe-tool -a3 --set-delsys=ATSC
INFO     Device LG Electronics LGDT3306A VSB/QAM Frontend (/dev/dvb/adapter3/frontend0) capabilities:
INFO          CAN_8VSB
INFO          CAN_INVERSION_AUTO
INFO          CAN_QAM_64
INFO          CAN_QAM_256
INFO     DVB API Version 5.10, Current v5 delivery system: DVBC/ANNEX_B
INFO     Supported delivery systems: 
INFO         [DVBC/ANNEX_B]
INFO          ATSC
Changing delivery system to: ATSC
```
I had to install w-scan to be able to scan the tuners for channels:
```
$ sudo apt-get install w-scan
```
Then I scanned for channels:
```

$ mkdir ~/.azap
$ w_scan -a3 -fa -A1 -cUS -X > ~/.azap/channels.conf
w_scan version 20130331 (compiled for DVB API 5.10)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
scan type TERRCABLE_ATSC, channellist 1
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.a
frontend 'LG Electronics LGDT3306A VSB/QAM Frontend' supports
INVERSION_AUTO
8VSB
QAM_64
QAM_256
FREQ (54.00MHz ... 858.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 8VSB(time: 00:01) 
63000: 8VSB(time: 00:06) 
69000: 8VSB(time: 00:10) 
```
A whole bunch of lines of output like this came up until it started finding channels, then I got stuff like this:
```
tune to: 8VSB     f=85000 kHz 
(time: 05:05) service is running. Channel number: 6:1. Name: 'WRGB-HD'
service is running. Channel number: 6:2. Name: 'this TV'
tune to: 8VSB     f=177000 kHz 
(time: 05:07) service is running. Channel number: 23:1. Name: 'WXXA-HD'
service is running. Channel number: 23:2. Name: 'WXXA-OT'
tune to: 8VSB     f=207000 kHz 
(time: 05:08) service is running. Channel number: 13:1. Name: 'WNYT-HD'
service is running. Channel number: 13:2. Name: 'WNYT-ME'
service is running. Channel number: 13:3. Name: 'WNYT-WX'
tune to: 8VSB     f=497000 kHz 
(time: 05:09) service is running. Channel number: 13:1. Name: 'WNYT-HD'
service is running. Channel number: 13:2. Name: 'WNYT-ME'
service is running. Channel number: 13:3. Name: 'WNYT-WX'
tune to: 8VSB     f=545000 kHz 
(time: 05:12) service is running. Channel number: 10:1. Name: 'WTEN-HD'
service is running. Channel number: 10:2. Name: 'WTEN-SD'
service is running. Channel number: 10:3. Name: 'LWN'
tune to: 8VSB     f=593000 kHz 
(time: 05:13) service is running. Channel number: 17:1. Name: 'WMHT-HD'
service is running. Channel number: 17:2. Name: 'WMHT-Cr'
service is running. Channel number: 17:3. Name: 'WMHT-Wo'
```Then using azap, tune the card to one of the found channels listed in ~/.azap/channels.conf:
```

$ azap -a3 "WNYT-HD" -r
using '/dev/dvb/adapter3/frontend0' and '/dev/dvb/adapter3/demux0'
Version: 5.10       FE_CAN { DVB-C (B) + ATSC }
tuning to 207000000 Hz
video pid 0x0031, audio pid 0x0034
```
I opened another terminal window and ran this command:
```

avplay /dev/dvb/adapter1/dvr0
```
I was pleased to see the video feed come up and play smoothly.  I have no idea if sound works as I was working on my MythTV backend-only machine which has no speakers. I use separate quiet frontends for viewing. I have no idea why MythTV can't use these tuners, and it may very well be something that is only a problem on my system.  But, this proves that the card can work in Linux, so I encourage you to give it a shot.  If you can get the card to initialize, it may well just work in MythTV for you.  I'll see what I can figure out as to why it's not working for my Myth setup, but like I said, it is a production system that the family uses frequently.  If it weren't I would probably dump out my table of recording history and rebuild from scratch to a clean system and try again.  Let me know if you get it working in Myth.  Or perhaps someone more experienced with Myth can chime in and give me some good pointers for troubleshooting this aspect of it.

---

### Post by bilkay on 2015-02-21
Just received the latest build of the Linux driver from Hauppauge dated 2015-01-23. It's back to work.

---

### Post by bilkay on 2015-02-21
I just got done rebuilding the new kernel from scratch using the newer patch (Jan. 23, '15) I just got from Hauppauge. Mythtv-setup is doing a QAM (cable) channel scan right now, but I'm seeing a lot of messages like "QAM-256 Channel 112 -- Timed out, 10 possible channels" (a few say "probable" instead of "possible". At least it's progress.

---

### Post by rheaj2 on 2015-02-21
I'm still unabel to get MythTv to find any channels on the 2255.  However, I was able to replicate the channel/frequency entries in the database from my working card to a set for the new card and MythTV can tune those channels on the new card now.  So I can now record up to three shows at once.  I have no idea why Myth is unable to find the channels during a scan.  Considering that w-scan was able to find them, I suspect there may either be some kind of bug in my Myth set up, or perhaps Myth is unable to recognize something from the patched drivers. I didn't see anything helpful in the logs. My setup is not exactly a fresh clean build. I believe I am running on a MythBuntu setup that started with something like 10.04 and has been repeatedly upgraded. One of these days I'll get around to doing a new clean install.

---

### Post by bilkay on 2015-02-22
> **rheaj2 said:**
> I'm still unabel to get MythTv to find any channels on the 2255.  However, I was able to replicate the channel/frequency entries in the database from my working card to a set for the new card and MythTV can tune those channels on the new card now.  So I can now record up to three shows at once.  I have no idea why Myth is unable to find the channels during a scan.  Considering that w-scan was able to find them, I suspect there may either be some kind of bug in my Myth set up, or perhaps Myth is unable to recognize something from the patched drivers. I didn't see anything helpful in the logs. My setup is not exactly a fresh clean build. I believe I am running on a MythBuntu setup that started with something like 10.04 and has been repeatedly upgraded. One of these days I'll get around to doing a new clean install.

It works for me, at least so far. I can record in SD and HD, but Mythtv gives a weird error if I try "Watch TV" on most (not all) channels. I can watch recorded programs however. I need to try recording two at once, and watching a recorded program while two are recording.

Since this thread is about the 2255 not working, it should probably be marked "Solved".

p.s. My card is installed on a new PC that had 14.04 installed originally. I "upgraded" to Mythbuntu from the software center.

---

### Post by spyderdyne on 2015-09-27
I think I have this issue.  It was sold as a 2250.  Is this the behavior of a 2255?

[http://ubuntuforums.org/showthread.php?t=2296391&highlight=2250+myth+db](http://ubuntuforums.org/showthread.php?t=2296391&highlight=2250+myth+db)

---

### Post by vidtek on 2015-09-30
The 22** series of Hauppauge cards have historically had issues with Mythtv and channel scanning.   Steven Toth, the man who wrote the drivers for Hauppauge advised me to do a w-scan and import that into Mythtv.

When I try a new release Ubuntu, Mint, Ultimate, whatever, I always install KDE&#347; Kaffeine which is a quick and easy way to check if all tuners and other system bits are working properly.

If it doesn´t work in Kaffeine, you have buckleys chance of it working in Mythtv!  Kaffeine has a nice interface and easy scanning system which is very transparent, not like Mythtv.

Tony.

---

