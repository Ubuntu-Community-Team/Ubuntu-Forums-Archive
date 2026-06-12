---
title: "VLC Bad Alloc error"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by egenesis on 2008-01-18
I am recently having some error while starting VLC. Does anyone has same problem?


VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 472 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


What I have tried so far?

1. Set the Visiual effects to None  on System->Preference-->Appearance. I believe this disables Compiz. Originally I thought I ran out video memory. This did not work.

2. Since step 1 did not work, I edited my xorg.conf file and added the following lines (bold ones). This did not work.

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express 
Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
[B]        Option "VideoRam" "65536"
        Option "CacheLines" "1980"
[/B]EndSection

3. Removed vlc, removed .vlc folder on my home directory, reboot and reinstalled vlc. This did not work too.

Here is the lspci info

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>


Does anyone has the same issue? or even a fix for this issue?

I tried opening video with Totem and it works fine ...

---

### Post by jharker on 2008-01-18
Yes, I can report almost exactly the same problem.  This is a very sudden occurrence, as I'm pretty sure I've used VLC successfully in the past couple of days.  I've made no major changes to my system in that time, but I have applied a few automatic updates.

Running "vlc" in a terminal returns:
```
VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 476 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Running "free" gives:
```
             total       used       free     shared    buffers     cached
Mem:       1554676    1506196      48480          0      43260    1211300
-/+ buffers/cache:     251636    1303040
Swap:      2104472      16528    2087944
```

Running "lspci -vv" gives (in part):
```
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0571
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at c1000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>
```

I run a Thinkpad G41 and a pretty much stock Ubuntu install.  I don't use desktop effects at all. If any other information would be helpful, I'd be happy to provide it!

*[Edited to provide more info.]*

---

### Post by jharker on 2008-01-18
Oh, I should mention something else I tried: I used Symantec to re-install vlc and a couple of libraries, on the off chance that something important had been corrupted.  No effect, though.

---

### Post by egenesis on 2008-01-18
Ya looks like you have the same issue. What updates did you apply, do you remember it?

---

### Post by egenesis on 2008-01-18
Nope, I tried reinstalling VLC plus couple of plugins. Still same issue. Just unlucky here.

jharker how does your xorg.conf file look like? Can you copy paste it here?

---

### Post by egenesis on 2008-01-18
How does your corg.conf file look like?

---

### Post by Talkless on 2008-01-18
I guess it's something with X.org latest update...

---

### Post by egenesis on 2008-01-18
I just ran the update using

apt-get update
apt-get upgrade

It says there is nothing to upgrade.

same with symaptic ...

All the update repository is turned on except the pre-release repository.

---

### Post by jharker on 2008-01-18
Hmm... okay, I checked in the apt log, which is in /var/log/apt/term.log.  This includes automatic updates from the last few days. I snipped out the manual installs, which were pdfedit, gtk-gnutella, and soundconverter.

Looks like the xserver-xorg-core package just got updated today; that might have something to do with it.

```
Log started: 2008-01-16  10:05:31
(Reading database ... 283452 files and directories currently installed.)
Preparing to replace libcupsys2 1.3.2-1ubuntu7.3 (using .../libcupsys2_1.3.2-1ubuntu7.5_i386.deb) ...
Unpacking replacement libcupsys2 ...
Preparing to replace libcupsimage2 1.3.2-1ubuntu7.3 (using .../libcupsimage2_1.3.2-1ubuntu7.5_i386.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace cupsys-common 1.3.2-1ubuntu7.3 (using .../cupsys-common_1.3.2-1ubuntu7.5_all.deb) ...
Unpacking replacement cupsys-common ...
Preparing to replace cupsys 1.3.2-1ubuntu7.3 (using .../cupsys_1.3.2-1ubuntu7.5_i386.deb) ...
 * Stopping Common Unix Printing System: cupsd
   ...done.
Unpacking replacement cupsys ...
Preparing to replace cupsys-bsd 1.3.2-1ubuntu7.3 (using .../cupsys-bsd_1.3.2-1ubuntu7.5_i386.deb) ...
Unpacking replacement cupsys-bsd ...
Preparing to replace cupsys-client 1.3.2-1ubuntu7.3 (using .../cupsys-client_1.3.2-1ubuntu7.5_i386.deb) ...
Unpacking replacement cupsys-client ...
Setting up libcupsys2 (1.3.2-1ubuntu7.5) ...

Setting up libcupsimage2 (1.3.2-1ubuntu7.5) ...

Setting up cupsys-common (1.3.2-1ubuntu7.5) ...
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.cupsd ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd
   ...done.

Setting up cupsys-client (1.3.2-1ubuntu7.5) ...

Setting up cupsys-bsd (1.3.2-1ubuntu7.5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-01-16  10:08:35

Log started: 2008-01-17  13:01:03
(Reading database ... 283452 files and directories currently installed.)
Preparing to replace libboost-filesystem1.34.1 1.34.1-2ubuntu1 (using .../libboost-filesystem1.34.1_1.34.1-2ubuntu1.1_i386.deb) ...
Unpacking replacement libboost-filesystem1.34.1 ...
Preparing to replace libboost-regex1.34.1 1.34.1-2ubuntu1 (using .../libboost-regex1.34.1_1.34.1-2ubuntu1.1_i386.deb) ...
Unpacking replacement libboost-regex1.34.1 ...
Preparing to replace libboost-signals1.34.1 1.34.1-2ubuntu1 (using .../libboost-signals1.34.1_1.34.1-2ubuntu1.1_i386.deb) ...
Unpacking replacement libboost-signals1.34.1 ...
Setting up libboost-filesystem1.34.1 (1.34.1-2ubuntu1.1) ...

Setting up libboost-regex1.34.1 (1.34.1-2ubuntu1.1) ...

Setting up libboost-signals1.34.1 (1.34.1-2ubuntu1.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-01-17  13:01:36

Log started: 2008-01-18  01:11:45
(Reading database ... 283843 files and directories currently installed.)
Preparing to replace libxfont-dev 1:1.3.0-0ubuntu1 (using .../libxfont-dev_1%3a1.3.0-0ubuntu1.1_i386.deb) ...
Unpacking replacement libxfont-dev ...
Preparing to replace libxfont1 1:1.3.0-0ubuntu1 (using .../libxfont1_1%3a1.3.0-0ubuntu1.1_i386.deb) ...
Unpacking replacement libxfont1 ...
Preparing to replace avahi-autoipd 0.6.20-2ubuntu3.1 (using .../avahi-autoipd_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement avahi-autoipd ...
Preparing to replace libavahi-common-data 0.6.20-2ubuntu3.1 (using .../libavahi-common-data_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-common-data ...
Preparing to replace libavahi-common3 0.6.20-2ubuntu3.1 (using .../libavahi-common3_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-common3 ...
Preparing to replace libavahi-core5 0.6.20-2ubuntu3.1 (using .../libavahi-core5_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-core5 ...
Preparing to replace avahi-daemon 0.6.20-2ubuntu3.1 (using .../avahi-daemon_0.6.20-2ubuntu3.2_i386.deb) ...
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon
   ...done.
Unpacking replacement avahi-daemon ...
Preparing to replace libavahi-client3 0.6.20-2ubuntu3.1 (using .../libavahi-client3_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-client3 ...
Preparing to replace libavahi-compat-libdnssd1 0.6.20-2ubuntu3.1 (using .../libavahi-compat-libdnssd1_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-compat-libdnssd1 ...
Preparing to replace libavahi-glib1 0.6.20-2ubuntu3.1 (using .../libavahi-glib1_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-glib1 ...
Preparing to replace libavahi-qt3-1 0.6.20-2ubuntu3.1 (using .../libavahi-qt3-1_0.6.20-2ubuntu3.2_i386.deb) ...
Unpacking replacement libavahi-qt3-1 ...
Preparing to replace xserver-xorg-core 2:1.3.0.0.dfsg-12ubuntu8 (using .../xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.1_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Preparing to replace xserver-xorg-dev 2:1.3.0.0.dfsg-12ubuntu8 (using .../xserver-xorg-dev_2%3a1.3.0.0.dfsg-12ubuntu8.1_i386.deb) ...
Unpacking replacement xserver-xorg-dev ...
Setting up libxfont1 (1:1.3.0-0ubuntu1.1) ...

Setting up libxfont-dev (1:1.3.0-0ubuntu1.1) ...
Setting up avahi-autoipd (0.6.20-2ubuntu3.2) ...

Setting up libavahi-common-data (0.6.20-2ubuntu3.2) ...
Setting up libavahi-common3 (0.6.20-2ubuntu3.2) ...

Setting up libavahi-core5 (0.6.20-2ubuntu3.2) ...

Setting up avahi-daemon (0.6.20-2ubuntu3.2) ...
 * Reloading system message bus config...
   ...done.
Fixing up startup script priorities...
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
   ...done.

Setting up libavahi-client3 (0.6.20-2ubuntu3.2) ...

Setting up libavahi-compat-libdnssd1 (0.6.20-2ubuntu3.2) ...

Setting up libavahi-glib1 (0.6.20-2ubuntu3.2) ...

Setting up libavahi-qt3-1 (0.6.20-2ubuntu3.2) ...

Setting up xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu8.1) ...
Setting up xserver-xorg-dev (2:1.3.0.0.dfsg-12ubuntu8.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-01-18  01:12:05
```

---

### Post by jharker on 2008-01-18
I'm pretty sure it's not my xorg.conf, since that hasn't changed in a long time and I just started having problems today.  I suspect it has something to do with that xorg update.

Anyone around here know something about the xorg update?

**Edit:** Yes, I checked, my xorg.conf hasn't been changed for several months. But here are some relevant bits anyway:

```
Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1400x1050"
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Driver          "nvidia"
        Vendorname      "NVIDIA"
        Boardname       "NVIDIA GeForce FX (generic)"
        Busid           "PCI:1:0:0"
        Screen  0
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1400x1050"     "1280x1024"     "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection
```

---

### Post by Azaphan on 2008-01-18
> Talkless  	
Re: VLC Bad Alloc error
I guess it's something with X.org latest update...

Yeah, the problem is tle X.org latest update. Try downgrade the X.org with the command:

> sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

---

### Post by jharker on 2008-01-18
Okay, this is a [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969") with the latest xserver-xorg-core release. It seems like it "breaks graphical java apps."

According to the bug report, the bug has just been fixed. The fix should be released in the next 15-20 minutes, so if you just keep checking for updates, you should see it soon.

---

### Post by louaym on 2008-01-18
I have installed the new released  xserver-xorg-core_1.2.0-3ubuntu8.2_i386.deb 
and it fix it for Ubuntu 7.04

---

### Post by -random on 2008-01-18
It's definitely the xserver-xorg-core update (found out after a long process of partimage-ing back to a prev systm that vlc worked, and checkd the possible updates one-by-one phew..),

wish i found this thread a couple of hours earlier.. it wouldv'e saved me a lot of trouble! :P

thnxk guys, re-installing the new update as we speak

---

### Post by egenesis on 2008-01-18
THE UPDATE FIXED THE ISSUE!! Thanks everyone/jharker!!

---

### Post by Daelyn on 2008-01-18
Got the exact same issue here today when I got home and tried starting a few movies in my VLC.

Could not by any way find any good cause. Hadn't done any changes, except doing the updates this morning.

Updating to latest xorg core SOLVED the issue.

---

### Post by nonovo on 2008-01-19
Hi,

'm having just a same problem. I am using vlc daily as my radio. The VLC player stopped working today, after I have loaded std. ubuntu patches as reported by synaptic manager.
I am 90% sure, it caused by one of the upgrades.
Guys, can someone look into it?

Thx,
N.


The log from yesterday's upgrades:
Upgraded the following packages:
avahi-autoipd (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
avahi-daemon (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
cupsys (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5
cupsys-bsd (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5
cupsys-client (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5
cupsys-common (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5
libavahi-client3 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
libavahi-common-data (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
libavahi-common3 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
libavahi-compat-libdnssd1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
libavahi-core5 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
libavahi-glib1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2
libcupsimage2 (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5
libcupsys2 (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5
libcupsys2-dev (1.3.2-1ubuntu7.3) to 1.3.2-1ubuntu7.5

---

### Post by niska on 2008-01-19
I have the exact same problem

---

### Post by RomeReactor on 2008-01-19
Hi. Try the [first post on this page]("http://ubuntuforums.org/showpost.php?p=4161650&postcount=11"). Please open a terminal (Applications->Accessories->Terminal) and enter:
```
vlc
```
If you get a 'BadAlloc' error, then try downgrading the xserver-xorg-core package:
```
sudo aptitude install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
```
Then restart your display by pressing CTRL+ALT+BACKSPACE and see if it works now.

---

### Post by nonovo on 2008-01-19
Thanks guys, the upgrade of xorg core helped.

---

### Post by SubCool on 2008-01-20
Hey,
Im a noob - so please excuse the ignorance.
but i am running into the same issue. 

> The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 141 minor_code 19)


I tried to downgrade the xorg. Didnt work.

---

### Post by RomeReactor on 2008-01-20
> **SubCool said:**
> > The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 48 error_code 11 request_code 141 minor_code 19)
I tried to downgrade the xorg. Didnt work.

Hi. With what program does this error happen? Do you have an Intel video card? The new xorg-core package is **xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu8.3)**; to install it, go to 'System->Administration->Update Manager' and press the 'Check' button. The updated package should show up then. Or to install it from the terminal:
```
sudo aptitude install xserver-xorg-core
```

Otherwise, you can get the package here:

* [32-bit package]("http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb")
* [64-bit package]("http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_amd64.deb")

---

