---
title: "HOWTO: Jaunty Intel Graphics Performance Guide"
date: 2009-04-19
forum: Multimedia Software
---

### Post by psyke83 on 2009-04-19
[COLOR="Red"]**Warning:** Although I have made an effort to make this guide as accessible as possible, if you are a beginner to Ubuntu then you are not recommended to follow this guide at all. Even if you stick to the safest method outlined, your system may experience difficulties due to the installation of unofficial drivers. Consider yourselves warned ;).[/COLOR]

[SIZE="3"]**Overview**[/SIZE]
*Some users are experiencing performance issues with Intel integrated graphics chips in Jaunty (9.04) for several possible reasons:*

[LIST=A]
[*]The current driver in our repository has some performance issues with the EXA acceleration method. Users will notice 2D performance is poor due to the default "migration heuristic" employed by EXA (to "always" migrate pixmaps), but this causes performance issues for many users. Setting the heuristic to "greedy" alleviates this problem somewhat. See **"man exa"**.

[*]The new and faster acceleration method (UXA) is not enabled by default, due to issues reported by many users. This code is being actively developed, and many stability and performance issues have been resolved in the latest drivers (specifically within the intel driver, libdrm, mesa and kernel 2.6.29.4 or later). Unfortunately, Jaunty will not include the latest versions necessary to improve performance.

[*]3D performance has regressed compared to the Intrepid release, possibly due to major code changes that have resulted from the introduction to the new acceleration and memory management code (UXA, GEM, DRI2). Due to these changes, there seems to be some regressions in the "legacy" DRI acceleration. 

[*]Either Xorg or the "intel" driver seems to be suffering from a [bug]("https://bugs.launchpad.net/bugs/314928") in which the memory (MTRR) region allocated for the graphics card is not set up with the proper type of caching. This results in jerky video playback of almost any content (from 720p media, all the way down to simple 320x240 mpeg content), and a potential loss of performance for other 2D and 3D operations.
[/LIST]
There are three possible configuration that this guide will present:

**_Safe_ Configuration**
[LIST]
[*]For this configuration, you will upgrade to the latest stable Xorg drivers (via the [X-Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/")), enable UXA acceleration and create a workaround for the MTRR bug. This is the solution recommended for users who possess hardware devices that depend on a restricted driver. If you don't know what this means, then this is the solution you should use.
[/LIST]
**_Optimal*_ Configuration**
[LIST]
[*]This configuration is identical to "Safe", but includes the [2.6.30.9]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/") kernel. Using this kernel will improve 3D performance for many users, but you will lose access to restricted kernel drivers. This configuration yields the best results for my system (an 855GM chipset), but of course, your experience may differ.
[/LIST]
**_Bleeding-Edge*_ Configuration**
[LIST]
[*]This configuration is the most risky. This will enable repository which contains bleeding-edge mesa & Xorg drivers which are continually updated (via the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa")), enable UXA acceleration, create a workaround for the MTRR bug and install kernel [2.6.30.9]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/"). This configuration is **not** necessarily the fastest (in fact, the Optimal configuration is fastest for my hardware), and is recommended only for users who want to test the latest Xorg code.
[COLOR="Blue"]**Note:** As per the PPA maintainer's wish, you are instructed to read the instructions [here]("https://launchpad.net/~xorg-edgers/+archive/ppa"), since the Bleeding-Edge repository is prone to breakage and important instructions may be added. Don't request support for these packages (and don't be surprised if questions are left unanswered).[/COLOR]

[/LIST]
[COLOR="Red"]***Disclaimer:** Using a third-party kernel means that you will no longer have access to "restricted" drivers such as FGLRX, NVIDIA, some Broadcom wireless chipsets, certain webcams and a handful new sound cards that require restricted firmware to function. If you believe that you have restricted hardware on your machine, you should continue using the official Jaunty kernel - in other words, stick to the **Safe** configuration.[/COLOR]

[COLOR="Red"]**Warning:** **Do not** switch between the Safe/Optimal and Bleeding-Edge solutions unless you have followed the steps to revert changes beforehand. For example, if you try the Bleeding-Edge method, and then decide to try the Optimal configuration, you will still be using the Bleeding-Edge drivers (because the xorg-edgers PPA contains newer drivers than the X-Updates PPA, which are not downgraded automatically).[/COLOR]

Once you have decided on the configuration that suits you, begin by following Part A below:

[SIZE="3"]**Part A - Common Instructions (Safe/Optimal/Bleeding-Edge)**[/SIZE]
*All users must follow this part.*

0. **Optional:** If there is no xorg.conf file present on your system, the following command will create a minimal configuration (which you can customize later):```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```[COLOR="Blue"]**Note:** Use caution with this command, as it will overwrite any xorg.conf file already present on your system (though it will create a backup).[/COLOR]

1. Edit your xorg.conf:
```
$ gksudo gedit /etc/X11/xorg.conf
```

Find the "Device" section and make sure it looks identical to the following (important: remove or comment any of your previous customizations):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" **# i8xx users: see note in guide**
EndSection
```[COLOR="Blue"]**N.B.:** If you are using an Intel 8xx chipset, tiling cause instability unless you use the Bleeding-Edge configuration. Therefore: if you are using the Safe/Optimal configurations, set tiling to false; if you are using the Bleeding-Edge configuration, set tiling to true.[/COLOR]

2. Download [Bartec's]("https://bugs.launchpad.net/~tschew") [fixmtrr.sh]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/38") script and make it executable:
```
$ sudo wget http://launchpadlibrarian.net/26193373/fixmtrr.sh -O /usr/local/bin/fixmtrr.sh
$ sudo chmod +x /usr/local/bin/fixmtrr.sh
```

3. Create a symbolic link to ensure the fixmtrr.sh script is executed upon each login via GDM:
```
$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default
```
[COLOR="Blue"]N.B. This works only if you are using the GNOME Display Manager (GDM). KDE/other users need to execute this script manually - see the **Important Note** section.[/COLOR]

4. If you want the Safe/Optimal configuration, continue to Part B. For Bleeding-Edge, skip to Part C.

[SIZE="3"]**Part B (Safe/Optimal)**[/SIZE]
*Users who wish to try the Safe **or** Optimal configurations must follow this part.*

1. Add the [X Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/") to your sources.list:

Edit /etc/apt/sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```

Add these entries to the end of your sources.list file (if they do not already exist):
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
```

2. Import the X Updates PPA key, update your apt sources, and perform an upgrade:
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```[COLOR="Blue"]**N.B.:** If you are asked to remove any packages, immediately cancel the process. The expected behaviour is only to upgrade packages, not to remove.[/COLOR]

3. If you want to use the Safe configuration, you're finished - proceed to the **Important Note** section. If you want the Optimal configuration, continue to Part C.

[SIZE="3"]**Part C (Optimal/Bleeding-Edge)**[/SIZE]
*Users who desire the Optimal or Bleeding-Edge configurations should follow this section.*

1. Download & install the 2.6.30.9 kernel according to your architecture:

**i386 users:**
```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009-generic_2.6.30-02063009_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-image-2.6.30-02063009-generic_2.6.30-02063009_i386.deb
$ sudo dpkg -i linux-headers-2.6.30-02063009-generic_2.6.30-02063009_i386.deb linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb linux-image-2.6.30-02063009-generic_2.6.30-02063009_i386.deb
```
**amd64 users:**
```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009-generic_2.6.30-02063009_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-image-2.6.30-02063009-generic_2.6.30-02063009_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-02063009-generic_2.6.30-02063009_amd64.deb linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb linux-image-2.6.30-02063009-generic_2.6.30-02063009_amd64.deb
```

3. If you want the Optimal configuration, you're finished - however, before rebooting into the new kernel, read the **Important Note** section. Bleeding-Edge users, continue to the Part D.

[SIZE="3"]**Part D (Bleeding-Edge)**[/SIZE]
*Users who desire the Bleeding-Edge configuration should follow this section.*

1. Add the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa") to your sources.list:

Edit /etc/apt/sources.list:

```
$ gksudo gedit /etc/apt/sources.list
```
Append the following text into the end of this file, then save and close:
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
```

Import the xorg-edgers PPA key, update your apt sources, and perform an upgrade:
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```[COLOR="Blue"]**N.B.:** If you are asked to remove any packages, immediately cancel the process. The expected behaviour is only to upgrade packages, not to remove.[/COLOR]

2. You're finished. However, before rebooting into the new kernel, read the **Important Note** section.

**[SIZE="3"]Important Notes (Safe/Optimal/Bleeding-Edge)[/SIZE]**

**Reporting Bugs**
If you choose the Safe or Optimal configuration, you will be using the stable (but unofficial) X-Updates drivers. From the [repository description]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"):

> While Ubuntu-X does not officially support these packages, if you discover problems when installing these debs please feel free to report bugs to launchpad. However, please** make sure to clearly state that you are running packages from this PPA** so we know the fixes need to come here.

Therefore, if you are using the Safe/Optimal configuration you may report bugs to [Launchpad]("https://bugs.launchpad.net/ubuntu") - as long as you adhere to the request above. I also recommend that you test against the official Ubuntu kernel, or at least disclose in your bug report that you are using the unofficial [mainline kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/").

If you are using the Bleeding-Edge configuration, you can also report bugs to Launchpad as long as you explicitly state that you are using the xorg-edgers drivers. Please keep in mind that the purpose of the xorg-edgers repository is to package semi-daily snapshots of upstream's code, and Launchpad may not the appropriate place to file bugs (since there are going to be days where stuff is expected to break, and filing a bug is a waste of time). Alternatively, you can report issues to the upstream bug tracker, but you are expected to submit [detailed reports]("http://intellinuxgraphics.org/how_to_report_bug.html"). Don't expect support for the xorg-edgers drivers in this thread!

Remember to use the *ubuntu-bug* tool to ensure the required information gets submitted to your bug report:
```
$ ubuntu-bug xserver-xorg-video-intel
```

**Using the fixmtrr.sh script**
The purpose of the fixmtrr.sh script is to workaround a [bug]("https://bugs.launchpad.net/bugs/314928") in the intel driver and/or kernel and ensure your graphics card's memory region gets set to the correct type of caching (write-combining). If your memory region is not set with the proper type of caching, you will experience video stuttering and reduced 3D performance.

[COLOR="Blue"]**Note:** If you are using Kubuntu or a custom distribution of Ubuntu that does not use the GNOME Display Manager (GDM), you need to execute the fixmtrr.sh script **each time X (re)starts**. Therefore, executing this script in your rc.local script is not sufficient.[/COLOR]

[SIZE="3"]**Interpreting Performance Gains**[/SIZE]

[COLOR="Red"]*Do. Not. Trust. Glxgears.*[/COLOR]

Seriously. Your glxgears score may reduce after following this guide and enabling UXA acceleration (i.e., when the DRI2 framework is activated), but it does *not* mean things are worse.

The glxgears application was never an accurate benchmark of 3D performance, and developers have pleaded for users to understand this fact for a long, long time. See [this]("http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark") page for an explanation.

I suggest you find a better tool to benchmark performance - in my case, I settled on PlanetPenguin racer (enabling the FPS counter in the options).

For comparison's sake, here's a rough outline of my performance results on my Inspiron 510m laptop with a Pentium M 1.5Ghz, 768MB ram and Intel 855GM chipset:
**Intrepid:** glxgears = ~1000fps, ppracer = ~23fps.
**Jaunty (default configuration):** glxgears = ~300fps, ppracer = ~19fps
**Jaunty (with Optimal configuration):** glxgears = ~340fps, ppracer = ~30fps

As you can see, glxgears does not accurately portray the improvement gained from testing the latest DRI2/UXA code.

[SIZE="3"]**To Revert Settings**[/SIZE]
*If these configurations didn't work for you, this is how to revert changes.*

[LIST=1]
[*]Edit your sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```

Remove the lines for the xorg-edgers and/or X-Updates repositories, then save and close.


[*]Downgrade packages:
```
$ sudo apt-get install libdrm-dev/jaunty libdrm2/jaunty libdrm-intel1/jaunty libdrm-radeon1/jaunty xserver-xorg-video-intel/jaunty libdrm-nouveau1/jaunty libgl1-mesa-dri/jaunty libgl1-mesa-glx/jaunty libgl1-mesa-dev/jaunty libglu1-mesa/jaunty mesa-common-dev/jaunty mesa-utils/jaunty xserver-common/jaunty xserver-xorg-core/jaunty xserver-xorg-input-evdev/jaunty xserver-xorg-input-evdev/jaunty xserver-xorg-input-synaptics/jaunty xserver-xorg-video-ati/jaunty xserver-xorg-video-nv/jaunty xserver-xorg-video-openchrome/jaunty xserver-xorg-video-radeon/jaunty
```[COLOR="Blue"]**N.B.:** Ensure that packages are only downgraded, not removed. Otherwise cancel the process.[/COLOR]


[*]Remove the 2.6.30.9 kernel:
```
$ sudo dpkg -r linux-headers-2.6.30-02063009 linux-headers-2.6.30-02063009-generic linux-image-2.6.30-02063009-generic

```

[*]Reset your xorg.conf to defaults:
```
$ sudo dpkg-reconfigure xserver-xorg
```

[*]Optional: remove the fixmtrr.sh script and GDM PostLogin hook:
```
$ sudo rm /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default
```[/LIST]
Your system will then be restored to normal.

[SIZE="1"]**Changelog**
v1.1 - 12/05/09 - Complete re-write.
v1.2 - 12/05/09 - Modified instructions to allow automatic startup of fixmtrr.sh script (Part A, step 3).
v1.3 - 19/05/09 - Updated Bleeding-Edge section to fetch -rc6 kernel.
v1.4 - 24/05/09 - Updated Bleeding-Edge section to fetch -rc7 kernel.
v1.5 - 01/06/09 - Updated Optimal section to fetch 2.6.29.4 kernel, added Bleeding-Edge note.
v1.6 - 02/06/09 - Added some warnings to guide.
v1.7 - 03/06/09 - Updated Bleeding-Edge section to fetch -rc8 kernel.
v1.8 - 11/06/09 - Updated Optimal and Bleeding-Edge sections to fetch final 2.6.30 kernel.
v1.9 - 15/06/09 - Added information regarding bug reporting policy to Important Note section.
v2.0 - 24/06/09 - Clarified bug reporting policy.
v2.1 - 22/07/09 - Updated guide to use 2.6.30.2 kernel.
v2.2 - 28/07/09 - Updated guide to use 2.6.30.3 kernel.
v2.3 - 15/09/09 - Updated guide to use 2.6.30.9 kernel.
[/SIZE]

---

### Post by crjackson on 2009-04-19
psyke83 - Thanks for the guide. I plan to upgrade my Intel powered laptop with an X3100 in a few days. I'll place this in my subscribed list for easy reference.

Thanks for all your hard and productive work.

---

### Post by novafluxx on 2009-04-19
Thank you!
Quick question though, how do I know if I've enabled UXA properly or not?

---

### Post by psyke83 on 2009-04-19
> **novafluxx said:**
> Thank you!
Quick question though, how do I know if I've enabled UXA properly or not?

It'll be mentioned in the logs.

```
$ grep -i UXA /var/log/Xorg.0.log
```

---

### Post by nwadams on 2009-04-19
is there any chance this stuff will get put into jaunty post-release or will we have to wait until karmic?

---

### Post by psyke83 on 2009-04-19
> **nwadams said:**
> is there any chance this stuff will get put into jaunty post-release or will we have to wait until karmic?

The chances are slim-to-none. However, there may be specific code commits that can be safely get backported into the current version of the drivers shipping with Jaunty, or some newer versions of the drivers may get released into the proposed repository. You'll never see kernel 2.6.29 or 2.6.30 in Jaunty (the latter isn't even finished yet). 

Karmic is your best bet for official support.

---

### Post by VMC on 2009-04-20
Here's the output you requested:

$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable

$ lspci -vvnn

00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
	Subsystem: Dell Device [1028:0151]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at ed98 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

---

### Post by psyke83 on 2009-04-20
By the way, I normally get angry at compiz due to slow scrolling, but I actually find it bearable right now ;). Scrolling is smooth on my old laptop (with exception to certain sites in Firefox, such as Gmail - but is the fault of Firefox and not compiz or Xorg).

---

### Post by VMC on 2009-04-20
Your fix didn't work. The new kernel works but the xorg.conf fix caused my screen to freeze. I needed to power cycle to reboot.

Can you post you complete xorg.conf for reference.

Below is what I put in Section device.

Also I have an intregrated 865G and I can't play movies at all, avi mpeg, dvd's mplayer crashes. I do have a xorg.conf fix that works but the screen to very slow and frames are choppy.

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"Tiling"			"false"
EndSection

---

### Post by psyke83 on 2009-04-20
> **VMC said:**
> Here's the output you requested:

$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable

$ lspci -vvnn

00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
	Subsystem: Dell Device [1028:0151]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at ed98 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

You're suffering from the bug. Open a new file:
```
$ gedit fixmtrr.sh
```

Paste the following text into this file, and save:
```
#!/bin/sh
echo "Before:"
echo "-------"
cat /proc/mtrr
echo "base=0xE8000000 size=0x08000000 type=write-combining" >| /proc/mtrr
echo ""
echo "After:"
echo "------"
cat /proc/mtrr

```

Make the script executable, and then move it into your local binary folder:
```
$ chmod +x fixmtrr.sh
$ sudo mv fixmtrr.sh /usr/local/bin
```

Finally, execute the script:
```
$ sudo fixmtrr
```

You'll see some output detailing your MTRR ranges before and after the tweak.

Note: you'll need to execute this script each time you restart your PC or Xorg.

Try to play some content in Totem and see if the stuttering has stopped. If you can clearly see this helps, please consider reporting your results on the [bug report]("https://bugs.launchpad.net/bugs/314928"), attaching the relevant logs as [Bryce]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/1") requested.

---

### Post by VMC on 2009-04-20
Thanks for your help, but that didn't work either. It plays as though frames are missing. still choppy, or the same same speed as without the fix.

I'm interested in that "Tiling" fis you presented. I wonder why my screen freezes? The mouse moves but nothing works.

Everything works perfectly using the old Harty xorg.conf, EXCEPT no video movies. Screen refreshes fast I can surf the net with speed scroll through docs fine. Its just when I try and play any movies that any player crashes.

---

### Post by psyke83 on 2009-04-20
> **VMC said:**
> Thanks for your help, but that didn't work either. It plays as though frames are missing. still choppy, or the same same speed as without the fix.

I'm interested in that "Tiling" fis you presented. I wonder why my screen freezes? The mouse moves but nothing works.

Everything works perfectly using the old Harty xorg.conf, EXCEPT no video movies. Screen refreshes fast I can surf the net with speed scroll through docs fine. Its just when I try and play any movies that any player crashes.

I am almost 100% certain that your MTRR setup is causing slow video playback, so can you please paste the output of the fixmtrr.sh script (preferably output just after restarting Xorg)? I also recommend you disable compiz (Desktop Effects) to ensure it's not interfering.

It's possible that UXA is incompatible with your chipset, so maybe you should revert to EXA (by removing the "AccelMethod" line from xorg.conf).

Note that the MTRR fix is necessary regardless of the acceleration method, kernel or driver versions you're using. It affects all Intel graphics users, even with the default Jaunty drivers.

---

### Post by Triggerhapp on 2009-04-20
Did wonders for my graphics, sadly it took away my wireless drivers at the same point, so I'm going to be nosing around to find a work around for them :P

---

### Post by ameyer on 2009-04-20
> **psyke83 said:**
> 
Note that the MTRR fix is necessary regardless of the acceleration method, kernel or driver versions you're using. It affects all Intel graphics users, even with the default Jaunty drivers.
Not all Intel graphics users.  It's apparently unnecessary on my Dell Vostro 220 with an integrated X4500HD GPU.
However, UXA still has stability issues, at least without the tiling fix.

EDIT: With the tiling fix, it's worse.

---

### Post by olskar on 2009-04-20
Thanks mate! That made the little penguin race down the mountain with ~18 FPS instead of ~4 :)

Here is some output if good for anything (after applying the fix)

> cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable


> 
cat /proc/mtrr
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ec00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb


---

### Post by psyke83 on 2009-04-20
> **olskar said:**
> Thanks mate! That made the little penguin race down the mountain with ~18 FPS instead of ~4 :)

Here is some output if good for anything (after applying the fix)

Judging from your output, you'll need to modify the fixmtrr.sh script:

```
#!/bin/sh
echo "Before:"
echo "-------"
cat /proc/mtrr
**echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr**
echo ""
echo "After:"
echo "------"
cat /proc/mtrr
```

The part in bold has been customized for your system (graphics memory starting at 0xD0000000 with a size of 256MB, or 0x10000000).

If you're not sure it worked, modify the script and paste the output again.

---

### Post by stewacide on 2009-04-20
Awsome! Worked on this 82865G (8086:2572) where neither EXA or UXA would previously!!!

Compiz performance seems restored if not superior to Hardy, and Flash video is INFINITELY faster; anything sub-HD plays perfectly smoothly now without tearing where it was laggy under Intrepid and unwatchable under Jaunty.

---

### Post by _tom_ on 2009-04-21
Would be very nice to have a ppa for 2.7.0 intel drivers + libdrm

---

### Post by HankB on 2009-04-21
> **_tom_ said:**
> Would be very nice to have a ppa for 2.7.0 intel drivers + libdrm

I think this is an answer for the same question I have.

I really like staying within the package manager guidelines. I'm concerned that some ad hoc additions could result in problems if something comes along later via the package manager. I suppose installing .debs is a lot safer than tarballs in this regard. But what about access to kernel upgrades?

Are my concerns justified or is that just the price for better Intel video performance?

thanks,
hank

---

### Post by Oenologist on 2009-04-21
Forgive me if I mess up the topic...

I tried to apply the solution posted above, and I believe it would have worked, but there seems to be a conflict between my xorg and UXA, which might result from a critical crash that occured yesterday on my Kubuntu.

More info here - [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/364479](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/364479)

Any ideas how to force xorg to cooperate with UXA?

Currently I operate on the recommended packages from the first post, but I had to remove the UXA entry from xorg. Otherwise I wouldn't be able to log in.

---

### Post by psyke83 on 2009-04-21
> **HankB said:**
> I think this is an answer for the same question I have.

I really like staying within the package manager guidelines. I'm concerned that some ad hoc additions could result in problems if something comes along later via the package manager. I suppose installing .debs is a lot safer than tarballs in this regard. But what about access to kernel upgrades?

Are my concerns justified or is that just the price for better Intel video performance?

thanks,
hank

The packages in this guide are from Debian sid. Technically you shouldn't use these packages in Ubuntu (due to different dependencies, etc.), but in practice they work absolutely fine. It's trivial to downgrade these packages to the Jaunty versions using the instructions in the first post.

---

### Post by HankB on 2009-04-21
> **psyke83 said:**
> The packages in this guide are from Debian sid. Technically you shouldn't use these packages in Ubuntu (due to different dependencies, etc.), but in practice they work absolutely fine. It's trivial to downgrade these packages to the Jaunty versions using the instructions in the first post.
Thanks for the reply.

Would it make sense to add that repo to the sources.list in order to insure that updates are automagically made available? Should that be done with apt-pinning (of which my understanding is that those repos can be given a lower priority than the Ubuntu repos.) Or would that just open up a bigger can-O-worms?

My understanding is that the need to do this will likely remain until the next version of Ubuntu is released. If that is not correct, then perhaps my concerns are unwarranted.

thanks again,
hank

---

### Post by zevans on 2009-04-21
@oenologist:I just posted to your bug with a workaround that got me super-stable and reasonable performance for everything except games, and allows me to use kwin effects. It's stable under 2.6.28 and 2.6.30

@people asking about "offical" fixes: The consensus on the bug reports seems to be that major fixes to stability or performance regression WILL make it into jaunty-updates. The reason they aren't going into base Jaunty is simply unlucky timing - not likely to get UXA fixed in a supportable way until then. There are quite a few bugs marked with the jaunty-updates milestone, so when those get fixed there will be an approved Jaunty fix for them.

The problem at the moment is that different people get different results when they make the changes suggested here, and some people get the desired performance but then start seeing graphics corruption instead.

So until we've got to the bottom of all the bugs marked critical and found fixes for them that don't introduce NEW critical bugs (!) there won't be an "official" fix... but anything that can be identified and fixed in a stable way WILL be updated.

Looks likely that Jaunty itself will be released with UXA disabled by default because there are still so many unknowns. The lowest common EXA config that -works- for everyone will be deathly slow on some people's hardware, but there doesn't seem to be one config that is stable AND quick at the moment, and stable is definitely better than quick!

At least, that's how I understand it. :-)

---

### Post by HankB on 2009-04-21
> **zevans said:**
> 
@people asking about "offical" ... There are quite a few bugs marked with the jaunty-updates milestone, so when those get fixed there will be an approved Jaunty fix for them.

The problem at the moment is that different people get different results when they make the changes suggested here, and some people get the desired performance but then start seeing graphics corruption instead.


Good to know we won't have to wait for k<whatever> for a fix.

Judging by the mix of results, it seems that some testing would be helpful. To that end, I applied the fix as described in the first post (except for the MTRR fix.) It did seem to produce some improvement in frame rates in ppracer. However when I went to load the page with the description for the MTRR fix I found that I had no wireless. My wireless H/W (Eee PC 901) uses the rt2860sta module which is included in linux-image-2.6.28-11-generic but not linux-image-2.6.30-020630rc2-generic. (Someone noticed that the driver is non-free.) I checked the directory where the kernel was found and saw no non-free packages. It looks like I can do limited testing, but w/out wifi this netbook is not so useful. ;)

Edit; suggestions for the  command line to run ppracer as a benchmark would be most welcome. I can't seem to get beyond 
```
hbarta@bonsai:~$ ppracer -a
PPRacer 0.3.1 --  http://racer.planetpenguin.de 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

get fences failed: -1
param: 6, val: 0
Benchmark error: unable to set course:
``` 
There's a -f option that I can't seem to get to work.

thanks,
hank

---

### Post by stewacide on 2009-04-21
I'm also interested in a repo to keep the intel drivers at the bleeding edge. This fix has solved all regular compiz and video issues (tiling is giving me no problem either), but I notice Google Earth is massively corrupted (not sure if this extends to 3D games since I don't play them). If an update comes along that fixes this and other currently-unknown issues it'd be nice to get it automatically.

---

### Post by VMC on 2009-04-21
I just want to report here that I found a fix for my video problem.

Video card:
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

Solution was to revert back to Intel driver 2.4. Go [HERE]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") for explanation.

My video now exactly the same as it was using Hardy. Speed is the same. No more choppy avi, vob's. Everything works.

---

### Post by jongkind on 2009-04-21
> **VMC said:**
> I just want to report here that I found a fix for my video problem.

Video card:
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

Solution was to revert back to Intel driver 2.4. Go [HERE]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") for explanation.

My video now exactly the same as it was using Hardy. Speed is the same. No more choppy avi, vob's. Everything works.

I can confirm this.

---

### Post by windozehater on 2009-04-22
Works flawlessly! thank-you I had given up on jaunty because of that.

---

### Post by Mindless Automata on 2009-04-22
For amd64:

Download:
```

$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_amd64.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_amd64.deb http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_amd64.deb

```

Install
```

sudo dpkg -i linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb libdrm-intel1_2.4.9-1_amd64.deb xserver-xorg-video-intel_2.7.0-1_amd64.deb

```

Testing now to see how well it works...

---

### Post by Amaranth on 2009-04-22
Disabling tiling is probably not what you actually want. A lot of the complaints about poor 2D performance with 945 are due to tiling being disabled due to GEM not supporting the crazy memory layout needed.

---

### Post by psyke83 on 2009-04-22
> **Amaranth said:**
> Disabling tiling is probably not what you actually want. A lot of the complaints about poor 2D performance with 945 are due to tiling being disabled due to GEM not supporting the crazy memory layout needed.

Yes, I know. However, it causes DRI2 to break on my particular system (Dell Inspiron 510m, 855GM graphics), even though tiling has never caused problems before. I decided to keep this guide somewhat conservative in order to minimize problems for users.

---

### Post by dentaku65 on 2009-04-22
On my card
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
I kept the default Jaunty installation with UXA and false tiling in Xorg. The system is quite good, the only thing I found very bad is flash on web (ie. Youtube), the CPU goes to 100% :-(

I've tried the vanilla kernel 2.6.30rc2 and no problem at all for the performances (flash too); just my old notebook do fan spins all the time :-)
As usual I found the kernel here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/)

PS. I discovered now also this one:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/)
Did not tried yet.

---

### Post by Cimi86 on 2009-04-22
any chance for a lpia build?
I don't have i386 here...

---

### Post by dentaku65 on 2009-04-22
Good news (at least for me) :P
I've applied a silly trick to xorg.conf and now also flash is working properly :KS
> Section "Device"
	Identifier	"Configured Video Device"
        Option "AccelMethod" "UXA"
	[COLOR="Red"]VideoRam	65536[/COLOR]
EndSection
Yes. Putting the forgotten and deprecated option of VideoRam (in my case 64MB) in xorg.conf fixed everything here.

Kernel:
> 2.6.28-11-generic
VGA:
> 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Warning in xorg.0.log:
> (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000202 to 0x80000202
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
[COLOR="Red"](WW) intel(0): VideoRam configuration found, which is no longer recommended.[/COLOR]
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) intel(0): Chosen PLL clock of 66.5 Mhz more than 2% away from desired 65.0 Mhz
(WW) intel(0):   Hardware claims pipe A is on while software believes it is off


I did not touch /proc/mtrr
Hope this helps

---

### Post by crjackson on 2009-04-22
> **dentaku65 said:**
> Good news (at least for me) :P
I've applied a silly trick to xorg.conf and now also flash is working properly :KS

Yes. Putting the forgotten and deprecated option of VideoRam (in my case 64MB) in xorg.conf fixed everything here.

Kernel:

VGA:

Warning in xorg.0.log:


I did not touch /proc/mtrr
Hope this helps

So this is a standard install of Jaunty (stock kernel) and updates with only the xorg changes listed for UXA / 64MB?

---

### Post by dentaku65 on 2009-04-22
> **crjackson said:**
> So this is a standard install of Jaunty (stock kernel) and updates with only the xorg changes listed for UXA / 64MB?

Yes, correct.
Btw, as I post before in this thread my only big, big issue was only on flash video on the web.
Now VideoRam fix this too.

---

### Post by crjackson on 2009-04-22
> **dentaku65 said:**
> Yes, correct.
Btw, as I post before in this thread my only big, big issue was only on flash video on the web.
Now VideoRam fix this too.

Great! I've got a lot of testing to do this comming week. I've got my ATI carded lappy working -okay- :-s 

Now with all the information in this thread, I hope to get my Intel X3100 working well.

Mods, since this Forum Section will be closed tomorrow. Please make this HOWTO: an active sticky in the appropriate place.

---

### Post by volanin on 2009-04-22
> mods, since this forum section will be closed tomorrow. Please make this howto: An active sticky in the appropriate place.

+1

---

### Post by psyke83 on 2009-04-22
I tested the 2.6.30-rc3 kernel and performance is slightly worse than rc2 - therefore I won't change the original instructions in the guide.

P.S. I'll request this thread to be moved as soon as Jaunty is released and this forum archived.

---

### Post by psyke83 on 2009-04-22
> **dentaku65 said:**
> Yes, correct.
Btw, as I post before in this thread my only big, big issue was only on flash video on the web.
Now VideoRam fix this too.

Here's what happens for me:

```
(WW) intel(0): VideoRam configuration found, which is no longer recommended.
(II) intel(0): Continuing with default 131072kB VideoRam instead of 65536 kB.
```

I suspect that something else fixed the issue for you, as your output indicates that you filtered only for warnings (WW), whereas the override is mentioned as information (II).

Our graphics device is the same:

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

---

### Post by dentaku65 on 2009-04-23
> **psyke83 said:**
> Here's what happens for me:

```
(WW) intel(0): VideoRam configuration found, which is no longer recommended.
(II) intel(0): Continuing with default 131072kB VideoRam instead of 65536 kB.
```

I suspect that something else fixed the issue for you, as your output indicates that you filtered only for warnings (WW), whereas the override is mentioned as information (II).

Our graphics device is the same:

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Adding Videoram is the only action I did as far as I can say.
The output of (II) is the same here, but if I try to put in the xorg option
Videoram 131072
instead of
Videoram 65526
my machine cannot even starts xorg.

My VGA
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 106a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e0380000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

My /proc/mtrr
> reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x040000000 ( 1024MB), size=  256MB, count=1: write-back
reg02: base=0x050000000 ( 1280MB), size=  128MB, count=1: write-back
reg03: base=0x058000000 ( 1408MB), size=   64MB, count=1: write-back
reg04: base=0x05c000000 ( 1472MB), size=   32MB, count=1: write-back
reg05: base=0x05e000000 ( 1504MB), size=   16MB, count=1: write-back


---

### Post by thebestofall007 on 2009-04-23
dude, your solution worked wonders for me!!! i am actually able to use google earth on my intel 945gm card my acer aspire 5610z has. the solution didnt work at first, but what i did was disable the atmosphere in the google earth app by going to view and unchecking atmosphere. after that, GOOGLE EARTH FLIES, EVEN WITH COMPIZ ENABLED (before, i had problems with GE becoming all glitchy). not only does it work for GE, but my system is way faster, like when the system accesses files for example or multitasks. the pointer moves smoother across the screen, and scrolling is more fluid.

i also noticed that the system overall has better memory management. google earth no longer hogs my ram. 

the only problem i have is the fact that i no longer have a splash screen when the system boots up or shuts down. 

why is that?

---

### Post by dentaku65 on 2009-04-23
> **thebestofall007 said:**
> dude, your solution worked wonders for me!!! i am actually able to use google earth on my intel 945gm card my acer aspire 5610z has. the solution didnt work at first, but what i did was disable the atmosphere in the google earth app by going to view and unchecking atmosphere. after that, GOOGLE EARTH FLIES, EVEN WITH COMPIZ ENABLED (before, i had problems with GE becoming all glitchy). not only does it work for GE, but my system is way faster, like when the system accesses files for example or multitasks. the pointer moves smoother across the screen, and scrolling is more fluid.

i also noticed that the system overall has better memory management. google earth no longer hogs my ram. 

the only problem i have is the fact that i no longer have a splash screen when the system boots up or shuts down. 

why is that?

For the splashscreen you can use startupmanager utility
```
sudo apt-get install startupmanager
```
then
```
sudo startupmanager
```
put the resolution to 800x600 or 1024x768 and color depth at 16 bits. Ensure that splash theme is selected too.

---

### Post by Roger E Critchlow Jr on 2009-04-23
> **Mindless Automata said:**
> For amd64:

Download:
```

$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_amd64.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_amd64.deb http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_amd64.deb

```Install
```

sudo dpkg -i linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb libdrm-intel1_2.4.9-1_amd64.deb xserver-xorg-video-intel_2.7.0-1_amd64.deb

```Testing now to see how well it works...

These packages worked for me on my amd64 install of jaunty beta+upgrades.  Along with the mtrr fix they make google-earth work (do turn off the atmospheric effects) and compiz is much snappier.  Ppracer is a mess, I tried to run benchmark mode and it crashed leaving me in lowrez.

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)

Thanks, much helpful.

-- rec --

---

### Post by bapoumba on 2009-04-23
Moved out of Jaunty to Multimedia & Video.

The thread will be linked into one of the Jaunty stickies we will release soon :)

---

### Post by thebestofall007 on 2009-04-23
> **dentaku65 said:**
> For the splashscreen you can use startupmanager utility
```
sudo apt-get install startupmanager
```
then
```
sudo startupmanager
```
put the resolution to 800x600 or 1024x768 and color depth at 16 bits. Ensure that splash theme is selected too.

i tried that, no glory. just a black screen at boot/shutdown where the splash is supposed to be.

---

### Post by dentaku65 on 2009-04-23
> **thebestofall007 said:**
> i tried that, no glory. just a black screen at boot/shutdown where the splash is supposed to be.

If you are using 2.6.30rcX yes, there is no way to have splash screens

---

### Post by thebestofall007 on 2009-04-23
> **dentaku65 said:**
> If you are using 2.6.30rcX yes, there is no way to have splash screens

gotcha. however i have noticed that if i run kernel 2.6.28-11 i386 generic the uxa option still runs and i still have the performance gains of this solution, plus the splash screen. what is the difference between the 2.6.30rcX kernel and 2.6.28-11 i386 generic?

---

### Post by psyke83 on 2009-04-23
> **thebestofall007 said:**
> gotcha. however i have noticed that if i run kernel 2.6.28-11 i386 generic the uxa option still runs and i still have the performance gains of this solution, plus the splash screen. what is the difference between the 2.6.30rcX kernel and 2.6.28-11 i386 generic?

The 2.6.30-rc2 kernel gives approximately 4-5fps extra in ppracer for my 855GM chipset (the MTRR fix is necessary for maximum performance). I assume this is because there have been some bugfixes/optimizations in the DRM/i915 kernel modules.

Other chipsets may not see the same performance gains, though it's worthwhile at least to check the newer kernel.

---

### Post by thebestofall007 on 2009-04-23
uh oh, i found a bug in this solution. when i run it in itself, it works, but if i open google earth, open vlc, and then drag and drop songs into vlc media player to make a playlist, the system freezes. i am able to use the mouse but nothing responds to clicking. the strange thing is that i can open google earth alone with no problems as well as any other program (including firefox) with it. the freeze happens after some system lag and then the freeze. 

i find that commenting out the uxa option in the xorg.conf is a workaround. the performance is slightly slower but more stable and the freeze doesnt happen. however, even with uxa commented out, the system is still faster than with what i had before this solution.

---

### Post by Cimi86 on 2009-04-23
who could port this packages to the lpia arch?:guitar:

---

### Post by jcapitan on 2009-04-23
Um, I'm taking a step back...  This is a wonderful fix.  Thank you for making it available!   But this for a relatively standard video card, not a "vostok-omsk 3".  Can/Should a "regular" user who is trying U-9.04 for the 1st time be expected to do this? Just curious.....

---

### Post by volneilo on 2009-04-23
Anyone with i845 had success with these workarounds? I mean, success in making Compiz to work? 'Cause I had everything running well here when testing a Jaunty LiveUSB, **except** by Compiz.

---

### Post by DavidFourer on 2009-04-23
Can you tell me if the Intel integtrated graphics controller 915GM/GMS/910GML is affected?
I ran the live-CD and display was kind of a wreck, though it didn't crash.  I have not upgraded.  Intrepid is working so well.

edit: on 06-01-09 I did a fresh install of Jaunty--it's flawless out of the box.

:~$ lspci
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
:~$ cat /proc/mtrr  (Intrepid Ibix)
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0x3f800000 (1016MB), size=   8MB: uncachable, count=1
reg02: base=0xfeda0000 (4077MB), size= 128KB: write-through, count=1
reg03: base=0xc0000000 (3072MB), size= 256MB: write-combining, count=1

---

### Post by dentaku65 on 2009-04-23
> **psyke83 said:**
> The 2.6.30-rc2 kernel gives approximately 4-5fps extra in ppracer for my 855GM chipset (the MTRR fix is necessary for maximum performance). I assume this is because there have been some bugfixes/optimizations in the DRM/i915 kernel modules.

Other chipsets may not see the same performance gains, though it's worthwhile at least to check the newer kernel.

This is correct for 2.6.30rc2 but on rc3 I experienced a regression with my card. Anyway I'm stay fine with 2.6.29-11 with videoram option (I forgot to mention that my box is on EXT4, but maybe is not important for video configuration/performance)

---

### Post by caish5 on 2009-04-24
It would be nice if someone could explain the MTRR fix in simple terms. I got a bit lost on those links. The other tweaks worked fairly well but i still get some tearing and slowness particularly with HD video. I'm using this graphics card.....
> 
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)


---

### Post by psyke83 on 2009-04-24
> **caish5 said:**
> It would be nice if someone could explain the MTRR fix in simple terms. I got a bit lost on those links. The other tweaks worked fairly well but i still get some tearing and slowness particularly with HD video. I'm using this graphics card.....

You didn't give enough information to help you. What you need to do is check the check the memory regions of your graphics adaptor using "lspci -vvnn", and find the "prefetchable" memory range.

Look at [this]("http://ubuntuforums.org/showpost.php?p=7104663&postcount=10") post. In the aforementioned post, the important line in the lspci output of the "VGA compatible controller" section is as follows:
```
Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
```

Keep in mind:
128MB = 0x08000000
256MB = 0x10000000

In this example the base memory address is at 0xE8000000, and the memory size is 0x08000000. Therefore, the fixmtrr.sh script contains the line:
```
echo "base=0xE8000000 size=0x08000000 type=write-combining" >| /proc/mtrr
```

All you need to do is follow the steps of that post, while remembering to write the correct base memory and size for your system.

---

### Post by glaze on 2009-04-24
Does there exist a PPA that has xserver-xorg-video-intel version 2.7 64-bit for 9.04 (Jaunty)?

---

### Post by Zorael on 2009-04-24
I made a script that adds the mtrr entry, and added it to /etc/sudoers so I can perform it without needing a password. Then I just added a symlink in ~/.kde/Autostart and now it gets run even after an X restart.

Lastly, I added that [2.4 repository](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) to get the old driver. And damn. Now I can watch flash again.

---

### Post by Zorael on 2009-04-24
> **glaze said:**
> Does there exist a PPA that has xserver-xorg-video-intel version 2.7 64-bit for 9.04 (Jaunty)?
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Drivers compiled from git semi-daily. Latest is from 22/04. If you want fresher than that, you'll have to compile them yourself (which isn't hard, though).

All launchpad ppas compile packages for i386, amd64 and lpia.

---

### Post by caish5 on 2009-04-24
> 00:02.0 VGA compatible controller [0300]: Intel Corporation 82G35 Express Integrated Graphics Controller [8086:2982] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8276]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at fe800000 (32-bit, non-prefetchable) [size=1M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at cc00 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller [0380]: Intel Corporation 82G35 Express Integrated Graphics Controller [8086:2983] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8276]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>


I keep getting
bash: echo: write error: Invalid argument
Any ideas?

---

### Post by JamesHowlett on 2009-04-24
> **dentaku65 said:**
> Good news (at least for me) :P
I've applied a silly trick to xorg.conf and now also flash is working properly :KS

Yes. Putting the forgotten and deprecated option of VideoRam (in my case 64MB) in xorg.conf fixed everything here.


I actually tried this without doing any of the major changes that were detailed in the first post.  While I can't exactly tell for sure if my graphics are back to the way they were in Intrepid, I can definitely say there's a pretty noticeable improvement over my fresh install of Jaunty.  Thanks for the tip.

---

### Post by onlyconnect on 2009-04-24
I fixed my problem (DRI not enabled) by temporarily booting into an older version of the kernel. Strange. Note I am NOT using UXA.

See: [http://www.itwriting.com/blog/1358-ubuntu-904-not-so-jaunty.html](http://www.itwriting.com/blog/1358-ubuntu-904-not-so-jaunty.html)

Tim

---

### Post by HankB on 2009-04-24
> **Zorael said:**
> 
All launchpad ppas compile packages for i386, amd64 and **lpia**.
Could this be a source for kernel and X server compiled for lpia? Is there some place where other than cutting edge builds are available?

I'm running Jaunty on an Intel Atom (Eee PC 901) and understand it could benefit from those optimizations.

The only thing I see in the normal i386 repos with lpia in the name is installation-guide-lpia. It describes where to find the installer and lpia does not exist for Jaunty.

Apologies for the semi-hijack.

thanks,
hank

---

### Post by StorMFreak on 2009-04-24
So, any help would be greatly appreciated!  I'm not sure if my issue is related to this or not.  I have a Asus EeePC 1000H and just installed 9.04 NBR last night.  The laptop has a Intel GMA 950, and I am noticing a lot of flickering on the screen.  It's not unbearable, but it's definitely irritating.  It also seems that it's just laggy in general, and I'm guessing the video issue has something to do with it.  Will the original poster's tips help me, or should I be looking down a different route?  Thanks!

---

### Post by HankB on 2009-04-24
> **StorMFreak said:**
> ... I have a Asus EeePC 1000H and just installed 9.04 NBR last night.  The laptop has a Intel GMA 950, and I am noticing a lot of flickering on the screen.

Can you elaborate on that? I have an Eee PC 901 with Intel 945GME graphics:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
```

When I run Firefox full screen (<F11>) and right click anywhere on the screen, the desktop background flashes briefly and the screen returns to the normal display. This also happens when I click the  forum jump menu near the bottom of the screen. It also happens at other times, but either of these two actions seem to provoke it 100% of the time. 

Is this the screen flicker that you are seeing?

I just tried applying the fixes described in the first post in this thread and that does not seem to make a difference. I wonder if this is a Firefox problem or the video drivers and how I can pursue a solution. On a 1024x600 screen it is really nice to use the full screen mode.

Aha! In a flash of inspiration, I went to System -> Preferences -> Appearance and switched visual effects from normal to none: No more flicker!

I'm guessing this means the problem is with the video driver (AKA X server.)

-hank

---

### Post by bittergourd on 2009-04-24
applying this change disables the brightness function key on thinkpad t61.  apparently only under the original combination of kernel and intel driver, and with 2.4 driver, this function key works.  either 2.6.30 kernel or 2.7 intel driver breaks it.

i am excited about this because for the first time, blur in compiz actually works, with pretty bad speed though.  

i am under gnome.  the original upgrade did not bother me much, although i noticed some slight performance reduce when maximizing or minimizing window.

---

### Post by JamesHowlett on 2009-04-24
> **HankB said:**
> 
Is this the screen flicker that you are seeing?

I just tried applying the fixes described in the first post in this thread and that does not seem to make a difference. I wonder if this is a Firefox problem or the video drivers and how I can pursue a solution. On a 1024x600 screen it is really nice to use the full screen mode.

Aha! In a flash of inspiration, I went to System -> Preferences -> Appearance and switched visual effects from normal to none: No more flicker!

I'm guessing this means the problem is with the video driver (AKA X server.)

-hank

Perhaps you are right. After doing that Videoram option, while it stopped the lag, the flickering that you describe exists for me when I do the right click with firefox on fullscreen too.

---

### Post by StorMFreak on 2009-04-24
My flicker issue actually looks like there is a loose cable.  I have read on some other topics, and it sounds like it may be due to my wireless driver (unfortunately the alternate madwifi is not working at all...)

As far as my video full screen flash is unwatchable due to lag... So even if wireless is causing the flickering, I still think I have some video issues (not to mention how hot my eeePC gets now!)

---

### Post by map84 on 2009-04-24
As described on this page,

[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance regressions on Intel graphics cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance regressions on Intel graphics cards)

i added the line, displayed in bold, to my xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	**Option		"MigrationHeuristic"	"greedy"**
EndSection
```

Without the line i got ~5 fps in ppracer, with this Option i get ~20 fps.

(edit) But playing videos in fullscreen-mode with totem leading to a restart of the x-server.

---

### Post by dentaku65 on 2009-04-24
> **JamesHowlett said:**
> Perhaps you are right. After doing that Videoram option, while it stopped the lag, the flickering that you describe exists for me when I do the right click with firefox on fullscreen too.
If you are using Compiz, try in settings/preferences/compiz config settings manager under general tab uncheck Unredirect fullscreen :)

---

### Post by RehabDJ on 2009-04-24
Thanks dentaku65.  That fixed my flicker from full screen Firefox and desktop.  Just a n00b to the OS, but getting into it thanx to the community. :)

---

### Post by emnii on 2009-04-24
THANKS! This fix worked wonders on my Dell Mini 9 and now everything runs nice and smooth again!

---

### Post by stukpixel on 2009-04-24
Does not work- on restart, ubuntu would not even boot up.

I had to boot into the older kernel for to roll back the changes.

---

### Post by JamesHowlett on 2009-04-24
> **dentaku65 said:**
> If you are using Compiz, try in settings/preferences/compiz config settings manager under general tab uncheck Unredirect fullscreen :)

Awesome. Thanks, that did the trick.

---

### Post by ElSlunko on 2009-04-24
The OPs fix worked well for me. The UXA change made an initial huge improvement. The newer drivers made another strong improvement (HD clips on youtube are no longer choppy). Too bad World of Warcraft still isn't playable on my Intel GMA 950. I believe opengl is buggy on this card.

---

### Post by JamesHowlett on 2009-04-25
> **ElSlunko said:**
> The OPs fix worked well for me. The UXA change made an initial huge improvement. The newer drivers made another strong improvement (HD clips on youtube are no longer choppy). Too bad World of Warcraft still isn't playable on my Intel GMA 950. I believe opengl is buggy on this card.

Would that fix work using the vanilla kernel for jaunty and the newer versions of  libdrm2, libdrm-intel1 and xserver-xorg-video-intel together?

---

### Post by psyke83 on 2009-04-25
> **JamesHowlett said:**
> Would that fix work using the vanilla kernel for jaunty and the newer versions of  libdrm2, libdrm-intel1 and xserver-xorg-video-intel together?

Jaunty's kernel has a regression in the DRM kernel module that impedes performance, unfortunately. However, updating the drivers and enabling UXA alone can give a performance boost (mostly 2D) over the stock Jaunty configuration.

---

### Post by psyke83 on 2009-04-25
Hey,

I've made a major update to the guide (added amd64 support, and moved towards using newer drivers from the xorg-edgers PPA). If you're interested, take a look at the guide again.

---

### Post by ElSlunko on 2009-04-25
> **psyke83 said:**
> Hey,

I've made a major update to the guide (added amd64 support, and moved towards using newer drivers from the xorg-edgers PPA). If you're interested, take a look at the guide again.

Thanks psyke83!

---

### Post by JamesHowlett on 2009-04-25
> **ElSlunko said:**
> Thanks psyke83!

Indeed.  Thanks for the effort you're putting into this.

---

### Post by S.A.A on 2009-04-25
I finally found a way to run compiz with:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

```
all you have to do is using "Indirect Rendering" option.
And now my old PC is back to life again (it's even faster than it was with Hardy).

---

### Post by hebeallrusty on 2009-04-25
just to say the bit that says alter the xorg.conf file:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" [b]#may break 3D rendering if enabled
EndSection
```

should not have the [b] before the # so should read
```
**	Option		"Tiling"			"false" #may break 3D rendering if enabled**
```
Though I'd killed my system when it wouldn't run X until i spotted that

---

### Post by psyke83 on 2009-04-25
> **hebeallrusty said:**
> just to say the bit that says alter the xorg.conf file:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" [b]#may break 3D rendering if enabled
EndSection
```

should not have the [b] before the # so should read
```
**	Option		"Tiling"			"false" #may break 3D rendering if enabled**
```
Though I'd killed my system when it wouldn't run X until i spotted that

Fixed, thanks!

---

### Post by noobaholic on 2009-04-25
Following the instructions, when I get to the apt-get update step, I get this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542
W: You may want to run apt-get update to correct these problems

Any ideas?

---

### Post by psyke83 on 2009-04-25
> **noobaholic said:**
> Following the instructions, when I get to the apt-get update step, I get this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542
W: You may want to run apt-get update to correct these problems

Any ideas?

The guide was fetching a different key than I intended, sorry. I've updated the guide with the proper key - follow that step again.

---

### Post by noobaholic on 2009-04-25
Works now. Thanks!

---

### Post by noobaholic on 2009-04-25
OK, so I followed the rest of the instructions. My machine boots to an error message:

"Ubuntu is running in low-graphics mode

...

(EE) intel(0) Cannot support DRI with framebuffer width > 2048."

Then I get a few more error messages and my video out no longer works (using a macbook with a DVI piping video to an external monitor).

EDIT:

Seems to be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859)

EDIT:

So I toned down my virtual display to 1900x1280 to workaround the DRI bug and... wow, my machine is really fubared... Now it seems if I boot at all with my external monitor attached, the OS locks up as soon as X starts. :(

---

### Post by dentaku65 on 2009-04-25
I've inserted a different HowTo for Intel video on Jaunty
[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)
I hope psyke83 put the link in the 1st post :-)

---

### Post by noobaholic on 2009-04-25
Maybe my configs weren't quite right when the machine was freezing, because now, with a display size of 1900x1280, I can use my external fine. Of course, the new kernel breaks my sound and my wifi :-/ but a functional video card is more important.

dentaku65, what's the rationale behind your method? Maybe I'll try it out later today.

---

### Post by volneilo on 2009-04-25
> **S.A.A said:**
> I finally found a way to run compiz with:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

```
all you have to do is using "Indirect Rendering" option.
And now my old PC is back to life again (it's even faster than it was with Hardy).

**S.A.A.**, this is the answer I was looking for! [-o<

How can I do this? Some parameter in xorg.conf?

---

### Post by psyke83 on 2009-04-25
> **volneilo said:**
> **S.A.A.**, this is the answer I was looking for! [-o<

How can I do this? Some parameter in xorg.conf?

It's a GConf key. Open gconf-editor and navigate to: /apps/compiz/general/screen0/options/unredirect_fullscreen_windows

Alternatively, install ccsm (Compiz Settings Manager).

---

### Post by densou on 2009-04-25
some users, who own i915 or later, told me that 'videoram' option didn't affect at all their experience while I received good news from i8xx users.

I'm under UXA (NO exaoptmizemigration/migrationheuristic enabled) at this time. It works flawless :KS however I noticed an awful video output after upgrading to new 2.7.0 on SD sources only, not HD ones :( (Jaunty Kernel+GMA950)
(now avaiable on both: [Intel PPA]("http://launchpad.com/~intel-gfx-testing/+archive") and [X-Swat PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/") - .deb !)

Perhaps many G3x/G4x might solve their tearing issue: I have just installed Gnome Mplayer 0.9.5 (from .deb) and .... never seen anything better ! :guitar:

:)

> **noobaholic said:**
> (EE) intel(0) Cannot support DRI with framebuffer width > 2048.

extract from [Intel Linux's webpage]("http://intellinuxgraphics.org/2009Q1.html"):

[I]known issues
Work in progress:
- UXA/DRI2:
* Virtual screen size limited to **2048x2048** for _pre-965_ platforms: bug#21190.[/I]

:(

---

### Post by volneilo on 2009-04-25
> **psyke83 said:**
> It's a GConf key. Open gconf-editor and navigate to: /apps/compiz/general/screen0/options/unredirect_fullscreen_windows

Alternatively, install ccsm (Compiz Settings Manager).

Ok. So, Indirect rendering = unredirect_fullscreen_windows ? 'Cause I found "unredirect fullscreen windows" under ccsm, and it's **enabled**. Should I disable it? It's the same that using "Indirect Rendering"?

---

### Post by psyke83 on 2009-04-25
> **densou said:**
> some users, who own i915 or later, told me that 'videoram' option didn't affect at all their experience while I received good news from i8xx users.


I've got an 855GM chipset and the VideoRAM parameter is ignored - my logs show that any value I select is overridden. Nevertheless, I tested for any changes and found none. See [here]("http://ubuntuforums.org/showpost.php?p=7142887&postcount=4").

> I'm under UXA (NO exaoptmizemigration/migrationheuristic enabled) at this time. It works flawless :KS however I noticed an awful video output after upgrading to new 2.7.0 on SD sources only, not HD ones :( (Jaunty Kernel+GMA950)
(now avaiable on both: [Intel PPA]("http://launchpad.com/~intel-gfx-testing/+archive") and [X-Swat PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/") - .deb !)

The EXAOptimizeMigration and MigrationHeuristic options only take effect if you're using EXA acceleration. Under UXA, they're ignored.

The PPAs you listed ship more recent milestone releases (e.g. the 2.7.0 driver), whilst the xorg-edgers repository is more bleeding-edge. The latter is more interesting for our purposes.

> Perhaps many G3x/G4x might solve their tearing issue: I have just installed Gnome Mplayer 0.9.5 (from .deb) and .... never seen anything better ! :guitar:

Tearing may be caused by a bug in the textured Xv output. Changing it to Xv Overlay will probably help (at the expense of making video playback conflict with compiz).

Your issue is probably also related to MTRR ranges not being set correctly - this has nothing to do with your system's media players. See the bug report linked to this guide, and you'll find that your system is affected too...

> extract from [Intel Linux's webpage]("http://intellinuxgraphics.org/2009Q1.html"):

[I]known issues
Work in progress:
- UXA/DRI2:
* Virtual screen size limited to **2048x2048** for _pre-965_ platforms: bug#21190.[/I]

:(

Thanks for the information!

---

### Post by smbm on 2009-04-25
This did the trick for me on AMD64 with X3100.

My brightness hot keys no longer work but the perceived speed increase is astonishing.

---

### Post by Tukker on 2009-04-25
Just applied the guide from the first post to my Dell Latitude D610 and it seems to have done the trick for now. Hoping I will not discover any instability issues. Will report back.

---

### Post by volneilo on 2009-04-25
> **psyke83 said:**
> It's a GConf key. Open gconf-editor and navigate to: /apps/compiz/general/screen0/options/unredirect_fullscreen_windows

Alternatively, install ccsm (Compiz Settings Manager).

Folks, I'm really sorry for insist in this very noob question but... I disabled the option **"unredirect_fullscreen_windows"** through GconfEditor. Unfortunately didn't worked for me. So, if it was all I needed to do in order to try **S.A.A.'s** suggestion (I'm not sure about that), I'm back to the start.

Thanks a lot for your patience! :)

---

### Post by S.A.A on 2009-04-25
Hy volneilo, Open the terminal and type:
```
compiz --indirect-rendering --replace
```

---

### Post by volneilo on 2009-04-25
> **S.A.A said:**
> Hy volneilo, Open the terminal and type:
```
compiz --indirect-rendering --replace
```

**S.A.A**, thanks a lot for the response.

Unfortunately, although my card is exactly the same as yours, that command lead me to a wallpaper-only screen and a mouse pointer. Did you do something else, some xorg.conf modification? Or everything else is out-of-the-box settings in your system?

Oh, I forgot to mention... I'm tryng all of this in a LiveUser session through as USB stick; dont know if it is relevant...

---

### Post by S.A.A on 2009-04-25
> **volneilo said:**
> **S.A.A**, thanks a lot for the response.

Unfortunately, although my card is exactly the same as yours, that command lead me to a wallpaper-only screen and a mouse pointer. Did you do something else, some xorg.conf modification? Or everything else is out-of-the-box settings in your system?

Oh, I forgot to mention... I'm tryng all of this in a LiveUser session through as USB stick; dont know if it is relevant...

Ok, first you must do all the instructions psyke83! had posted (especially xorg driver).

---

### Post by ripps818 on 2009-04-25
This How-to shouldn't be telling users to install packages from debian. The intel testing PPA has the packages need: [https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa](https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa)

[https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa/+files/libdrm2_2.4.1-0ubuntu7~intrepid_i386.deb](https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa/+files/libdrm2_2.4.1-0ubuntu7~intrepid_i386.deb)
[https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa/+files/libdrm-intel1_2.4.9-1ubuntu1~xup~1_i386.deb](https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa/+files/libdrm-intel1_2.4.9-1ubuntu1~xup~1_i386.deb)
[https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa/+files/xserver-xorg-video-intel_2.7.0-1ubuntu1~xup~1_i386.deb](https://edge.launchpad.net/~intel-gfx-testing/+archive/ppa/+files/xserver-xorg-video-intel_2.7.0-1ubuntu1~xup~1_i386.deb)

---

### Post by volneilo on 2009-04-25
> **S.A.A said:**
> Ok, first you must do all the instructions psyke83! had posted (especially xorg driver).

Thanks again, **S.A.A**. I now realize that I must install Jaunty in order to try this, because I'm not able to boot into the new kernel in a Live User session.

Taking courage...

---

### Post by Alpha UMa on 2009-04-25
psyke83 I love you! :lolflag:
I'm using a 945GM [8086:27a2]. I tryed everything before, even to revert Xorg intel driver to 2.4, but nothing worked well enough. I was almost to give up with Jaunty, until I found your guide and it worked! Not even Hardy was so fast. 2D scrolling is really smooth, 3D is fast: my Tux races at ~25 - 35 fps instead of ~10 - 25 FPS with the standard Jaunty kernel and UXA enabled. 
Some games under Wine (ie IL-2) are extremely slow if Tiling is disabled. I tested it, as suggested on your guide, and luckly my box works without any issues with Option "Tiling" "true", so all my Wine games run smoothly now.

Thank you very much! =D> :)

---

### Post by celr on 2009-04-25
Hi, just to let you know this works like a charm on my 945GM :). Thanks.

---

### Post by Mr_bleu on 2009-04-25
I haven't been able to edit my xorg file since 8.04 or maybe even before that one.  Please help.  I miss playing Eternal-Lands.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by SteveMcQwark on 2009-04-25
Thanks! This works great! Now everything is zippier than it was in Intrepid :) One minor quibble: is there any way to re-enable usplash afterwards? For some reason, its disabled. I've tried using SUM, but that doesn't seem to have anything to do, so...

---

### Post by Mr_bleu on 2009-04-25
djr@popeye-laptop:~/elc$ ./el.x86.linux.bin
Failed to initialize GEM.  Falling back to classic.
el.x86.linux.bin: intel_tex_image.c:355: intelTexImage: Assertion `texImage->RowStride == postConvWidth' failed.
Aborted

I've installed xorg 2.4 and I still can't get eternal lands working.  It was playing fine before the update.

---

### Post by psriram on 2009-04-25
My problem goes like this 

Intel 845GVSR with on board graphics 
downloaded the iso from ubuntu website and installed as fresh copy

Ubuntu 8.04 and 8.10 starts the installation with GUI but 9.04 was unable to detect my vga and installation went on the text mode.
installed all the packages via aptitude and x11 is installed.

Now,
When boot up x window is not starting up instead login enabled using tty's

i tried to do this

sudo startx

but result was command not found

its says xinit package not installed and am trying to do this

sudo apt-get install xinit

cd reads and says similar package x11-common is installed

what might be the problem of X window starting? how to go ahead and fix it ?

---

### Post by Mr_bleu on 2009-04-26
I formatted and installed 8.10.  Game's working again.  Sad that Jaunty was released and crippled intel's already poor 3d graphics.  I tried both rc2 and rc3 kernels.  And a few different "fixes" from this thread.  I've installed the latest version of Ubuntu each time they release one since 6.04.

---

### Post by rikxik on 2009-04-26
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


Base install of Jaunty with Compiz enabled had lots of lag/sluggishness. The mtrr fix (see first post)  + adding below lines to /etc/X11/xorg.conf has improved the performance a lot:

```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
EndSection

```

I removed the tiling option since it caused slowness. No kernel changes or downgrading of Intel drivers was done. Hope this is useful to anyone with similar graphics.

---

### Post by Arup on 2009-04-26
> **Mr_bleu said:**
> I formatted and installed 8.10.  Game's working again.  Sad that Jaunty was released and crippled intel's already poor 3d graphics.  I tried both rc2 and rc3 kernels.  And a few different "fixes" from this thread.  I've installed the latest version of Ubuntu each time they release one since 6.04.

Actually its my observation that on Intel cards, Hardy runs best.

---

### Post by jbernardo on 2009-04-26
On a Acer Aspire One, running jaunty with kernel 2.6.28sickboy-kuki (have yet to try with 2.6.30rc, as recommended here) I get 31FPS in glblur with EXA and 14 with UXA, even with xorg-edgers ppa drivers.

```
/usr/lib/xscreensaver/glblur -window -fps

```For now things are good enough with exa.

ppracer gave me 7-12 fps with exa, 3-5 with uxa. Time to download and test kernel 2.6.30 with sickboy config.

---

### Post by kennyschiff on 2009-04-26
I'm a noob. I'm reluctant to upgrade the kernel and would like to use 2.6.28-11 first but with latest intel video drivers. I updated my PPA list, imported the PGP key, but can't seem to figure out how to install the driver. If someone could nudge me in the right direction, I'd appreciate it.

---

### Post by pappfer on 2009-04-26
> **kennyschiff said:**
> I'm a noob. I'm reluctant to upgrade the kernel and would like to use 2.6.28-11 first but with latest intel video drivers. I updated my PPA list, imported the PGP key, but can't seem to figure out how to install the driver. If someone could nudge me in the right direction, I'd appreciate it.

Just go to System -> Administration -> Updates and refresh it.
The system will show you the newest Intel video driver in case if you've added the PPA properly.
It didn't make any difference to me using the new (2.7) video driver with the default kernel in Jaunty, though.


PS: Like Mr_bleu I've always installed the latest version of Ubuntu each time they released one, but now I'm really thinking about going back to Intrepid or Hardy. :(

---

### Post by gus.ke on 2009-04-26
Alright, so I tried this, but it screwed up my wifi drivers so I reverted.  But now, i see a bunch of text every time I boot up telling me what the computer is doing.  How do I turn this back off???

---

### Post by glaze on 2009-04-26
Just reporting that using xserver-xorg-video-intel 2.7 and kernel 2.6.30-rc3 seems to have fixed my vsync and occasional pixel distortion problems on G45 (X4500HD, EXA, 64-bit Kubuntu) :KS

---

### Post by pappfer on 2009-04-26
> **glaze said:**
> Just reporting that using xserver-xorg-video-intel 2.7 and kernel 2.6.30-rc3 seems to have fixed my vsync and occasional pixel distortion problems on G45 (X4500HD, EXA, 64-bit Kubuntu) :KS
Great! Does updating kernel have any disadventages? Do Ubuntu use some patches in their kernel which I'll miss when updating it? If so, what are they?

---

### Post by psyke83 on 2009-04-26
> **pappfer said:**
> Great! Does updating kernel have any disadventages? Do Ubuntu use some patches in their kernel which I'll miss when updating it? If so, what are they?

Yes. The kernel is a bleeding-edge release candidate, and it's not supported at all. Don't bother filing any bugs on Launchpad with this kernel (and drivers from the PPA), don't expect usplash to work, don't be surprised if some restricted/wifi drivers don't work, etc.

The guide has downgrade instructions to restore your system to normal for a reason.

---

### Post by psyke83 on 2009-04-26
> **glaze said:**
> Just reporting that using xserver-xorg-video-intel 2.7 and kernel 2.6.30-rc3 seems to have fixed my vsync and occasional pixel distortion problems on G45 (X4500HD, EXA, 64-bit Kubuntu) :KS

2.6.30-rc3 has a performance regression compared to 2.6.30-rc2, which is why I didn't update the instructions to install the newer kernel.

---

### Post by psyke83 on 2009-04-26
> **kennyschiff said:**
> I'm a noob. I'm reluctant to upgrade the kernel and would like to use 2.6.28-11 first but with latest intel video drivers. I updated my PPA list, imported the PGP key, but can't seem to figure out how to install the driver. If someone could nudge me in the right direction, I'd appreciate it.

The instructions will upgrade the driver. Honestly, I placed a warning in the guide for a reason. 

This guide was intended mostly for people who know how to navigate the terminal, fix a broken X, etc. Installing a bleeding-edge kernel and unsupported drivers is not recommended for most users.

---

### Post by glaze on 2009-04-26
> **psyke83 said:**
> 2.6.30-rc3 has a performance regression compared to 2.6.30-rc2, which is why I didn't update the instructions to install the newer kernel.
I didn't know it when I compiled it, but no big deal, rc4 should be out soon.

---

### Post by pappfer on 2009-04-26
> **psyke83 said:**
> Yes. The kernel is a bleeding-edge release candidate, and it's not supported at all. Don't bother filing any bugs on Launchpad with this kernel (and drivers from the PPA), don't expect usplash to work, don't be surprised if some restricted/wifi drivers don't work, etc.

Is it because that the kernel is still RC? I mean will usplash and others work on stable kernels?
Is there a significant difference on the Intel graphics cards' performance between using Jaunty's default kernel and the new 2.6.30 RC2 kernel?

Glxgears gives me better results (higher FPSs) when using EXA while most people say that UXA gives them a great performance increase. I wonder why. I know, glxgears is not a benchmark!

BTW [I found a kernel PPA]("https://launchpad.net/~kernel-ppa/+archive/ppa") but it's not updated for Jaunty yet. Is there a kernel PPA for Jaunty?

---

### Post by umaxtu on 2009-04-26
Had there beeny any word on an official fix?

---

### Post by psyke83 on 2009-04-26
> **pappfer said:**
> Is it because that the kernel is still RC? I mean will usplash and others work on stable kernels?
Is there a significant difference on the Intel graphics cards' performance between using Jaunty's default kernel and the new 2.6.30 RC2 kernel?

Glxgears gives me better results (higher FPSs) when using EXA while most people say that UXA gives them a great performance increase. I wonder why. I know, glxgears is not a benchmark!

BTW [I found a kernel PPA]("https://launchpad.net/~kernel-ppa/+archive/ppa") but it's not updated for Jaunty yet. Is there a kernel PPA for Jaunty?

See: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I recall reading somewhere that the developers didn't want to make it "too easy" to upgrade a kernel from a PPA, so they placed them in regular directories.

---

### Post by umaxtu on 2009-04-26
> **psyke83 said:**
> See: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

I recall reading somewhere that the developers didn't want to make it "too easy" to upgrade a kernel from a PPA, so they placed them in regular directories.

So now that we've run out of government conspiracy theories were onto Linux conspiracy theories? :lolflag:

---

### Post by montamer on 2009-04-26
hi ;can i enable "UXA" in 2.6.28-11 kernel or do i need 2.6.30?
it seems to work fine when enable in 2.6.28-11-generic (deafult kernel) also

---

### Post by psyke83 on 2009-04-26
> **montamer said:**
> hi ;can i enable "UXA" in 2.6.28-11 kernel or do i need 2.6.30?
it seems to work fine when enable in 2.6.28-11-generic (deafult kernel) also

Yes. I recommend you test the 2.6.30-rc2 kernel to see if there is a performance increase, though. Don't forget that you can choose the kernel in GRUB upon boot, and it's trivial to remove the 2.6.30-rc2 kernel packages later.

---

### Post by umaxtu on 2009-04-26
I tried following these instructions earlier and the end result was that it froze when ever i Logged on or it never let me logged on.

---

### Post by uniontroublemaker on 2009-04-26
Thanks!  I am back in business on Dell laptop.  Wireless did not work booting into 2.6.30-rc2 kernel, but everything appears to work now booting into 2.6.28 kernel.

---

### Post by marco1986 on 2009-04-26
thank you very much!

This howto fixed my notebook (sony vaio vgn-cr410e) and also my day :)

I followed all of those step (also enabling tiling - didn't break 3d).

I will spread the word to all kubuntu 9.04 users with intel video cards.

Once again, many thanks!

---

### Post by inobe on 2009-04-26
> **marco1986 said:**
> thank you very much!

This howto fixed my notebook (sony vaio vgn-cr410e) and also my day :)

I followed all of those step (also enabling tiling - didn't break 3d).

I will spread the word to all kubuntu 9.04 users with intel video cards.

Once again, many thanks!

hey congrats marco, i am glad i directed you here.

---

### Post by progre55 on 2009-04-26
Worked well for me, thanks a lot! The ppracer fps is about ~80, while it used to be around 40.
However, after switching to the 2.6.30 kernel and installing the startupmanager, I don't see any splashscreen on startup and most importantly, when everything is up and running, I cannot switch using CTRL+ALT+F1 ... F6. It just shows a blank black screen.

Can anybody suggest anything here, please?

---

### Post by markbl on 2009-04-26
Thanks psyke83. Following your guide here exactly *massively* improved my machine responsiveness, youtube, etc. I have "VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)".

One litte thing though - to run a second monitor off my laptop I have to manually set a  "Virtual 2720 1024" in my Display subsection of my xorg.conf. After implementing your changes my X died on first restart telling me that the "Virtual specification was incompatible with DRI" so I commented out the virtual line and rebooted fine with great X performance. So I can't use a second screen at present unless you tell me what other trick I can do to fix this?

Also, there are posts earlier recommending to do these changes but use all ubuntu kernels etc from various ppa's. Is there a guide somewhere on how to do this? I'd really would rather stick to ubuntu.

---

### Post by psyke83 on 2009-04-26
> **markbl said:**
> Thanks psyke83. Following your guide here exactly *massively* improved my machine responsiveness, youtube, etc. I have "VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)".

One litte thing though - to run a second monitor off my laptop I have to manually set a  "Virtual 2720 1024" in my Display subsection of my xorg.conf. After implementing your changes my X died on first restart telling me that the "Virtual specification was incompatible with DRI" so I commented out the virtual line and rebooted fine with great X performance. So I can't use a second screen at present unless you tell me what other trick I can do to fix this?

See the second entry of "Known Issues" here: [http://intellinuxgraphics.org/2009Q1.html](http://intellinuxgraphics.org/2009Q1.html)

> Also, there are posts earlier recommending to do these changes but use all ubuntu kernels etc from various ppa's. Is there a guide somewhere on how to do this? I'd really would rather stick to ubuntu.

I'm not sure what you mean? If you mean to have a kernel installable from a PPA, it's not really necessary.

As far as I'm aware (somebody correct me if I'm wrong), the kernel packages I advise users to install were built by the Ubuntu kernel team - but of course they have an unsupported status.

---

### Post by psyke83 on 2009-04-26
> **progre55 said:**
> Worked well for me, thanks a lot! The ppracer fps is about ~80, while it used to be around 40.
However, after switching to the 2.6.30 kernel and installing the startupmanager, I don't see any splashscreen on startup and most importantly, when everything is up and running, I cannot switch using CTRL+ALT+F1 ... F6. It just shows a blank black screen.

Can anybody suggest anything here, please?

Well, usplash doesn't work for me using the 2.6.30-rcX kernels, but I've no problem switching to different VTs... maybe the framebuffer didn't initialize properly on your system. You can try the -rc3 kernel (see [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/")), or simply stay with the official Jaunty kernel.

Edit: hmm, perhaps if you experiment with the boot option "vga=791" or something similar. That may fix the framebuffer issue. I'll do some testing on my laptop when I next reboot.
Edit 2: see "Known Issues [...] VT switch broken on some machines" here: [http://intellinuxgraphics.org/2009Q1.html](http://intellinuxgraphics.org/2009Q1.html)

---

### Post by psyke83 on 2009-04-26
> **umaxtu said:**
> I tried following these instructions earlier and the end result was that it froze when ever i Logged on or it never let me logged on.

It's probably because UXA is buggy for your chipset. Try reverting to EXA (comment the "AccelMethod" line, or change it from "uxa" to "exa").

It could also be a bug in the kernel - try booting with the official Jaunty kernel.

---

### Post by Arup on 2009-04-27
Thankfully, the Intel G31/33 and above chipsets seems to have none of the issues which are being described above, things work quite well with the included xorg-intel in Jaunty. No compiz slowdowns but for Google Earth to work, effects have to be turned off. Otherwise no desktop response issues or 2d issues so far.

---

### Post by ComputerExpertVK on 2009-04-27
THANK YOU SOOO MUCH!!!
THIS FIXED MY COMPUTER!!!
Ubuntu was working for me for the past few years until I upgraded to this version...
After this post, Ubuntu is back to being great!

---

### Post by psyke83 on 2009-04-27
> **Arup said:**
> Thankfully, the Intel G31/33 and above chipsets seems to have none of the issues which are being described above, things work quite well with the included xorg-intel in Jaunty. No compiz slowdowns but for Google Earth to work, effects have to be turned off. Otherwise no desktop response issues or 2d issues so far.

Glad to hear your system is working fine. Did you consider following the guide to see if it may improve performance beyond what you're experiencing now?

---

### Post by Arup on 2009-04-27
> **psyke83 said:**
> Glad to hear your system is working fine. Did you consider following the guide to see if it may improve performance beyond what you're experiencing now?

I am definitely tempted but since I don't do much games if at all and Google Earth and other 3d apps that I need seem to be running OK I would prefer not to tinker for the sake of stability. However I also see that most of the issues faced here are with the 945 and 965 chip and few are with G31/35 or others. I may be wrong. Whats your suggestion? This is for my other PC with a G31, my main PC with ATI dual GPU 4850 runs great with drivers from ATI site.

---

### Post by psyke83 on 2009-04-27
> **Arup said:**
> I am definitely tempted but since I don't do much games if at all and Google Earth and other 3d apps that I need seem to be running OK I would prefer not to tinker for the sake of stability. However I also see that most of the issues faced here are with the 945 and 965 chip and few are with G31/35 or others. I may be wrong. Whats your suggestion? This is for my other PC with a G31, my main PC with ATI dual GPU 4850 runs great with drivers from ATI site.

I think that the problem is with all chipsets, but the issues are most visible for 9xx and 8xx chipsets (possibly due to the lower performance characteristics of older hardware).

I totally respect your decision not to test these packages - however, I can guarantee that you are suffering from the MTRR issue. I recommend you follow steps 4 and 5 to create a customized fixmtrr.sh script - this will improve performance and lower CPU usage for video playback on your system - without sacrificing any stability.

Please confirm the linked bug report if you decide to try this on your system, by the way. Thanks!

---

### Post by noobaholic on 2009-04-27
I've seen a couple other users in this thread mention system lockups using this setup.  Mine are sporadic - they typically occur after a couple hours of use. I'm chalking them up to the bleeding-edge kernel, but I thought I might ask if anyone has more specific info about what might be causing them.

---

### Post by psyke83 on 2009-04-27
> **noobaholic said:**
> I've seen a couple other users in this thread mention system lockups using this setup.  Mine are sporadic - they typically occur after a couple hours of use. I'm chalking them up to the bleeding-edge kernel, but I thought I might ask if anyone has more specific info about what might be causing them.

See: [http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues)

The first three issues may affect you (of which the third is unrelated to this guide, being an EXT4 bug).

I recommend you troubleshoot by reducing the variables. Switch back to EXA and see if the crashes stop, switch back to the stock kernel (please note that the official Jaunty kernel is probably more unstable with UXA), then revert to the official drivers. Unfortunately, it's possible that none of these changes will prevent freezes aside from disabling DRI entirely (according to the release notes).

I only notice crashes when using compiz, so you may also want to try disabling that.

---

### Post by JamesHowlett on 2009-04-27
> **psyke83 said:**
> I recommend you follow steps 4 and 5 to create a customized fixmtrr.sh script - this will improve performance and lower CPU usage for video playback on your system - without sacrificing any stability.

Speaking of which, I made the script but being new to ubuntu how do i get it to run each time i log in?

EDIT: NVM i got it.

---

### Post by noobaholic on 2009-04-27
> **psyke83 said:**
> See: [http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues)

The first three issues may affect you (of which the third is unrelated to this guide, being an EXT4 bug).

I recommend you troubleshoot by reducing the variables. Switch back to EXA and see if the crashes stop, switch back to the stock kernel (please note that the official Jaunty kernel is probably more unstable with UXA), then revert to the official drivers. Unfortunately, it's possible that none of these changes will prevent freezes aside from disabling DRI entirely (according to the release notes).

I only notice crashes when using compiz, so you may also want to try disabling that.

Thanks a lot for all the help. I'm on an ext3 filesystem, so it's not being caused by the fs.

As I get more time, I'll experiment with some of these variables. One new piece of information: DISABLING compiz actually reliably causes my machine to lock up immediately - but only when I have my external monitor hooked up. I tried disabling it, thinking, like you that it was potentially causing problems. Not sure what to make of the results being the other way around.

---

### Post by rabbit251 on 2009-04-27
I just finished completing the instructions and already see some real results in my graphics performance. Everything is just so much quicker, except for Alt+F8 window resizing, which is still choppy and slow. I'm using a Dell Inspiron 1520 with an Intel X3100 graphics card. Thanks for the great HOWTO, psyke83.

---

### Post by Tich666 on 2009-04-27
Unfortunately the MTRR fix doesn't work for me, here's the relevant outputs:
```
lspci -v
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

```

The line modified for my values in the fixmtrr.sh script:
```
echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```

The output of fixmtrr.sh script:
```
Before:
-------
reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg04: base=0x0bde00000 ( 3038MB), size=    2MB, count=1: uncachable

After:
------
reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg04: base=0x0bde00000 ( 3038MB), size=    2MB, count=1: uncachable

```
Strangely /proc/mtrr already contains 5 values from the beginning, thus another one can't be added I think.

Trying to manually add it gives the following error:
```
sudo -s
echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
bash: echo: write error: Invalid argument
```


There is also a new ppa with the latest stable versions of x-server related packages, recommended for people who want to check out new versions without living at the bleeding edge: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

---

### Post by markbl on 2009-04-27
> **caish5 said:**
> I keep getting
bash: echo: write error: Invalid argument
Any ideas?
I was getting this too because I put a #!/bin/bash at the top of my fixmtrr.sh script. Take it out and you don't get this error although it seems to still run under bash anyhow. Can somebody explain why this error occurs?

---

### Post by markbl on 2009-04-27
> **psyke83 said:**
> See the second entry of "Known Issues" here: [http://intellinuxgraphics.org/2009Q1.html](http://intellinuxgraphics.org/2009Q1.html)
So is there any chance a fix will come through for this Virtual size bug? It would be a damn shame if I can't use a second monitor for 6 months until karmic comes out :( Will I just pick it up as an update from the ppa repo?

Also, as I said earlier, these fixes make a massive improvement to my machine. However, when I run the fixmtrr.sh script immediately after reboot + X start I get:

Before:
-------
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining

After:
------
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining

i.e. I don't see any change in before/after. So is it true that I don't need to bother with this script?

Thanks very much psyke83 for your fantastic help here. This poor X performance really is a show-stopper.

---

### Post by Fale on 2009-04-27
> **VMC said:**
> I just want to report here that I found a fix for my video problem.

Video card:
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

Solution was to revert back to Intel driver 2.4. Go [HERE]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") for explanation.

My video now exactly the same as it was using Hardy. Speed is the same. No more choppy avi, vob's. Everything works.


I can confirm this. Works perfectly on my Laptop.

I upgraded Intrepid --> Jaunty which caused very **SLOW** performance on desktop use. After that guide everything runs smoothly.

I have:
*00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)*

---

### Post by ovidiub on 2009-04-27
Thank you for this How To. It solved my problem with compiz working slow.

---

### Post by rabbit251 on 2009-04-27
> Providing that your system boots normally, execute the "fixmtrr.sh" script (it's necessary to fix upon each restart of X), and do some testing!

```
$ sudo fixmtrr.sh
```

> Speaking of which, I made the script but being new to ubuntu how do i get it to run each time i log in?

EDIT: NVM i got it.

So, there is a way to automate the script execution on each restart of X?

---

### Post by Arup on 2009-04-27
> **psyke83 said:**
> I think that the problem is with all chipsets, but the issues are most visible for 9xx and 8xx chipsets (possibly due to the lower performance characteristics of older hardware).

I totally respect your decision not to test these packages - however, I can guarantee that you are suffering from the MTRR issue. I recommend you follow steps 4 and 5 to create a customized fixmtrr.sh script - this will improve performance and lower CPU usage for video playback on your system - without sacrificing any stability.

Please confirm the linked bug report if you decide to try this on your system, by the way. Thanks!


I just enabled uxa on xorg and ran it for a whole day, glxgears indicated less fps, from average of 2200fps it dropped to 880fps but interestingly, Google Earth picked up speed, earlier I had to set effects to none to run GE but now it runs well with no flickering and compiz enabled.

---

### Post by mk4umha on 2009-04-27
> **Fale said:**
> I can confirm this. Works perfectly on my Laptop.

I upgraded Intrepid --> Jaunty which caused very **SLOW** performance on desktop use. After that guide everything runs smoothly.

I have:
*00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)*

I also reverted to the older Intel Driver with Jaunty but had flickering problems going full screen in videos or virtual box. I had the vsync disabled along with the undirect fullscreen unchecked. Unfortunately I went back to 8.10 which is a whole lot smoother on my Dell D630 with the intel chipset.

---

### Post by tomchiverton on 2009-04-27
Cheers for this, on my hardware (a Dell 1525n laptop):
$ lspci -v|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I was already using UXA to fix corruption in KDE, but adding the MTRR fix helped a bit (up from 19 to 25 frames in ppracer), with the updated Kernel, Xorg and driver packages I get 40 :-)

---

### Post by Area51mafia on 2009-04-27
After following this guide my performance with my GM965 was greatly increased, and Compiz worked great. The only problem is that after a couple hours my system still freezes to the point where it's unusable until it rights itself about 10 minutes later.

From lscpi:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 000e
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at ffc00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
```

So I have
```
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
``` in the fixmtrr file. When it runs the before and after are exactly the same every time.

Everything else is the same as in this guide, followed step by step. The only thing extra I had to do was remove the blacklist on the GM965 in Compiz so that it could start, but they were only blacklisted because of the but this guide was meant to fix.

Any help?

---

### Post by tomchiverton on 2009-04-27
> 
So I have
```
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
``` in the fixmtrr file. When it runs the before and after are exactly the same every time.

Silly question, you did the echo as root, right ? Either by putting in /etc/rc.local or running sudo -i first ?

---

### Post by Inquisitorthemad on 2009-04-27
I found that the new kernel in the instructions broke ndiswrapper on my machine, denying me internet access until I reversed the change. Is there any way to get the graphical improvements mentioned in the first post without having to mess with the kernel?

---

### Post by umaxtu on 2009-04-27
I think the've mentioned somewhere in this thread that you can do this without messing with the kernel but it is recommended.

---

### Post by ripps818 on 2009-04-27
Add this ppa to your sources.list to install the newest ubuntu-dev supported drivers:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Your even allowed to file bug reports against these.

---

### Post by dentaku65 on 2009-04-27
> **ripps818 said:**
> Add this ppa to your sources.list to install the newest ubuntu-dev supported drivers:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Your even allowed to file bug reports against these.

Are these drivers usable with 2.6.28-11-generic kernel?

---

### Post by bucketoftruth on 2009-04-27
What about adding "/usr/local/bin/fixmtrr.sh" in /etc/init.d/x11-common as
> 
case "$1" in
  start)
    set_up_socket_dir
    set_up_ice_dir
    **/usr/local/bin/fixmtrr.sh**
  ;;

instead of running it by hand every time X starts?

---

### Post by Area51mafia on 2009-04-27
> **tomchiverton said:**
> Silly question, you did the echo as root, right ? Either by putting in /etc/rc.local or running sudo -i first ?

Yup. The fixmtrr script is run as root every time I start X.

Edit: It happens whether or not Compiz is on.

---

### Post by AK Dave on 2009-04-27
I note that the how-to has changed since Friday.

I did this fix on Friday on a Dell Mini-9 with intel 945 chipset.

pre:
PPR 12-16fps
post:
PPR 26-30fps

Only downside of this for me, was that the 2.6.30-rc2 kernel defaulted to using some bt43 wifi kernel module for my wifi chipset, when the wl module is the one that works the best. Jaunty defaults properly to the wl module. I was unable to modprobe the wl module in place with 2.6.30-rc2 so ultimately I backed out of almost all of the changes.

I kept the xorg.conf and mtrr changes in place, and still enjoy 16-20fps in PPR. Not what I saw with 2.6.30-rc2, but until I can work out a fix for the wl module, I have to stick with 2.6.28. :(

---

### Post by psyke83 on 2009-04-27
> **ripps818 said:**
> Add this ppa to your sources.list to install the newest ubuntu-dev supported drivers:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Your even allowed to file bug reports against these.

Note that if anyone wishes to try these "stable" drivers but has already followed this guide, you must first downgrade all the packages from the xorg-edgers repository & remove it from your sources.list. You can do that by following the instructions in this guide to revert changes.

---

### Post by psyke83 on 2009-04-27
> **AK Dave said:**
> 
I kept the xorg.conf and mtrr changes in place, and still enjoy 16-20fps in PPR. Not what I saw with 2.6.30-rc2, but until I can work out a fix for the wl module, I have to stick with 2.6.28. :(

Unfortunately the wl module is restricted, and the testing kernels do not come with a "linux-restricted-modules-`uname -a`" package like the official packages. You'll have to use the official kernel.

---

### Post by psyke83 on 2009-04-27
> **Tich666 said:**
> Unfortunately the MTRR fix doesn't work for me, here's the relevant outputs:
```
lspci -v
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Fujitsu Siemens Computers Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

```

The line modified for my values in the fixmtrr.sh script:
```
echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```

The output of fixmtrr.sh script:
```
Before:
-------
reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg04: base=0x0bde00000 ( 3038MB), size=    2MB, count=1: uncachable

After:
------
reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg04: base=0x0bde00000 ( 3038MB), size=    2MB, count=1: uncachable

```
Strangely /proc/mtrr already contains 5 values from the beginning, thus another one can't be added I think.

Your MTRR ranges are messed up for some reason, which is preventing the appropriate region to get marked write-combining.

Try this script for your system:
```
echo "Before:"
echo "-------"
cat /proc/mtrr
echo "disable=0" >/proc/mtrr
echo "disable=1" >/proc/mtrr
echo "disable=2" >/proc/mtrr
echo "disable=3" >/proc/mtrr
echo "disable=4" >/proc/mtrr
echo "base=0x00000000 size=0x100000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr

echo ""
echo "After:"
echo "------"
cat /proc/mtrr
```

Basically, it resets your MTRR range, then sets up a minimal table. Be warned, marking those uncachable areas as cachable may cause your system to freeze.

P.S. Is it correct that you have 5GB RAM on your system? If not, please let me know.

---

### Post by wirechief on 2009-04-27
i do not understand the error message from /var/log/Xorg.0.log
grep -i UXA /var/log/Xorg.0.log
(WW) intel(0): DRI2 requires UXA

What am i missing in my xorg.conf  ???
is the rest of my work with the files for improving performance ok ?

My /etc/X11/xorg.conf  ...
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Onboard Intel Video"
	#Option "AccelMethod" "exa"
	#Option "monitor-VGA" "ExternalVGA"
	#Option "monitor-LVDS" "OnboardLVDS"
	 Option "EXAOptimizeMigration" "true"
	 Option "MigrationHeuristic" "greedy"
	 Option "AccelMethod" "uxa"
         Option	"Tiling"  "false" # may break 3D rendering if enabled

EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection




Linux wirechief-laptop 2.6.30-020630rc2-generic #020630rc2 SMP Wed Apr 15 13:20:18 UTC 2009 x86_64 GNU/Linux

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

/usr/local/bin/fixmtrr.sh

echo "Before:"
echo "-------"
cat /proc/mtrr
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
echo ""
echo "After:"
echo "------"
cat /proc/mtrr


sudo fixmtrr.sh
Before:
-------
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f700000 ( 2039MB), size=    1MB, count=1: uncachable
reg02: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  256MB, count=2: write-combining

After:
------
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f700000 ( 2039MB), size=    1MB, count=1: uncachable
reg02: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  256MB, count=3: write-combining

---

### Post by psyke83 on 2009-04-28
> **wirechief said:**
> i do not understand the error message from /var/log/Xorg.0.log
grep -i UXA /var/log/Xorg.0.log
(WW) intel(0): DRI2 requires UXA

That's not enough information to help. What other warnings or errors are displayed?

```
$ grep EE /var/log/Xorg.0.log
$ grep WW /var/log/Xorg.0.log
```

Maybe attach your entire Xorg.0.log if you can't identify the problem.

> My /etc/X11/xorg.conf  ...
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Onboard Intel Video"
	#Option "AccelMethod" "exa"
	#Option "monitor-VGA" "ExternalVGA"
	#Option "monitor-LVDS" "OnboardLVDS"
	 Option "EXAOptimizeMigration" "true"
	 Option "MigrationHeuristic" "greedy"
	 Option "AccelMethod" "uxa"
         Option	"Tiling"  "false" # may break 3D rendering if enabled

EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection


You should probably remove one of the Device sections to avoid conflicts.

> 
Before:
-------
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f700000 ( 2039MB), size=    1MB, count=1: uncachable
reg02: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  256MB, count=2: write-combining

After:
------
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f700000 ( 2039MB), size=    1MB, count=1: uncachable
reg02: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  256MB, count=3: write-combining

That's fine. The 2.6.30-rc2 kernel sets up write-combining correctly upon the first start of X. After restarting X you will lose the write-combining range (reg03), however, so the script is handy in this situation.

---

### Post by Area51mafia on 2009-04-28
> **Area51mafia said:**
> After following this guide my performance with my GM965 was greatly increased, and Compiz worked great. The only problem is that after a couple hours my system still freezes to the point where it's unusable until it rights itself about 10 minutes later.

From lscpi:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 000e
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at ffc00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
```

So I have
```
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
``` in the fixmtrr file. When it runs the before and after are exactly the same every time.

Everything else is the same as in this guide, followed step by step. The only thing extra I had to do was remove the blacklist on the GM965 in Compiz so that it could start, but they were only blacklisted because of the but this guide was meant to fix.

Any help?

I figured out that NOT running the fixmtrr script was the fix. The before and after outputs weren't QUITE the same, but the line was already in /proc/mtrr before, and the script was adding the line AGAIN (making count=2, instead of count=1). I've since rebooted and haven't run the script and it's been 5 hours with no freezing.

---

### Post by psyke83 on 2009-04-28
> **Area51mafia said:**
> I figured out that NOT running the fixmtrr script was the fix. The before and after outputs weren't QUITE the same, but the line was already in /proc/mtrr before, and the script was adding the line AGAIN (making count=2, instead of count=1). I've since rebooted and haven't run the script and it's been 5 hours with no freezing.

Glad to hear you identified the problem. Can you do me a favour when you have some time, and post the fixmtrr.sh output so I can see the before and after differences? Thanks.

---

### Post by VyacheslavS on 2009-04-28
It works with latest kernel 2.6.30-**rc3**?

---

### Post by Ralphthedog on 2009-04-28
> **VyacheslavS said:**
> It works with latest kernel 2.6.30-**rc3**?

I believe rc3 has a regression, so don't use that.



My EeePC 900 (i915) is a lot happier with this fix, tiling set to "true" doesn't break anything either. I wouldn't say it's perfect, especially the NBR desktop, but it's "OK" now

The fixmtrr.sh seems to be unnecessary too - same before and after??

EDIT: After a bit of testing tiling "true" is a bad idea....

---

### Post by Arup on 2009-04-28
Actually on my G31 motherboard, all I added was the uxa enable option and it ran well without any issues, I then added the stable xorg via the ppa and now the FPS has picked up in Super Penguin, also Google Earth runs even better, still have no stability issues. I don't use desktop effects but all the Compiz wiz bangs work fine, I have compiz turned off and metacity turned on.

---

### Post by koycan on 2009-04-28
My /proc/mtrr was already fixed after installing the packages in this guide (965GMA chipset, X3100 gfx), so no need to run mtrr-fix script.  
I also enabled UXA and did not disable Tiling. So far things are back to normal, actually better performance than it was with 8.10. 
Compiz does not work because of blacklisting (I don't use it anyway).
But I'm having significant overheating, CPU temp. is around 60-65C when idle (it was about 45-50C before). Any advice to fix this?

EDIT: 
/proc/mtrr remains fixed only during the first X session. Following sessions (e.g. logout-login) show it broken, hence the script has to be run.

---

### Post by Arup on 2009-04-28
> **koycan said:**
> My /proc/mtrr was already fixed after installing the packages in this guide (965GMA chipset, X3100 gfx), so no need to run mtrr-fix script.  
I also enabled UXA and did not disable Tiling. So far things are back to normal, actually better performance than it was with 8.10. 
Compiz does not work because of blacklisting (I don't use it anyway).
But I'm having significant overheating, CPU temp. is around 60-65C when idle (it was about 45-50C before). Any advice to fix this?

Check if your CPU is being overloaded, find the rogue app.

---

### Post by koycan on 2009-04-28
> **Arup said:**
> Check if your CPU is being overloaded, find the rogue app.
Well, therein lies the rub: I don't observe any abnormal CPU utilization. It's around 3% right now, but CPU is 65C.

---

### Post by Tich666 on 2009-04-28
> **psyke83 said:**
> Your MTRR ranges are messed up for some reason, which is preventing the appropriate region to get marked write-combining.

Try this script for your system:
```
echo "Before:"
echo "-------"
cat /proc/mtrr
echo "disable=0" >/proc/mtrr
echo "disable=1" >/proc/mtrr
echo "disable=2" >/proc/mtrr
echo "disable=3" >/proc/mtrr
echo "disable=4" >/proc/mtrr
echo "base=0x00000000 size=0x100000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr

echo ""
echo "After:"
echo "------"
cat /proc/mtrr
```

Basically, it resets your MTRR range, then sets up a minimal table. Be warned, marking those uncachable areas as cachable may cause your system to freeze.

P.S. Is it correct that you have 5GB RAM on your system? If not, please let me know.

They sure look messed up to me too.
I have 4GB of RAM (2x2GB), only 3GB of which get recognized by linux (32bit or 64bit kernel, it doesn't matter. I think it is due to the last GB being dedicated to the GFX card in the bios, unfortunately I haven't found a way to change that.)

I modified the script to look like:
```
#!/bin/sh
echo "Before:"
echo "-------"
cat /proc/mtrr
echo "disable=0" >/proc/mtrr
echo "disable=1" >/proc/mtrr
echo "disable=2" >/proc/mtrr
echo "disable=3" >/proc/mtrr
echo "disable=4" >/proc/mtrr
echo "base=0x00000000 size=0xC0000000 type=write-back" >| /proc/mtrr
echo "base=0xD0000000 size=0x10000000 type=write-combining" >| /proc/mtrr

echo ""
echo "After:"
echo "------"
cat /proc/mtrr
```

which resulted in the system becoming very slow, almost unresponsive and me rebooting the machine.
After excecuting the script, only the write-combining line was in the mtrr, so I guess the "write-back" line had wrong values.

Thanks for your continued help and support psyke! :)

---

### Post by kennymchansen on 2009-04-28
Hi thank you for the guide. Graphics and video playback are running a lot smoother now.
After upgrading the Kernel i just have this small problem, that i cannot adjust the brightness of my laptopscreen. 
i have the Intel 965 express chipset on a Lenovo 3000 v200 laptop
- Any ideas on how to restore this functionality?

---

### Post by wirechief on 2009-04-28
Here are the greps..
$ grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
wirechief@wirechief-laptop:~$  grep WW /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000206 to 0x80000206
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): DRI2 requires UXA

ok i removed the duplicate device section in xorg.conf.

there are talk of a virtual setting affecting this freeze bug
i dont know if that is the same as what is shown in the ubuntu geek 
website, it got too confusing for me to calculate what setting would
be needed the numbers didnt work out for me, so i left it with no setting..

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

my entire /var/log/Xorg.0.log is here [http://pastebin.com/f10da7929](http://pastebin.com/f10da7929)
thank you for reviewing my data and making suggestions...

---

### Post by Arup on 2009-04-28
> **koycan said:**
> Well, therein lies the rub: I don't observe any abnormal CPU utilization. It's around 3% right now, but CPU is 65C.

Sometimes lm-sensors don't callibrate properly, check your temp in the BIOS and see if that corresponds to what you see in Ubuntu.

---

### Post by Area51mafia on 2009-04-28
> **psyke83 said:**
> Glad to hear you identified the problem. Can you do me a favour when you have some time, and post the fixmtrr.sh output so I can see the before and after differences? Thanks.

Well I won't run it, since I'm not in a position to reboot soon. But this is my unaltered /proc/mtrr
```

reg00: base=0x0feda0000 ( 4077MB), size=  128KB, count=1: write-back
reg01: base=0x07d800000 ( 2008MB), size=    8MB, count=1: uncachable
reg02: base=0x07e000000 ( 2016MB), size=   32MB, count=1: uncachable
reg03: base=0x0ffe00000 ( 4094MB), size=    2MB, count=1: write-protect
reg04: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg05: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining

```

The only difference after running fixmtrr is count=2 on write-combining.

---

### Post by cracksquirrel on 2009-04-28
Not sure if this was posted already, but I found a WIKI that worked like a charm and was much easier than this guide. I appreciate the info and time given in this thread, but all that seems like overkill when this WIKI solution is as easy as an apt-get install of a later intel driver. 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Shrikaant on 2009-04-28
Can u please post the equivalent instructions for the 64bit version Ubuntu Jaunty. :)

---

### Post by VMC on 2009-04-28
> **ripps818 said:**
> Add this ppa to your sources.list to install the newest ubuntu-dev supported drivers:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Your even allowed to file bug reports against these.

I used the "[Reverting the Jaunty Xorg intel driver to 2.4x]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")". Now I'm wondering if this one is more permanent fix. It looks like they updated the Intel Xorg driver. Has anyone tried this newest method?

---

### Post by chronniff on 2009-04-28
that looks like its about rolling back to the old intrepid drivers, the end result of this is is testing out the bleeding edge intel drivers being developed....down the road this guide will be much more beneficial as they continue to improve the drivers, but I can see why you might use your way, I actually used this guide, but instead of using the 2.6.30-rc2 I am using the 2.6.29.1, which I have found to have equally if not better performance enhancements, as well as being a stable kernel....for instance I found a patch so that I can build vmware modules on 2.6.29.1 however since 2.6.30 is still in testing I would have to figure one out for myself.....Also just to throw in my own experience thus far, I custom compiled the 2.6.29.1 kernel to be preemptive....not sure if it really boosts the graphics in reality, but it sure makes it feel a lot faster and responsive

---

### Post by chronniff on 2009-04-28
I also have the same question as Area51mafia, the only difference after running the script is the count, does that essentially mean it isn't doing anything and that it was ok to begin with?

---

### Post by stewacide on 2009-04-28
> **cracksquirrel said:**
> Not sure if this was posted already, but I found a WIKI that worked like a charm and was much easier than this guide. I appreciate the info and time given in this thread, but all that seems like overkill when this WIKI solution is as easy as an apt-get install of a later intel driver. 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I tried that first, and it was a big improvement over the default Jaunty situation, but the solution in this thread improves performance even more, particularly for video playback (at least that's my perception). I'd say if it doesn't break any of your other drivers it's best to go with the cutting-edge intel drivers than to revert to the old ones.

Also there was a lot of corruption/artifacting in Compiz with the Intrepid drivers for me that's gone completely with UXA.

---

### Post by psyke83 on 2009-04-28
> **wirechief said:**
> my entire /var/log/Xorg.0.log is here [http://pastebin.com/f10da7929](http://pastebin.com/f10da7929)
thank you for reviewing my data and making suggestions...

From reviewing your Xorg.0.log, the cause is quite simply due to the fact that you were using an xorg.conf with two "Device" sections, and the second one was being ignored.

Reset your xorg.conf:
```
$ sudo dpkg-reconfigure xserver-xorg
```

Then, edit this fresh xorg.conf according to the guide, without making any further customizations.

---

### Post by psyke83 on 2009-04-28
> **koycan said:**
> My /proc/mtrr was already fixed after installing the packages in this guide (965GMA chipset, X3100 gfx), so no need to run mtrr-fix script.  
I also enabled UXA and did not disable Tiling. So far things are back to normal, actually better performance than it was with 8.10. 
Compiz does not work because of blacklisting (I don't use it anyway).
But I'm having significant overheating, CPU temp. is around 60-65C when idle (it was about 45-50C before). Any advice to fix this?

Maybe you are seeing higher temperatures because of a bug in the driver causing the graphics hardware to poll constantly. Have you tried disabling compiz to see if it helps? Also try disabling UXA to see if it reduces temperature.

My laptop runs idle at 34 degrees, and reaches no more than 60 degrees under full load. I opened it up and cleaned out a lot of dust a few days ago, which reduced the temperature significantly - but the driver changes didn't affect temperature for me.

---

### Post by psyke83 on 2009-04-28
> **chronniff said:**
> I also have the same question as Area51mafia, the only difference after running the script is the count, does that essentially mean it isn't doing anything and that it was ok to begin with?

Well, if you're using the 2.6.30-rc2 kernel, you'll notice that the write-combining range is active when you first boot your computer (without any need for the script). When you restart X, however, the write-combining range disappears - in this case, you should use the script.

Therefore, use the script only if you have restarted X.

---

### Post by dentaku65 on 2009-04-28
> **VMC said:**
> I used the "[Reverting the Jaunty Xorg intel driver to 2.4x]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")". Now I'm wondering if this one is more permanent fix. It looks like they updated the Intel Xorg driver. Has anyone tried this newest method?

Yes. It works nice with official Jaunty kernel 2.6.28-11
[Here]("http://ubuntuforums.org/showthread.php?t=1136738")

---

### Post by wyth on 2009-04-28
I used this guide for my Intel chip (GM965), and it's worked just fine.  Some things I've noticed, though; the boot splash is gone -- I just get the standard verbose text up to the login screen.  In that text, I'm also seeing
```
Loading AppArmor module... [fail]
```Is this just because the rc2 kernel doesn't have the restricted modules that the generic kernel has?  Is it even really a problem?

---

### Post by imhoff on 2009-04-28
lspci |grep VGA:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

also just did - as I now know - not successfully the following:

1. added ppa x to /etc/apt/apt.sources:
#...
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

...
as root: 
apt-get update ; apt-get dist-upgrade

2. activated uxa in /etc/X11/xorg.conf: Don't use my BUS ID if not matched> 
#...
Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
**	Option 		"AccelMethod" "UXA"**
	BusID		"PCI:0:2:0"
EndSection

3. reboot

ppracer now works fine and faster with uxa enabled than with 8.10, even with 1680x1050.
With exa I just had estimated unusable 3fps...

I need to say that after enabling compiz my x-server crashed :(
so uxa still not stable using compiz with latest jaunty kernel 
and still some artifacts watching videos. 
I did not try and don't want to use rc-kernels...

finally performace is acceptable after using rc2-kernel with exa and
until now stable instead of using uxa.
I used the settings from psyke83 except using exa instead of uxa.
Maybe this helps someone having the same hardware as there seem to be different behaviour for different intel-cards.
ppracer now works smoothly again.

kind regards Peter

---

### Post by Yoshidude on 2009-04-28
Is this intended to also fix a problem where Ubuntu is unable to boot into X at all? My computer always takes a long time to boot, then says it's going to go into low-graphics mode for the session. That always crashes, so I just drop into the command-line and run startx. That seems to work pretty decently, and video quality seems fine (haven't tried any games yet).

I tried this fix, but it didn't really change much regarding the boot. Low-graphics mode stopped complaining about tiling (I assume that was only because of the line in the xorg that turns off tiling), and now it just says that it can't find the configuration info.

Any help would be very much appreciated.

---

### Post by psyke83 on 2009-04-28
> **imhoff said:**
> lspci |grep VGA:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

also just did successfully the following :):

1. added ppa x to /etc/apt/apt.sources:
#...
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

...
as root: 
apt-get update ; apt-get dist-upgrade

2. activated uxa in /etc/X11/xorg.conf: Don't use my BUS ID if not matched

3. reboot

ppracer now works fine and faster with uxa enabled than with 8.10, even with 1680x1050.
With exa I just had estimated unusable 3fps...

Updating to the stable drivers and enabling UXA does help performance to a certain degree. However, it still won't fix the MTRR bug, and the official Jaunty kernel has a performance regression in the DRM kernel module compared to 2.6.30-rc2.

Different strokes for different folks.

---

### Post by psyke83 on 2009-04-28
> **Yoshidude said:**
> Is this intended to also fix a problem where Ubuntu is unable to boot into X at all? 

Nope, sorry.

---

### Post by psyke83 on 2009-04-28
> **wyth said:**
> I used this guide for my Intel chip (GM965), and it's worked just fine.  Some things I've noticed, though; the boot splash is gone -- I just get the standard verbose text up to the login screen.  In that text, I'm also seeing
```
Loading AppArmor module... [fail]
```Is this just because the rc2 kernel doesn't have the restricted modules that the generic kernel has?  Is it even really a problem?

Your experience reflects my own (no usplash and an error loading the AppArmor module). Unfortunately, the testing kernel doesn't include restricted modules. If you rely on any restricted drivers, revert to the official kernel (with the understanding that performance will drop).

---

### Post by zevans on 2009-04-28
> **Ralphthedog said:**
> 
My EeePC 900 (i915) is a lot happier with this fix [...] 

EDIT: After a bit of testing tiling "true" is a bad idea....

RC2 gets the MTRR stuff right at boot time, so you don't need the scripts - unless you restart X without rebooting, in which case the script allows you to fix it without needing a complete reboot. 

Your tiling problems:
[https://bugs.launchpad.net/linux/+bug/349314](https://bugs.launchpad.net/linux/+bug/349314)
...will be fixed in an update release and it's already confirmed fixed in the test 2.6.28 kernel mentioned there, so don't post any "me-too" posts to that bug.

It's also logged as a kernel bug upstream so eventually the Ubuntu-specific fixes they've come up with won't be needed.

---

### Post by Craig73 on 2009-04-28
> **psyke83 said:**
> Well, if you're using the 2.6.30-rc2 kernel, you'll notice that the write-combining range is active when you first boot your computer (without any need for the script). When you restart X, however, the write-combining range disappears - in this case, you should use the script.

Therefore, use the script only if you have restarted X.

This does seem to reflect what I'm experiencing except the MTRR fix doesn't really seem to change anything for me;  I need to reboot to get that extra MTRR line back.  Note that having or not these values seem to change the status of my problems (which perhaps are slightly different?)

Running an Inspiron 700m so I have an 855GME and have applied your guide and upgraded to the latest kernel/driver/etc.  I do see the performance increase in ppracer.  [Note I had not tried just turning on UXA under the default setup, but that is 2d and doesn't related to 3d]

My issue seems to be related to closing a graphics app.  If I close ppracer (3d) it hangs.  If I close world of goo (2d I think?) it hangs.  If I play a flash video and close that tab it hangs.  Note first I thought it was X hanging in the case of the games, but if I launch the game from a terminal, then I can kill/close the terminal to close the app (note I can't terminate the app directly)

Video does seem to play slowly in Totem... but fine in VLC and Flash (although Flash seems to intermitedly stick and needs a boot, by moving the slider on the movie timeline, to unstick it).

Anyway... at least for the hanging games, at least I have a way to play them without having to reboot ;-)  and more importantly a way to reproduce this problem without needing to reboot as I look for a solution.

If you have any suggestions for running a debugger to identify what is actually getting stuck (driver/x/whatever) I'll see what I can do

[OK I've had a couple hangs launching ppracer... weird how it worked well for a while and now just doesn't with no change that I know if]

---

### Post by koycan on 2009-04-28
> **psyke83 said:**
> Maybe you are seeing higher temperatures because of a bug in the driver causing the graphics hardware to poll constantly. Have you tried disabling compiz to see if it helps? Also try disabling UXA to see if it reduces temperature.
I don't have compiz, it does not work because of blacklisting (and I don't fancy it either).
I disabled UXA, no joy.
This looks like a kernel problem, because the temp readings returned back to normal after booting the stock Jaunty kernel 2.6.28-11. However, my display intermittently flickers when I boot kernel 2.6.28-11 and brightness keys don't work (these happen regardless of the version of intel driver). With 2.6.30-rc2, display no longer flickers and brightness keys work perfect, but the system overheats :(
Overall, I seem to suffer some acpi instability.

EDIT:
Per your advice I opened up the laptop, came across a dust ball blocking half of the heat sink, cleaned it. Now, I've been using the laptop for an hour and the temp has not exceeded 55C so far! It seems kernel 2.6.30-rc2 was actually doing the right thing. Thanks psyke83, you're the man =D>

---

### Post by mikhmv on 2009-04-28
Hi, 

Good topic. 
Just want to add rc3 is available now. 
changing in your methods rc2 on rc3 work perfectly.

Thanks

---

### Post by Sesivany on 2009-04-28
Hi,
I upgraded to new drivers and kernel, too. But brightness control on Thinkpads doesn't work at all. It works with new drivers and standard kernel (.28). The bug has been filed and patch sent. It's supposed to be fixed in 2.6.30RC3 but it doesn't still work with RC3 from kernel.ubuntu.com. 
Do you still have the same problem? I hope it will be fixed until the final version is released. Because that's the only problem I have. Everything else works fine and performance is much better than with 2.6.28.

---

### Post by psyke83 on 2009-04-28
> **Sesivany said:**
> Hi,
I upgraded to new drivers and kernel, too. But brightness control on Thinkpads doesn't work at all. It works with new drivers and standard kernel (.28). The bug has been filed and patch sent. It's supposed to be fixed in 2.6.30RC3 but it doesn't still work with RC3 from kernel.ubuntu.com. 
Do you still have the same problem? I hope it will be fixed until the final version is released. Because that's the only problem I have. Everything else works fine and performance is much better than with 2.6.28.

Unless someone can correct me, you shouldn't file bugs on Launchpad for the 2.6.30-rcX kernels, or the xorg-edgers packages either. These are unsupported.

---

### Post by Jenda on 2009-04-28
Thanks for the guide - it seems to have helped somewhat. The sound was broken with the new kernel, though, but switching everything to OSS seems to have fixed that.

---

### Post by Sesivany on 2009-04-28
> **psyke83 said:**
> Unless someone can correct me, you shouldn't file bugs on Launchpad for the 2.6.30-rcX kernels, or the xorg-edgers packages either. These are unsupported.

I'm not talking about Launchpad. I'm talking about the kernel bugzilla. And I didn't file that bug, somebody else did.

---

### Post by umaxtu on 2009-04-28
will the new drivers alone fix the problem of intel graphics and desktop effects?

---

### Post by psyke83 on 2009-04-29
> **umaxtu said:**
> will the new drivers alone fix the problem of intel graphics and desktop effects?

Depends on what "problem" you mean - the initial posting explains the aims fully.

If you notice that desktop effects refuses to be enabled, but 3D applications work fine otherwise, it means that your graphics adapter has been deliberately blacklisted due to crashes in compiz - this guide is not relevant to you.

Search the forum for compiz + blacklist + jaunty, and you'll find one of the many posts explaining this.

---

### Post by VMC on 2009-04-29
> **imhoff said:**
> lspci |grep VGA:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

also just did - as I now know - not successfully the following:

1. added ppa x to /etc/apt/apt.sources:
#...
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

...
as root: 
apt-get update ; apt-get dist-upgrade

2. activated uxa in /etc/X11/xorg.conf: Don't use my BUS ID if not matched

3. reboot

...



This method does NOT work for my integrated Intel chip

```
$ lspci -nn|grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
```

---

### Post by Tenoq on 2009-04-29
This fix works like a charm on the eeePC 1000H.  I was just about to give up on Ubuntu on my netbook because the Flash performance was **terrible!**  This upgrade fixed it right up - Flash playback is very smooth now (probably as good as Windows).  

Unfortunately this disabled my Broadcom wi-fi (BCM4328).  Can anyone please tell me how to add the Broadcom driver into this kernel?  Or point me in the direction of another fix?  A netbook without wi-fi is like a car with no wheels. ;)

---

### Post by Praxicoide on 2009-04-29
After the first reboot the desktop did not cover the whole screen, and using xrandr only broke it, but after another reboot it worked OK on my inspiron. 

My card:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by wightman.p on 2009-04-29
This worked **100%** on my **Acer TravelMate 5720** - I do not appear to have the mttr bug (before and after outputs are the same).  Very chuffed!  TORCS performs nicely, the penguin slides as expected & AWN loads - awesome!  Already gone through some updates to the drivers, not a single issue!!!!

---

### Post by balduin on 2009-04-29
Same here: Works nicely on an Amilo Si 3655.
Thanks for the guide!

---

### Post by Tich666 on 2009-04-29
balduin, do the fn-brightness keys work for you, or the display switching (dvi-out, LVDS)?

I have scripts for the latter and gnome brightness panel applet for the former, but the brightness control is broken in 2.6.30-rc2 and -rc3 for me.

My mtrr problem still persists as well, as I explained in [this post](http://ubuntuforums.org/showthread.php?p=7166634#post7166634)
Could you post the output of fixmtrr.sh for me, as well as the other relevant outputs please?

---

### Post by shadyzay on 2009-04-29
works great on Sony Vaio VGN-FW170j
thanks :)

---

### Post by shadyzay on 2009-04-29
The only issue with this was that the new kernel broke vmware-player. VMWare modules failed to compile :(

---

### Post by umaxtu on 2009-04-29
> **psyke83 said:**
> Depends on what "problem" you mean - the initial posting explains the aims fully.

If you notice that desktop effects refuses to be enabled, but 3D applications work fine otherwise, it means that your graphics adapter has been deliberately blacklisted due to crashes in compiz - this guide is not relevant to you.

Search the forum for compiz + blacklist + jaunty, and you'll find one of the many posts explaining this.

I will thanks

---

### Post by glaze on 2009-04-30
Anyone tried Linux 2.6.30-rc4 yet? I'm compiling it now.

---

### Post by adster101 on 2009-04-30
Ooops. I tried this and now I can't even boot into the desktop.

When I updated the Kernel I was prompted to either keep a modified file (I think a menu.lst or a grub file) or to use the packaged version.

I opted to keep the file and now I don't have any options to even boot into 9.04 from grub boot loader. It just shows the 8.10 kernels and nothing else. Then all I get is  black screen.

Anyone know how to fix that or should I just try and revert it all?

P.S. the machine is a Dell Optiplex sx260.

Thanks,

Adam

---

### Post by adster101 on 2009-04-30
OK - reverting Xorg.conf fixed it up.

:-)

---

### Post by Phil Urich on 2009-04-30
Strangely enough, I don't seem to be able to boot from either 2.6.30rc2 or 2.6.30rc3:

```
Error 13: Invalid or unsupported executable format
```

Worth noting is that my /boot partition is ext4, I'm not really sure why 2.6.30 would have a problem with that when 2.6.28 doesn't, but who knows.

---

### Post by VMC on 2009-04-30
> **adster101 said:**
> Ooops. I tried this and now I can't even boot into the desktop.

When I updated the Kernel I was prompted to either keep a modified file (I think a menu.lst or a grub file) or to use the packaged version.

I opted to keep the file and now I don't have any options to even boot into 9.04 from grub boot loader. It just shows the 8.10 kernels and nothing else. Then all I get is  black screen.

Anyone know how to fix that or should I just try and revert it all?

P.S. the machine is a Dell Optiplex sx260.
 A couple of things. When you installed the RCx kernel and were asked to keep the current grub loader or replace it with the new one. What did you do? You must have keep the current. So that means you need to edit menu.lst and add the new kernel to it.

I interested that you have a Dell Optiplex SX260. I have a GX270. What Intel chip set do you have:
```
$ lspci -nn|grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

``` If it is a 82865G, then stop here and use the [[COLOR="Red"]**RollBack**[/COLOR]]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") method. none of the others I found work.

---

### Post by densou on 2009-04-30
> **psyke83 said:**
> Your issue is probably also related to MTRR ranges not being set correctly - this has nothing to do with your system's media players. See the bug report linked to this guide, and you'll find that your system is affected too...

you were right .... I had to create your script however it helped a little not so much I wished for .... why?

I'm still stuck with 2.6.28-11 (default kernel) and it won't be helpful at all; I tried Mandriva One 2009.1 Spring yesterday, using Gnome LiveCD - kernel 2.6.29.1+mesa7.3 o_O - well, MTRR was already caught out-of-the-box and N O choppy flash playback under FF (shipped with 3.0.8) ! Compiz ran smooth but not as fast as on Fedora 11 Preview (mesa 7.5-devel)

> Thanks for the information!

you're welcome lad/mate :KS

> **koycan said:**
> Overall, I seem to suffer some acpi instability.

rc4 contains mostly ACPI, ALSA and DRM/i9x5 related fixes.

I think it's MORE worth than a mere try :P




Extract from rc4's changelog:
[http://freetexthost.com/ts15cts6g6](http://freetexthost.com/ts15cts6g6)
(Intel/DRM related only) :)

---

### Post by c4pp4 on 2009-04-30
I didn't want to change the kernel so I've tried mtrr fix with jaunty kernel and it works great on my VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). I've also included EXAOptimizeMigration and MigrationHeuristic lines in xorg.conf and commented out GM965 in compiz blacklist in /usr/bin/compiz (#T="$T 8086:2a02 " # Intel GM965).
**Thanks psyke83**

```
Before:
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg02: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable

After:
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg02: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
**reg03: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining**
```

```
lspci -v | grep -A 7 VGA
```
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Memory at **e0000000** (64-bit, prefetchable) [size=**256M**]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

```
```
BASE_MEMORY="**0xe0000000**"
MEMORY_SIZE="**0x10000000**"
```

---

### Post by tschew on 2009-04-30
Here's a version of fixmtrr.sh which (I hope!) automates the process of passing the right base address and memory size to /proc/mtrr.

---

### Post by koycan on 2009-04-30
> **c4pp4 said:**
> I didn't want to change the kernel so I've tried mtrr fix with jaunty kernel and it works great on my VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). I've also included EXAOptimizeMigration and MigrationHeuristic lines in xorg.conf and commented out GM965 in compiz blacklist in /usr/bin/compiz (#T="$T 8086:2a02 " # Intel GM965).

So, you did not ever divert from the official Jaunty repos and not get other packages like intel driver, drm stuff, etc mentioned in this guide? Or, just the kernel?

---

### Post by Craig73 on 2009-04-30
> **Craig73 said:**
> My issue seems to be related to closing a graphics app.  If I close ppracer (3d) it hangs.  If I close world of goo (2d I think?) it hangs.  If I play a flash video and close that tab it hangs.  Note first I thought it was X hanging in the case of the games, but if I launch the game from a terminal, then I can kill/close the terminal to close the app (note I can't terminate the app directly)

Video does seem to play slowly in Totem... but fine in VLC and Flash (although Flash seems to intermitedly stick and needs a boot, by moving the slider on the movie timeline, to unstick it).

Anyway... at least for the hanging games, at least I have a way to play them without having to reboot ;-)  and more importantly a way to reproduce this problem without needing to reboot as I look for a solution.

[OK I've had a couple hangs launching ppracer... weird how it worked well for a while and now just doesn't with no change that I know if]


SOLVED !!! And the Intel drivers were not the issue but rather Pulse Audio (or some related pieces).   Backed up and removed my .pulse and .pulse-cookies folders and now everything is fine.  

[btw - I have not rolled back to the default Jaunty drivers yet so not sure if I will get different / non-pulseaudio / issues there]

[of course going to push things a bit now by running phoronix test suite]

---

### Post by ferossan on 2009-04-30
> **c4pp4 said:**
> I didn't want to change the kernel so I've tried mtrr fix with jaunty kernel and it works great on my VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). I've also included EXAOptimizeMigration and MigrationHeuristic lines in xorg.conf and commented out GM965 in compiz blacklist in /usr/bin/compiz (#T="$T 8086:2a02 " # Intel GM965).


Could you be so kind and post your "Section "Device"" in xorg.conf to make it more clear?
Thanks a lot

---

### Post by c4pp4 on 2009-05-01
> **koycan said:**
> So, you did not ever divert from the official Jaunty repos and not get other packages like intel driver, drm stuff, etc mentioned in this guide? Or, just the kernel?
Yes that's right, everything is from Jaunty repos. I've just changed the xorg.conf, mtrr, /usr/bin/compiz and unchecked "unredirect fullscreen windows" in general settings of compiz. My laptop uptime is now 17:34 hours without problems. Glxgears test gives me 832.285 FPS and flash is playing smoothly, before it was some 500 FPS and choppy flash.


> **ferossan said:**
> Could you be so kind and post your "Section "Device"" in xorg.conf to make it more clear?
Thanks a lot
my xorg.conf
```
Section "Device"
	Identifier	"Configured Video Device"
[B]	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
[/B]EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

part of my /usr/bin/compiz
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
**#T="$T 8086:2a02 " # Intel GM965**
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T
```

---

### Post by pappfer on 2009-05-01
Linux Kernel v2.6.30-rc4 is out, hope they'll upload it to [Ubuntu's kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), soon.

What are the differences between official kernels and kernel's from Ubuntu's PPA? What patches Ubuntu use, if any?

Hope this new version of kernel will increase Intel's video card performance.

---

### Post by breaddawson on 2009-05-01
I'm using Dell inspiron 700m with a 855GM
but this workaround does not work for me
i got 300fps after using this method instead of 500 fps  before in glxgears
and i actually felt the difference except for the data reported by glxgears

now i'm rolling back and look forward for another workaround which is suited to my graphic card

---

### Post by zevans on 2009-05-01
> **StorMFreak said:**
> The laptop has a Intel GMA 950, and I am noticing a lot of flickering on the screen.  It's not unbearable, but it's definitely irritating.  It also seems that it's just laggy in general, and I'm guessing the video issue has something to do with it.  Will the original poster's tips help me, or should I be looking down a different route?  Thanks!

OP will help with lagginess, but will not help with flickering if it's the same as I've got...

I've got a flicker in the sense of the backlight changing itself in a bizarre way, and it's only ever happened under the last couple of Jaunty kernels before release. Doesn't happen with older or newer kernels, and I have seen a few people report strange ACPI goings on with that kernel too. It also only happens on battery, which would fit with this explanation. It's kind of like it's trying too hard to keep the backlight dim...

---

### Post by pappfer on 2009-05-01
2.6.30 RC4 kernel already appeared in Ubuntu's kernel PPA.
I've did this guide with this new kernel and I noticed some performance increase.
MTRR fix seems to do nothing for me, the "Before" and "After" values are exactly the same which is fine I guess.

Although I'm wondering how could we keep our system up-to-date? I mean, kernel is still in RC and also there might be a new version of libdrm coming out, etc... The best would be to check these websites for kernels, for newer version of libdrm, etc and install the latest of them?
It's fine with the video driver cause it has a repository, but what about the others?

---

### Post by RacerII on 2009-05-01
For anyone with an eeepc 1000h and want to try the 2.6.30 kernel with the rt2860 module build in , try my kernel posted here:

[http://forum.eeeuser.com/viewtopic.php?id=66573](http://forum.eeeuser.com/viewtopic.php?id=66573)

---

### Post by ad5os on 2009-05-01
Hey thanks for these fixes.. but... is there a repository that would have all these fixes solved?

BTW???  Why did the Ubuntu people release a kernel that was so buggy for the MOST common integrated graphics chipset???  I don't think you guys did Ubuntu a favor until you fixed all this for the vast majority of business and laptop computers!

---

### Post by jerrylamos on 2009-05-01
planetpenguin-racer fps

I'm not into games.  I do ubuntu internet mail, news videos, office write & spreadsheet, YouTube videos, try to run latest ubuntu currently karmic, ...

I've got 4 pc's, a Thinkpad with i830 graphics, a ThinkCentre with i845 graphics. a Compaq with ATI, and a Thinkpad with ATI.  Three out of the four have had video trouble (!) with intrepid, jaunty, now karmic.

How do I get fps out of planet penguin?  
I did sudo apt-get install planetpenguin-racer which it did.

What menu selections?  How do you get fps?

Thanks, Jerry

---

### Post by Craig73 on 2009-05-01
> **jerrylamos said:**
> 

What menu selections?  How do you get fps?

Thanks, Jerry


Configuration - Graphics - Display FPS

Then play a game

---

### Post by Craig73 on 2009-05-01
> **ad5os said:**
> Hey thanks for these fixes.. but... is there a repository that would have all these fixes solved?

BTW???  Why did the Ubuntu people release a kernel that was so buggy for the MOST common integrated graphics chipset???  I don't think you guys did Ubuntu a favor until you fixed all this for the vast majority of business and laptop computers!

Agreed... 

There have been some great suggestions about changing the scheduling to allow more of April to allow the schedule to slip in the face of major issues.

---

### Post by Craig73 on 2009-05-01
> **breaddawson said:**
> I'm using Dell inspiron 700m with a 855GM
but this workaround does not work for me
i got 300fps after using this method instead of 500 fps  before in glxgears
and i actually felt the difference except for the data reported by glxgears

now i'm rolling back and look forward for another workaround which is suited to my graphic card

Glxgears is not a benchmark... and most of the time yields little useful information beyond glxgears runs.

---

### Post by Craig73 on 2009-05-01
> **c4pp4 said:**
>  My laptop uptime is now 17:34 hours without problems. Glxgears test gives me 832.285 FPS and flash is playing smoothly, before it was some 500 FPS and choppy flash.


As it can't be said enough... Glxgears is not a benchmark.  Run planet penguin racer if you have nothing else.

Although that's great to hear about stability and flash.  [Ironically what I thought was a video problem on my machine was actually pulse audio]

---

### Post by jerrylamos on 2009-05-01
> **Craig73 said:**
> As it can't be said enough... Glxgears is not a benchmark.  Run planet penguin racer if you have nothing else.

Although that's great to hear about stability and flash.  [Ironically what I thought was a video problem on my machine was actually pulse audio]

So I got planetpenguin-racer on one pc from apt-get and extreme tux racer on another from synaptic and ran a demo on both.

How do I get fps frames per second from them?  I do internet and applications however I'm not a game player.  I've certainly had video problems with i830 and i845 and ATI on intrepid jaunty and now karmic.

Thanks, Jerry

---

### Post by Arup on 2009-05-01
> **jerrylamos said:**
> So I got planetpenguin-racer on one pc from apt-get and extreme tux racer on another from synaptic and ran a demo on both.

How do I get fps frames per second from them?  I do internet and applications however I'm not a game player.  I've certainly had video problems with i830 and i845 and ATI on intrepid jaunty and now karmic.

Thanks, Jerry

You can get FPS via video config tab.

---

### Post by Craig73 on 2009-05-01
> **jerrylamos said:**
> So I got planetpenguin-racer on one pc from apt-get and extreme tux racer on another from synaptic and ran a demo on both.

How do I get fps frames per second from them?  I do internet and applications however I'm not a game player.  I've certainly had video problems with i830 and i845 and ATI on intrepid jaunty and now karmic.

Thanks, Jerry

In PPRacer
Configuration - Graphics - Display FPS
Then play a game

I'd also suggest using the same app and version on both machines for benchmarking as each game will generate different FPS (The frame rate is all about what and how they draw stuff on the screen)

(although one game based off the other the difference may not be significant)

---

### Post by SteveMcQwark on 2009-05-01
Everything worked well (a couple of total freezes, but that is expected) until the brightness controls randomly broke. Rebooting did nothing. Fixed it by booting into the default kernel (just to KDM). On reboot back into the new kernel they worked again. 

Just a note to those couple of people I've seen who have brightness issues in the new kernel.

Any idea why this would be? Is there some setting that the old kernel would know how to fix on boot up that the new kernel wouldn't?

---

### Post by Quinn The Eskimo on 2009-05-01
thank you very much
my computer's primary function is to stream video for my viewing pleasure
i found this thread after a quick search... read the first post and decided there had to be an easier way lol... after seeing it linked in other threads i finally caved and tried it... it took a few minutes, but i can now watch flash video again

---

### Post by idrivefast on 2009-05-01
I'm so sorry, I just suck at this. I really want to make this work and I've read through this whole thread and thought I did it right but nothing seems to be working. 

** The first problem was that NO video would work at all. So I tried the method at the begining of this thread and all it did was loose my wifi network driver. I reinstalled because I couldnt figure out how to roll back my system. I am getting really frustrated, I would love a little help....please!

---

### Post by sandb on 2009-05-01
> **Phil Urich said:**
> Strangely enough, I don't seem to be able to boot from either 2.6.30rc2 or 2.6.30rc3:

```
Error 13: Invalid or unsupported executable format
```

Worth noting is that my /boot partition is ext4, I'm not really sure why 2.6.30 would have a problem with that when 2.6.28 doesn't, but who knows.

I'm running the 2.6.30rc2 kernel right now on an ext4 root mount, so might be something non-ext4 related.

---

### Post by djuliette on 2009-05-02
I installed the 30rc3 kernel several days ago and the video is much better, however I just noticed my built in card reader no longer works. Booting into the older kernel /dev/sdb is there but booting to the 30rc3 kernel /dev/sdb is missing.  Is this a case where I have to configure the kernel and compile?

---

### Post by pappfer on 2009-05-02
> **SteveMcQwark said:**
> Just a note to those couple of people I've seen who have brightness issues in the new kernel.
I had brightness issues when using RC2 kernel, too. Now I'm using RC4 kernel and it works fine.

Although sound seems to have some issues. It works great by default but if I make my notebook sleep and then wake it up sound is gone. Don't know why?!

---

### Post by c4pp4 on 2009-05-02
> **Craig73 said:**
> As it can't be said enough... Glxgears is not a benchmark.  Run planet penguin racer if you have nothing else.

Although that's great to hear about stability and flash.  [Ironically what I thought was a video problem on my machine was actually pulse audio]

Ok so planet penguin gives me 10-15fps more.
Can you please tell more about pulse problem?

---

### Post by Marlock on 2009-05-02
Hi!

My Video Card is 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

I'm using the ubuntu's ppa kernel 2.6.30-rc4 and it seems to improve a lot performances using EXA. But i've got a problem.

Using EXA, Xorg increase the ram usage in exponential way so after 2-3 hours i've got to restart X.

I tried the fixmtrr.sh script but i haven't noticed any differences.

Using UXA, instead of using RAM, it fills SWAP causing a really laggy system.

I'm the only one having this trouble?

I would like to use EXA for stability...Is there any workoround?

---

### Post by Craig73 on 2009-05-02
> **c4pp4 said:**
> Ok so planet penguin gives me 10-15fps more.
Can you please tell more about pulse problem?

Are you having anymore issues?  It sounded like the MTRR fix resolved most of yours...

In my case video playback was slow only in Totem (Movie Player), video paused in Flash but could be resumed, and games would hang when quiting or on occasion hung my machine. But I also had sound issues as well (no sound after the crackly login sound)... it seemed to be an old system wide mixer setup was messing things up and once I deleted the pulse audio configuration and went back to defaults sound worked and all my remaining seemingly video issues went away.  [Note - I had already went to the new kernel/video driver/etc. and have not reverted back yet to validate what combination produced what result]

---

### Post by djuliette on 2009-05-02
intel video seems to be fixed now. The latest updates and the 30rc4 kernel has brought my video performance to where it was with ubuntu 8.10.
And installing the 30rc4 kernel fixed my card reader, so everything is running perfectly now.

---

### Post by S.A.A on 2009-05-02
> **Marlock said:**
> Hi!

My Video Card is 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

I'm using the ubuntu's ppa kernel 2.6.30-rc4 and it seems to improve a lot performances using EXA. But i've got a problem.

Using EXA, Xorg increase the ram usage in exponential way so after 2-3 hours i've got to restart X.

I tried the fixmtrr.sh script but i haven't noticed any differences.

Using UXA, instead of using RAM, it fills SWAP causing a really laggy system.

I'm the only one having this trouble?

I would like to use EXA for stability...Is there any workoround?
I confirm this problem with my:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```
So after doing "just regular" things with "uxa" enabled for one hours or two, it starts using swap (I've 1 gb of ram) and rapidly swap becomes full :(.

---

### Post by dagelsbagels on 2009-05-02
I followed the instructions as described, when i rebooted after the splash screen all i got was a black screen (no login window.) It went through grub fine and the splash screen fine, I noticed after the splash screen some lines showed up and one of the had a red star beside it saying something like "no suitable module for running kernel found" Please help!! :confused:

---

### Post by c4pp4 on 2009-05-02
> **Craig73 said:**
> Are you having anymore issues?  It sounded like the MTRR fix resolved most of yours...

Exactly, no more issues. The first version of Ubuntu which I am happy with because everything works :) Thank you!

---

### Post by Craig73 on 2009-05-02
> **S.A.A said:**
> I confirm this problem with my:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```
So after doing "just regular" things with "uxa" enabled for one hours or two, it starts using swap (I've 1 gb of ram) and rapidly swap becomes full :(.

FWIW - I do not see this issue with 2.6.30-RC2 (855GME)

---

### Post by Craig73 on 2009-05-02
> **Craig73 said:**
> FWIW - I do not see this issue with 2.6.30-RC2 (855GME)

Installed RC4 to see if I get the memory issues described / I have noted RC4 is 4-5 FPS faster (in ppracer) over RC2 and video is smoother.  

Finding with RC2/4 I do get hung up in games but at times it works for a while flawlessly so I'm not sure the issue...

---

### Post by jerrylamos on 2009-05-02
xorg edgers PPA as suggested at top of this forum ran, but slower.

Thanks for the directions on how to revert!

This is an IBM Thinkpad R31, 1 gHz Celeron, i830 integrated video, 512 mb

Runs better with rc4 and "uxa" than the way at the beginning at the forum.

I used benchmark glxdragon from Tom Murphy.  It's a pretty heavy duty rotating 3D figure with highlights and shadows.  2.3 fps with edger stuff, 2.8 using the revert directions but leaving on rc4 and "uxa".

Thanks for all the input and things to try.

Jerry

---

### Post by Mr_bleu on 2009-05-02
Any word on an update to fix this?  I don't think folks should have to tinker around with the operating system to get basic 3d graphics.  And Intel graphics are pretty basic.

---

### Post by Mamsaac on 2009-05-02
First of all: thank you very much for this thread. It fixed BroodWar, as well as other things that got slowed down badly.

Second, you mention that it is necessary to run the script after each re-start of the X server. I was wondering what was the recommended method for doing that automatically.

Thanks in advance =)

---

### Post by quackeroni_pizza on 2009-05-03
I agree this must be fixed by an update that does not require manual tinkering....

---

### Post by Arup on 2009-05-03
> **quackeroni_pizza said:**
> I agree this must be fixed by an update that does not require manual tinkering....

Actually if you are running the newer G31/35 and above series chip, all you have to do is to enable uxa in xorg, no need to update xorg or kernel, everything works fine, Google Earth, Penguin racer etc. Best of all no crashes. I haven't tried the kernel way but using newer xorg from ppa made the system unusable and I had to revert back to the xorg supplied with Jaunty. For older chipsets and other 9xx series Intel, you have no resort but to go the recommended way of changing kernel and driver and then applying mttr fix.

---

### Post by Forceflow on 2009-05-03
I'm pretty new to this issue, but enabling UXA in xorg.conf already boosted performance a lot. No more sloppy windows and grinding to a halt when a lot of effects are going on ...

Intel 945GM

---

### Post by treesurf on 2009-05-03
I am also curious if there is going to be an update to fix this bug.  For the moment I have reverted back to the older Intel driver because I haven't had time to tinker with these fixes yet, but it would be nice to know that the Ubuntu folks are working on this and plan to come up with a real fix.  Any way to find out what's going on with it?

---

### Post by WhiteHorse on 2009-05-03
I'm getting 10fps on penguin racer, sometimes 15.
/etc/X11/xorg.conf
Section "Device"
	Identifier 	"intel"
        Driver     	"intel"
	Option 		"AccelMethod" 	"UXA"
	Option 		"XvMC" 	"true"
	Option 		"Tiling" "false"
EndSection

I ran the Nexuiz timedemo and got 23fps average on 640x480. Desktop effects are working after doing some other fix. Open-arena runs great at full 1280x800. Google Earth works well, as does glest, chromium, lincity-ng, and flash, mpeg video, etc. Glxgears gets 593fps.

This is for a:Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

I am using the stock jaunty kernel, stock intel driver, etc.

---

### Post by Sarvatt on 2009-05-03
Why would you possibly recommend manual mtrr setup when you can just boot with enable_mtrr_cleanup to get the same results without the chance of screwing anything up? I have to use enable_mtrr_cleanup mtrr_spare_reg_nr=1 on all my ubuntu stock kernels where those options aren't enabled by default, but I use an aspire one with a bug that has a full mtrr list so I need that spare reg. 

Also note EXA support is dropped in the xserver-xorg-video-intel drivers in xorg-edgers now, my package on 042709 was the last one with EXA support. I wouldn't recommend disabling tiling unless absolutely required, there have been major changes in that area lately and disabling it would help far fewer than it'd hurt in my opinion (aka only really needed on 8xx series right now last I checked).

---

### Post by psyke83 on 2009-05-03
> **Sarvatt said:**
> Why would you possibly recommend manual mtrr setup when you can just boot with enable_mtrr_cleanup to get the same results without the chance of screwing anything up? I have to use enable_mtrr_cleanup mtrr_spare_reg_nr=1 on all my ubuntu stock kernels where those options aren't enabled by default, but I use an aspire one with a bug that has a full mtrr list so I need that spare reg. 

Also note EXA support is dropped in the xserver-xorg-video-intel drivers in xorg-edgers now, my package on 042709 was the last one with EXA support. I wouldn't recommend disabling tiling unless absolutely required, there have been major changes in that area lately and disabling it would help far fewer than it'd hurt in my opinion (aka only really needed on 8xx series right now last I checked).

The enable_mtrr_cleanup does *not* solve this issue. With kernel 2.6.28, the write-combining range is never set. With the 2.6.30 kernel, write-combining is correctly set upon the first initialization of X, but the write-combining range will disappear upon restarting X. The script therefore has a purpose (but could be improved to only set the write-combining range when necessary). Of course, getting this fixed the correct way is more important, and you can see a bug is filed and triaged.

As for the tiling issue, I have an 855GM chipset and can confirm that tiling breaks my setup. Therefore, I ensured the guide is conservative (i.e., works for as many people as possible), with the added instructions to re-enable tiling only after it has been verified that direct rendering otherwise works.

---

### Post by scarf on 2009-05-03
> **treesurf said:**
> I am also curious if there is going to be an update to fix this bug.  For the moment I have reverted back to the older Intel driver because I haven't had time to tinker with these fixes yet, but it would be nice to know that the Ubuntu folks are working on this and plan to come up with a real fix.  Any way to find out what's going on with it?

that seems like a more doable solution for me, can you explain how to do that?

i have Intel 82852/82855 GM/GME/PM/GMV

---

### Post by scarf on 2009-05-03
> **VMC said:**
> I just want to report here that I found a fix for my video problem.

Video card:
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

Solution was to revert back to Intel driver 2.4. Go [HERE]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") for explanation.

My video now exactly the same as it was using Hardy. Speed is the same. No more choppy avi, vob's. Everything works.


ok thanks, that's what i was looking for.  maybe this can be added to the first post?  after reverting back to 2.4 drivers, my video performance seems to be back to how it was in intrepid, and my CPU is also running much cooler, a plus for this 6 year old laptop that could go at any moment!

---

### Post by scarf on 2009-05-03
> **jcapitan said:**
> um, i'm taking a step back...  This is a wonderful fix.  Thank you for making it available!   But this for a relatively standard video card, not a "vostok-omsk 3".  Can/should a "regular" user who is trying u-9.04 for the 1st time be expected to do this? Just curious.....

no

---

### Post by linux_lover69 on 2009-05-03
I have a computer with Intel graphics and every video player crashes when I try to play any video's, this is totems log from the terminal. ```
xp@xp-desktop:~$ totem 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 94 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
``` Will this fix, fix it??:confused: Sorry if it has nothing to do with it.

---

### Post by Mr_bleu on 2009-05-03
> **Arup said:**
> *Actually if you are running the newer G31/35 and above series chip, all you have to do is to enable uxa in xorg, no need to update xorg or kernel, everything works fine, Google Earth, Penguin racer etc. Best of all no crashes. I haven't tried the kernel way but using newer xorg from ppa made the system unusable and I had to revert back to the xorg supplied with Jaunty. For older chipsets and other 9xx series Intel, you have no resort but to go the recommended way of changing kernel and driver and then applying mttr fix.*
:confused:
What I am wondering is **when or If** there will be a fix applied via update manager or synaptic.  I have the intel 945gm onboard graphics.  I haven't seen an xorg.conf that had much in it since 7.10 (I could be wrong, I'll check once 8.04 is reinstalled) for my card.  It used to list all kinds of things.
:confused:

---

### Post by wyth on 2009-05-03
I'm only posting this response because I'm subscribed to this thread, and my inbox is being flooded with the same question -- when will the Intel issue be fixed.

The release notes, links from there, [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=NzA0NQ"), and other places, have all reported a major overhaul of this Intel driver, moving from EXA to UXA.  The new versions have been incrementally released from upstream, which then works its way down into the various distributions.  

So as I understand it, this is an upstream thing, not an Ubuntu thing.  Yes, a lot of people use these chips, but depending on your setup, everyone using these chips has different results (I'm having next to no problems with a GM965).  So it seems it wasn't enough to be a show-stopper.  After all, you won't read complaints on ubuntuforums from people whose chips *work*.

When the UXA driver is stabilized, it'll be the default (I believe EXA isn't even included in 2.6.30 anymore, at least in the release candidates that some people have been testing.)  

If you're not comfortable trying the more in-depth tweaks included here, the lighter-impact X11 tweaks may help (turning tiling on or off, setting the MigrationHeuristic to greedy, setting the EXAOptimizeMigration to true).  You may not get great performance yet, but it should help until a newer kernel is available -- and they are coming out fairly regularly, 2.6.28 was released just about a week after 9.04 was released.

Another thing to try, if you're not willing to try out release candidates of the kernel or intel drivers, is to turn off Compiz.  That may help.

You can also check the [Ubuntu-X Team page]("https://wiki.ubuntu.com/X/"); there's a lot of good info linked from there.

**EDIT:**
[This article on the Intel chip issues in 9.04 was just dugg]("http://www.h-online.com/open/Ubuntu-9-04-and-Intel-graphics--/features/113196"), and it does a decent job of explaining the various issues with the chip, development, and its roll-out.

One paragraph especially gives some good info:
> As Packard helpfully [calculates]("http://keithp.com/blogs/Sharpening_the_Intel_Driver_Focus/") – GEM or no GEM, mode setting in the kernel or by the driver, four different 2D (none, XAA, EXA, UXA) and three different 3D (none, DRI, DRI2) acceleration options gives 48 theoretical combinations the driver needs to cope with (although some combinations are in practice not achievable, since, for example, UXA requires GEM and DRI2 is not compatible with EXA). There is also a further difficulty – the driver must control a wide range of Intel graphics chips and different versions of these chips. This makes systematic testing nigh on impossible.

But it's not all dark; people know about it, and it seems they're working on it.

---

### Post by Phil Urich on 2009-05-04
> **sandb said:**
> I'm running the 2.6.30rc2 kernel right now on an ext4 root mount, so might be something non-ext4 related.

What in the world could it be, then? I tried removing all of the previous 2.6.30 versions and installing rc4 tonight and I'm still getting "Error 13: Invalid or unsupported executable format" and being unable to load the kernel from within Grub....and google's search results only show up with a handful of hits, one of which is my post!

Edit: Came across [this Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331"), maybe currently thing will simply screw up for any newly installed kernels on an ext4 boot partition?  The working kernels, after all, were installed *before* I did the transition...

---

### Post by glaze on 2009-05-04
I noticed that I cannot apply the i915 MCHBAR patch ([http://lists.freedesktop.org/archives/intel-gfx/2009-January/001186.html]("http://lists.freedesktop.org/archives/intel-gfx/2009-January/001186.html")) to 2.6.30 to get tiling working so I made my own patch based on it. With this patch I can enable tiling on my Eee PC 701 and glxgears went from 100 fps to 145 fps and by own 3D engine fps went from 60 to 85. I created the patch against 2.6.30-rc4. Here's my patch (based on the patch by Jesse Barnes):
```

diff -Naur a/drivers/gpu/drm/i915/i915_drv.h b/drivers/gpu/drm/i915/i915_drv.h
--- a/drivers/gpu/drm/i915/i915_drv.h	2009-05-04 12:13:10.281378416 +0300
+++ b/drivers/gpu/drm/i915/i915_drv.h	2009-05-04 10:23:08.976353424 +0300
@@ -142,6 +142,7 @@
 	unsigned int status_gfx_addr;
 	drm_local_map_t hws_map;
 	struct drm_gem_object *hws_obj;
+	struct resource mch_res;
 
 	unsigned int cpp;
 	int back_offset;
diff -Naur a/drivers/gpu/drm/i915/i915_gem_tiling.c b/drivers/gpu/drm/i915/i915_gem_tiling.c
--- a/drivers/gpu/drm/i915/i915_gem_tiling.c	2009-05-04 12:13:10.321377153 +0300
+++ b/drivers/gpu/drm/i915/i915_gem_tiling.c	2009-05-04 10:46:28.220355077 +0300
@@ -25,6 +25,7 @@
  *
  */
 
+#include <linux/acpi.h>
 #include "linux/string.h"
 #include "linux/bitops.h"
 #include "drmP.h"
@@ -81,6 +82,212 @@
  * to match what the GPU expects.
  */
 
+#define MCHBAR_I915 0x44
+#define MCHBAR_I965 0x48
+#define MCHBAR_SIZE (4*4096)
+
+#define DEVEN_REG 0x54
+#define DEVEN_MCHBAR_EN (1 << 28)
+
+/*
+ * ACPI resource checking fun.  So the MCHBAR has *probably* been set
+ * up by the BIOS since drivers need to poke at it, but out of paranoia
+ * or whatever, many BIOSes disable the MCHBAR at boot.  So we check
+ * to make sure any existing address is reserved before using it.  If
+ * we can't find a match or there is no address, allocate some new PCI
+ * space for it, and then enable it.  And of course 915 has to be different
+ * and put its enable bit somewhere else...
+ */
+static acpi_status __init check_mch_resource(struct acpi_resource *res,
+                                            void *data)
+{
+       struct resource *mch_res = data;
+       struct acpi_resource_address64 address;
+       acpi_status status;
+
+       if (res->type == ACPI_RESOURCE_TYPE_FIXED_MEMORY32) {
+               struct acpi_resource_fixed_memory32 *fixmem32 =
+                       &res->data.fixed_memory32;
+               if (!fixmem32)
+                       return AE_OK;
+
+               if ((mch_res->start >= fixmem32->address) &&
+                   (mch_res->end < (fixmem32->address +
+                                     fixmem32->address_length))) {
+                       mch_res->flags = 1;
+                       return AE_CTRL_TERMINATE;
+               }
+       }
+       if ((res->type != ACPI_RESOURCE_TYPE_ADDRESS32) &&
+           (res->type != ACPI_RESOURCE_TYPE_ADDRESS64))
+               return AE_OK;
+
+       status = acpi_resource_to_address64(res, &address);
+       if (ACPI_FAILURE(status) ||
+          (address.address_length <= 0) ||
+          (address.resource_type != ACPI_MEMORY_RANGE))
+               return AE_OK;
+
+       if ((mch_res->start >= address.minimum) &&
+           (mch_res->end < (address.minimum + address.address_length))) {
+               mch_res->flags = 1;
+               return AE_CTRL_TERMINATE;
+       }
+       return AE_OK;
+}
+
+static acpi_status __init find_mboard_resource(acpi_handle handle, u32 lvl,
+                                              void *context, void **rv)
+{
+       struct resource *mch_res = context;
+
+       acpi_walk_resources(handle, METHOD_NAME__CRS,
+                           check_mch_resource, context);
+
+       if (mch_res->flags)
+               return AE_CTRL_TERMINATE;
+
+       return AE_OK;
+}
+
+static int __init is_acpi_reserved(u64 start, u64 end, unsigned not_used)
+{
+       struct resource mch_res;
+
+       mch_res.start = start;
+       mch_res.end = end;
+       mch_res.flags = 0;
+
+       acpi_get_devices("PNP0C01", find_mboard_resource, &mch_res, NULL);
+
+       if (!mch_res.flags)
+               acpi_get_devices("PNP0C02", find_mboard_resource, &mch_res,
+                                NULL);
+
+       return mch_res.flags;
+}
+
+/* Allocate space for the MCH regs if needed, return nonzero on error */
+static int
+intel_alloc_mchbar_resource(struct drm_device *dev)
+{
+       struct pci_dev *bridge_dev;
+       drm_i915_private_t *dev_priv = dev->dev_private;
+       int reg = IS_I965G(dev) ? MCHBAR_I965 : MCHBAR_I915;
+       u32 temp_lo, temp_hi = 0;
+       u64 mchbar_addr;
+       int ret;
+
+       bridge_dev = pci_get_bus_and_slot(0, PCI_DEVFN(0,0));
+       if (!bridge_dev) {
+               DRM_DEBUG("no bridge dev?!\n");
+               return -ENODEV;
+       }
+
+       if (IS_I965G(dev))
+               pci_read_config_dword(bridge_dev, reg + 4, &temp_hi);
+       pci_read_config_dword(bridge_dev, reg, &temp_lo);
+       mchbar_addr = ((u64)temp_hi << 32) | temp_lo;
+
+       /* If ACPI doesn't have it, assume we need to allocate it ourselves */
+       if (mchbar_addr &&
+           is_acpi_reserved(mchbar_addr, mchbar_addr + MCHBAR_SIZE, 0))
+               return 0;
+
+       /* Get some space for it */
+       ret = pci_bus_alloc_resource(bridge_dev->bus, &dev_priv->mch_res,
+                                    MCHBAR_SIZE, MCHBAR_SIZE,
+                                    PCIBIOS_MIN_MEM,
+                                    0,   pcibios_align_resource,
+                                    bridge_dev);
+       if (ret) {
+               DRM_DEBUG("failed bus alloc: %d\n", ret);
+               dev_priv->mch_res.start = 0;
+               return ret;
+       }
+
+       if (IS_I965G(dev))
+               pci_write_config_dword(bridge_dev, reg + 4,
+                                      upper_32_bits(dev_priv->mch_res.start));
+
+       pci_write_config_dword(bridge_dev, reg,
+                              lower_32_bits(dev_priv->mch_res.start));
+
+       return 0;
+}
+
+/* Setup MCHBAR if possible, return true if we should disable it again */
+static bool
+intel_setup_mchbar(struct drm_device *dev)
+{
+       struct pci_dev *bridge_dev;
+       int mchbar_reg = IS_I965G(dev) ? MCHBAR_I965 : MCHBAR_I915;
+       u32 temp;
+       bool need_disable = false, enabled;
+
+       bridge_dev = pci_get_bus_and_slot(0, PCI_DEVFN(0,0));
+       if (!bridge_dev) {
+               DRM_DEBUG("no bridge dev?!\n");
+               goto out;
+       }
+
+       if (IS_I915G(dev) || IS_I915GM(dev)) {
+               pci_read_config_dword(bridge_dev, DEVEN_REG, &temp);
+               enabled = !!(temp & DEVEN_MCHBAR_EN);
+       } else {
+               pci_read_config_dword(bridge_dev, mchbar_reg, &temp);
+               enabled = temp & 1;
+       }
+
+       /* If it's already enabled, don't have to do anything */
+       if (enabled)
+               goto out;
+
+       if (intel_alloc_mchbar_resource(dev))
+               goto out;
+
+       need_disable = true;
+
+       if (IS_I915G(dev) || IS_I915GM(dev))
+               pci_write_config_dword(bridge_dev, DEVEN_REG,
+                                      temp | DEVEN_MCHBAR_EN);
+       else
+               pci_write_config_dword(bridge_dev, mchbar_reg, temp | 1);
+
+out:
+       return need_disable;
+}
+
+static void
+intel_teardown_mchbar(struct drm_device *dev, bool disable)
+{
+       drm_i915_private_t *dev_priv = dev->dev_private;
+       struct pci_dev *bridge_dev;
+       int mchbar_reg = IS_I965G(dev) ? MCHBAR_I965 : MCHBAR_I915;
+       u32 temp;
+
+       bridge_dev = pci_get_bus_and_slot(0, PCI_DEVFN(0,0));
+       if (!bridge_dev) {
+               DRM_DEBUG("no bridge dev?!\n");
+               return;
+       }
+
+       if (disable) {
+               if (IS_I915G(dev) || IS_I915GM(dev)) {
+                       pci_read_config_dword(bridge_dev, DEVEN_REG, &temp);
+                       temp &= ~DEVEN_MCHBAR_EN;
+                       pci_write_config_dword(bridge_dev, DEVEN_REG, temp);
+               } else {
+                       pci_read_config_dword(bridge_dev, mchbar_reg, &temp);
+                       temp &= ~1;
+                       pci_write_config_dword(bridge_dev, mchbar_reg, temp);
+               }
+       }
+       if (dev_priv->mch_res.start)
+               release_resource(&dev_priv->mch_res);
+}
+
+
 /**
  * Detects bit 6 swizzling of address lookup between IGD access and CPU
  * access through main memory.
@@ -91,6 +298,7 @@
 	drm_i915_private_t *dev_priv = dev->dev_private;
 	uint32_t swizzle_x = I915_BIT_6_SWIZZLE_UNKNOWN;
 	uint32_t swizzle_y = I915_BIT_6_SWIZZLE_UNKNOWN;
+	bool need_disable;
 
 	if (!IS_I9XX(dev)) {
 		/* As far as we know, the 865 doesn't have these bit 6
@@ -101,6 +309,9 @@
 	} else if (IS_MOBILE(dev)) {
 		uint32_t dcc;
 
+		/* Try to make sure MCHBAR is enabled before poking at it */
+		need_disable = intel_setup_mchbar(dev);
+
 		/* On mobile 9xx chipsets, channel interleave by the CPU is
 		 * determined by DCC.  For single-channel, neither the CPU
 		 * nor the GPU do swizzling.  For dual channel interleaved,
@@ -135,11 +346,11 @@
 			break;
 		}
 		if (dcc == 0xffffffff) {
-			DRM_ERROR("Couldn't read from MCHBAR.  "
-				  "Disabling tiling.\n");
 			swizzle_x = I915_BIT_6_SWIZZLE_UNKNOWN;
 			swizzle_y = I915_BIT_6_SWIZZLE_UNKNOWN;
 		}
+
+		intel_teardown_mchbar(dev, need_disable);
 	} else {
 		/* The 965, G33, and newer, have a very flexible memory
 		 * configuration.  It will enable dual-channel mode

```
DISCLAIMER: I'm not a kernel hacker, just a random goon who likes to code. While this patch works for my Eee PC 701, I cannot guarantee that it works for you or that it doesn't burn your house, eat your dog etc.

---

### Post by jbernardo on 2009-05-04
I just tried rc4, and while exa performance went down (15fps in glblur), uxa performance in ppracer went up to 15 fps (in glblur it stayed at 15). uxa now seems usable. I haven't tested ppracer with exa and 2.6.30-rc4

---

### Post by wyth on 2009-05-04
> **jbernardo said:**
> I just tried rc4, and while exa performance went down (15fps in glblur), uxa performance in ppracer went up to 15 fps (in glblur it stayed at 15). uxa now seems usable. I haven't tested ppracer with exa and 2.6.30-rc4

You're getting that with rc4?  Are you using the Xorg Edger's repo?


Right now I'm getting 32 fps on glblur with:

[LIST]
[*]**Kernel:** 2.6.28-generic
[*]**GFX:** Intel X3100 (GM965/GL960)
[*]**Display Driver: **2.2.7.0-1ubuntu1~xup~1 from the X Updates repo (the stable version of Xorg Edgers
[/LIST]

My relevant xorg.conf info:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod" "UXA"
#       Option          "EXAOptimizeMigration" "true"
#       Option          "MigrationHeuristic" "greedy"
        Option          "XvMC" "true"
        Option          "Tiling" "true"
EndSection
```So that's 32 fps on glblur (nice little program) with no massive CPU or memory hits. But the general desktop response is still a little sluggish (menus not opening as snappily as before), which means I'm still looking for the right combination.  Not sure if I need XvMC, but I'm not having any video issues, and I've left tiling on.

But finding that right combination is also what [the article I linked to above]("http://www.h-online.com/open/Ubuntu-9-04-and-Intel-graphics--/features/113196") was getting at; there's such a wide variety of possible combinations, it's hard to find just the right one.

---

### Post by jbernardo on 2009-05-04
> **wyth said:**
> You're getting that with rc4?  Are you using the Xorg Edger's repo?

Yes, on a Aspire One (945GM chipset).

---

### Post by densou on 2009-05-04
> **wyth said:**
> But the general desktop response is still a little sluggish (menus not opening as snappily as before), which means I'm still looking for the right combination.

I hope my whole xorg.conf could be helpful for you :popcorn: (Jaunty default kernel, gma950/i945gc, Intel 2.7.0, compiz off, metacity on)

```
Section "Module"
	Load 	"ddc"
	Load 	"dri"
	Load 	"glx"
	Load	"GLcore"
	Load	"v4l"
EndSection

Section "Device"
	Identifier 	"Configured Video Device"
	Driver 		"intel"
	Option		"AccelMethod"	"UXA"
	Option          "XvMC"  "true"
#	Option		"EXAOptimizeMigration"		"true"
#	Option		"MigrationHeuristic"		"greedy"
	VideoRam	261376
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Monitor		"Generic Monitor"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "DRI"
	Mode 	0666
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Extensions"
	Option 		"Composite" 		"true"
EndSection
```

Note: I bought a Compaq TFT7000 during an electronic expo last weekend, this is the configuration which provides the best fidelity/performance after testing stuff for half a day.

---

### Post by wyth on 2009-05-04
I just tried the rc4 kernel and the Xorg Edgers drivers, and under my Device section, the only thing different from densou's is the VideoRam (I don't have that added).

My glblur fps is about 31 as opposed to 32 with 2.6.28-12-generic and the X Updates version of xserver-xorg-video-intel.

However, the desktop response seems a little quicker, and given that most people are getting rates like 15 fps, I don't think I have anything to complain about.

densou, is that module section in your xorg.conf necessary?

---

### Post by densou on 2009-05-04
> **wyth said:**
> I just tried the rc4 kernel and the Xorg Edgers drivers, and under my Device section, the only thing different from densou's is the VideoRam (I don't have that added).

it might help on MTRR issue but I don't know if it really works.
( Videoram Option, how to: [http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738) )

> densou, is that module section in your xorg.conf necessary?

well :lolflag: I used a Module Section on both Hardy and Intrepid, however I had no gain in Jaunty (beta) so I dropped it. However I tried latest Mandriva, Fedora & OpenSuse -stable/milestone/beta/preview/etc-

the first two distros ran :guitar: out-of-the-box so I asked myself: "could it be related to a tweaked xorg.conf from the start?"  I found that section was still there .... (and both include .29.1 kernel)....I'm still checking if it is useful :KS

---

### Post by muhannadfa on 2009-05-04
actually i suggest u to add a voting overall the topic
to sort out if it works for all
thanks in advance
-----------------------------------------
didn't improve things much in my machine

---

### Post by Uzi304 on 2009-05-04
After updating to this new kernel, when Ubuntu is starting up or shutting down, there's  a bunch of text instead of the normal bar. That's not a problem but when I put my laptop to sleep, when it wakes up, it just goes to the login screen and that's annoying. Any help?

---

### Post by Geistanon on 2009-05-04
AMAZING. I am VERY impressed with this guide. I'm using an Acer with the 945G set, and I have to say this was a tremendous boon. In intrepid ppracer was ~10 and after following this guide (in addition to the bonus tiling option) I'm getting ~50. Jaunty now runs beautifully! Thank you, thank you, thank you!

:guitar:

---

### Post by wyth on 2009-05-04
> **Uzi304 said:**
> After updating to this new kernel, when Ubuntu is starting up or shutting down, there's  a bunch of text instead of the normal bar. That's not a problem but when I put my laptop to sleep, when it wakes up, it just goes to the login screen and that's annoying. Any help?

Do you see "Loading apparmor module... [fail]" in that running text?

That's the one thing I've noticed with all these release candidate kernels.  I don't know if it's a problem, really, just something I noticed.

---

### Post by isleshocky77 on 2009-05-04
I'm not positive if my information already exists somewhere in this thread because it has gotten quite long. I wanted to throw in my experience in case it can help as well as to say that there should be a note about the Virtual Screen in the how-to.

I followed the how-to word for word and upon restarting I was presented with a fubar'd screen.  Green line down one side and repeating non usable windows which looked like some sort of warning.

While reading through some of the first 10 pages of this thread I noticed people complaining about a bug with virutal screens. I disabled the Virtual parameter in my xorg.conf file and presto I was able to login.  

I'm now using 1680x1050 on my external monitor instead of my laptop monitor and it runs beautifully. I'm actually able to use the highest appearance setting for the first time ever and I have a whole bunch of compiz effects turned on including cubed desktop and animated window actions.  I've tested video and it's all back to normal including high def video.

My setup is a Compaq Presario v2335us with Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

My next goal is to see if there are any work arounds for getting my virtual screen back setup so I can have my external and my laptop together.

---

### Post by isleshocky77 on 2009-05-04
> **wyth said:**
> Do you see "Loading apparmor module... [fail]" in that running text?

That's the one thing I've noticed with all these release candidate kernels.  I don't know if it's a problem, really, just something I noticed.

I have the same thing; however, I generally like seeing my bootup messages so I had it on while I was running 8.10 and I'm almost positive I had it then as well.  I know I definitely had it while running 9.04 without before running this tutorial.

---

### Post by zevans on 2009-05-05
> **treesurf said:**
> it would be nice to know that the Ubuntu folks are working on this and plan to come up with a real fix. 
They are for sure, but there isn't a bug, there are several, and for some people they interact - you fix one and it triggers another. Some are in the kernel, some are in mesa, some are in the Intel drivers...

>  Any way to find out what's going on with it?

Yes - keep an eye on the many bugs logged on bugs.launchpad.net. If you've got a particular set of symptoms it's worth searching around on launchpad and finding your bug(s) and keeping an eye on them, because for some of them there are ALREADY proposed fixes out and the guys need confirmation that the fix versions are good.

---

### Post by TheExplorer on 2009-05-05
Tried it also and I can say that the desktop response is a bit quicker indeed (menus etc.).
One question though: can I use **rc4** kernel instead of **rc2** as in your Guide?

Thank you btw for the manual!

---

### Post by robfindlay on 2009-05-05
Can someone describe how the MTRR issue manifests? 

Amazingly somehow I have all the nifty desktop effects--even got it working on an external monitor--the only thing I see is on occasion the screen sort of flickers for a second. 

Is that the MTRR issue?

> **densou said:**
> it might help on MTRR issue but I don't know if it really works.
( Videoram Option, how to: [http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738) )



well :lolflag: I used a Module Section on both Hardy and Intrepid, however I had no gain in Jaunty (beta) so I dropped it. However I tried latest Mandriva, Fedora & OpenSuse -stable/milestone/beta/preview/etc-

the first two distros ran :guitar: out-of-the-box so I asked myself: "could it be related to a tweaked xorg.conf from the start?"  I found that section was still there .... (and both include .29.1 kernel)....I'm still checking if it is useful :KS

---

### Post by acroporas on 2009-05-05
I tried to follow the instructions in the first post:

I got to the last command in step #2 and it gave: 

```
william@emachine:~$ sudo apt-get dist-upgrade
[sudo] password for william: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xserver-xorg-video-intel: Depends: libdrm-intel1 (>= 2.4.9) but 2.4.5-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```

I restarted the computer and tried again, and I got the same thing.

What should I do?

---

### Post by knievel84 on 2009-05-05
This worked great for me, but my wireless card is now not working. I even tried using a restricted driver, but it still didn't work. Any ideas?

---

### Post by crjackson on 2009-05-05
> **acroporas said:**
> I tried to follow the instructions in the first post:

I got to the last command in step #2 and it gave: 

```
william@emachine:~$ sudo apt-get dist-upgrade
[sudo] password for william: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xserver-xorg-video-intel: Depends: libdrm-intel1 (>= 2.4.9) but 2.4.5-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```

I restarted the computer and tried again, and I got the same thing.

What should I do?

I don't know if it would help but did you try running the code it requested?

```
sudo apt-get -f install
```

---

### Post by Tich666 on 2009-05-05
> **isleshocky77 said:**
> My next goal is to see if there are any work arounds for getting my virtual screen back setup so I can have my external and my laptop together.

You can easily achieve that with xrandr
```
xrandr
```
to show the connected displays.
```
xrandr --output HDMI-1 --auto --output LVDS --auto --right-of HDMI-1
```
something along the lines of that to enable both, the external monitor on the left of the laptop.

However once your virtual screen size exceeds 2048 in any direction, say goodbye to compiz and 3d effects.

Btw.. my mtrr values are [still]("http://ubuntuforums.org/showthread.php?p=7158322#post7158322") [borked.]("http://ubuntuforums.org/showthread.php?p=7166634#post7166634") Please help! :-k

---

### Post by wyth on 2009-05-05
> **TheExplorer said:**
> Tried it also and I can say that the desktop response is a bit quicker indeed (menus etc.).
One question though: can I use **rc4** kernel instead of **rc2** as in your Guide?

Thank you btw for the manual!

Yep, it works.  I just copied the terminal commands from the first post into a text file and replaced rc2 with whatever kernel I'm trying (rc3, rc4).  Then I copied that block of command from the text file into the terminal when I installed the release candidate.  Worked fine.

---

### Post by Throwup222 on 2009-05-05
> **acroporas said:**
> I tried to follow the instructions in the first post:

I got to the last command in step #2 and it gave: 

```
william@emachine:~$ sudo apt-get dist-upgrade
[sudo] password for william: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xserver-xorg-video-intel: Depends: libdrm-intel1 (>= 2.4.9) but 2.4.5-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```I restarted the computer and tried again, and I got the same thing.

What should I do?

Hi,

For some reason libdrm-intel1_2.4.9-1_i386.deb no longer exists on the server that the wget command tries to use.  I changed mine to libdrm-intel1_2.4.9-2_i386.deb.

BUT -- I just solved this problem 5 seconds ago, and I haven't actually tested the rest of the fix using this new package.  So beware!

---

### Post by relgames on 2009-05-05
Hi. I tried the steps mentioned at the beginning of this thread, and I failed at the "/proc/mtrr" step.

I tried it on my Dell E6500 laptop.

Here is my kernel & harware:
```
relgames@rg-work:~$ uname -a
Linux rg-work 2.6.30-020630rc2-generic #020630rc2 SMP Wed Apr 15 14:00:27 UTC 2009 i686 GNU/Linux

``````

relgames@rg-work:~$ lspci -v
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 024f
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ef98 [size=8]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 024f
    Flags: bus master, fast devsel, latency 0
    Memory at f6b00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

```xorg.conf:
```

Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true" # may break 3D rendering if enabled
EndSection

```xorg log:
```

relgames@rg-work:~$ cat /var/log/Xorg.0.log |grep UXA
(--) intel(0): Using UXA for acceleration

```fixmtrr.sh:
```

relgames@rg-work:~$ cat /usr/local/bin/fixmtrr.sh
echo "Before:"
echo "-------"
cat /proc/mtrr
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr

echo ""
echo "After:"
echo "------"
cat /proc/mtrr

```result of running fixmtrr.sh:
```

relgames@rg-work:~$ sudo fixmtrr.sh 
Before:
-------
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

After:
------
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

```So, nothing changes after I run fixmtrr.sh

I also tried with size=0x2... (I was confused by "Memory at e0000000 (**64-bit**, prefetchable) [size=256M]" line and tried to multiply by 2) with the same effect.

Also, I have the following lines at my source.list
```

deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA

deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main

```and did "apt-get update" and "apt-get upgrade", so I have the latest drivers etc.

I tried this guide on my second laptop (HP nx7300) and it works fine...

---

### Post by Uzi304 on 2009-05-05
> **wyth said:**
> Do you see "Loading apparmor module... [fail]" in that running text?

That's the one thing I've noticed with all these release candidate kernels.  I don't know if it's a problem, really, just something I noticed.

Yeah that's exactly what I get. Anyone know of a fix for the suspend/wake up problem?

---

### Post by Throwup222 on 2009-05-05
I used all the fixes in the first post, and the video is much smoother.  However, the fan on my laptop is spinning much faster all the time.  Instead of being inaudible at idle, it's spinning at about half its max speed.  Opening or doing anything sends it into overdrive.

Anyone else experiencing this?  The gain in video performance isn't worth the fan noise for me.

I'm using an HP NX 6110, Intel 915GM.

---

### Post by WhiteHorse on 2009-05-05
> **robfindlay said:**
> Can someone describe how the MTRR issue manifests? 

Amazingly somehow I have all the nifty desktop effects--even got it working on an external monitor--the only thing I see is on occasion the screen sort of flickers for a second. 

Is that the MTRR issue?

The MTRR issue was fixed in the latest intel drivers(2.7.x). Some reasons there are issues with mtrr's are because the graphics card shares memory with the system ram, but there is also ram in the cpu. If you have multiple cpus, it gets even more complicated because you may have 2 caches(cpu ram), and the system has to switch from cpu to cpu to access the video card memory, and if it's not there then it has to go to the system ram. Whereas a "normal" video card has it's own ram, processor, etc.

---

### Post by Valir on 2009-05-05
Problems with FONTS?!? 

Hi, I applied the advice on my computer (ACER 4060, Intel 900), after experiencing jerky and jumpy playback on fullscreen mode for FLASH video. 

It worked like a charm. Until a couple of days later I started to notice some weird behaviour with my fonts. Sometimes the fonts in Firefox get garbled, sometimes not. Today my terminal has all the fonts strangely aligned. Could this be related to the fix? 

Anotherthing, why is it necessary to sudo fixntrr.sh everytime after startup to get the Flash in order?

best

---

### Post by szoasis on 2009-05-06
thanks for this guide,but my 915GM/PM/GMS/910GML is not so happy for this guide.
when i just reboot the machine after i setup all the steps on the 1st post,my machine runs flawlessly,and flash flies....but just use for about 1 or 2 hours,my machine begins lagging&#65292;it seems that there is a huge IO or the system keeping swap in and out.
when i run "iotop -o",the IO r/w is very huge(around 2,3m/s),and interesting the huge IO is caused by many application(firefox,skype,pidgin and even gnome-terminal),but when i switch back to EXA,will not met this issue.
unfortunately,when i update my machine to the newest packages on the xorg-edge yesterday, i cannot use EXA anymore,when i comment on the line  Option "AccelMethod" "UXA" or just replace UXA to EXA,i always see 
intel(0): Using UXA for acceleration
 on the Xorg.0.log.and the IO problem always happened when i use my machine for several hours...:(

---

### Post by needhelp123 on 2009-05-06
After I rebooted I get the following message:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init
No init found. Try passing init = bootarg

Any help is appreciated.

Thanks.

---

### Post by PlaceboMessiah on 2009-05-06
> **acroporas said:**
> I tried to follow the instructions in the first post:

I got to the last command in step #2 and it gave: 

```
william@emachine:~$ sudo apt-get dist-upgrade
[sudo] password for william: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xserver-xorg-video-intel: Depends: libdrm-intel1 (>= 2.4.9) but 2.4.5-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```

I restarted the computer and tried again, and I got the same thing.

What should I do?

same thing happened to me except with the 64bit versions

i noticed i got 404'd on a few of the files I was supposed to download

---

### Post by TheExplorer on 2009-05-06
[B][COLOR=Black]2 wyth:
[/COLOR][/B][COLOR=Black]
Thank you!
[/COLOR]

---

### Post by TheExplorer on 2009-05-06
There is only one issue that should be somehow fixed:
**There is no splash screen after these manipulations**.

It's not so critical for me but is there a way to get it back?

Thank you, guys.

---

### Post by colinpat on 2009-05-06
> **psyke83 said:**
> **Overview**
Some users are experiencing performance issues with Intel integrated graphics chips in Jaunty (9.04) for several possible reasons:

[LIST=A]
[*]The current driver in our repository has some performance issues with the EXA acceleration method. Users will notice 2D performance is poor due to the default "migration heuristic" employed by EXA (to "always" migrate pixmaps), but this causes performance issues for many users. Setting the heuristic to "greedy" alleviates this problem somewhat. See **"man exa"**.

[*]The new and faster acceleration method (UXA) is not enabled by default, due to issues reported by many users. This code is being actively developed, and many stability and performance issues have been resolved in the latest drivers (specifically within the intel driver, libdrm and the latest kernel 2.6.30-rc2). Unfortunately, Jaunty will not include the latest versions necessary to improve performance.

[*]3D performance has regressed compared to the Intrepid release, possibly due to major code changes that have resulted from the introduction to the new acceleration and memory management code (UXA, GEM, DRI2). Due to these changes, there seems to be some regressions in the "legacy" DRI acceleration. 

[*]Either Xorg or the "intel" driver seems to be suffering from a [bug]("https://bugs.launchpad.net/bugs/314928") in which the memory region allocated for the graphics card is not set up with the proper type of caching. This results in jerky video playback of almost any content (from 720p media, all the way down to simple 320x240 mpeg content), and a potential loss of performance for other 2D and 3D operations.
[/LIST]

**The solution**
It is possible to overcome all of these issues if you are willing to install some third-party packages. It is necessary to install kernel 2.6.30-rc2 (due to performance improvements in the drm/i915 kernel modules), and updated libdrm and xserver-xorg-video-intel packages to improve UXA and DRI2 performance. Finally, you need to manually fix the MTRR range of your graphics adapter (until it's fixed in the driver). 

If you're willing to test, the solution is documented below...

[COLOR="Red"]**Disclaimer:** This process is recommended only for users who feel comfortable working with the terminal. Since these packages have an unsupported status, do not file bugs on Launchpad unless you are using the official kernel and drivers from Jaunty.[/COLOR]

[LIST=1]
[*]Download & install the 2.6.30-rc2 kernel:

**i386 users:**
```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_i386.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_i386.deb http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_i386.deb
$ sudo dpkg -i linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb libdrm2_2.4.9-1_i386.deb libdrm-intel1_2.4.9-1_i386.deb xserver-xorg-video-intel_2.7.0-1_i386.deb
```
**amd64 users:**
```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_amd64.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_amd64.deb http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_amd64.deb libdrm-intel1_2.4.9-1_amd64.deb xserver-xorg-video-intel_2.7.0-1_amd64.deb
```

[*]Next you need to add the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa") in order to avail of updated graphics drivers.

Edit /etc/apt/sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```
Append the following text into the end of this file, then save and close:
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
```

Import the xorg-edgers key, update your apt sources, and perform an upgrade:
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 165d673674a995b3e64bf0cf4f191a5a8844c542
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```[COLOR="Blue"]**N.B.:** If you are asked to remove any packages, immediately cancel the process. The expected behaviour is only to upgrade packages, not to remove.[/COLOR]


[*]In this step you will edit your xorg.conf and enable UXA acceleration as well as some other configuration options that are important.

Edit your xorg.conf:
```
$ gksudo gedit /etc/X11/xorg.conf
```

Find the "Devices" section and make sure it looks identical to the following (remove or comment any of your previous customizations):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" **# may break 3D rendering if enabled**
EndSection
```[COLOR="Blue"]**N.B.:** The EXAOptimizeMigration and MigrationHeuristic options have no effect when using UXA acceleration. They will improve performance if you revert to EXA acceleration, however.[/COLOR]


[*]To fix the MTRR issue you will need two pieces of information - the address and size of your graphics adapter's *prefetchable* memory region.

Run the following command:
```
$ lspci -v
```
Find the section beginning with "VGA compatible controller" that lists your graphics adapter, and look for the "Memory at" entry that mentions *prefetchable* memory. Here's an example from my laptop:
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Dell Device 0164
	Flags: bus master, fast devsel, latency 0, IRQ 11
**	Memory at f0000000 (32-bit, prefetchable) [size=128M]**
	Memory at faf80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at c000 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb
```

Unfortunately, you need to convert the size from MB notation to hexadecimal notation. For your convenience, here is a conversion table:
```
512MB = 0x20000000
256MB = 0x10000000
128MB = 0x08000000
64MB  = 0x04000000
32MB  = 0x02000000
16MB  = 0x01000000
```

In the case of my laptop, therefore, the address is 0xF0000000 and the size is 0x08000000.


[*]Create a new file called fixmtrr.sh:
```
$ gksudo gedit /usr/local/bin/fixmtrr.sh
```

Paste:
```
echo "Before:"
echo "-------"
cat /proc/mtrr
echo "base=**<your base memory>** size=**<your memory size>** type=write-combining" >| /proc/mtrr

echo ""
echo "After:"
echo "------"
cat /proc/mtrr
```

Before saving, edit the parts in bold to reflect the memory address and size you discovered in the last step. In the example case of my laptop, that line would read:
```
echo "base=**0xF0000000** size=**0x08000000** type=write-combining" >| /proc/mtrr
```

Finally, make the script executable:
```
$ sudo chmod +x /usr/local/bin/fixmtrr.sh

```

[*]Reboot into the new 2.6.30-rc2 kernel. 

Providing that your system boots normally, execute the "fixmtrr.sh" script (it's necessary to fix upon each restart of X), and do some testing!
```
$ sudo fixmtrr.sh
```
[COLOR="Blue"]**N.B.:** Ensure the output of this script shows a write-combining entry for your graphics hardware in the "After" part.[/COLOR]


[*] (Optional). Enable "Tiling" in your xorg.conf (see Step 3), and re-test 3D rendering after restarting X.

Unfortunately, enabling tiling in the Intel driver breaks 3D rendering on my laptop (855GM), so I decided to disable tiling in the guide to ensure as many users as possible could get 3D working as soon as possible. I highly recommend you try to enable tiling, however, as it should improve performance (provided that it functions properly for your system).[/LIST]

**Interpreting performance gains**
Please don't trust the results of glxgears, for heaven's sake! For a long time the developers have asked users to stop interpreting performance from this program, but it's more important now than ever. I recommend you test PlanetPenguin Racer instead (it's not perfect, but it's a better real-world test).

For comparison's sake, here's a rough outline of my performance results on my Inspiron 510m laptop with a Pentium M 1.5Ghz, 768MB ram and Intel 855GM chipset:
**Intrepid:** glxgears = ~1000fps, ppracer = ~23fps.
**Jaunty (default configuration):** glxgears = ~300fps, ppracer = ~19fps
**Jaunty (with changes outlined here):** glxgears = ~340fps, ppracer = ~30fps

As you can see, glxgears does not accurately portray the improvement gained from testing the latest DRI2/UXA code.

**To revert settings:**
If this solution didn't work for you, this is how to revert changes.

[LIST=1]
[*]Edit your sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```

Remove the two xorg-edgers lines, then save and close.


[*]Downgrade packages:
```
$ sudo apt-get update
$ sudo apt-get install libdrm-dev/jaunty libdrm2/jaunty libdrm-intel1/jaunty xserver-xorg-video-intel/jaunty libdrm-nouveau1/jaunty libgl1-mesa-dri/jaunty libgl1-mesa-glx/jaunty libgl1-mesa-dev/jaunty libglu1-mesa/jaunty mesa-common-dev/jaunty mesa-utils/jaunty
```[COLOR="Blue"]**N.B.:** Ensure that packages are only downgraded, not removed. Otherwise cancel the process.[/COLOR]


[*]Remove the 2.6.30-rc2 kernel:
```
$ sudo dpkg -r linux-headers-2.6.30-020630rc2 linux-headers-2.6.30-020630rc2-generic linux-image-2.6.30-020630rc2-generic
```

[*]Reset your xorg.conf to defaults:
```
$ sudo dpkg-reconfigure xserver-xorg
```
[/LIST]
Your system will then be restored to normal.

Tried the above and it works after a fashiion.  I get lots of errors and messages during boot-up.  
Running in low-graphics mode
There already appears to be an X-server running on display:0  Should another display number be tried.  If I select yes more messages and eventually gets to the login screen.
Also get message, The greeter application appears to be crashing.
Any ideas as how I can fix these boot-up glitches??
Once running scrolling in the autocad program QCad works really well.  Before it was slow and jerky.
Thanks

---

### Post by wyth on 2009-05-06
> **TheExplorer said:**
> There is only one issue that should be somehow fixed:
**There is no splash screen after these manipulations**.

It's not so critical for me but is there a way to get it back?

Thank you, guys.

No, no splash screen with these testing kernels.  I'm not sure if it'll be there with the final release, but once the final release of 2.6.30 makes it into the regular repos, it'll be there.

---

### Post by relgames on 2009-05-06
Anyone?.. This is really annoying...
[http://ubuntuforums.org/showpost.php?p=7221046&postcount=299](http://ubuntuforums.org/showpost.php?p=7221046&postcount=299)

---

### Post by Sesivany on 2009-05-06
> **Uzi304 said:**
> Yeah that's exactly what I get. Anyone know of a fix for the suspend/wake up problem?

I'm experiencing it, too. Suspend doesn't work. Sometimes, it doesn't get sleep at all, sometimes I just get the login screen.

---

### Post by donpdonp on 2009-05-06
> **Sesivany said:**
> I'm experiencing it, too. Suspend doesn't work. Sometimes, it doesn't get sleep at all, sometimes I just get the login screen.

After doing the upgrade, i can sort of run WoW in WINE again. But now my laptop does not suspend! Its a lenovo R61

$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

If i close the lid, the moon icon blinks like its in the process of shutting down, but everything is still usable. after using it for a couple hours i do shutdown and during the shutdown process it goes to sleep.

then when it unsleeps it finished the shutdown process.

---

### Post by DarkAngel88 on 2009-05-06
> **Valir said:**
> Problems with FONTS?!? 

Hi, I applied the advice on my computer (ACER 4060, Intel 900), after experiencing jerky and jumpy playback on fullscreen mode for FLASH video. 

It worked like a charm. Until a couple of days later I started to notice some weird behaviour with my fonts. Sometimes the fonts in Firefox get garbled, sometimes not. Today my terminal has all the fonts strangely aligned. Could this be related to the fix? 

Anotherthing, why is it necessary to sudo fixntrr.sh everytime after startup to get the Flash in order?

best

Wow, thought I was the only one with this issue !!  I'm having issues also with the font display in firefox.  At first, it seems like all instance of a given letter (w for example) is mixed up and then, more and more letters gets weird.  Only fix is to restart firefox or restart the computer.  Also, I'm one of those who can't put their computer to sleep too.  Hope there will be a fix soon !

---

### Post by scarf on 2009-05-06
i have the Intel Corporation 82852/82855 GM/GME/PM/GMV, and i have simply downgraded to the older 2.4 version of drivers, with xserver-xorg-video-intel-2.4 package.

however, the video still isn't performing well.  for example, if i open a man page in the terminal and then scroll through it with up and down arrows, the text moves slowly and my CPU usage goes way up... lol, such a simple task.

also, sometimes when i am typing and i want to delete a bunch of text, i will hold down the backspace and the text is deleted slower than normal.  when i let go of backspace, the text continues to be deleted for a while.

---

### Post by Don1500 on 2009-05-06
Link bump

---

### Post by needhelp123 on 2009-05-06
> **needhelp123 said:**
> After I rebooted I get the following message:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init
No init found. Try passing init = bootarg

Any help is appreciated.

Thanks.

Hello? Anyone?

Edit: Never mind, I got it solved by upgrading to rc4, it's a problem with rc2.

---

### Post by wirechief on 2009-05-06
After a very long time my machine a R61e suffered a "freeze" 
Linux wirechief-laptop 2.6.30-020630rc2-generic #020630rc2 SMP Wed Apr 15 13:20:18 UTC 2009 x86_64 GNU/Linux
dpkg -l |grep xserver-xorg-video-intel
ii  xserver-xorg-video-intel                   2:2.7.99.1+git20090505.r1.a8a771a8-0ubuntu0sarvatt         X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-intel-dbg               2:2.7.99.1+git20090505.r1.a8a771a8-0ubuntu0sarvatt         X.Org X server -- Intel i8xx, i9xx display d
I was not doing any 3d however i did click this url [www.woodtv.com](www.woodtv.com)
and it immediately froze. I ssh'd into the sick machine and did some xswat
testing with the following reports (attached)
my xorg.conf...
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        Virtual 2048 2048
EndSection


Section "Device"

	Identifier	"Onboard Intel Video"
	#Option "AccelMethod" "exa"
	#Option "monitor-VGA" "ExternalVGA"
	#Option "monitor-LVDS" "OnboardLVDS"
	#Option "EXAOptimizeMigration" "true"
	#Option "MigrationHeuristic" "greedy"
	#Option "AccelMethod" "uxa"
        #Option	"Tiling"  "false" # may break 3D rendering if enabled
         VideoRam 261120
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection


another report of this same website [www.woodtv.com](www.woodtv.com) crashing as mine did... [https://bugs.freedesktop.org/show_bug.cgi?id=21512](https://bugs.freedesktop.org/show_bug.cgi?id=21512)

---

### Post by Uzi304 on 2009-05-06
Edit: nevermind

---

### Post by markbl on 2009-05-06
> **DarkAngel88 said:**
> Wow, thought I was the only one with this issue !!  I'm having issues also with the font display in firefox.
I've applied the fix exactly as described in the first post here and I have also seen this font corruption problem. I've seen it in gnome-terminal. The bottom line (i.e. the prompt line) gets corrupted. It seems to occur after the machine has been running for many hours.

---

### Post by nnutter on 2009-05-07
I just wanted to share what I did, which is a tad bit different from what was recommended. Unfortunately, I did not have the patience to read 30+ pages on the topic so somebody else may have already point this out.

The two main differences from the OP is that I used X Updates instead of X Edgers and I put the MTRR fix into GDM's PreSession.

To find out the details visit my post on the topic. Thanks to the OP for providing such great information.

[http://nnutter.com/2009/05/fix-poor-intel-graphics-performance-on-jaunty/](http://nnutter.com/2009/05/fix-poor-intel-graphics-performance-on-jaunty/)

---

### Post by b-boy on 2009-05-07
Hi 

I have the intel GM965/GL960 graphics card and since I upgraded from 8.04 to 9.04 my graphics were really bad and was very unstable, small things like maximizing and minimizing a window was a problem. BUT after following this fix tutorial everything is working just as well or even better that 8.04 

Thanks psyke83 this was really helpfull

---

### Post by cyricc on 2009-05-07
I took the steps in this guide and it totally fixed my sluggish graphics issues in Jaunty, which was great. However, kernel 2.6.30rc2 appears to break acpi-cpufreq (controls cpu scaling) which results in overheating issues with my laptop. (I have a C2D T8300 and GM965 graphics)

With kernel 2.6.30rc2 the cpu seems to ignore the scaling driver and always runs at the highest available frequency. Any changes to scaling through /sys/devices/system/cpu/cpu0/cpufreq appear to be ignored, as cpuinfo_cur_freq does not match scaling_cur_freq as it should. To confirm this I ran a benchmark setting scaling at fixed 800MHz and one setting at 2.4GHz. Both benchmarks returned more or less equal (+/- 1%), which clearly indicates that the scaling driver is not working as it should.

This problem is not present running with vanilla kernel 2.6.28-11-generic on the same computer. My THRM temperatures on 2.6.30 can run up to 20C hotter than 2.6.28 under similar conditions.

Anyway, just a warning to anyone who is using this fix, it might be damaging your laptop. I've reverted back to slow 2.6.28 for now.

---

### Post by mag1 on 2009-05-07
Im using an nc10 netbook and just want to get vsync working for now with videos as the tearing is bad, i really don't want to mess with the system too much so i was wondering if there's any way to get a simple fix working for now without resorting to major changes?

Also any idea if or when there will be an official fix?

Thanks!

---

### Post by Alloc on 2009-05-07
Hi,

> **nnutter said:**
> To find out the details visit my post on the topic. Thanks to the OP for providing such great information.[http://nnutter.com/2009/05/fix-poor-intel-graphics-performance-on-jaunty/](http://nnutter.com/2009/05/fix-poor-intel-graphics-performance-on-jaunty/)
I followed those instructions and they were at least really improving ETuxRacer's performance. Can't tell about anything else yet cause I already updated the graphics-drivers from ubuntu-x-swat-repository a while ago.

One step I had to take in order to boot my machine into kernel 2.6.30 though:
I've got my harddisk completely **encrypted** with dm-crypt and it normally asks for the passphrase on the splashscreen. Since the splashscreen isn't shown with kernel 2.6.30 I had to disable it to be able to enter my password and continue booting.

Everything else seems to be fine so far.

Thanks to everyone who's trying to figure out how to get the best performance and stability out of the Intel chips :)

Regards,
Chris

---

### Post by djuliette on 2009-05-07
I got my graphics running pretty well using this guide. I upgraded the kernel to 2.6.30-rc4. But now Ubuntu's update manager wants to install kernel 2.6.28-12.  Is there a way to configure the update manager to ignore kernel updates (but also keep other important updates)?

---

### Post by relgames on 2009-05-07
> **relgames said:**
> Anyone?.. This is really annoying...
[http://ubuntuforums.org/showpost.php?p=7221046&postcount=299](http://ubuntuforums.org/showpost.php?p=7221046&postcount=299)
No answers... I can't work, it's really slow. 
And it seems as "stand by" mode is broken.
I'm reverting back to the old drivers, and, probably, to the version 8.10.

p.s.
I moved from Windows to Ubuntu 8.10 in Feb, and I felt comfortable with it.
But right now I'm more and more thinking about moving back to Windows. I just want to work on my laptop, not to doing hacks with drivers/XOrg/mtrr/etc.
Also I do not recommend Ubuntu to my friends anymore.
And I think, I'm not alone. And it's very sadly.

---

### Post by terrax on 2009-05-07
> **relgames said:**
> No answers... I can't work, it's really slow. 
And it seems as "stand by" mode is broken.
I'm reverting back to the old drivers, and, probably, to the version 8.10.

p.s.
I moved from Windows to Ubuntu 8.10 in Feb, and I felt comfortable with it.
But right now I'm more and more thinking about moving back to Windows. I just want to work on my laptop, not to doing hacks with drivers/XOrg/mtrr/etc.
Also I do not recommend Ubuntu to my friends anymore.
And I think, I'm not alone. And it's very sadly.

Hmm any reason why you can't use Intrepid if that run well? You are not alone, trust me :-)

---

### Post by blindside on 2009-05-07
Kinda new to linux here. I was kinda disappointed in how my laptop was running. Firefox would not scroll right among other issues. I followed this guide and everything is running perfect and my  jaunty is a whole different OS now. Thanks man.

---

### Post by Eberhard on 2009-05-07
This Howto gave me greatly improved performance but when shutting down the computer i get a loud "beep", like an alarm - very annoying. I decided to change back to the old version using the instructions in the first post but the "beep" is still there. Any suggestions?

---

### Post by stewacide on 2009-05-07
> **djuliette said:**
> I got my graphics running pretty well using this guide. I upgraded the kernel to 2.6.30-rc4. But now Ubuntu's update manager wants to install kernel 2.6.28-12.  Is there a way to configure the update manager to ignore kernel updates (but also keep other important updates)?

You can let it install ..28-12 or not, won't affect anything if you're booting into ..30rc4

---

### Post by stewacide on 2009-05-07
> **Eberhard said:**
> This Howto gave me greatly improved performance but when shutting down the computer i get a loud "beep", like an alarm - very annoying. I decided to change back to the old version using the instructions in the first post but the "beep" is still there. Any suggestions?

I'm getting the same thing (w/ a Dell desktop), I'm just ignoring it (how often do you re-start your computer that it's a problem?)

---

### Post by relgames on 2009-05-07
> **terrax said:**
> Hmm any reason why you can't use Intrepid if that run well? 
I do like new Gnome from 9.04 :-)

BTW, now I'm just realized that my /proc/mtrr already contains a line for the video memory, but with "uncachable" option.

reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
[B]reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
[/B]reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

Maybe I need to somehow erase that line before running fixmtrr.sh??

Also, there are strange messages from logs:
/var/log/syslog.0:May  7 01:33:07 rg-work kernel: [   14.320969] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
/var/log/syslog.0:May  7 01:33:07 rg-work kernel: [   14.320971] [drm] MTRR allocation failed.  Graphics performance may suffer.

---

### Post by djuliette on 2009-05-07
> **stewacide said:**
> You can let it install ..28-12 or not, won't affect anything if you're booting into ..30rc4

Oh yea. I should have realized that. I was just a bit freaked out, I just got the video working perfectly and am afraid of screwing it up again.

---

### Post by mpicker21 on 2009-05-07
Has anyone that has done this with RC4 found that it doesn't have the power management issues that can cause the overheating?  I'd love to do this but that would be a stopper for me.

---

### Post by NJC on 2009-05-08
post deleted

---

### Post by Arup on 2009-05-08
G31 works well with uxa enabled using the default Jaunty xorg. The one from ppa, even the stable one crashes it.

---

### Post by oOarthurOo on 2009-05-08
If you're gettting the 404 errors during download you've got to change those files to -2 from -1.
```

wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-2_i386.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-2_i386.deb http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_i386.deb
sudo dpkg -i linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb libdrm2_2.4.9-2_i386.deb libdrm-intel1_2.4.9-2_i386.deb xserver-xorg-video-intel_2.7.0-1_i386.deb
```

---

### Post by NJC on 2009-05-08
> **Arup said:**
> G31 works well with uxa enabled using the default Jaunty xorg. 
Depends on what you mean by "works well". I added this to xorg.conf:
```
Option        "AccelMethod"            "uxa"
```Glxgears now went from 1600fps to 700fps. A quick TG Motocross (online flash game) test rendered identical unstable and slow performance as before the xorg.conf "Uxa" mod.

---

### Post by psyke83 on 2009-05-08
> **NJC said:**
> Depends on what you mean by "works well". I added this to xorg.conf:
```
Option        "AccelMethod"            "uxa"
```Glxgears now went from 1600fps to 700fps. A quick TG Motocross (online flash game) test rendered identical unstable and slow performance as before the xorg.conf "Uxa" mod.

If you read the guide properly, you'd know that glxgears is not a benchmark. The numbers it produces do not benchmark 3D in any meaningful way.

The difference between "EXA" and "UXA" acceleration methods are major, because if you enable UXA, the new DRI2 rendering framework is used. Although glxgears seems "slower", real 3D applications should be faster (if UXA & DRI2 work correctly on your chipset at this time).

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

You do realize that compiz will cause increased CPU usage with Adobe Flash? Although Flash can support hardware rendering, it's explicitly disabled when any composite manager (e.g. compiz) is detected. If your MTRR ranges aren't fixed properly (with or without the newer drivers/configuration), you're always going to experience slowdowns and stuttering in video-intensive applications.

---

### Post by Arup on 2009-05-08
> **psyke83 said:**
> Don't trust glxgears, blank it from your mind and never think of it again. The numbers it produces do not benchmark 3D in any meaningful way. 

The difference between "EXA" and "UXA" is major - enabling UXA activates the new DRI2 rendering framework. Although glxgears seems "slower", real 3D applications should be faster (if UXA & DRI2 work correctly on your chipset at this time).

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

Very true, without uxa the Intel G31 PC wouldn't run Google Earth but with uxa, it runs GE even with Compiz enabled. glxgears is not at all the method of choice when it comes to benchmarking 3D performance. gtkperf which is in the repos is a far better method which gives detailed description.

---

### Post by NJC on 2009-05-08
> **psyke83 said:**
> If you read the guide properly, you'd know that glxgears is not a benchmark. The numbers it produces do not benchmark 3D in any meaningful way.

Thank-you for that encouragement. I read the same thing tonight and will be happy to banish it. :)

> **psyke83 said:**
> 
The difference between "EXA" and "UXA" acceleration methods are major, because if you enable UXA, the new DRI2 rendering framework is used. Although glxgears seems "slower", real 3D applications should be faster (if UXA & DRI2 work correctly on your chipset at this time).

I'm going to assume uxa and dr12 don't work correctly with the G31, as per my above post. Flash games were still unusable using uxa.

EDIT: EXA is not enabled by default either in xorg.conf.

---

### Post by Arup on 2009-05-08
> **NJC said:**
> Thank-you for that encouragement. I read the same thing tonight and will be happy to banish it. :)


I'm going to assume uxa and dr12 don't work correctly with the G31, as per my above post. Flash games were still unusable using uxa.

EDIT: EXA is not enabled by default either in xorg.conf.

Try reverting back to the original kernel which came with Jaunty and also the original xorg. Then enable uxa and see if you have any issues.

---

### Post by NJC on 2009-05-08
> **Arup said:**
> Try reverting back to the original kernel which came with Jaunty and also the original xorg. Then enable uxa and see if you have any issues.

I *only* tried to change xorg.conf to uxa/exa, as per Ubuntu.com instructions so am still running 2.6.28 - 11. I suspect my initial post was not useful in this thread - apologies. I really needed to test UXA in conjunction with the newer kernel in order to give accurate results.

---

### Post by Arup on 2009-05-08
> **NJC said:**
> I *only* tried to change xorg.conf to uxa/exa, as per Ubuntu.com instructions so am still running 2.6.28 - 11. I suspect my initial post was not useful in this thread - apologies. I really needed to test UXA in conjunction with the newer kernel in order to give accurate results.

So I assume your drivers were original and not from the ppa? In that case I am a bit surprised as the G31 truly runs good unlike the other chipset with the original setup using the included xorg and kernel, all it needs is uxa enabled.

---

### Post by NJC on 2009-05-08
I again added the UXA in xorg.conf. Everything runs fine, except online flash games are still intermittently slow - but that could be another issue. EDIT - yes, all original drivers and not from ppa.

---

### Post by Arup on 2009-05-08
> **NJC said:**
> I again added the UXA in xorg.conf. Everything runs fine, except online flash games are still intermittently slow - but that could be another issue. EDIT - yes, all original drivers and not from ppa.

If I am not mistaken, most online games need Shockwave and that is yet to be implemented in Linux.

---

### Post by cankoy on 2009-05-08
Hello,
I'm not interested in 3D, I don't use compiz et al. I just want good 2D, and get rid of the randomly flickering display problem. But, I cannot use 30-rc kernels because I need Vmware. I tried standard Jaunty packages and x-swat updates for xserver-xorg-intel et al., I also applied the mtrr fix, but I still suffer display flickering (965gm).
Is there a way to get rid of it w/o reverting to 30-rc kernel?

---

### Post by Arup on 2009-05-08
> **cankoy said:**
> Hello,
I'm not interested in 3D, I don't use compiz et al. I just want good 2D, and get rid of the randomly flickering display problem. But, I cannot use 30-rc kernels because I need Vmware. I tried standard Jaunty packages and x-swat updates for xserver-xorg-intel et al., I also applied the mtrr fix, but I still suffer display flickering (965gm).
Is there a way to get rid of it w/o reverting to 30-rc kernel?


Turn off effects in appearance and enable metacity composting via gnome-conf and see if that works out for you.

---

### Post by cankoy on 2009-05-08
> **Arup said:**
> [quote=cankoy;7237479]Hello,
I'm not interested in 3D, I don't use compiz et al. I just want good 2D, and get rid of the randomly flickering display problem. But, I cannot use 30-rc kernels because I need Vmware. I tried standard Jaunty packages and x-swat updates for xserver-xorg-intel et al., I also applied the mtrr fix, but I still suffer display flickering (965gm).
Is there a way to get rid of it w/o reverting to 30-rc kernel?
Turn off effects in appearance and enable metacity composting via gnome-conf and see if that works out for you.[/quote]
hi there,
I appreciate you trying to help, but your response is nothing but some random musing in this context.

---

### Post by Arup on 2009-05-08
> **cankoy said:**
> hi there,
I appreciate you trying to help, but your response is nothing but some random musing in this context.

Sorry if my input seems like random musing. Thats how its done I am afraid, one step at a time, sometimes its complex and sometimes its as simple as one setting. The fact that just putting uxa solves myriads of issues in the Intel cards goes to show how it is. Anyways, good luck with your quest.

---

### Post by Kerubu on 2009-05-08
I tried this fix using the rc2 kernel and having to use -2 versions for some of the packages. While it fixed the the brightness control problems I was having it resulted in a non-functioning wireless card. this forced me to return to the stable Jaunty release using the instructions you gave to undo the fix.

Until a 'simpleton-user' fix is available I'll have to put up with the brightness bug.

---

### Post by zevans on 2009-05-08
> **Kerubu said:**
> I tried this fix using the rc2 kernel and having to use -2 versions for some of the packages. While it fixed the the brightness control problems I was having it resulted in a non-functioning wireless card. this forced me to return to the stable Jaunty release using the instructions you gave to undo the fix.

Until a 'simpleton-user' fix is available I'll have to put up with the brightness bug.

RC2 definitely has some weirdness in it. RC4 seems much better for me.

There will be a .28 kernel out soon with the fix for MTRR built in properly - and then we'll be able to use that from jaunty-proposed and/or jaunty-updates instead of the fixmtrr.sh.

---

### Post by jon.reeve on 2009-05-08
The new kernel and drivers work great, and they more than tripled my graphics output. Only thing is, this broke my wifi, and I got a "fatal" error about modprobe on startup, so I had to revert to my old kernel. :(

---

### Post by Depressed Man on 2009-05-08
Haha was trying to see if I could use dual monitors, messed up my xorg.conf so badly that I couldn't even return it to install performance (couldn't even enable slow Compiz). So I was about to wipe it and redo everything till I tried this. Everything is up to speed now except my webcam no longer works since there isn't a driver for this kernal yet (works normally in Jaunty). But I'll take fast speed performance over a webcam.

Edit: Hmm it seems to defautly boot up without Compiz. So I have to manually put it into Compiz with compiz --replace but then the notification icon for notificaitons doesn't come up (no big deal though).

---

### Post by mpicker21 on 2009-05-09
I just wanted to give my experience input.  Following the instructions on the front page worked well for me.  I changed it up a bit by installing the most current packages of those listed but I haven't noticed any problems.  I was mostly concerned about full screen flash performance and from the tests I've run it all seems to be fine.  I had to install my wireless drivers manually which I made harder than it was.  Turns out that you can use the b43 driver in the 2.6.30 instead of having to use the restricted-modules driver.  The only issue was getting the firmware but a simple search on the forums solved this.  Thanks for the great fix.  It's sad that this has to be such an issue.  I hesitate to recommend Jaunty to people who are new to linux for fear they might be turned off by it.

---

### Post by LifeTheHound on 2009-05-09
> 1. Download & install the 2.6.30-rc2 kernel:
No. Because the modules in this non-ubuntu kernel are not the same as in stock 2.6.28, I lost wifi stability, all SD card support, and more quirks appeared.

Don't use pre-release software, especially if it's as important as the kernel, especially if it's not designed for your distro, ESPECIALLY since there are often deleterious side effects. 
Just don't do it. There are other ways.

---

### Post by ZeroColds on 2009-05-09
I have some problems with this fix. I install new kernel 2.6.30-020630rc4 and rc2 i didn't find any difirence betwen them. And i have 950(945)gma
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 10ad
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 10ad
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb
```
 my performance grue up. but in Rune (the game) performance is too hight, i can feel thet i am neo not a wiking so it`s unplayeble And the settings set to 50% of game speed..., tux racer works nears 25-30 fps, and armagetron works around 45-70 fps.  2d games works perfect. But google earth works extrimli slow on both kernels. What is the mater with my card?

---

### Post by btermeli on 2009-05-09
Hey guys,

I have a fresh 9.04 install but graphic performance is not like 8.04.
Is it helpful for Intel 915???

Thanx.

---

### Post by psyke83 on 2009-05-09
> **LifeTheHound said:**
> No. Because the modules in this non-ubuntu kernel are not the same as in stock 2.6.28, I lost wifi stability, all SD card support, and more quirks appeared.

Don't use pre-release software, especially if it's as important as the kernel, especially if it's not designed for your distro, ESPECIALLY since there are often deleterious side effects. 
Just don't do it. There are other ways.

Too true. I'm going to revise and compartmentalize the guide, offering upgrade paths based on the needs of the users. In my case, for example, I can use the mainline testing kernels on my laptop without sacrificing any functionality, as I don't depend on any restricted/non-free drivers. That doesn't mean it's ideal for everyone, though.

---

### Post by fondle-em on 2009-05-09
> **mpicker21 said:**
> It's sad that this has to be such an issue.  I hesitate to recommend Jaunty to people who are new to linux for fear they might be turned off by it.

This statement cannot possibly be repeated often enough.

---

### Post by LifeTheHound on 2009-05-09
> **fondle-em said:**
> This statement cannot possibly be repeated often enough.


Amen to that. :(

---

### Post by mbay2002 on 2009-05-09
This got compiz going for me with my card [Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)] on a Dell Latitude D610.   FINALLY.  It's a shame this doesn't work with the default driver in the Jaunty repository.  

A few notes: 
(1) the "wget" in the post #1 needs to be updated to reflect that the intel libdrm stuff is (as of this writing) at 2.4.9-2 (not 2.4.9-1);
(2) setting my xorg.conf as described actually slowed things down, I ended up leaving xorg.conf untouched (glxgears went from over 600 fps down to 300 fps when I made the xorg.conf changes)
(3) As described in post #199 of the this thread, with the test kernel, restricted modules are not included, so "apparmor" fails to load, and the boot splash disappears.  I did an "apt-get remove apparmor --purge" to get rid of the message, this is fine with me now that compiz is going.

---

### Post by wirechief on 2009-05-09
using the xserver-xorg-video-intel from
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

seems my freeze issue has gotten resolved with the installation of
ii  xserver-xorg-video-intel                   2:2.7.0-1ubuntu2~xup~1
as a curious note the glxgears jumped from around 500 to 1200, my penquin racer seems a bit faster with speeds of 85
on the downhill.
exa seems to now be included..
grep exa /var/log/Xorg.0.log
(**) intel(0): Option "AccelMethod" "exa"
(II) intel(0): Using exact sizes for initial modes
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
(II) intel(0): 0x0ed40000-0x0fffffff: exa offscreen (19200 kB)

Linux wirechief-laptop 2.6.30-020630rc4-generic #020630rc4 SMP Fri May 1
08:25:59 UTC 2009 x86_64 GNU/Linux

---

### Post by Daniel15 on 2009-05-10
> **btermeli said:**
> Hey guys,

I have a fresh 9.04 install but graphic performance is not like 8.04.
Is it helpful for Intel 915???

Thanx.

This is for all Intel graphics chips, so yes, I assume it'd be helpful for you.

This is a terrible issue to see in a release, seeing as how widespread Intel graphics chips are. :(

---

### Post by Arup on 2009-05-10
For older Intel chips apart from the G series its better to use the 2.4 driver from Heron 8.04. Lots of people are having success with it. Jaunty uses the newer kernel which implements GEM and UXA, when they work like in case of chipsets like G31 and other newer ones work out quite well with uxa enabled in xorg, others have severe issues like lockup, flaky video and flash etc. In my testing, without uxa, Google Earth refused to run flickering around in the G31 chipset motherboard, just enabling uxa sent away all the gremlins except for one or two occasional lock ups.

---

### Post by alex.rayu on 2009-05-10
Do things actually get BETTER with a new release?
What a shame. I used to have ati - I bout intel cause ati would never perform right, And lo.

---

### Post by Arup on 2009-05-10
Everything runs fine on my system, far more improved than Hardy and Intrepid, ext4 rocks, boot time is faster, apps load fast, compiling is a breeze, there is always improvement in Ubuntu but sometimes it also comes at a cost.

---

### Post by cankoy on 2009-05-10
All this has become a tragicomedy.
I urged several colleagues to purchase Intel-based notebooks and install Ubuntu so they get better Linux experience, now they not only hate Linux but hate me as well.
I used to think Canonical refrained from exploiting users as **lab rats in testing** like Red Hat/Novell does with Fedora/OpenSuse, but after 3 releases in a row I've concluded I was wrong.
I'd better jump ship and leave the fun to you Ubuntlings. 
Enjoy the vaporware, and come visit here often in whining so that the bogus big community remains vivid.

*To the mod:* yes, I know nobody wants the awful truth, you can remove this post now.

---

### Post by Arup on 2009-05-10
Why dont' you go rant at the Intel fools for doing this instead of blaming Ubuntu solely? I guess Ubuntu and Intel shouldn't make any efforts for improvement, the GEM and uxa is a huge step in right direction and with some patience, IGP would be giving value added performane when all the bugs get ironed out. Said and done my IGP G31 chipset laptop runs fine with uxa enabled, no issues at all so all is not lost and things look bright. I am sure Ubuntu staff is hard at work and very soon the solution will come out. Meanwhile for older 9xx and 8xx Intel chipset, its better to use Hardy Heron for now.

As I mentioned above, majority of the IGP chipset latops can't run on native resolution using Intel drivers in Windows XP and Vista due to a faulty EDID issue, all of them have to manually hack the driver to make it run. Looks like something going seriously wrong in Intel vid department, if you wish to buy a laptop, buying one with nvidia chipset is your best bet.

---

### Post by galv on 2009-05-10
> **Arup said:**
> (...) Looks like something going seriously wrong in Intel vid department, if you wish to buy a laptop, buying one with nvidia chipset is your best bet.
That's not really an option if you're talking about netbooks.

One thing that I love in Debian is "release when ready", I think that *fixed* 6 months cycles are too short and you'll always release with issues like this, or releasing beta version of Firefox or not including OpenOffice3, or a faulty PulseAudio config, etc. If the schedule was a bit more flexible this would not happen.

Sorry for the off-Topic.

---

### Post by Arup on 2009-05-10
> **galv said:**
> That's not really an option if you're talking about netbooks.

One thing that I love in Debian is "release when ready", I think that *fixed* 6 months cycles are too short and you'll always release with issues like this, or releasing beta version of Firefox or not including OpenOffice3, or a faulty PulseAudio config, etc. If the schedule was a bit more flexible this would not happen.

Sorry for the off-Topic.

You have tried and trusty Hardy in case you wish to go the Debian way. Netbooks I do agree depend on IGP.

---

### Post by SteveMcQwark on 2009-05-10
> **ZeroColds said:**
> I have some problems with this fix. I install new kernel 2.6.30-020630rc4 and rc2 i didn't find any difirence betwen them. And i have 950(945)gma
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 10ad
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 10ad
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb
```
 my performance grue up. but in Rune (the game) performance is too hight, i can feel thet i am neo not a wiking so it`s unplayeble And the settings set to 50% of game speed..., tux racer works nears 25-30 fps, and armagetron works around 45-70 fps.  2d games works perfect. But google earth works extrimli slow on both kernels. What is the mater with my card?

Well, I found Google Earth is unbearable on bootup, but if you switch to Mars and back, then it runs better than I've ever had it work in Ubuntu.

---

### Post by jongkind on 2009-05-10
> **SteveMcQwark said:**
> Well, I found Google Earth is unbearable on bootup, but if you switch to Mars and back, then it runs better than I've ever had it work in Ubuntu.

Wow, I can confirm this!

My Kernel is 2.6.28-11-generic
Intel Corporation Mobile 945GM/GMS Express Integrated Graphics Controller
2:2.7.0-1ubuntu2~xup~1 driver

---

### Post by jooby on 2009-05-10
I made these changes and the video performance did improve.  But does anyone know if this issue will be fixed with update manager automatically when the fixes become available or do I have to revert back before any fixes that come out will be applied?

---

### Post by stewacide on 2009-05-10
> **galv said:**
> That's not really an option if you're talking about netbooks.

One thing that I love in Debian is "release when ready", I think that *fixed* 6 months cycles are too short and you'll always release with issues like this, or releasing beta version of Firefox or not including OpenOffice3, or a faulty PulseAudio config, etc. If the schedule was a bit more flexible this would not happen.

Sorry for the off-Topic.

Agree completely. 6 months is unnecessarily short, and fixed release dates are asking for trouble.

---

### Post by JoeJoeMa on 2009-05-10
not only did the fix not fix the laptop (probably my fault). It "fixed" my wireless, as in, fixed it to not "work" anymore.

---

### Post by galv on 2009-05-10
> **JoeJoeMa said:**
> not only did the fix not fix the laptop (probably my fault). It "fixed" my wireless, as in, fixed it to not "work" anymore.

Have you tried using the previous kernel?

---

### Post by shahin_gh on 2009-05-10
This fixed did improve graphics performance on my EEE PC 901. Most things run smooth now, unfortunately Firefox 3 scrolling performance on certain pages is atrocious compared to 8.10. For instance, the website [www.prisjakt.se](www.prisjakt.se) scrolls terribly slow compared to 8.10.

This doesn't seem to affect Opera. It would be interesting to know what causes this issue. I would guess that Firefox and Opera use different methods of redrawing the page and whatever method Firefox uses is poorly optimized in the 9.04 intel xorg driver.

---

### Post by PatrickVogeli on 2009-05-10
for me performance is alright.. the only thing non-stock I have is a custom compiled 2.6.29.3 kernel and the following configuration in xorg.conf:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"intel"
	Option 		"FramebufferCompression" "on"
	Option 		"AccelMethod" 		 "EXA"
	Option 		"Tiling" 		 "on"
EndSection

```

With the following I get about 900fps in glxgears.

Scrolling and such is usually just fine.

---

### Post by era506 on 2009-05-10
Wow!! Compiz is so fast after applying this fix!!! Thanks!! I have an Intel GM965 and I have enabled Tiling with no problems with 3D. Just have a little problem... If I enable "Opacity, Brightness and Saturation" on CompizConfig my panel and menus look like the screenshot, but with that plugin disabled when I open any menu it look transparent (like screenshot) but for like half second or so and then it gets back to normal. I hope someone has a solution or explanation for this. Thanks in advance!

[[IMG]http://img228.imageshack.us/img228/9396/screenshot2k.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshot2k.png)

PS: Oh! I almost forgot, is there any way to execute the "fixmttr.sh" script at startup? I think that it will not work if I add it to "Startup Programs" on Preferences menu, right? I'm sure that I will forget to execute it sometimes....

---

### Post by jsegel on 2009-05-11
bummed. none of these solutions work for me - old laptop, pentium 3 with intel i810.
just getting black and grey bars and lines with the intel driver. black screen with vesa.

---

### Post by scarf on 2009-05-11
> **shahin_gh said:**
> This fixed did improve graphics performance on my EEE PC 901. Most things run smooth now, unfortunately Firefox 3 scrolling performance on certain pages is atrocious compared to 8.10. For instance, the website [www.prisjakt.se](www.prisjakt.se) scrolls terribly slow compared to 8.10.

This doesn't seem to affect Opera. It would be interesting to know what causes this issue. I would guess that Firefox and Opera use different methods of redrawing the page and whatever method Firefox uses is poorly optimized in the 9.04 intel xorg driver.

i must say that the performance here still blows with my 82852/82855 GM/GME/PM/GMV after installing the 2.4 drivers.  i had initially thought that the performance was better, and it may have been compared to the stock jaunty configuration, but it still blows compared to what i remember in intrepid.

firefox scrolling is definitely atrocious.  when i scroll up or down the page continues to scroll even though i have stopped scrolling.  i haven't tried opera and won't ;)

also keyboard repeating has a similar problem.  i will hold down a key to repeat it, and it will continue to be repeated long after i have released the key.

---

### Post by relgames on 2009-05-11
> **relgames said:**
> I do like new Gnome from 9.04 :-)

BTW, now I'm just realized that my /proc/mtrr already contains a line for the video memory, but with "uncachable" option.

reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
[B]reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
[/B]reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

Maybe I need to somehow erase that line before running fixmtrr.sh??

Also, there are strange messages from logs:
/var/log/syslog.0:May  7 01:33:07 rg-work kernel: [   14.320969] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
/var/log/syslog.0:May  7 01:33:07 rg-work kernel: [   14.320971] [drm] MTRR allocation failed.  Graphics performance may suffer.
Guys, did I write something wrong? Do I need to provide some more information/logs/etc?

Why nobody can help me? Is there a some other forum where I can receive help?

---

### Post by udippel on 2009-05-11
If nobody has noted this in this looong thread, at least here and on mplayer, I found that it helps to play audio through anything but pulseaudio (e.g. "mplayer myfile.avi -ao oss).

---

### Post by Quirinius on 2009-05-11
> **psyke83 said:**
> By the way, I normally get angry at compiz due to slow scrolling, but I actually find it bearable right now ;). Scrolling is smooth on my old laptop (with exception to certain sites in Firefox, such as Gmail - but is the fault of Firefox and not compiz or Xorg).

Try do disable smooth scrolling in Firefox, that did the trick with me.

---

### Post by Yako on 2009-05-11
Works for me... I went from about 200fps to 1000fps in glxgears. Planet Penguin Racer runs a lot smoother as well.
Not all packages mentioned in the HOWTO are still available though, the DRM packages have new versions and need to be manually downloaded and installed seperately.

---

### Post by ZeroColds on 2009-05-11
I found another one problem in this fix, low torrent speed on this kernel. On default kerenel a have full speed of my cannel (2Mb/s) and on the 2.6.30-020630rc4-generic and rc2 i have only 200kb/s. And so the question is how to get rivers from stock kernel to new kernel? And on rc5 speed better but not as on original kernel.
2 **SteveMcQwark**
Thankyou i found my problem it was atmosfere.

---

### Post by paulmerchant on 2009-05-11
> **Yako said:**
> Works for me... I went from about 200fps to 1000fps in glxgears. Planet Penguin Racer runs a lot smoother as well.
Not all packages mentioned in the HOWTO are still available though, the DRM packages have new versions and need to be manually downloaded and installed seperately.

Thanks for pointing out that some of the packages have changed. I tried this HOWTO over the weekend without good results. A lot of things were broken.

I tried it again today and watched the errors. Then I manually downloaded and installed the packages in the HOWTO that have been upgraded: at the time of this writing, you have to change all instances of libdrm2_2.4.9-1_i386.deb and libdrm-intel1_2.4.9-1_i386.deb to libdrm2_2.4.9-2_i386.deb and libdrm-intel1_2.4.9-2_i386.deb respectively.

Now everything is working great. In fact, I've never seen this laptop with integrated Intel 945 perform this well, ever. Compiz is faster than I've ever seen it and things like Blender and 3D games, which now work with Compiz running, are doing well.

---

### Post by psyke83 on 2009-05-11
> **paulmerchant said:**
> Thanks for pointing out that some of the packages have changed. I tried this HOWTO over the weekend without good results. A lot of things were broken.

I tried it again today and watched the errors. Then I manually downloaded and installed the packages in the HOWTO that have been upgraded: at the time of this writing, you have to change all instances of libdrm2_2.4.9-1_i386.deb and libdrm-intel1_2.4.9-1_i386.deb to libdrm2_2.4.9-2_i386.deb and libdrm-intel1_2.4.9-2_i386.deb respectively.

Now everything is working great. In fact, I've never seen this laptop with integrated Intel 945 perform this well, ever. Compiz is faster than I've ever seen it and things like Blender and 3D games, which now work with Compiz running, are doing well.

My apologies for this, but it wasn't necessary to install packages from Debian's archive - it was based on the original version of this guide and I thought that I had removed the entries dealing with these archives.

Please take a look again, and you should see that the guide only requires you to download the mainline kernel debs, and the actual drivers are upgraded from the Xorg-edgers repository. If the Debian packages are conflicting, force a downgrade (using the downgrade instructions in the first post).

---

### Post by dicairo on 2009-05-11
sorry doesn't work for me . when i reboot in the new kernel it gives me a masege that i am using lower graphics and gives 3 chioses use default graphics - use the lower grahics - and anoter choice i cant rember it now.  i have intel X3100 maybe because i upgrade my kernel to 2.6.30-rc5 
sorryyyy about my english and i hope to see this bug risolved or by upgrading the kernel or by a normal update

---

### Post by psyke83 on 2009-05-11
Hi,

I've re-written the guide to clarify the instructions; there are now three ways to resolve the Intel drivers performance issues.

I recommend new users to use the Safe configuration, and those who understand the risks can try the more advanced options.

---

### Post by appzattak on 2009-05-11
Hey there, great write up! I'm not too sure I need to do this or not. For the most part my system works good. I can watch movies and play video with what seems to be ok. My one issue is that when I enable the Cube and rotate cube, my laptop goes to a crawl, I've not ever had that issue on any laptop. If you could let me know if I could benefit from it I will try it.

Here is my card info.

> steve@steve-lapppy:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0a00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 1800 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at f0b00000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f0a80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>



---

### Post by psyke83 on 2009-05-11
> **appzattak said:**
> Hey there, great write up! I'm not too sure I need to do this or not. For the most part my system works good. I can watch movies and play video with what seems to be ok. My one issue is that when I enable the Cube and rotate cube, my laptop goes to a crawl, I've not ever had that issue on any laptop. If you could let me know if I could benefit from it I will try it.

Here is my card info.

You can download and use the fixmtrr.sh script to see if it helps, and it's worth checking if UXA acceleration helps. 

Maybe give the Safe configuration a try - you can easily downgrade packages if you have any problems.

---

### Post by volneilo on 2009-05-11
**psyke83**, I guess there's a typo in this line on your tutorial in the first post. Check out the command below, **Part C (Optimal)** section:

$ sudo dpkg -i linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb linux-headers-2.6.29-02062903_2.6.29-02062903_all.**_deblinux_**-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb

Seems there's a missing space between **deb** and **linux**. I had trouble with the installation untill a figured it out.

By the way, thank you for all your efforts in helping us out! :popcorn:

---

### Post by psyke83 on 2009-05-11
> **volneilo said:**
> **psyke83**, I guess there's a typo in this line on your tutorial in the first post. Check out the command below, **Part C (Optimal)** section:

$ sudo dpkg -i linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb linux-headers-2.6.29-02062903_2.6.29-02062903_all.**_deblinux_**-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb

Seems there's a missing space between **deb** and **linux**. I had trouble with the installation untill a figured it out.

By the way, thank you for all your efforts in helping us out! :popcorn:

Thanks, I'll make the correction. Let me know if you spot any more mistakes!

---

### Post by wersdaluv on 2009-05-11
I followed the solutions from this thread (before it was edited). Probably, it's the "bleeding edge" solution from the OP. However, I have been experiences problems with suspend. My GNOME sessions aren't preserved when I do so. I'm not sure if this guide caused that but I tried to follow instructions from [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) . This reverted my driver to xserver-xorg-intel-video-driver-2.4. 

Doing that caused my GNOME session not to start so I reinstalled the xserver-xorg-intel-video-driver from the repository from the OP. After doing that, GNOME already starts but I'm stuck with a mouse cursor and a white background with low resolution after logging in. 

Any idea how to fix this?

---

### Post by appzattak on 2009-05-11
> **psyke83 said:**
> You can download and use the fixmtrr.sh script to see if it helps, and it's worth checking if UXA acceleration helps. 

Maybe give the Safe configuration a try - you can easily downgrade packages if you have any problems.


I went ahead and did Solution A and B. So far so good, it really easy way snappier. Before I could not record a screenshot session (video) and now it does perfectly. Compiz runs super fast with the desktop cube now. So all in all I like it very much. 

Is there a way to run the sudo fixmtrr.sh on startup?

--Steve

---

### Post by psyke83 on 2009-05-11
> **appzattak said:**
> I went ahead and did Solution A and B. So far so good, it really easy way snappier. Before I could not record a screenshot session (video) and now it does perfectly. Compiz runs super fast with the desktop cube now. So all in all I like it very much. 

Is there a way to run the sudo fixmtrr.sh on startup?

--Steve

I've revised the guide to do exactly this. Refresh the guide and do Part A, Step 3 to create the appropriate symlink. Also re-read the Important Note section.

---

### Post by psyke83 on 2009-05-12
> **wersdaluv said:**
> I followed the solutions from this thread (before it was edited). Probably, it's the "bleeding edge" solution from the OP. However, I have been experiences problems with suspend. My GNOME sessions aren't preserved when I do so. I'm not sure if this guide caused that but I tried to follow instructions from [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) . This reverted my driver to xserver-xorg-intel-video-driver-2.4. 

Doing that caused my GNOME session not to start so I reinstalled the xserver-xorg-intel-video-driver from the repository from the OP. After doing that, GNOME already starts but I'm stuck with a mouse cursor and a white background with low resolution after logging in. 

Any idea how to fix this?

I suggest you follow the instructions to revert changes in this guide. Additionally, go to Synaptic, click Status -> Installed (Local or Obsolete), and ensure that you don't have any xorg/mesa/drm packages listed in this section. If you do have driver packages listed in this category, do the following for each: select a package, go to the Package menu, choose "Force Version...", and pick the default Jaunty version of the package. Providing that there's no conflicts, apply changes, and then log out and back in.

---

### Post by wersdaluv on 2009-05-12
> **psyke83 said:**
> I suggest you follow the instructions to revert changes in this guide. Additionally, go to Synaptic, click Status -> Installed (Local or Obsolete), and ensure that you don't have any xorg/mesa/drm packages listed in this section. If you do have driver packages listed in this category, do the following for each: select a package, go to the Package menu, choose "Force Version...", and pick the default Jaunty version of the package. Providing that there's no conflicts, apply changes, and then log out and back in.
Hmm. It's just that, GNOME (and KDE) isn't usable because I just see a white screen background. Any suggestion, sir? :)

---

### Post by psyke83 on 2009-05-12
> **wersdaluv said:**
> Hmm. It's just that, GNOME (and KDE) isn't usable because I just see a white screen background. Any suggestion, sir? :)

You can revert changes via the failsafe terminal. 

Note that a white screen possibly indicates a problem with compiz, so using the failsafe graphics (vesa driver) will allow you to bypass that.

---

### Post by markbl on 2009-05-12
I've followed this guide and upgraded to the rc kernels as they have been released. I just updated to 2.6.30-rc5, as in the latest version of this guide, and noticed that the nice looking jaunty boot splash screen has returned.

---

### Post by scarf on 2009-05-12
i have the Intel 855GM and have just now gone from the old 2.4 drivers to following the "Safe" solution (i removed the 2.4 drivers and reinstalled xserver-xorg-video-intel, which is now version 2.7.0-1ubuntu2~xup~1).  my initial impression is there hasn't been much, if any, improvement.  i'm only testing scrolling, and it's really laggy.. lol.  i haven't tested with penguin racer before, but when i started it my whole screen turns white and i have to hit ESC to end the application and return to my desktop.....

---

### Post by wersdaluv on 2009-05-12
> **psyke83 said:**
> You can revert changes via the failsafe terminal. 

Note that a white screen possibly indicates a problem with compiz, so using the failsafe graphics (vesa driver) will allow you to bypass that.
You're a genius! I logged in GNOME and disabled compiz with the trusty GNOME Do. I'm reverting changes now. 

Btw, your new post instructs the deletion of kernels that aren't installed in my system. Are the kernels here different from your older post?

---

### Post by wersdaluv on 2009-05-12
After reverting changes, I did your "Optimal" fix. Now, my touch pad acts oddly. If I move my finger quickly, the mouse pointer's movement becomes smaller than if I move it slowly. 

I mean, if a move my finger from a point to another on the touchpad slowly, the movement of the mouse cursor is of greater distance than if I move my finger quickly.

Any idea why and how to fix this?

---

### Post by cankoy on 2009-05-12
What's the point of making 5 alpha releases + Beta + RC if this is what we get for *stable*? Can someone **honestly** explain, please?

---

### Post by svtguy88 on 2009-05-12
I just installed Jaunty on my friends desktop and was appalled by the terrible full screen flash and overall video performance.  I updated to the latest kernel RC, latest drivers and enabled the options in X's config file.

The performance increase is good, but everything still isn't perfect.  I can watch full screen 720p quicktime movie files now (barely could do it before), but still can't stream high quality from you tube in full screen.  I'm thinking this is more flash related than anything at this point, as other video performance is pretty good considering the ancientness of this desktop (P4 2.66 w/Intel 865G).

---

### Post by wersdaluv on 2009-05-12
Due to the touch pad problem, I reformatted. I thought, the problem is caused by something else, but apparently, its caused by the new instructions. I just did the safe configuration then the touch pad problem came out. I reverted the changes but the touch pad issue is still here.

I hope to find a fix soon. This is very bugging

---

### Post by psyke83 on 2009-05-12
> **cankoy said:**
> What's the point of making 5 alpha releases + Beta + RC if this is what we get for *stable*? Can someone **honestly** explain, please?

Your question begins with a fallacy. Jaunty was shipped with a configuration that was deemed *stable*, at the cost of performance (we shipped with EXA acceleration as the default rather than UXA).

What exactly is your problem? Ubuntu, like any other distribution, is at the mercy of release schedules for upstream projects. There was no Intel driver with stable UXA (and therefore DRI2) acceleration shipping in time for Jaunty's release, so the Ubuntu developers wisely opted to revert to the more stable EXA acceleration.

Stability does not equal performance.

---

### Post by psyke83 on 2009-05-12
> **pkmgarf said:**
> I just installed Jaunty on my friends desktop and was appalled by the terrible full screen flash and overall video performance.  I updated to the latest kernel RC, latest drivers and enabled the options in X's config file.

The performance increase is good, but everything still isn't perfect.  I can watch full screen 720p quicktime movie files now (barely could do it before), but still can't stream high quality from you tube in full screen.  I'm thinking this is more flash related than anything at this point, as other video performance is pretty good considering the ancientness of this desktop (P4 2.66 w/Intel 865G).

I have an Intel 855GM chipset, so our configuration is similar. I experience the best results with the Optimal configuration. At present, the Bleeding-Edge combination results in reduced 3D performance (though that can change at any time, since the drivers are updated from the xorg-edgers repository every few days).

By the way, the latest kernel isn't necessarily the fastest/best. There was a regression in 3D performance from 2.6.30rc2 to rc3 (and later) for my chipset. Just stick with the Optimal config.

You'll need to revert the drivers according to the instructions (as the xorg-edgers PPA contains versions are higher than the ones in the X-Updates PPA).

---

### Post by psyke83 on 2009-05-12
> **wersdaluv said:**
> Due to the touch pad problem, I reformatted. I thought, the problem is caused by something else, but apparently, its caused by the new instructions. I just did the safe configuration then the touch pad problem came out. I reverted the changes but the touch pad issue is still here.

I hope to find a fix soon. This is very bugging

If you are using the official Jaunty kernel, these instructions should have absolutely no impact on the touchpad. Is your touchpad usually recognised by default, or do you have to adjust your xorg.conf?

---

### Post by svtguy88 on 2009-05-12
^^^While I agree with the performance doesn't equal stability statement, in this case stability didn't even equal stability for me.  With the default configuration (just after install), X would crash randomly and the config file had to be reconfigured numerous times before it was any sort of "stable."

Just my $.02 with the rig I have been working on.

---

### Post by scarf on 2009-05-12
> **wersdaluv said:**
> Due to the touch pad problem, I reformatted. I thought, the problem is caused by something else, but apparently, its caused by the new instructions. I just did the safe configuration then the touch pad problem came out. I reverted the changes but the touch pad issue is still here.

I hope to find a fix soon. This is very bugging

i remember seeing a xserver-xorg-input-synaptics (pointing device) package being updated last night while following the instructions, after running 'apt-get install dist-upgrade' i believe.  however, i can't seem to find any record of that now......

however, 0.99.3-2ubuntu4 is the version available in the repositories, and 0.99.3-2ubuntu5 is the version available in the new X Updates PPA we added in step 1 of the instructions.

not sure if this is the correct way, but you can go back to the previous version by opening synaptic package manager, searching for 'synaptics', finding the installed package, clicking package > force version (or typing ^E), and change the version back to 0.99.3-2ubuntu4

---

### Post by HotShotDJ on 2009-05-12
Some notes as I attempt to fix the performance on my Dell Inspiron E1505 with the following Intel Graphics:```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```[LIST]
[*]Simply editing /etc/X11/xorg.conf as suggested in the HOWTO brings things back to life... however, stability becomes an issue (X locks up randomly requiring a hard reboot).
[*]The "Optimal" setup returns my system to the same poor performance I experienced with Jaunty's default configuration (sluggish/jerky compiz effects & PlanetPenguinRacer around 6 to 9 fps, jerky full-screen flash videos via YouTube). _SECURITY ISSUE_ -- gksudo provides permission elevation without requiring a password when using the 2.6.29 kernel as instructed.  Returning to the default kernel restores expected behavior.
[*]"Safe" Instructions -- Much better performance of desktop effect (compiz), PlanetPenguinRacer (around 18 to 24 fps) and smooth performance of full-screen flash (including HQ videos) -- Alas, the same lock-up problem.
[*]"Bleeding Edge" option as a last resort -- WOW!  PlanetPenguinRacer now showing about 25 - 53 fps.  It gave me the courage to try Googleearth 5 -- running VERY smoothly under compiz.  However, fullscreen flash on YouTube back to being dodgy (I can live with that for now)  Video appears stable.  4 hours without locking up and without a reboot. -- Just noticed on boot-up "Loading securityfs  [COLOR="Red"][FAILED][/COLOR] (will double check on next boot) -- any idea what this is about and how to fix?
[/LIST]
I'll edit the above list as I continue testing.

psyke83: If there is any addition information you need as I progress that would help you as you develop your HOWTO, please ask and I will do my best to provide it.

---

### Post by wyth on 2009-05-12
> **cankoy said:**
> What's the point of making 5 alpha releases + Beta + RC if this is what we get for *stable*? Can someone **honestly** explain, please?

Don't take this the wrong way, although I'm afraid that's a tough call, but --

What's the point of explaining it to you when it's been explained in previous posts here, elsewhere in these forums, on Phoronix, and in just about every blog that's covering Ubuntu, let alone podcasts?  Can you **honestly** explain why you need someone to explain it to you again?  Because all we'll do at this point is just refer you to everything that's already been written on it.  

Please exert the minimal required effort to find the answer to a question before begging for everyone's attention. 

My GM965 has been working brilliantly lately, better than on Intrepid.  I think I'm done with this thread -- too many email updates in my box asking the same questions over and over and over again. 

psyke83, thanks for the help.  With the guide and a little experimentation, I've been able to get some fantastic graphics going.

---

### Post by thebestofall007 on 2009-05-12
**UPDATE**

i recommend doing this intel graphics guide on a fresh install for the best stability. this solution works wonders for me, but i had problems with it freezing my system (as i stated in another post on this thread). i installed windows xp as a dual boot in order to use a firmware update tool for an rca pearl mp3 player that only works with windows. unfortunately windows trashed grub (dammit windows, you suck! you are now banned from my hard drive indefinitely!) and i was unable to restore it so i reinstalled my ubuntu jaunty setup windows messed up (i didnt lose any of my documents, etc though). i applied this solution to the new install, and it is working better than what i had before the reinstall. i try the same things that froze my system in the old install and i dont have those problems anymore after trying the safe method.

thanks psyke83!!!
if any other issues come up, ill post.

---

### Post by wersdaluv on 2009-05-12
> **psyke83 said:**
> If you are using the official Jaunty kernel, these instructions should have absolutely no impact on the touchpad. Is your touchpad usually recognised by default, or do you have to adjust your xorg.conf?
I'm using the default kernel. The condition of the touch pad is the same from the new and default kernels

---

### Post by wersdaluv on 2009-05-12
> **scarf said:**
> i remember seeing a xserver-xorg-input-synaptics (pointing device) package being updated last night while following the instructions, after running 'apt-get install dist-upgrade' i believe.  however, i can't seem to find any record of that now......

however, 0.99.3-2ubuntu4 is the version available in the repositories, and 0.99.3-2ubuntu5 is the version available in the new X Updates PPA we added in step 1 of the instructions.

not sure if this is the correct way, but you can go back to the previous version by opening synaptic package manager, searching for 'synaptics', finding the installed package, clicking package > force version (or typing ^E), and change the version back to 0.99.3-2ubuntu4
I'll try it when I get home. Thanks. 

I love this howto's fix because it doesn't just improve my video cards performance. It also fixes jaunty bugs on my machine like not shutting down properly and (maybe) not recovering my session from sleep.

If I manage to fix the touch pad issue with the "Optimal" configuration, I would finally have a properly configured Jaunty.

---

### Post by psyke83 on 2009-05-12
> **wersdaluv said:**
> I'm using the default kernel. The condition of the touch pad is the same from the new and default kernels

Yes, it appears that scarf's advice applies to you. I didn't notice that the Synaptics driver was also in the X-Updates repository, and the update must have caused issues for your touchpad.

Remember you can also lock the older version in Synaptic  (not Synaptics, heh) after downgrading the package.

---

### Post by psyke83 on 2009-05-12
> **thebestofall007 said:**
> **UPDATE**

i recommend doing this intel graphics guide on a fresh install for the best stability. this solution works wonders for me, but i had problems with it freezing my system (as i stated in another post on this thread). i installed windows xp as a dual boot in order to use a firmware update tool for an rca pearl mp3 player that only works with windows. unfortunately windows trashed grub (dammit windows, you suck! you are now banned from my hard drive indefinitely!) and i was unable to restore it so i reinstalled my ubuntu jaunty setup windows messed up (i didnt lose any of my documents, etc though). i applied this solution to the new install, and it is working better than what i had before the reinstall. i try the same things that froze my system in the old install and i dont have those problems anymore after trying the safe method.

thanks psyke83!!!
if any other issues come up, ill post.

It's actually quite easy to restore GRUB if you have a live cd available, but it seems that a full reinstall turned out for the best anyway! :)

---

### Post by wersdaluv on 2009-05-12
> **psyke83 said:**
> Yes, it appears that scarf's advice applies to you. I didn't notice that the Synaptics driver was also in the X-Updates repository, and the update must have caused issues for your touchpad.

Remember you can also lock the older version in Synaptic  (not Synaptics, heh) after downgrading the package.

Nice. I'm excited to go home. lol. I left my laptop because of being so pissed. hehe. Please include in the original post how to revert the synaptic driver :)

---

### Post by cankoy on 2009-05-13
Can someone tell how to stop the LCD randomly flashing?
That's all I want.
I repeat: I don't care about 3D, or EXA, or UXA, or no accel.
Just tell me how to put an Intel X3100+965GMA powered laptop display to a sane state.

---

### Post by bobe84 on 2009-05-13
Hmmm, i have also X3100 on Inspiron 1525 and it doesn't flash, can you describe what is problem...
also ```
lspci -nn
```
What version of ubuntu do u use, and what kind of computer do you have?Did you try newest drivers?



PS. I didnt read whole thread, so if you posted these infos sorry!

---

### Post by Inaia on 2009-05-13
Awesome tut, but do these instructions also fix various issues with Intel 9xx series in Hardy Heron, or is there another tut for that somewhere? Games that use OpenGL are leaving ghost images, tearing, flickering, low performance, and various other issues, so as a gamer I'd really like a fix >_<

---

### Post by Arup on 2009-05-13
Hardy Heron has way less issues with Intel, in fact exa works fine, some with Intrepid and Jaunty are reverting back to Hardy Heron 2.4 xorg.

---

### Post by Inaia on 2009-05-13
> **Arup said:**
> Hardy Heron has way less issues with Intel, in fact exa works fine, some with Intrepid and Jaunty are reverting back to Hardy Heron 2.4 xorg.

2D apps are working fine, but anything OpenGL-related is giving me problems. Is there other support I can try besides Mesa that won't cause excessive tearing, slowdown, and afterimages that won't go away?

---

### Post by wersdaluv on 2009-05-13
So happy! My touch pad is fine now :D

Edit: I just hate the fact that the new kernel messes up with my brightness multimedia keys. hehe. It's not too bad, though :)

---

### Post by thebestofall007 on 2009-05-13
> **psyke83 said:**
> It's actually quite easy to restore GRUB if you have a live cd available, but it seems that a full reinstall turned out for the best anyway! :)

i had the live cd but when i tried to fix grub by using this method:

```
sudo grub

grub> find /boot/grub/stage1

[should return your Ubuntu partition in the form (hdX,Y), use that:]

grub> root (hdX,Y)

grub> setup (hdX)

grub> quit


```

i got the error 15 file not found on the "find /boot/grub/stage1" part. that was a showstopper for me. i used this method before to fix grub after i installed linux first and then windows and it worked fine, but this time it didnt work.  when i tried to boot (after removing windows, and installing ubuntu again in the partition where windows was, in order to have a bootable partition to access the nonbootable partition's files), i got the "error 2, bad directory or file type".

---

### Post by svtguy88 on 2009-05-13
So after a few days of using the new kernel, my audio has disappeared.  The card is still recognized by running aplay in terminal, and it also still shows up in lspci.  Thoughts?  I've already uninstalled/reinstalled all of the alsa components using synaptic.

---

### Post by lucis on 2009-05-13
I'm running a fully updated Jaunty installation with an Intel Mobile GM965/GL960 graphics chipset. I followed all the instructions here and still have a ton of issues. 

* Firefox fonts are garbled. The extent of this varies; sometimes it will go away after a Firefox restart, sometimes not. Sometimes all fonts are garbled, sometimes just a specific letter or two.

* Performance in general is terrible. I have never had these sorts of problems in all my time using Ubuntu (since early '05). Apps freeze up, my laptop becomes unresponsive, audio playback skips and stammers like a scratched up CD, random colors flicker by when opening or moving a window, etc. 

Really frustrating. ](*,)

---

### Post by jsegel on 2009-05-13
reiterating: i have (as i stated at least once during this thread) an intel i810/p3 laptop that's getting zero video on its little screen. i've tried all the suggestions here, editing xorg.conf, using the script for /proc/mtrr, doing the driver reversion etc.
best i get is some flickery grey and black bars. 

so, i just tried plugging in an extrenal vga lcd monitor, 1440x900, and lo and behold, booting gives me a normally working screen on it. still nothing on my laptop's lcd though. what does this mean?

one note, this only works using startx, if i try to get video using "X -config /path/to/xorg.conf"
whether it's the basic minimal /etc/X11/xorg.conf   (which is like the dpkg-reconfigure one with 5 lines) or ~/xorg.conf.new  which is a maximal one with all sorts of  tries from all suggestions, i get NOTHING. 
huh? so using startx, what conf is it using? and why doesn't it see the laptop's internal screen?

---

### Post by lucis on 2009-05-13
> **jsegel said:**
> reiterating: i have (as i stated at least once during this thread) an intel i810/p3 laptop that's getting zero video on its little screen. i've tried all the suggestions here, editing xorg.conf, using the script for /proc/mtrr, doing the driver reversion etc.
best i get is some flickery grey and black bars. 

so, i just tried plugging in an extrenal vga lcd monitor, 1440x900, and lo and behold, booting gives me a normally working screen on it. still nothing on my laptop's lcd though. what does this mean?

one note, this only works using startx, if i try to get video using "X -config /path/to/xorg.conf"
whether it's the basic minimal /etc/X11/xorg.conf   (which is like the dpkg-reconfigure one with 5 lines) or ~/xorg.conf.new  which is a maximal one with all sorts of  tries from all suggestions, i get NOTHING. 
huh? so using startx, what conf is it using? and why doesn't it see the laptop's internal screen?

I had an issue similar to this in the past when I upgraded to Edgy. It turned out Ubuntu was outputting video by default to the external VGA, which was switched over to the laptop screen via a key combination (Fn + F8 on my Dell laptop). Have you tried this?

alternatively, did the laptop screen work prior to upgrading? one suspects hardware issues, e.g. a loose wire or the like.

---

### Post by Endolith on 2009-05-13
> **psyke83 said:**
> The chances are slim-to-none.

Why don't they fix things like this after a release?

> Karmic is your best bet for official support.

But there will be something equivalently bad that is broken in Karmic, and then that won't be fixed until 6 months later.   How are we supposed to deal with this constant cycle of breakage with each release?

---

### Post by jsegel on 2009-05-13
> **lucis said:**
> I had an issue similar to this in the past when I upgraded to Edgy. It turned out Ubuntu was outputting video by default to the external VGA, which was switched over to the laptop screen via a key combination (Fn + F8 on my Dell laptop). Have you tried this?

alternatively, did the laptop screen work prior to upgrading? one suspects hardware issues, e.g. a loose wire or the like.

fn + f11 (display switch)  key trick doesn't seem to do anything here. just makes the external go blank.

and yeah, the screen works fine - did for planetccrma fedora core 3-7 which was on the laptop before. when i installed ubuntu and found the screen dead, i wiped the new drive and reloaded windows, and that worked fine. so i wiped the drive again and loaded ubuntu studio, and no screen ever since.

btw, the opening UBUNTU STUDIO  scroll is present on both screens.

---

### Post by psyke83 on 2009-05-13
> **Endolith said:**
> Why don't they fix things like this after a release?



But there will be something equivalently bad that is broken in Karmic, and then that won't be fixed until 6 months later.   How are we supposed to deal with this constant cycle of breakage with each release?

Nothing is really "broken" in Jaunty. What you quoted was a reply to the question as to whether kernel 2.6.30 and a new Intel driver with UXA enabled by default would be available in Jaunty.

It's not going to happen because of the [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") process.

What is possible to happen, and will hopefully happen, is that fixes will be backported to Jaunty's Intel driver and/or kernel 2.6.28 to improve performance and stability.

So try not to spread misinformation, please. Ask upstream about the "constant cycle of breakage"; the Ubuntu developers work with the code they're given before release, and they couldn't have done much better than they did.

---

### Post by psyke83 on 2009-05-13
> **jsegel said:**
> reiterating: i have (as i stated at least once during this thread) an intel i810/p3 laptop that's getting zero video on its little screen. i've tried all the suggestions here, editing xorg.conf, using the script for /proc/mtrr, doing the driver reversion etc.
best i get is some flickery grey and black bars. 

so, i just tried plugging in an extrenal vga lcd monitor, 1440x900, and lo and behold, booting gives me a normally working screen on it. still nothing on my laptop's lcd though. what does this mean?

one note, this only works using startx, if i try to get video using "X -config /path/to/xorg.conf"
whether it's the basic minimal /etc/X11/xorg.conf   (which is like the dpkg-reconfigure one with 5 lines) or ~/xorg.conf.new  which is a maximal one with all sorts of  tries from all suggestions, i get NOTHING. 
huh? so using startx, what conf is it using? and why doesn't it see the laptop's internal screen?

You really need to file a bug on this issue (and revert changes from this guide before doing so).

Unfortunately, i810 hardware isn't tested by the developers too often, so the potential for regressions in new drivers is high. Have you done the obvious, such as checking the Xorg.0.log for errors, seeing if VESA works, etc?

It could be a refresh rate problem with your laptop screen.

---

### Post by psyke83 on 2009-05-13
> **lucis said:**
> I'm running a fully updated Jaunty installation with an Intel Mobile GM965/GL960 graphics chipset. I followed all the instructions here and still have a ton of issues. 

* Firefox fonts are garbled. The extent of this varies; sometimes it will go away after a Firefox restart, sometimes not. Sometimes all fonts are garbled, sometimes just a specific letter or two.

* Performance in general is terrible. I have never had these sorts of problems in all my time using Ubuntu (since early '05). Apps freeze up, my laptop becomes unresponsive, audio playback skips and stammers like a scratched up CD, random colors flicker by when opening or moving a window, etc. 

Really frustrating. ](*,)

I've noticed corrupted fonts in Firefox after several hours uptime when using the latest drivers from Xorg-edgers - Karmic Koala alpha testers seem to suffer from the issue too. My suggestion is that you only stick to the Safe or Optimal configuration.

Your issues of unresponsive applications probably aren't related to the Intel driver, so you should take these issues elsewhere. For your information, the ALSA kernel drivers for intel8x0 and intel-hda are buggy when using PulseAudio, and a kernel with the required fixes is in the "proposed" repository - this could resolve your choppy audio, at least. Again though, this isn't the proper place to ask about these issues.

Remember that you need to revert to the official Jaunty drivers before reporting bugs.

---

### Post by psyke83 on 2009-05-13
> **pkmgarf said:**
> So after a few days of using the new kernel, my audio has disappeared.  The card is still recognized by running aplay in terminal, and it also still shows up in lspci.  Thoughts?  I've already uninstalled/reinstalled all of the alsa components using synaptic.

Then revert to the old kernel, or follow the instructions to revert changes entirely.

It could be something really simple, such as your PCM volume getting reset to 0%. You may want to take a look at my PulseAudio guide. There's troubleshooting steps in the guide where you can see potential problems with your sound card.

This is the wrong thread to deal with audio or kernel issues - I assume you read the disclaimer regarding unofficial kernels in the guide?

---

### Post by svtguy88 on 2009-05-13
I did not read it...but I would have thought it would have been good to note that the bleeding edge fix is causing other issues (as expected)....

---

### Post by lucis on 2009-05-14
> **psyke83 said:**
> I've noticed corrupted fonts in Firefox after several hours uptime when using the latest drivers from Xorg-edgers - Karmic Koala alpha testers seem to suffer from the issue too. My suggestion is that you only stick to the Safe or Optimal configuration.

Your issues of unresponsive applications probably aren't related to the Intel driver, so you should take these issues elsewhere. For your information, the ALSA kernel drivers for intel8x0 and intel-hda are buggy when using PulseAudio, and a kernel with the required fixes is in the "proposed" repository - this could resolve your choppy audio, at least. Again though, this isn't the proper place to ask about these issues.

Remember that you need to revert to the official Jaunty drivers before reporting bugs.


But how can you be so sure? Audio playback problems and garbled fonts go hand in hand on my machine. Audio works fine for a while, then fonts go wonky, apps start locking up, and the audio goes. 

I finally just gave up and downgraded to Intrepid. Really shakes my faith in the Ubuntu development process, though, if they do all this testing and this is what we get as a final product.

---

### Post by JamesHowlett on 2009-05-14
Hi guys, been running the safe method for a couple of weeks now.  Anyways, I just want to ask a question to see if anyone else is getting the same type of performance.

I'm running on an 945GM chipset with the latest xorg-edgers drivers and vanilla kernel and I'm wondering if anyone else, not necessarily on the same setup, is getting this issue where if Totem is running in the background, the Ubuntu notifications no longer appear on screen?  thanks.

---

### Post by objem on 2009-05-14
Thanks for the excellent guide. I have been running the bleeding edge configuration for a while now and I got a significant improvement over default. Although performance is still not as good as it was under previous Ubuntu versions. I wonder how long it will take for the new Intel drivers to be as good as the old ones?

---

### Post by S.A.A on 2009-05-14
I'm using the **Bleeding Edge** Configuration, the performance is good, but there is somthing with my xorg.conf, it's not using uxa:
```
cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000207
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): Option "AccelMethod" is not used

```
and my graphic card is:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

```

---

### Post by briansrapier on 2009-05-14
I've applied the 'optimal' configuration to my HP 6510B running 9.04. I'm interested to know what the kernel changes are. 

As a side note, my X performance has improved, but I still can't enable visual effects despite having no issues in 8.04 or 8.10.

---

### Post by psyke83 on 2009-05-14
> **S.A.A said:**
> I'm using the **Bleeding Edge** Configuration, the performance is good, but there is somthing with my xorg.conf, it's not using uxa:
```
cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000207
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): Option "AccelMethod" is not used

```
and my graphic card is:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

```

None of those messages are any cause for alarm. The libpciaccess warning happens to a lot of users, and it's innocuous. The "AccelMethod" warning is simply because the latest bleeding-edge Intel driver has dropped EXA/XAA acceleration support, therefore there is no need to specify an "AccelMethod" at all. 

It's necessary to keep in the guide, since users of the Safe/Optimal configuration (with the stable driver) still require this option to be specified explicitly.

P.S. The Optimal configuration is currently faster on my system. Though I can't say it's true for your hardware too, just keep it in mind. Latest is not always greatest.

---

### Post by psyke83 on 2009-05-14
> **briansrapier said:**
> I've applied the 'optimal' configuration to my HP 6510B running 9.04. I'm interested to know what the kernel changes are. 

As a side note, my X performance has improved, but I still can't enable visual effects despite having no issues in 8.04 or 8.10.

Check the guide again, and see the site from which the kernel is downloaded - the directory has a CHANGES file.

If you can't enable desktop effects, your card is possibly blacklisted by compiz (and changing the driver version won't help). Search the forum for compiz + blacklist.

---

### Post by S.A.A on 2009-05-14
> **psyke83 said:**
> The "AccelMethod" warning is simply because the latest bleeding-edge Intel driver has dropped EXA/XAA acceleration support, therefore there is no need to specify an "AccelMethod" at all. 

It's necessary to keep in the guide, since users of the Safe/Optimal configuration (with the stable driver) still require this option to be specified explicitly.

P.S. The Optimal configuration is currently faster on my system. Though I can't say it's true for your hardware too, just keep it in mind. Latest is not always greatest.
Hey, thanks again, but i think i followed your GUIDE very well.
BTW, the new kernel 2.6.30rc5 doesn't complain about the write combining issue, even if you killed the xserver without restarting, so i think you should modify the GUIDE so **Part A** becomes just for Safe/Optimal.

---

### Post by slothdog on 2009-05-14
The "Optimal" fix doesn't improve video performance for me on an Eee PC 900 (915GM/GMS/910GML chipset).  However the patched kernel posted in [https://bugs.launchpad.net/linux/+bug/349314](https://bugs.launchpad.net/linux/+bug/349314) does seem to fix the problem.  I haven't tried the "Bleeding-Edge" fix yet.

---

### Post by Vadi on 2009-05-14
Well written guide.

---

### Post by scarf on 2009-05-14
> **JamesHowlett said:**
> Hi guys, been running the safe method for a couple of weeks now.  Anyways, I just want to ask a question to see if anyone else is getting the same type of performance.

I'm running on an 945GM chipset with the latest xorg-edgers drivers and vanilla kernel and I'm wondering if anyone else, not necessarily on the same setup, is getting this issue where if Totem is running in the background, the Ubuntu notifications no longer appear on screen?  thanks.

i didn't notice this with 855GM.  i tried disconnecting and connecting to wifi networks with totem running minimized and i still got the notifications.

it might only do it with totem in full-screen mode?

if that is the case, i would think this would be a good thing, as most people wouldn't want to be bothered with notifications while watching something in full-screen mode.  i think that is why we use full-screen mode, to minimize distractions. ;)

---

### Post by psyke83 on 2009-05-14
> **S.A.A said:**
> Hey, thanks again, but i think i followed your GUIDE very well.
BTW, the new kernel 2.6.30rc5 doesn't complain about the write combining issue, even if you killed the xserver without restarting, so i think you should modify the GUIDE so **Part A** becomes just for Safe/Optimal.

The script is smart enough not to set the MTRR range if it already exists, so there's no need to change the guide.

---

### Post by btermeli on 2009-05-14
Thanx for help but didn't work for me.
i915

---

### Post by tomchiverton on 2009-05-14
To run at start up, put in /etc/rc.local

---

### Post by psyke83 on 2009-05-14
> **tomchiverton said:**
> To run at start up, put in /etc/rc.local

No, it's not good enough. The script needs to be started each time X is restarted, which doesn't happen if you put it in /etc/rc.local.

The latest release candidate kernel has the fix, as S.A.A. mentioned, but the others do not.

---

### Post by jsegel on 2009-05-14
> **lucis said:**
> I had an issue similar to this in the past when I upgraded to Edgy. It turned out Ubuntu was outputting video by default to the external VGA, which was switched over to the laptop screen via a key combination (Fn + F8 on my Dell laptop). Have you tried this?

alternatively, did the laptop screen work prior to upgrading? one suspects hardware issues, e.g. a loose wire or the like.

(thought i had posted this reply yesterday, it doesn't seem to be here?)

the fn+F11 (in my case) display switch just leaves both black.

and yes. the laptop screen works - the initial UBUNTU loading scroll is fine. 

again, vesa drivers produce black screen. intel driver produces grey bars and black lines.

xorg.log.0 is generic errors - can't write to slave 236 etc...

---

### Post by jsegel on 2009-05-14
> **psyke83 said:**
> 
It could be a refresh rate problem with your laptop screen.

so... how would i change the lcd screen's refresh rate? i know i can put it into xorg.conf in the monitor section, but it seems everything that i try that uses xorg.conf is just black screen...
if i do startx, i get the grey bars - which i realize now, tells me that it's trying to render the ubuntu studio login screen! (though failing...)
what conf file is startx reading?   and how do i tell it  a different vertrefresh...?

---

### Post by risknothin on 2009-05-14
worked, i was having trouble with rhythmbox before doing the safe without the kernal update and now it works great no more skipping when i open other apps

Thanks!

---

### Post by wersdaluv on 2009-05-15
What would happen if I use the Optimal kernel with the xorg-edgers PPA? Is that fine?

---

### Post by PatrickVogeli on 2009-05-15
Ok there, after doing some tests, here are my results. I'm using a custom kernel 2.6.29.3.

With Jaunty and 2.6 intel drivers, I get ~800fps in glxgears and I don't suffer from the mtrr bug. 15-20fps in extreme tux racer
Jaunty and 2.4 intel drivers from some ppa didn't work well, I got some GEM error and only ~300fps in glxgears.
With Intrepid I remember I had also about 800fps in glxgears
Today booted a 8.04 live cd (from shipit, so it's 8.04.0) and glxgears got me ~800fps too.

So, two choices: my laptop has always been broken regarding to intel, or has never been...

Anyway, it works fine. Compiz is fast, scrolling in firefox is ok (there are few sites that won't be so smooth though) and the computer feels fast. That's it!

Patrick

---

### Post by DavetheDude on 2009-05-15
Thanks for the help, I followed the safe procedure and compiz runs notably faster.

A couple of strange things though... on restart it didn't seem to work and I was taken to a screen suggesting that I allow it to attempt to 'autofix' the problem. I proceeded and the greeter started as normal and have been fine since. I would have catalogued this process more carefully, only I didn't detect any problems until now, some days later. Today I noticed that I no longer have access to virtual terminals via the ctrl-alt-function. Instead, I get some flickering and then the ubuntu greeter. This also seems to end my original gnome session (ctrl-alt-f7). Trying this a few times produced the message 'the greeter application appears to be crashing, attempting to use different one'.

So, as something of an epic n00b, I humbly request assistance from any who may be able to provide it.

Cheers.

---

### Post by Andrew May on 2009-05-15
Hi,
I am running Jaunty on a desktop machine.
I have been following the evolution of these instructions and have taken the plunge as a newbie and applied the changes for optimal effect. 
They have done nothing except give me 1280x1024 resolution which was not available before. 
I cannot activate visual effects to normal setting and when I run PPRacer I have about 2 (yes two!) fps, which is what I had before the changes. I have restarted several times, and it tells me it is already applied:
Supplying corrected MTRR ranges to /proc/mtrr
doing nothing, MTRR range already set up
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x0f0000000 ( 3840MB), size=  128MB, count=1: write-combining

I have a dual core P4 3GHz with intel integrated graphics:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a5
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at fbe80000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at d800 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb

What am I doing wrong? any ideas? 
The rest of the computer functions fine...just no games or effects.
thanks,
Andrew

---

### Post by gambothell on 2009-05-15
:p Thanks for such great support. I used safe/optimal method on a Dell Inspiron 1420 with an Intel GM965. My wife now can watch Hulu ... 


Your the Man

---

### Post by Vadi on 2009-05-15
> **cankoy said:**
> Can someone tell how to stop the LCD randomly flashing?
That's all I want.
I repeat: I don't care about 3D, or EXA, or UXA, or no accel.
Just tell me how to put an Intel X3100+965GMA powered laptop display to a sane state.

Email [email]support@intel.com[/email] asking them why did they make such buggy drivers and didn't finish new ones in time? Ubuntu isn't the one that makes the Intel drivers and breaks them.

---

### Post by lucis on 2009-05-15
> **Vadi said:**
> Email [email]support@intel.com[/email] asking them why did they make such buggy drivers and didn't finish new ones in time? Ubuntu isn't the one that makes the Intel drivers and breaks them.

I would personally be more interested in hearing Ubuntu's side of the story. The new infrastructure in the kernel and in xorg are experimental, so why did the Ubuntu devs include them in the first place? I think it's pretty appalling that this thread has grown to 47 pages and I have yet to hear any official word from Ubuntu on the matter. 

When Jaunty breaks on my laptop, that's fine. I'm a geek and I know how to fix it. When it breaks on the machine of my non-geek friend who wants a viable alternative to virus-ridden Windows, that's a totally different issue. Where does she go when she can't do basic tasks without huge headaches? What a debacle.

---

### Post by psyke83 on 2009-05-15
> **lucis said:**
> I would personally be more interested in hearing Ubuntu's side of the story. The new infrastructure in the kernel and in xorg are experimental, so why did the Ubuntu devs include them in the first place? I think it's pretty appalling that this thread has grown to 47 pages and I have yet to hear any official word from Ubuntu on the matter. 

When Jaunty breaks on my laptop, that's fine. I'm a geek and I know how to fix it. When it breaks on the machine of my non-geek friend who wants a viable alternative to virus-ridden Windows, that's a totally different issue. Where does she go when she can't do basic tasks without huge headaches? What a debacle.

I suggest you do some research before making accusations. The Ubuntu developers **did not **ship Jaunty with the new acceleration framework for the reason that it was less stable.

The default Jaunty driver uses EXA by default (whereas the same upstream version uses UXA), and using UXA caused system freezes for many users. Whilst EXA suffered from some performance regressions, its stability was roughly the same as Intrepid.

In other words, what you think **should** have happened, **did** happen.

---

### Post by Arup on 2009-05-15
Why blame Ubuntu, they are giving us a choice of extremely stable and quick 8.04.2 LTS with support till 2011 and then you have cutting edge Jaunty which for sake of progress has to incorporate the latest stuff and only then can Ubuntu move on. Point being that Ubuntu of all the distros is far less prone to sacrifice stability for the sake of latest and speed, they always act with responsibility compared to many others who add all the latest kernel, xorg, etc. just to make their release look attractive at the sake of compatibility and stability.

In case you have issues with Jaunty, reverting back to 8.04 LTS is your best bet, its still supported and it runs fast as well.

Speaking about Intel drivers, they have myriads of issues in Windows world as well and I have used them on Windows so I speak from experience. Primarily till today Intel's latest 5029 still can't recognize the EDID of some leading monitors, LCD and CRT so you have to to a registry hack to get them working. Kinda annoying to see when your shiny new LCD monitor can't be set to its native resolution and thereby negating the who purpose of getting a new monitor. Then there are issues which have been typical with Intel from its early days of i740. Many games refuse to run and these don't just include high end stuff like the ones from Crysis etc. Even basic games, also Intel always has been known to skip complex frames to get their drivers to benchmark well, this still persists till today. I could go on and on but I would end it by repeating psyke83's advice of doing some research before plunging in. As a matter of fact, the amount of advice and hard work he and other give in this forum can't be touched by any Windows forum. When I ran into the resolution issue, there was no answer from Windows newsgroup, Intel reverted me back to a older modified driver, I needed to do some serious digging to find out the hack needed for the native resolution to function properly.

---

### Post by VMC on 2009-05-15
> **Andrew May said:**
> 
...
I have a dual core P4 3GHz with intel integrated graphics:

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    
What am I doing wrong? any ideas? 
The rest of the computer functions fine...just no games or effects.
thanks,
Andrew
Andrew, Your not doing anything wrong. I also have an Intel 82865G intregreated chip. I couldn't get my video working correctly following these instructions.

I found the [Revert_to_2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") method worked best for my chip.

---

### Post by HotShotDJ on 2009-05-15
psyke83:  Only the Bleeding-Edge instructions worked for me, and it worked brilliantly.  Thank you for your HOWTO.

I have only one concern.  On boot-up with the RC5 Kernel, I see the message:```
mounting securityfs on /sys/kernel/security   [COLOR="Red"][FAILED][/COLOR]
```
Do you know what the problem is and/or what the solution may be?  I haven't seen any problems on my system, but any failure (real or imagined) in my system's security makes me a bit nervous.

EDIT:  Ooops... just rechecked message.  Edited to correct.

---

### Post by markbl on 2009-05-16
> **HotShotDJ said:**
> Only the Bleeding-Edge instructions worked for me, and it worked brilliantly.  Thank you for your HOWTO.

Don't count your chickens too early. It always works well just after a reboot. I've been updating my laptop in sync with the RC kernels etc and find significant stability problems still occur. I'm currently on RC5 with the bleeding edge drivers and find that after a solid day of using my laptop (with a second external screen) that the system can get very slow and frequent screen/font corruptions start occurring. A reboot will clear this but it is a pain.

It is also a massive inconvenience that uxa/dri2 (which is the only mode intel driver will soon support) can not drive a second screen side by side with chipsets before 965 (unless total screen res is < 2048 which is not feasible in this day and age). I can only configure my second screen logically below my laptop screen and in spite of using this for a while it still feels really awkward. There is no solution in near sight.

Refer [https://bugs.freedesktop.org/show_bug.cgi?id=21190](https://bugs.freedesktop.org/show_bug.cgi?id=21190) and [https://bugs.freedesktop.org/show_bug.cgi?id=10479](https://bugs.freedesktop.org/show_bug.cgi?id=10479).

---

### Post by scarf on 2009-05-16
hi i wanted to add more about the scrolling issues.

it seems that scrolling works perfectly fine, in my opinion, with thunderbird, and also with text file in gedit.  i can use hyper-scrolling and it stops on a dime.

firefox, gnome-terminal, openoffice, and evince all have laggy scrolling capabilities.

---

### Post by Andrew May on 2009-05-16
> **VMC said:**
> Andrew, Your not doing anything wrong. I also have an Intel 82865G intregreated chip. I couldn't get my video working correctly following these instructions.

I found the [Revert_to_2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") method worked best for my chip.

Thanks VMC. My framerate on PPRacer is up to 35/40. I can now concentrate when my wife wants to talk to me...............:)
Andrew

---

### Post by tomchiverton on 2009-05-16
Put it in ~/.xinitrc then

---

### Post by psyke83 on 2009-05-16
> **tomchiverton said:**
> Put it in ~/.xinitrc then

Try again... ;) The script needs to be executed with root privileges.

---

### Post by tomchiverton on 2009-05-16
Aww, come on. Do I have to think of everything ? Set up a cron job (using root's crontab). Or chgrp adm /proc/mtrr;chmod g+rw /proc/mtrr in rc.local. Or ...

---

### Post by fcarb on 2009-05-16
Thanks for the straightforward fix (Used "optimal"). Fullscreen videos are now running smoothly.

Cheers!

---

### Post by joeray on 2009-05-16
I have a new jaunty install with an intel 945 chipset. I have trouble with scrolling and fullscreen flash. I have tried the various fixes in this thread without any noticeable improvements. The main reason I'm posting is to find out where the config file for the configured video device is located. It is not in the xorg.conf file. There are no specs at all in the file. Configured Monitor section is also empty. Please let me know what info about my setup and system I have to post in order to receive support. Thank you all for your invaluable help in the past and that which you all will provide to me and the community in the future. Joeray saying FREEDOM ISN'T FREE.

---

### Post by appzattak on 2009-05-16
anyone gettting "freezes"? I can only say that when I'm on random sites, say myspace or facebook and am viewing a picture or video, and scrolling quickly, my whole computer freezes. The only thing that works is the mouse, well it moves, but you cannot click anything. Caps lock does nothing when pressed, ctrl alt delete, does nothing...only way out is to hard shutdown the computer. Just wondering if anyone else has this issue. It has only been doing this since I did the optimal settings.

--Steve

---

### Post by EvanCarroll on 2009-05-16
This is getting more and more ridiculous. There is something to be said for an upgrade with an unforeseen problem; there is a whole different statement being made when you know about the problem before hand and you don't inform people through the official mechanism (do-release-upgrade/upgrade-manager). Why isn't there a caveat emptor notifying the user their configuration won't work after the upgrade? Certainly we know who won't be happy with this upgrade...

---

### Post by psyke83 on 2009-05-16
> **EvanCarroll said:**
> This is getting more and more ridiculous. There is something to be said for an upgrade with an unforeseen problem; there is a whole different statement being made when you know about the problem before hand and you don't inform people through the official mechanism (do-release-upgrade/upgrade-manager). Why isn't there a caveat emptor notifying the user their configuration won't work after the upgrade? Certainly we know who won't be happy with this upgrade...

You may not realize, but you're bordering within the territory of trolling. These issues have been identified in the official release notes for Jaunty; bugs are filed, and fixes will come.

See: [http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

The purpose of this guide is for **willing** users to experiment with some **unofficial** fixes via updated drivers. If you are not willing, simply ignore this thread.

---

### Post by psyke83 on 2009-05-16
> **joeray said:**
> I have a new jaunty install with an intel 945 chipset. I have trouble with scrolling and fullscreen flash. I have tried the various fixes in this thread without any noticeable improvements. The main reason I'm posting is to find out where the config file for the configured video device is located. It is not in the xorg.conf file. There are no specs at all in the file. Configured Monitor section is also empty. Please let me know what info about my setup and system I have to post in order to receive support. Thank you all for your invaluable help in the past and that which you all will provide to me and the community in the future. Joeray saying FREEDOM ISN'T FREE.

The /etc/X11/xorg.conf file is in fact the correct configuration file. Not too long ago, Xorg migrated towards the concept of an automatically-configured Xorg. The bare configuration file is still present in Ubuntu, presumably to make it easier for users to add driver/monitor options in the relative sections (for cases where automatic configuration is insufficient).

---

### Post by Endolith on 2009-05-16
> **psyke83 said:**
> You may not realize, but you're bordering within the territory of trolling.

So saying anything at all critical of Ubuntu is trolling?

---

### Post by Arup on 2009-05-16
Constructive criticism is fine with perspective, blatand rants just amounts to trollism.

---

### Post by psyke83 on 2009-05-16
> **Endolith said:**
> So saying anything at all critical of Ubuntu is trolling?

Not at all (within the guidelines of this forum, I suppose), but what the previous poster was saying was a distortion of reality.

---

### Post by mbay2002 on 2009-05-16
> **psyke83 said:**
> Your question begins with a fallacy. Jaunty was shipped with a configuration that was deemed *stable*, at the cost of performance (we shipped with EXA acceleration as the default rather than UXA).

What exactly is your problem? Ubuntu, like any other distribution, is at the mercy of release schedules for upstream projects. There was no Intel driver with stable UXA (and therefore DRI2) acceleration shipping in time for Jaunty's release, so the Ubuntu developers wisely opted to revert to the more stable EXA acceleration.

Stability does not equal performance.

Hi Psyke -
Let me jump in here... first, thanks for all your help with this.  I think the general frustration is that many of us assume that when a new stable version is released, we should download it and everything will work just as well as before, and hopefully we will see improvements.

When I ran update manager several weeks ago, I got a message that a new distro was available, and I elected to install on 3 of my systems that are running Ubuntu.  Interestingly, only me EEE ran without a hitch... my other 2 systems required lots of hacks but are now running fine.

I don't know what the solution is, but the PROBLEM is that there needs to be an easy way to find out what is likely to break if a user chooses to install a new "stable" distro...

---

### Post by joeray on 2009-05-16
> **psyke83 said:**
> The /etc/X11/xorg.conf file is in fact the correct configuration file. Not too long ago, Xorg migrated towards the concept of an automatically-configured Xorg. The bare configuration file is still present in Ubuntu, presumably to make it easier for users to add driver/monitor options in the relative sections (for cases where automatic configuration is insufficient).
I just tried the safe mode option. Thanks to your helping me to understand how to configure the video device file, I have noticed a marked improvement over all in performance. Many Thanks to all involved. Joeray Out.

---

### Post by psyke83 on 2009-05-16
> **mbay2002 said:**
> Hi Psyke -
Let me jump in here... first, thanks for all your help with this.  I think the general frustration is that many of us assume that when a new stable version is released, we should download it and everything will work just as well as before, and hopefully we will see improvements.

When I ran update manager several weeks ago, I got a message that a new distro was available, and I elected to install on 3 of my systems that are running Ubuntu.  Interestingly, only me EEE ran without a hitch... my other 2 systems required lots of hacks but are now running fine.

I don't know what the solution is, but the PROBLEM is that there needs to be an easy way to find out what is likely to break if a user chooses to install a new "stable" distro...

Perhaps it was some kind of rhetorical question, but what you're asking for is the release notes - they exist, and they are always available on the day of each new release. The issue of potential performance regressions with Intel drivers was documented.

See: [http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues)

It would be nice to have a link to the release notes via the upgrade manager to make them more accessible, though.

---

### Post by markbl on 2009-05-16
> **psyke83 said:**
> The issue of potential performance regressions with Intel drivers was documented.

"Performance regression" is one thing though, "Unusable" is what many of us actually get. My laptop was simply unusable after I upgraded to jaunty, after running intrepid and earlier releases just fine. Video and games stuttered, desktop/compiz struggled, etc. That's what brought me here (and thanks for the semi-workaround).

I personally struggle to understand how ubuntu were happy to release jaunty like this given the enormous number of laptop + intel video users out there. This is one big killer issue and it has a low potential of being fixed in the near term, certainly unlikely within this release. Jaunty is looking like being ubuntu's "Vista".

---

### Post by psyke83 on 2009-05-16
> **markbl said:**
> "Performance regression" is one thing though, "Unusable" is what many of us actually get. My laptop was simply unusable after I upgraded to jaunty, after running intrepid and earlier releases just fine. Video and games stuttered, desktop/compiz struggled, etc. That's what brought me here (and thanks for the semi-workaround).

I personally struggle to understand how ubuntu were happy to release jaunty like this given the enormous number of laptop + intel video users out there. This is one big killer issue and it has a low potential of being fixed in the near term, certainly unlikely within this release. Jaunty is looking like being ubuntu's "Vista".

I understand your frustration, but you have to understand that this issue did not affect all Intel graphics users - you (and I) were the unlucky ones.

Whilst I found the problem with video performance somewhat irritating, every other aspect of Jaunty was an improvement over Intrepid in my eyes (extremely fast boot, better PulseAudio integration, good general responsiveness, etc.).

Let's imagine the possible choices that the Ubuntu developers were presented with:
[LIST]
[*]Keep the 2.4 Intel driver. Then DRI would break for a lot of users (due to the Xorg server and DRM kernel changes).
[*]Keep the entire Xorg stack at the same version as Intrepid. What's the point, when you can just keep Intrepid installed?
[*]Delay the release until an Intel driver with better performance was released. Do you honestly think it would be wise to delay the entire distribution because of one driver that presents issues for a subset of users?
[/LIST]
In reality, two feasible choices existed - either:
[LIST]
[*]to include the latest Intel driver with the new UXA acceleration method enabled by default (faster, but causes system freezes), or; 
[*]include the latest Intel driver with the older EXA acceleration method enabled by default (slower, but it doesn't cause system freezes).
[/LIST]
The developers chose the safest option - I would appreciate if you (or anyone) could suggest something better? The bugs are filed, the issues are being investigated, and (official) fixes will eventually arrive.

---

### Post by markbl on 2009-05-17
I don't have the technical background to propose the best way that ubuntu could have attacked this but I suspect that this problem affects *way* more people than you allude to and thus ubuntu could have perhaps identified this as a killer issue in the lead up to jaunty release and thrown more resources at the problem. Quite simply, the solution chosen is as unpalatable as the others.

For the few here who have expressed frustration, I bet there are *plenty more* others and new users who tried out the latest ubuntu on their intel laptop and then simply tossed the disk into the bin and gone back to Windows. There would be plenty more again who probably just live with their latest ubuntu installation and just think that "ubuntu doesn't work very well".

I really appreciate your work and comments here psyke83. I just think this is the worst bug I've ever seen in a ubuntu release from the perspective of one long time ubuntu user. Ok, it may not be their explicit fault but unfortunately it rubs some shine off the ubuntu reputation.

---

### Post by arun_3t on 2009-05-17
Hi all,

Even after following the steps given in #1. I am not able to enable the desktop effects in my system. can anyone please help me on this!!!!

If i choose "normal" in my desktop effect my system refreshes and freezes with the background image after that i have to hard reboot my system to see the desktop effect is reverted back to "no effects". Any help on this???

---

### Post by densou on 2009-05-17
I argued/complained a lot about Canonical's policy, but I realized lately that (imo) the more 'user-friendly' major distro required a full stable environment for its purpose.

I have tested a large amount of stuff, and here you are my two cents after all my time spent and 0&#8364;/$ gained:

If you are not satisfied with combo Intel GMA+Ubuntu due to potential issues or something else (but similar), I'd recommend to try FEDORA 11 [to be release SOON], the bleeding-edge distro for who desires best experience with Intel GPU (just few clicks with your mouse/touchpad and it'll work BETTER than any other OS - note: by default only and regarding mere performances/FPS, not else).


Did you noticed that X-Swat released a 2.7.1 stable driver ?!? :o


Plus:
*```
Xserver-xorg-video-intel 2:2.7.99.1 drivers do not have EXA/XAA/XvMC support any longer!
```*

so I assume 2.8.0 would support UXA/DRI2 only (they will be shipped with Karmic !?) and become the 1st stable release supporting that :D




edit:
woah, what is this ???? [http://www.tungstengraphics.com/wiki/index.php/Gallium3D](http://www.tungstengraphics.com/wiki/index.php/Gallium3D)
It should be the main feature in Mesa 7.5 (currently in 7.5-RC2, last stable: 7.4.2 -released both on 15th May)

I wonder if it'll affect UXA/DRI2 or it'll be an "alternative driver", dunno :o

---

### Post by dicairo on 2009-05-17
Hi every one let me tell u my story with intel X3100 ,
 I installed ubuntu 9.04 with ex4  and as u know I found my intel black listed so I moved it from the black list and I force compiz to run but unfortunately the visual effects was slow in confront with ubuntu 8.10  after this I found this solution I did the optimal one but unfortunately I was having continuous freezing of the desktop I wasn't even able to revert the situation so I googled and I found that ex4 itsnt ready for use so i decided to reinstall 9.04 with ex3 and apply the optimal solution of this thread and wowwww the 2d is very goog but again the **3d operations are really bad**      .  
 I am just writing because I want to see ubuntu os the most perfect os [B]and I am really sad because until now there isn't any official solution that ca be done with normal update bye every one and i hope that my story was useful 
[/B]

---

### Post by tomchiverton on 2009-05-17
> **psyke83 said:**
> You may not realize, but you're bordering within the territory of trolling. These issues have been identified in the official release notes for Jaunty; bugs are filed, and fixes will come.
Well, the point was really that numerous beta and alpha testers found the problem, and it was released with them anyway.
A perfectly reasonable, indeed safer, solution existed (keep the whole X stack as it was and ship the updates (with 9.10 ?) when Intel had finished their changes) after all.

---

### Post by VMC on 2009-05-17
> **arun_3t said:**
> ...
Even after following the steps given in #1. I am not able to enable the desktop effects in my system. can anyone please help me on this!!!!

If i choose "normal" in my desktop effect my system refreshes and freezes with the background image after that i have to hard reboot my system to see the desktop effect is reverted back to "no effects". Any help on this???From a terminal run the following command:

```
lspci | grep VGA
```

Then come back with your results. If it reports 82865G, then you might consider installing Intel 2.4 driver

---

### Post by jsenlai on 2009-05-17
it works. I chose the "safe" one and it's enough fix for me. As long as my flash goes smoothly on fullscreen. thx

---

### Post by Arup on 2009-05-17
> **tomchiverton said:**
> Well, the point was really that numerous beta and alpha testers found the problem, and it was released with them anyway.
A perfectly reasonable, indeed safer, solution existed (keep the whole X stack as it was and ship the updates (with 9.10 ?) when Intel had finished their changes) after all.

With G31/33/45 the included xorg with uxa enabled works out fine and therefore if they would have kept the older xstack, people using these chips wouldn't have got the benefit of the newer uxa+gem features.

---

### Post by psyke83 on 2009-05-17
> **tomchiverton said:**
> Well, the point was really that numerous beta and alpha testers found the problem, and it was released with them anyway.
A perfectly reasonable, indeed safer, solution existed (keep the whole X stack as it was and ship the updates (with 9.10 ?) when Intel had finished their changes) after all.

That option is not compatible with Ubuntu's [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") policy. Besides, why should all users suffer with the older Xorg server and drivers when it is only a subset of Intel graphics users with any real issues?

If you hate Jaunty's Intel driver so much, stick with Hardy or Intrepid.

---

### Post by wersdaluv on 2009-05-18
The instuctions for the kernel of bleeding edge has a wrong architecture

Edit:
I meant, for the 64bit

---

### Post by Arup on 2009-05-18
> **dicairo said:**
> Hi every one let me tell u my story with intel X3100 ,
 I installed ubuntu 9.04 with ex4  and as u know I found my intel black listed so I moved it from the black list and I force compiz to run but unfortunately the visual effects was slow in confront with ubuntu 8.10  after this I found this solution I did the optimal one but unfortunately I was having continuous freezing of the desktop I wasn't even able to revert the situation so I googled and I found that ex4 itsnt ready for use so i decided to reinstall 9.04 with ex3 and apply the optimal solution of this thread and wowwww the 2d is very goog but again the **3d operations are really bad**      .  
 I am just writing because I want to see ubuntu os the most perfect os [B]and I am really sad because until now there isn't any official solution that ca be done with normal update bye every one and i hope that my story was useful 
[/B]


Did you try enabling uxa in xorg?

---

### Post by cyper on 2009-05-18
I just 'd like to say "Thank you!". Bleeding-edge drivers finally brought my system back to normal. Your how-to is great. But you know, it even got better after i commented out greedy migration heuristic ;) don't know why...
Anyway - Thanks!;)

---

### Post by galv on 2009-05-18
Can anybody give me a recommendation of the best method for a EEEPC 1000H user?
```
 lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)

```

Thanks

---

### Post by dicairo on 2009-05-18
> **Arup said:**
> Did you try enabling uxa in xorg?
 
if u mean by editing the xorg i did it and this my xorg : 
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false" 
EndSection
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

i am waiting for your answer  thanks man

---

### Post by Arup on 2009-05-18
> **dicairo said:**
> if u mean by editing the xorg i did it and this my xorg : 
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false" 
EndSection
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

i am waiting for your answer  thanks man


[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

This is all that should be in our xorg under device in case you are using Jaunty with xorg 1.6

---

### Post by dicairo on 2009-05-18
> **Arup said:**
> [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

This is all that should be in our xorg under device in case you are using Jaunty with xorg 1.6
how do i know that i am using xorg 1.6 ? and i didn't tell u that i am using this kernel 2.6.29.3-candela is this a problem ?2.6.29.3-candela

---

### Post by Arup on 2009-05-18
> **dicairo said:**
> how do i know that i am using xorg 1.6 ? and i didn't tell u that i am using this kernel 2.6.29.3-candela is this a problem ?2.6.29.3-candela

xorg 1.6 is included in default Jaunty installation but by the looks of it, don't think you are running a default installation.

---

### Post by dicairo on 2009-05-18
> **Arup said:**
> xorg 1.6 is included in default Jaunty installation but by the looks of it, don't think you are running a default installation.
 what do u mean by default installation?  i have ubuntu 9.04 and the only modification i done is upgrade the kernel by "kernel check" thanks again   :D

---

### Post by Arup on 2009-05-18
> **dicairo said:**
> what do u mean by default installation?  i have ubuntu 9.04 and the only modification i done is upgrade the kernel by "kernel check" thanks again   :D

Kernel check upgradation means its no longer default, in case of default Jaunty, your xorg section will not have the number of entries that I see.

---

### Post by dicairo on 2009-05-18
> **Arup said:**
> Kernel check upgradation means its no longer default, in case of default Jaunty, your xorg section will not have the number of entries that I see.
i real[HTML][/HTML]y dont know how to thank u , thanks again and appreciate any advise ):P

---

### Post by tomchiverton on 2009-05-18
Or, another way, why upset a bunch of people when there is little evidence of 'suffering' under the older drivers ? And please don't quote the well known 'SRU policy' line - the issue was known during the alpha and beta releases.

---

### Post by Arup on 2009-05-18
> **dicairo said:**
> i real[HTML][/HTML]y dont know how to thank u , thanks again and appreciate any advise ):P

You are welcome, any reason why you did the Kernel upgrade? Also what IGP are you using btw?

---

### Post by VMC on 2009-05-18
> **dicairo said:**
> how do i know that i am using xorg 1.6 ? and i didn't tell u that i am using this kernel 2.6.29.3-candela is this a problem ?2.6.29.3-candela
Below will tell you everything installed regarding Xorg:
```
dpkg -s xorg
```

or 

```
dpkg -s xorg|grep Version
```

---

### Post by alphaniner on 2009-05-18
Has anyone tried this on an Intel D945GCLF board?  I had already updated to the latest stable Xorg drivers when I came across this guide.  I don't think that would have had any bearing on the problems I ran across but I figured I'd mention it.

I added the lines to my xorg.conf and did the workaround for the MTRR bug.  I did a warm boot and made it to the greeter.  After entering my login info the screen flickered a bit then I was back to the greeter.  Another login attempt yielded the same result.  So I logged in via a terminal and commented out the first of the new lines in xorg.conf.  After that I was able to login successfully.  I then started up FF and Deluge then left the machine otherwise idle for about an hour.
When I returned to the machine to do some troubleshooting, I noticed that the screen was intermittently 'fuzzy' after a few minutes of activity.  Then the NB fan started spinning faster than I had ever heard it before.  I disabled all the xorg.conf changes then restarted X, but the fuzziness remained.  So I removed the MTRR workaround and did a warm boot.  The fuzziness was still there after a restart, but eventually went away.  My best guess is that the NB/VPU was starting to overheat.

---

### Post by psyke83 on 2009-05-19
> **alphaniner said:**
> Has anyone tried this on an Intel D945GCLF board?  I had already updated to the latest stable Xorg drivers when I came across this guide.  I don't think that would have had any bearing on the problems I ran across but I figured I'd mention it.

I added the lines to my xorg.conf and did the workaround for the MTRR bug.  I did a warm boot and made it to the greeter.  After entering my login info the screen flickered a bit then I was back to the greeter.  Another login attempt yielded the same result.  So I logged in via a terminal and commented out the first of the new lines in xorg.conf.  After that I was able to login successfully.  I then started up FF and Deluge then left the machine otherwise idle for about an hour.
When I returned to the machine to do some troubleshooting, I noticed that the screen was intermittently 'fuzzy' after a few minutes of activity.  Then the NB fan started spinning faster than I had ever heard it before.  I disabled all the xorg.conf changes then restarted X, but the fuzziness remained.  So I removed the MTRR workaround and did a warm boot.  The fuzziness was still there after a restart, but eventually went away.  My best guess is that the NB/VPU was starting to overheat.

If anything, the MTRR workaround should reduce CPU usage (and therefore heat). It's likely that UXA acceleration was causing problems for your chipset. Keep the AccelMethod to exa, but keep the other tweaks, as they will most likely improve EXA performance.

You can monitor your temperatures with sensors-applet, if you wish to test your hypothesis.

---

### Post by bobe84 on 2009-05-19
I have D945GCLF, using xorg-edgers ppa and kde 4.2.3
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "exa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "true" 
EndSection

```
Works actually very good if u have <10 windows.
I hope performance will increase much more otherwise this motherboard is going to be used for network storage and video surveilance. :p
Im not saying that performance is bad though, because i personally started to track performance of xorg-edgers about 1.5 months ago and it improved about 3x no more glitches and lockups. There is some text corruption though i dont know why. This was tested on GMA 950 and X3100. (X3100 and KDE 4.2.3 wow even on 1680x1050)

---

### Post by dicairo on 2009-05-19
> **Arup said:**
> You are welcome, any reason why you did the Kernel upgrade? Also what IGP are you using btw?
i upgraded because i think its good thing having the last stable kernel and also i did it  to have better 3d operation (my only problem) and the xorg version is 1:7.4~5ubuntu18 and if for IGP u intend which hardware i use , is Intel Graphics media Accelerator X3100 thanks again

---

### Post by psyke83 on 2009-05-19
> **bobe84 said:**
> I have D945GCLF, using xorg-edgers ppa and kde 4.2.3
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "exa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "true" 
EndSection

```
Works actually very good if u have <10 windows.
I hope performance will increase much more otherwise this motherboard is going to be used for network storage and video surveilance. :p
Im not saying that performance is bad though, because i personally started to track performance of xorg-edgers about 1.5 months ago and it improved about 3x no more glitches and lockups. There is some text corruption though i dont know why. This was tested on GMA 950 and X3100. (X3100 and KDE 4.2.3 wow even on 1680x1050)

The performance of the Intel drivers also depend on the kernel version you're using (due to the kernel-side drm/i915 changes). For my hardware, the stable 2.6.29.3 works best at the moment.

Also, note that the xorg-edgers drivers aren't necessarily the fastest (hint: I gave the "Optimal" configuration its name for a reason).

---

### Post by galv on 2009-05-19
> **galv said:**
> Can anybody give me a recommendation of the best method for a EEEPC 1000H user?
```
 lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)

```

Thanks

Any thoughts on this question?

Thanks.

---

### Post by psyke83 on 2009-05-19
> **galv said:**
> Any thoughts on this question?

Thanks.

The recommendation for you is no different than anybody else. Try Optimal, and if you have problems with the kernel, revert to the official Jaunty kernel (the equivalent of Safe).

---

### Post by alperyilmaz on 2009-05-19
People who are experiencing freezes and hard-boots can try this method so that data loss is minimal.

Start with the Ctrl + SysRq + R key combo. Wait a few seconds and press the Ctrl + SysRq + E key combo. Continue with the remaining I , S , U and B keys making sure to wait a few seconds between each key combo. These key combinations stand for:
Raw (take control of keyboard back from X)
tErminate (send SIGTERM to all processes, terminate gracefully)
kIll (send SIGKILL to all processes, terminate immediately)
Sync (flush data to disk)
Unmount (remount all filesystems read-only)
reBoot

(taken from [http://tazbuntu.blogspot.com/2008/05/magic-sysrq-key.html](http://tazbuntu.blogspot.com/2008/05/magic-sysrq-key.html))

---

### Post by povvy on 2009-05-19
Intel 965 here: does anyone experience slighlty better performance in 2.6.30 rc2 than in the following rc's? In my case 2d performances are REALLY decreasing...

---

### Post by psyke83 on 2009-05-19
> **povvy said:**
> Intel 965 here: does anyone experience slighlty better performance in 2.6.30 rc2 than in the following rc's? In my case 2d performances are REALLY decreasing...

Different chipset, but...

The 2.6.29.3 and 2.6.30-rc2 kernels give the best performance for me (not much different between the two). Kernel 2.6.30-rc3 and beyond all exhibit performance regressions for my 855GM chipset. The latest xorg-edgers drivers also slowed things down slightly.

---

### Post by psyke83 on 2009-05-20
Bleeding-Edge users,

I've updated the guide to fetch the -rc6 kernel, if you're interested.

---

### Post by povvy on 2009-05-20
rc6 gives me the same performance regression as rc3-4-5 :( does anyone know why?

---

### Post by psyke83 on 2009-05-20
> **povvy said:**
> rc6 gives me the same performance regression as rc3-4-5 :( does anyone know why?

Quite simply, there are still many issues with the latest drivers/DRM code. It may take some more time for things to stabilize with the bleeding-edge code, so try the stable drivers/kernel. The 2.6.29.3 kernel is just as fast as 2.6.30-rc2 for me.

---

### Post by jbernardo on 2009-05-20
rc6 fixes the problems I was having with bluetooth (kernel panics) so it is great for my aspire one. I rebuilt it with a small variation from kuki linux's kernel configuration, and now my A1 boots in less than 20 seconds, suspends with /home on a sd card without problems, and has finally half-decent video performance. And with last night's xorg-edgers drivers, UXA performance in glblur is up to 24fps, nearly on par to the max I had in intrepid with EXA (30fps). Google Earth is almost usable under kde4 with compositing on, the screen corruption is gone, it is just very slow updating the globe.

---

### Post by povvy on 2009-05-20
@psyke83

unfortunately it is not that simple: i'm having good performance with rc2 and safe intel drivers (not xedgers ones); any other kernel i've tried gives me the same, poor, performance (even 2.6.29); it seems for me that the improvements cited in phoronix about 2.6.30 are gone with rc's later than rc2 :(

---

### Post by psyke83 on 2009-05-20
> **povvy said:**
> @psyke83

unfortunately it is not that simple: i'm having good performance with rc2 and safe intel drivers (not xedgers ones); any other kernel i've tried gives me the same, poor, performance (even 2.6.29); it seems for me that the improvements cited in phoronix about 2.6.30 are gone with rc's later than rc2 :(

Have you tried to disable tiling? Although tiling is supposed to give a considerable performance boost, it's currently buggy on my chipset and actually halves 3D performance (e.g. ppracer gives 15fps when tiling is enabled, vs 30fps with tiling disabled).

Conversely, if you already have tiling disabled, enabling it may provide a performance boost for your particular chipset.

---

### Post by povvy on 2009-05-20
it's the same, with or without tiling enabled :( by the way, i own a GM965/GL960

---

### Post by zevans on 2009-05-20
> **povvy said:**
> it's the same, with or without tiling enabled :( by the way, i own a GM965/GL960

Povvy, looked at your other posts and couldn't figure out whether you are on UXA or EXA. Performance regressions are now quite different between the two, and caused by different things.

---

### Post by povvy on 2009-05-20
u're right :) i'm using uxa

---

### Post by alperyilmaz on 2009-05-20
Hi, When I installed the Jaunty initially everything was working fine. Then update-manager told me couple days ago there was xorg package update and I went ahead and did the update. Then I started having random freezes in the system. 

I stumbled upon this forum to solve the problem and tried the "Safe" option. 
Initially, I didn't have /etc/X11/xorg.conf file(*) but when I did sudo apt-get dist-upgrade then I got a standard xorg.conf file and then I added the Device options into it. However, when I look into Xorg log, I see that the options are not accepted.

(WW) intel(0): Option "AccelMethod" is not used
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used

The log file says UXA method is used for accelaration though:
(--) intel(0): Using UXA for acceleration


Full contents of Xorg.log can be found [ **here.**]("http://alper.pastebin.com/m1894c7d1")
Isn't UXA supposed to solve freeze problems? What am I doing wrong here?

-------------------------------
Information about my system:

```
$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
```

My xorg.conf file (all of it!):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" # i8xx users: set to false - i'm not sure if i'm i8xx (**)

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
```


-------------------------------
(*) where's the config file located now, I read it's xml format, but where?
(**) lsmod tells me that drm is using i915 module, does it mean I'm not i8xx ?

---

### Post by densou on 2009-05-20
2.6.29.4 is out ):P I think it'll be uploaded on Kernel PPA within tomorrow ;)

Has anyone tried Mesa 7.4.2 (bugfixing release) ? I wonder if debs are already avaiable somewhere :KS

---

### Post by Seishuku on 2009-05-20
Man, I did everything I could find to fix driver issues (including reverting to 2.4, which actually worsened performance), but my system still can't properly render 3d.  The only 3d game I can play well is planet penguin racer. =/

Interestingly enough, the PlaneShift that refuses to render entirely works perfectly on my Windoze XP partition.  I just hate booting into it.

---

### Post by psyke83 on 2009-05-20
> **alperyilmaz said:**
> Hi, When I installed the Jaunty initially everything was working fine. Then update-manager told me couple days ago there was xorg package update and I went ahead and did the update. Then I started having random freezes in the system. 

I stumbled upon this forum to solve the problem and tried the "Safe" option. 
Initially, I didn't have /etc/X11/xorg.conf file(*) but when I did sudo apt-get dist-upgrade then I got a standard xorg.conf file and then I added the Device options into it. However, when I look into Xorg log, I see that the options are not accepted.

(WW) intel(0): Option "AccelMethod" is not used
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used

The log file says UXA method is used for accelaration though:
(--) intel(0): Using UXA for acceleration


Full contents of Xorg.log can be found [ **here.**]("http://alper.pastebin.com/m1894c7d1")
Isn't UXA supposed to solve freeze problems? What am I doing wrong here?

-------------------------------
Information about my system:

```
$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
```

My xorg.conf file (all of it!):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" # i8xx users: set to false - i'm not sure if i'm i8xx (**)

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
```


-------------------------------
(*) where's the config file located now, I read it's xml format, but where?
(**) lsmod tells me that drm is using i915 module, does it mean I'm not i8xx ?

You probably followed the Bleeding-Edge configuration by accident (or were testing the Xorg-edgers repository before getting here). This guide assumes that you're using the regular Ubuntu version of everything when you begin, but this isn't true on your system. Those Xorg configuration warnings suggest that you are using the latest bleeding-edge driver which now only supports UXA acceleration. If you read the text of guide, you'll see that latest is not always greatest.

Follow the instructions to revert changes (make sure you're using the oficial Jaunty packages), and try again.

---

### Post by kwaanens on 2009-05-20
Subscribing to thread the hard way because Ubuntuforums will not cooperate today. Annoying!

---

### Post by lethalfang on 2009-05-20
The graphics performance is **woeful** in my dated Dell Dimension 3000 (Pentium 4), even without compiz, but it wasn't that way with Intrepid. Xorg is routinely using up 100% of my CPU.
I've tried the "safe configuration" from the OP, and the problem remains and might be even worse. From changing tabs on Firefox to changing workspace, takes many seconds to complete such a process. 

How do I go back to Intrepid video drivers?

---

### Post by psyke83 on 2009-05-20
> **lethalfang said:**
> The graphics performance is **woeful** in my dated Dell Dimension 3000 (Pentium 4), even without compiz, but it wasn't that way with Intrepid. Xorg is routinely using up 100% of my CPU.
I've tried the "safe configuration" from the OP, and the problem remains and might be even worse. From changing tabs on Firefox to changing workspace, takes many seconds to complete such a process. 

How do I go back to Intrepid video drivers?

You can't simply use the Intrepid drivers directly, as they're built against an older X server.

See the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards") for information on using an older driver rebuilt against Jaunty's X server.

P.S. Revert all changes from this guide beforehand, and this thread isn't the place to ask for help with the older driver.

---

### Post by mikemcginn on 2009-05-20
I have a Dell Inspiron 1545 laptop with an intel graphics chip. I followed the "safe" instructions and ended up with a black screen. I reverted my xorg.conf and my /etc/apt/source.list and updated. I restarted X and did some checking. I found that just running /usr/local/bin/fixmtrr.sh had fixed most of my painting problems. I decided to experiment with xorg.conf with the settings detailed in the instructions. When I did get X to start, one of my cores was eunning at 100% all the time, so I gain reverted xorg.conf. So most of my painting problems are solved with /usr/local/bin/fixmtrr.sh and the default xorg.cong. Interesting.

---

### Post by businessgeeks on 2009-05-20
Thnks for this guide. i just want to ask if the GL screensavers built into ubuntu is a good benchmark of improvements? 

It seems i didn't have any issues with my Intel graphics adapter when I initially installed jaunty. I used the Gl based screensavers as a reference and they seem pretty quick for me. (Im using a Intel 915G).

After doing the safe configuration stated in this guide, the rendering performance of the screensavers actually suffered so I had to revert back to the old configuration which was the default install of jaunty.

I find it really weird because the first time i used jaunty on my thinkpad x41 laptop, i had these Intel graphics problems however, the second time i installed, none of the problems manifested.

The only difference was that the first time i installed, the laptop was not plugged into the network and the second time was plugged into the network...

weird....

---

### Post by Arup on 2009-05-20
A good way to benchmark is to run Google Earth, if it runs smoothly then you are all set.

---

### Post by LifeTheHound on 2009-05-21
Turns out UXA is much slower than EXA greedy with all xorg/driver/kernel setups on my eee pc 1002HA (945gm chipset). 

Odd huh?  It's also a bit more glitchy with transparency in compiz.

---

### Post by cyper on 2009-05-21
Hi again!
I'm using MSI S262 notebook. My best configuration is rc5 kernel with latest Bleeding-Edge drivers (yes - rc6 worked slower and i got rid of it :?: ). Also I turned off greedy MigrationHeuristic. Rest of options are according to this HOW-TO.
Result - performance is almost the same as in Hardy ;) Though I might be not absolutely correct. I didn't benchmark it.

---

### Post by kwaanens on 2009-05-21
> **cyper said:**
> Hi again!
I'm using MSI S262 notebook. My best configuration is rc5 kernel with latest Bleeding-Edge drivers (yes - rc6 worked slower and i got rid of it :?: ). Also I turned off greedy MigrationHeuristic. Rest of options are according to this HOW-TO.
Result - performance is almost the same as in Hardy ;) Though I might be not absolutely correct. I didn't benchmark it.

I have the exact same laptop. I'm using the "optimal" solution. The main problem has been super slow cursor with the x-swat synaptics version, so I'm holding back on the default synaptics version.
Is there anything I should know about our laptops before I decide to switch to the bleeding edge solution? Do you have any problems at all? Suspend and hibernate works?

---

### Post by DavidKelly999 on 2009-05-21
Following these steps caused my touchpad to freeze and stutter, basically making it unusable. I had to revert back.

---

### Post by kwaanens on 2009-05-21
> **DavidKelly999 said:**
> Following these steps caused my touchpad to freeze and stutter, basically making it unusable. I had to revert back.

Mine too, but I solved it by holding back xserver-xorg-input-synaptics to version 0.99.3-2ubuntu4

- K

---

### Post by TpyKv on 2009-05-21
Pat on the back for you sir, looking forward to trying this out!

---

### Post by JJRules on 2009-05-21
Great guide, increased my graphics performance significantly.  I'm curious though, has anyone been getting occasional corrupt characters on screen?  After my laptop has been running a while, I sometimes get a random character corruption, say the Vs in Firefox turn into something that looks like jagged Ws.  Disappears after I restart X and seems to happen randomly.

---

### Post by R Clemons on 2009-05-21
Great guide, worked flawlessly for me and I'm getting smoother video than I did with previous releases

---

### Post by psyke83 on 2009-05-21
> **JJRules said:**
> Great guide, increased my graphics performance significantly.  I'm curious though, has anyone been getting occasional corrupt characters on screen?  After my laptop has been running a while, I sometimes get a random character corruption, say the Vs in Firefox turn into something that looks like jagged Ws.  Disappears after I restart X and seems to happen randomly.

Yes, I noticed that too - it's a UXA bug, I think, and it happens only after a few hours of X uptime on my system. I read a post from Sarvatt somewhere that the bug was identified and getting fixed, but I don't have the link/bug report handy right now.

---

### Post by Pauly Psychotic on 2009-05-21
Thank you for the fix I tried the *Safe* settings and I'll see if that boosted the performance or not if it doesn't then I will try the next step. ):P:p

---

### Post by Murrquan on 2009-05-21
I set things up for "Optimal," and they worked great! Extreme Tux Racer didn't even work on my notebook before, and it does now at around 16 FPS.

Sadly, the Linux client for Second Life and modern Windows games still will not run. >.>

---

### Post by kwaanens on 2009-05-22
> **psyke83 said:**
> I've noticed corrupted fonts in Firefox after several hours uptime when using the latest drivers from Xorg-edgers - Karmic Koala alpha testers seem to suffer from the issue too. My suggestion is that you only stick to the Safe or Optimal configuration.

I'm now having corrupted fonts in Firefox with the optimal configuration. Arrgh.

---

### Post by jbernardo on 2009-05-22
Well, running 2.6.30-rc6 with KMS enabled by default, and xorg-edgers packages, I now get 24 fps in glblur with UXA, and things all seem snappy. I have sometimes a blank screen when logging out, but it seems that today's mesa update fixed that. My aspire one is snappier than ever, and kde 4.2.3 looks great here. No corruption, no longer the strange flashing I got at times, everything working and moderately fast. As good as intrepid, not as fast as hardy yet.

The only strange thing is that with KMS enabled the intel driver ignores the "NoDDC" option, but I can just set font DPP in kde to 96 and the screen looks right again.

---

### Post by dicairo on 2009-05-22
Hi every body i tried many work arounds but unfortunately nothing worked for  me  , so i turned back to ubuntu 8.10 and every thing is perfect now and i am looking forward for ubuntu 9.10 ;)

---

### Post by c0nfusedami on 2009-05-22
when I performed all the steps in this guide i started up my computer and got only a black screen instead of my normal memory issue and low graphics mode. I had to run a live cd start up nautilus and change the xorg.conf file back to the way it was. Any idea why?

---

### Post by jerrylamos on 2009-05-22
> **kwaanens said:**
> I'm now having corrupted fonts in Firefox with the optimal configuration. Arrgh.

With i830 on IBM Thinkpad R31 fonts corrupt/characters smear on jaunty in a few minutes as of yesterday's update with everything mentioned in the Performance Guide.  gtkperf is pretty slow at 50.  That's jaunty with xorg-xserver-video-intel 2:2.7.1-1

I've never seen intrepid to smear fonts on the Thinkpad so it is dual boot because jaunty is nearly useless.  I use intrepid to do anything, jaunty only to see the problem still exists.  Yes, there's a launchpad bug on the i830 font smears; no action that I've seen.

i845 on this IBM ThinkCentre tower where today's 2.7.2-1 on karmic is running the fastest I've seen on this pc, at 26.7.  This pc is not a particularly good performer for 2 ghz so slowdowns/speedups are really noticeable.  Do note /etc/X11/xorg.conf is an empty file so all defaults are being hidden from us.  I presume I could boot in recovery and select the option which restores xorg.conf, however that will wait until such time as it breaks.

Wednesday's gtkperf was 31 on the i845.  I do have a Compaq tower that got about 10 with ati radeon video graphics.
  
Jerry

---

### Post by c0nfusedami on 2009-05-22
After making a second attempt at fixing my integrated memory I discovered that my computer was unable to find the launchpad site and therefore not able to download the package any ideas

---

### Post by c0nfusedami on 2009-05-22
oops spelling error I'm good

---

### Post by davdi on 2009-05-22
Hello,

I followed the howto with the optimal setting.
However, 3d perf is still very slow. (extremetuxracer is not playable and do not obey the show fps option)

Moreover, I experience some annoyances with the mtrr fix :
- closing the kde session gives a black screen : I never reaches back the kdm login screen. I have to use the magic keys or the hard reset to reboot.
- on another machine with the safe settings, xbmc crashes each time I stop a video (it also gives a temporary black screen before returning to kde)

If I do not execute fixmtrr.sh, then both problems are resolved.

Any ideas / hints ?

Tx

David

Here's my xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"           "uxa"
        Option          "EXAOptimizeMigration"  "true"
        Option          "MigrationHeuristic"    "greedy"
        Option          "Tiling"                "true"
EndSection

Here's my uname -a
Linux cagouille 2.6.29-02062903-generic #02062903 SMP Mon May 11 14:20:34 UTC 2009 i686 GNU/Linux

I have integrated fixmtrr.sh using /etc/kde4/kdm/Xstartup

Here's my lspci -v00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Sony Corporation Device 81ef                                                                               
        Flags: fast devsel                                                                                                    
        Memory at 8c000000 (32-bit, non-prefetchable) [disabled] [size=512K]                                                  
        Capabilities: [d0] Power Management version 2

---

### Post by davdi on 2009-05-22
with the fps in extremetuxracer :
exa : 4+ fps
uxa : 5- fps
uxa + fixmtrr : 5+ fps

This game used to be smooth 2 years ago !

---

### Post by davdi on 2009-05-22
In bleeding edge, I get a 25fps.
fixmtrr.sh is not needed anymore (it reports that correct range are already setup).
+ it fixes my 'close session' problem.
=> all problems fixed for my laptop !

However I cannot use that fix with my multimedia box because I depend on atheros and ath5k is not working for me.

Tx !

---

### Post by Orographic on 2009-05-23
Wow, great stuff. I have a Gigabyte 945GZM-S2 board with intel on board graphics. The Safe approach worked great for me. Before I found this thread my full screen on iView was awful, now its great. Will report back on how it works out in the longer term.

I have my original settings backed up via an image from Clonezilla.

Thanks for the hard work put into this thread.


Edit: I can't seem to find where to edit my profile to change my OS to Jaunty instead of Intrepid...fixed now.

---

### Post by cravidousa on 2009-05-23
I tried the bleeding-edge configuration and everything went smooth and snappy.

Just one thing that was not working. My Broadcom STA wireless card. It says that the driver is activated and currently in use. But my laptop couldn't detect my any wireless network..  I tried to downgrade the kernel to optimal configuration and everything went alright again.

Is there any way I can use the bleeding edge configuration and still having my wireless card working?

---

### Post by jsday187 on 2009-05-23
I don't know about the Broadcom user, but the atheros user two posts back can compile his own driver so he could use the newer 30rc6 kernel and his wireless together. 

Here a link to a page that explains the process in a very easy to perform way:

[http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html](http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html)

---

### Post by SteveMcQwark on 2009-05-23
> **jbernardo said:**
> Well, running 2.6.30-rc6 with KMS enabled by default, and xorg-edgers packages, I now get 24 fps in glblur with UXA, and things all seem snappy. I have sometimes a blank screen when logging out, but it seems that today's mesa update fixed that. My aspire one is snappier than ever, and kde 4.2.3 looks great here. No corruption, no longer the strange flashing I got at times, everything working and moderately fast. As good as intrepid, not as fast as hardy yet.

The only strange thing is that with KMS enabled the intel driver ignores the "NoDDC" option, but I can just set font DPP in kde to 96 and the screen looks right again.

rc6 doesn't have font corruption?

---

### Post by jbernardo on 2009-05-24
> **SteveMcQwark said:**
> rc6 doesn't have font corruption?

Nothing yet, might be because I am running it with KMS enabled.

---

### Post by keypox on 2009-05-24
seems like 4500 just sucks.  Getting worse than the poster.  With new morden computer.

---

### Post by psyke83 on 2009-05-24
> **jbernardo said:**
> Nothing yet, might be because I am running it with KMS enabled.

I still get corruption. I also run Karmic with kernel 2.6.30-6-generic, and it gives the same problem (with or without xorg-edgers drivers). It usually takes a few hours to manifest itself, though, and restarting X always solves the issue.

The bug should be fixed soon, hopefully.

---

### Post by densou on 2009-05-24
RC7 out! ):P


one i915 fix only: _*[Bug 13165]("http://bugzilla.kernel.org/show_bug.cgi?id=13165") -  2.6.30-rc3 : Regression: i915 , video*_

but rather important, imo :KS

---

### Post by jbernardo on 2009-05-24
> **psyke83 said:**
> I still get corruption. I also run Karmic with kernel 2.6.30-6-generic, and it gives the same problem (with or without xorg-edgers drivers). It usually takes a few hours to manifest itself, though, and restarting X always solves the issue.

The bug should be fixed soon, hopefully.

After 6-7 hours I got font corruption. Not in firefox (was closed at the time) but in konsole. Will now build rc7 with my config to see how it goes.

---

### Post by cloudraven on 2009-05-24
Did wonders for my inspiron 640m, went from 10-12 to 25-30, funny enough that was for safe, optimal actually made it worse (8), and I didn't try bleeding edge.
It feels like in intrepid again, great article

---

### Post by knievel84 on 2009-05-24
I am trying to do the udates in this post on Kubuntu 9.4, but I can't get past the first step. When I run 'sudo kate /ect/X11/xorg.conf' I get the following output:

Error: "/var/tmp/kdecache-knievel" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-knievel" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-knievel" is owned by uid 1000 instead of uid 0.
QThreadStorage: Thread 0x8aaab48 exited after QThreadStorage 2147483641 destroyed

I have looked through many forums, but I cant' find one that addresses this problem. Does anyone have any ideas as how to fix this problem.  Thank you

---

### Post by jmp on 2009-05-25
Thanks a lot!!!
I followed the safe mode and my pavillion dv2000 with i915 is working great

---

### Post by AlphaMack on 2009-05-25
Been following the thread for quite some time but was lurking until I made sure everything was working reliably...

FWIW.  ThinkPad R61i with the GM965 and AR5212 chipsets...

Stock Jaunty:  Video performance was abysmal even with Compiz disabled.  Tried the 'greedy' option with no improvement.  Tried downgrading the driver as suggested in the Wiki and bug reports only to get worse performance.  Xorg was eating about 30% of the CPU at any given time.  Idle temps were ~70C.  Add to all that, Jaunty kept locking up (flashing Caps and all) which I later traced to madwifi (and no simple way to undo it in favor of ath5k).  I was so frustrated that I was ready to wipe Jaunty for Hardy again at the cost of losing a year's worth of application improvements.

Safe:  No improvement.

Optimal:  Madwifi wasn't an issue for me, so no complaints about losing restricted drivers.  Ath5k actually performs better with the 2.6.29 kernel (perhaps a false improvement only perceived by me).  No more kernel panics.  Dramatic improvement with graphics.  Compiz can actually be enabled without tearing and slow all-around performance.  CPU temps are actually lower than what they were in Hardy - ~50C while idle.  Google Earth needs atmosphere disabled but can otherwise play well with Compiz.

The only catch was having to recompile ALSA 1.0.19 with the Conexant patch (to get back a working microphone).  Otherwise, this is what Jaunty should have been...

I ended up dumping the stock Jaunty kernel from my system and leaving the 2.6.29 kernel as the only boot option because it dramatically improved my system all around.

Even with the optimal config, I too suffer from the garbled font issue.  I can reliably reproduce the condition by reverting from Compiz to Metacity or by switching users and back.

Now to do something about Pidgin (still goes south even with 2.5.6)...

YMMV.

---

### Post by svQuick on 2009-05-25
Bingo- Dell inspirion b130 has this chipset and this is a quick fix.  running optimal, still a little slow but certainly tolerable.  Thanks.

---

### Post by ferossan on 2009-05-25
Anyone using the new 2.6.29.[COLOR="Red"]4[/COLOR] Kernel for "Optimal"? Does it worth?

---

### Post by oleg77 on 2009-05-25
acer 5620z with x3100, kubuntu jaunty

had config:
  BoardName "965 GM"                     
  VendorName "Intel"                     
  Driver "intel"                         
  Option "AddARGBGLXVisuals" "True"      
  Option "XAANoOffscreenPixmaps" "true"  
  Option "DRI" "true"                    
  Option "AccelMethod" "EXA"
  Option "NoAccel" "False"
  Option "MigrationHeuristic" "greedy"

glxgears ~700fps, ppracer ~25
had trable with icons in tray

After "safe" patch have badly result:
glxgears <600fps, ppracer ~20
and have trable - after logout from kde, have blackscreen, keyboard and mouse don't work.
Work only button "power off".
But with this config I don't have trable with icons in tray.

---

### Post by caish5 on 2009-05-25
I've been following the optimal path since rc5.
With rc5 i had tearing video in windows but finally could manage tear free fullscreen. I was excited to say the least!!
Now with rc6 and rc7 the tearing is back all the time.
Is this something i should bug report or is it a known thing?
I'm using..
> Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)

---

### Post by markbl on 2009-05-25
> **jbernardo said:**
> After 6-7 hours I got font corruption. Not in firefox (was closed at the time) but in konsole. Will now build rc7 with my config to see how it goes.
I'm a developer and have reported the same here earlier. I can sit in gnome-terminal all day and have seen after about 5 hours that my terminal window fonts can start getting corrupted and my machine slows down. This is on all kernals up to rc6. I'll try rc7 now and see how it goes but not expecting much difference.

---

### Post by gillouz on 2009-05-25
Hello 

I use Kde4 and need to type: $ sudo fixmtrr.sh

so I did the following thing:

I mad a little C programme

```

#include <stdio.h>

int main(void)
{
system("fixmtrr.sh");
return 0;
}

```

saved it under : fixmtrr.c 
compile it:

$ Developpement$ gcc -o fixmtrr fixmtrr.c

then change owner to root 
give it the bit sticky 
give everyone the right to execute

so this little programme can make "sudo fixmtrr.sh" without the sudo.
then you can execute it automatically when KDE starts (in the control pannel)

I don't know if anyone had find a solution for Kde I did not find the strenght to read 51 pages of messages...;)

---

### Post by meganox on 2009-05-25
Just a heads-up.

After applying these changes on my Advent 6001 915GM laptop, performance was considerably *worse*.

Then I noticed my user created during install had not been added to group 'video'.

use "$ grep video /etc/group" to check you are in group video.

use "$ sudo adduser <username> video" to add you if necessary.

---

### Post by kwaanens on 2009-05-25
My user wasn't either in the video group. Which effect should this have had?

---

### Post by magic_k on 2009-05-25
I tried the "safe/optimal" way by updating x and drivers and enabling uxa under kernel 2.6.28.11. I wanted to get rid of the tearing in videos on my Toshiba NB100 netbook but the result was worse than before. UNR was unusable sluggisch. After changing back to exa the netbook is usable again.

Anyone an idea whats happening there? Upgrading the kernel seems not possible as theres no lpia kernel.

---

### Post by hiikeeba on 2009-05-25
I updated an older system to Jaunty from 8.10.  The graphics are not working.  No application has a title bar, minimize, maxize, or close button; Totem will play a movie, just not display the video--only a black screen; terminal is a simple white square that cannot be typed in.  Any advice?

---

### Post by AlphaMack on 2009-05-25
> **ferossan said:**
> Anyone using the new 2.6.29.[COLOR="Red"]4[/COLOR] Kernel for "Optimal"? Does it worth?

I just upgraded.  Had to recompile ALSA (running a patch) but other than that no harm no foul.

Prior to that, I experienced the font corruption yet again after my crummy battery discharged and sent my machine to hibernation.  When I woke it up, Firefox and Thunderbird both had garbled text.  Restarting X as others reported resolved the issue.

I doubt that the kernel upgrade will do anything for the font corruption as I'm pretty sure this is more of an issue with X and the driver.

---

### Post by malangbaba on 2009-05-26
hey. Using the Simple option got my flash video working better.

My computer has slowed down a little, and my touchpad is little more jerky (moreso when using small distances - but fine for major movements).

I wanted to see if I need to tweak MTRR

> sarfarosh@sarfarosh:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x01f700000 (  503MB), size=    1MB, count=1: uncachable
reg02: base=0x01f800000 (  504MB), size=    8MB, count=1: uncachable
reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining


> 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 1800 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>


Whats my base memory address, and whats the memory size for fixmtrr.sh?

Help would be appreciated

---

### Post by anipet on 2009-05-26
A big THANK YOU from México :)

My Toshiba Satellite is much more responsive and faster on visuals now, and talk about easy to follow! really an awesome work on your procedure :)

-Fer-

---

### Post by TedCarnahan on 2009-05-26
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Works for me only with the Bleeding Edge instructions - that is, requires kernel rc7, latest X.org drivers, and fixmtrr.sh script.  But performance is, subjectively speaking, back up to Intrepid's standards.  Thank you!

---

### Post by Venter127 on 2009-05-26
This seems to be solution I was looking for, since my 3d graphics run at about half the speed theyre supposed to. Id love to be able to update my graphics card, but Im new to ubuntu, and getting errors on Step one. I open the xorg conf. file and nothing is there in the terminal. It also opens up the file in a seperate window, but it is also blank. Do I not have any xorg files, and if so, where and how do I get them? Due to my ametur status with linux, half of the explanations on how to get the drivers installed I cant understand for the life of me. I apologise for any inconvience, but I need a bit of a down-to-earth explanation of how to get it to work.

---

### Post by SeaJey on 2009-05-26
>  ... I mad a little C programme ... 
For me It's unnecessarily complex solution.

Just launch System Settings -> Advanced tab -> Autostart -> Add Script -> choose fixmtrr.sh and Run On - Startup

And thats all -- after reboot for assurance I've manually did:
```
$ fixmtrr.sh
Extracing base address and memory size from lspci -v
d0000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
doing nothing, MTRR range already set up
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining
```

---

### Post by Lord Quinny on 2009-05-26
Thankyou so much. I did the Optimal install and got the graphics working better!

glxgears went from about 250 fps to about 1200 fps.

Games and screensavers were a notible improvement (except for the Helios screen saver, that one is still jerky).

---

### Post by psyke83 on 2009-05-26
> **SeaJey said:**
> For me It's unnecessarily complex solution.

Just launch System Settings -> Advanced tab -> Autostart -> Add Script -> choose fixmtrr.sh and Run On - Startup

And thats all -- after reboot for assurance I've manually did:
```
$ fixmtrr.sh
Extracing base address and memory size from lspci -v
d0000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
doing nothing, MTRR range already set up
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining
```

No, that won't work. The fixmtrr.sh script needs to be executed with root privileges, and GNOME Startup entries are executed with user privileges.

The script isn't working on your system, but you perhaps mistakenly think it is. The 2.6.29.* and 2.6.30-rc* kernels set the write-combining range correctly, but only the first time the X server is started. If you restart your X session, the write-combining range will disappear. Try it if you don't believe me.

---

### Post by SeaJey on 2009-05-26
> The script isn't working on your system, but you perhaps mistakenly think it is. The 2.6.29.* and 2.6.30-rc* kernels set the write-combining range correctly, but only the first time the X server is started. If you restart your X session, the write-combining range will disappear. Try it if you don't believe me.

Did not know this will check it.

---

### Post by davdi on 2009-05-26
You can also edit /etc/kde4/kdm/Xstartup and add a call to fixmtrr.sh straight at the beginning.

---

### Post by cocolocko on 2009-05-26
So now also with replay from me :D

I made the Optimal Configuration with Kernel update and everything works fine on my Toshiba A9 with GM965 / X3100 Graphiccard.
The compiz eye candys i activate with this nice blog: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

so on, thanks to everybody :popcorn:

Greetings

---

### Post by reverend_nerd on 2009-05-26
Hello,

I followed the instructions to Optimal config, but I got a set back.
I'm using Linux Mint 7, a distro that is heavily based in Ubuntu and inherits it's design and code benefits and flaws.
Along with the ride came the problem with the slow performance in Intel Graphics. I found this post with the instructions I followed through the letter.

The graphic performance is quite all right, however, I've been recently facing problems with font characters and icons in certain apps.

Describing the problem is somewhat funny, I guess it's the X, that is printing the wrong fonts in the screen and them messes up everything. For example, the letter "X" itself right now is deformed, like the part of a bigger X.

Has anyone faced a similar bug? should I revert the config and try again? or is there a fix? like, downgrading my fonts?

Cheers!
Felipe Sentelhas

---

### Post by andyprough on 2009-05-27
Thanks for the how-to! I installed Ubuntu with wubi as a large file on a Vista 32-bit system, and I was getting horrible graphics performance. I thought the problem was with using the Windows file, instead of a dedicated partition, and thought I would have to go in and re-install with a partition setup. However, I found this how-to first, and with a little tweaking I got it running just right.

I've got two monitors running off of my Acer laptop, with Intel 945GM/GMS integrated graphics. I found the UXA did not work with the Intel chipset and the large screen sizes I wanted to use on the two monitors, so I commented out UXA, EXAOptimizeMigration, MigrationHeuristic and tiling. The only way to work with UXA and the Intel chipset seemed to be to settle for much smaller screen sizes. It is possible that there is a simple fix to get UXA and Intel working together on larger screen dual monitors, but I could not find it in my limited research. I would have tried configuring Xinema settings in xorg.conf, but this how-to got me working.

I installed the new kernel under the Optimal method from this how-to, and employed the fixmtrr script. I also increased the Virtual display size to 3000 960 in xorg.conf in order to accomodate my two large screens. Gnome seemed to try to fight me the first  time I logged in, but after a reboot it started working perfectly.

The only trouble I've seen is that the system has locked up twice. Each time it locked up I was exiting a program, and trying to quickly start a gnome setting app. I don't know if the lock-ups are related to the graphics card, but I figure it is likely. However, the simple fix for now is to allow a few seconds for programs to exit before trying to start a gnome configuration gui.

---

### Post by scarf on 2009-05-27
> **Venter127 said:**
> This seems to be solution I was looking for, since my 3d graphics run at about half the speed theyre supposed to. Id love to be able to update my graphics card, but Im new to ubuntu, and getting errors on Step one. I open the xorg conf. file and nothing is there in the terminal. It also opens up the file in a seperate window, but it is also blank. Do I not have any xorg files, and if so, where and how do I get them? Due to my ametur status with linux, half of the explanations on how to get the drivers installed I cant understand for the life of me. I apologise for any inconvience, but I need a bit of a down-to-earth explanation of how to get it to work.

hi. your xorg.conf should be there.  make sure you are copying the command exactly as it is written in the guide.  don't copy the dollar signs, as those just indicate the prompt. ;)  my guess is you typed x11 instead of X11, and case matters in linux.

---

### Post by draggy on 2009-05-27
Nice guide, I just wish it would work for me.

I have a eee 900HA using NBR, with an Intel 945GME

I've followed the safe method and after rebooting performance was faaaaarr worse then when using the exa acceleration. I checked the fixmtrr.sh and it said that it was already applied. 

I started reading through the massive amounts of threads here, and found a post that said I needed to upgrade to kernel 2.6.28-11.43 because of the bug mentioned here: [https://bugs.launchpad.net/linux/+bug/349314](https://bugs.launchpad.net/linux/+bug/349314) 
I applied the kernel mentioned at the bottom, and rebooted.

I made sure the new kernel was running, and I checked the xorg log for errors but there were none. According to the log, uxa loaded and was running with no errors, but the performance is so bad I can barely navigate the menu on NBR. Switching back to exa puts the performance back to the way it was. I have also tried it with tiling enabled and disabled, but it makes no difference. According to the log, Tiling is enabled without problems.

I seem to be out of ideas, does anyone have suggestions?

---

### Post by sketec on 2009-05-27
> **draggy said:**
> Nice guide, I just wish it would work for me.

I have a eee 900HA using NBR, with an Intel 945GME

I've followed the safe method and after rebooting performance was faaaaarr worse then when using the exa acceleration. I checked the fixmtrr.sh and it said that it was already applied. 

I started reading through the massive amounts of threads here, and found a post that said I needed to upgrade to kernel 2.6.28-11.43 because of the bug mentioned here: [https://bugs.launchpad.net/linux/+bug/349314](https://bugs.launchpad.net/linux/+bug/349314) 
I applied the kernel mentioned at the bottom, and rebooted.

I made sure the new kernel was running, and I checked the xorg log for errors but there were none. According to the log, uxa loaded and was running with no errors, but the performance is so bad I can barely navigate the menu on NBR. Switching back to exa puts the performance back to the way it was. I have also tried it with tiling enabled and disabled, but it makes no difference. According to the log, Tiling is enabled without problems.

I seem to be out of ideas, does anyone have suggestions?

My computer also uses the i945GME. I just got my Dell Vostro A90 (mini 9 clone) and immediately installed the latest Ubuntu 9.04 Netbook Remix. To my disappointment, with or without compiz, some graphics performance is awful. I tried everything mentioned in the Ubuntu Forums, Launchpad, Blogs, etc. Nothing helps. I even tried installing Ubuntu 9.10 because it includes the new kernel that suposily fixes the problems, it didn't help, and I lost wireless (Broadcom). Currently I'm using this PPA [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) which installs version 2:2.7.1-0ubuntu1~xup~1 with Option "AccelMethod" "exa", Option "EXAOptimizeMigration" "true", Option "MigrationHeuristic" "greedy", and Option "Tiling" "true". I tried UXA too, but every 30-60 seconds my screen would glitch, so I switched to EXA (which doesn't it default to that). The delayed scrolling in Firefox is the main graphics issue I'm having and it is slightly worse with compiz. I use Flashblock, so it can't be that. The animations in compiz are fine though, no glitches, and very smooth. I don't have smooth scrolling enabled either. Any clues for us i945GME users?

---

### Post by Venter127 on 2009-05-27
> **scarf said:**
> hi. your xorg.conf should be there.  make sure you are copying the command exactly as it is written in the guide.  don't copy the dollar signs, as those just indicate the prompt. ;)  my guess is you typed x11 instead of X11, and case matters in linux.

Ah! Thank you. It WAS a syntax error (thought the "1" was an "l"), so I got it to work, and This helps alot, thank you very much! My 3d programs run alot faster now, though A few of them still crash on me (in some wierd way that ignores force quit and all other commands, making the only way to exit them manually turning off the computer), and they still dont quite run as fast as they should, but it took me over a week to figure this one out, so I think Ill take a break before tackling any other problems.

Thanks again.

---

### Post by SomeOne77 on 2009-05-27
Hi,
I have done the Optimal config on my Acer Aspire One and now the hibernate does not work anymore.

When it restore from hibernate it goes back to the login screen as if it did a full reboot

I have the Intel 945GM Graphic controller

Does anyone have ideas ?

---

### Post by theromanone on 2009-05-28
Hi there, I have the Broadcom STA Wireless Driver, and my wireless wouldn't work anymore after doing the "Optimal" section. I just finished reintalling Jaunty, and have no problem viewing anything after finishing the "Safe" part.. is there any fix to the Broadcom driver issue? I'd really appreciate it!

-Also, if I go ahead and try again with the "optimal" part, any suggestions as to what I can do to go back to my current settings incase the wireless goes out?

---

### Post by AlphaMack on 2009-05-28
> **reverend_nerd said:**
> Hello,

I followed the instructions to Optimal config, but I got a set back.
I'm using Linux Mint 7, a distro that is heavily based in Ubuntu and inherits it's design and code benefits and flaws.
Along with the ride came the problem with the slow performance in Intel Graphics. I found this post with the instructions I followed through the letter.

The graphic performance is quite all right, however, I've been recently facing problems with font characters and icons in certain apps.

Describing the problem is somewhat funny, I guess it's the X, that is printing the wrong fonts in the screen and them messes up everything. For example, the letter "X" itself right now is deformed, like the part of a bigger X.

Has anyone faced a similar bug? should I revert the config and try again? or is there a fix? like, downgrading my fonts?

Cheers!
Felipe Sentelhas

Restart X.

---

### Post by Janma on 2009-05-28
worked for me.. thanks a lot :)

---

### Post by VCSkier on 2009-05-28
The "optimal" configuration certainly helped 3D performance on my system (Intel 855GM) quite a bit, but font/character/image corruption was quite problematic.  So, I reverted to the stock Jaunty kernel, resulting in the "safe" configuration, and performance is still significantly improved as compared to prior to the workaround, and the corruption is gone!  Hopefully the bug in kernel 2.6.29 will be fixed soon, and I can upgrade back to that.  In the meantime, 2.6.28 will do.

Thanks psyke83!

---

### Post by Craig73 on 2009-05-29
> **VCSkier said:**
> The "optimal" configuration certainly helped 3D performance on my system (Intel 855GM) quite a bit, but font/character/image corruption was quite problematic.  So, I reverted to the stock Jaunty kernel, resulting in the "safe" configuration, and performance is still significantly improved as compared to prior to the workaround, and the corruption is gone!  Hopefully the bug in kernel 2.6.29 will be fixed soon, and I can upgrade back to that.  In the meantime, 2.6.28 will do.

Thanks psyke83!

If you check out the phoronix forums and their intel driver testing thread, there is someone offering a patched 2.6.30rc7 kernel that addresses the font corruption.

[http://phoronix.com/forums/showthread.php?p=76563#post76563](http://phoronix.com/forums/showthread.php?p=76563#post76563)

Haven't tried it myself as it hasn't gotten annoying enough yet for me...

---

### Post by VioletsPie on 2009-05-29
im not sure what i did but i got nice graphics now!

---

### Post by bapoumba on 2009-05-29
[http://ubuntuforums.org/showpost.php?p=7365345&postcount=54](http://ubuntuforums.org/showpost.php?p=7365345&postcount=54)

Congrats psyke83 :)

---

### Post by kennyschiff on 2009-05-29
I did the optimal for my Thinkpad X61 with an Intel GM965 and seemed to work fine until I tried to turn on desktop effects. 

I was initially unable to do this, because it turns out the GM965 is black listed. I followed the procedure described [here]("http://ubuntuforums.org/showthread.php?t=1155448") to remove it from the list, which did allow me to enable desktop effects; however, the side effect is that my shift key stops working. 

I've seen this problem within VMWare before, but changing the keyboard layout doesn't solve this problem, nor does "setxkbmap ." I guess there is a reason that the GM965 is black listed ;)

---

### Post by Roanoke on 2009-05-30
Thanks a ton for this guide. My FPS in nexuiz spiked at least 200%.

---

### Post by SQuark on 2009-05-30
Worked great for me! Many many thanks!

Just one little note: Xubuntu does use GDM for the login screen, so no need to scare off the less knowledgeable Xubuntu users. :)

---

### Post by jerrylamos on 2009-05-30
With Karmic Alpha 1, Edgers 2.7.99 driver slowed down vs. 2.7.0 on my IBM Thinkpad R31 with i830 video and IBM ThinkCentre A30 with i845 video.  

Launchpad bug 382017 has the #'s including 36% slower on GtkPerf from Synaptic on the i845, 90% slower on the i830. Oof.

Fastest driver on the i845 is VESA.  2.7.99 measured 58% slower....

Jerry

---

### Post by scarf on 2009-05-31
shouldn't the downloads for the kernels be verified in some way?  gpg signature? or at least by using https?

also, how do we get updates for the kernels?  just keep monitoring this thread?

---

### Post by scarf on 2009-05-31
text and scrolling seem to be big problems for me still, with 855GM and safe configuration.  i ran gtkperf maximized (almost 1280x768) and i set the test rounds to 1000.
results:
```

GtkPerf 0.40 - Starting testing: Sun May 31 00:53:14 2009

GtkEntry - time:  1.25
GtkComboBox - time: 36.97
GtkComboBoxEntry - time: 19.45
GtkSpinButton - time:  7.62
GtkProgressBar - time: 22.39
GtkToggleButton - time: 10.27
GtkCheckButton - time:  6.56
GtkRadioButton - time: 11.32
GtkTextView - Add text - time: 256.86
GtkTextView - Scroll - time: 64.59
GtkDrawingArea - Lines - time: 46.25
GtkDrawingArea - Circles - time: 52.83
GtkDrawingArea - Text - time: 63.21
GtkDrawingArea - Pixbufs - time:  1.69
 --- 
Total time: 601.29

```

i tried the optimal configuration, and the results are slightly better on paper, but hardly noticeable:

```

GtkPerf 0.40 - Starting testing: Sun May 31 01:56:06 2009

GtkEntry - time:  1.16
GtkComboBox - time: 36.37
GtkComboBoxEntry - time: 18.92
GtkSpinButton - time:  7.48
GtkProgressBar - time: 21.36
GtkToggleButton - time: 10.07
GtkCheckButton - time:  5.22
GtkRadioButton - time: 10.71
GtkTextView - Add text - time: 235.12
GtkTextView - Scroll - time: 60.79
GtkDrawingArea - Lines - time: 42.52
GtkDrawingArea - Circles - time: 51.07
GtkDrawingArea - Text - time: 57.71
GtkDrawingArea - Pixbufs - time:  1.59
 --- 
Total time: 560.08

```

unfortunately, i couldn't get my rt2860 wifi driver working with the 2.6.29 kernel, even tho i have the source code and recompiled and reinstalled the module for the 2.6.29 kernel.  so, back to the safe config for now.

---

### Post by meganox on 2009-05-31
I'm getting absolutely horrible effects with UXA enabled now, going to revert.  Hopefully Karmic will be better.

---

### Post by 3rdalbum on 2009-05-31
Can I just say: Don't fiddle with the graphics on a production system. I tried a HOWTO on my netbook and it caused the graphics to go much slower. I reversed what I did as well as I could, and it broke Gnome - nothing I've done has fixed it. Reinstall time.

---

### Post by jsravn on 2009-05-31
This solution is a mixed bag for me. I have a thinkpad x41 with i810 graphics.

Optimal solution (with the kernel upgrade) proved to be very unstable. Random lockups, and suspend/hibernate stopped working completely. However, my 2d performance improved remarkably.

I'm using the safe solution now (without kernel upgrade), and my system is much stabler and I still have improved 2d. However hibernate no longer works for me, X crashes on resume, and screen fonts occasionally get corrupted (missing the top bit of the character).

Also, despite what the guide says, I found my system to be less stable and I lost all my 2d performance by disabling tiling. So I have tiling set to true now.

Hoping for a more permanent, working solution... :-).

---

### Post by bradvf on 2009-05-31
Rc2 worked for me (full screen Flash was the main problem), however all other fixes and kernels had varying results. In the end I repartitioned the h/d and moved my home folder onto a separate partition, then installed Ibex. It's so much quicker (even the Rc2 fix seems sluggish compared to this. 
The work put into this thread is amazing, and a credit to the ubuntu community imho. I've learned so much from following it, and although it's not working for everyone, it is for some. 
Cheers everyone.

---

### Post by malangbaba on 2009-05-31
hey. Using the Simple option got my flash video working better.

My computer has slowed down a little, and my touchpad is little more jerky (moreso when using small distances - but fine for major movements).  BUT I SEEM TO HAVE SOME MEMORY (LEAK?) PROBLEM OR SOMETHING WITH FIREFOX.  AFTER 30+ MINUTES OF USE, ITS BECOMES REALLY SLOW, AND htop
SHOWS IT USING 40%+ OF SYSTEM MEMORY...

Thoughts on firefox?

Also, I wanted to see if I need to tweak MTRR

> sarfarosh@sarfarosh:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x01f700000 (  503MB), size=    1MB, count=1: uncachable
reg02: base=0x01f800000 (  504MB), size=    8MB, count=1: uncachable
reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining


> 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 1800 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>


Whats my base memory address, and whats the memory size for fixmtrr.sh?

Help would be appreciated

---

### Post by DylanH on 2009-05-31
Thanks for posting this! I managed to solve my crippling display problems (described in this thread: [http://ubuntuforums.org/showthread.php?p=7379146#post7379146](http://ubuntuforums.org/showthread.php?p=7379146#post7379146))

---

### Post by psyke83 on 2009-06-01
Some news on the current state of the Intel driver: [http://anholt.livejournal.com/41132.html](http://anholt.livejournal.com/41132.html)

**8xx users:**
I tested Jaunty + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Unfortunately, tiling isn't fixed, and the Xorg.0.log displays errors regarding front buffers.

However, I also tested Karmic + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Tiling now works properly, and 2D/3D performance is excellent; I'm now getting up to 35fps in ppracer (even better than Hardy). No errors are displayed in the Xorg.0.log.

I'll try to see what's missing in the Jaunty packages.

---

### Post by Orographic on 2009-06-01
Thanks for that, this thread has been an interesting read indeed and the Safe method really helped my intel 945GZM get up to speed, or at least improve a good deal.

---

### Post by Craig73 on 2009-06-01
> **psyke83 said:**
> Some news on the current state of the Intel driver: [http://anholt.livejournal.com/41132.html](http://anholt.livejournal.com/41132.html)

**8xx users:**
I tested Jaunty + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Unfortunately, tiling isn't fixed, and the Xorg.0.log displays errors regarding front buffers.

However, I also tested Karmic + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Tiling now works properly, and 2D/3D performance is excellent; I'm now getting up to 35fps in ppracer (even better than Hardy). No errors are displayed in the Xorg.0.log.

I'll try to see what's missing in the Jaunty packages.

OK but Savant's build is 2 days before the commit referred to by Eric's blog - so did you miss the 8xx fixes he was referring to?

---

### Post by Maupertus on 2009-06-01
Little bit frustrating, but although upgrading to 2.6.30 rc7 did wonders for my video performance (and even battery life) for some reason the great wireless support for the eeepc (904HA, basically the same architecture as the 1000h) has been ruined. 

Is there any way I can resolve this on my own, or is this something up-river?

---

### Post by psyke83 on 2009-06-01
> **Craig73 said:**
> OK but Savant's build is 2 days before the commit referred to by Eric's blog - so did you miss the 8xx fixes he was referring to?

Hmm, I'm not certain. Perhaps part of the fixes were merged a few days earlier. It appears that it is working correctly, though (no errors in the logs, and 3D performance has definitely increased).  I experienced some freezes during 3D operations; it could be due to Sarvatt's changes to the kernel build options, or perhaps the drm fixes weren't finalized.

See: [http://www.phoronix.com/forums/showpost.php?p=76563&postcount=221](http://www.phoronix.com/forums/showpost.php?p=76563&postcount=221)

The -sarvatt2 kernel was built after Linus merged the drm-intel branch.

---

### Post by vistamacbuntu on 2009-06-01
Hi, I just upgraded my Thinkpad X200 to Jaunty (well Linux Mint Gloria to be exact).  I'm a new Linux user and have been very excited with 100% migrating my work/personal machine to Linux.  (still have not deleted my Vista partition because I need to be 100% sure I do not need to go back).

Same problems as most of you here. Went through all 4 intel drivers from Jaunty default, to x-swat PPA stable to edgers to Intrepid 2.4  Don't feel any difference.

(I miss compiz! Can't even turn it on.)

Anyway, I'm eagerly waiting for the official update with the right driver, but in the meantime, I have a feeling that my setup is using VESA drivers. Can someone help me confirm whether this is the case?  Here's what I see from my lspci -nn command:

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)

Thanks in advance for any help or feedback!

---

### Post by xakh on 2009-06-01
Okay. Is this necessary for nVidia stuff, since I've been getting annoying crashes, and video issues, or is this only for intel stuff?

---

### Post by thundaraptor on 2009-06-01
I completed all the commands.  System seems faster but still have only basic access to ubuntu visual effects.  Am a basic user so please help and keep tech statements as straight forward as possible.

---

### Post by galv on 2009-06-01
> **xakh said:**
> Okay. Is this necessary for nVidia stuff, since I've been getting annoying crashes, and video issues, or is this only for intel stuff?

Just Intel.

---

### Post by Ekeluo on 2009-06-01
Thank you thank you thank you for this. I thought my 1.6Ghz PM/GMA 900 combo had finally fallen in the grave but you have provided an invaluable helping hand. Thanks again.

P.S. Why haven't they incorporated the memory fix in the repo driver? Seems easy... But then, what do I know?

---

### Post by Ekeluo on 2009-06-01
Thank you thank you thank you for this. I thought my 1.6Ghz PM/GMA 900 combo had finally fallen in the grave but you have provided an invaluable helping hand. Thanks again.

P.S. Why haven't they incorporated the memory fix in the repo driver? Seems easy... But then, what do I know?

Sorry a bit excited, guess I clicked submit too many times

---

### Post by psyke83 on 2009-06-01
> **Ekeluo said:**
> Thank you thank you thank you for this. I thought my 1.6Ghz PM/GMA 900 combo had finally fallen in the grave but you have provided an invaluable helping hand. Thanks again.

P.S. Why haven't they incorporated the memory fix in the repo driver? Seems easy... But then, what do I know?

Sorry a bit excited, guess I clicked submit too many times

As far as I'm aware, the fix for the MTRR driver needs to be applied to the DRM kernel module, not the driver itself. Kernel 2.6.30 should have this fix included, but it won't be included in Jaunty, so the only other option is to wait for the fix to be backported into the Jaunty kernel.

---

### Post by psyke83 on 2009-06-01
> **malangbaba said:**
> hey. Using the Simple option got my flash video working better.

My computer has slowed down a little, and my touchpad is little more jerky (moreso when using small distances - but fine for major movements).  BUT I SEEM TO HAVE SOME MEMORY (LEAK?) PROBLEM OR SOMETHING WITH FIREFOX.  AFTER 30+ MINUTES OF USE, ITS BECOMES REALLY SLOW, AND htop
SHOWS IT USING 40%+ OF SYSTEM MEMORY...

Thoughts on firefox?

Also, I wanted to see if I need to tweak MTRR





Whats my base memory address, and whats the memory size for fixmtrr.sh?

Help would be appreciated

Yes, there appears to be some memory leaks with UXA. There is no easy fix for this yet, but I believe it will come soon (see [here]("http://ubuntuforums.org/showthread.php?p=7380051#post7380051")).

---

### Post by crjackson on 2009-06-01
> **psyke83 said:**
> Some news on the current state of the Intel driver: [http://anholt.livejournal.com/41132.html](http://anholt.livejournal.com/41132.html)

**8xx users:**
I tested Jaunty + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Unfortunately, tiling isn't fixed, and the Xorg.0.log displays errors regarding front buffers.

However, I also tested Karmic + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Tiling now works properly, and 2D/3D performance is excellent; I'm now getting up to 35fps in ppracer (even better than Hardy). No errors are displayed in the Xorg.0.log.


I'll try to see what's missing in the Jaunty packages.

Wow, that sounds great, I hope I get the same results with:

```
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

---

### Post by psyke83 on 2009-06-01
> **Maupertus said:**
> Little bit frustrating, but although upgrading to 2.6.30 rc7 did wonders for my video performance (and even battery life) for some reason the great wireless support for the eeepc (904HA, basically the same architecture as the 1000h) has been ruined. 

Is there any way I can resolve this on my own, or is this something up-river?

I have no pity for you if you don't read the guide properly... I specifically warn in the disclaimer that using a third-party kernel will mean that restricted drivers no longer function. You should revert the changes (or simply choose the official Jaunty kernel in GRUB - press ESC to access the menu if necessary).

---

### Post by psyke83 on 2009-06-01
> **thundaraptor said:**
> I completed all the commands.  System seems faster but still have only basic access to ubuntu visual effects.  Am a basic user so please help and keep tech statements as straight forward as possible.

I'm sorry, but this guide isn't aimed towards complete beginners. There are too many risks involved in following these instructions.

You need to express your problem more clearly. What do you mean by "all the commands"? Did you choose Safe, Optimal or Bleeding-Edge? What Intel graphics chipset do you own?

The most likely answer is that compiz is blacklisting your card (and updating drivers won't fix it). Search the forum for compiz + blacklist.

---

### Post by psyke83 on 2009-06-01
> **crjackson said:**
> Wow, that sounds great, I hope I get the same results with:

```
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

Well, the UXA corruption issue is fixed (where fonts and images become garbled in Firefox) - that affects all users. But the specific performance improvements are only for the older 8xx-based chipsets, it seems. Your chipset won't apply.

---

### Post by malangbaba on 2009-06-02
> **psyke83 said:**
> Yes, there appears to be some memory leaks with UXA. There is no easy fix for this yet, but I believe it will come soon (see [here]("http://ubuntuforums.org/showthread.php?p=7380051#post7380051")).

Thanks for the response.  I'll read the link.

Do you think trying to tweak the MTRR would be pointless at this stage?

---

### Post by Orographic on 2009-06-02
Just for the record, I don't seem to be getting any memory leaks of note after having used the Safe Configuration method.

I have 2 gig of ram on my Gigabyte 945GZM-S2 motherboard with intel onboard graphics. Typically I use less than 20% of memory, from what I can tell but will keep an eye on it.

---

### Post by dentaku65 on 2009-06-02
> **psyke83 said:**
> Some news on the current state of the Intel driver: [http://anholt.livejournal.com/41132.html](http://anholt.livejournal.com/41132.html)

**8xx users:**
I tested Jaunty + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Unfortunately, tiling isn't fixed, and the Xorg.0.log displays errors regarding front buffers.

However, I also tested Karmic + [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled. Tiling now works properly, and 2D/3D performance is excellent; I'm now getting up to 35fps in ppracer (even better than Hardy). No errors are displayed in the Xorg.0.log.

I'll try to see what's missing in the Jaunty packages.

I can confirm this in Jaunty, Tiling has problems (garbage output display with glxgears); I have a little bit different conf here, in part based on this wiki [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
Jaunty + [ubuntu-x-swat]("https://edge.launchpad.net/~ubuntu-x...ive/x-updates/") + [Karmic kernel 2.6.30-6-generic]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/") + KMS

Weird thing: booting in recovery mode from Grub I get true KMS; default boot of the kernel no (maybe splash option in Grub has problems)

***UPDATE*** in the meantime:
Jaunty + [ubuntu-x-swat]("https://edge.launchpad.net/~ubuntu-x...ive/x-updates/") + kernel [2.6.30-rc7-sarvatt2]("http://sarvatt.com/downloads/2.6.30-rc7-sarvatt2/") + tiling enabled + KMS
Works perfect.
No garbage output in glxgears
No Tiling errors in Xorg.0.log
True KMS booting from default kernel image (Sarvatt2 2.6.30-rc7 kernel)
I must say the better performances with my card since long time.

---

### Post by vistamacbuntu on 2009-06-02
I'm trying to love Linux, but it isn't loving me back. :)

Still can't get this to work.

Anyway, a simple question to the experts in behalf of the noobs / semi-noobs: is it fair to expect that when an official update comes out, it will be before the next major release of Ubuntu? And that it will just "fix" these Intel problems?  I.e. a simple click in synaptics...

At this point, I'm just hanging on to basic 2D graphics on my thinkpad.  Tempted to revert to 08.10 but it takes so much time customizing and transferring all my work and personal files/apps!

---

### Post by paulmerchant on 2009-06-02
The latest bleeding-edge drivers from edgers PPA just broke me this morning. I'm getting nothing but a black screen after logging in after the updates on an Intel 945GM with Compiz enabled. I'll go back to x-swat.

On another note, I ended up seeing some kernel updates submitted last week that should fix font corruption and/or other problems that happen with a lot of us after a few hours with Intel cards and Jaunty. It looked like these updates should make it into the 2.6.30 rc8 kernel. This new kernel and the next stable Intel drivers might provide a good sweet spot.

---

### Post by Craig73 on 2009-06-02
> **psyke83 said:**
> Hmm, I'm not certain. Perhaps part of the fixes were merged a few days earlier. It appears that it is working correctly, though (no errors in the logs, and 3D performance has definitely increased).  I experienced some freezes during 3D operations; it could be due to Sarvatt's changes to the kernel build options, or perhaps the drm fixes weren't finalized.

See: [http://www.phoronix.com/forums/showpost.php?p=76563&postcount=221](http://www.phoronix.com/forums/showpost.php?p=76563&postcount=221)

The -sarvatt2 kernel was built after Linus merged the drm-intel branch.

Sarvatt confirmed for me that this included the fixes (the commit was to the kernel and his was from intel sources, iirc)

---

### Post by paulmerchant on 2009-06-02
> **Craig73 said:**
> Sarvatt confirmed for me that this included the fixes (the commit was to the kernel and his was from intel sources, iirc)

Thanks for bringing up the Sarvatt build. I figured that someone had already built an rc7 with the latest fixes. I just didn't know where to look.

---

### Post by metapaso on 2009-06-02
[/QUOTE]
[SIZE="1"]**Changelog**
v1.1 - 12/05/09 - Complete re-write.
v1.2 - 12/05/09 - Modified instructions to allow automatic startup of fixmtrr.sh script (Part A, step 3).
v1.3 - 19/05/09 - Updated Bleeding-Edge section to fetch -rc6 kernel.
v1.4 - 24/05/09 - Updated Bleeding-Edge section to fetch -rc7 kernel.
v1.5 - 01/05/09 - Updated Optimal section to fetch 2.6.29.4 kernel, added Bleeding-Edge note.
v1.6 - 02/05/09 - Added some warnings to guide.[/SIZE][/QUOTE]

Should the v1.5 and v1.6 of your changelog read 01/06/09 and 02/06/09, respectively?

Not trying to nit-pick, just trying to establish a timeline of the solutions to this problem.

---

### Post by psyke83 on 2009-06-02
> **metapaso said:**
> 

Should the v1.5 and v1.6 of your changelog read 01/06/09 and 02/06/09, respectively?

Not trying to nit-pick, just trying to establish a timeline of the solutions to this problem.

Fixed, thanks for pointing out the error.

---

### Post by markbl on 2009-06-02
Note (as Paul Merchant above hints at), for anybody using the bleeding edge x-edgers PPA note that the update today of xserver-xorg-video-intel 2:2.7.99.1+git20090601.704771f1-0ubuntu0sarvatt~jaunty -> 2:2.7.99.1+git20090602.ec2fde7c-0ubuntu0sarvatt~jaunty may break X savagely.
X would only run on my 945GM laptop for about 5 secs after startup. I downgraded back to the earlier version (20090601) and all was ok again.

---

### Post by 11010110 on 2009-06-03
Hey i did the safe configuration and if need be i was going to move up to optimal and so forth but all of my problems with flash have been completely fixed as of right now! Thanks a bunch for this tut i have been scouring the internet for a few weeks to get this fixed and finally i found this.

The only thing is that some of the effects got a little screwed up from compiz fusion. Some of the animations and the pulldown menus in firefox are a bit messed up. Does anyone have any idea how that may be remedied? I ended up using the safe configuration. 

Thanks again!

---

### Post by 11010110 on 2009-06-03
Hi again,

I managed to fix (or workaround) most of the graphics glitches thusfar but one thing is still puzzling me... since doing this my mounse funtionality has changed. when moved slow it is more sensitive than when it is moved fast. basically when i drag my finger across the mousepad fast it only moves an inch or so but when i drag it slow it darts to the end of the screen easily. Any ideas on how to fix this?

Thanks a lot in advance.

---

### Post by Orographic on 2009-06-03
I ended up restoring an earlier Jaunty image via Clonezilla and performing the Safe Configuration fix again as I initially did it a week ago, late at night, and wasn't sure I edited the xorg.conf exactly right. 

I re-read this entire thread and performed the safe config again and as I was doing this I noticed some updates coming through that looked like they had some fixes for this Intel problem but I was distracted in the office and couldn't remember what they were about. 

How do you see a list of the updates that have been applied to Jaunty? Specifically, the ones that came through today.

---

### Post by cyper on 2009-06-03
to **Orographic**:
/var/log/apt/term.log
/var/log/dpkg.log
/var/log - interesting place ;)

I was guided by [http://ubuntuforums.org/showthread.php?t=1054219](http://ubuntuforums.org/showthread.php?t=1054219) Thanks to mc4man

---

### Post by bearozo on 2009-06-03
Where do I find this option ?

> **S.A.A said:**
> I finally found a way to run compiz with:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

```all you have to do is using "Indirect Rendering" option.
And now my old PC is back to life again (it's even faster than it was with Hardy).

---

### Post by map84 on 2009-06-03
Part **Safe** and Part **Optimal** did the trick for my system.

```
lspci -vnnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
```

Is there a "*-server" Edition of the Kernel 2.6.29-02062904 for download? 

With *-generic Kernel only 3GB of my 4GB RAM could be recognized.

---

### Post by psyke83 on 2009-06-03
> **map84 said:**
> Part **Safe** and Part **Optimal** did the trick for my system.

```
lspci -vnnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
```

Is there a "*-server" Edition of the Kernel 2.6.29-02062904 for download? 

With *-generic Kernel only 3GB of my 4GB RAM could be recognized.

No, there isn't. If you check the link to the kernel provided, you'll see that only the i386 and amd64 builds are available.

---

### Post by psyke83 on 2009-06-03
I've updated the guide to fetch the latest -rc8 kernel. The Bleeding-Edge configuration should now yield the best performance for 8xx users due to recent fixes (but it's still the most risky method, as always).

---

### Post by Hyperion_1984 on 2009-06-03
Can the size of the virtual screen have an effect of the success or the failure of the different configuration?

---

### Post by sn0m on 2009-06-03
thanks mate, nice how to.
I've managed to get my blink back.
One thing though, mouse seem to be not as responsive as befor, a bit slow, otherwise everything works ok.
Thanks
Sokol :)

---

### Post by paulmerchant on 2009-06-03
The bleeding-edge xserver-xorg-video-intel is broken for the second day on my 945GM (a black screen after logging in on the 20090603 build). It's a pity I can't find and download the 20090601 bleeding-edge drivers now, especially with rc8 of the latest kernel out.

Anyway, the rc8 kernel fixed a number of issues. For one thing, I haven't seen any corrupted fonts. However, without the bleeding-edge drivers I'm missing a few of the fixes and improvements that I was getting a few days ago.

By the way, I'm not complaining. Thanks to everyone working these issues and making it easy for us to use and test the latest software. I'm looking forward to future builds.

---

### Post by Mike.lifeguard on 2009-06-03
> **psyke83 said:**
> 
...
**8xx users:**


How does one tell if they're an "8xx user"? :D

Also, do we have info on the bug (or a workaround) where CTRL-ALT-F2 et al don't show terminals?

---

### Post by pawnrocket on 2009-06-03
wow that was a lot of information to go through. 

```
$ cat /proc/mtrr
reg00: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg01: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg02: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg03: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable
reg04: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg05: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining


lspci -vvnn


00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff64]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d3200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
```

I ran the fix from the first page. I first tried the step 1, then moved onto step two and ended up on Bleeding edge. 

I have poor desktop graphics and cannot enable 3D graphics. 

Based off of what I read I think this has something to do with it.

```
reg01: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
```

However I have no idea what to do with it :)

---

### Post by pawnrocket on 2009-06-03
> **Mike.lifeguard said:**
> How does one tell if they're an "8xx user"? :D

Also, do we have info on the bug (or a workaround) where CTRL-ALT-F2 et al don't show terminals?

```

lspci -vvmm

```

ctrl+alt+f2 just crashes my computer.... blackscreen of death!

---

### Post by markbl on 2009-06-03
> **paulmerchant said:**
> The bleeding-edge xserver-xorg-video-intel is broken for the second day on my 945GM (a black screen after logging in on the 20090603 build). It's a pity I can't find and download the 20090601 bleeding-edge drivers now, especially with rc8 of the latest kernel out.

Well if you have installed it previously then it will still be in /var/cache/apt/archives/. Just find the version you want and "dpkg -i" it.

PS: Paul, note that kernel rc8 + the latest xserver-xorg-video-intel 2:2.7.99.1+git20090603.b8e360bf-0ubuntu0sarvatt~jaunty works fine for me (after X failing immediately with 20090602 (on rc7)). I also have 945GM graphics.

PPS: Oops, actually the intel driver 20090603 doesn't work. It runs for a while ok but then the compiz wm seems to play up. Windows don't maximise or close etc. I've gone back again to 20090601 and all ok.

---

### Post by Mike.lifeguard on 2009-06-03
> **pawnrocket said:**
> 
ctrl+alt+f2 just crashes my computer.... blackscreen of death!

Are you sure it crashes? I get a black screen, but I can get back to my graphical session with CTRL-ALT-F7, just like normal.

---

### Post by anipet on 2009-06-04
Hi, I just wanted to share my own experience; I have a toshiba satellite M55.

I might have been a little to fast to give thank yous at first, but now and a hefty couple of lines on the console later I found out what really worked for my laptop... at first I tried the optimal approach only to get decent output at the beginning of every session, that would later badly degrade after a couple of hours of use and such. My system presented problems like the corrupted text that's been mentioned here before, zombie processes appearing on every session... also obviously losing all hibernation and suspension possibilities using the 'most recent stable kernel'.

I tried out different approaches, different kernels.... the sarvatt2 one kind of made some things better, but the degrading/freezing/dragging problems didn't stop. 

At the end, a little frustrated about the whole procedure and results I was near deciding to revert everything done and just bear with what jaunty standards offer so far... until I got a little more humble and gave just the safe approach a chance.

I've got to say, performance HAS really now gotten better... I've still got a little trouble with my RAM performance degrading a little bit over time every session, but it's all much more bearable than it was before. There's no font corruption now, the freezing and dragging has reduced drastically now and I can even suspend and hibernate just as I used to do before.

I must say... thanks a second time. Aside from the minor setbacks, the effort has all been well worth it :)

-Fer-

---

### Post by Denis.Sle on 2009-06-04
> **Hyperion_1984 said:**
> Can the size of the virtual screen have an effect of the success or the failure of the different configuration?
My video card is Intel Mobile GM965, I use second way from first post guide.
My virtual screen section in xorg.conf:
```

    SubSection "Display"
        Virtual    1280 1824
    EndSubSection

```

WORK PERFECT, GOOD PERFORMANCE , WITH NO PROBLEM

---

### Post by zevans on 2009-06-04
> **map84 said:**
> 
Is there a "*-server" Edition of the Kernel 2.6.29-02062904 for download? 

With *-generic Kernel only 3GB of my 4GB RAM could be recognized.

I can only suggest you try a -server kernel from Karmic, assuming they've built some as yet. RC5 or 7 were good for me, 6 had some oddities... yet to try 8.

The problem is that there are dozens of bugfixes between the latest "official" Jaunty kernel and the current .30RC. I realise that's the problem and it's not Ubuntu's fault... but WE NEED THOSE BUGFIXES IN JAUNTY. There is resistance to releasing .30 as an SRU because it's considered a major change. However there are SO MANY fixes in .30 and it works better in so many ways, I really honestly cannot see the problem with releasing it to jaunty-updates when it's finally released.

---

### Post by zevans on 2009-06-04
> **Hyperion_1984 said:**
> Can the size of the virtual screen have an effect of the success or the failure of the different configuration?

Yep, in various ways. If you have a 965 there was a weird bug in the original Jaunty release that went away with certain virtual screen sizes. That's long since been fixed in the xorg-edgers stuff and later kernels, so if you're on "bleeding edge" you're probably OK.

If you have a 945 acceleration just plain stops working on sizes over 2048x2048.

---

### Post by zevans on 2009-06-04
> **markbl said:**
> Well if you have installed it previously then it will still be in /var/cache/apt/archives/. Just find the version you want and "dpkg -i" it.


If someone has 20090601 in their /var/cache/apt/archives/ could you attach it here? It's gone from the "pool" directory in the PPA.

I don't because I only switched back to xorg-edgers yesterday... bad timing :-)

---

### Post by VCSkier on 2009-06-04
First of all, thank you to all how have contributed to this guide, particularly psyke83.  It has already been very helpful to me.

My system has a Intel 855GM graphics chipset.  A couple weeks ago, I tried the "optimal" setup, and that led to font corruption.  So I reverted to the stock Jaunty kernel, and have been using the "safe" setup.  Now, I'd like to try the newer 2.6.30-rc8 kernel, because of the work that has gone into it specifically on i8xx chipsets, but I don't really want the instability of xorg-edgers repo.  Could I use the 2.6.30-rc8 kernel with the X-Updates repository?  Would doing this allow me to achieve a more stable setup than the "Bleeding-Edge Configuration," while still allowing me to reap the benefits of the latest kernel bug fixes for my graphics chip?

Thanks!

---

### Post by bearozo on 2009-06-04
Hi !

I have tried the safe config but still cannot use compiz. I think it has with the monitor config to do (on my other machine with old monitor I had a lot of problems untill I changed to a newer monitor with proper plug and play and it solved everything !!! it all configured the xorg in a working way)So where can _I find out __how my_ (laptop) _monitor is configured_ ("Configured Monitor" in xorg.conf and Monitor0 if one looks in hardinfo )```
sudo ddcprobe | grep monitorrange
``` will freeze (pictue and pointer froozen kbrd not responding) my laptop and I have to cut power and restart a few times before I get a picture again (Ctrl + Alt + SysRq + REISUB does not work).
Would be nice to see what monitorrange and resolution etc. my monitor have or do I have to take my lappy apart to find out  ?(A Gericom Hummer 755II P4 with VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) )
If I have the right data I would be able to configure the Monitor section in xorg.conf.
Also in system\preferences\display everything is greyed out I cannot detect monitor that way either.
I cannot log out and back in, I do not get any graphical login and have to REISUB my way out, only regular start or reboot will get me a picture.

My xorg.conf:
> Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    1024 768
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "Intel"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false" 
EndSection

---

### Post by pawnrocket on 2009-06-04
> **Mike.lifeguard said:**
> Are you sure it crashes? I get a black screen, but I can get back to my graphical session with CTRL-ALT-F7, just like normal.

Ha! yeah the same here... 
feels like an idiot!

---

### Post by pawnrocket on 2009-06-04
So far I have just migrated everything back to Hardy. I don't much mind using it, but I do have this spiffy 9.04 with rc8 on it and I will keep looking in here to see of any new developments. 

Thanks everyone for all of your work!

---

### Post by paulmerchant on 2009-06-04
> **VCSkier said:**
> First of all, thank you to all how have contributed to this guide, particularly psyke83.  It has already been very helpful to me.

My system has a Intel 855GM graphics chipset.  A couple weeks ago, I tried the "optimal" setup, and that led to font corruption.  So I reverted to the stock Jaunty kernel, and have been using the "safe" setup.  Now, I'd like to try the newer 2.6.30-rc8 kernel, because of the work that has gone into it specifically on i8xx chipsets, but I don't really want the instability of xorg-edgers repo.  Could I use the 2.6.30-rc8 kernel with the X-Updates repository?  Would doing this allow me to achieve a more stable setup than the "Bleeding-Edge Configuration," while still allowing me to reap the benefits of the latest kernel bug fixes for my graphics chip?

Thanks!

Yesterday I ran the 2.6.30-rc8 kernel with the drivers in the x-Updates repository on my 945GM. It was a stable combination for me, significantly better than the current "Optimum" because of the fixes found in rc8. Those Intel drivers aren't as far along with fixing several problems, like with opengl, etc., as the drivers found in the edgers bleeding-edge repository, but the bleeding-edge currently has major problems on my 945GM.

---

### Post by paulmerchant on 2009-06-04
> **markbl said:**
> PS: Paul, note that kernel rc8 + the latest xserver-xorg-video-intel 2:2.7.99.1+git20090603.b8e360bf-0ubuntu0sarvatt~jaunty works fine for me (after X failing immediately with 20090602 (on rc7)). I also have 945GM graphics.

PPS: Oops, actually the intel driver 20090603 doesn't work. It runs for a while ok but then the compiz wm seems to play up. Windows don't maximise or close etc. I've gone back again to 20090601 and all ok.

Thanks for the note. For some reason I ran an apt-get clean a couple of days ago. Doh. I found a 20090601 on someone's site, but it had a slightly newer dependency that currently isn't in the edgers repository.

The 20090603 appeared to go a little further for me, too, than the 20090602, but not much.

---

### Post by JPD2010 on 2009-06-04
> **alphaniner said:**
> Has anyone tried this on an Intel D945GCLF board?  I had already updated to the latest stable Xorg drivers when I came across this guide.  I don't think that would have had any bearing on the problems I ran across but I figured I'd mention it.

I added the lines to my xorg.conf and did the workaround for the MTRR bug.  I did a warm boot and made it to the greeter.  After entering my login info the screen flickered a bit then I was back to the greeter.  Another login attempt yielded the same result.  So I logged in via a terminal and commented out the first of the new lines in xorg.conf.  After that I was able to login successfully.  I then started up FF and Deluge then left the machine otherwise idle for about an hour.
When I returned to the machine to do some troubleshooting, I noticed that the screen was intermittently 'fuzzy' after a few minutes of activity.  Then the NB fan started spinning faster than I had ever heard it before.  I disabled all the xorg.conf changes then restarted X, but the fuzziness remained.  So I removed the MTRR workaround and did a warm boot.  The fuzziness was still there after a restart, but eventually went away.  My best guess is that the NB/VPU was starting to overheat.


By any chance is that a a HP Laptop with nvidia graphics?

---

### Post by bearozo on 2009-06-04
Ok since I posted this [http://ubuntuforums.org/showpost.php?p=7398877&postcount=672](http://ubuntuforums.org/showpost.php?p=7398877&postcount=672) I found that my intel grapics card is blacklisted in compiz, one of the only two now in the list :( 
I edited compiz putting an # in front of the line blacklisting my card and could start compiz, unfortunatly it did not work I just got my wallpaper and a working mouse pointer nothing else so I REISUBbed. 
Apperantly there is a reason for the  blacklisting :) so I have to give up for now and live without compiz, I do not know how the grapics performance is as I have nothing to compare with, this is the first ubuntu distro I tried on this lappy that actually gave a picture ! I can use my USB TV and watch TV movies works fine etc. so other than no compiz and some small problems mentioned in #672 it is fine, I am a nOOb but am learning more and more. I do think if I could configure my monitor correctly in xorg.conf the chance of succes with compiz would increase :)

---

### Post by The Tapsa on 2009-06-05
$ grep -i UXA /var/log/Xorg.0.log
(WW) intel(0): DRI2 requires UXA

Does this mean I didn't do it right?

---

### Post by tomchiverton on 2009-06-05
Maybe. What are you using ? With the x-edgers X updates and the latest .30 kervel (rc 8 ), I get:
$ grep -i UXA /var/log/Xorg.0.log
(--) intel(0): Using UXA for acceleration
(II) UXA(0): Driver registered support for the following operations:

---

### Post by The Tapsa on 2009-06-05
I have Intel GMA3100 integrated to my motherboard (Asus P5KPL-CM).
And I'm using Xubuntu 9.04.

---

### Post by tomchiverton on 2009-06-05
> **The Tapsa said:**
> I have Intel GMA3100 integrated to my motherboard (Asus P5KPL-CM).
And I'm using Xubuntu 9.04.

You don't say which of the steps in the first post here you've done.

---

### Post by markbl on 2009-06-05
> **zevans said:**
> If someone has 20090601 in their /var/cache/apt/archives/ could you attach it here? It's gone from the "pool" directory in the PPA.

Here you go, I put it here for you and Paul Merchant:

[http://markb.dreamhosters.com/xserver-xorg-video-intel_2%253a2.7.99.1+git20090601.704771f1-0ubuntu0sarvatt~jaunty_i386.deb](http://markb.dreamhosters.com/xserver-xorg-video-intel_2%253a2.7.99.1+git20090601.704771f1-0ubuntu0sarvatt~jaunty_i386.deb)

---

### Post by bearozo on 2009-06-05
> **The Tapsa said:**
> I have Intel GMA3100 integrated to my motherboard (Asus P5KPL-CM).
And I'm using Xubuntu 9.04.
I do not think the GMA3100 is blacklisted in compiz any longer.
Take look in /usr/bin/compiz  u will see the blacklist near the top of the file.

---

### Post by The Tapsa on 2009-06-05
Now I got it working. I just did write one line wrong in xorg.conf.
Thanks anyway.

---

### Post by Forceflow on 2009-06-05
I did the following (Intel 945GM)
[LIST]
[*]Enabled UXA in xorg.conf
[*]Updated to latest stable X drivers using launchpad repos
[*]Enabled fixmttr script
[/LIST]

Performance is better with UXA, and using the latest stable X-drivers the annoying problem of X eating up swap space seems to have dissapeared ... crossing fingers though.

---

### Post by synonymy on 2009-06-05
Performed the upgrade and had a little better performance I suppose. Initially I had a blank screen upon restart and had to clear out the xorg.conf options specified in the how-to in order to get the screen to come up. 

Now however, my alps touchpad is functioning more erratically. I'd rather have the poorer graphic performance than the strategic labor of moving my finger around to the satisfaction of the machine.

Has anyone else noticed their touchpad behave differently after messing around with this procedure? Mine seems to have lost it's slow speed sensitivity and winds up jumping once you cross the threshold. It works like a frog, not a mouse. I dread using the thing. The world of setting these things seems daunting within the research I have done. The default install had perfect settings and performance.

xubuntu

Thx

---

### Post by paulmerchant on 2009-06-05
> **markbl said:**
> Here you go, I put it here for you and Paul Merchant:

[http://markb.dreamhosters.com/xserver-xorg-video-intel_2%253a2.7.99.1+git20090601.704771f1-0ubuntu0sarvatt~jaunty_i386.deb](http://markb.dreamhosters.com/xserver-xorg-video-intel_2%253a2.7.99.1+git20090601.704771f1-0ubuntu0sarvatt~jaunty_i386.deb)

Big thanks, Mark. For the last couple of hours, Jaunty has been the best Ubuntu ever. I'm now running kernel 30 rc8 with the 20090601 bleeding-edge Intel driver and seeing excellent results.

---

### Post by synonymy on 2009-06-05
I removed the synaptics driver from the update and reverted back to the ubuntu main driver. It now works like it should.

> **synonymy said:**
> Performed the upgrade and had a little better performance I suppose. Initially I had a blank screen upon restart and had to clear out the xorg.conf options specified in the how-to in order to get the screen to come up. 

Now however, my alps touchpad is functioning more erratically. I'd rather have the poorer graphic performance than the strategic labor of moving my finger around to the satisfaction of the machine.

Has anyone else noticed their touchpad behave differently after messing around with this procedure? Mine seems to have lost it's slow speed sensitivity and winds up jumping once you cross the threshold. It works like a frog, not a mouse. I dread using the thing. The world of setting these things seems daunting within the research I have done. The default install had perfect settings and performance.

xubuntu

Thx

---

### Post by jonathanmotes on 2009-06-06
Could someone recommend the best solution for x3100 intel graphics on Jaunty? I guess I'm a little lazy about looking though the whole thread, although I did look at about 10 pages of it :)

By the way, I'm not running any restricted drivers since most of my hardware is made my intel. 

Will the "optimal" solution improve my graphics enough so that I can run Compiz effectively? I also wish I could watch Hulu videos video full screen - right now its not possible without hangups.


Thanks!

---

### Post by dot2kode on 2009-06-06
Just wanted to say thanks for putting this togather psyke83...I have fought and fought with this card to get it working and after I spent 5  minute's on just the first part of your guide it works perfectly now, which is why I'm going to to work down and do the 'optimil' setup now for the fun of it and see if I can squeeze a lil' more outa of her. My compiz and effects all worked fine the problem I was having was any kind of HD  play back would tear and jerk sooo freakin' bad normal non HD would do O..K..not great...The only reason I dual booted was for video playback with Vista...Little run down of what my laptop is and if anyone else has the same hardware as mine:
```
Computer
Processor	      2x Intel(R) Core(TM)2 Duo CPU T5800 @ 2.00GHz
Memory                3025MB (1166MB used)
Operating System      Ubuntu 9.04

Display
Resolution	1366x768 pixels
OpenGL Renderer	Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090326 2009Q1 RC2 x86/MMX/SSE2 
```

if anyone would like a little more info on my setup feel free to ask.

Thanks again psyke!! \\:D/

---

### Post by ontadimanamana on 2009-06-06
very usefull
thanks.

---

### Post by smackcode on 2009-06-06
very helpful indeed, I get 2770 frames on glxgears (i know it shouldn't be the basis) with the latest driver update (bleeding edge option) from the original 600+ frames

---

### Post by discord on 2009-06-06
I used the "safe" option, however sometimes after using my desktop for awhile the characters in different applications such as firefox or open office all look like they turn into cyrillic. Does anybody else have this issue? See the attached screenshot.

---

### Post by shinji257 on 2009-06-06
That is some weird video corruption.  Nothing I have ever seen.  Odd that it only affects fonts.  Imo that is definately not cyrillic though.

---

### Post by christianxxx on 2009-06-06
Thanks for a great guide!
I was a little concerned about poor graphics performance after the upgrade, and had a little feeling it could be related to the graphics driver. But because I also moved to 64bit there were multiple factors to concider.

But I'm running your optimal configuration now, and everything is smooth as silk.
My glxgears-rate is 5x what it used to be (yes, I read your comments on glxgears, but mine went up and that's good).

I'm really happy now!

---

### Post by lalun09 on 2009-06-06
> **discord said:**
> I used the "safe" option, however sometimes after using my desktop for awhile the characters in different applications such as firefox or open office all look like they turn into cyrillic. Does anybody else have this issue? See the attached screenshot.

I have exactly the same problem, just not as extreme. In my case it is only one or two characters that become weird.
Any help would be appreciated!

---

### Post by thegreek on 2009-06-06
Extracing base address and memory size from lspci -v
40000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
reg00: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg01: base=0x0fffc0000 ( 4095MB), size=  128KB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg03: base=0x020000000 (  512MB), size=  512MB, count=1: write-back
reg04: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg05: base=0x03f600000 ( 1014MB), size=    2MB, count=1: uncachable
reg06: base=0x03f500000 ( 1013MB), size=    1MB, count=1: uncachable
reg07: base=0x000000000 (    0MB), size=  128KB, count=1: uncachable

 this is what terminal is giving when i run the script..
PLs help me to fix my acer aspire one.i like ubuntu but i get many freezes and black screens..

---

### Post by Mike.lifeguard on 2009-06-06
> **shinji257 said:**
> That is some weird video corruption.  Nothing I have ever seen.  Odd that it only affects fonts.  Imo that is definately not cyrillic though.

A number of people have reported this font corruption. I don't know if it's been reported to launchpad, or if anyone has found a workaround or fix yet.

Based on no expertise or knowledge at all, but observing this for quite some time... it seems to me as though the fonts get rendered for use over and over again, each time a new font/size/whatever is needed. At some point, this fails to overwrite the previous stuff (or maybe reading from the wrong place) so what gets written to screen is font-content, but not the right font-content. Either it's old (if it failed to overwrite properly) or from a different area of the screen/offscreen buffer (if it's reading from the wrong memory address(es).

Or I could be full of ****, and it's nothing like what I've hypothesized.


Equally, I've yet to see anyone address the missing terminals on CTRL-ALT-F2 and friends :\

---

### Post by psyke83 on 2009-06-07
> **Mike.lifeguard said:**
> A number of people have reported this font corruption. I don't know if it's been reported to launchpad, or if anyone has found a workaround or fix yet.

Based on no expertise or knowledge at all, but observing this for quite some time... it seems to me as though the fonts get rendered for use over and over again, each time a new font/size/whatever is needed. At some point, this fails to overwrite the previous stuff (or maybe reading from the wrong place) so what gets written to screen is font-content, but not the right font-content. Either it's old (if it failed to overwrite properly) or from a different area of the screen/offscreen buffer (if it's reading from the wrong memory address(es).

Or I could be full of ****, and it's nothing like what I've hypothesized.


Equally, I've yet to see anyone address the missing terminals on CTRL-ALT-F2 and friends :\

**Don't **report bugs to Launchpad if you are using unofficial drivers - they're unsupported. Revert to the official drivers (and Jaunty kernel) and try to reproduce using them, or else it's a waste of time.

The font corruption bug is known (as well as UXA crashing when Firefox displays large images), and it seems to be fixed upstream. To avail of these fixes, you should follow the "Bleeding-Edge" configuration - but of course, be warned that since the xorg-edgers package are updated on a semi-daily basis, breakage is possible.

Note: recently the Bleeding-Edge and Optimal configuration were somewhat unstable; aside from font corruption, I experienced some crashes and a lot of memory leaks (lots of swapping/disk activity even with few applications running). Since the rc8 kernel and the recent UXA/DRI2 bugfixes, I am no longer experiencing these issues.

---

### Post by psyke83 on 2009-06-07
> **thegreek said:**
> Extracing base address and memory size from lspci -v
40000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
reg00: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg01: base=0x0fffc0000 ( 4095MB), size=  128KB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg03: base=0x020000000 (  512MB), size=  512MB, count=1: write-back
reg04: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg05: base=0x03f600000 ( 1014MB), size=    2MB, count=1: uncachable
reg06: base=0x03f500000 ( 1013MB), size=    1MB, count=1: uncachable
reg07: base=0x000000000 (    0MB), size=  128KB, count=1: uncachable

 this is what terminal is giving when i run the script..
PLs help me to fix my acer aspire one.i like ubuntu but i get many freezes and black screens..

See: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/52](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/52)

---

### Post by mister_playboy on 2009-06-07
I have an Intel 965 chipset.  I have never had any freezes or problems with movie playback, and I get a consistent 680~740 FPS in glxgears with smooth animation.  This is with the driver blacklisted.

The only trouble is some "trailing ghost" effects during drag n' drop, and occasional graphical corruption in the form of multiple black outlines and a brief pause when minimizing a window.

Should I try un-blacklisting the the driver to allow compiz, since everything else is basically okay?  Or should I just leave it be?

---

### Post by psyke83 on 2009-06-07
> **mister_playboy said:**
> I have an Intel 965 chipset.  I have never had any freezes or problems with movie playback, and I get a consistent 680~740 FPS in glxgears with smooth animation.  This is with the driver blacklisted.

The only trouble is some "trailing ghost" effects during drag n' drop, and occasional graphical corruption in the form of multiple black outlines and a brief pause when minimizing a window.

Should I try un-blacklisting the the driver to allow compiz, since everything else is basically okay?  Or should I just leave it be?

Cards are blacklisted if they exhibit crashes or problems with compiz using EXA & DRI1 - however, they have not yet been tested with DRI2 (which is enabled when UXA is active, and will be the default in the 2.8 intel driver). Therefore it is possible that compiz will now work without the problems experienced in DRI1, but in reality it could be even more unstable. 

Give it a shot, but be prepared to encounter problems (such as freezes during login - you'll need to switch to vesa in that case). If you're not experienced at fixing a broken X configuration, don't un-blacklist the driver in compiz.

---

### Post by jbernardo on 2009-06-07
> **thegreek said:**
> PLs help me to fix my acer aspire one.i like ubuntu but i get many freezes and black screens..

I've build the karmic 2.6.30-rc8 kernel for jaunty, using the sickboy config as a starting point. I've included the mtrr combining fixes, and enabled KMS. The only problems I have now is degraded graphics performance after a few hours (glblur goes down from 20fps to 11fps) and suspending with /home mounted on a sdcard - even with sickboy's options I now end up getting corruption in /home.
I built the kernel with [this guide]("http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/") -  - but using karmic's repository (so the git clone line should read "git clone git:[COLOR=#000000]**//**[/COLOR]kernel.ubuntu.com[COLOR=#000000]**/**[/COLOR]ubuntu[COLOR=#000000]**/**[/COLOR]ubuntu-karmic.git source"), and I had a couple of problems because of options that are set in regular configs and not sickboy; check my (jbernardo) comments on the end of that guide.
With that kernel and the xorg-edgers ppa everything now seems snappier, and I can almost use google earth on my aspire... KDE4 with all efects (including the cube, blur, etc.) is smooth and responsive. And since I used sickboy's config, my boot time is around 20secs.[COLOR=#7a0874][/COLOR]

---

### Post by PatrickVogeli on 2009-06-07
Hi there,

I was using the optimal configuration, but instead of using the provided kernel I compiled my own 2.6.29.4, and I applied the linux PHC and tuxonice patches and enabling KMS

Performance was fine but, with UXA enabled, gdm would always crash after resuming. I tried different kernel versions, always the same problem. At the end, I tried installing the xorg-edgers packages and now alls is fine!

Tuxonice works beautifully, UXA is enabled, kms gives me nice terminals and usplash and performance is also very nice.

---

### Post by johnj.964 on 2009-06-07
I've searched this thread and have not seen a discussion on a problem I am having updating to 9.04 on my Dell 700m w/ Inel 855gm video card.
Install upgade from 8.10 goes fine and OS boots fine. the problem is the display comes up with a 1" black border on each side of the display. Trying to change r3esolutions does not help. 
I am quite new to Ubuntu, but am loving it, and don't really want to go back to the "W" world.
Has anyone else experienced this video problem and found a solution?

Thank you for your time

---

### Post by spikyjt on 2009-06-07
Thanks for this - Safe Configuration works a treat for me with my 945GM. I have enabled tiling, by the way, and all seems to be well.

Just a note for KDE users - add: ```
/usr/local/bin/fixmtrr.sh
``` to the end of /etc/kde4/kdm/Xsetup.
This runs as root, just before the login screen appears, so you don't need to manually run the script or put it in your autostart.

---

### Post by Mike.lifeguard on 2009-06-07
> **psyke83 said:**
> **Don't **report bugs to Launchpad if you are using unofficial drivers - they're unsupported...

The font corruption bug is known (as well as UXA crashing when Firefox displays large images), and it seems to be fixed upstream.

If it's already fixed, then I won't be reporting it as a bug :)


For the other folks affected, I fixed the missing terminals on CTRL-ALT-F2 etc by removing "VGA=791" (or something like that) from the main option in /boot/grub/menu.lst (ie the default one, which for me is now rc8, but I had that problem with .29 as well). The rest of the line is fine, just that last VGA bit.

One thing I've noticed with that is that music stops when I switch to a terminal - previously, that didn't happen. Is that a setting I could tweak somewhere? In theory, my graphical session should still have access to the sound card while I'm in a terminal, no?

Equally, note I've had no font corruption with bleeding-edge stuff. I was prepared to live with it, but it kept coming faster and faster after starting X (to the point where firefox would be unusable within a half-hour after logging in) so I bit the bullet and tried the bleeding edge configuration suggested. This was yesterday - had no issues so far. (fingers crossed!)

---

### Post by Kaliyuga on 2009-06-07
Hello guys,   just like thegrek and psycke83, Ive found myself struggling with the same big issue on my acer aspire one 110-ab (Intel chipset 945). I followed all the instructions and all the posts suggested,but nothing changed. Everytime I launch the script fixmtrr, I still have the same response:  reg00: base=0x0fffe0000 ( 4095MB), size= 128KB, count=1: write-protect reg01: base=0x0fffc0000 ( 4095MB), size= 128KB, count=1: uncachable reg02: base=0x000000000 ( 0MB), size= 512MB, count=1: write-back reg03: base=0x020000000 ( 512MB), size= 512MB, count=1: write-back reg04: base=0x03f800000 ( 1016MB), size= 8MB, count=1: uncachable reg05: base=0x03f600000 ( 1014MB), size= 2MB, count=1: uncachable reg06: base=0x03f500000 ( 1013MB), size= 1MB, count=1: uncachable reg07: base=0x000000000 ( 0MB), size= 128KB, count=1: uncachable  every help would be much appreciated. I love ubuntu, it works like a charm on my aspire one (512mb ram is not a lot:), but this damn problem with playing flash video is really annoying! Anyway, thanx for your attention ;).

---

### Post by pluckypigeon on 2009-06-07
I just did a fresh install of Jaunty. 

Updated it with official repos and it's running as good, and fast, if not faster, than hardy did(I haven't tried compiz though)

I've been on it all day and I've had no problems with garbled fonts or anything like that.

I regularly take glxgears readings although some people will say don't.

```
hardy heron :

1559 frames in 5.0 seconds = 311.707 FPS
1748 frames in 5.0 seconds = 349.442 FPS
1778 frames in 5.0 seconds = 355.596 FPS

jaunty fresh install default kernel and default intel

1642 frames in 5.0 seconds = 328.380 FPS
1643 frames in 5.0 seconds = 328.480 FPS
1576 frames in 5.0 seconds = 315.115 FPS
```
 
btw my chip is i845g

hope this helps someone else



These are some older readings on Arch and Ubuntu:
```


Arch:
415 frames in 5.0 seconds = 82.828 FPS
429 frames in 5.0 seconds = 85.618 FPS
425 frames in 5.0 seconds = 84.992 FPS
Ubuntu:
828 frames in 5.0 seconds = 165.505 FPS
864 frames in 5.0 seconds = 172.673 FPS
795 frames in 5.0 seconds = 158.900 FPS
```

btw ..... I should mention I couldn't get the LiveCD to work.. so I choose the install Ubuntu option from the LiveCd menu

---

### Post by psyke83 on 2009-06-07
> **pluckypigeon said:**
> I just did a fresh install of Jaunty. 

Updated it with official repos and it's running as good, and fast, if not faster, than hardy did(I haven't tried compiz though)

I've been on it all day and I've had no problems with garbled fonts or anything like that.

I regularly take glxgears readings although some people will say don't.

```
hardy heron :

1559 frames in 5.0 seconds = 311.707 FPS
1748 frames in 5.0 seconds = 349.442 FPS
1778 frames in 5.0 seconds = 355.596 FPS

jaunty fresh install default kernel and default intel

1642 frames in 5.0 seconds = 328.380 FPS
1643 frames in 5.0 seconds = 328.480 FPS
1576 frames in 5.0 seconds = 315.115 FPS
```
 
btw my chip is i845g

hope this helps someone else



These are some older readings on Arch and Ubuntu:
```


Arch:
415 frames in 5.0 seconds = 82.828 FPS
429 frames in 5.0 seconds = 85.618 FPS
425 frames in 5.0 seconds = 84.992 FPS
Ubuntu:
828 frames in 5.0 seconds = 165.505 FPS
864 frames in 5.0 seconds = 172.673 FPS
795 frames in 5.0 seconds = 158.900 FPS
```

btw ..... I should mention I couldn't get the LiveCD to work.. so I choose the install Ubuntu option from the LiveCd menu

Did you even read the guide? You shouldn't rely on glxgears as a benchmark at all. That being said, if you don't see any problems with performance, there's no need to risk breakage by following the guide.

---

### Post by psyke83 on 2009-06-07
> **Kaliyuga said:**
> Hello guys,   just like thegrek and psycke83, Ive found myself struggling with the same big issue on my acer aspire one 110-ab (Intel chipset 945). I followed all the instructions and all the posts suggested,but nothing changed. Everytime I launch the script fixmtrr, I still have the same response:  reg00: base=0x0fffe0000 ( 4095MB), size= 128KB, count=1: write-protect reg01: base=0x0fffc0000 ( 4095MB), size= 128KB, count=1: uncachable reg02: base=0x000000000 ( 0MB), size= 512MB, count=1: write-back reg03: base=0x020000000 ( 512MB), size= 512MB, count=1: write-back reg04: base=0x03f800000 ( 1016MB), size= 8MB, count=1: uncachable reg05: base=0x03f600000 ( 1014MB), size= 2MB, count=1: uncachable reg06: base=0x03f500000 ( 1013MB), size= 1MB, count=1: uncachable reg07: base=0x000000000 ( 0MB), size= 128KB, count=1: uncachable  every help would be much appreciated. I love ubuntu, it works like a charm on my aspire one (512mb ram is not a lot:), but this damn problem with playing flash video is really annoying! Anyway, thanx for your attention ;).

What happened to the formatting in your post?? ;)

I answered this just a few post back. See: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/52](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/52)

The Aspire One has issues with MTRR allocation because the default MTRR layout prevents any further entries. The comment above indicates some kernel boot options that can possibly fix the issue. I don't own such hardware so I can't comment or verify further.

---

### Post by Kaliyuga on 2009-06-07
Yeah, I was wondering too.... I just wrote it and seemed ok, but then my post turned out to be a real mess...;)).   Thanx for the link, I saw that and I had already tried to apply all that was suggested (cleanin up and fixing mtrr). I dont understand why nothing seems to work.   Oh well, I hope someone will figure it out sooner or later. Ive already lost several days trying to solve it: now I give up.   Id like to know if some other aspire one with intel chipset 945gm owner managed to solve this issue of the choppy flash videos.  Thanx again for your quick reply.

---

### Post by jsday187 on 2009-06-08
If you want to get really bleeding-edge they also have daily kernel builds in the mainline ppa.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/")

Beeware of that dentaku65):P character he's been in and out these forums as well as launchpad making claims to bogus fixes and such that do nothing more than waste your time and give you false hopes of improvement.
****

---

### Post by Orographic on 2009-06-08
> **pluckypigeon said:**
> I just did a fresh install of Jaunty. 

Updated it with official repos and it's running as good, and fast, if not faster, than hardy did(I haven't tried compiz though)

I've been on it all day and I've had no problems with garbled fonts or anything like that.

I regularly take glxgears readings although some people will say don't.

```
hardy heron :

1559 frames in 5.0 seconds = 311.707 FPS
1748 frames in 5.0 seconds = 349.442 FPS
1778 frames in 5.0 seconds = 355.596 FPS

jaunty fresh install default kernel and default intel

1642 frames in 5.0 seconds = 328.380 FPS
1643 frames in 5.0 seconds = 328.480 FPS
1576 frames in 5.0 seconds = 315.115 FPS
```
 
btw my chip is i845g

hope this helps someone else



These are some older readings on Arch and Ubuntu:
```


Arch:
415 frames in 5.0 seconds = 82.828 FPS
429 frames in 5.0 seconds = 85.618 FPS
425 frames in 5.0 seconds = 84.992 FPS
Ubuntu:
828 frames in 5.0 seconds = 165.505 FPS
864 frames in 5.0 seconds = 172.673 FPS
795 frames in 5.0 seconds = 158.900 FPS
```

btw ..... I should mention I couldn't get the LiveCD to work.. so I choose the install Ubuntu option from the LiveCd menu

Have you tried things like full screen iView and YouTube? Its not hard for me to do a re-install of Jaunty if the official repos have fixed the graphics issue.

---

### Post by glaze on 2009-06-08
Should I enable PAT in my kernel config when using kernel 2.6.30 and Intel driver 2.7.1 or newer? Any suggestions for/against it?

---

### Post by jbernardo on 2009-06-08
> **glaze said:**
> Should I enable PAT in my kernel config when using kernel 2.6.30 and Intel driver 2.7.1 or newer? Any suggestions for/against it?

I've built my kernel with PAT disabled, as that was the recommendation until now. I'm also interested if anyone has tried with PAT enabled, and what were the results.

---

### Post by jsday187 on 2009-06-08
> **jbernardo said:**
> I've built my kernel with PAT disabled, as that was the recommendation until now. I'm also interested if anyone has tried with PAT enabled, and what were the results.

I have it enabled but I'm pretty sure that it only enables support for it, not implements it. 

****

---

### Post by densou on 2009-06-09
guys, tried bleeding-edge because I wasn't still satisfaid with both safe and optimal .... (not perfect OGL rendering, and I felt video playback lacked something), I hadn't solved those issues until I have installed 2.6.30-999-generic (today's build) :D 


-ot-
well, I don't know why my gnome panel lose its localization, now it's half in English and half in Italian (and it must be fully localizated again or users of this desktop -my parents- will not recognize at all applications)

---

### Post by cliddell on 2009-06-09
Just wanted to add a note of thanks to psyke83 for the howto. The "safe" settings, without the "uxa" option have solved my video playback problems (mainly shearing and tearing of the picture during playback) and I'm very, very grateful. With the uxa option, I get no video signal (monitor goes into power saving mode).

For what it's worth, that's on a Mac Mini with the i945 chip - I think... It's definitely not the newer nVidia Mac Mini, anyway.

Thanks  again,

Chris

---

### Post by vaibhav on 2009-06-09
I followed the steps in the guide (the Bleeding edge one). Now my X does not start. Manually typing X on the command line says "Bus error". Any pointers?

---

### Post by bearozo on 2009-06-09
Hi all :)

First a thanx to psyke83 for the howto and an apology for not noticing the don't PM.

I first found this thread when I wanted to make compiz work everything else works.
Tried the safe one first and then the optimal and now the bleeding edge non of them allows me to use compiz, my VGA compatible controller: Intel Corporation 82845G/GL [Brookdale-G]/GE Chipset Integrated Graphics Device is b lacklisted in compiz and editing enables but I just get wallpaper and a pointer and have to REISUB out of it.
On the other hand the performance have increased with all of them and the bleeding edge works the best 360-400 FPS in glxgears and 35-40 in ppracer which btw only works in the bleeding edge config ppracer will work but crashes xorg when I quit and I have to REISUB if I use this xorg.conf:

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    1024 768
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "Intel"
    VideoRam    131072
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true" 
EndSection

```but if I use the "default" one:

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection
```ppracer will work and I can quit and keep using my lappy but the FPS goes down to 30-35 instead of 35-40 (well it hit 40 once) but glxgears stays the same if not a tad better.

The optimal config gave me font distortion in kaffeine and in panel so that was no good for me.

So for now I am sticking with the bleeding edge and default xorg.conf but I will change it if I can get compiz to work so here is some questions and thoughts:

QUESTION: the  "Configured Monitor" in the monitor section in xorg.conf how do I find out how it is configured ?
I cannot use ddcprobe as it deep freezes my system and I have to do a hard shutdown and in the System\Preferences\Display all is greyed out and I can do nothing, all I see is monitor "on" if I hit apply it tells that xorg.conf needs a Virtual Display subentry and does it for you adding Virtual 0 0 I changed it to 1024 x 768 because that is what the display defaults to with "Configured Monitor". My monitor seems non- probeable !!!  All that I know replacement is either a TFT Display 15 Zoll XGA (1024 x 768 Pixel) or 15 Zoll SXGA+ (1400 x 1050 Pixel)


I think I can use compiz if my monitor is correctly configured in xorg.conf by bypassing blacklist I think so because on the machine in my sig i had problems with compiz because I did not have all the right values on my ancient KFC non plug and play monitor and when I changed monitor to a newer Nokia with proper plug and play everything started to work perfectly and it rewrote xorg.conf with the right values :)

QUESTION is, how can I get the correct values ? horiz and vert rates etc. 
Seems that I might have to dismantele to see if I can find make and model.

.
Last QUESTION what does 0 0 mean in the Virtual Monitor setting ? and can I set a higher value than Physical range ?

---

### Post by Xion345 on 2009-06-09
I just wanted to mention that i tried the three methods with an i845G chipset and I wasn't able to get decent 2D performance (2D redraw was horribly slow and scrolling unusable).
However, th MTRR fix seemed to help.

The only solution I found was to downgrade the intel driver to 2.4and use XAA.
3D performance decreased a little (-20fps in glxgears, and same performance in tuxracer)

Has anyone succeeded to make a modern acceleration architecture work with an i845G ?

```
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

---

### Post by simmerz on 2009-06-09
I want to say my thanks to psyke83 as well. Now running with the optimal settings on an EeePC 901 and it feels so much more responsive.

Thanks again.

---

### Post by bearozo on 2009-06-09
I have the same chipset which works fine with bleeding edge, can you run compiz
with the 2.4 driver and XAA ? I cannot whatever I try (the chipset is blacklisted in compiz though) see this post for more detail [http://ubuntuforums.org/showpost.php?p=7427942&postcount=724](http://ubuntuforums.org/showpost.php?p=7427942&postcount=724)
 
> **Xion345 said:**
> I just wanted to mention that i tried the three methods with an i845G chipset and I wasn't able to get decent 2D performance (2D redraw was horribly slow and scrolling unusable).
However, th MTRR fix seemed to help.
 
The only solution I found was to downgrade the intel driver to 2.4and use XAA.
3D performance decreased a little (-20fps in glxgears, and same performance in tuxracer)
 
Has anyone succeeded to make a modern acceleration architecture work with an i845G ?
 
```
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

---

### Post by psyke83 on 2009-06-09
> **Xion345 said:**
> I just wanted to mention that i tried the three methods with an i845G chipset and I wasn't able to get decent 2D performance (2D redraw was horribly slow and scrolling unusable).
However, th MTRR fix seemed to help.

The only solution I found was to downgrade the intel driver to 2.4and use XAA.
3D performance decreased a little (-20fps in glxgears, and same performance in tuxracer)

Has anyone succeeded to make a modern acceleration architecture work with an i845G ?

```
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

You could try an intermediary solution: use the 2.7.x series driver (i.e. Optimal configuration), but use EXA acceleration instead of UXA, and enable the greedy migration heuristic. It may yield better 2D performance.

Note: the xorg-edgers drivers no longer have EXA support.

---

### Post by psyke83 on 2009-06-09
> **bearozo said:**
> I have the same chipset which works fine with bleeding edge, can you run compiz
with the 2.4 driver and XAA ? I cannot whatever I try (the chipset is blacklisted in compiz though) see this post for more detail [http://ubuntuforums.org/showpost.php?p=7427942&postcount=724](http://ubuntuforums.org/showpost.php?p=7427942&postcount=724)

See my reply to Xion345. Note that XAA is no longer supported upstream, and bugs will never be fixed. It's a dead-end.

---

### Post by psyke83 on 2009-06-09
> **Xion345 said:**
> I just wanted to mention that i tried the three methods with an i845G chipset and I wasn't able to get decent 2D performance (2D redraw was horribly slow and scrolling unusable).
However, th MTRR fix seemed to help.

The only solution I found was to downgrade the intel driver to 2.4and use XAA.
3D performance decreased a little (-20fps in glxgears, and same performance in tuxracer)

Has anyone succeeded to make a modern acceleration architecture work with an i845G ?

```
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

I also forgot to mention: i8xx class hardware had problems with tiling until the very latest updates (Bleeding-Edge with rc8 kernel).

If you didn't test the rc8 kernel yet, try it with tiling enabled. If you're using Safe or Optimal, disable tiling or else your 3D performance may be halved (which happens on my 855GM hardware).

---

### Post by psyke83 on 2009-06-09
> **vaibhav said:**
> I followed the steps in the guide (the Bleeding edge one). Now my X does not start. Manually typing X on the command line says "Bus error". Any pointers?

Sorry, I'm not supporting these kinds of issues. There are (multiple) warnings not to try the Bleeding Edge configuration unless you know how to fix a broken Xorg setup.

All I can suggest is that you revert the packages (it's in the guide). You can do it via the failsafe terminal, or you can switch to the VESA driver temporarily.

---

### Post by bearozo on 2009-06-09
Thanx psyke83 :) I am still interested in knowing a way to see how "Configured Monitor" is configured though.

---

### Post by vaibhav on 2009-06-10
> **psyke83 said:**
> Sorry, I'm not supporting these kinds of issues. There are (multiple) warnings not to try the Bleeding Edge configuration unless you know how to fix a broken Xorg setup.

All I can suggest is that you revert the packages (it's in the guide). You can do it via the failsafe terminal, or you can switch to the VESA driver temporarily.Thanks for that. But I was trying Bleeding edge since I was hoping to get direct rendering on my 865G. I'll try karmic alpha 2 (when that comes out), and hope that it works good on my PC.

---

### Post by 0Sully on 2009-06-10
Hello Psyke83,

I have gotten as far as the safe options and it is working quite a bit better :) but the one thing I was trying to address still has issues. :( Thats using software in wine that has video and flash in the program.  

I was attempting to get the kernel for your Optimal config when I encountered this problem.  I can download it just fine.  It saves all 3 files.  When running your next command it gives this.

1. Download & install the 2.6.29.4 kernel, based on your architecture:

**i386 users:**
 	Code:
$ sudo dpkg -i linux-headers-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb linux-headers-2.6.30-020630rc8_2.6.30-020630rc8_all.deb linux-image-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb
[sudo] password for sully: 
dpkg: error processing linux-headers-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing linux-headers-2.6.30-020630rc8_2.6.30-020630rc8_all.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing linux-image-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb
 linux-headers-2.6.30-020630rc8_2.6.30-020630rc8_all.deb
 linux-image-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb


I am wondering why?  And how do I get it to see the downloaded files?  I am kind of new to Ubuntu but, I like to learn the nit and gritty way.  I read your warnings and understand the risks.  This is an old lapi that I plan on using just for this kind of learning. :p

I am on an Dell Inspiron 500M with the 855G chip set.
Thanks, 
Sully

---

### Post by Orographic on 2009-06-10
> **simmerz said:**
> I want to say my thanks to psyke83 as well. Now running with the optimal settings on an EeePC 901 and it feels so much more responsive.

Thanks again.

That's interesting as I have recently installed Eeebuntu on my 701. Its just great compared to the stock Xandros but video in iView is a bit rough. Media Player video is great though. I may not try this fix though, not sure how it would go on my little beast.

---

### Post by psyke83 on 2009-06-10
> **0Sully said:**
> Hello Psyke83,

I have gotten as far as the safe options and it is working quite a bit better :) but the one thing I was trying to address still has issues. :( Thats using software in wine that has video and flash in the program.  

I was attempting to get the kernel for your Optimal config when I encountered this problem.  I can download it just fine.  It saves all 3 files.  When running your next command it gives this.

1. Download & install the 2.6.29.4 kernel, based on your architecture:

**i386 users:**
 	Code:
$ sudo dpkg -i linux-headers-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb linux-headers-2.6.30-020630rc8_2.6.30-020630rc8_all.deb linux-image-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb
[sudo] password for sully: 
dpkg: error processing linux-headers-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing linux-headers-2.6.30-020630rc8_2.6.30-020630rc8_all.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing linux-image-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb
 linux-headers-2.6.30-020630rc8_2.6.30-020630rc8_all.deb
 linux-image-2.6.30-020630rc8-generic_2.6.30-020630rc8_i386.deb


I am wondering why?  And how do I get it to see the downloaded files?  I am kind of new to Ubuntu but, I like to learn the nit and gritty way.  I read your warnings and understand the risks.  This is an old lapi that I plan on using just for this kind of learning. :p

I am on an Dell Inspiron 500M with the 855G chip set.
Thanks, 
Sully

You appear to have followed the wrong instructions (you pasted the first part of the Optimal instructions, and the second part from Bleeding-Edge).

---

### Post by Mike.lifeguard on 2009-06-10
For those using bleeding-edge:
An update within the past ~72h seems to have a regression causing freezes - avoid it if you can.

I imagine there's a log of system updates somewhere, right? Anyone know if there's a simple way to un-update something? :D

---

### Post by ferossan on 2009-06-10
Just upgraded to 2.6.30 Kernel (from 2.6.29-4) using -Optimal- configuration (still keeping ubuntu-x-swat/x-updates drivers) and using EXA.
Results: I didn't see any difference. Same good performance on Planet Penguin Racer ~25 to ~32 no matter wich kernel.
Switching to UXA, same good performance with 2.6.30 but worst with 2.6.29-4
So, looks like 2.6.30 is a keeper. Now just wondering if I should use UXA or EXA (keeping my ubuntu-x-swat/x-updates drivers, I don't want to try xorg-edgers PPA drivers)

I have a Intel Corporation Mobile GM965/GL960 and I have set my xorg.conf this way:
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" # i8xx users: set to false
EndSection

---

### Post by psyke83 on 2009-06-10
> **Mike.lifeguard said:**
> For those using bleeding-edge:
An update within the past ~72h seems to have a regression causing freezes - avoid it if you can.

I imagine there's a log of system updates somewhere, right? Anyone know if there's a simple way to un-update something? :D

Yes: read the changelogs (via the xorg-edgers packages and upstream git). As I said in the guide, I won't provide support for the Bleeding Edge stuff.

You can sometimes grab the previous build of a package by browsing the pool directory where the deb files are saved. Launchpad doesn't appear to store older builds from PPAs.

---

### Post by Mike.lifeguard on 2009-06-10
> **psyke83 said:**
> Yes: read the changelogs (via the xorg-edgers packages and upstream git). As I said in the guide, I won't provide support for the Bleeding Edge stuff.

I've decided I don't much like launchpad, but I did manage to find one relevant commit in xorg-edgers PPA. Still trying to figure out where I'm supposed to report bugs for that repo...

---

### Post by psyke83 on 2009-06-10
> **Mike.lifeguard said:**
> I've decided I don't much like launchpad, but I did manage to find one relevant commit in xorg-edgers PPA. Still trying to figure out where I'm supposed to report bugs for that repo...

As far as I know, you're not supposed to file bugs against packages in PPAs unless the developers explicitly ask you to do so.

The purpose of the xorg-edgers PPA is to experiment with the latest xorg code which is updated frequently, and filing bugs against a constantly moving target doesn't make a lot of sense. It almost makes more sense to report bugs upstream (but they may be rejected if the xorg-edgers packages have Ubuntu patches applied).

---

### Post by psyke83 on 2009-06-10
> **ferossan said:**
> Just upgraded to 2.6.30 Kernel (from 2.6.29-4) using -Optimal- configuration (still keeping ubuntu-x-swat/x-updates drivers) and using EXA.
Results: I didn't see any difference. Same good performance on Planet Penguin Racer ~25 to ~32 no matter wich kernel.
Switching to UXA, same good performance with 2.6.30 but worst with 2.6.29-4
So, looks like 2.6.30 is a keeper. Now just wondering if I should use UXA or EXA (keeping my ubuntu-x-swat/x-updates drivers, I don't want to try xorg-edgers PPA drivers)

I have a Intel Corporation Mobile GM965/GL960 and I have set my xorg.conf this way:
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" # i8xx users: set to false
EndSection

Well, you will gain no benefits from EXA as it is no longer maintained in the Intel driver, and still uses DRI1 - the focus on development is on UXA/DRI2. The 2.8 driver will no longer support EXA (the current xorg-edgers driver version has already removed support as well).

---

### Post by psyke83 on 2009-06-10
> **bearozo said:**
> Thanx psyke83 :) I am still interested in knowing a way to see how "Configured Monitor" is configured though.

The xorg.conf file is mostly obsolete - the empty sections (including "Configured Monitor") are provided if users need to apply non-standard customizations; otherwise, everything is autodetected. Customizing of screen properties is handled via XRandR, which is what the GNOME graphical utilities use.

---

### Post by Mike.lifeguard on 2009-06-10
> **psyke83 said:**
> As far as I know, you're not supposed to file bugs against packages in PPAs unless the developers explicitly ask you to do so.

The purpose of the xorg-edgers PPA is to experiment with the latest xorg code which is updated frequently, and filing bugs against a constantly moving target doesn't make a lot of sense. It almost makes more sense to report bugs upstream (but they may be rejected if the xorg-edgers packages have Ubuntu patches applied).

I switched to x-swat/x-updates and all seems fine (for now).

As for bug reporting - if the code is broken, presumably whoever wrote it wants to know. OTOH, I definitely do not understand the large-scale structure of how ubuntu code is developed. For example, I don't understand why there isn't a single central repo where I can get revision X and use it if I want to. Instead we have different people releasing tagged versions in various states of stability. Very confusing - for now at least.

---

### Post by psyke83 on 2009-06-10
> **Mike.lifeguard said:**
> I switched to x-swat/x-updates and all seems fine (for now).

As for bug reporting - if the code is broken, presumably whoever wrote it wants to know. OTOH, I definitely do not understand the large-scale structure of how ubuntu code is developed. For example, I don't understand why there isn't a single central repo where I can get revision X and use it if I want to. Instead we have different people releasing tagged versions in various states of stability. Very confusing - for now at least.

The Xorg and Mesa code is not developed by Canonical employees, it is developed by the people involved in the freedesktop.org/Mesa/Xorg projects. The xorg-edgers PPA is merely one or more persons (Sarvatt and possibly others) packaging daily snapshots of the current git code from upstream for consumption by Ubuntu testers.

Here's the web interface for the Intel git repository, as an example: [http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/)

If you want to file bugs, file them on [https://bugs.freedesktop.org](https://bugs.freedesktop.org) - but I'm not sure that it is ideal to do it this way.

Upstream generally prefer for users to test code that is either in a stable series (such as the stable Intel 2.7.1 driver), *or* the latest code from git, so they can effectively perform troubleshooting via the features of git (e.g. bisecting changes). You're not in a position to provide this kind of in-depth help, because you are relying on code that someone else compiled.

---

### Post by joemun on 2009-06-10
Here is an article addressing the issue with the new kernel and intel drivers...

[http://www.linuxpromagazine.com/online/news/ubuntu_9_04_new_intel_graphics_drivers](http://www.linuxpromagazine.com/online/news/ubuntu_9_04_new_intel_graphics_drivers)

---

### Post by psyke83 on 2009-06-10
I've updated the guide to account for the final 2.6.30 kernel release - with this update, the Optimal and Bleeding-Edge configuration both use this kernel (as it should be as stable as 2.6.29 for Optimal users).

---

### Post by bearozo on 2009-06-11
Thanx again :) 
Yes with a lot of searching I have found some info on XRandR, something new to look into :)
 
I wonder if a change from
 
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```
 
to
 
```
Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Monitor0"
    Device        "Configured Video Device"
EndSection

```

would be better if one wants to add HorizRate and VertSync etc.  ?
 
> **psyke83 said:**
> The xorg.conf file is mostly obsolete - the empty sections (including "Configured Monitor") are provided if users need to apply non-standard customizations; otherwise, everything is autodetected. Customizing of screen properties is handled via XRandR, which is what the GNOME graphical utilities use.

---

### Post by 0Sully on 2009-06-11
Thanks much Psych83.  I'm only blind in one eye.  I just cant see out of the other.  :oops:

Movies and web based flash is now working flawlessly!  Unfortunately, the real purpose of this was to get programs running in Wine to work better and this was no help there.    Wine is still very very slow and video in wine is unusable/unwatchable and the sound does not work.

Does anyone know of a fix for that and where to look?  My eyes are obviously tired if I spent 3 hours yesterday skipping from Optimal to Bleeding and not even realizing it!

Thanks,
Sully

---

### Post by joemun on 2009-06-11
I have an Asus eee 900 linux version (4GB/16GB SSD) with Ubuntu 9.04 and did the optimal configuration (with the 2.6.30 kernel, the video issues i had were solved!... 
Thanks psyke83.

---

### Post by mabovo on 2009-06-11
Planet Penguim Racer is freezing X with 2.6.30 and xserver-xorg-video-intel version 2:2.7.99.901+git20090610.9d3c3b05-0ubuntu0sarvatt~jaunty.

---

### Post by markbl on 2009-06-11
> **mabovo said:**
> Planet Penguim Racer is freezing X with 2.6.30 and xserver-xorg-video-intel version 2:2.7.99.901+git20090610.9d3c3b05-0ubuntu0sarvatt~jaunty.
mabovo, what intel graphics are you using? I am using 945GM and have found all the recent x-edgers intel drivers to be problematic. git20090601 worked ok for me but all versions from there to today (i.e. the one you also report above) have locked up my X in various ways. Others here have reported it as well (e.g. Paul Merchant and zevel).

In fact, I think the x-edgers ppa is too unreliable and the best approach is to use the optimal x-swat ppa. That is what I am doing from today since kernel 2.6.30.

---

### Post by densou on 2009-06-11
> **markbl said:**
> mabovo, what intel graphics are you using?

his log reports: "i945GM rev 3" (I have i945gm rev 2 and no issues anymore with OGL games :D now running final 2.6.30+2.7.99.901)
but it seems X stuff has still some problems with laptop panels (note: LVDS option is enabled by default now)

I use an old 17" TFT (connected with D-sub). I was able to auto-detect both my monitors (TFT & CRT) -since Gutsy!- only editing Xorg.conf in this way:

```
Section "Device"
	Identifier 	"intel" #*Configured Video Device* must be discarded
	Driver 		"intel"
	Option		"AccelMethod"	"UXA"
EndSection
```


P.S. woah, X.log states that VideoRam option is now useless and suggest to remove it :o

---

### Post by mabovo on 2009-06-11
The prior driver was working nice !

---

### Post by i speak in math on 2009-06-11
After foolishly following the optimal directions (like several others may have), I have killed my broadcom wireless ndiswrapper driver. I have tried to revert the settings but when trying to remove the 2.6.30 kernel, it tells me it can't because it isn't present. All other steps seems to be done. But my wireless isn't back.

The "windows wireless driver" tells me the hardware is present and that the driver is already installed. But "hardware drivers" lists no proprietary drivers. 

Argg, what to do?

---

### Post by michael.conner on 2009-06-11
Sweet. 64-bit Flash plugin has better, smoother video performance now under Linux on my laptop than the 32-bit version did under Vista.

DVD / XviD playback now completely smooth, no tearing whatsoever. Thanks!

---

### Post by svtguy88 on 2009-06-11
Just installed a whole host of updates (well, the owner of the computer did, so I don't know exactly what was installed), and high(er) def online video streams much better now (like Hulu's "hi-def" option).  Only problems I've noticed is the video not matching up to the audio 100%, but it never got too bad.

I should note that I'm using kernel RC7 and the bleeding edge Intel driver (as of about two weeks ago).

---

### Post by soul_rebel on 2009-06-11
How about using /etc/rc.local for fixing mtrr? It's easier and cleaner. Is there anything against it?

---

### Post by wabbster on 2009-06-11
LOVELY! Display is much much much... much smoother now! Thanks a ton for this very helpful HOWTO! :)

---

### Post by LinuxUserW on 2009-06-11
well i have a problem, i did the safe optimal configuration. The screen speeded up but the problem is that there seem to be some sort of distortion in some programs. For example when i run glxgears the image seem distorted. There are white lines above the image. And if a run openoffice the menu is distorted too and soon after that the screen crashes and i have to reboot. Anyone has a solution??

---

### Post by markbl on 2009-06-11
> **densou said:**
> I have i945gm rev 2 and no issues anymore with OGL games :D now running final 2.6.30+2.7.99.901
but it seems X stuff has still some problems with laptop panels (note: LVDS option is enabled by default now)

Yes, I am using 945GM on my Dell 640m laptop. I'm also often using a second external monitor as well (vertically stacked due to Virtual screen horizontal limitation with UXA and 945 - grrr) so maybe that is pushing it a bit more?

---

### Post by densou on 2009-06-11
> **soul_rebel said:**
> Is there anything against it?

psyke83 already wrote why, GDM only can catch up MTRR fix on every Gnome Session. It means if you add the MTRR fix into your *rc.local* it won't run after restarting X (with old **ctrl+alt+backspace** replaced with **AltGr+Print+K** -THERE'S NO NEED to add "dont zap" onto xorg.conf, imo-).


-ot- wanna adopt an unanswered post ? :p click below, tnks....

> **markbl said:**
> I'm also often using a second external monitor as well (vertically stacked due to Virtual screen horizontal limitation so maybe that is pushing it a bit more?

That's it, imo .... and I doubt it will be fixed due to GMA950 (i945) hardware limitations while i965 owners need to wait a bit more. ;) (perhaps 'til 2.9.0 ? or 3.0.0 ?)

---

### Post by markbl on 2009-06-11
> **densou said:**
> 
That's it, imo .... and I doubt it will be fixed due to GMA950 (i945) hardware limitations while i965 owners need to wait a bit more. ;) (perhaps 'til 2.9.0 ? or 3.0.0 ?)
densou, you seem to know what you are talking about. Can you please explain something about this problem which I have not seen explained anywhere. What is this suddenly a "hardware limitation" when Virtual screen worked perfectly with EXA on intrepid and earlier ubuntu's?

---

### Post by david_lynch on 2009-06-12
This was very helpful, thanks! After this straightforward procedure (I picked the "optimal" path) my i945-equipped jaunty system went from being like molasses, to being farly snappy.:D

---

### Post by wersdaluv on 2009-06-12
There's a problem reverting changes. How do I revert v1.7 Bleeding Edge changes?

---

### Post by jsday187 on 2009-06-12
I'm using the bleeding-edge configuration. I noticed this in my Xorg.0.log
```

(II) intel(0): direct rendering: DRI2 Enabled
(WW) intel(0): Option "AccelMethod" is not used
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used

```

Are those warnings normal? It says that UXA is enabled also.
****

---

### Post by psyke83 on 2009-06-12
> **jsday187 said:**
> I'm using the bleeding-edge configuration. I noticed this in my Xorg.0.log
```

(II) intel(0): direct rendering: DRI2 Enabled
(WW) intel(0): Option "AccelMethod" is not used
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used

```

Are those warnings normal? It says that UXA is enabled also.
****

Yes, they're normal. For older drivers which still support EXA, those options help improve EXA performance (but still don't affect UXA).

---

### Post by psyke83 on 2009-06-12
> **wersdaluv said:**
> There's a problem reverting changes. How do I revert v1.7 Bleeding Edge changes?

Paste the output of any warnings or errors you receive after trying to revert changes. I'm not psychic, so I can't tell what's wrong on your system without some information.

---

### Post by psyke83 on 2009-06-12
> **markbl said:**
> densou, you seem to know what you are talking about. Can you please explain something about this problem which I have not seen explained anywhere. What is this suddenly a "hardware limitation" when Virtual screen worked perfectly with EXA on intrepid and earlier ubuntu's?

From [Intel notes]("http://intellinuxgraphics.org/2009Q1.html"):

> known issues
Work in progress:
- UXA/DRI2:
* Virtual screen size limited to 2048x2048 for pre-965 platforms: [bug #21190]("https://bugs.freedesktop.org/show_bug.cgi?id=21190").

---

### Post by Mike.lifeguard on 2009-06-12
> **wersdaluv said:**
> There's a problem reverting changes. How do I revert v1.7 Bleeding Edge changes?

There are instructions at the bottom of the guide.

---

### Post by markbl on 2009-06-12
> **psyke83 said:**
> From [Intel notes]("http://intellinuxgraphics.org/2009Q1.html"):
psyke83, I've seen those links you posted before and they don't address what I am saying. I can only think you misunderstood my question. My point is that I have had the same laptop for a few years and run quite a few versions on ubuntu on it using a right side external monitor just fine. Now suddenly with the new Xorg and UXA, they suddenly tell me that I can't run a right-side monitor - due to "hardware limitations"! I've only changed the software - not the hardware! It doesn't make sense?

---

### Post by wersdaluv on 2009-06-12
> **psyke83 said:**
> Paste the output of any warnings or errors you receive after trying to revert changes. I'm not psychic, so I can't tell what's wrong on your system without some information.
I was just hoping you can post the package downgrade code from v1.7, but I just thought that you might not have changed it when you posted v1.8.

I had the Bleeding-Egde setting and wanted to revert changes so I can try the Optimal setting. When I ran the downgrade code, I had error messages saying that many of the packages do not have jaunty versions. I resorted to looking at the xorg-edgers ppa and downgrading packages I found there, that are also installed in my system, to versions from x-updates ppa. By doing that, I thought I had the Optimal version already. My system became much smoother, to my surprise. 

I just tried running the package downgrade code again to make sure I have a clean "Optimal" setting. It worked this time. I'm upgrading packages again. I hope this really makes a clean "Optimal" setting.

---

### Post by psyke83 on 2009-06-12
> **wersdaluv said:**
> I was just hoping you can post the package downgrade code from v1.7, but I just thought that you might not have changed it when you posted v1.8.

I had the Bleeding-Egde setting and wanted to revert changes so I can try the Optimal setting. When I ran the downgrade code, I had error messages saying that many of the packages do not have jaunty versions. I resorted to looking at the xorg-edgers ppa and downgrading packages I found there, that are also installed in my system, to versions from x-updates ppa. By doing that, I thought I had the Optimal version already. My system became much smoother, to my surprise. 

I just tried running the package downgrade code again to make sure I have a clean "Optimal" setting. It worked this time. I'm upgrading packages again. I hope this really makes a clean "Optimal" setting.

You can look in Synaptic, Status, "Installed (local or obsolete)". If any Mesa/Xorg/libdrm2 packages are listed in this section, it may mean that you still have packages remaining from the xorg-edgers repository and you can downgrade these packages in Synaptic.

The apt package management system isn't really designed to do graceful downgrades, so my instructions to revert settings are a guess of the most likely packages that need to be reverted on a typical user's system. If you have a lot of -dev packages installed, for example, the instructions may fail.

---

### Post by psyke83 on 2009-06-12
> **markbl said:**
> psyke83, I've seen those links you posted before and they don't address what I am saying. I can only think you misunderstood my question. My point is that I have had the same laptop for a few years and run quite a few versions on ubuntu on it using a right side external monitor just fine. Now suddenly with the new Xorg and UXA, they suddenly tell me that I can't run a right-side monitor - due to "hardware limitations"! I've only changed the software - not the hardware! It doesn't make sense?

I didn't misunderstand your question, you just assumed that I would know the answer. I'm not involved in the development of the intel driver, so I don't know (but the bug report is the best place to find out, isn't it?). My guess is that the new memory management employed by DRI2 and UXA (GEM - Graphics Execution Manager) has different requirements to operate than the previous EXA/DRI1 code, which didn't even use a unified method of memory management.

---

### Post by shadyzay on 2009-06-12
I successfully followed the optimal approach, everything was great. I've been updating the kernel as the rc's were released. I have even stopped using the mttr bug fix ( since rc5 I guess ).
Now I just installed the 2.6.30 kernel, I'm having a new issue with occasional corruption in KDE task bar. I have attached a snapshot. any ideas?

EDIT: I'm using xserver-xorg-video-intel Version: 2:2.7.0-1ubuntu2~xup~1 and not the later versions because of [bug #360319]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319")

---

### Post by wersdaluv on 2009-06-12
Those using the Optimal setting, have you managed holding back the upgrade of the xserver-xorg-input-synaptics driver? The package upgrade from the X Updates repository makes the touchpad act weirdly. 

I forced install the version from the official repos but the package manager still notifies me to upgrade to the version from X Updates. How do I stop that?

---

### Post by Digit0 on 2009-06-12
Thanks a lot for the tutorial, very elaborated. That totally did the trick for me.

---

### Post by tayran on 2009-06-13
Thanks for this thread. 

It solved all the display problems of my lenovo r61i having intel gm965 chipset. I am running Kubuntu Jaunty and KDE 4.2.2. I have applied optimal configuration and without any issues i followed step by step all the instructions and as a result:

1) Beforehand scrolling in dolphin, okular, FF was a torture, so slow and not responding well. Now it is flawless like it should be.
2) PP Racer score rose to 36-42fps from 20-24 fps. Almost doubled.
3) Now composite effects are also bearable

:popcorn:

Thank you also for continously updating the thread with latest information. Inclusion of the 2.6.30 kernel was excellent.

---

### Post by kwaanens on 2009-06-13
> **wersdaluv said:**
> Those using the Optimal setting, have you managed holding back the upgrade of the xserver-xorg-input-synaptics driver? The package upgrade from the X Updates repository makes the touchpad act weirdly. 

I forced install the version from the official repos but the package manager still notifies me to upgrade to the version from X Updates. How do I stop that?

In Synaptic, have the official repo package installed, to to Package > Lock version
Done.

---

### Post by densou on 2009-06-13
> **markbl said:**
> It doesn't make sense?

which laptop do you own and which external display did you use ?
Tell us more info. ;)

> **kwaanens said:**
> Done.

God ettermiddag :-({|=




[SIZE="1"]-ot- I still have a thing for Norge despite I moved back to this awful hot place :oops: [/SIZE]

---

### Post by Gellule Xg on 2009-06-13
Many thanks to [psyke83]("http://ubuntuforums.org/member.php?u=50843") for putting this guide together.
I have an intel 965GM on a MacBook, Planet Penguin Racer FPS went up from ~4 in the Safe configuration, to ~50 in the Optimal configuration.

Best wishes,

Gellule

---

### Post by bearozo on 2009-06-13
I found this ```
     Option      "AddARGBVisuals"     "True"
     Option      "AddARGBGLXVisuals"  "True"
```here:[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61#Compiz]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T61#Compiz")

What do they do and are they a good idea or not ?

---

### Post by psyke83 on 2009-06-13
> **bearozo said:**
> I found this ```
     Option      "AddARGBVisuals"     "True"
     Option      "AddARGBGLXVisuals"  "True"
```here:[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61#Compiz]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T61#Compiz")

What do they do and are they a good idea or not ?

Useless. The wiki is inaccurate; those options are for the proprietary NVIDIA driver (and those options are now obsolete even for NVIDIA users).

---

### Post by bearozo on 2009-06-13
Thanx for a prompt answer :)

> **psyke83 said:**
> Useless. The wiki is inaccurate; those options are for the proprietary NVIDIA driver (and those options are now obsolete even for NVIDIA users).

---

### Post by markbl on 2009-06-13
> **densou said:**
> which laptop do you own and which external display did you use ?
densou, it has nothing to do with my specific laptop or monitor. Have a look at the bugs referenced by psyke83 many times in this thread [https://bugs.freedesktop.org/show_bug.cgi?id=21190](https://bugs.freedesktop.org/show_bug.cgi?id=21190) and [https://bugs.freedesktop.org/show_bug.cgi?id=10479](https://bugs.freedesktop.org/show_bug.cgi?id=10479). Nobody running UXA with earlier than 965 can run a virtual screen with total horizontal res >2048. My laptop is 1400x900 and my monitor is 1280x1024. A pretty stock arrangement that is not catered for by the new xorg, but which worked fine on earlier ubuntu's.

---

### Post by foxy123 on 2009-06-13
Tried it but my laptop freezes when I try to switch to a different users. Had to comment all changes in xorg.conf.

---

### Post by Orographic on 2009-06-14
I've been using the Safe Configuration for some weeks now on my 945 GZM-S2 Gigabyte system and all is well. Haven't noticed any problems at all, that I can think of.

YouTube and iView have been quite good indeed. I watch iView at least a few times a week and full screen (22 inch) is fine although once I had lag. I normally only view at about 80% screen anyway in this smallish room.

---

### Post by Rizado on 2009-06-14
The new drivers are not so good on my GM45. They are working and with a great performance increase, but many games crash X too... I've tried Simcity 4 and Civilization 4 through wine and both crash. Civilization 4 does it everytime when loading a map and Simcity only sometimes crash during startup.

I have used both bleeding edge and optimized.

---

### Post by bearozo on 2009-06-14
> Originally Posted by S.A.A                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7141627#post7141627")                 
                 I finally found a way to run compiz with:
     Code:
     00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03) 
all you have to do is using "Indirect Rendering" option.
And now my old PC is back to life again (it's even faster than it was with Hardy).


> **bearozo said:**
> Where do I find this option ?

I found this:
 ```
compiz.real --indirect-rendering
``` but I get this:
```
b@b-laptop:~$ compiz.real --indirect-rendering
compiz.real (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real (core) - Fatal: No manageable screens found on display :0.0

```and if I try --replace it starts with just a wallpaper and a working mouse pointer i.e like this "I" allmost as if I just start compiz, I get the same but with and ordinary arrow as pointer.

Have to REISUB out of it.

I do not know what that other window manager would be ?

---

### Post by kd0afk on 2009-06-14
I went all the way to the Bleeding edge and it still didn't fix the problems I am having with Blender. The only thing it did was to make my mouse track pad VERY choppy.
How do I undo everything I did on this thing?

---

### Post by Mike.lifeguard on 2009-06-14
> **kd0afk said:**
> I went all the way to the Bleeding edge and it still didn't fix the problems I am having with Blender. The only thing it did was to make my mouse track pad VERY choppy.
How do I undo everything I did on this thing?

Look towards the bottom of the guide - it tells you exactly how to revert your changes.

---

### Post by Mike.lifeguard on 2009-06-14
> **psyke83 said:**
> Launchpad doesn't appear to store older builds from PPAs.

Actually, it appears they do, at least for some stuff. For example, I can get .debs for "superseded" (ha!) stuff in the xorg-edgers PPA. I'm going to try each and every one starting from now and going backwards until I find one that works. Wish me luck!

---

### Post by bearozo on 2009-06-14
I get this with the latest updates, Linux 2.6.30-020630-generic etc. :

```
b@b-laptop:~$ egrep "(GLX|DRI)" /var/log/Xorg.0.log
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading extension XFree86-DRI
(II) Loading extension DRI2
(II) intel(0): [DRI2] Setup complete
(II) intel(0): 0x007df000-0x07ffefff: DRI memory manager (123008 kB)
(II) intel(0): direct rendering: DRI2 Enabled
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
b@b-laptop:~$ grep -i UXA /var/log/Xorg.0.log
(--) intel(0): Using UXA for acceleration
(II) UXA(0): Driver registered support for the following operations:
```using this xorg.conf:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```so I wonder the xorg.conf in the howto is still necessary in the bleeding edge config. ?

i.e. ```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true" **# i8xx users: see note in guide**
EndSection
```One strange thing though, after this line nothing is listed !
```
(II) UXA(0): Driver registered support for the following operations:
```

---

### Post by psyke83 on 2009-06-14
> **bearozo said:**
> so I wonder the xorg.conf in the howto is still necessary in the bleeding edge config. ?

i.e. ```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true" **# i8xx users: see note in guide**
EndSection
```One strange thing though, after this line nothing is listed !
```
(II) UXA(0): Driver registered support for the following operations:
```

The extra options are unnecessary for the xorg-edgers driver, but they won't cause any harm either (as they're ignored). It's better to leave it in the guide in case users switch back to the Optimal or Safe configuration.

As for nothing being listed after the UXA line, that's merely because UXA is not mentioned on the next lines, so your grep of the log didn't display them. Everything is normal; you merely need to read the log manually to see the information you want.

---

### Post by psyke83 on 2009-06-14
> **Mike.lifeguard said:**
> Actually, it appears they do, at least for some stuff. For example, I can get .debs for "superseded" (ha!) stuff in the xorg-edgers PPA. I'm going to try each and every one starting from now and going backwards until I find one that works. Wish me luck!

Good luck, you'll need it :P. The previous build links are all ghosted for me (perhaps due to space considerations).

However, if you look in the "pool" directories, you may find the previous build: [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/)

---

### Post by psyke83 on 2009-06-14
> **shadyzay said:**
> I successfully followed the optimal approach, everything was great. I've been updating the kernel as the rc's were released. I have even stopped using the mttr bug fix ( since rc5 I guess ).
Now I just installed the 2.6.30 kernel, I'm having a new issue with occasional corruption in KDE task bar. I have attached a snapshot. any ideas?

EDIT: I'm using xserver-xorg-video-intel Version: 2:2.7.0-1ubuntu2~xup~1 and not the later versions because of [bug #360319]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319")

Try to disable KWin compositing (or switch the engine from xrender to opengl, or vice-versa). I don't have an installation of KDE4 right now, so I don't recall precisely where you'll find the options for compositing - you'll need to search yourself.

---

### Post by Mike.lifeguard on 2009-06-14
Well, I started too far back and worked further back, wasting a lot of time.

But, it looks like 2:2.7.99.901+git20090610.9d3c3b05-0ubuntu0sarvatt~jaunty (from xorg-edgers) is working. I was able to get a freeze within minutes on every other version I tried, including other ones reported to be stable (for example 2.7.0-1ubuntu2~xup~1, and 2.7.99.901 +git20090611.6d062e9e-0ubuntu0sarvatt~jaunty)

I'll keep testing.

---

### Post by kd0afk on 2009-06-15
> **Mike.lifeguard said:**
> Look towards the bottom of the guide - it tells you exactly how to revert your changes.
 
Thanks Mike.

---

### Post by Forceflow on 2009-06-15
Using UXA with the X.org drivers from the X-SWAT ppa,and I applied the "safe" configuration. Standard ubuntu jaunty kernel, 2.6.28.13.

Works, but has one big annoyance: my SWAP space fills up slowly, so after 2 or 3 hours the system almost grinds to a halt. Restarting X (= logging out/in) solves the problem ...

Any ideas?

---

### Post by Mike.lifeguard on 2009-06-15
> **Forceflow said:**
> Using UXA with the X.org drivers from the X-SWAT ppa,and I applied the "safe" configuration. Standard ubuntu jaunty kernel, 2.6.28.13.

Works, but has one big annoyance: my SWAP space fills up slowly, so after 2 or 3 hours the system almost grinds to a halt. Restarting X (= logging out/in) solves the problem ...

Any ideas?

I think this is a known bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319)

---

### Post by kd0afk on 2009-06-15
What is the bugzilla link for ubuntu?

---

### Post by psyke83 on 2009-06-15
> **kd0afk said:**
> What is the bugzilla link for ubuntu?

This is not a general help thread. Read the Important Note section of the guide fully.

---

### Post by kd0afk on 2009-06-15
> **psyke83 said:**
> This is not a general help thread. Read the Important Note section of the guide fully.
In the time it took you to scold me, you could have provided the link. If you don't know, then just say so. I asked for the link to the Ubuntu bugzilla because I am having similar graphics problems that need to be addressed and rather than take up important space here I thought it better to post the obvious bug on bugzilla. I was in no way asking for "general help" I posted because of the same issues that the thread starter was having.

---

### Post by psyke83 on 2009-06-15
> **kd0afk said:**
> In the time it took you to scold me, you could have provided the link. If you don't know, then just say so. I asked for the link to the Ubuntu bugzilla because I am having similar graphics problems that need to be addressed and rather than take up important space here I thought it better to post the obvious bug on bugzilla. I was in no way asking for "general help" I posted because of the same issues that the thread starter was having.

I directed you to the answer. Launchpad is Ubuntu's bug tracker (which isn't based on bugzilla), and the section I asked you to read has important information that will let you know whether it is appropriate to file bugs, and the procedure to follow when it is appropriate.

I wasn't scolding you, but your question was more suited to the Absolute Beginners section (or easily found via a search). This thread is already over 80 pages, so it's important to keep it on-topic.

---

### Post by kd0afk on 2009-06-15
> **psyke83 said:**
> I directed you to the answer. Launchpad is Ubuntu's bug tracker (which isn't based on bugzilla), and the section I asked you to read has important information that will let you know whether it is appropriate to file bugs, and the procedure to follow when it is appropriate.

I wasn't scolding you, but your question was more suited to the Absolute Beginners section (or easily found via a search). This thread is already over 80 pages, so it's important to keep it on-topic.
Alright, thanks. 80 pages is pretty big. This thread really shouldn't exist at all. If the graphics aspects of a new release aren't tested clean then the new release shouldn't be released. On a side note, at lease people are replying to this thread.

---

### Post by jperez on 2009-06-15
psyke83, thanks for this!  Although I can't get Compiz to work under GNOME, short of trying to find a way anyway, it seems to have sped up my KDE session noticeably.  I installed Ubuntu, not Kubuntu, initially and yet it starts up on both session at login, but only seems to really work for Kubuntu.  It's not a big deal though.

Highly appreciate the work you put into this so us Intel Graphics people could get more performance where Jaunty initially left us without.

Jesse~

---

### Post by psyke83 on 2009-06-15
> **kd0afk said:**
> Alright, thanks. 80 pages is pretty big. This thread really shouldn't exist at all. If the graphics aspects of a new release aren't tested clean then the new release shouldn't be released. On a side note, at lease people are replying to this thread.

I disagree - the intel driver has been extensively tested. UXA was deemed unstable during the development process of Jaunty, and the decision was made to revert to the older EXA acceleration to avoid many users suffering from system crashes. The trade-off is some performance regressions for some users (with EXA) versus crashes for most users (with UXA). It's documented in Jaunty's [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards"). 

The purpose of this guide is to have stable UXA drivers for those willing to put up with a certain amount of risk from third-party packages. Ubuntu's [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") policy does not allow for significant updates to be released in a distribution's lifetime, so stable UXA acceleration is unlikely to happen officially in Jaunty, except through fixes manually backported to the older version of the intel driver we have in Jaunty.

It's now June, and only in the past two weeks has UXA become stable for my chipset (and only with kernel 2.6.30) - but some issues still need to be addressed. Do you honestly expect that the release of Jaunty in April should have been delayed until June (or later)? I suspect you would have complained even louder.

---

### Post by psyke83 on 2009-06-15
> **jperez said:**
> psyke83, thanks for this!  Although I can't get Compiz to work under GNOME, short of trying to find a way anyway, it seems to have sped up my KDE session noticeably.  I installed Ubuntu, not Kubuntu, initially and yet it starts up on both session at login, but only seems to really work for Kubuntu.  It's not a big deal though.

Highly appreciate the work you put into this so us Intel Graphics people could get more performance where Jaunty initially left us without.

Jesse~

Compiz is probably blacklisted on your card - the compiz packages maintain the blacklist, so newer drivers won't override it. Search the forums for "compiz blacklist" to find workarounds (I've never needed to do it, as my chipset was never blacklisted).

Note that the blacklist for your chipset was present for a reason - EXA/DRI1 must have been causing crashes. Whilst UXA/DRI2 may be more stable, it's equally likely that it will be more unstable. All you can do is test yourself (and be prepared for the consequences ;)).

---

### Post by psyke83 on 2009-06-15
> **Mike.lifeguard said:**
> Well, I started too far back and worked further back, wasting a lot of time.

But, it looks like 2:2.7.99.901+git20090610.9d3c3b05-0ubuntu0sarvatt~jaunty (from xorg-edgers) is working. I was able to get a freeze within minutes on every other version I tried, including other ones reported to be stable (for example 2.7.0-1ubuntu2~xup~1, and 2.7.99.901 +git20090611.6d062e9e-0ubuntu0sarvatt~jaunty)

I'll keep testing.

Have you tested on the official kernel as well as the 2.6.30 kernel? Your problem may be kernel-related. Most of the performance regressions in Jaunty are due to the drm/i915 kernel modules - many fixes for performance and stability have been included in the latest 2.6.30 kernel, but there is also the possibility of regressions too.

---

### Post by psyke83 on 2009-06-15
> **Forceflow said:**
> Using UXA with the X.org drivers from the X-SWAT ppa,and I applied the "safe" configuration. Standard ubuntu jaunty kernel, 2.6.28.13.

Works, but has one big annoyance: my SWAP space fills up slowly, so after 2 or 3 hours the system almost grinds to a halt. Restarting X (= logging out/in) solves the problem ...

Any ideas?

The only difference between Safe and Optimal configuration is the 2.6.30 kernel - perhaps you might consider testing that kernel to see if the memory leak occurs? I had this problem as well, but I don't seem to experience it lately (either via the Bleeding-Edge config, or the Karmic development release which is roughly equivalent to the Bleeding-Edge configuration).

The reason why I'm suggesting this is that many of the UXA/DRI2 fixes have been within the drm/i915 kernel modules.

Pressing ESC while GRUB initializes will display the boot options, so you can easily boot into the Jaunty kernel if you have problems.

---

### Post by Mike.lifeguard on 2009-06-15
> **psyke83 said:**
> Have you tested on the official kernel as well as the 2.6.30 kernel? Your problem may be kernel-related. Most of the performance regressions in Jaunty are due to the drm/i915 kernel modules - many fixes for performance and stability have been included in the latest 2.6.30 kernel, but there is also the possibility of regressions too.

Yes, I'm using .30 (Briefly tried whatever is in jaunty-proposed currently too). Right now, I'm using xserver-xorg-video-intel 2:2.6.3-0ubuntu9.3, which seems reasonably stable. I've had a few hours of freeze-free performance, but I was able to purposefully trigger a freeze early on.

I did notice that things seem far less stable with compiz's wobbly windows enabled (specifically, using shiver on window mapping). There may be something more specific happening with that feature that isn't intel-related -- but that's far from certain.

---

### Post by treesurf on 2009-06-15
When I first installed Jaunty I decided to just revert to the Intrepid intel driver and give this some time to develop.  I just followed the Optimal version of this fix and so far so good!  ppracer is giving me about 30fps, which is acceptable.  GoogleEarth still runs slower than dirt, but I've been having that problem on this laptop since it was first ported to Linux.  I have a a 945GM, by the way.

Thank you psyke!

---

### Post by jperez on 2009-06-15
> **psyke83 said:**
> Compiz is probably blacklisted on your card - the compiz packages maintain the blacklist, so newer drivers won't override it. Search the forums for "compiz blacklist" to find workarounds (I've never needed to do it, as my chipset was never blacklisted).

Note that the blacklist for your chipset was present for a reason - EXA/DRI1 must have been causing crashes. Whilst UXA/DRI2 may be more stable, it's equally likely that it will be more unstable. All you can do is test yourself (and be prepared for the consequences ;)).

Thanks for the reply.  I would find a workaround, however, I'm not really as interested in Compiz on Gnome as I am in KDE, which was working (yet a bit slower) until I did your workaround.  Now Compiz on KDE works faster on my laptop with the minimal effects I have running and that's really all I wanted.  If Compiz worked in Gnome, meaning not being blacklisted, after the workaround, it would have just been a bonus, but it's not an issue.  I like the KDE environment a lot more, especially KDE 4.

Many thanks for the guide and keep up the great work.

Jesse~

---

### Post by hamidoo on 2009-06-16
Thanks for this gr8 guide.
But this WORKS with restricted nvidia drivers as well.
I just add the repository and i got my nvidia drivers updated and working.
I'm using a custom built kernel 2.6.30

---

### Post by tompravi on 2009-06-16
I have an "HP Compaq Presario V4000". The first time I've installed Ubuntu 9.04 I was disappointed for the desktop performance. Yesterday, I've found this guide and installed the new drivers. I had a freezing of desktop - mouse and keyboard. Then, I installed the kernel 2.6.30. Everything works very well ( until now ). The improvement is significance. The deference in desktop performance between old and new drivers - kernel is like the difference between day and night. Now I can keep the ubuntu installation on my notebook. Thank you

PS. Sorry for my english

---

### Post by HotShotDJ on 2009-06-16
> **HotShotDJ said:**
> Just noticed on boot-up "Loading securityfs  [COLOR="Red"][FAILED][/COLOR] (will double check on next boot) -- any idea what this is about and how to fix?A quick update on my previous comments -- it wasn't "Loading securityfs" that was failing, it was loading the AppArmor modules, which is addressed in [Bug #375422]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422").  So, I guess folks who need AppArmor should not be using the "Bleeding Edge" method (no real surprise there).  Other than that, the Bleeding Edge method has worked perfectly for me with my Intel Corporation Mobile 945GM/GMS integrated video card.  As a bonus, it seems that [Bug #193419]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/193419") is fixed (that might have nothing to do with the "Bleeding Edge" changes, but I'm happy about it, nonetheless).

---

### Post by Abdullah Umer on 2009-06-16
I am using intel 82845. I cannot install the kernal 2.6.30-020630.
This is what i get when i install.



abdullah@abdullah-desktop:~$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
(Reading database ... 162706 files and directories currently installed.)
Preparing to replace linux-headers-2.6.30-020630-generic 2.6.30-020630 (using linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb) ...
Unpacking replacement linux-headers-2.6.30-020630-generic ...
Preparing to replace linux-headers-2.6.30-020630 2.6.30-020630 (using linux-headers-2.6.30-020630_2.6.30-020630_all.deb) ...
Unpacking replacement linux-headers-2.6.30-020630 ...
Preparing to replace linux-image-2.6.30-020630-generic 2.6.30-020630 (using linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-020630-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.30-020630 (2.6.30-020630) ...
Setting up linux-image-2.6.30-020630-generic (2.6.30-020630) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-020630-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.30-020630 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.30-020630 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.30-020630-generic                                                   
 *  fglrx (8.602)...                                                                                                         fglrx (8.602): Installing module.
..........(bad exit status: 7)
  Build failed.  Installation skipped.
                                                                                                                      [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-headers-2.6.30-020630-generic (2.6.30-020630) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.30-020630-generic                                                   
 *  fglrx (8.602)...                                                                                                         fglrx (8.602): Installing module.
.......(bad exit status: 7)
  Build failed.  Installation skipped.
                                                                                                                      [fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

abdullah@abdullah-desktop:~$ 


There are FAILURES.

I am unable to have EXTRA visual effects. It cannot be loaded.

Any help???

---

### Post by romualdJ on 2009-06-16
Hello,

I recently upgraded Ubuntu to Jaunty on my old Fujitsu-Siemens Amilo M7400 notebook.
My graphics card is intel 82852/855GM.

I followed the optimal method but after some time got regular freezes of X's. I could ssh remotely, the mouse moved but the keyboard was unresponsive and clicks were ignored.
Initially I could find in the logs that syndaemon caused a segfault in libX11 (I think).
I deactivated syndaemon's but the freezes continued - this time with nothing appearing in the logs. Then I rolled back the modifications of safe/optimal but keeping the fixmbbtr script. Still freezes. Then I erased the fixmbtr script and the freezes still occur!
There does not seem to be anything specific which causes them.

<rant>I was using Linux on this laptop for 5 years I think (going through Fedora, Mandrake and then some releases of Ubuntu and NEVER had any such problem).
I cannot afford to have random freezes when giving talks at conferences - so I guess that I will have to boot into Windows XP for stability - what irony... </rant>

Let me know if someone else has this problem. My current xorg.conf is a bare bones almost empty file (automatically generated) - the only option set is
Option        "UseFBDev"        "true"

I'll be grateful for any hints - if nothing happens I will abandon ship and do a clean install of some other distribution.. :(

Best,
Romuald

---

### Post by HotShotDJ on 2009-06-16
> **romualdJ said:**
> I followed the optimal method but after some time got regular freezes of X's.I had the same problem with all the methods except for the "Bleeding Edge" instructions.  However, I wonder if some of your issue is that you did not edit xorg.conf as instructed in the HowTo at the beginning of this thread:
> **romualdJ said:**
> My current xorg.conf is a bare bones almost empty file (automatically generated) - the only option set is
Option "UseFBDev" "true"
[QUOTE="psyke83"]Find the "Device" section and make sure it looks identical to the following (important: remove or comment any of your previous customizations):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" # i8xx users: see note in guide
EndSection
```[/QUOTE]
I would first try double checking to make sure that you followed all the steps of the HowTo, including the edits to your xorg.conf.  If that doesn't help, you might need to give the "Bleeding Edge" instructions a shot.  However, be sure to keep all of psyke83's warnings and notes to heart!

---

### Post by CJ_Hudson on 2009-06-16
Just upgraded, and chose the 'Optimal' graphics setting for my Intel integrated graphics chipset.
 Video much better, and flickering black bars gone from my favourite game (SuperTuxCart) but for some reason the game runs in slow-motion. Keyboard response sluggish, entire game seems to be running slowly. But at least the black bars have gone!
Any comments?

---

### Post by treesurf on 2009-06-16
A couple days into using the optimal fix and the only problem I've noticed so far is that my Wobbly Windows are kind of jagged and not very smooth.  I can live with that, though.  Hopefully future updates will solve this problem.

---

### Post by Abdullah Umer on 2009-06-17
Hello.
I am using intel 82845 graphics.

This is what i get from terminal.

[I]~$  lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
[/I]

I also have made modification to the *xorg.conf* file. I added the following.[I]

Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false" # i8xx users: see note in guide

EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/I]

I also have installed the kernal

[I]abdullah@abdullah-desktop:~$ uname -a
Linux abdullah-desktop 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:45:40 UTC 2009 i686 GNU/Linux

[/I]My system is running although there was some failures during the installation of this kernal. That i have mentioned in my previous post.

Extra VISUAL effects still cannot be enabled.

I am new to UBUNTU and i need help.

I have spent many hours on the internet to solve this problem. But still cannot find any.

Abdullah

---

### Post by zbugski on 2009-06-17
> **treesurf said:**
> When I first installed Jaunty I decided to just revert to the Intrepid intel driver and give this some time to develop.  I just followed the Optimal version of this fix and so far so good!  ppracer is giving me about 30fps, which is acceptable.  GoogleEarth still runs slower than dirt, but I've been having that problem on this laptop since it was first ported to Linux.  I have a a 945GM, by the way.

Thank you psyke!

I'm running Jaunty on a HP Mini 2140 with the GMA950 card. I can only use the Safe config with stock kernel and updated X drivers - EXA is fast enough for Compiz while enabling UXA means the computer doesn't wake from sleep properly. Using the Optimal or Bleeding Edge configs, while faster, ended up hosing support for the Broadcom Wi-fi card due to the new kernel.

How can I run Intrepid X drivers on a Jaunty install? Can the existing Jaunty stock kernel be used or do I have to switch to the Intrepid kernel? I'd love to eke out a bit more performance in Tuxracer :)

Thanks!

---

### Post by robert114 on 2009-06-17
psyke83,

I'd like to thank you. This guide helped me with my tearing problems on my Intel G31.

Thanx!

---

### Post by S3NATOR on 2009-06-17
Sweet!!! The **_Safe_** **Configuration** worked for me! Here are the results of lspci on my machine:
```
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express (rev 02)

```
FYI I also set "Tiling" to "false" like it says in the Part A Step 1 note. I hope this helps anyone else who has the same chipset/mobo/graphics as me.

I recently upgraded from 8.1 to 9.04 and noticed a bit of a slow down. I noticed my CPU load stayed around 2.00 while running Virtual Box and Firefox. My system was usable but I could definitely feel the slow down. 

I eventually came across this thread and safe config works for me. I haven't tried the Optimal or Bleeding Edge configs but I don't see a need to if the safe config works.

Thank you psyke83 and all the contributors for this thread!

S3N

---

### Post by romualdJ on 2009-06-17
Thanks - I had all the xorg.conf options from the guide... - I was quite careful when doing that.
The barebones xorg.conf that I have now was obtained after rolling back..
Best,
Romuald

---

### Post by treesurf on 2009-06-17
> **zbugski said:**
> I'm running Jaunty on a HP Mini 2140 with the GMA950 card. I can only use the Safe config with stock kernel and updated X drivers - EXA is fast enough for Compiz while enabling UXA means the computer doesn't wake from sleep properly. Using the Optimal or Bleeding Edge configs, while faster, ended up hosing support for the Broadcom Wi-fi card due to the new kernel.

How can I run Intrepid X drivers on a Jaunty install? Can the existing Jaunty stock kernel be used or do I have to switch to the Intrepid kernel? I'd love to eke out a bit more performance in Tuxracer :)

Thanks!

Here are instructions for reverting to the Intrepid intel drivers.  There's no need to install a different kernel, the stock Jaunty kernel works fine for this.  It's also really easy to switch back to the Jaunty drivers if this doesn't work out for you.  How to is here:

[http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html](http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html)

Best of luck!

---

### Post by bearozo on 2009-06-17
> **Abdullah Umer said:**
> Hello.
I am using intel 82845 graphics.

This is what i get from terminal.

[I]~$  lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
[/I]


Extra VISUAL effects still cannot be enabled.

I am new to UBUNTU and i need help.

I have spent many hours on the internet to solve this problem. But still cannot find any.

Abdullah

I have the same graphic chip and it is blacklisted in Compiz, hence no visual effects :(

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by treesurf on 2009-06-17
The 2.6.30 kernel is pretty buggy when it comes to resume from suspend. :(

---

### Post by Mike.lifeguard on 2009-06-17
> **Mike.lifeguard said:**
> Yes, I'm using .30 (Briefly tried whatever is in jaunty-proposed currently too). Right now, I'm using xserver-xorg-video-intel 2:2.6.3-0ubuntu9.3, which seems reasonably stable. I've had a few hours of freeze-free performance, but I was able to purposefully trigger a freeze early on.

I did notice that things seem far less stable with compiz's wobbly windows enabled (specifically, using shiver on window mapping). There may be something more specific happening with that feature that isn't intel-related -- but that's far from certain.

Looks like I was right. Freeze-free performance (using xserver-xorg-video-intel 2:2.7.99.1+git20090605.66ceedc0-0ubuntu0sarvatt2~jaunty) since that post until now after disabling wobbly windows, even when trying to induce freezes purposefully. Where should compiz bugs get reported?

---

### Post by psyke83 on 2009-06-17
> **Mike.lifeguard said:**
> Looks like I was right. Freeze-free performance (using xserver-xorg-video-intel 2:2.7.99.1+git20090605.66ceedc0-0ubuntu0sarvatt2~jaunty) since that post until now after disabling wobbly windows, even when trying to induce freezes purposefully. Where should compiz bugs get reported?

Don't report these kind of bugs against compiz - it's clearly an Intel driver bug. Read the guide thoroughly (Important Note -> Reporting Bugs) - you're using xorg-edgers, so you can't report bugs to Launchpad. You can report them upstream if you want, though.

---

### Post by cywhale on 2009-06-17
Thank you very much for this thread - just made me stop returning to arch linux for now :)
Compiz runs fine on a Thinkpad T61 w. X3100 using the "bleeding edge" method.

---

### Post by d3athp3nguin on 2009-06-17
To: the person who made this guide.

You rock.

That is all.

---

### Post by Mike.lifeguard on 2009-06-17
> **psyke83 said:**
> Don't report these kind of bugs against compiz - it's clearly an Intel driver bug. Read the guide thoroughly (Important Note -> Reporting Bugs) - you're using xorg-edgers, so you can't report bugs to Launchpad. You can report them upstream if you want, though.

I think you've already told me twice that I can't report bugs to launchpad for this stuff, and I knew that already anyways. I didn't suggest reporting anything to Launchpad - however, the code is broken, and whoever writes it will care. So, yes: I will probably report it upstream (Ubuntu doesn't run the sole bug tracker in the universe & bugs in bleeding-edge code should be reported to the corresponding bug tracker). I appreciate that you're trying to keep cruft out of Launchpad, but this is becoming excessive and/or insulting.

On a more constructive note: Can you help me understand why this issue is "clearly" an intel driver bug? I'd rather not report it to the wrong upstream bug tracker if I can help it.

I thought I had fairly clearly shown (with limited resources - I have only this Intel machine available for testing) that the xserver-xorg-video-intel code is stable *except* in the case of wobbly windows (and in particular with shiver on mapping), and so it was actually a problem with that code (compiz's wobbly windows/shiver-on-mapping code). I guess that'd be easily proven false if it doesn't freeze with other graphics cards, but I didn't notice that anyone specifically tested that.

---

### Post by Andreas1 on 2009-06-18
I have an intel 915 chipset and use the "optimal" configuration, performance has improved (2d firefox scrolling, 3d sauerbraten fps), and scrolling in firefox got a bit better when i disabled the suggested xorg options except the "greedy" one again. (i think it was actually disabling "uxa" that caused slight improvement). however, booting the new kernel i get nothing on the tty except a black screen. with the old kernel it still works. still worth it though, and i am optimistic i will fix the tty issue. could it be related to the manual "vga=792" setting i added to the grub entry?

EDIT: so here is the xorg.conf that works best for me, in combination with the "optimal" configuration:

```
Section "Device"
	Identifier	"Configured Video Device"
	#Option		"AccelMethod"			"uxa"
	#Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	#Option		"Tiling"			"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by cuginguilu4 on 2009-06-18
I have problem, my computer model is HP6720s, and when I install the newest version of the kenel, the Interner drivers deactivate by themself. I had to remove it to get my Internet back. What should I do to install the newest kernel and stay with the internet drive? :\

I got this from lspci: 

00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by cyper on 2009-06-18
Just had a problem: could not start compiz after fresh mesa update. had to revert to manually downloaded mesa packadges one step back (should say they worked perfectly). I just got out from digging in logs - found nothing I could filter out like weird.
Problem looked like (all i can tell, after all):
1. updated
2. Logging out to restart X-server
3. Gnome flashscreen.
4. empty (!) panel comes out.
5. All screenlets jerk up, regardless their settings (part of them are on widget screen so they must not be in view).
6. An thats all. No awn, still nothing on panel, transparent screenlets appear spotty and unreadable, no compiz effects, but system works - i can open any program via Alt-F2 or terminal screenlet which is not transparent as it should be - just while on black.
Finally I was able to populate the gnome-panel through opening its Preferences (rightclick menu) and switching stretch option to and fro.
But i could not: automatically got that all done after logon (at least!), and still no compiz effects, no normal screenlets.

Now I have everything back by downloading previous iteration of mesa stuff (6 packets) from ppa.launchpad*/xorg-edgers/* and dpkg -i 'ing them.

Does anyone had any issues with mesa-7-5-branch.39366ed9-0ubuntu0sarvatt packages?

---

### Post by Mike.lifeguard on 2009-06-18
> **cyper said:**
> Just had a problem: could not start compiz after fresh mesa update...

Does anyone had any issues with mesa-7-5-branch.39366ed9-0ubuntu0sarvatt packages?

So, what mesa code are you using now?

---

### Post by Mike.lifeguard on 2009-06-18
> **Andreas1 said:**
> ...booting the new kernel i get nothing on the tty except a black screen. with the old kernel it still works. still worth it though, and i am optimistic i will fix the tty issue. could it be related to the manual "vga=792" setting i added to the grub entry?


Yes, remove that from the grub entry to fix your terminals and boot messages. I had the same problem, which led me to start [http://ubuntuforums.org/showthread.php?p=7457110](http://ubuntuforums.org/showthread.php?p=7457110)

---

### Post by cyper on 2009-06-18
> **Mike.lifeguard said:**
> So, what mesa code are you using now?

Im currently using mesa packages *+mesa-7-5-branch.d027e8fe-0ubuntu0sarvatt, as the day before ;)

---

### Post by Mike.lifeguard on 2009-06-18
> **cyper said:**
> Im currently using mesa packages *+mesa-7-5-branch.d027e8fe-0ubuntu0sarvatt, as the day before ;)

Thanks - your wording was confusing because that's not the second-most-latest version, but rather the third-most-latest :D

---

### Post by cyper on 2009-06-18
> **Mike.lifeguard said:**
> Thanks - your wording was confusing because that's not the second-most-latest version, but rather the third-most-latest :D

Ok, im not thoroughly sure that it is "second-latest" version of mesa - it is second-latest for me. *+mesa-7.6-* which is present on the PPA, is not currently a part of "bleeding-edge configuration". At least it isnt proposed for installation via apt-get on my computer. And *+mesa-7-5-branch.39366ed9-0ubuntu0sarvatt was uploaded on a PPA today at 6:25 AM (+2:00 GMT) - thats why i supposed it was the latest one ;)
Anyway i'm interested if someone can expand the situation with usefull comments.. :)
Thanks!

P.S.: Aha - i see, if you're talking about mesa-7.6: it is for Karmic. For Jaunty my wording seems to be correct.

---

### Post by DizzyTech on 2009-06-18
Mike, you seem to be on track.  I have all the latest from Xorg-edgers - including 2.6.30-9 - and disabling wobbly windows has given me no crashes for an hour.  Firefox didn't even slow down with the infamous Singapore picture.  Not sure whether this is Intel or Compiz.  Due to the nature of the bug as explained on Launchpad, it appears that wobbly windows does... um, something to cause the past-the-end-of-the-aperture freeze bug... but Intel has the bug fixed, according to them.  Hmm.
:popcorn:  I'll be waiting...

---

### Post by treesurf on 2009-06-18
What's the infamous Singapore picture?

---

### Post by DizzyTech on 2009-06-18
It's this huge panorama of a port in Singapore hosted on Wikimedia that, among other triggers, has proved to be a trigger of the bug on most systems.  I use it constantly for checking.

---

### Post by chronniff on 2009-06-19
I have been using the compiz Loose Binding option to get a significant boost in the compiz effects smoothness while using uxa, anyone have any idea what it does, the only research I have found is that you shouldn't use it on intel cards, but it seems to be helping with my 965 card

---

### Post by bearozo on 2009-06-19
You are lucky you all that get compiz to work I still have no luck, I can start it but all I get is wallpaper and a working mouse pointer with my blacklisted Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) :( **if anyone knows about or find a fix please give a holler.**
On the other hand everything else seems fine, I get 35-40 fps in ppracer and 400-420 fps in glxgears which I suppose is quite good with that chipset on an old P4.

---

### Post by bearozo on 2009-06-19
> **DizzyTech said:**
> It's this huge panorama of a port in Singapore hosted on Wikimedia that, among other triggers, has proved to be a trigger of the bug on most systems.  I use it constantly for checking.

Please give a link to said picture if this is not the one:[http://upload.wikimedia.org/wikipedia/commons/a/a2/Singapore_Panorama_v2.jpg ]("http://upload.wikimedia.org/wikipedia/commons/a/a2/Singapore_Panorama_v2.jpg")
Which btw. also works fine :)
I use the bleeding edge, updated intel drivers and mesa.

---

### Post by psyke83 on 2009-06-19
> **DizzyTech said:**
> Mike, you seem to be on track.  I have all the latest from Xorg-edgers - including 2.6.30-9 - and disabling wobbly windows has given me no crashes for an hour.  Firefox didn't even slow down with the infamous Singapore picture.  Not sure whether this is Intel or Compiz.  Due to the nature of the bug as explained on Launchpad, it appears that wobbly windows does... um, something to cause the past-the-end-of-the-aperture freeze bug... but Intel has the bug fixed, according to them.  Hmm.
:popcorn:  I'll be waiting...

I get random crashes with compiz without wobbly windows enabled - for example, my system recently froze while running the gtkperf text scrolling benchmark. While wobbly windows may easily trigger this bug, it is still only a trigger for the real bug in the Intel driver (as you seem to have guessed already), and it doesn't appear to be the only trigger.

The crashes with UXA and large images happened on my system even when compiz was disabled, so I also don't think that compiz was more than a possible trigger. That bug seems to have been fixed on my system since a few weeks, though.

---

### Post by psyke83 on 2009-06-19
> **chronniff said:**
> I have been using the compiz Loose Binding option to get a significant boost in the compiz effects smoothness while using uxa, anyone have any idea what it does, the only research I have found is that you shouldn't use it on intel cards, but it seems to be helping with my 965 card

That doesn't affect performance on my system, how did you run compiz with loose binding?

I tried:
```
$ compiz.real --replace --loose-binding
```

Maybe compiz works differently nowadays, I haven't checked extensively.

---

### Post by Mike.lifeguard on 2009-06-19
> **DizzyTech said:**
> Mike, you seem to be on track.  I have all the latest from Xorg-edgers - including 2.6.30-9 - and disabling wobbly windows has given me no crashes for an hour.  Firefox didn't even slow down with the infamous Singapore picture.  Not sure whether this is Intel or Compiz.  Due to the nature of the bug as explained on Launchpad, it appears that wobbly windows does... um, something to cause the past-the-end-of-the-aperture freeze bug... but Intel has the bug fixed, according to them.  Hmm.
:popcorn:  I'll be waiting...

Yeah, but fixed where? I haven't been able to find a packaged update with the fix. I'll be checking the commits to the upstream repository eventually (ie once I find it).

---

### Post by Mike.lifeguard on 2009-06-19
> **bearozo said:**
> You are lucky you all that get compiz to work I still have no luck, I can start it but all I get is wallpaper and a working mouse pointer with my blacklisted Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) :( **if anyone knows about or find a fix please give a holler.**
On the other hand everything else seems fine, I get 35-40 fps in ppracer and 400-420 fps in glxgears which I suppose is quite good with that chipset on an old P4.

I don't think any fix is possible because your card is blacklisted (and they blacklist cards with good reason, apparently). You can try disabling the blacklisting code, but that's likely to result in badness of one variety or another.

---

### Post by bearozo on 2009-06-19
> **Mike.lifeguard said:**
> I don't think any fix is possible because your card is blacklisted (and they blacklist cards with good reason, apparently). You can try disabling the blacklisting code, but that's likely to result in badness of one variety or another.

Well I did disable blacklist, that is the only way to start it :) but just mouse + wallpaper and
REISUB to get out of it. I have seen some with the same chip manage to get it running but
on this wierd Gericom Hummer 755II the monitor setup seems strange, ddcprobe freezes
the machine and only a hard shutdown takes me out of it. I do think that if I can configure
Monitor properly in xorg.conf  I have a chance to get it working. After a crash I get a black screen (no graphical log in) and if I log in blindly it starts and I can use a terminal (in my case Yakuake)by hitting F12 and type sudo reboot and pwd. (blindly) and next time it start
it act normal again, it is like hal/fdi (or something) tries a one or two settings before it finds one that works with my TFT monitor. I cannot set resolution in Display settings, it is greyed
out (and I can see that monitor is ON) I get 1024 x 768 whatever I do, if I hit apply in display it sais I have no virtual screen and asks if I want xorg configured I say yes and it adds a subsection in Screen "Virtual 0 0" but still wont work.

---

### Post by nikolayo on 2009-06-19
Thank you for the post. It worked well for me on Thinkpad T500 with Intel X4500HD GMA running generic kernels 2.6.28-11, 2.6.28-13 and 2.6.30-020630. Effect on pae-enabled kernels (Ubuntu server and custom compiled) though is catastrophic. Before the fix X used to work extremely poorly with those kernels, now it does not work with them at all. 

Can you comment on how the fix relates to pae kernels and is there a way to fix those in 9.04? Or/and in 9.10?

---

### Post by psyke83 on 2009-06-19
> **nikolayo said:**
> Thank you for the post. It worked well for me on Thinkpad T500 with Intel X4500HD GMA running generic kernels 2.6.28-11, 2.6.28-13 and 2.6.30-020630. Effect on pae-enabled kernels (Ubuntu server and custom compiled) though is catastrophic. Before the fix X used to work extremely poorly with those kernels, now it does not work with them at all. 

Can you comment on how the fix relates to pae kernels and is there a way to fix those in 9.04? Or/and in 9.10?

Since PAE does some "magic" with regards to memory allocation, the MTRR setup may be different for these kernels, which I guess is causing issues for you. Unfortunately I have no 64-bit systems available to test this issue.

---

### Post by chronniff on 2009-06-19
> **psyke83 said:**
> That doesn't affect performance on my system, how did you run compiz with loose binding?

I tried:
```
$ compiz.real --replace --loose-binding
```

Maybe compiz works differently nowadays, I haven't checked extensively.

I actually cheat and use the compiz fusion icon, which lets you change various compiz options without needing to learn the command options, but that sounds about right, although I have never actually set it that way

---

### Post by nikolayo on 2009-06-20
> **psyke83 said:**
> Since PAE does some "magic" with regards to memory allocation, the MTRR setup may be different for these kernels, which I guess is causing issues for you. Unfortunately I have no 64-bit systems available to test this issue.

Thank you. I found out that pae kernels work fine and there is LOT of improvement compared to pre-fix behavior if new entries in xorg.conf are commented out. 

I also compared memory layouts reported by lspci and they are the same. What differs is reported IRQ. Any advice based on that? Here is the relevant part of lspci output:

```

Generic kernel:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0, IRQ 2296
        Memory at f4400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0
        Memory at f4200000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>


Pae kernel:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at f4400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 20e4
        Flags: bus master, fast devsel, latency 0
        Memory at f4200000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>


```

---

### Post by jonathanmotes on 2009-06-20
I recently tried the safe sections on my laptop with Intel X3100 graphics (running Jaunty), and it worked VERY well - even better than with Intrepid.

However, I decided to try the "safe" configuration on my brother's HP Mini 110 Mi netbook (running Ubuntu UNR 9.04) with **Intel GMA 950** graphics and it made performance much WORSE.

So, my question is, has anyone successfully fixed their graphics problems on Jaunty with GMA 950 hardware? 

I think I saw somewhere that the bleeding edge configuration solves the problem but I'm afraid that will introduce other issues.

Thanks!

---

### Post by Ubuntu Terrier on 2009-06-20
Hello, 

I followed the guide to set up the optimal video configuration, but when (and only when) UXA acceleration is enabled, after I close Google Earth, X crashes and I get kicked back to the login screen. Also some graphic effects with Compiz (standard light settings) like menu transprency looks a bit weird with UXA enabled.

If I comment out the line which sets up UXA configuration in xorg.conf, all works almost perfectly (except for serious issues in 3d programs like Blender and Google Earth), and X doesn't crash.

My video card is a G45 Intel GMA X4500HD.

---

### Post by PatrickVogeli on 2009-06-20
I've had some troubles with Uxa and optimal configuration, so I just moved to the Bleeding-edge, which works absolutelly well.

You could try switching to bleeding edge and, if everything works like you expect, comment the bleeding edge repos lines in /etc/apt/sources.list, so nothing could break in a future upgrade.

---

### Post by JohnnyRogers on 2009-06-21
This guide is awesome!

I have an x3100, and using the "Optimal" setup solved the last compiz errors I had, and it seems to be running better than even before I enabled compiz.

I do have one problem though - I can't use Remastersys to make a live CD backup anymore. Does anyone know a workaround for this?

---

### Post by treesurf on 2009-06-21
When doing the most recent stock kernel updates I noticed that it mentioned something about intel i8xx chipsets.  Was this related to the video problems?  My chipset is actually a 945GM, but I was hoping that this might help some other users.

---

### Post by lbharti on 2009-06-21
I can see improvement in FPS, but how do I fix Google earth, or any thing using video acceleration from displaying on top of everything, I mean I am not able to place a window on top of the displayed video, or earth. It is very annoying. I am using Thinkpad X61 with optimum. xorg.conf follows:

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "true"
EndSection

My system configuration:
Ubuntu Hardy Heron 8.04
Compiz enabled, Metacity engine in use.

Thinkpad X61 with Intel 3100.

Thanks
Loke

---

### Post by draggy on 2009-06-22
> **jonathanmotes said:**
> 
However, I decided to try the "safe" configuration on my brother's HP Mini 110 Mi netbook (running Ubuntu UNR 9.04) with **Intel GMA 950** graphics and it made performance much WORSE.

So, my question is, has anyone successfully fixed their graphics problems on Jaunty with GMA 950 hardware?

I have the same problem on a netbook with a 945GM chip. enabling uxa makes it unbearably worse. I was hoping that with today's new kernel and xorg updates that it would be fixed, but it seems it still is broken. I have tried many things including a patched 28-11 kernel, but it just refuses to work correctly with this chipset. It seems netbook users are doomed...

---

### Post by Mike.lifeguard on 2009-06-22
Looks like 'real' fixes are in:
*Bug 359392 is fixed with patches to compiz (1:0.8.2-0ubuntu8.1) and xserver-xorg-video-intel (2:2.6.3-0ubuntu9.3) in jaunty-proposed.

MTRR bug is in progress - please see bug 314928 and help test the proposed fix.

---

### Post by Ubuntu Terrier on 2009-06-22
> **Mike.lifeguard said:**
> Looks like 'real' fixes are in:
*Bug 359392 is fixed with patches to compiz (1:0.8.2-0ubuntu8.1) and xserver-xorg-video-intel (2:2.6.3-0ubuntu9.3) in jaunty-proposed.

MTRR bug is in progress - please see bug 314928 and help test the proposed fix.

Since I have the 'unofficial' fixes and xorg drivers installed, I'm wondering, being a newbie, what will happen when official fixes (or also Karmic, in 4-5 months) will come out. Will I need to manually uninstall them?

---

### Post by chronniff on 2009-06-22
> **Ubuntu Terrier  said:**
> Since I have the 'unofficial' fixes and xorg drivers installed, I'm wondering, being a newbie, what will happen when official fixes (or also Karmic, in 4-5 months) will come out. Will I need to manually uninstall them?

Refer to the "To Revert Settigns" section at the end of the how-to, it explains how to revert back to the "current" packages that are in the standard repos

---

### Post by Orographic on 2009-06-22
> **chronniff said:**
> Refer to the "To Revert Settigns" section at the end of the how-to, it explains how to revert back to the "current" packages that are in the standard repos

I created a Clonezilla image of my Jaunty setup just before I performed the Safe configuration fix here, so I may just restore that image then apply any official fixes.

Re netbook intel problems, I have an Eee 701 with Eeebuntu Base 3.0 and haven't applied the new netbook kernel update yet but apparently it fixes the intel graphics issue.

---

### Post by Orographic on 2009-06-23
I've just restored a Clonezilla image of Jaunty prior to my Safe Configuration changes for my Intel 945GZM system and then performed all of the latest updates. Can confirm that full screen video is still awful via sites like iView. I will image this current setup and restore it to use if more helpful fixes come in the future.

---

### Post by SteveMcQwark on 2009-06-23
> **jonathanmotes said:**
> I recently tried the safe sections on my laptop with Intel X3100 graphics (running Jaunty), and it worked VERY well - even better than with Intrepid.

However, I decided to try the "safe" configuration on my brother's HP Mini 110 Mi netbook (running Ubuntu UNR 9.04) with **Intel GMA 950** graphics and it made performance much WORSE.

So, my question is, has anyone successfully fixed their graphics problems on Jaunty with GMA 950 hardware? 

I think I saw somewhere that the bleeding edge configuration solves the problem but I'm afraid that will introduce other issues.

Thanks!

I got it to work with Bleeding Edge. However, when I close my laptop lid, my computer freezes with a black screen. (might be a KDE 4.3 beta 2 bug) But the seamless video makes it worthwhile for me.

---

### Post by jonathanmotes on 2009-06-23
> **SteveMcQwark said:**
> I got it to work with Bleeding Edge. However, when I close my laptop lid, my computer freezes with a black screen. (might be a KDE 4.3 beta 2 bug) But the seamless video makes it worthwhile for me.

Are you using the Intel 950 graphics card? Thanks!

---

### Post by SteveMcQwark on 2009-06-23
> **jonathanmotes said:**
> Are you using the Intel 950 graphics card? Thanks!

Yeah, thats what I meant.

---

### Post by jbernardo on 2009-06-23
> **SteveMcQwark said:**
> I got it to work with Bleeding Edge. However, when I close my laptop lid, my computer freezes with a black screen. (might be a KDE 4.3 beta 2 bug) But the seamless video makes it worthwhile for me.

 That bug has appeared with the two days ago version of bleeding edge xserver-xorg-intel-driver/mesa libs. Yesterday (14-16h ago) a new version was available that seems to have fixed that, at least on my AAO 110.  Anyway, for the last three releases screen mode switching/stretching works again, blobwars now occupies full screen and not just a square in the middle. And the speed of yesterday's release is bearable again - 17-18 fps in glblur.

---

### Post by thom_raindog on 2009-06-23
First off: Thanks a big big bundle for all the work.
But, how is it that things get worse for me when I use the Safe Mode? The racer drops from close to 20fps to just around 10, if I keep ```
Option "Tiling" "true"
``` fps go down to under 10.
I have an Intel 945GM as grafics card.

---

### Post by zevans on 2009-06-23
> **Orographic said:**
> I've just restored a Clonezilla image of Jaunty prior to my Safe Configuration changes for my Intel 945GZM system and then performed all of the latest updates. Can confirm that full screen video is still awful via sites like iView. I will image this current setup and restore it to use if more helpful fixes come in the future.

Hang on. It's in Safe config but with all updates applied? Do you mean all updates from jaunty-updates only, or do you have xorg-edgers stuff on there, in which case it's no longer in Safe config. Sounds like you might have a half-Safe half-Optimal half-Bleeding Edge config, which is just never gonna work. :-)

---

### Post by treesurf on 2009-06-23
The latest compiz updates specifically mention the GM965.  Has anyone with this chipset installed the latest updates on a stock system, and if so, what were the results?

I'm wondering if I should revert to stock setup and give this a shot, as I have the GM965.

---

### Post by zevans on 2009-06-23
> **treesurf said:**
> The latest compiz updates specifically mention the GM965.  Has anyone with this chipset installed the latest updates on a stock system, and if so, what were the results?

I'm wondering if I should revert to stock setup and give this a shot, as I have the GM965.

Yes, do. I've just been catching up on some bugs and the HUGE "freezes on i965" bug discussion is coming to an end and the releases in -updates seem to fix it. So on a 965 if you go back to stock, and pull in OFFICIAL jaunty-updates, you should be stable and compiz ought to work if you un-blacklist.

If you try this and it doesn't work, then the guys on bug 359392 will want to know! I would cut-and-paste the relevant parts here but launchpad isn't playing right now, probably due to the size of this bug's discussion.

---

### Post by zevans on 2009-06-23
@psyke83, @thom_raindog: Tiling is broken in a few ways in .28. All fixed in .30 but the changes are horribly complex and the team aren't willing to backport (I must say I agree in this case), so all we can do is say you need 2.6.30 for stability AND performance, and if you want stability and support, stay on the Jaunty-updates kernel and disable tiling.

@thom_raindog: If you want stability, performance, and official support... you can't, because the Intel code is changing too quickly. I've read about some other distros running into this problem too.

If you want the rocket science around it, use your favourite search engine to look into "A17 tiling intel" but my head exploded after 10 minutes of that.

---

### Post by treesurf on 2009-06-23
Thanks zevans.  I've all I've done so far was to install the compiz updates and then reboot into the stock kernel.  Already there seems to be significant improvement, at least with compiz.  Wobbly windows wobble smoothly again and overall things seem a little less laggy.  This is good because I prefer the stock kernel, it handles resume from suspend much better then the .30 kernel.

Do you I suggest I revert all of the other settings from the original howto as well, or just leave well enough alone?


EDIT: random processor activity seems to have dropped as well.

---

### Post by mister_playboy on 2009-06-23
> **treesurf said:**
> The latest compiz updates specifically mention the GM965.  Has anyone with this chipset installed the latest updates on a stock system, and if so, what were the results?

I'm wondering if I should revert to stock setup and give this a shot, as I have the GM965.

I have been running 9.04 with a stock setup since release, and I have a 965 chipset.  Just downloaded the updates, and I was able to turn on compiz!  Everything is working so far!  :D:D:D

I'm so glad this issue has been fixed.

---

### Post by treesurf on 2009-06-23
That's good to hear!

I have essentially downgraded from the Optimal fix to the Safe fix, and since everything seems to be going smoothly I will just leave it at that for now.

---

### Post by Rizado on 2009-06-24
It just gets more odd :) I'm using the bleeding edge drivers and a 2.6.30 kernel. A few days ago a driver upgrade increased my glxgears fps to about 2300 with composting on. But only 1500 with it turned off! I've never seen something like this before. FPS with composting turned on is always lower, I do however notice some stuttering in glxgears with composting turned on which makes me believe it might be a bug or bad setting making glxgears skip some frames. Has anyone noticed the same or is able to replicate it?

I'm on a Intel GM45 chipset btw. (Intel 4500MHD graphics that is)

EDIT: Hah! I added ```
Option          "EXAOptimizeMigration"          "true"
Option          "MigrationHeuristic"            "greedy"

```to xorg.conf and that took away the odd behavior. glxgears is still stuttering with composting turned on however.

---

### Post by psyke83 on 2009-06-24
> **Rizado said:**
> It just gets more odd :) I'm using the bleeding edge drivers and a 2.6.30 kernel. A few days ago a driver upgrade increased my glxgears fps to about 2300 with composting on. But only 1500 with it turned off! I've never seen something like this before. FPS with composting turned on is always lower, I do however notice some stuttering in glxgears with composting turned on which makes me believe it might be a bug or bad setting making glxgears skip some frames. Has anyone noticed the same or is able to replicate it?

I'm on a Intel GM45 chipset btw. (Intel 4500MHD graphics that is)

EDIT: Hah! I added ```
Option          "EXAOptimizeMigration"          "true"
Option          "MigrationHeuristic"            "greedy"

```to xorg.conf and that took away the odd behavior. glxgears is still stuttering with composting turned on however.

Really? With the xorg-edgers drivers those options do absolutely nothing (except a placebo effect, perhaps :P).

Those options are used to tweak EXA; they won't do anything as the latest Intel driver no longer supports EXA acceleration at all.

---

### Post by psyke83 on 2009-06-24
xorg-edgers users:

In the next update of Sarvatt's packages (whenever that happens), the intel driver will have a new option (SwapBuffersWait) that may interest you folks.

See the upcoming option's information here: [http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=1eec83a203c48822400742a1fb184b2cb52c62f7](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=1eec83a203c48822400742a1fb184b2cb52c62f7)

---

### Post by AaronD12 on 2009-06-24
I am AMAZED at the increased graphics performance on my Dell Mini 9. The Skyrocket screen saver was barely a slideshow before, now it's running nicely. The best improvement I've seen, though, is in scrolling in Firefox. It lagged so badly it was frustrating. Now it keeps up with no problem! [U]THANKS [U]PSYKE83!!!!  :D
[/U][/U]

---

### Post by PiCkAjEw on 2009-06-25
> **psyke83 said:**
> xorg-edgers users:

In the next update of Sarvatt's packages (whenever that happens), the intel driver will have a new option (SwapBuffersWait) that may interest you folks.

See the upcoming option's information here: [http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=1eec83a203c48822400742a1fb184b2cb52c62f7](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=1eec83a203c48822400742a1fb184b2cb52c62f7)

Glanced the code from your url. Isn't the new option enable by default anyways?

---

### Post by Orographic on 2009-06-25
> **zevans said:**
> Hang on. It's in Safe config but with all updates applied? Do you mean all updates from jaunty-updates only, or do you have xorg-edgers stuff on there, in which case it's no longer in Safe config. Sounds like you might have a half-Safe half-Optimal half-Bleeding Edge config, which is just never gonna work. :-)

I did an image restore via Clonezilla and this image of Ubuntu didn't have the Safe Configuration set up, it was just a stock Jaunty install. I then performed all of the Jaunty updates since I made this image, which was about four weeks worth. So, its a stock install of Jaunty with all of the latest updates and iView and YouTube were still jerky and fragmented at full screen on my 945GZM-S2 motherboard.

I then restored my Clonezilla image that has the Safe Configuration via this guide and its all working great again in iView and YouTube.

I'm no expert but this is how I test things out. So at this stage, Jaunty updates (Important Security and Recommended updates only) are not helping my intel board, so I will stick to the Safe Config for now.

Hope this helps someone with my setup or similar.

---

### Post by hamidoo on 2009-06-25
Hey guys, does anyone got a black screen at login after the latest xorg-edgers update?
everything was super smooth with my intel 915 vga from the xorg-edgers repository, but after the updated "xserver-xorg-video-intel - 2:2.7.99.901+git20090**622**" i got a black screen at login.

so i downgraded to "xserver-xorg-video-intel - 2:2.7.99.901+git20090**619**" (i also have to downgrade some other packages) and everything is ok again.

---

### Post by bearozo on 2009-06-25
I get this all the time after any change in xorg or update or trying to run compiz etc.
I get black screen but I hear plonk so I can log in blindly and when start a terminal (still blindly) type sudo reboot + enter + pass after a few reboots it starts working normally again, it seems like hal/fdi whatever tries a few settings before one comes up which work ?
I always get black screen if I log out so I always have to reboot or shut down.
Have: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

> **hamidoo said:**
> Hey guys, does anyone got a black screen at login after the latest xorg-edgers update?
everything was super smooth with my intel 915 vga from the xorg-edgers repository, but after the updated "xserver-xorg-video-intel - 2:2.7.99.901+git20090**622**" i got a black screen at login.

so i downgraded to "xserver-xorg-video-intel - 2:2.7.99.901+git20090**619**" (i also have to downgrade some other packages) and everything is ok again.

---

### Post by wate on 2009-06-25
I'm getting 30-40% better graphic perfomance with driver from 2.6.30-020630rc2-generic kernel on X3100 graphic card. But some of the functionalities (brightness adjust, Fn shortcuts, boot image splash, ...) doesn't work.
Any suggestions how to use a driver from rc2 kernel with latest or stock kernel?

---

### Post by psyke83 on 2009-06-25
> **wate said:**
> I'm getting 30-40% better graphic perfomance with driver from 2.6.30-020630rc2-generic kernel on X3100 graphic card. But some of the functionalities (brightness adjust, Fn shortcuts, boot image splash, ...) doesn't work.
Any suggestions how to use a driver from rc2 kernel with latest or stock kernel?

There are no "drivers" in the kernel except the DRM kernel modules (to handle memory management, etc). They're built from the kernel sources and can't be mixed and matched with different versions of the kernel.

---

### Post by psyke83 on 2009-06-25
> **PiCkAjEw said:**
> Glanced the code from your url. Isn't the new option enable by default anyways?

Yes, but if you read the description you'll see that you may want to disable this option.

---

### Post by wate on 2009-06-25
> **psyke83 said:**
> There are no "drivers" in the kernel except the DRM kernel modules (to handle memory management, etc). They're built from the kernel sources and can't be mixed and matched with different versions of the kernel.

Thank you for the reply. 
Then, the only way to achieve the performance from rc2 kernel is to use the rc2 kernel?

---

### Post by psyke83 on 2009-06-25
> **wate said:**
> Thank you for the reply. 
Then, the only way to achieve the performance from rc2 kernel is to use the rc2 kernel?

Nobody should be using the rc2 kernel anymore. What configurations have you tried?

Many improvements have been made to the drivers lately - the Bleeding-Edge configuration (with the final 2.6.30 kernel) works best on my system, have you tried it yet? Also see the SwapWaitBuffers option that I mentioned in my recent post.

---

### Post by wate on 2009-06-25
> **psyke83 said:**
> Nobody should be using the rc2 kernel anymore. What configurations have you tried?

Many improvements have been made to the drivers lately - the Bleeding-Edge configuration (with the final 2.6.30 kernel) works best on my system, have you tried it yet? Also see the SwapWaitBuffers option that I mentioned in my recent post.

I've tried Optimal and Bleeding edge configuration, but performance drops by ~ 50%. I reverted the settings and using the final kernel now.
Why isn't performace from final 2.6.30 kernel the same as in rc2? 

Thanks for the guide and help.

---

### Post by psyke83 on 2009-06-25
> **wate said:**
> I've tried Optimal and Bleeding edge configuration, but performance drops by ~ 50%. I reverted the settings and using the final kernel now.
Why isn't performace from final 2.6.30 kernel the same as in rc2? 

Thanks for the guide and help.

I guess there's a regression affecting your chipset; you may want to file a detailed bug report upstream (see Important Note from the guide for details).

What you can do is revert to the Safe configuration, but use EXA acceleration instead of UXA.

---

### Post by loudog23 on 2009-06-25
hey, i was going though your thread -> [http://ubuntuforums.org/showthread.php?t=1130582&highlight=ati+update](http://ubuntuforums.org/showthread.php?t=1130582&highlight=ati+update) and noticed something...

In part A you wrote:
>  4. If you want the Safe/Optimal configuration, continue to Part B. For Bleeding-Edge, skip to Part D. 

But at beginning of part c, you state that you need to follow part C for bleeding-edge configuration:
> Part C (Optimal/Bleeding-Edge)
Users who desire the Optimal or Bleeding-Edge configurations should follow this section. 

ty for this thread... 
lou

---

### Post by wate on 2009-06-25
> **psyke83 said:**
> I guess there's a regression affecting your chipset; you may want to file a detailed bug report upstream (see Important Note from the guide for details).

What you can do is revert to the Safe configuration, but use EXA acceleration instead of UXA.

:) 
Great, now the performace is almost the same as in rc2. 
I'll report this bug.

Thanks a lot to you and the team working on the drivers.
cheers

---

### Post by psyke83 on 2009-06-25
> **loudog23 said:**
> hey, i was going though your thread -> [http://ubuntuforums.org/showthread.php?t=1130582&highlight=ati+update](http://ubuntuforums.org/showthread.php?t=1130582&highlight=ati+update) and noticed something...

In part A you wrote:


But at beginning of part c, you state that you need to follow part C for bleeding-edge configuration:


ty for this thread... 
lou

Thanks, I fixed the error in the guide.

---

### Post by Rizado on 2009-06-26
> **psyke83 said:**
> Really? With the xorg-edgers drivers those options do absolutely nothing (except a placebo effect, perhaps :P).

Those options are used to tweak EXA; they won't do anything as the latest Intel driver no longer supports EXA acceleration at all.Are you sure? I know uxa is default but I thought MigrationHeuristic defaulted to all. If it doesn't there's either something wrong with some other settings or there's a bug. Because I tried this several times.
I do have: ```
Option          "UseFBDev"              "true"
``` too.

---

### Post by Roby64 on 2009-06-26
Thanks

---

### Post by zevans on 2009-06-26
> **Orographic said:**
> I did an image restore via Clonezilla and this image of Ubuntu didn't have the Safe Configuration set up, it was just a stock Jaunty install. I then performed all of the Jaunty updates since I made this image, which was about four weeks worth. So, its a stock install of Jaunty with all of the latest updates and iView and YouTube were still jerky and fragmented at full screen on my 945GZM-S2 motherboard.

Right, this is interesting then... because I thought the tearing/jerkiness issues were fixed in jaunty-updates for EXA. Clearly not! I'm sure the bugs are marked fix-released though...

---

### Post by psyke83 on 2009-06-26
> **zevans said:**
> Right, this is interesting then... because I thought the tearing/jerkiness issues were fixed in jaunty-updates for EXA. Clearly not! I'm sure the bugs are marked fix-released though...

AFAIK there is no way to stop tearing in Flash video; not even the binary NVIDIA driver with vsync forced can solve tearing in Flash video, and it's the same in Windows. Flash doesn't use XV, and doesn't seem to use opengl on my systems (though opengl acceleration can be forced via configuration, it's unstable).

...or is it a different tearing issue you're referring to?

---

### Post by zevans on 2009-06-26
> **hamidoo said:**
> Hey guys, does anyone got a black screen at login after the latest xorg-edgers update?
everything was super smooth with my intel 915 vga from the xorg-edgers repository, but after the updated "xserver-xorg-video-intel - 2:2.7.99.901+git20090**622**" i got a black screen at login.

so i downgraded to "xserver-xorg-video-intel - 2:2.7.99.901+git20090**619**" (i also have to downgrade some other packages) and everything is ok again.

Both versions were OK for me (945GME) except that for quite a few releases now, I have a black screen on logout. It's not locked up though, I can shut down cleanly with the power button.

Are you rebooting between driver upgrades? Because the driver interacts with the kernel so heavily I don't think HAL can work out what's going on without a reboot - that might be the problem?

---

### Post by zevans on 2009-06-26
> **psyke83 said:**
>  Flash doesn't use XV, and doesn't seem to use opengl on my systems (though opengl acceleration can be forced via configuration, it's unstable).

I read somewhere on Slashdot that Flash will attempt to use hardware acceleration when playing full-screen but not when in a window. Which might explain why I had stabilty problems with Flash full screen under Windows XP. :-)

---

### Post by psyke83 on 2009-06-26
> **zevans said:**
> I read somewhere on Slashdot that Flash will attempt to use hardware acceleration when playing full-screen but not when in a window. Which might explain why I had stabilty problems with Flash full screen under Windows XP. :-)

Possibly, but I don't think that Flash uses OpenGL on Windows, it uses DirectX/Direct3D.

---

### Post by abhilash82 on 2009-06-27
Using this link worked for me [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Cimi86 on 2009-06-29
My guide for netbooks (intel gma 950):
[http://www.cimitan.com/blog/2009/06/28/get-a-dramatic-2d-graphics-boost-on-your-netbook/](http://www.cimitan.com/blog/2009/06/28/get-a-dramatic-2d-graphics-boost-on-your-netbook/)

Feel free to link it in the first post, I got a dramatic boost in 2d graphics compared to the default jaunty.

---

### Post by Orographic on 2009-07-01
> **psyke83 said:**
> AFAIK there is no way to stop tearing in Flash video; not even the binary NVIDIA driver with vsync forced can solve tearing in Flash video, and it's the same in Windows. Flash doesn't use XV, and doesn't seem to use opengl on my systems (though opengl acceleration can be forced via configuration, it's unstable).

...or is it a different tearing issue you're referring to?

I had a play without the Safe Config fix again today as I had to re-install my OS from scratch thanks to my website being hacked - in the end it had nothing to do with Ubuntu.

Iview and YouTube seem a bit better but still below par. From my experience Windows XP is good on iView and Youtube with flash, a bit better than Jaunty with the Safe Config fix which I am running again now.

---

### Post by tori_yang613 on 2009-07-01
Thanks. My graphics probelm is solved with this thread. (I'm using intel xps m1210 laptop) However, I was once surprised by an unexpected error message after the setup.

I tried the Optimized approach. When I rebooted, I got an error message before getting to the login menu.

```
Ubuntu us running in low-graphics mode

The following error was encountered. You may need 
to update your configuration to solve this.

(EE) intel(0): Cannot support DRI with frame buffer width 
> 2048
```After clicking OK, I was given choices to fix this problem. I chose to restore my graphic configuration to default setting. Then the display came back to the normal resolution. This problem has not re-occured after that, and my graphics performance has improved significantly. Still, I wonder why this happened.

---

### Post by fynn_ on 2009-07-02
Hi,
thx to you my performance increased.
The only problem that I have now, is that apt-get still wants to update the 2.6.28 kernel, which is not installed anymore; what can i do to stop this?

---

### Post by tomchiverton on 2009-07-02
It should be fine - double check grub's menu.lst but you should be fine with both a .30 'manual' kernal and the .28 apt provides. I am :-)

---

### Post by psyke83 on 2009-07-02
> **fynn_ said:**
> Hi,
thx to you my performance increased.
The only problem that I have now, is that apt-get still wants to update the 2.6.28 kernel, which is not installed anymore; what can i do to stop this?

The 2.6.28 kernel is still installed, should stay installed, and you should keep it updated to guarantee stability and security (if you need to revert back to it). Don't ignore the warnings in this guide about the 2.6.30 kernel being unsupported, either.

If you're not dual-booting with Windows, then GRUB automatically hides the boot menu when your computer boots. Press the ESC key when GRUB starts and you will see the boot menu, and you can choose the older kernel from there.

---

### Post by siabost on 2009-07-02
Hi,

This is a little odd: on typing > $ gksudo gedit /etc/X11/xorg.conf in a terminal it brings up a blank xorg.conf file.

I have never opened nor tampered with it since I installed 9.04!

I have an integrated Intel 82865G Graphics chip. When I try to run any kind of effects it searches for a driver, finds none & says that no desktop effects can be enabled.

Any ideas, anyone?

Thanks

---

### Post by psyke83 on 2009-07-02
> **siabost said:**
> Hi,

This is a little odd: on typing  in a terminal it brings up a blank xorg.conf file.

I have never opened nor tampered with it since I installed 9.04!

I have an integrated Intel 82865G Graphics chip. When I try to run any kind of effects it searches for a driver, finds none & says that no desktop effects can be enabled.

Any ideas, anyone?

Thanks

That's probably nothing to worry about; Xorg no longer needs a configuration file to operate, so it may have never been generated on your system.

You can generate a "bare" configuration file like so:
```
$ sudo dpkg-reconfigure xorg-xserver -phigh
```

Your problem with compiz may be due to a blacklisted driver. You can temporarily override the blacklist via:
```
$ SKIP_CHECKS=yes compiz
```

---

### Post by bullbutch on 2009-07-03
I tried the how-to on this page and I went from 5-10 fps in planet penguin to 25-30 fps. Glxgears showed me 250 fps before and 600 fps after.

I used the bleeding edge configuration on my Intel 945GM computer.

It worked better than before, but I wasn't satisfied. 

I went on to downloaded the latest kernel for Ubuntu Karmic Koala, and installed it, rebooted, and viola, I got 50-60fps i planet penguin and 1200fps with glxgears. 

Firefox and flash also work a lot better than with the bleeding edge configuration from this page. And everything else is working flawless with the new kernel.

To sum it all up, all I did was use all the steps from this guide, and then I installed the latest karmic koala kernel. 

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_amd64.deb)

I hope it can help someone!

Thanks for this guide.

---

### Post by almess301 on 2009-07-03
I am using a dell inspiron mini 10 with the dreaded Intel GMA 500, I managed to get the 2d drivers working at an acceptable level on Ubuntu 9.04, but I am wondering if support for the GMA 500 will work out of the box in October on Karmic.  I understand there might not be a definite answer, but if there is please post.

---

### Post by commonplace on 2009-07-03
> **bullbutch said:**
> I tried the how-to on this page and I went from 5-10 fps in planet penguin to 25-30 fps. Glxgears showed me 250 fps before and 600 fps after.

I used the bleeding edge configuration on my Intel 945GM computer.

It worked better than before, but I wasn't satisfied. 

I went on to downloaded the latest kernel for Ubuntu Karmic Koala, and installed it, rebooted, and viola, I got 50-60fps i planet penguin and 1200fps with glxgears. 

Firefox and flash also work a lot better than with the bleeding edge configuration from this page. And everything else is working flawless with the new kernel.

To sum it all up, all I did was use all the steps from this guide, and then I installed the latest karmic koala kernel. 

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-1-generic_2.6.31-1.14_amd64.deb)

I hope it can help someone!

Thanks for this guide.

When you say you followed the steps from the guide, did you do the Safe, Optimal, or Bleeding Edge process? I know you did one of those and then the Karmic kernel, but did you do Safe or Optimal or Bleeding Edge? Thanks!!

/Kevin

---

### Post by jsr77 on 2009-07-03
hi,
thanks for the guide :)

after this operation my desktop / screen is flipped upside down every time i boot ubuntu?? how can i change this?

i am on an asus eee 900, running ubuntu 9.04

best,
jacob

---

### Post by SudaDreamS on 2009-07-03
Thanks alot

I am wondering, will we have howto for ATI cards soon?

---

### Post by bullbutch on 2009-07-03
> **commonplace said:**
> When you say you followed the steps from the guide, did you do the Safe, Optimal, or Bleeding Edge process? I know you did one of those and then the Karmic kernel, but did you do Safe or Optimal or Bleeding Edge? Thanks!!

/Kevin


I tried all of them, but in the end I did the bleeding edge steps, and added the karmic kernel to that.

---

### Post by charcer on 2009-07-04
I also recommend the karmic .31-1.14 kernel, got a huge increase in fps today with the latest xorg-edgers. 
Usually I get average 3.2-3.8 fps in Nexuiz timedemo1 even with karmic .30, but today the fps jumped to 4.8

---

### Post by c.monty on 2009-07-05
hi!
i would like to follow the guide in order to
- improve performance,
- make monitor mode 800 x 480 VGA available for Navilock 8" 16:9.

however, my xorg.conf is empty after fresh installation of ubuntu 9.04.

am i supposed to fill the xorg.conf with content?
how do i proceed?

THX

---

### Post by psyke83 on 2009-07-05
> **c.monty said:**
> hi!
i would like to follow the guide in order to
- improve performance,
- make monitor mode 800 x 480 VGA available for Navilock 8" 16:9.

however, my xorg.conf is empty after fresh installation of ubuntu 9.04.

am i supposed to fill the xorg.conf with content?
how do i proceed?

THX

To generate a minimal xorg.conf:
```
$ sudo dpkg-reconfigure xorg-xserver -phigh
```

This guide will do nothing to help with your resolution issue. If a newer driver provides this feature, then it will work, but there's no guarantee.

---

### Post by jerrylamos on 2009-07-05
> **charcer said:**
> I also recommend the karmic .31-1.14 kernel, got a huge increase in fps today with the latest xorg-edgers. 
Usually I get average 3.2-3.8 fps in Nexuiz timedemo1 even with karmic .30, but today the fps jumped to 4.8

i830 on IBM Thinkpad R31 video performance as measured by GtkPerf from Ubuntu Synaptic:

Karmic 2.6.31-1 83% slower than Intrepid.

Yes KMS is running.  I'm not sure what good that does if it is that much slower.

Jerry

---

### Post by psyke83 on 2009-07-06
> **jerrylamos said:**
> i830 on IBM Thinkpad R31 video performance as measured by GtkPerf from Ubuntu Synaptic:

Karmic 2.6.31-1 83% slower than Intrepid.

Yes KMS is running.  I'm not sure what good that does if it is that much slower.

Jerry

KMS does appear to impact performance (even though it shouldn't). Try to disable KMS and see if your score improves.

Kernel 2.6.31-1-generic has caused a 3D regression for my 855GM (very noticeable jerking in games), but 2D is unaffected (fast).

---

### Post by beefcurry on 2009-07-08
Now this has got me quite confused, I started with the first command running on a standard up to date Jaunty UNR with backports installed. Running

```
sudo dpkg-reconfigure -phigh xorg-xserver
```

returns me

```
/usr/sbin/dpkg-reconfigure: xorg-xserver not installed
```

I did this using xterm, and have no reason to believe why I don't have xorg-xserver.

A quite sudo apt-get install xorg-xserver just returns with couldn't find package xorg-server.

Any insight on what this might be due to? using a Acer Aspire One

---

### Post by psyke83 on 2009-07-08
> **beefcurry said:**
> Now this has got me quite confused, I started with the first command running on a standard up to date Jaunty UNR with backports installed. Running

```
sudo dpkg-reconfigure -phigh xorg-server
```

returns me

```
/usr/sbin/dpkg-reconfigure: xorg-server not installed
```

I did this using xterm, and have no reason to believe why I don't have xorg-server.

A quite sudo apt-get install xorg-server just returns with couldn't find package xorg-server.

Any insight on what this might be due to? using a Acer Aspire One

It should be xorg-xserver, not xorg-server. That command is only necessary if you don't have an xorg.conf file present; make sure to read the guide carefully.

---

### Post by beefcurry on 2009-07-08
> **psyke83 said:**
> It should be xorg-xserver, not xorg-server. That command is only necessary if you don't have an xorg.conf file present; make sure to read the guide carefully.

Yes sorry, I had in fact used xorg-xserver in xterm but had a typo here in the forums. With my repositories set to the Ubuntu Main (and tested on Ubuntu UK as well) xorg-xserver was not around, however there was a xserver-xorg. So the logical next step became "sudo dpkg-reconfigure -phigh xserver-xorg" which worked like a charm.

However adding the UXA option decreased my speed by about 40-50fps everytime for some unknown reason (intel 945GM) and when quoting it out caused it to go back to what it was originally at 145fps while using glxgears. Even with the updated xserver-xorg packages and the newer kernel nothing seemed to change. glxgears is still in its low 145 fps. I know glxgears is not exactly a very good measurement of 3D performance, but it roughly gives me a idea. I havn't tried gtkperf and flash yet. 

I really can not come up with an explanation for the speed.

While running mtrr.sh I get the following results, which seem a bit off to me, any thoughts?

```
Extracing base address and memory size from lspci -v
20000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
reg00: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg01: base=0x0fffc0000 ( 4095MB), size=  128KB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size=  256MB, count=1: write-back
reg03: base=0x010000000 (  256MB), size=  256MB, count=1: write-back
reg04: base=0x01f800000 (  504MB), size=    8MB, count=1: uncachable
reg05: base=0x01f600000 (  502MB), size=    2MB, count=1: uncachable
reg06: base=0x01f500000 (  501MB), size=    1MB, count=1: uncachable
reg07: base=0x000000000 (    0MB), size=  128KB, count=1: uncachable

```

I did also add mtrr clean and the rest to my grub as suggested @ [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552)

I would assume if all else fails, I would be back on Intepid. And for one final question, why does the how to use xorg-xserver while I can only use xserver-xorg. I doubt the original howto was mistaken as there has been over 90 pages and after reading a good 40 of them no one has mentioned this.

---

### Post by Maupertus on 2009-07-08
> **psyke83 said:**
> I have no pity for you if you don't read the guide properly... I specifically warn in the disclaimer that using a third-party kernel will mean that restricted drivers no longer function. You should revert the changes (or simply choose the official Jaunty kernel in GRUB - press ESC to access the menu if necessary).

Bit late to respond but @Psyke83
It was by no means meant as offensive or a putdown, just that the kernels up till then did wonders for the WiFi drivers and then rc7 was radically different. Didn't mean to offend and I was fully aware of the consequences of modding in the kernel. Cheers!

---

### Post by AoSteve on 2009-07-09
I'm just a n00bie here.  Never did any kernel updates or anything and I was nervous about going to the new kernel with my laptop.   But for those who are reading and are worried, don't be.   I'll explain why I finally did this.

First, Compiz was horrible at times..  with Audacious playing along with anything else, even wobbly windows was LAME on the 945GM in this laptop.  Yeah, I expect that from an 8mb shared intel gpu tho..

I only got 150 frames per five seconds with glxgears which was HORRID.   I didn't mind much, it's a two year old el-cheapo portable that works for what I need it for, a mobile web browser and music player that permits me to do "on the road" schooling.

Well, tonight I played a movie on my TV through the RGB out and it scorched my xorg.conf somehow and I was literally stuck at 1024x768 on my 1280x800 screen....   I was more/less mad.   I worked on that Xorg for a while and now Ubuntu is stuck.   So I followed the instructions on the first post to the safe/optimal settings up to installing the .30 kernel...       

I went ahead and checked glxgears and noticed I was getting TWICE the frame rate!!  Just with the quick fix!   The script and the Xorg update..  "Fine, I'll try it..  I guess it's got an undo here.. what the heck."    It literally took me five minutes to restart.   It took a few seconds longer to start, and I was already thinking..  "I BROKED MY LAPTOP OH NOES".    Then it all the sudden popped up with gnome and there it was.   So..   I tried glx gears..    I'm getting 4x the framerate I originally was and now compiz is smooth as my desktop!!!!    I'm happy as could be!   Also, my overpowering loud sound effects have nulled down to more ...  acceptable volumes.  Specially for my headphones.  First set blew out on the second I plugged them in because of the output!!!    Now it's perfect.   Switching to this kernel and changing the setup around was the best thing I've done yet!   To cap it all off, Compiz works smoooooothly even with a Vbox with XP home installed and running!!!     Thank you to the original poster and anyone who has helped with the process!  I love my new found smooth graphics laptop!!!

---

### Post by Citizen_Kane01 on 2009-07-09
A million thankyou's!

I am a dedicated Linux user, but not a computer expert. I was trying to run Blender on my Acer Aspire 7730 but the screen just went crazy with the blender app window half frozen onto the desktop even after I closed the app.

Did the 'Safe' routine and things got better, but got a black bar across the bottom of the 3D window.

Did the 'Optimal' -same thing

Did the 'bleeding edge' and things now seem to be just perfect.

Thanks again for you clear instructions.

---

### Post by gaminggeek on 2009-07-12
Blender for me still isn't working perfectly, now menus will not render properly

---

### Post by glaze on 2009-07-12
> **gaminggeek said:**
> Blender for me still isn't working perfectly, now menus will not render properly

You can get Blender to display its UI correctly by downloading **statically linked** Blender 2.48a from blender.org. You also need to install Python 2.5 from Ubuntu's package manager.

---

### Post by Richard9795 on 2009-07-12
Wow, looks like the bleeding-edge method gave me some tear-free windows, but compiz is still slow! But metacity works like in intrepid, even the compositing metacity works smoother than compiz. is there something wrong with compiz?

---

### Post by gaminggeek on 2009-07-12
> **glaze said:**
> You can get Blender to display its UI correctly by downloading **statically linked** Blender 2.48a from blender.org. You also need to install Python 2.5 from Ubuntu's package manager.
I am aware of this how ever that version is using software acelleration and is quite slow on more complex scenes

---

### Post by psyke83 on 2009-07-12
> **Richard9795 said:**
> Wow, looks like the bleeding-edge method gave me some tear-free windows, but compiz is still slow! But metacity works like in intrepid, even the compositing metacity works smoother than compiz. is there something wrong with compiz?

Your performance may be worse because DRI2 supports vertical synchronization in compiz (whereas DRI1 didn't). You can disable vsync by setting "SwapbuffersWait" to false. See "man intel" for more details.

---

### Post by Richard9795 on 2009-07-12
> **psyke83 said:**
> Your performance may be worse because DRI2 supports vertical synchronization in compiz (whereas DRI1 didn't). You can disable vsync by setting "SwapbuffersWait" to false. See "man intel" for more details.

I did set it to false, but preformance was about the same, except there was tearing when i moved the window. I might want to try out all the possible options "man intel" gies me to see what happens.

---

### Post by Setomidor on 2009-07-13
I just made the switch from a desktop Debian 5 machine to a new Jaunty laptop, but the really really crappy graphics performance almost made me switch back! I've just done the "Safe" routine, and things are already considerably improved.

Thanks a bunch!

---

### Post by Jamie Jackson on 2009-07-13
> **noobaholic said:**
> OK, so I followed the rest of the instructions. My machine boots to an error message:

"Ubuntu is running in low-graphics mode

...

(EE) intel(0) Cannot support DRI with framebuffer width > 2048."

Then I get a few more error messages and my video out no longer works (using a macbook with a DVI piping video to an external monitor).

EDIT:

Seems to be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146859)

EDIT:

So I toned down my virtual display to 1900x1280 to workaround the DRI bug and... wow, my machine is really fubared... Now it seems if I boot at all with my external monitor attached, the OS locks up as soon as X starts. :(

I also get the "(EE) intel(0) Cannot support DRI with framebuffer width > 2048." message with a dual-head environment

I am then asked if I want to reconfigure the settings or use low-graphics mode.

What is the recommended strategy for dealing with a virtual display width that exceeds 2048?

(I can stack the displays on top of each other, but usability is awkward.)

BTW, lshw shows: product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

Thanks,
Jamie

---

### Post by psyke83 on 2009-07-13
> **Jamie Jackson said:**
> I also get the "(EE) intel(0) Cannot support DRI with framebuffer width > 2048." message with a dual-head environment

I am then asked if I want to reconfigure the settings or use low-graphics mode.

What is the recommended strategy for dealing with a virtual display width that exceeds 2048?

(I can stack the displays on top of each other, but usability is awkward.)

BTW, lshw shows: product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

Thanks,
Jamie

I'm not sure what's optimal for your case. As far as I'm aware, the UXA acceleration architecture has a working limit of 2048x2048 (and I'm not sure exactly why this is the case). I'm not using a multiple monitor configuration here, so I can't do much testing.

---

### Post by thefaint on 2009-07-13
Hello,

thank you for the perfect guide! I have followed the "Bleeding-edge" step and I have no problems 'till yesterday. I have upgraded my system and now my screen is not detected properly and I'm login in gnome with "safe mode" configuration. 

Is there any fix about this?

P.P. my graphic card:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by KubuntuKilledMe on 2009-07-14
> **thefaint said:**
> Hello,

thank you for the perfect guide! I have followed the "Bleeding-edge" step and I have no problems 'till yesterday. I have upgraded my system and now my screen is not detected properly and I'm login in gnome with "safe mode" configuration. 

Is there any fix about this?

P.P. my graphic card:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Me too.

---

### Post by Jamie Jackson on 2009-07-14
> **psyke83 said:**
> I'm not sure what's optimal for your case. As far as I'm aware, the UXA acceleration architecture has a working limit of 2048x2048 (and I'm not sure exactly why this is the case). I'm not using a multiple monitor configuration here, so I can't do much testing.

I guess I'll stick with workarounds for now. I've physically and virtually rotated one of my displays to get the total width to equal 2048. I might get used to it, but for right now, it's making me oddly seasick.

---

### Post by U3Lnx on 2009-07-14
> **KubuntuKilledMe said:**
> Me too.

Join the club ^^

---

### Post by RehabDJ on 2009-07-14
> **U3Lnx said:**
> Join the club ^^

Ditto

---

### Post by Orographic on 2009-07-14
I've been using the Safe Configuration approach for a month or two now on my 945GZM board and still haven't had one problem. All is well.

---

### Post by eramddd on 2009-07-15
I also have problems since yesterday.

---

### Post by von fracer on 2009-07-15
Hi,

I've had the same issue with my T60 trying the 2.6.30 final kernel and the newest 2.6.31-rc3 kernel.
My graphic card is the same as thefaint's:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Now I'm booting from the 2.6.30-9-generic kernel I got from the Koala-Kernel-PPA some time ago, cleared xorg.conf and everything works just fine. 

Chris

---

### Post by KubuntuKilledMe on 2009-07-15
> **von fracer said:**
> cleared xorg.conf

Chris

What did you do exactly? Thanks.

---

### Post by zhurai-tsuki on 2009-07-15
> **thefaint said:**
> Hello,

thank you for the perfect guide! I have followed the "Bleeding-edge" step and I have no problems 'till yesterday. I have upgraded my system and now my screen is not detected properly and I'm login in gnome with "safe mode" configuration. 

Is there any fix about this?

P.P. my graphic card:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

you could try going into the tty's (alt+ctrl+F1~F6)
or in grub go to the recovery console

then do (if in tty's):

sudo dpkg-reconfigure xserver-xorg

or in recovery console (a root account)

dpkg-reconfigure xserver-xorg

to at least try to revert your xorg.conf file back to normal

---

### Post by svelter on 2009-07-15
Hi, all. I'm not sure if this fix will help me with my problem or not. And I apologize for not reading ALL of the posts, but there are 95 pages at this point...
 
I was running Intrepid up until 2 days ago. I updated to Jaunty, and everything ran with no problem at all. Last night I tried to boot and got a screen similar to the one shown [here]("http://ubuntuforums.org/showthread.php?t=1206355") (see third image). I cannot do anything - there is no sound. I cannot do ctrl+alt+F1. I have to hard power down and restart. 
 
These are the steps I've tried:
 
[LIST]
[*]pressing esc to enter GRUB menu, I have tried all the options listed (kernel 2.6.28-13-generic; same kernel in recovery mode; kernel 2.6.27-14-generic; same kernel in recovery mode)
[*]running dpkg, i get a long list of errors (failed to fetch various items from various URLs; some index files failed to download; you way want to run apt-get update to corect these problems). it tells me it will upgrade wine and wine-gecko. I agree, and it fails to fetch the items
[*]have chosen items to update grub bootloader and xfix to auto repair graphic problems
[*]dropped to root and ran apt-get update. fails to retrieve all items and tells me to run apt-get update to correct the problems.
[*]entered the following at root:
[LIST]
[*]sudo dpkg-reconfigure xserver-xorg
[*]went through all steps to no avail
[/LIST]
[*]downloaded the .iso and burned to CD. through boot menu, booted from hard drive with various options selected (acpi=off; noapic; nolapic). none worked.
[/LIST] 
I can run Jaunty from the LiveCD - no problem there. So I don't know if the problem I have is related to my graphics card or not. I do have an ATI mobility radeon, but believe I also have a pentium video chipset integrated into the motherboard. I'm not sure which my computer is reading at this point, as my BIOS doesn't list this info.
 
Does anyone have any ideas? I tried following the guide, but upon entering the first command, my computer tells me it cannot display. (also, FYI - I am a noob and probably need things spelled out a bit more than the average bear)
 
Any help is much appreciated.

---

### Post by von fracer on 2009-07-15
Hi @ KubuntuKilledMe,

First I followed this guide here for the bleeding edge solution.
Then I tried [this]("https://wiki.ubuntu.com/X/KernelModeSetting") one as I couldn't get the boot text and the other terminals to work with the 2.6.30 kernel. ( I mean they worked but I couldn't see anything switching to them. ) But kms crashed on suspend and hibernate.

What works for me at the moment is the 2.6.30-9-generic kernel, the xserver-xorg-video-intel - 2:2.7.99.902 driver and an empty /etc/X11/xorg.conf.

I would need to see something on the tty's to try zhurai-tsuki's hint, but with the 2.6.30 kernel I don't see anything on these.

Chris

-----
ThinkPad T60 
Jaunty
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by psyke83 on 2009-07-15
Folks,

The bleeding-edge drivers are not guaranteed to work upon each update. The point of these drivers is to test the absolutely latest upstream code, warts and all. There is ample warning about this in the guide, but if you have trouble understanding this warning, consider it a threat!

Options:
[LIST=1]
[*]When you have a good, working configuration of your system, make a backup of the working packages:

Packages to backup (from /var/cache/apt/archives):
[LIST]
[*]**essential:** libdrm1-intel, libgl1-mesa-dri, libgl1-mesa-glx, libglu1-mesa, mesa-utils, xserver-common, xserver-xorg-core, xserver-xorg-input-evdev, xserver-xorg-input-synaptics, xserver-xorg-video-intel

[*]**optional (in case of dependency issues):** libdrm1-nouveau, libdrm-radeon1, xserver-xorg-video-ati, xserver-xorg-video-nv, xserver-xorg-video-nv).
[/LIST]

If you receive a bad upgrade, downgrade to the drivers you backed up, and wait for an update that fixes the issue.


[*]If for some reason you cannot downgrade to working drivers (or if you haven't backed up working drivers), temporarily switch to the VESA driver until the upgraded packages resolve whatever issues were giving you problems.

In 'Section "Device"' of your xorg.conf:

Change this line:
```
        Driver          "intel"
```
To this:
```
        Driver          "vesa"
```

**OR** add the line above manually, if the driver was not defined (which is quite likely).


[*]Revert to the default drivers! It's documented in the guide.
[/LIST]

If you're using the edgy drivers, you should always monitor [driver logs]("http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/log/") from the upstream git repository, and always keep in mind that you're probably not going to get support from this thread.

---

### Post by KubuntuKilledMe on 2009-07-16
Hi, thanks for the advice.

I understand the dangers and consequences of following the bleeding edge version of these drivers. At first i was willing to take the ridiculous performance hit on intel/jaunty but then it turned out that panda3d apps would just not work in jaunty AT ALL. I am developing in panda3d, and Searching the internet i found it didn't work for anyone and that it was considered "not a problem" because it did work on karmic alpha. So i followed this guide hoping to get panda3d working, and it did, but now the update broke it. 
Thanks a lot for the list of packages to backup when one has a working setup. Hopefully a working update will be released so i can do it.

---

### Post by U3Lnx on 2009-07-16
Maybe there is a way, to get the old updates back? Those, that were before recent updates ? :)

-- Cheers,

---

### Post by Orographic on 2009-07-16
> **svelter said:**
> ...
Does anyone have any ideas? I tried following the guide, but upon entering the first command, my computer tells me it cannot display. (also, FYI - I am a noob and probably need things spelled out a bit more than the average bear)
 
Any help is much appreciated.

If your are a noob it might not be wise to try any options available in this thread. Read the first page very carefully as it speaks of this.

And as long as the thread is, to save folk answering the same questions again, it is worth reading it. ;)

---

### Post by treesurf on 2009-07-16
Could someone please point me to some intsructions on how to install the new Karmic kernel? (I'm assuming this is the 2.6.30-9-generic kernel).  It seems many people are having good luck with it and I'm guessing this is actually a supported kernel, as opposed to the 2.6.30 that is recommended in the guide.

---

### Post by psyke83 on 2009-07-16
> **treesurf said:**
> Could someone please point me to some intsructions on how to install the new Karmic kernel? (I'm assuming this is the 2.6.30-9-generic kernel).  It seems many people are having good luck with it and I'm guessing this is actually a supported kernel, as opposed to the 2.6.30 that is recommended in the guide.

While I can't stop you doing this, let's get something clear: using the Karmic kernel in Jaunty is **absolutely not** supported.  If you file a bug on any issue - even unrelated to Intel graphics - and mention that you're using the Karmic kernel, your bug will most likely get marked invalid.

Also, the current Karmic kernel is 2.6.31-3-generic, which is based off of a release candidate (2.6.31rc3) kernel.

---

### Post by svelter on 2009-07-16
> **Orographic said:**
> If your are a noob it might not be wise to try any options available in this thread. Read the first page very carefully as it speaks of this.

And as long as the thread is, to save folk answering the same questions again, it is worth reading it. ;)

Thanks, Orographic.  I understand, but am very stubborn and like to think i understand things.  ;)  Anyhoo, my issue turned out to be unrelated to this specific issue.  During an update the other night, I downloaded a suggested driver that I feel may have been at fault.  I did a fresh side-by-side install yesterday so I could rescue my files, and my new install is working perfectly.  No glitches, no strange visual funk, and it's the exact same kernel.  Quite intriguing.

Thanks again.

---

### Post by davidY on 2009-07-16
I recently used the bleeding edge ppa, and discovered to my pleasent surprise that the kernel was in the ppa. Most is good with my X4500HD graphics card. I can now watch HD videos without tearing in mplayer/totem, with the full screen windows not being unredirected. 

However, youtube is painfully slow, not an issue with HD/HQ/LQ processing power - rather an issue with xorg. Thankfully youtube videos load to /tmp

---

### Post by Napu5 on 2009-07-16
I tried the Safe Configuration on my Lenovo s10e netbook with Intel GMA 950. It made 3D much slower (including the netbook-launcher), and no noticeable effect on 2D. I commented out Option "AccelMethod" "uxa" in xorg.conf, and everything is back to normal.

After upgrading to the 2.6.30 kernel ("Optimal Configuration") I can enable UXA without too bad performance, though glxgears give slightly lower FPS. The wireless doesn't work with 2.6.30 so I had to revert back.

Is there a problem making UXA slow on Intel GMA 950?

---

### Post by davidY on 2009-07-16
Does anybody know how to get plymouth running?

Also, I discovered that using the .30 kernel makes resume fail. It resumes the screen instantly, but there is no input and it doesn't seem to do anything. Something didn't unfreeze?

---

### Post by xItachi on 2009-07-17
Just want to point out that in the "Revert Settings" section, step 4 should be

```
$ sudo dpkg-reconfigure xserver-xorg
```
instead of 
```
$ sudo dpkg-reconfigure xorg-xserver
```

---

### Post by SteveMcQwark on 2009-07-17
I had the problem with xorg-edgers where X wouldn't start and had to revert. However, I just tried them out again and its working :)

---

### Post by U3Lnx on 2009-07-17
Hi,

  Ok, now after almost 3 days of trying to repair my laptop for work, im getting tired of trying. 
  Before the recent updates came, everything worked perfectly, i used optimal configuration by this tutorial, but after those updates nothing worked. I tried probably everything that i found on google, and cant start my 3d acceleration ( although its good that now i can start my computer, when i couldn't. When loging in, my pc restarted, o even didn't show any signs of movement )

Now im running on default kernel, jaunty version of ubuntu. (its
Linux marka-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

All other kernels just freeze the system before event starting gdm ( or freeze WHEN starting gdm :D ).

laptop:~$ glxgears -info
GL_RENDERER   = Software Rasterizer
GL_VERSION    = 2.1 Mesa 7.6-devel
GL_VENDOR     = Mesa Project

Section "Device"
	Identifier	"Intel"
	Driver		"intel"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false"
EndSection

marka@marka-laptop:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1297]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

---
Im quite desperate, compiz doesn't start, now i'm thinking of a fresh intrepid ibex install, that didn't have any problems on my metal (hw) :)

Any ideas, that had fixed their 3d acceleration, that had similar problems ?

-- Cheers,

---

### Post by Chrisn02 on 2009-07-17
Optimal Configuration seems to work well on my new Dell 10v and made Trackmania United Forever almost playable (still a bit too slow).
Not been brave enough to try "Bleeding-Edge" yet.

This is the second time this guide has helped me, once a none graphics problem.  Thank you. :D

> **Napu5 said:**
>  The wireless doesn't work with 2.6.30 so I had to revert back.
Not sure if this will help you or not but I fixed my wireless using 
[https://launchpad.net/~albertomilone/+archive/broadcom-sta](https://launchpad.net/~albertomilone/+archive/broadcom-sta)
Only Karmic is listed but I ignored it and downloaded the files anyway.
Assuming its a Broadcom wireless device that works with the drivers it should work.

---

### Post by jtreach on 2009-07-17
Thanks this works a treat with the new inspiron!

---

### Post by SteveMcQwark on 2009-07-17
> **U3Lnx said:**
> Hi,

  Ok, now after almost 3 days of trying to repair my laptop for work, im getting tired of trying. 
  Before the recent updates came, everything worked perfectly, i used optimal configuration by this tutorial, but after those updates nothing worked. I tried probably everything that i found on google, and cant start my 3d acceleration ( although its good that now i can start my computer, when i couldn't. When loging in, my pc restarted, o even didn't show any signs of movement )

Now im running on default kernel, jaunty version of ubuntu. (its
Linux marka-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

All other kernels just freeze the system before event starting gdm ( or freeze WHEN starting gdm :D ).

laptop:~$ glxgears -info
GL_RENDERER   = Software Rasterizer
GL_VERSION    = 2.1 Mesa 7.6-devel
GL_VENDOR     = Mesa Project

Section "Device"
	Identifier	"Intel"
	Driver		"intel"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false"
EndSection

marka@marka-laptop:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1297]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

---
Im quite desperate, compiz doesn't start, now i'm thinking of a fresh intrepid ibex install, that didn't have any problems on my metal (hw) :)

Any ideas, that had fixed their 3d acceleration, that had similar problems ?

-- Cheers,

I couldn't get my graphics card to work properly until I emptied my Device section in xorg.conf to look like this:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Then it worked great. (With Intel GMA 950)

It would help if you said what graphics card you have, because each one is different in terms of what gets it to work.

I haven't tried it, but above, Napu5 mentioned that commenting out the 'Option "AccelMethod" "uxa".' (again for GMA 950) I'd try that first, before trying mine.

---

### Post by Morphias on 2009-07-17
I have been following this thread for a while as a guest and trying to get ubuntu 9.04 to work on my laptop, a Dell Inspirion 1420.  I just redownloaded the distro and did a fresh reinstall (because I was testing out other distros) and I did the in place updates to the distro.
After a restart, COMPIZ works with my Intel GM965 card in this Dell Inspirion 1420.

---

### Post by cottfcfan on 2009-07-18
Can someone plz help me with psyke83s workaround.
I have a ATI radeon HD2400 card installed.
 If I run the "safe configuration" to the letter, reboot, then install the fglrx driver from  "hardware drivers" my computer runs like a dream, (everything fast, inc live streaming).
 But as soon as I reboot, I loose all my improvements. The only way I get them back is by Uninstalling and installing FGLRX again. But it only lasts for 1 boot.
 Any help would be much appreciated, ive wrestled with this for endless weeks.

---

### Post by psyke83 on 2009-07-18
> **cottfcfan said:**
> Can someone plz help me with psyke83s workaround.
I have a ATI radeon HD2400 card installed.
 If I run the "safe configuration" to the letter, reboot, then install the fglrx driver from  "hardware drivers" my computer runs like a dream, (everything fast, inc live streaming).
 But as soon as I reboot, I loose all my improvements. The only way I get them back is by Uninstalling and installing FGLRX again. But it only lasts for 1 boot.
 Any help would be much appreciated, ive wrestled with this for endless weeks.

You shouldn't be using this guide at all.

The FGLRX driver is for ATI graphics cards. This guide is for Intel graphics cards only.

---

### Post by cottfcfan on 2009-07-18
I know but it was the only workaround that stopped my computer crashing, on login.

---

### Post by Richard9795 on 2009-07-18
I have an Eee pc 900, and the graphics were terrible, but doing the bleeding edge configuration has improved a little, but installing the .31 rc3 kernel has seriously improved my preformance (but everything comes with a catch, my webcam doesnt work) but i bet a later release would fix that

here is the URL:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

go to the bottom one (2.6.31-rc3)

install image first (22 MB), then the headers (9.1 MB)

---

### Post by Miss Kudos on 2009-07-18
I love you **so hard**!

I did the basic mod on my HP Pavilion dv6000 laptop and it worked perfectly after a reboot.

THANK YOU.

Call me sometime, I'll make ya cookies :)

---

### Post by Marcelo Ramone on 2009-07-19
A few days ago  the  "low graphics mode" problem began and I fix the problem enabling the "backports" and "proposed updates" but today when I started the system this problem returned. 

 I Followed this guide carefully, I tried with different settings but it does not work.

Ubuntu is running in low graphics mode with my asrock motherboard with 945 Intel video card.

---

### Post by Orographic on 2009-07-19
> **svelter said:**
> Thanks, Orographic.  I understand, but am very stubborn and like to think i understand things.  ;)  Anyhoo, my issue turned out to be unrelated to this specific issue.  During an update the other night, I downloaded a suggested driver that I feel may have been at fault.  I did a fresh side-by-side install yesterday so I could rescue my files, and my new install is working perfectly.  No glitches, no strange visual funk, and it's the exact same kernel.  Quite intriguing.

Thanks again.

Glad you resolved it. Yeah, I like to work things out too and am quite determined but I try to remind myself to read a thread in its entirety where possible. At least the first page under its revision needs to be read anyway.

---

### Post by NagWolf on 2009-07-20
Hi,
Thought I will mention the following, I'm using an HP G7000 which has the 945 Chipset and I installed Ubuntu 64 Ultimate Edition. 
I had a problem with OpenGL and Compiz, especially GoogleEarth, what with flickering white and the usual bit and after setting up the suggested Safe Option ('cause I don't need better Bleeding edge and all that, afraid of other driver issues popping up again), Google Earth is working perfectly.

So the verdict, this solved OpenGL and Compiz issues for me, so thank you to the Author

---

### Post by incudie on 2009-07-21
Hello psyke83,

I just wanted to say thank you and that this post helped me out with my thinkpad t500. I had no problems installing.

Regards,

---

### Post by cywhale on 2009-07-21
Works great on my Lenovo X200, too, using kernel 2.6.31 from Karmic with Jaunty, Xorg/Mesa/Intel drivers from Xorg-edgers PPA.
Last issue remaining seems to be occasionally missing window decorations after suspend/resume...

---

### Post by glaubersm on 2009-07-22
My intel onboard video card dont works with Ubuntu 9.04 32 bits. Video players close itself. I have reverted to 2.4 driver version but the cpu usage is very high (22% with no application opened and 100% when i watch some video). I already attempt "optimal' and "safe" optins from this article but the X server dont starts after the steps. Can anybody help me? Thanks.
This is my video card
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```EDIT: 
"sudo dpkg-reconfigure -phigh xorg-xserver" command dont works here. Why?

---

### Post by treris on 2009-07-22
First off I want to give big thanks to psyke for this excellent howto!!

I do want to point out though that there have been two point updates to the stable 2.6.30 kernel. It might be good to update the howto to the new 2.6.30.2 kernel packages. I have already downloaded and installed them to my laptop and they work a treat. 

Honestly couldn't tell you whether they're quicker or whether they contain any further graphics improvements, but since they're bug fix releases it shouldn't hurt to update, right?

Treris

---

### Post by psyke83 on 2009-07-22
> **treris said:**
> First off I want to give big thanks to psyke for this excellent howto!!

I do want to point out though that there have been two point updates to the stable 2.6.30 kernel. It might be good to update the howto to the new 2.6.30.2 kernel packages. I have already downloaded and installed them to my laptop and they work a treat. 

Honestly couldn't tell you whether they're quicker or whether they contain any further graphics improvements, but since they're bug fix releases it shouldn't hurt to update, right?

Treris

Guide updated, thanks!

---

### Post by LifeTheHound on 2009-07-22
I just want to point out that **a new stable Intel video driver, xf86[xserver-xorg]-video-intel 2.8.0, has landed and will be hitting the x updates ppa shortly**. 

Please be advised that if you are using EXA, your system might be in trouble if the update occurs, since all EXA code has been removed in this update and will no longer be supported by Intel. 

The guide would also benefit from a rewrite of the section pertaining to EXA-specific migration heuristics and memory allotment mode. 

One more point of interest, "unsupported" though it may be: the new 2.8.0 driver was written specifically for the latest development 2.6.31 kernel, which includes highly updated kernel modules for the i915, along with other revamped intel-specific components. 

Please be advised.

---

### Post by zevans on 2009-07-23
> **LifeTheHound said:**
> 
The guide would also benefit from a rewrite of the section pertaining to EXA-specific migration heuristics and memory allotment mode. 

Meaning it's wrong? Or...?

It was Canonical that took the decision NOT to fix UXA bugs in Jaunty, and make EXA the supported configuration.

> 
One more point of interest, "unsupported" though it may be: the new 2.8.0 driver was written specifically for the latest development 2.6.31 kernel, which includes highly updated kernel modules for the i915, along with other revamped intel-specific components. 


Sigh. How can it be "stable" if it relies on an unreleased kernel?

> Please be advised.

Your post reads as if everyone should get rid of EXA immediately, otherwise everything will break. Let me emphasise this is only true if you are using xorg-edgers.

---

### Post by pepeng on 2009-07-23
how to install driver for VGA intel GMA 950 ???

---

### Post by treesurf on 2009-07-23
> **treris said:**
> First off I want to give big thanks to psyke for this excellent howto!!

I do want to point out though that there have been two point updates to the stable 2.6.30 kernel. It might be good to update the howto to the new 2.6.30.2 kernel packages. I have already downloaded and installed them to my laptop and they work a treat. 

Honestly couldn't tell you whether they're quicker or whether they contain any further graphics improvements, but since they're bug fix releases it shouldn't hurt to update, right?

Treris


A small warning:  this kernel update has killed suspend to RAM on my laptop.  Otherwise, no noticeable difference.

---

### Post by snssswc on 2009-07-24
> **The Tapsa said:**
> I have Intel GMA3100 integrated to my motherboard (Asus P5KPL-CM).
And I'm using Xubuntu 9.04.

Please could you advise how did you make xserver work please?
I have tried to install the package provided above, but got the errors below:
----
Unpacking replacement xserver-xorg-video-intel ...
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on libdrm-intel1 (>= 2.4.11+git20090519.f355ad89); however:
  Version of libdrm-intel1 on system is 2.4.9-1ubuntu1~xup~1.
 xserver-xorg-video-intel depends on libdrm2 (>= 2.4.11+git20090519.f355ad89); however:
  Version of libdrm2 on system is 2.4.9-1ubuntu1~xup~1.
dpkg: error processing xserver-xorg-video-intel (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 xserver-xorg-video-intel

---

### Post by LifeTheHound on 2009-07-24
> **zevans said:**
> Meaning it's wrong? Or...?

It was Canonical that took the decision NOT to fix UXA bugs in Jaunty, and make EXA the supported configuration.
EXA has been fully deprecated upon stable driver update to 2.8.0. This will very soon be the driver found in xorg-updates PPA as well. 


> Sigh. How can it be "stable" if it relies on an unreleased kernel?
It isn't; I am simply pointing out that the driver is made for this kernel and its updated modules. Perhaps when the kernel is officially released (a few weeks' time), it will be more so, but I am not one to say. 


> Your post reads as if everyone should get rid of EXA immediately, otherwise everything will break. Let me emphasise this is only true if you are using xorg-edgers.
This is incorrect. There will be absolutely no EXA support, even in x-updates PPA, very soon. This is because the pre-release driver touted in xorg-edgers has been completed and has now been pushed to 'stable' and will make it to x-updates very soon. Users will be rid of their EXA support whether they like it or not, no matter which of the two PPA's they use.  This is the purpose of my post, to give fair warning.

---

### Post by Browser_ice on 2009-07-24
The office desktop I installed Kubuntu 9.04 on simply do not have any section in xorg.conf related to the intel video card this PC has. So do I don't think I need to do all the steps in your tutorials. I simply want xorg.conf to have intel infos and see from there how it acts.

> lspci | grep -i intel
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

> dpkg -l | grep intel
ii  libdrm-intel1                              2.4.5-0ubuntu4                            Userspace interface to intel-specific kernel
ii  xserver-xorg-video-intel                   2:2.6.3-0ubuntu9.3                        X.Org X server -- Intel i8xx, i9xx display d


> glxinfo|grep render
Error: unable to open display              

lsmod              
Module                  Size  Used by      
i915                   65540  2            
drm                    96296  3 i915       
bridge                 56340  0            
stp                    10500  1 bridge     
bnep                   20224  2            
input_polldev          11912  0            
video                  25360  0            
output                 11008  1 video      
lp                     17156  0            
snd_intel8x0           37532  2            
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0               
snd_mixer_oss          22656  1 snd_pcm_oss   
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0                                        
snd_seq_oss            37760  0                                        
snd_seq_midi           14336  0                                        
snd_rawmidi            29696  1 snd_seq_midi                           
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi               
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq                                          
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0                                                           
iTCO_vendor_support    11652  1 iTCO_wdt                                                  
snd                    62628  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  15620  0                                                                                                                        
pcspkr                 10496  0                                                                                                                        
soundcore              15200  1 snd                                                                                                                    
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm                                                                                                   
parport_pc             40100  1                                                                                                                        
parport                42220  3 lp,ppdev,parport_pc                                                                                                    
intel_agp              34108  1                                                                                                                        
agpgart                42696  3 drm,intel_agp                                                                                                          
usbhid                 42336  0                                                                                                                        
usb_storage            82880  1                                                                                                                        
tg3                   131204  0                                                                                                                        
floppy                 64324  0                                                                                                                        
fbcon                  46112  0                                                                                                                        
tileblit               10752  1 fbcon                                                                                                                  
font                   16384  1 fbcon                                                                                                                  
bitblit                13824  1 fbcon                                                                                                                  
softcursor              9984  1 bitblit        

> /etc/X11$ cat xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#                                                            
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.                                         
#                                                                           
# Edit this file with caution, and see the xorg.conf manual page.           
# (Type "man xorg.conf" at the shell prompt.)                               
#                                                                           
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg    
# package.                                                                  
#                                                                           
# Note that some configuration settings that could be done previously       
# in this file, now are automatically configured by the server and settings 
# here are ignored.                                                         
#                                                                           
# If you have edited this file but would like it to be automatically updated
# again, run the following command:                                         
#   sudo dpkg-reconfigure -phigh xserver-xorg                               

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection                                  

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection                                       

Section "Device"
        Identifier      "Configured Video Device"
EndSection                                       

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection                             


---

### Post by thezood on 2009-07-24
> **Richard9795 said:**
> I have an Eee pc 900, and the graphics were terrible, but doing the bleeding edge configuration has improved a little, but installing the .31 rc3 kernel has seriously improved my preformance (but everything comes with a catch, my webcam doesnt work) but i bet a later release would fix that

here is the URL:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

go to the bottom one (2.6.31-rc3)

install image first (22 MB), then the headers (9.1 MB)

I went for 2.6.31-rc4 and it increased my Planet Penguin FPS from 5-10 to ~25! Let's just hope it's stable as well because I really love being able to use my little netbook for a wee bit of gaming... :)

Thanks Psyke83 and Richard9795 for your tips!

---

### Post by Orographic on 2009-07-24
> **LifeTheHound said:**
> I just want to point out that **a new stable Intel video driver, xf86[xserver-xorg]-video-intel 2.8.0, has landed and will be hitting the x updates ppa shortly**. 

Please be advised that if you are using EXA, your system might be in trouble if the update occurs, since all EXA code has been removed in this update and will no longer be supported by Intel. 

The guide would also benefit from a rewrite of the section pertaining to EXA-specific migration heuristics and memory allotment mode. 

One more point of interest, "unsupported" though it may be: the new 2.8.0 driver was written specifically for the latest development 2.6.31 kernel, which includes highly updated kernel modules for the i915, along with other revamped intel-specific components. 

Please be advised.

So, if someone has used say the Safe Config setup here, do we need to do anything in preparation for this? I have a Clonezilla image though, without any changes from this thread, that I can use is needs be.

---

### Post by psyke83 on 2009-07-24
> **Orographic said:**
> So, if someone has used say the Safe Config setup here, do we need to do anything in preparation for this? I have a Clonezilla image though, without any changes from this thread, that I can use is needs be.

You'll be fine. If you followed the Safe configuration, you're already using UXA (see the AccelMethod line from the guide).

The only difference with the 2.8.0 driver is that EXA/DRI1 support has been deprecated, which means that UXA/DRI2 is now the only choice.

---

### Post by Orographic on 2009-07-25
Thanks psyke83. I thought as much but just wanted to check. I'll go back and re-read things. The Safe Config has been great for me.

---

### Post by dfm21 on 2009-07-25
Thank you very much! The optimal configuration works like a charm on my Vaio VGN T2-XP with an 855GM.

---

### Post by Metoshade on 2009-07-26
I have tried the suggestions on an MSI X320, sadly they do not offer a vast improvement. The MSI X320 is loaded with an Atom Z530 processor and a GMA500 graphics card. The result was as follows:

Resolution: 1024x768 ( should be 1366x768 )
2D: Slow
3D (Compiz): not available

instead I will keep using the Poulsbo driver offerd by the Ubuntu Mobile PPA: [https://launchpad.net/~ubuntu-mobile/+archive/ppa/](https://launchpad.net/~ubuntu-mobile/+archive/ppa/)

(xserver-xorg-video-psb and psb-kernel-source) 

Sadly the Poulsbo 2d driver results in a slow system and the 3d and glx drivers reduce speed even more. The MSI X320 seems to be left with a slow 2d driver under Ubuntu. Windows (Vista) on the other hand feels snappy and is much faster. 

Hopefully the Linux driver guru's will help us out in the near future! Linux Rocks and I am a very happy and proud Ubuntu user, I would be very happy if the MSI X320 would get full driver support!

---

### Post by leandromartinez98 on 2009-07-26
Thanks pskyke for the how-to. The Optimal configuration worked well
on a Vaio NR11Z/S and on a EeePC 1008HA. 

The good news is that I've tested Karmic alpha 3 on both machines and
the graphics performance is even better. Actually, Karmic Alpha 3 on both these machines was increadibly responsive, running from a USB stick.

---

### Post by treris on 2009-07-26
Just for everyone's information, psyke83's especially of course, the 2.6.30 kernel has been updated to 2.6.30.3, but there aren't a lot of changes, as you can see here:

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.30.3](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.30.3)

I'm not sure whether it's actually worth updating the howto for, but then again I don't compile much so your experiences may vary.

Treris

---

### Post by H4F on 2009-07-26
there was a bug with intel graphics about leaking memory.
was that bug fixed. cause after few days my swap becomes 1 Gb and system becomse slow

---

### Post by WhiteHorse on 2009-07-27
Here are my results:
```
uname -r
2.6.30-02063002-generic
```
```
lspci -v
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011d
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
```
I am running the rc2 kernel and the bleeding edge drivers
I'm getting 25-30fps in tux-racer, 20-40 fps in Nexuiz(640x480 low graphics)
I can run Glest with no lag, 2D is great in Chromium, all compiz/Beryl desktop effects work fine. The system is overall much faster, including loading videos/music, 
I get 5fps more by not running the fixmtrr.sh script. 

By using the safe/optimal config, I got 8-12fps in tux and 10-20fps in Nexuix.

Before, with the standard kernel and drivers I got 3-5fps in tux and 3-15fps in Nexuiz. 

I now get the following errors in dmesg:
```

[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.004000] SELinux:  Disabled at boot.
[    1.592685] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.596286] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7012270), AE_NOT_FOUND

```

Basically Apparmor is disabled and the system randomly freezes once/day. All devices are working at boot-up, I don't use ndsiwrapper for wireless, and the mouse works fine when the system freezes but clicking on things has no effect and I must reboot.

---

### Post by andy_boy on 2009-07-27
Hi all, 

I've been following the instructions for the Safe Configuration, and I'm stuck on the last set of instructions. 

After running the line (from the last part of section B): 
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9 

I get the error: 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Am I doing anything wrong? Apologies if it has already been mentioned, I did have a quick look through this thread.

Thanks in advance.

---

### Post by Bogdan_C on 2009-07-27
Hi, I have a question about Intel GMA performance. Currently I'm running x64 Jaunty on a Intel DG45FC (with GMA X4500HD) with E5300 dual core processor. The system is intended as a HTPC (mainly running Boxee) but I have a bit of a problem with the "almost-non-existing" Intel drivers. Which of the config specs wrote in the first post of this thread do you recommend for clear 720 and 1080p playback? (at the moment with the latest xorg-intel drivers I have a strange playback which at some points lags on the screen and it's obviously frustrating. Besides that, I don't want Windows on my HTPC.

Thanks

---

### Post by Aris+ on 2009-07-27
In case anyone's wondering, here are the results I got following the guide.

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

So I failed to record any benchmarks before I followed this guide, but I have noticed a significant (about 80-90%) improvement in full screen flash video. Scrolling is much smoother, even on pages with an flv -- whereas it used to get super choppy and laggy as I scrolled down the page as it passed the flv. I suppose compiz animations are smoother (but I didn't install compiz till after applying these fixes)

I followed the Optimal route and here's what I got:

First I edited Xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"               "uxa"
	Option		"EXAOptimizeMigration"      "true"
	Option		"MigrationHeuristic"        "greedy"
	Option		"Tiling"                    "true"
EndSection
```
Originally I had tiling set to false but then decided to try true and it works fine this way. Still don't know what that means if anyone cares to clarify :)

On Part B Step 2 I neglected to see if any packages were to be removed because after adding the key a dialog popped up asking to update -- I don't think any packages were removed but then again I have no way of knowing (unless there are some logs I can look at?).


Then I downloaded and installed the fixmtrr script:
```
$ cat /proc/mtrr 
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
reg02: base=0x0a0000000 ( 2560MB), size=  256MB, count=1: write-combining

```
Don't know if that's better, but the output before installing the mtrr script had only two of those lines.


Then I did everything in Part C but somewhere along the line it asked me if it could update my /boot/grub/menu.lst and I said no (I recently edited it and didn't want it to screw it up). So then a bunch of stuff popped up on the screen..some stuff about DKMS...then I went to go reboot. As expected, the grub menu was exactly the same and it booted into the old 2.6.28-11-generic kernel. So I figured nothing changed.

Then today I went into my /boot/ directory and saw that the 2.6.30-02063002 kernel files are there so I edited menu.lst to include an option to boot it.

```
$ uname -a
Linux Plato 2.6.30-02063002-generic #02063002 SMP Mon Jul 20 17:21:37 UTC 2009 i686 GNU/Linux
```
So it looks like I'm running it? Not really sure. Qualitative experience seems the same since before I changed menu.lst today.

Final result: FLV video is very smooth and scrolling windows with it is smooth as well. Desktop/compiz animations are alright but then again they were never that great on 8.10 either -- I suppose they're about the same now. FLV playback is a heck of a lot smoother than on 8.10, however.

All in all, thanks for this guide, it really helped a lot!

---

### Post by psyke83 on 2009-07-27
> **Aris+ said:**
> 
Then I did everything in Part C but somewhere along the line it asked me if it could update my /boot/grub/menu.lst and I said no (I recently edited it and didn't want it to screw it up). So then a bunch of stuff popped up on the screen..some stuff about DKMS...then I went to go reboot. As expected, the grub menu was exactly the same and it booted into the old 2.6.28-11-generic kernel. So I figured nothing changed.

It's always a good idea to let the menu.lst file get updated, otherwise kernels can go missing as you've observed.

In future, be sure to edit the file correctly (editing the entries near the top of the file and then invoking "sudo update-grub").

---

### Post by psyke83 on 2009-07-27
> **Bogdan_C said:**
> Hi, I have a question about Intel GMA performance. Currently I'm running x64 Jaunty on a Intel DG45FC (with GMA X4500HD) with E5300 dual core processor. The system is intended as a HTPC (mainly running Boxee) but I have a bit of a problem with the "almost-non-existing" Intel drivers. Which of the config specs wrote in the first post of this thread do you recommend for clear 720 and 1080p playback? (at the moment with the latest xorg-intel drivers I have a strange playback which at some points lags on the screen and it's obviously frustrating. Besides that, I don't want Windows on my HTPC.

Thanks

Stick with the Safe configuration, or experiment with the Optimal (to see if the newer kernel yields better results). Most of the problems with HD playback is due to memory not being set to write-combining, so the fixmtrr.sh script should fix that issue.

---

### Post by Browser_ice on 2009-07-28
Can someone answer my question in the previous thread page ?

xorg.conf did not detect the intel 915G chipset. Because of this some applications like Blender are having refresh/drawing corruption problems.

I just want to know what to put in xorg.conf

---

### Post by TSWMIN85 on 2009-07-28
Honestly, I have no idea what I did here... but I'll put in some input.

I came here trying to get Warzone 2100 not to render 3D in black, since I have an Acer Aspire 5315 with a s*** out of luck Intel Graphics Card. So...

I tried the safe method and no luck. I went ahead start to the bledding edge because I just don't care, and it fixed my issue, and probably others I'm yet to discover.

Hopefully they fix this in Karmic.

One question, if I run into problems, this is entirely reversible?

And what are the advantages and disadvantages of me doing this?

If someone so kindly cares to elaborate.

:popcorn:

EDIT: BEFORE THIS ANY FULLSCREEN VIDEOS SUCKED VICIOUSLY (i.e. VLC, HULU, YOUTUBE, ETC.) I JUST WENT TO HULU AND BAMMMMM MY VIDEOS FULLSCREEN ARE SICKER THAN THE AVERAGE INTEL BOGGED DOWN VIDEO CARD...

ONLY IF I KNEW WHAT THE H*** I DID...

---

### Post by om26er on 2009-07-28
i have a problem my etc/X11/xorg.conf file does not have xorg.conf file and
sudo dpkg-reconfigure -phigh xorg-xserver gives the following error

Package `xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed
but i have installed xorg and xserver-xorg

---

### Post by j0hn00 on 2009-07-28
> **om26er said:**
> i have a problem my etc/X11/xorg.conf file does not have xorg.conf file and
sudo dpkg-reconfigure -phigh xorg-xserver gives the following error

Package `xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed
but i have installed xorg and xserver-xorg

it's actually

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by psyke83 on 2009-07-28
> **Browser_ice said:**
> Can someone answer my question in the previous thread page ?

xorg.conf did not detect the intel 915G chipset. Because of this some applications like Blender are having refresh/drawing corruption problems.

I just want to know what to put in xorg.conf

Your system is probably using the intel driver, but it's not giving you the performance you expect.

```
cat /var/log/Xorg.0.log | grep intel
```

If you see lots of lines prefixed with "intel(0)", you're using the right driver. No need to paste any output here.

---

### Post by Bogdan_C on 2009-07-29
> **psyke83 said:**
> Stick with the Safe configuration, or experiment with the Optimal (to see if the newer kernel yields better results). Most of the problems with HD playback is due to memory not being set to write-combining, so the fixmtrr.sh script should fix that issue.

Thanks for your support, you've done a great job with this thread. :D I went for Optimal and it works like a charm. :popcorn:

---

### Post by mabovo on 2009-07-29
> **psyke83 said:**
> Your system is probably using the intel driver, but it's not giving you the performance you expect.

```
cat /var/log/Xorg.log | grep intel
```

If you see lots of lines prefixed with "intel(0)", you're using the right driver. No need to paste any output here.

Wouldn't be cat /var/log/Xorg.0.log | grep intel ?

---

### Post by psyke83 on 2009-07-29
> **mabovo said:**
> Wouldn't be cat /var/log/Xorg.0.log | grep intel ?

That's right, thanks.

---

### Post by ENigma885 on 2009-07-29
Thanks psyke83 for ur effort!

I followed the _"Optimal Configuration"_ but it seems like the old slow performance is gone...and now a [COLOR="Red"]new problem appears[/COLOR]
I usually use [[COLOR="Blue"]Cooliris[/COLOR]]("http://www.cooliris.com/") to test VGA performance since it used not to work at all with the default old configuration.

The problem is that few minutes after Cooliris is launched my _*swap jumps to >85% usage*_, which wasn't the case before this change,. 
And to make sure it's not Cooliris problem. I only launched few applications like a mediaplayer, Firefox, and few OOo documents (with compiz enabled) and the same swap overusage.

---

### Post by garijon on 2009-07-29
> **ENigma885 said:**
> Thanks psyke83 for ur effort!

I followed the _"Optimal Configuration"_ but it seems like the old slow performance is gone...and now a [COLOR="Red"]new problem appears[/COLOR]
I usually use [[COLOR="Blue"]Cooliris[/COLOR]]("http://www.cooliris.com/") to test VGA performance since it used not to work at all with the default old configuration.

The problem is that few minutes after Cooliris is launched my _*swap jumps to >85% usage*_, which wasn't the case before this change,. 
And to make sure it's not Cooliris problem. I only launched few applications like a mediaplayer, Firefox, and few OOo documents (with compiz enabled) and the same swap overusage.

I've done the same and have the same problem with swap.

---

### Post by duvoisin on 2009-07-30
I tried both the safe and the optimal patches on my 901, but neither one was workable. Optimal could not complete regular bootup because of an incomplete video configuration. Safe hangs up during boot unless I choose an earlier kernel in the grub. I removed the safe patches except for the fixmttrr.sh patch, as your final note suggests, however, and this seems to have improved my flash video a bit. It's not perfect, but hulu is now watchable full screen. It also seems to survive rebooting, for some reason--mine is gnome, but I was under the impression that it would be erased after a reboot without the rest of the patch. Perhaps it is preserved by the asus eeepc boot booster feature.

jad

---

### Post by treesurf on 2009-07-30
> **treesurf said:**
> A small warning:  this kernel update has killed suspend to RAM on my laptop.  Otherwise, no noticeable difference.


The 2.6.30.3 kernel has restored suspend RAM. Thanks!:D

---

### Post by PreThunder on 2009-07-31
Hi!

Thanks for this awsome guide, it really helped improved scrolling and other stuff like workspace switching:)

However, not everything is what it could be. For example when I play a video it is noticably stuttering a little. Also, when I play games like planet penguin racer it still has small stuttering in it.

I have the optimal Configuration set. I even tried reinstalling the fixmtrr script, but it said it was already running, so that shouldn't be the problem.

I have a Fujitsu Siemems Amilo Pi 1505 with an Intel 945GM card

---

### Post by treris on 2009-08-01
Yet another kernel update has been released, with a significantly longer changelog this time. I didn't really see anything related to intel graphics performance, but I could be wrong of course.

Anyone interested can find the changelog here: [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.30.4](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.30.4)

The updated kernel packages can be found here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.4/)

---

### Post by treris on 2009-08-01
> **PreThunder said:**
> Hi!

Thanks for this awsome guide, it really helped improved scrolling and other stuff like workspace switching:)

However, not everything is what it could be. For example when I play a video it is noticably stuttering a little. Also, when I play games like planet penguin racer it still has small stuttering in it.

I have the optimal Configuration set. I even tried reinstalling the fixmtrr script, but it said it was already running, so that shouldn't be the problem.

I have a Fujitsu Siemems Amilo Pi 1505 with an Intel 945GM card

Unfortunately even with the latest packages the graphics performance isnt overly impressive, you can find some recent benchmarks of the current intel graphics stack at [Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=intel_q309_flakes&num=1").

Hopefully it will get better over the next few months leading up to Karmic....

Treris

PS saw that this was you're first post on this forum; welcome!

---

### Post by benne on 2009-08-01
You have a small error in your guide. 

> 0. Optional: If there is no xorg.conf file present on your system, the following command will create a minimal configuration (which you can customize later):
Code:

```
$ sudo dpkg-reconfigure -phigh xorg-xserver
```



The package is named xserver-xorg and not xorg-xserver. Thus the code should be:

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bonfire89 on 2009-08-03
OMG!!! I can watch youtube!!!!!!!!!!!:guitar:

heh. 

I followed the instructions for "optimal"

on a thinkpad x60 tablet with a fresh install of jaunty.


Hopefully this is not all in my head. I have tried a few fixes in the past and I think I wanted them to work so much that I saw performance gains that didn't exist.

I know we aren't supposed to trust glxgears. but going from ~150 to ~770-880 has to mean something!


EDIT: It seems as if I can no longer user the external monitor.

---

### Post by Browser_ice on 2009-08-03
> **psyke83 said:**
> That's right, thanks.

By the way, its more like
[INDENT]cat /var/log/Xorg.0.log | grep intel[/INDENT]

Doing this I have around 50 lines of intel(0). 

Now, what is the whole xorg.conf that I have to use in order for this office to use the Intel driver ?  I already posted what I have so far on this. I don't want to spend days replying to fix it.

I assume its because it is not properly used that I have graphic corruptions in Blender. Right ?

---

### Post by glaze on 2009-08-04
> **Browser_ice said:**
> 
I assume its because it is not properly used that I have graphic corruptions in Blender. Right ?

Blender's graphic corruption seems to be Mesa related. You can download a statically linked older release of Blender, it works without corruption.

---

### Post by Browser_ice on 2009-08-04
> **glaze said:**
> Blender's graphic corruption seems to be Mesa related. You can download a statically linked older release of Blender, it works without corruption.

Ok but my initial question is not answered.

---

### Post by psyke83 on 2009-08-04
> **Browser_ice said:**
> Ok but my initial question is not answered.

It was answered. You assumed that because Blender wasn't working correctly that the intel driver wasn't being used properly. It is.

---

### Post by jeremyjjbrown on 2009-08-05
Since preforming the "safe" method on my laptops I now no longer get updates on either machine either automatically or manually. I have also had issues trying to install other software. 

Basically Youtube works now, but apt doesn't. Since this is on two very different machines I can't be the only one. Any ideas?

update...

commenting the new addresses out of my sources list abates the issue. 

# deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA
# deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA

I'd like to find a way to properly fix this.

---

### Post by emeraldgirl08 on 2009-08-05
**This is my lspci.**

```
yrene@tyrene-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

05:00.0 USB Controller: NEC Corporation USB (rev 43)

05:00.1 USB Controller: NEC Corporation USB (rev 43)

05:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

**And my xorg.conf.**

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

As you can tell I don't have any tweaks for my video driver. My things run fine for the time being however- I'd like to know what I could do to maximize the current hardware I'm running. I also should mention that I'm using 1gb of RAM now (512 + 512) and will be receiving 2gb (1 + 1) in the mail any day now if that will help :)

---

### Post by psyke83 on 2009-08-05
> **jeremyjjbrown said:**
> Since preforming the "safe" method on my laptops I now no longer get updates on either machine either automatically or manually. I have also had issues trying to install other software. 

Basically Youtube works now, but apt doesn't. Since this is on two very different machines I can't be the only one. Any ideas?

update...

commenting the new addresses out of my sources list abates the issue. 

# deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA
# deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA

I'd like to find a way to properly fix this.

You can't get updates through update-manager (the GUI)? Maybe you misinterpreted a warning about a missing repository key - make sure you've followed the instructions in the guide, including the step to add the X-Updates PPA key to your system.

---

### Post by psyke83 on 2009-08-05
> **emeraldgirl08 said:**
> 
As you can tell I don't have any tweaks for my video driver. My things run fine for the time being however- I'd like to know what I could do to maximize the current hardware I'm running. I also should mention that I'm using 1gb of RAM now (512 + 512) and will be receiving 2gb (1 + 1) in the mail any day now if that will help :)

Follow this guide only if you feel that 2D or 3D performance isn't good enough. If you want to proceed, I recommend you stick with the Safe configuration. 

You may get a performance boost by using the 2.6.31.3 kernel (the only difference between Safe and Optimal configuration), so try that if you're still not satisfied. Just make sure to read the guide fully (including warnings).

---

### Post by emeraldgirl08 on 2009-08-05
Psyke. This is only a temporary fix right?

I'm hoping that Karmic has a built-in solution for my type of machine (I kinda doubt it b/c it's an older chipset). When Karmic is distributed by Ubuntu do you think I'd have to reinstall these mods to my xorg file???

---

### Post by draggy on 2009-08-05
I'm not sure what else I can do. I've tried the safe and bleeding edge multiple times over the past few months and every time compiz performance in the NBR main window is so slow it's unusable. 

2D performance seems fine, and testing 3D performance with ppracer shows hardly any gain at all.

If I try to go back to EXA with edgers, compiz is still just as slow as it was with UXA. The only way to get the compiz performance back to normal is to revert everything back to x-updates ppa or before.

I have a eee 900 with a 945GME chipset

Does anyone have any suggestions, I don't know what else to do with this chipset.

---

### Post by psyke83 on 2009-08-05
> **emeraldgirl08 said:**
> Psyke. This is only a temporary fix right?

I'm hoping that Karmic has a built-in solution for my type of machine (I kinda doubt it b/c it's an older chipset). When Karmic is distributed by Ubuntu do you think I'd have to reinstall these mods to my xorg file???

Karmic will include the latest drivers, so there won't be any need for this guide.

---

### Post by emeraldgirl08 on 2009-08-06
:)

I can't wait for Karmic then!

As for tweaking right now...I'll just leave it be. Karmic is due out in what....two or three months?

I should also mention that I can use the extra or normal visual effects but choose none. I just like to use my OS w/o so much eyecandy.

It's nice knowing that it's there though for showing off ;)

---

### Post by PreThunder on 2009-08-06
> **treris said:**
> Unfortunately even with the latest packages the graphics performance isnt overly impressive, you can find some recent benchmarks of the current intel graphics stack at [Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=intel_q309_flakes&num=1").

Hopefully it will get better over the next few months leading up to Karmic....

Treris

PS saw that this was you're first post on this forum; welcome!

Thanks for replying

Yeah, I'm planning on reinstalling Ubuntu with Karmic once it has been officially released^^

---

### Post by jonathanmotes on 2009-08-08
How would I install the restricted modules for the corresponding new kernel (for the optimal setup)? My broadcom 4312 wireless breaks with the new kernel....

Thanks :)

---

### Post by jback2 on 2009-08-09
I wanted to ask you about an improvement in Jaunty (without any manual fixes). GLXGears now has more than 1400 FPS each round. Okay, I know that this isn't a real benchmark but thats a great improvement as far as I remember the first days with Jaunty.

But I still have problems with Compiz. Especially big apps animations like Firefox or Eclipse lag very hard. Is this still a driver problem? Or is it normal at last that compiz animations don't have such a constant frame rate?

Thanks for reading.

---

### Post by jeremyjjbrown on 2009-08-09
Has anyone else experienced random xorg crashes?

I did the "safe" method on my MSI Wind U100 and xorg crashes to a black screen at random times.

The Wind has an Intel Mobile 945GM/GMS/GME/ Express Integrated Graphics Controller.

Thanks

---

### Post by VMC on 2009-08-09
> **jeremyjjbrown said:**
> Has anyone else experienced random xorg crashes?

I did the "safe" method on my MSI Wind U100 and xorg crashes to a black screen at random times.

The Wind has an Intel Mobile 945GM/GMS/GME/ Express Integrated Graphics Controller.

Thanks

Yes, I have. I've had two different types of "black screen". One, it just goes black for a few seconds, then reappears like magic. The other one never recovers and it appears to restart xorg. I see the small white wheel at times, and my indicator lights go off and on. That takes a hard reset. I haven't had either in a few days. Hopefully and update fix it. I have an integrated i865 chip.

---

### Post by Orographic on 2009-08-10
> **jeremyjjbrown said:**
> Has anyone else experienced random xorg crashes?

I did the "safe" method on my MSI Wind U100 and xorg crashes to a black screen at random times.

The Wind has an Intel Mobile 945GM/GMS/GME/ Express Integrated Graphics Controller.

Thanks

I have a Gigabyte desktop 945GZM-S2 mobo with integrated graphics and it works very well with the Safe Config approach.

---

### Post by bearozo on 2009-08-10
> **VMC said:**
> Yes, I have. I've had two different types of "black screen". One, it just goes black for a few seconds, then reappears like magic. The other one never recovers and it appears to restart xorg. I see the small white wheel at times, and my indicator lights go off and on. That takes a hard reset. I haven't had either in a few days. Hopefully and update fix it. I have an integrated i865 chip.

I have these with my i845 and had before I tried this howto, I am now running bleeding edge and everything else works fine (except compiz chip is blacklisted) peformance is very good for this old p4 laptop. But I get random "blackouts" I can not log in and back and randomly at start I get progress bar but no "little wheel" or graphical log in, just a black screen, I can log in blindly and hit F12  (Yakuake) for terminal and do a "blind" sudo reboot after 1, 2, or 3 reboots I am back to normal. No need for hard resets though if you cannot use blind log in use REISUB (Ctrl + Alt + SysRq (Prnt Screen) keep holding Ctrl + Alt and press R+E etc. one at the time.

I h

---

### Post by zevans on 2009-08-10
> **jeremyjjbrown said:**
> 
The Wind has an Intel Mobile 945GM/GMS/GME/ Express Integrated Graphics Controller.


I run everything bleeding-edge on my MSI Wind clone and have been doing so for months now - it all works fantastically well. So rather than worry about "safe" I would upgrade to "bleeding-edge."

---

### Post by zevans on 2009-08-10
OK thanks for the clarifications!

> **LifeTheHound said:**
> 
There will be absolutely no EXA support, even in x-updates PPA, very soon. This is because the pre-release driver touted in xorg-edgers has been completed and has now been pushed to 'stable' and will make it to x-updates very soon. 


I agree this is good news and gives much better focus.

I was asking on behalf of users who use Jaunty as-shipped who are still suffering from freeze-bugs and so on. Are you saying that 2.8 will go into jaunty-updates? (This is not the same thing as x-updates, or did you mean "x" to stand for [jaunty|karmic] ?)

> Users will be rid of their EXA support whether they like it or not, no matter which of the two PPA's they use.

I wasn't talking about PPAs - I was talking about Joe User who expects Ubuntu to work properly on his netbook without having to mess with additional PPAs...

---

### Post by zevans on 2009-08-11
We now have friends in high places...
[http://xkcd.com/619/]("http://xkcd.com/619/")

---

### Post by instant on 2009-08-11
Hi Guys!

Great thread, nice and easily understandable.

I have a little problem with my laptop.

I recently installed Ubunut 9.04 so it is completely fresh.
I tried following the guide but for some reason this lowers my performance, ie in PPracer from 25-37fps down to 10-25fps

I reverted the changes but let the fixmtrr.sh still run when X starts, still no change, but after doing a chmod -x on the fixmtrr.sh everything seems fine and PPracer is back to 37fps.

With other words my issue is with the fixmtrr.sh which seems strange, 
does anyone have an explanation to this since I would like to have even better performance than I already have.

I've got a:
```
instant@laptop1:~$ lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

Thx, 
instant.

---

### Post by psyke83 on 2009-08-11
> **instant said:**
> 
I reverted the changes but let the fixmtrr.sh still run when X starts, still no change, but after doing a chmod -x on the fixmtrr.sh everything seems fine and PPracer is back to 37fps.


Can you paste the contents of /proc/mtrr before **and** after running the fixmtrr.sh script?

---

### Post by burkas on 2009-08-12
Anyone had try xorg intel driver (2.8) in Jaunty ? I had try it and desktop didn't show off. But i was installed it completely. Anyone know what's my fault ?

---

### Post by instant on 2009-08-12
[B]@psyke83
[/B]

Before running fixmtrr.sh
```
reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg03: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg04: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable

```

After manually running fixmtrr.sh
```
Extracing base address and memory size from lspci -v
d0000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg03: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg04: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable

```

I dont really see any difference between the two but just tried PPracer and I once again have lower FPS.

Thankful for any help,
instant

---

### Post by ilna on 2009-08-12
> **psyke83 said:**
> Can you paste the contents of /proc/mtrr before **and** after running the fixmtrr.sh script?
I also have the problem - up to date Karmic. After rebooting and being in KDE (I have added BEFORE/AFTER echos):
```

$ sudo ./fixmtrr.sh
cat /proc/mtrr BEFORE:             
reg00: base=0x080000000 ( 2048MB), size= 2048MB, count=1: uncachable
reg01: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg03: base=0x140000000 ( 5120MB), size=  512MB, count=1: write-back
reg04: base=0x160000000 ( 5632MB), size=  256MB, count=1: write-back
reg05: base=0x170000000 ( 5888MB), size=  128MB, count=1: write-back
reg06: base=0x178000000 ( 6016MB), size=   64MB, count=1: write-back
reg07: base=0x0af800000 ( 2808MB), size=    8MB, count=1: uncachable
Extracing base address and memory size from lspci -v
d0000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
cat /proc/mtrr AFTER:
reg00: base=0x080000000 ( 2048MB), size= 2048MB, count=1: uncachable
reg01: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg03: base=0x140000000 ( 5120MB), size=  512MB, count=1: write-back
reg04: base=0x160000000 ( 5632MB), size=  256MB, count=1: write-back
reg05: base=0x170000000 ( 5888MB), size=  128MB, count=1: write-back
reg06: base=0x178000000 ( 6016MB), size=   64MB, count=1: write-back
reg07: base=0x0af800000 ( 2808MB), size=    8MB, count=1: uncachable

 
```Also /var/log/messages has this fragment:


```
Aug 12 19:35:06 localhost kernel: [    1.540207] agpgart-intel 0000:00:00.0: Intel 965G Chipset
Aug 12 19:35:06 localhost kernel: [    1.541047] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Aug 12 19:35:06 localhost kernel: [    1.543783] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Aug 12 19:35:06 localhost kernel: [    1.558561] [drm] Initialized drm 1.1.0 20060810
Aug 12 19:35:06 localhost kernel: [    1.566119] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 12 19:35:06 localhost kernel: [    1.569486] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Aug 12 19:35:06 localhost kernel: [    1.569489] [drm] MTRR allocation failed.  Graphics performance may suffer.
Aug 12 19:35:06 localhost kernel: [    1.689866] [drm] fb0: inteldrmfb frame buffer device
Aug 12 19:35:06 localhost kernel: [    1.689946] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

```

---

### Post by GNUbee40 on 2009-08-12
Hello there!

Tried the Safe mode with good success. HD Youtube is no longer an issue. However, now I get logged out every time I send my machine to sleep and thus loose all my opened windows. Not sure if this is related to the X-upgrades, but I suppose it is some kind of problem with X.
Any comments or suggestions, what could have changed?

Regards

---

### Post by PatrickVogeli on 2009-08-12
yeah, I had that problem too. It was related to UXA, using EXA it didn't happen, if I recall correctly.

What I ended doing? upgrading to the optimal bleeding edge. Once I found a completely working update, I disabled the extra ppas, so I have everything I need working, nice speed and on breakage.

---

### Post by instant on 2009-08-12
I've been doing some reading about this whole MTRR thing here and I believe that my only issue is that I cannot change /proc/mtrr.

I checked the fixmtrr.sh script and tried the commands manually, but all i get is an error message about invalid argument.
I have seen this exact issue [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210780"), but cant seem to replicate the workaround mentioned in the report.

The workaround is exactly what the fixmtrr.sh script does, simply:
```
echo "base=0xd0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```

Anyone? 

/instant

---

### Post by psyke83 on 2009-08-12
> **instant said:**
> I've been doing some reading about this whole MTRR thing here and I believe that my only issue is that I cannot change /proc/mtrr.

I checked the fixmtrr.sh script and tried the commands manually, but all i get is an error message about invalid argument.
I have seen this exact issue [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210780"), but cant seem to replicate the workaround mentioned in the report.

The workaround is exactly what the fixmtrr.sh script does, simply:
```
echo "base=0xd0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```

Anyone? 

/instant

Try the following to see if it helps:

a) Update your BIOS to the latest version;
b) Boot the kernel with the extra parameter "enable_mtrr_cleanup"
c) Try the "mtrr_uncover" tool.

See [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210780/comments/36") comment from [bug #210780]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210780") (but keep in mind that an increase or decrease in glxgears fps does not necessarily mean very much).

---

### Post by Mr_bleu on 2009-08-12
Do we have to wait until 9.10 is released to get intel driver support via synaptic/adept managers?  I don't like the idea of having to mess around to get my graphics working enough to play a game.  I've reinstalled Windows :(  and am using it to play Eternal Lands.  I get a whopping 6 fps and average 4 with 9.04 installed.  I've been using linux since 2007.  This is by far my worst experience related to it.  I really like linux.

---

### Post by jeremyjjbrown on 2009-08-12
> **zevans said:**
> I run everything bleeding-edge on my MSI Wind clone and have been doing so for months now - it all works fantastically well. So rather than worry about "safe" I would upgrade to "bleeding-edge."

I upgraded to optimal and the xorg crashes are gone. Thanks.

---

### Post by poosterl on 2009-08-13
[SIZE=2]Thanks psyke83, this surely helped a lot, I'd been wondering about the poor graphics performance on my DELL D620 :(.

I went for the optimal configuration.

When rebooting with the 2.6.30 kernel, the graphics performance was as I would expect it to be and everything *seemed* to work just splendidly ... until I launched my (genuine) Cisco VPN client. As soon as I tried to navigate to some site in Firefox, my system just frooze completely. When I reboot with the last canonical jaunty kernel (i.e. reverting to the "safe configuration") I apparently have the same performance but without VPN troubles.[/SIZE]

---

### Post by rbloch66 on 2009-08-13
This fix is just what the doctor ordered.

THANK YOU!!!!!!

Games run up to speed and video's no longer crash the players.

:P

---

### Post by instant on 2009-08-13
Hey thanks alot psyke83!! :P One problem solved, I think.

Added enable_mtrr_cleanup to the kernel line in GRUB and my /proc/mtrr now reads:

```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg03: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg05: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining
```
[I]
Does this look OK to you guys?[/I] I dont know anything about this but
i've got 4Gb RAM and 256Mb Graphics memory.

Not a big FPS difference in PPracer but still, a step in the right direction.

/instant

---

### Post by ilna on 2009-08-14
How to downgrade after trying xorg-edgers?[U]
[/U]

---

### Post by rgsteele on 2009-08-14
> **ilna said:**
> How to downgrade after trying xorg-edgers?[U]
[/U]

Follow the instructions in the "To Revert Settings" section.

---

### Post by ilna on 2009-08-14
> **rgsteele said:**
> Follow the instructions in the "To Revert Settings" section.Ups.. Sorry... Where were my eyes?

---

### Post by treesurf on 2009-08-14
Whatever happened to that update that was supposed to hit the X-Updates PPA?

---

### Post by ilna on 2009-08-15
Up to date Karmic has happened :-)

---

### Post by vedek on 2009-08-15
worked like a charm mate thanks, firefox is a bit unresponsive but thats nothing to do with the graphics side of things.

---

### Post by Orographic on 2009-08-16
> **Mr_bleu said:**
> Do we have to wait until 9.10 is released to get intel driver support via synaptic/adept managers?  I don't like the idea of having to mess around to get my graphics working enough to play a game.  I've reinstalled Windows :(  and am using it to play Eternal Lands.  I get a whopping 6 fps and average 4 with 9.04 installed.  I've been using linux since 2007.  This is by far my worst experience related to it.  I really like linux.

I guess we are all different. Its was a disappointing problem, this issue in Jaunty but its not that long to wait until Karmic. For me, I would rather wait than go to Windows to play a game but I respect your need for games.

---

### Post by VMC on 2009-08-16
> **Orographic said:**
> I guess we are all different. Its was a disappointing problem, this issue in Jaunty but its not that long to wait until Karmic. For me, I would rather wait than go to Windows to play a game but I respect your need for games.

I'm using both jaunty and Karmic, with the same results. I have an i865 integrated chip and I have to revert to the old intel-2.4 driver and use "nomodeset" on Karmic. So if there is a fix it's not here yet.

---

### Post by sonusikka on 2009-08-17
```
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable


00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: [e4] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: intelfb

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20)
	Subsystem: Dell Device [1028:0160]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 40000000-400fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Region 5: Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 3
	Region 4: I/O ports at eda0 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
	Subsystem: Dell Device [1028:0160]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at ee00 [size=256]
	Region 1: I/O ports at edc0 [size=64]
	Region 2: Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:09.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
	Subsystem: Dell Device [1028:8127]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fe9fe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at 40000000 [disabled] [size=16K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: b44
	Kernel modules: b44
```

---

### Post by cariboo on 2009-08-17
@sonusikka

It would help if you explained your problem, instead of posting the output of several commands. We are here to help, but we can't answer the question if we don't know what it is.

---

### Post by pkeefe on 2009-08-17
I've been seeing the following error message on a laptop with a 945GM chipset that is running the base install of Ubuntu 9.04.
[FONT=monospace]
[/FONT]../../../libdrm/intel/intel_bufmgr_gem.c:624: Error mapping buffer 64593(region): Cannot allocate memory .
Shortly after this occurs, I see the following segfault:

Aug 17 09:06:51 laptop kernel: [ 5483.189649] python2.5[3461]: segfault
at 0 ip b3e2d82a sp af037080 error 6 in i915_dri.so[b3d34000+246000]

Also, I noticed the following messages in dmesg:

    [   37.981052] [drm] Initialized i915 1.6.0 20080730 on minor 0
    [   37.983083] [drm:i915_setparam] *ERROR* unknown parameter 4
    [   37.983111] [drm:i915_getparam] *ERROR* Unknown parameter 6
    [   39.692696] [drm:i915_getparam] *ERROR* Unknown parameter 6
    [   54.302753] [drm:i915_getparam] *ERROR* Unknown parameter 6
    [   57.616276] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank 
count for disabled pipe 0

These messages indicate that invalid IOCTLs are being sent down to the driver.
So, I took a look at libdrm-intel1 v2.4.5-0ubuntu4 which comes standard with 
Ubuntu 9.04 and compared it with the xserver-xorg-video-intel driver v2.6.3-0ubuntu9 and they are obviously out of sync in terms of the IOCTLs in the driver not
existing yet.  Could this have anything to do with the issues that I'm seeing?
Is this a known problem?

---

### Post by sonusikka on 2009-08-18
@all users
well I'm not able to enable my desktop effects to either normal or extra!!

---

### Post by bearozo on 2009-08-18
> **sonusikka said:**
> @all users
well I'm not able to enable my desktop effects to either normal or extra!!

I have the same chip, it is blacklisted in compiz so u cannot turn on desktop effects well u
can edit out from blacklist but it still will not work it will freeze the puter.

---

### Post by sonusikka on 2009-08-19
but it was working fine in hardy heron and i was able to have all features including cube and others as well!!
is there no possible solution in jaunty!!

---

### Post by PatrickVogeli on 2009-08-19
yeah, sure it is. I have an Intel x3100 (the 965 chipset) and compiz is working fine.

just do the following:

```

cd
touch .config/compiz/compiz-manager
echo "SKIP_CHECKS=yes" > .config/compiz/compiz-manager

```

Then go and try to activate compiz again.

---

### Post by relgames on 2009-08-19
Hello again. Still no answers since May. The guide didn't help me.

Now I updated to 9.10, and I have the following kernel & drivers:
```
Linux oleg-laptop 2.6.31-6-generic #25-Ubuntu SMP Fri Aug 14 16:25:04 UTC 2009 i686 GNU/Linux
``````
oleg@oleg-laptop:~$ dpkg -l |grep intel
ii  libdrm-intel1                        2.4.12-1ubuntu1                            Userspace interface to intel-specific kernel
ii  xserver-xorg-video-intel             2:2.8.0-0ubuntu2                           X.Org X server -- Intel i8xx, i9xx display d

```/proc/mtrr:
```
oleg@oleg-laptop:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

```And again, when I try to run fixmtrr.sh, nothing changes.

fixmtrr.sh:
```
#!/bin/sh
echo "Extracing base address and memory size from lspci -v"

# extract the base address for the video memory
address=`lspci -v \
    | grep -A 7 VGA\
    | grep -F " prefetchable"\
    | awk 'BEGIN{OFS="";ORS=""}
          {print $3
          i = length($3)
          while(i<8){
                  print 0
                   i++
           }}'`

# we extract the memory size as a decimal number from lspci from the correct
# line, we then convert it to hexadecimal and fill it up with the correct
# number of zeroes

hsize=`lspci -v \
    | grep -A 7 VGA \
    | grep -F " prefetchable" \
    | awk '{print $6}' \
    | sed 's/[^0-9]//g' \
    | awk 'BEGIN {OFS = "";ORS=""}
           { printf "%x" , $1
         i = length($1)
         while (i<8) {
             print 0
             i++
         } }'`

echo $address
echo $hsize
echo

# check if the mtrr range has already been set and, if it hasn't, set it up
echo 1
echo "Supplying corrected MTRR ranges to /proc/mtrr"
echo "base=0x$address size=0x$hsize type=write-combining"

echo "base=0x$address size=0x$hsize type=write-combining" > /proc/mtrr

echo 2
cat /proc/mtrr

```

```
oleg@oleg-laptop:~$ sudo ./fixmtrr.sh 
Extracing base address and memory size from lspci -v
e0000000
10000000

1
Supplying corrected MTRR ranges to /proc/mtrr
base=0xe0000000 size=0x10000000 type=write-combining
2
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
oleg@oleg-laptop:~$ 

```


lspci -v
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 024f
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ef98 [size=8]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 024f
    Flags: bus master, fast devsel, latency 0
    Memory at f6b00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

```Help me please!!! I really love Ubuntu, it works great on my second laptop and on office workstation, but it really bothers me with my Dell laptop...

---

### Post by bearozo on 2009-08-20
I have not found one but there might be one, 845 is the only one on the list now.

---

### Post by psyke83 on 2009-08-20
> **relgames said:**
> Hello again. Still no answers since May. The guide didn't help me.

See: [http://ubuntuforums.org/showthread.php?p=7776678&highlight=enable_mtrr_cleanup#post7776678](http://ubuntuforums.org/showthread.php?p=7776678&highlight=enable_mtrr_cleanup#post7776678)

---

### Post by Mr_bleu on 2009-08-20
I reverted to the 2.4 intel driver to play in ubuntu.  This has helped me alot.  I only use the windows partition to use my printer or connect to my Blackberry.

---

### Post by VMC on 2009-08-20
> **Mr_bleu said:**
> I reverted to the 2.4 intel driver to play in ubuntu.  This has helped me alot.  I only use the windows partition to use my printer or connect to my Blackberry.

According to your stats, you have a 945G chip. I have read success from others. I have to use 2.4 driver, since I have i865 chip. Have you followed this guide completely? Also, what's wrong with your printer? Most work without problems.

---

### Post by relgames on 2009-08-21
> **psyke83 said:**
> See: [http://ubuntuforums.org/showthread.php?p=7776678&highlight=enable_mtrr_cleanup#post7776678](http://ubuntuforums.org/showthread.php?p=7776678&highlight=enable_mtrr_cleanup#post7776678)
I updated my BIOS to the latest one from Dell website (A13)

Then I tried to boot with enable_mtrr_cleanup option, but there were no any changes, and the next messages were in log files:
```
Aug 21 20:01:16 oleg-laptop kernel: [    0.000000] mtrr_cleanup: can not find optimal value
Aug 21 20:01:16 oleg-laptop kernel: [    0.000000] please specify mtrr_gran_size/mtrr_chunk_size

```

Next I tried mtrr-uncover, and now my /proc/mtrr looks like:
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg04: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back
reg05: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg06: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back

```

But I don't see video memory here.. According to my lspci -v it should be "e0000000"
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 024f
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
    [COLOR=Red]Memory at e0000000 (64-bit, prefetchable) [size=256M][/COLOR]
    I/O ports at ef98 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```

And fullscreen flash video still goes ugly...

---

### Post by mrkrrtft on 2009-08-22
> **psyke83 said:**
> 
**_Optimal*_ Configuration**
[LIST]
[*]This configuration is identical to "Safe", but includes the [2.6.30]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/") kernel. Using this kernel will improve 3D performance for many users, but you will lose access to restricted kernel drivers. This configuration yields the best results for my system (an 855GM chipset), but of course, your experience may differ.
[/LIST]

A week ago I installed 9.04.  I am really enjoying using Ubuntu fulltime on one of my computers.  In a way it is freeing not having to rely on Microsoft software.

I wanted to say Thank You for this article.  I followed the Optimal Config, and my major issue was resolved.

FYI, the major issue was fullscreen video playback of Flash based video.  Specifically, Hulu.com.  I followed all the steps for Optimal, rebooted after the kernel install, booted into the 2.6.30xxx kernel, ran Hulu.com, fullscreen LOST S01E01 and w00t! No choppy video.

FYI, 3D performance wasn't my goal as my laptop (Dell Inspiron 6000) isn't that great.  Just fullscreen flash video. :) 

THANKS!!!!!!!

---

### Post by treesurf on 2009-08-22
I've just ordered a new laptop with an Intel 4500MHD.  Does anyone have any experience with this chipset?  I'm curious to know which configuration works best with the 4500MHD.

thanks.

---

### Post by treesurf on 2009-08-22
I've just ordered a new laptop with an Intel 4500MHD.  Does anyone have any experience with this chipset?  I'm curious to know which configuration works best with the 4500MHD.

thanks.

---

### Post by relgames on 2009-08-23
> **relgames said:**
> ......
And fullscreen flash video still goes ugly...
Also X.Org constantly consumes 25-30% of CPU. User interface is very slow (I used Gnome and now use Xfce). When I reboot my laptop, this problem is temporary solved, but then it goes high again after some period of time.

---

### Post by relgames on 2009-08-23
Finally, I added the next lines to kernel boot options:
```
enable_mtrr_cleanup mtrr_chunk_size=256M mtrr_gran_size=256M
```

And after reboot /proc/mtrr looks like:
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg04: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg05: base=0x400000000 (16384MB), size=16384MB, count=1: write-back
reg06: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining

```

And Flash fullscreen video goes smoothly! So the problem is solved.

Yes, that's Linux way - spent a lot of time to solve issues that Windows users do not have at all :)

BTW, there is a bad effect also: now system detects only 3355 MB...

---

### Post by FreezWay on 2009-08-23
i followed the steps to update the kernal, but it still says i have 2.6.28.15... im fairly new, but not brand new here. It still works the same, but not better.... any1 know why i dont have the most recent kernal? 

I used the Optimal instructions

---

### Post by rgsteele on 2009-08-23
> **relgames said:**
> BTW, there is a bad effect also: now system detects only 3355 MB...

This sounds like perhaps you have inadvertently installed the 32-bit kernel rather than the 64-bit kernel.

---

### Post by rgsteele on 2009-08-23
> **FreezWay said:**
> i followed the steps to update the kernal, but it still says i have 2.6.28.15... im fairly new, but not brand new here. It still works the same, but not better.... any1 know why i dont have the most recent kernal?

When you say "it" says you have 2.6.28.15, what do you mean by "it" exactly? What is the output of the ```
uname -a
``` command? Did you get any errors when you performed the steps in part C? What is the output of ```
dpkg -s linux-image-2.6.30-02063003-generic | grep ^Status
``` ? If it says "Status: install ok installed", what is the output of

```
cat /boot/grub/menu.lst | grep "^title\|^default"
```

?

---

### Post by triplesick on 2009-08-23
I installed the "Safe" method and it wasn't safe.  Ubuntu is now EXTREMELY laggy and sluggish; it's effectively unusable.  It took me ~five minutes to navigate to this page, and then I just gave up and booted into Windows.  I'm using the Intel 965 chipset.  Does anyone have any idea what this is related to?  I searched the thread and found nothing.  

(This isn't what "tiling" would do to an 800 series, is it?  I did everything exactly as it said for the "Safe" method and enabled tiling.)

---

### Post by psyke83 on 2009-08-23
> **triplesick said:**
> I installed the "Safe" method and it wasn't safe.  Ubuntu is now EXTREMELY laggy and sluggish; it's effectively unusable.  It took me ~five minutes to navigate to this page, and then I just gave up and booted into Windows.  I'm using the Intel 965 chipset.  Does anyone have any idea what this is related to?  I searched the thread and found nothing.  

(This isn't what "tiling" would do to an 800 series, is it?  I did everything exactly as it said for the "Safe" method and enabled tiling.)

Your chipset may still have performance regressions with UXA, or may required the newer kernel modules from the 2.6.30 kernel onwards to perform properly (which is equivalent to the Optimal configuration).

Make sure you read the guide properly - there are instructions to revert changes.

---

### Post by FreezWay on 2009-08-23
it says it is not installed...

2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

and

Package `linux-image-2.6.30-02063003-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by psyke83 on 2009-08-23
> **FreezWay said:**
> it says it is not installed...

2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

and

Package `linux-image-2.6.30-02063003-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

You didn't follow the guide properly, then. Are you aware that for the lines which are prefixed with "$", that symbol only signifies that commands are to be entered in the terminal? In other words, paste the lines without the dollar symbol prefixed.

---

### Post by FreezWay on 2009-08-24
hmm i did it and did not paste the $, i'll try again....

---

### Post by psyke83 on 2009-08-24
> **FreezWay said:**
> hmm i did it and did not paste the $, i'll try again....

Ok, but you may want to check the resulting output for errors (or paste it here if you're not sure).

---

### Post by triplesick on 2009-08-24
thanks psyke for being such a diligent contributer, even though it didn't work for my system.

---

### Post by bkb on 2009-08-24
Hi,
My graphics card is Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10).  I did Part A & B (Safe/Optimal).  There has been some improvement in performance.  I had a follow up question.  Another suggestion I came across was to download xorg-edit - I got the latest version, v07.08.11.  When I open the file xorg.conf in /etc/x11, under the Device tab most of the fields are blank:

Device: Configured Video Device
Driver:
BusID:
Video Ram:
Screen Number:
Option: 
AccelMethod = uxa
EXAOptimizeMigration = true
Migration Heuristic = greedy
Tiling = false

I recognize the options - I remember inserting them in Part A step 1.  However, when I try to change the tab away from Device I get the error box: Device drive must not be empty!

Is this the way it should be or is my configuration missing something?

---

### Post by inobe on 2009-08-24
using the basic setup/ safe i was able to get decent rendering :)

```
112 frames in 5.4 seconds = 20.604 FPS
347 frames in 5.0 seconds = 69.162 FPS
407 frames in 5.0 seconds = 81.123 FPS
426 frames in 5.0 seconds = 85.119 FPS
400 frames in 5.0 seconds = 79.961 FPS
402 frames in 5.0 seconds = 80.223 FPS
416 frames in 5.0 seconds = 83.031 FPS
404 frames in 5.0 seconds = 80.662 FPS

```

i have extra affects enabled.

```
ss@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

it's a dell inspiron 1200 using the onboard memory which is less than 256mb minus what's allocated for vram.

---

### Post by psyke83 on 2009-08-24
> **inobe said:**
> using the basic setup/ safe i was able to get decent rendering :)

```
112 frames in 5.4 seconds = 20.604 FPS
347 frames in 5.0 seconds = 69.162 FPS
407 frames in 5.0 seconds = 81.123 FPS
426 frames in 5.0 seconds = 85.119 FPS
400 frames in 5.0 seconds = 79.961 FPS
402 frames in 5.0 seconds = 80.223 FPS
416 frames in 5.0 seconds = 83.031 FPS
404 frames in 5.0 seconds = 80.662 FPS

```

i have extra affects enabled.

```
ss@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

it's a dell inspiron 1200 using the onboard memory which is less than 256mb minus what's allocated for vram.

Glad to hear it's working, but don't forget to read the guide in its entirety. Your glxgears performance is meaningless - and in your case, it seems to be throttled against your monitor's vertical refresh rate (80Hz).

---

### Post by inobe on 2009-08-24
i will certainly read threw it several times, as i said' i haven't went bleeding edge, i just decided to fiddle with it this evening :)


i like what everyone is trying to do here, great job

---

### Post by FreezWay on 2009-08-25
i have tried the commands for optimal twice now, but my kernal is still 2.6.28.blah blah blah. Any1 help me out here?

---

### Post by braver on 2009-08-25
I've tried 8.10 EasyPeasy on my Eee 900 (Celeron), and netbook-laucnher was flying.  Then installed 9.04 UNR and it was slow as heck.  Tried Optimal from this Guide, didn't really improve much -- anmations are still sluggish.  UXA did speed a bit, but nowhere near the level of 8.10.

The only thing I didn't try from the above is bleeding-edge, but given my experiences of using cutting-edge nvidia drivers, nouveau, in the past, this is not good at all.

I'm very tempted to go back to EasyPeasy and 8.10.  This looks like a major flop of Jaunty, BTW.

Ran the update, it brought up kernel to 2.8.28-15, still the same.
I also tried patched apw kernel from April 21, from the relevant bug, and results are the same as 2.6.28-15 and 2.6.30.

So is there anything else I could try for netbook-launcher acceleration -- some GL tweaks, anything?

---

### Post by triplesick on 2009-08-25
psyke--

I initially had trouble with the "Safe" procedure.  It made my 965 system slow to the point of being unusable.  I've narrowed down the problem to the modifications to the xorg config file: it was either the accelmethod line or the exaoptimizemigration line that was causing the problem.  I then got tired of rebooting and got too lazy to narrow it down further.  Even without including these first two lines, though, my problems are solved: I can watch fulllscreen flash videos with no stuttering.

Thanks a lot for the help.  You might want to subdivide the original post further to clarify that just installing the driver might be sufficient for some users, and if it's not, they can go on to mess with the xorg file, the kernel, etc.

A further question...i use a restricted driver for my internet connection, so I don't want to use the new kernel.  would the 2.6.29 kernel work with restricted drivers?  is there a way to get them working with 2.6.30?

---

### Post by braver on 2009-08-25
triplesick -- thanks to your report, I've commented out UXA and got speed back in netbook-launcher!  Yay!  Now it's on par with 8.10.

---

### Post by triplesick on 2009-08-25
yayay!  good to hear!  this marks my first post that was in any way useful.

---

### Post by checoimg on 2009-08-25
This is my output:


[COLOR=DarkGreen]$ grep -i UXA /var/log/Xorg.0.log[/COLOR]
(WW) intel(0): DRI2 requires UXA

[COLOR=DarkGreen]$ cat /proc/mtrr[/COLOR]
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg03: base=0x0bc000000 ( 3008MB), size=   64MB, count=1: uncachable
reg04: base=0x0bbe00000 ( 3006MB), size=    2MB, count=1: uncachable
evo@evo-laptop:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 2294
    Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=4M]

---

### Post by rgsteele on 2009-08-26
> **FreezWay said:**
> i have tried the commands for optimal twice now, but my kernal is still 2.6.28.blah blah blah. Any1 help me out here?

Can you please paste the output of the commands from part C into your reply? We're happy to help but without more information there isn't much we can do!

---

### Post by Shii on 2009-08-26
> **braver said:**
> triplesick -- thanks to your report, I've commented out UXA and got speed back in netbook-launcher!  Yay!  Now it's on par with 8.10.

Haha, I skipped right to the last page and found exactly what I needed to fix UNR. Now it's speedier than ever before! :)

---

### Post by triplesick on 2009-08-26
hurray hurrah!  i will take credit for that.

---

### Post by vicaya on 2009-08-27
My observation with an Acer 5730-6918 (with Intel 4500M HD), performance seems fine with 64-bit jaunty with no modification (glxgears at 1100+fps). But graphics is not stable with a lot of tearing; virtual desktop doesn't seem to work with dual monitor setup (with a 24" Samsung at 1920x1200.)

Since 64-bit Jaunty is not stable enough for me, I tried 32-bit Jaunty, the performance is still fine (glxgears at 1000+fps) with no mods. However the graphics performance plummeted to unusable state (glxgears at 120+ fps) when I switched to a PAE kernel (from jaunty server) when I want to take advantage of 4GB of RAM (normal 32-bit kernel only sees 3GB.)

The fix is to apply the fixmtrr.sh and graphics is usable again (glxgears at 700 fps) any other tweaks to the xorg.conf doesn't make any difference to me, so I just leave it in its default state.

Now rotating two deskcubes (one on the 1680x945 internal LCD and one on the 1920x1200 external LCD) in compiz is not smooth as butter but it works (unlike 64-bit jaunty, which rotates really responsively and smooth but with tearing/garbled display all over the place.)

---

### Post by frausch on 2009-08-28
Yhanks for the howto. It improved the compiz performance on my Lifebook S7010 (82852/855GM) a lot. Unfortunately, I suffer from errors in the displaying of windows, especially when desktop effects are rendered. It looks as if the content of different windows get confused, so that in some areas of one window, the content of another window (or the background) is displayed for a short time. I have the impression, that it has something to do with the mtrr script, because it starts after executing this script.

cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg02: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg03: base=0x0d8000000 ( 3456MB), size=  128MB, count=1: write-combining

The last line was added by the script.

lspci -v
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Fujitsu Limited. Device 126d
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 2450 [size=8]
        Capabilities: <access denied>
        Kernel modules: intelfb

Is this a bug, that I have to sit out, or is there a possibility to cirecumvent this. 

Cheers

Felix

PS: I followed your instructions up to stable/optimal

---

### Post by frausch on 2009-08-28
Sorry for the noise. I yust noticed, that I stll had an additional device section in my xorg. Now it works!

Sorry! There is still one hair in the soup: The video output via the xv driver (xine -V xv) does not work. I see a blue rectangle where the video should be. I think it is the color, that should be replaced by the video, when xv is in overlay mode.

Cheers

Felix

---

### Post by aboutblank on 2009-08-28
Thanks for this guide.

I have a T61 with X3100 / 965 graphics and, like others, I needed to comment the 'Option "AccelMethod" "uxa"' in xorg.conf to get usable graphics. With that option enabled, graphics were unbearably slow with compiz enabled. Without compiz, graphics were reasonably fast. Commenting out that line when otherwise using the "safe" method yields very usable graphics for me, including with compiz.

---

### Post by Offoffoff on 2009-08-28
I have installed Bleeding Edge 2.8.0 driver. And everything is fine - DRI2, xv, DVD acceleration, blender, games, except WarZone2100 (now it does not start).
I have:
ivan@awesome2000:~$ uname -a
Linux awesome2000 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:45:40 UTC 2009 i686 GNU/Linux
ivan@awesome2000:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
Thank you, Intel Driver Developers! I hope in Karmic will be xorg-xserver-video-intel-2.8.0.

---

### Post by fcsabihu on 2009-08-29
Hello

Thanks for the guide.

I tried SAFE and OPTIMAL ways, both cause the system to halt after rebooting. Dark screen after the UBUNTU logo and nothing else. I can restore using xfix 'try to auto repair graphics problems' in the Recovery Menu but this reverts the xorg.conf file to the original.

Does this mean that my graphics chipset (Intel 82845G/GL) cannot be well used under Ubuntu? Now display is VERY slow.

Any ideas?

---

### Post by psyke83 on 2009-08-29
> **frausch said:**
> Sorry for the noise. I yust noticed, that I stll had an additional device section in my xorg. Now it works!

Sorry! There is still one hair in the soup: The video output via the xv driver (xine -V xv) does not work. I see a blue rectangle where the video should be. I think it is the color, that should be replaced by the video, when xv is in overlay mode.

Cheers

Felix

Are you using compiz? Overlay video doesn't work when any compositing manager is running, and your graphics chipset may not support textured video (which is the only way to get XV and compositing to cooperate).

Check the output of "xvinfo" to see what's available.

---

### Post by psyke83 on 2009-08-29
> **fcsabihu said:**
> Hello

Thanks for the guide.

I tried SAFE and OPTIMAL ways, both cause the system to halt after rebooting. Dark screen after the UBUNTU logo and nothing else. I can restore using xfix 'try to auto repair graphics problems' in the Recovery Menu but this reverts the xorg.conf file to the original.

Does this mean that my graphics chipset (Intel 82845G/GL) cannot be well used under Ubuntu? Now display is VERY slow.

Any ideas?

You have two options:
1. Use the Optimal, Safe or default Jaunty configuration with EXA and greedy acceleration. In other words,

Ensure your xorg.conf matches the following (the bold items are the important bits):
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"**exa**"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"**greedy**"
	Option		"Tiling"			"true" # i8xx users: see note in guide
EndSection
```

2. Try the Bleeding-Edge configuration *if and only if* you have fully read the guide, know how to revert changes and can deal with temporary X breakage.

---

### Post by frausch on 2009-08-29
> **psyke83 said:**
> Are you using compiz? Overlay video doesn't work when any compositing manager is running, and your graphics chipset may not support textured video (which is the only way to get XV and compositing to cooperate).

Check the output of "xvinfo" to see what's available.

Actually, xv works now. I played a bit around with xorg.conf, and tying (without success) to switch to textured video. I think it was after a reboot, that it suddenly worked with overlay video. The video is certainly not treated correctly in desktop effects, but one can watch it.

I found another issue: The google earth window is only filled in a small area in the upper left corner  (see attachement). 

In armagetron, the menus are shifted upwards so that they are only partially visible.

Cheers

Felix

---

### Post by FreezWay on 2009-08-30
here is all the text in the terminal.

```


theawwsomeness@theawwsomenesss-computer:~$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
--2009-08-29 21:39:05--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
Resolving kernel.ubuntu.com... 91.189.94.216
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

--2009-08-29 21:39:06--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

--2009-08-29 21:39:06--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

theawwsomeness@theawwsomenesss-computer:~$ sudo dpkg -i linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
[sudo] password for theawwsomeness: 
(Reading database ... 212270 files and directories currently installed.)
Preparing to replace linux-headers-2.6.30-02063003-generic 2.6.30-02063003 (using linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb) ...
Unpacking replacement linux-headers-2.6.30-02063003-generic ...
Preparing to replace linux-headers-2.6.30-02063003 2.6.30-02063003 (using linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb) ...
Unpacking replacement linux-headers-2.6.30-02063003 ...
Preparing to replace linux-image-2.6.30-02063003-generic 2.6.30-02063003 (using linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-02063003-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-02063003-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.30-02063003 (2.6.30-02063003) ...
Setting up linux-image-2.6.30-02063003-generic (2.6.30-02063003) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-02063003-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.30-02063003 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.30-02063003 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-02063003-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-headers-2.6.30-02063003-generic (2.6.30-02063003) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

```

---

### Post by rionline on 2009-08-30
> **Offoffoff said:**
> I have installed Bleeding Edge 2.8.0 driver. And everything is fine - DRI2, xv, DVD acceleration, blender, games, except WarZone2100 (now it does not start).
I have:
ivan@awesome2000:~$ uname -a
Linux awesome2000 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:45:40 UTC 2009 i686 GNU/Linux
ivan@awesome2000:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
Thank you, Intel Driver Developers! I hope in Karmic will be xorg-xserver-video-intel-2.8.0.

he guys,
i wish that it could be so simple. please try celestia with this driver. i have a build-in X3100 (gma965) and celestia shows me only its menu...nothing else. cairo-dock isn't running in opengl either... :(

Linux rionline-laptop 2.6.31-020631rc7-generic #020631rc7 SMP Sat Aug 22 09:51:01 UTC 2009 i686 GNU/Linux
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
newest driver from [https://edge.launchpad.net/~xorg-edgers/+archive/ppa]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa")

---

### Post by rgsteele on 2009-08-30
> **FreezWay said:**
> here is all the text in the terminal.

```


theawwsomeness@theawwsomenesss-computer:~$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
--2009-08-29 21:39:05--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
Resolving kernel.ubuntu.com... 91.189.94.216
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

--2009-08-29 21:39:06--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

--2009-08-29 21:39:06--  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
Connecting to kernel.ubuntu.com|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

theawwsomeness@theawwsomenesss-computer:~$ sudo dpkg -i linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
[sudo] password for theawwsomeness: 
(Reading database ... 212270 files and directories currently installed.)
Preparing to replace linux-headers-2.6.30-02063003-generic 2.6.30-02063003 (using linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb) ...
Unpacking replacement linux-headers-2.6.30-02063003-generic ...
Preparing to replace linux-headers-2.6.30-02063003 2.6.30-02063003 (using linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb) ...
Unpacking replacement linux-headers-2.6.30-02063003 ...
Preparing to replace linux-image-2.6.30-02063003-generic 2.6.30-02063003 (using linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-02063003-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-02063003-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.30-02063003 (2.6.30-02063003) ...
Setting up linux-image-2.6.30-02063003-generic (2.6.30-02063003) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-02063003-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.30-02063003 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.30-02063003 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-02063003-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-headers-2.6.30-02063003-generic (2.6.30-02063003) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

```

Looks like the kernel is installing fine. Can you please post the contents of /boot/grub/menu.lst? I suspect Grub is configured to boot the wrong kernel.

---

### Post by FreezWay on 2009-08-30
issue there.
i tried out ubuntu karmic and haven't figured out how to uninstall it. i am therefore using grub2 when i boot.

---

### Post by sancho panza on 2009-09-01
Thanks for the guide psyke!

I'm having an issue with jaunty that I am not able to put my finger on 
and I'm trying to eliminate various possibilities, one after the other.

The ISSUE: After running jaunty for about a day or so (with a few suspends in between), the system starts using swap heavily and slows down to a crawl. At this point the physical ram (2GB) is under 25% use as per system monitor, but the "free" command shows that its fully used up.

CAUSES: Thru testing, I'm almost sure its not any specific program that I run. Its something in the background. 
I have followed your guide verbatim and have tried both the Safe and Optimal configs, but both present the same problem. I havent yet tried to see if a fresh install has the same issue. Are there any changes I could make to your Howto so as to fix my problem? Should I try reverting to original settings?

PS: are these [instructions]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T61#Intel_Graphics") consistent with your guide? Should I try it out? 

Thanks,

---

### Post by frausch on 2009-09-04
Hi sancho panza,

could you run "top" in a terminal and then press M (shift-m). This should show you the processes sorted by memory usage. Please post something like the lines for the top 10 processes.

What I see is, that Xorg reserves about a 1Gb of virtual memory after some time:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6720 root      20   0 1106m  58m  22m R  4.3  5.9  19:14.02 Xorg


I am not sure if this is a bug.

Cheers

Felix

---

### Post by Ekeluo on 2009-09-04
I used this guide (bleeding edge/sect C) when installing jaunty on my laptop and it worked fine. Games (TORCS, yo frankie, neverputt), kde 4.2.4 effects were all ok. Then I upgraded to 4.3 and it was still fine. Meanwhile I now used The 2.6.30-10 kernel from Xorg-edgers repos and they worked fine, until I upgraded to kde 4.3.1.(or there abouts, batch of updated included a few things from xorg-edgers repos)

To the point, I now witness graphics corruption (mostly the lower panel flickering whenever a new window is opening), but everything else is fine. No slow downs, games work (with some flickering). I tried resetting my xorg.conf and after running dpkg-reconfigure xserver-xorg, nothing changed (even though this deleted all the line I added from this post) I enabled the fbdev module and it seems to have improved, but there's still some intrusive flickering especially on the panels and during redraws.

Any help is appreciated in advance.

---

### Post by Richard9795 on 2009-09-04
There are some complaints about the netbook-launcher, and compiz not playing nicely with each other. well, with the most recent xserver-xorg-video-intel package (sudo apt-get dist-upgrade, using the ubuntu X repo mentioned with the bleeding edge section of this preformance guide), and the Kernel 2.6.31 rc7, makes the netbook-launcher usable under compiz.

Link to the kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc8/)

It works fine on my Eee pc 900

---

### Post by verv87 on 2009-09-05
Should I use the 30.3 kernel posted in the guide or should I use a newer one?

This is on a msi wind u100 (gma 950). Tried the optimal modifications but so far no results. Video is still choppy, specially flash.

Should I go with the bleeding edge x or another kernel?

---

### Post by treris on 2009-09-05
> **verv87 said:**
> Should I use the 30.3 kernel posted in the guide or should I use a newer one?

This is on a msi wind u100 (gma 950). Tried the optimal modifications but so far no results. Video is still choppy, specially flash.

Should I go with the bleeding edge x or another kernel?

From personal experience I'd say that you might as well use the 30.5 kernel. For me the optimal setup worked like a charm, but then again I'm using a x3100 graphics chip on kubuntu without desktop effects.

---

### Post by verv87 on 2009-09-05
After applying all the changes in optimal (30.3 kernel, mttr script, xorg.conf changes and the latest stable x drivers):
```
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61110 (PORT_HOTPLUG_EN) changed from 0x00000000 to 0x00000020
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000202 to 0x80000202
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): ESR is 0x00000001, instruction error
(WW) intel(0): Existing errors found in hardware state.
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used

```
Output from fixmttr script:
```
Extracing base address and memory size from lspci -v
c0000000
10000000

Supplying corrected MTRR ranges to /proc/mtrr
doing nothing, MTRR range already set up
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg02: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining
```
This is on a msi wind u100 with a gma 950. I can't ppracer -a, although I can play the actual game. Enabling UXA made everything (flash, video, ppracer) significantly slower. Help?

---

### Post by F.G. on 2009-09-06
hi, sorry if this is a repeat.  I had trouble with watching stuff full screen  off the internet.  fixmtrr.sh in etc/init.d with the correct permissions seems to have fixed it, thanks.  I'm currently using workarounds for my wireless (rtl8187b) and graphics (mobile GM965/GL960). does anyone have permanent fixes? is it worth the hassle or does anyone know if this will be fixed in the next release?  I'm new to all this, so thanks for any replies.

also, for some reason windows wont install functionally on my hard disk (my laptop used to have it, but I think I have a faulty hard disk) yet, linux (mint 5,6,7, ubuntu, kubuntu, suse, bt3, bt4, knoppix etc) seems to have no problem, anyone know why this might be? (i'd like to have a dual boot system with windos, currently I have to run it as a virtual machine). thanks.

---

### Post by reesje on 2009-09-08
Hi,
> **verv87 said:**
> This is on a msi wind u100 (gma 950). Tried the optimal modifications but so far no results. Video is still choppy, specially flash.
If flash is choppy I think you should find your problems elsewhere. I've got a AA1 110L, which uses the same CPU as yours. The problem is the ondemand speed stepping.

Try to add the CPU  frequency scaling icon to your panel and check if the CPU stays at 800MHz. It does so on both my AA1 and my wifes.

You can the manually select the CPU frequency by leftclicking the icon.

I find it amazing that this problem seems to get very little attention. There are a few posting on this, try to search "choppy flash" and you will find a few.

BR,
René

---

### Post by reesje on 2009-09-08
> **reesje said:**
> If flash is choppy I think you should find your problems elsewhere. I've got a AA1 110L, which uses the same CPU as yours. The problem is the ondemand speed stepping.
Check this link:
[http://ubuntuforums.org/showthread.php?t=1111090&highlight=up_threshold]("http://ubuntuforums.org/showthread.php?t=1111090&highlight=up_threshold")

---

### Post by reesje on 2009-09-08
> **reesje said:**
> If flash is choppy I think you should find your problems elsewhere. I've got a AA1 110L, which uses the same CPU as yours. The problem is the ondemand speed stepping.
Check this link:
[http://ubuntuforums.org/showthread.php?t=1111090&highlight=up_threshold]("http://ubuntuforums.org/showthread.php?t=1111090&highlight=up_threshold")

---

### Post by markus.readus on 2009-09-08
Hi,

Thanks very much for the guide, its comprehensive, and easy to follow (which is much more appreciated than some of the other resources I have found!). I'm having a problem with one of the steps on the guide though, section B part 2, the terminal command

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9


does not appear to work, I get a time out, as follows:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
[sudo] password for mark: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?

Thanks,

Mark

---

### Post by FireLink on 2009-09-08
> **markus.readus said:**
> Hi,

Thanks very much for the guide, its comprehensive, and easy to follow (which is much more appreciated than some of the other resources I have found!). I'm having a problem with one of the steps on the guide though, section B part 2, the terminal command

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9


does not appear to work, I get a time out, as follows:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
[sudo] password for mark: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?

Thanks,

Mark

Same problem here!

---

### Post by Dangger on 2009-09-08
> **11010110 said:**
> Hi again,

I managed to fix (or workaround) most of the graphics glitches thusfar but one thing is still puzzling me... since doing this my mounse funtionality has changed. when moved slow it is more sensitive than when it is moved fast. basically when i drag my finger across the mousepad fast it only moves an inch or so but when i drag it slow it darts to the end of the screen easily. Any ideas on how to fix this?

Thanks a lot in advance.


I'm having the same problem here. Video definitely works better with safe optimization but now my mousepad is behaving weird. Any solutions to this issue?

---

### Post by BassKozz on 2009-09-08
I recently upgraded from Intrepid to Jaunty on my Dell e1505, and I now can no longer get into my boot screen, all I get is some pixels that run across the screen.  

I've uploaded a video to better describe (and help diagnose) the problem here: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)
Or jump right to the part with the problem: [1minute and 5seconds in](http://www.youtube.com/watch?v=7vLEi68wrQI#t=1m5s)

I've already tried all the suggestions in the [Release Notes](http://www.ubuntu.com/getubuntu/releasenotes/904) including [Reverting the Intel Drivers back to 2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) as well as the **Optimal** configuration found in this thread. Yet nothing seems to work.  Where can I go from here?
See Also: [http://ubuntuforums.org/showthread.php?p=7917708](http://ubuntuforums.org/showthread.php?p=7917708)

Please Help [-o<,
Thanks,
-BassKozz

---

### Post by rgsteele on 2009-09-08
> **markus.readus said:**
> Hi,

Thanks very much for the guide, its comprehensive, and easy to follow (which is much more appreciated than some of the other resources I have found!). I'm having a problem with one of the steps on the guide though, section B part 2, the terminal command

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9


does not appear to work, I get a time out, as follows:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
[sudo] password for mark: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?

Thanks,

Mark

It's possible that the server was down. Perhaps try the command again.

The other possibility is that you are in a corporate environment where outgoing connections on ports other than the standard http/https ports are blocked for security reasons. GPG needs to be able to connect to port 11371 on the keyserver.

If this is the case, possible solutions are: have your IT department open this port for the computer in question (good luck with that), plug the computer in somewhere with unrestricted Internet access, or download the key on a second computer with unrestricted Internet access and copy it to the first computer.

Or, let me retrieve the key from [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9) for you:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXVCiwEEANKBDbiSLOJOouub/S97iDifYCVW1b0KONg7XkFYiFos+bMBzzZyGGo90k1h
hCxcseLvqCKPL7dG0RzPRKMo7mvM68yyqi2ljw0ZYC9cVf0YzgKRTohVhihelpwZ+sBRGNYk
OCu+u0Dr+EdVI3u5RNOxAELrbd4vYaS+2cCOfzmLABEBAAG0GkxhdW5jaHBhZCBQUEEgZm9y
IFVidW50dS1YiLYEEwECACAFAkl1QosCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRA7
IquXrxzfqY4HBACIQEFhl59ZkuIhTD3pmCQgfkhpcg0RVdB6Xwhu3QDJvmlWmrs+cofNMzyA
7SwdjD9ARvhGbqHwub+T7oGiHlmFyodGypUZ4i/fdHsZYpsf34MwgYxhyNyOPY/jNImUE/yw
kSI+kV5esWURH4j0jYfkaergFqCpDnsSkxuIvdjH2Q==
=bkAa
-----END PGP PUBLIC KEY BLOCK-----

```

Copy and paste the PGP key block into a text editor and save it somewhere. Launch Synaptic, go to Settings>Repositories>Authentication>Import Key File... and import the file you just saved.

Be aware that if you were to import a key file created by a malicious individual, AND that individual also had the means to redirect your computer to download updates from his repository (i.e. through DNS cache poisoning), your system could be compromised. So, do you trust me? :wink:

---

### Post by sancho panza on 2009-09-08
> **sancho panza said:**
> Thanks for the guide psyke!

I'm having an issue with jaunty that I am not able to put my finger on 
and I'm trying to eliminate various possibilities, one after the other.

The ISSUE: After running jaunty for about a day or so (with a few suspends in between), the system starts using swap heavily and slows down to a crawl. At this point the physical ram (2GB) is under 25% use as per system monitor, but the "free" command shows that its fully used up.

CAUSES: Thru testing, I'm almost sure its not any specific program that I run. Its something in the background. 
I have followed your guide verbatim and have tried both the Safe and Optimal configs, but both present the same problem. I havent yet tried to see if a fresh install has the same issue. Are there any changes I could make to your Howto so as to fix my problem? Should I try reverting to original settings?

PS: are these [instructions]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T61#Intel_Graphics") consistent with your guide? Should I try it out? 

Thanks,

Ok so my previous post is more aptly [described here]("http://dannipenguin.livejournal.com/275982.html?thread=1375246#t1375246").
Does anybody have a fix for this yet?

---

### Post by Verve87 on 2009-09-09
> **reesje said:**
> Hi,

If flash is choppy I think you should find your problems elsewhere. I've got a AA1 110L, which uses the same CPU as yours. The problem is the ondemand speed stepping.

Try to add the CPU  frequency scaling icon to your panel and check if the CPU stays at 800MHz. It does so on both my AA1 and my wifes.

You can the manually select the CPU frequency by leftclicking the icon.

I find it amazing that this problem seems to get very little attention. There are a few posting on this, try to search "choppy flash" and you will find a few.

BR,
René
I don't use gnome and I set the governor to performance before even installing X. Thanks anyway, though.

---

### Post by bobterri on 2009-09-09
Looks like the server is still down for keyserver.ubuntu.com.

I can't download the key file for 8844C542.

---

### Post by mbrion on 2009-09-09
> **markus.readus said:**
> Hi,

Thanks very much for the guide, its comprehensive, and easy to follow (which is much more appreciated than some of the other resources I have found!). I'm having a problem with one of the steps on the guide though, section B part 2, the terminal command

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9


does not appear to work, I get a time out, as follows:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
[sudo] password for mark: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?

Thanks,

Mark

Try this comand instead:
```
gpg --keyserver subkeys.pgp.net --recv AF1CDFA9 && gpg --export --armor AF1CDFA9  | sudo apt-key add -
```

---

### Post by glaze on 2009-09-10
I installed 2.6.31 today and 3D is a bit faster than in .30 on my GMA 950.

---

### Post by BassKozz on 2009-09-10
> **BassKozz said:**
> I recently upgraded from Intrepid to Jaunty on my Dell e1505, and I now can no longer get into my boot screen, all I get is some pixels that run across the screen.  

I've uploaded a video to better describe (and help diagnose) the problem here: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)
Or jump right to the part with the problem: [1minute and 5seconds in](http://www.youtube.com/watch?v=7vLEi68wrQI#t=1m5s)

I've already tried all the suggestions in the [Release Notes](http://www.ubuntu.com/getubuntu/releasenotes/904) including [Reverting the Intel Drivers back to 2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) as well as the **Optimal** configuration found in this thread. Yet nothing seems to work.  Where can I go from here?
See Also: [http://ubuntuforums.org/showthread.php?p=7917708](http://ubuntuforums.org/showthread.php?p=7917708)

Please Help [-o<,
Thanks,
-BassKozz
:Bump:
Does anyone know what could be causing this problem: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)
Or jump right to the part with the problem: [1minute and 5seconds in](http://www.youtube.com/watch?v=7vLEi68wrQI#t=1m5s)

---

### Post by OBpaddleoutSD on 2009-09-10
Running 9.04 on acer aspire 5610 intel 945 integrated graphics... everything seems good desktop visual effects like wobbly windows and cube work great.
 
However!
 
I was messing with chess and it won't load says i have no:
Python OpenGL Support
Python GTKGLExt Support
 
Wondering if this will conflict with other Apps (playonlinux, WINE) with gaming etc...
 
i tried the the process from post 1 to no avail...
 
Maybe i'm doin it wrong but i dont think so.
 
any takers?

---

### Post by rgsteele on 2009-09-10
> **BassKozz said:**
> :Bump:
Does anyone know what could be causing this problem: [http://www.youtube.com/watch?v=7vLEi68wrQI](http://www.youtube.com/watch?v=7vLEi68wrQI)
Or jump right to the part with the problem: [1minute and 5seconds in](http://www.youtube.com/watch?v=7vLEi68wrQI#t=1m5s)

Your issue isn't really relevant to this thread. The steps in the HOWTO are only meant for resolving performance issues, not problems at boot time. I'll see if I can help out in your other thread, though.

---

### Post by treris on 2009-09-11
Is it possible to upgrade to kernel 2.6.31 final and still use the optimal configuration without breaking anything, or should I only use the bleeding-edge configuration with 2.6.31?

Just fyi I'm currently running the optimal configuration with the 2.6.30.5 kernel.

---

### Post by hexag on 2009-09-11
hi guys,

first, thanks so much for getting my darling little laptop all sparkly again, to the point it actually offends people with total un-necessary silliness. i went for the optimum/bleeding edge, but there is one problem (isn't there always?!)...

wine has stopped displaying fonts of any sort, whether in winecfg or applications, i've been through the wine support pages & done all they've suggested; reinstall, download fonts through a variety of avenues, etc. the fonts are actually in the fonts directory anyway. i know this isn't a wine support forum, but this has been a cause of the above patching which i'm guessing you guys might have an idea why.

spec info, jaunty, fully updated
intel 945graphics
1gb ram
kernal described above
installation of bleeding-edge went without hiccup
everything else running smooth

cheers,

nick,

---

### Post by lwhitmore on 2009-09-11
Hi 

I've been using the Intel driver from the edgers ppa + the latest kernel for a while now, and it's been working well.  Nice fast graphics and dual screen capability too.  Every so often the drivers are improved upon.. occasionally, the graphics are a bit worse for a revision while the bugs are worked upon - but generally it all works well.

At the moment though, I'm unable to use dual sreen (the display properties application shows *no screens at all*!)

I'm assuming that this is due to the current version of the intel driver in the repository.

Can anyone confirm whether the same is true for them?

---

### Post by ENigma885 on 2009-09-11
_@lwhitmore and hexag_

I confirm the same behaviour here also with xorg-edgers PPA. And no fonts in Wine as well.

---

### Post by lwhitmore on 2009-09-11
@ENigma885

Thanks for the confirmation - I guess we just have to hold tight.. pretty annoying though ;) 

It would be nice if we could roll back a revision and stick with it in cases like this, but afaik it's not possible.

Cheers

Luke

---

### Post by uHoptu on 2009-09-11
will this help to enable extra effects in ubuntu 9.04 on a Dell mini 10 using the Intel GMA500/945 chipset?

---

### Post by Alex_W on 2009-09-11
xorg-edgers PPA drivers with 2.6.30.5 kernel from mainline on a laptop with Intel 915GM graphics: the latest xserver-xorg-video-intel driver (from Sep 7th) actually caused all fonts to disappear on my laptop.

fixed by searching in var/apt/cache for corresponding packages 1 version down and dpkg -i them -- it worked.

---

### Post by ManDay on 2009-09-11
Hello, I've followed the recent SAFE instructions in order to fix my gnome-terminal (gterm) and browser (firefox) which are stuttering/laggy on scrolling (manpages/pages with pictures) on my EEE PC 1000h

the fixmttr.sh script runs properly, the apt-get did the update, yet I still have the same issues.

Can anyone help? Maybe it didnt work properly - how do I find out?

> (WW) intel(0): drmDropMaster failed: Unknown error 4294967295
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used


---

### Post by Verve87 on 2009-09-11
> **ManDay said:**
> ```
(WW) intel(0): drmDropMaster failed: Unknown error 4294967295
[B](WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used[/B]
```
The bolded part is expected if you enabled UXA. They're not being used by X because you're using UXA, not EXA.

This has already been pointed out. I know it's a big thread but you could still search.

---

### Post by uniontroublemaker on 2009-09-11
> **Alex_W said:**
> xorg-edgers PPA drivers with 2.6.30.5 kernel from mainline on a laptop with Intel 915GM graphics: the latest xserver-xorg-video-intel driver (from Sep 7th) actually caused all fonts to disappear on my laptop.

fixed by searching in var/apt/cache for corresponding packages 1 version down and dpkg -i them -- it worked.

I have this same issue too with a laptop, the same integrated graphics, and the latest 2.6.30 kernel --  there are no fonts.  All drop down menus have the icon but no label.

---

### Post by ManDay on 2009-09-12
> **Verve87 said:**
> The bolded part is expected if you enabled UXA. They're not being used by X because you're using UXA, not EXA.

This has already been pointed out. I know it's a big thread but you could still search.

I've tried the "Search thread" function but it's not really helpful, to be honest. Does this mean that I can't use the solution presented in the first post?

---

### Post by sleepitoff on 2009-09-12
Okay, so how do I make  fixmtrr.sh execute at start up in KDE ? 

and yes, I searched the thread, but only found a couple of replies from people saying they created a script and got it to work, but none of them saying what the script is or how to make it work. 

thanks!

---

### Post by kendoori on 2009-09-13
Is the Intel Graphics problem solved in 9.10?

I have followed the "safe" version of this guide, to reasonable benefit; however, something doesn't seem to be quite right about how my Intel GM965/GL960 plays. One would have imagined that this would have been fixed by now.

---

### Post by dc2447 on 2009-09-14
> **markus.readus said:**
> Hi,

Thanks very much for the guide, its comprehensive, and easy to follow (which is much more appreciated than some of the other resources I have found!). I'm having a problem with one of the steps on the guide though, section B part 2, the terminal command

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9


does not appear to work, I get a time out, as follows:

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
[sudo] password for mark: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?

Thanks,

Mark

are you behind a firewall that doesn't allow outbound connections to some ports?

---

### Post by Verve87 on 2009-09-14
> **ManDay said:**
> I've tried the "Search thread" function but it's not really helpful, to be honest. Does this mean that I can't use the solution presented in the first post?
The behavior is expected if you enabled UXA. It's normal, the log is supposed to say that.

The thing is whether or not UXA gave you a performance boost. Can you use ppracer? Compare your results before and after enabling UXA.

---

### Post by quebeck5 on 2009-09-14
> **ENigma885 said:**
> _@lwhitmore and hexag_

I confirm the same behaviour here also with xorg-edgers PPA. And no fonts in Wine as well.

Fonts are now working on my system with the just released intel drivers, 2:2.8.99.901~git20090914.c2abfa8e-0ubuntu0tormod~jaunty
(using the 2.6.30.5 kernel)

Still getting crashes in 3d programs, most notably google earth crashes with this error: /usr/lib/dri/i915_dri.so(vbo_split_copy+0x7d3) [0xa91446b3]


On the positive side, I'm getting ~52 fps in openarena compared to ~40 fps with the last driver version!

---

### Post by uniontroublemaker on 2009-09-15
fonts are now working for me too.

---

### Post by andrewabc on 2009-09-15
> **kendoori said:**
> Is the Intel Graphics problem solved in 9.10?

I have followed the "safe" version of this guide, to reasonable benefit; however, something doesn't seem to be quite right about how my Intel GM965/GL960 plays. One would have imagined that this would have been fixed by now.

This Thursday, download alpha6. Burn it to a CD (cd-rw preferred), and see if it works (maybe put it onto usb stick for max performance). I have g965 x3000 (desktop edition) and intel works fine. It also works fine on jaunty. There have been many improvements. Although some people are still reporting problems, so the best way for you to find out is to test the alphas/betas and report bugs, create/reply to threads in the development board for Karmic 9.10

---

### Post by Skottie88 on 2009-09-16
where is this fixmtrr.sh????

---

### Post by kwaanens on 2009-09-16
> **Skottie88 said:**
> where is this fixmtrr.sh????

The details are in the very first post of this thread.

---

### Post by MedeX on 2009-09-16
My pc lags and today it refused to show me the screen the moment i turned some features of compiz on!!!     my grahic card is intel 82915gl/gv any help??

---

### Post by kwaanens on 2009-09-17
After being on this solution since ~ day 3 of Jaunty I recently tried going back to the most recent linux-image from jaunty-proposed (2.6.28-15.52), and find that this setup works the same as the kernel installed from this thread. Only the kernel is different, all other changes from this thread is still applied. 
Planet penguin racer works, Gnome Do is as responsive as it should, flash works. No freezes or crashes the days I've been using it. Intel 945GM on an MSI s262 notebook.

---

### Post by PatrikG on 2009-09-17
I'm on an Intel D945 mini-ITX motherboard, and the performance on Karmic alpha is just stunning (finally!). Much smoother effects and it also detects my monitor without any problems.

---

### Post by cs_at_colorado on 2009-09-17
Hey-

Just ran the base fix, performance is exceptionally better -- getting 24+ FPS on the Penguin game, just have a few more questions. 

I want to run a virtual machine on an on an extern monitor via my HDMI or VGA port. This works OK -- however, when I crank up the resolution on the external say to 1680x1050 (max for my DELL) I get trailers behind all my windows like it was *'69* and I'd just discovered LSD...

I believe this may be the product of not having allocated enough video mem. I have 4gig base memory (no 64-bit virtual machines on the Core 2 Duo t6500) So I have some extra and I'd like to devote at least 512mb to my video. 

I'm assuming I can just adjust the: *fixmtrr.sh* script to crank up the VRAM settings by changing the hex addresses for my video base address?

Here are some shell prints to give you an idea of where I'm at!

Advice on how to execute these changes without sending myself over the deep-end would be very helpful

Great work!

```

$ cat /proc/mtrr

reg00: base=0x0ffe00000 ( 4094MB), size=    2MB, count=1: write-protect
reg01: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg02: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg03: base=0x0bc000000 ( 3008MB), size=   64MB, count=1: uncachable
reg04: base=0x0ba000000 ( 2976MB), size=   32MB, count=1: uncachable
reg05: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back

```

and looking at the display controller:

```

$ lspci -vvnn

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2299
	Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 5110 [size=8]
	Capabilities: <access denied>
```

---

### Post by Nephiel on 2009-09-18
A bit offtopic: I was having a similar mtrr issue with a GeForce MX400. It's not an Intel card, but this thread helped me a lot with it so I'll share my findings.

I'm using xdm and fluxbox on Ubuntu 9.04.
X ran fine, but I was seeing errors in */var/log/kern.log* about mtrr which led me to investigate:
```
Sep 18 16:07:45 mymachine kernel: [  602.693584] mtrr: no MTRR for d0000000,4000000 found
```
These lines appeared every time I restarted xdm or logged off xdm.

For some reason the MTRRs as set by Xorg for my NVidia GeForce MX400 are wrong.

The card has 64MB of video RAM (for sure, saw it on the VGA BIOS screen).
AGP Aperture size is set to 128 in the BIOS.

*lspci -v* reports the card as having 128MB:
```
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at dfef0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb, rivafb
```

No, I'm not confusing it with the AGP aperture. This is the AGP aperture value:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
	Subsystem: VIA Technologies, Inc. Device 0000
	Flags: bus master, 66MHz, medium devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp
```
If I change AGP aperture in the BIOS, the latter (agpgart) changes size accordingly but the former (video card) is still being reported as having 128MB.

Curiously, *Xorg* knows the card has only 64MB:
```
$ cat /var/log/Xorg.0.log | grep -i videoram
(--) NV(0): VideoRAM: 65536 kBytes
```

*cat /proc/mtrr* reports:
```
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg05: base=0x0e0000000 ( 3584MB), size=  128MB, count=1: write-combining
```

*reg05* is the mtrr for AGP aperture, changes size when I change the value in the BIOS.

What is missing is the mtrr for the VideoRAM, which starts at *d0000000* and has a size of 64MB = *4000000*.

I can do this as root:
```
echo "base=0xd0000000 size=0x4000000 type=write-combining" >| /proc/mtrr
```
then I can log out or restart xdm without the error appearing in *kern.log*, but only one time (*Xorg* restores the mtrr after logout).

If I run the *fixmtrr.sh* script as root, it also works for the current session, but since the memory size reported by *lspci* is wrong, the mtrrs set by the script are also wrong and could overlap or cause other problems.
So I changed the *fixmtrr.sh* script to read the memory size from *Xorg.0.log* instead:
```
#!/bin/sh

echo 'Extracting base address from "lspci -v"...'

# extract the base address for the video memory
address=`lspci -v \
	| grep -A 7 VGA\
	| grep -F " prefetchable"\
	| awk 'BEGIN{OFS="";ORS=""}
	      {print $3
	      i = length($3)
	      while(i<8){
	      		print 0
	       		i++
	       }}'`

echo "Base address: $address"

echo 'Extracting memory size from "/var/log/Xorg.0.log"...'

# we extract the memory size as a decimal number from the Xorg log,
# we then convert it to hexadecimal and fill it up with the correct
# number of zeroes
hsize_kb=`grep -i videoram /var/log/Xorg.0.log | awk '{print $4}' | sed 's/[^0-9]//g'`
hsize=$(( $hsize_kb * 4 ))
hsize=`echo $hsize \
	| awk 'BEGIN {OFS = "";ORS=""}
	       { printf "%x" , $1
		 i = length($1)
		 while (i<8) {
		 	print 0
		 	i++
		 } }'`

echo "Memory size: $hsize_kb KB = $hsize"

echo -n "Supplying corrected MTRR ranges to /proc/mtrr... "
if ! grep -q $address /proc/mtrr; then
	echo "base=0x$address size=0x$hsize type=write-combining" >| /proc/mtrr && echo success
else
    echo "no need to do anything, MTRR range already set up"
fi

cat /proc/mtrr

exit 0

```

To make it run when xdm starts, I copied *fixmtrr.sh* to */usr/local/bin/*, and gave it execution permissions for root.
Then, I edited */etc/X11/xdm/Xsetup* and added the line:
```
/usr/local/bin/fixmtrr.sh
```

This is my setup now and it works for me, the mtrr errors are gone. YMMV.

---

### Post by Fiona23 on 2009-09-19
I type in:

$ gksudo gedit /etc/X11/xorg.conf

but nothing happens... Can't even manually edit file because I'm not root.

Edit:
Ahh no wonder. I don't have gedit, so I typed
```
$ gksudo mousepad /etc/X11/xorg.conf
``` 
instead

---

### Post by tomchiverton on 2009-09-19
> **Fiona23 said:**
> I type in:

$ gksudo gedit /etc/X11/xorg.conf

but nothing happens... Can't even manually edit file because I'm not root.

Try 
# sudoedit  /etc/X11/xorg.conf
or
# sudo -i
# gedit /etc/X11/xorg.conf

---

### Post by Auslegung on 2009-09-21
Searched the thread but didn't find any solutions.  My mousepad is now acting strange.  It is nearly impossible to move it a small amount, but moving it a far amount is easy as usual.  I have changed every setting under Mouse to no avail.  

On the plus side, I am now able to watch video smoothly, even HD video on youtube, but it does *devour* a lot of resources.

---

### Post by lwhitmore on 2009-09-22
HI

The lastest round of MESA and intel drivers seems to have completely broken my X windows.  Messed up fonts, laggy performance and no compiz.

This kind of thing is happening far more frequently these days.  A few weeks ago,  I was very happy with the performance and would have been happy to stick with what I had.  Since then, Ubuntu's gone from rock solid to unusable - and every update is like russian roulette.

Does anyone know if there's a version of the driver I could install that would solve my woes?  E.g. would it be possible to install the karmic intel driver (without installing karmic alpha)?

---

### Post by Jeff Saffan on 2009-09-22
Thank you for this guide!
I'm now enjoying great graphics :-)
peace
jeff

---

### Post by tomchiverton on 2009-09-22
At this point I've disabled auto-updates from the Xorg-edgers (etc.) repo., as it got to a point a few weeks back where it all worked and I was happy with it.
Right now, if I were you I would be sorely tempted to install the current Karmic pre-release all-in.
It would also be possible to just grab their kernel, xorg-*, mesa etc. packages, I suppose...

---

### Post by lwhitmore on 2009-09-22
@tomchiverton;

I wish I'd had the sense to do the same :)  .. I think the debs are probably still in my cache so I might just manually install those from a few versions back.

I'm not sure I want to install karmic yet - I installed Jaunty as a beta and it was great .. but my system was running almost perfectly.  I'm not sure I can be bothered to go through another round of growing pains just yet ;)

---

### Post by BarefootSoul83 on 2009-09-22
just did the "Optimal" settings....FABULOUS! graphics are noticeably better...especially in full screen

:guitar:

Jammin!!

Thanks!

---

### Post by rgsteele on 2009-09-24
> **Auslegung said:**
> Searched the thread but didn't find any solutions.  My mousepad is now acting strange.  It is nearly impossible to move it a small amount, but moving it a far amount is easy as usual.  I have changed every setting under Mouse to no avail.  

On the plus side, I am now able to watch video smoothly, even HD video on youtube, but it does *devour* a lot of resources.

Assuming you are using the "Optimal" configuration, I suspect your trackpad was using a driver that is not supported by the new kernel. Your best bet might be to upgrade to the alpha of Karmic. I'd recommend trying the live CD first to make sure everything works.

---

### Post by BarefootSoul83 on 2009-09-26
I have 2 problems:

1) Bleeding edge crashed my graphics...I'm having to boot using the Ubuntu live cd... how do I get into my actual root to fix this? HEEEELLLLPPP!!!

2) The optimal settings worked GREAT...the graphics stopped shuddering.. however, dual screen stopped working...when I set it up for dual...the 2nd screen is just a "stretch" of the first screen instead of its own virtual desktop...any suggestions?

---

### Post by WhiteHorse on 2009-09-26
I had the same problem with the kernel 2.6.30-02063002-generic and 2.6.28-15 so I installed 2.6.30-02063003-generic and now video playback is smooth again.

---

### Post by baytuni on 2009-09-27
I apllied the optimal safe solution but with kernel 2.6.29 . But it seems that exa is giving way better performance than uxa for that kernel.

---

### Post by glaze on 2009-09-28
I'm currently reading ChangeLog for 2.6.32-rc1 and it seems to have a lot of stability fixes.

---

### Post by rgsteele on 2009-09-28
> **BarefootSoul83 said:**
> I have 2 problems:

1) Bleeding edge crashed my graphics...I'm having to boot using the Ubuntu live cd... how do I get into my actual root to fix this? HEEEELLLLPPP!!!

2) The optimal settings worked GREAT...the graphics stopped shuddering.. however, dual screen stopped working...when I set it up for dual...the 2nd screen is just a "stretch" of the first screen instead of its own virtual desktop...any suggestions?

First, eject the live CD.

Second, EJECT THE LIVE CD. You appear to have missed this step when following the instructions BslBryan posted in [this thread]("http://ubuntuforums.org/showthread.php?p=8011381"). :)

When you boot the computer, you will see a prompt saying "GRUB loading, please wait. Press ESC to enter the menu...". Press ESC. The message will only appear for a second so you have to be quick.

Once you get into the GRUB menu, select the [recovery mode] option of one of the kernels. When the Recovery Menu appears, select the "netroot" option. Now you will be able to follow the instructions in the "To revert settings" section.

Note that since we are not in the graphical environment, you will need to use a terminal-based editor instead of gedit to edit your sources.list. Instead of "gksudo gedit /etc/apt/sources.list", use "pico /etc/apt/sources.list". Once you are done making the changes, press ctrl-X to exit and press Y when asked whether to save.

Also, since you're already root, you won't need to put "sudo" in front of any of the commands.

Once you have finished following the instructions, use the "reboot" command to restart your system.

---

### Post by zevans on 2009-10-02
> **kwaanens said:**
> After being on this solution since ~ day 3 of Jaunty I recently tried going back to the most recent linux-image from jaunty-proposed (2.6.28-15.52), and find that this setup works the same as the kernel installed from this thread. Only the kernel is different, all other changes from this thread is still applied. 
Planet penguin racer works, Gnome Do is as responsive as it should, flash works. No freezes or crashes the days I've been using it. Intel 945GM on an MSI s262 notebook.

Yup, that's because over on launchpad a lot of tracking down of bugs was done and the really egregious bugs that were fixed in later kernels have had the fixes backported. -14 had some of them, guess -15 must have all the important ones!

---

### Post by X1R1 on 2009-10-02
Now I see why you were featured on the tutorial of the week thread, really amazing job, helped a LOT, thanks!!!!

---

### Post by Masterofpsi on 2009-10-02
Posting from the Karmic beta with the default driver. The devs really improved this; where blur used to make my system unusuable, even with this thread's fix, I can now blur things, although it makes some Compiz effects (the cube and scale, most noticeably for me) slower.

---

### Post by solitaire on 2009-10-03
in Karmic the first repo's I added was the Xorg Edgers Builds for my GM965 "http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu"
But I usually then uninstall "Compiz" lol!

I've never had any problems when I did run Compiz. I just don't need eye-candy (unless she's a cute wallpaper!!) ^_~ lol

---

### Post by Masterofpsi on 2009-10-03
> **solitaire said:**
> in Karmic the first repo's I added was the Xorg Edgers Builds for my GM965 "http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu"
But I usually then uninstall "Compiz" lol!

I've never had any problems when I did run Compiz. I just don't need eye-candy (unless she's a cute wallpaper!!) ^_~ lol

Eye-candy can be such a pejorative term. There are plenty of useful effects. :P

---

### Post by ravi.xolve on 2009-10-06
I googled and found this tutorial based on this long and informative thread.

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

I just modified the x.org file (I stick to default kernel and X.org as long as possible) as told.
 Here is my VGA controller specifications:


 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Device 3a02
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 2297
        Region 0: Memory at f4000000 (64-bit, non-prefetchable) [size=4M]
        Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 4: I/O ports at 1800 [size=8]
        Capabilities:




Now my computer is showing me the expected performance!!!

---

### Post by VioletsPie on 2009-10-08
From the early days of Jaunty I had the 'bleeder' configuration with no problems. Just now I updated and like some other posters got nailed. I am currently running Ubuntu on low graphics mode. 

The revert settings did not seem to work. When I boot in it tells me there's another 'X' server listening to '0' and then it boots as '1'.


X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-24-xen i686 Ubuntu
Current Operating System: Linux Melpomene 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Kernel command line: root=UUID=f305f904-ba39-454f-aa3b-475e2cc2b213 ro quiet splash vga=758 
Build Date: 06 August 2009  08:08:47PM
xorg-server 2:1.6.3+git20090805+server-1.6-branch.f274e595-0ubuntu0sarvatt3~jaunty (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Oct  8 14:39:35 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xd0000000, size = 0x00770000, type = 1) Invalid argument (22)
 ddxSigGiveUp: Closing log

---

### Post by baytuni on 2009-10-08
I tried all the possible configurations described on the guide. The best results were with safe configuration and with "exa". I tried "uxa" with safe,optimal and bleeding edge configurations but the effects were choppy and with the bleeding edge it was unusable. I think I'm gonna have to wait for karmic stable to get uxa work properly. Here is my optimal configuration with my _GMA965 video card._

Kernel: 2.6.28-15
Xorg: 1:7.4~5
xserver-xorg-video-intel: 2:2.7.1-0

and /etc/X11/xorg.conf looks like this

```
Section "Device"
	Identifier	"Configured Video Device"
        Driver          "intel"
        Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true"

EndSection
```

I also did not understand why they include "EXAoptimizemigration" and "MigrationHeuristic" options in the guide. Since these are exa options once "uxa" was enabled the should be no longer valid. Am I wrong?

---

### Post by Alex_W on 2009-10-08
@VioletsPie:

had the same problem just this morning. fixed by allowing the low graphics mode (you also might have to press Space or Enter if the screen remains dark for too long -- it then loads X) and pulling out the older packages from /var/cache/apt/archives... one by one, looking at the date, getting only those that I know worked before (my case -- form Oct 4th)... and then dpkg'ing them all.

If you have the earlier kernel still installed (2.6.28), you can boot it in recovery mode, get root shell, and then do the same (having something like Midnight Commander handy will ease the task).

I also tried to figure out exactly which package caused the trouble -- it's NOT xserver-xorg-intel (like the last time); my suspicion is on libdrm2.

Cheers,

Alex

Jaunty on HP Pavillion dv4000

---

### Post by rob22941 on 2009-10-08
Now I did each level of upgrade and I did notice a difference in the scrolling in firefox. Although there is a small amount of skip its tolerable now. Thanks much.

---

### Post by solitaire on 2009-10-09
> **VioletsPie said:**
> From the early days of Jaunty I had the 'bleeder' configuration with no problems. Just now I updated and like some other posters got nailed. I am currently running Ubuntu on low graphics mode. 

The revert settings did not seem to work. When I boot in it tells me there's another 'X' server listening to '0' and then it boots as '1'.


X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-24-xen i686 Ubuntu
Current Operating System: Linux Melpomene 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Kernel command line: root=UUID=f305f904-ba39-454f-aa3b-475e2cc2b213 ro quiet splash vga=758 
Build Date: 06 August 2009  08:08:47PM
xorg-server 2:1.6.3+git20090805+server-1.6-branch.f274e595-0ubuntu0sarvatt3~jaunty (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Oct  8 14:39:35 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xd0000000, size = 0x00770000, type = 1) Invalid argument (22)
 ddxSigGiveUp: Closing log


I just got hit with the same problem...
Any know how to fix it?

I'm going to revert to the stable drivers and see if those work ^_^

---

### Post by quebeck5 on 2009-10-10
> **solitaire said:**
> I just got hit with the same problem...
Any know how to fix it?

I'm going to revert to the stable drivers and see if those work ^_^

Had the same problem, was running 2.6.30.7 kernel, updated to the very latest development kernel and the problem went away.

---

### Post by solitaire on 2009-10-10
> **quebeck5 said:**
> Had the same problem, was running 2.6.30.7 kernel, updated to the very latest development kernel and the problem went away.

I just dropped the "Xorg Edgers" builds for intel GFX testing builds (also removed bits of the nv and ATI drivers it was trying to install for some reason?!?!?!)

but after that it booted fine.

I've not tested it with my second monitor attached (the default drivers don't give me 1920x1080 on the second monitor) So not sure if everything is OK.

Hope they fix the Edgers problem soon! ^_^

---

### Post by tormod on 2009-10-10
psyke, please make sure the guide clearly informs people to go to the xorg-edgers PPA page and read everything there before installing packages from that PPA. I get reports from people who seem to have added the PPA but are not aware of the information on the PPA page.

Otherwise, your guide looks good and seems to contain the necessary disclaimers :)

---

### Post by scarf on 2009-10-10
hi.  i modified my system months ago, following the safe method.  i have the 855GM.  xserver-xorg-video-intel is 2:2.7.1-0ubuntu1~xup~1.

lately, upon rebooting, when gdm loads, my screen will turn completely white.  it doesn't start out completely white, however.  instead, most of the screen turns white, and during the next few seconds, the white color "bleeds" across the screen until the screen is completely white.

in order to resolve this, i have had to switch to the console and restart gdm.  the first time this happened, restarting gdm once resolved the problem.  today, after my second reboot, i had to restart gdm twice before the problem disappeared.

so, i have run into this problem twice now after two reboots.  i don't reboot my system often.  the second to last reboot was:

reboot   system boot  2.6.28-15-generi Thu Sep 17 12:32 - 10:18 (22+21:46)

and the last reboot was today:

reboot   system boot  2.6.28-15-generi Sat Oct 10 09:49 - 10:15  (00:26)


this is also the same thing that happened to me months ago when we were told to test performance with planet penguin racer.  after launching the game my screen would turn white as if it was malfunctioning, and over the next few seconds the white would "bleed" across the whole screen until it was completely white. i had to wait for the game to load and then press ESC in order to get out.

---

### Post by Wandel on 2009-10-10
> **quebeck5 said:**
> Had the same problem, was running 2.6.30.7 kernel, updated to the very latest development kernel and the problem went away.

Do you have link to a guide for that, or could you post some relatively user-friendly instructions? Thanks.

---

### Post by solitaire on 2009-10-10
I updated to the same kernel as karmic and the Xorg-Edgers drivers worked, but the new kernel does not have the module for my laptops wireless card! :(

need to work out how to get the drivers! (I'm currently running my Karmic install till I can get Jaunty working again!).

---

### Post by quebeck5 on 2009-10-10
> **Wandel said:**
> Do you have link to a guide for that, or could you post some relatively user-friendly instructions? Thanks.

go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

download whatever kernel you want. for the very latest one the directory you should be in is
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

download 3 files for the architecture of your computer. for me (i386), that's the 

linux-image....i386.deb
linux-headers...i386.deb

and

linux-headers....all.deb (that's for both archtiectures)


once you've downloaded them somewhere, run in the directory they are in:

sudo dpkg -i  file1 file2 file3

then restart.

---

### Post by tormod on 2009-10-11
> **quebeck5 said:**
> go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Fail. Technically the instructions are correct, but you should rather point people to [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) so they read the instructions from the people who run the PPA.

---

### Post by tormod on 2009-10-11
> **solitaire said:**
> I updated to the same kernel as karmic and the Xorg-Edgers drivers worked, but the new kernel does not have the module for my laptops wireless card! :(

need to work out how to get the drivers! (I'm currently running my Karmic install till I can get Jaunty working again!).
So you are saying the Karmic kernel has the necessary driver in a Karmic installation, but not when you use it in Jaunty? Or does "same kernel as karmic" not mean the karmic kernel? Well hard to guess any further since you don't even mention the name of the card or driver involved...

---

### Post by areskz on 2009-10-11
Yesterday I updated many packages, and xorg-video-intel was among them. And I think that is the source of my problem now.

When I boot my Ubuntu Jaunty, I get this message:
```
Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): No kernel modesetting driver detected.
(EE) Screen(s) found, but none have a usable configuration.
```

After that I can choose from several options: reconfigure graphics (it doesn't help), go back to the console login, or to start ubuntu in low-graphics mode (that's what I am doing now). If I start in low-graphics mode, everything works good, but in a small (about 640x480) window in the center of the screen. Borders are black.

How can I solve this?

---

### Post by Wandel on 2009-10-11
> **quebeck5 said:**
> go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

download whatever kernel you want. for the very latest one the directory you should be in is
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

download 3 files for the architecture of your computer. for me (i386), that's the 

linux-image....i386.deb
linux-headers...i386.deb

and

linux-headers....all.deb (that's for both archtiectures)


once you've downloaded them somewhere, run in the directory they are in:

sudo dpkg -i  file1 file2 file3

then restart.Thanks a lot, that did the trick :)

@areskz: You should try this. You're getting the same error message I was having.

---

### Post by SteveMcQwark on 2009-10-11
> **areskz said:**
> Yesterday I updated many packages, and xorg-video-intel was among them. And I think that is the source of my problem now.

When I boot my Ubuntu Jaunty, I get this message:
```
Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): No kernel modesetting driver detected.
(EE) Screen(s) found, but none have a usable configuration.
```

After that I can choose from several options: reconfigure graphics (it doesn't help), go back to the console login, or to start ubuntu in low-graphics mode (that's what I am doing now). If I start in low-graphics mode, everything works good, but in a small (about 640x480) window in the center of the screen. Borders are black.

How can I solve this?

First step: follow the instructions in the original post to downgrade from xorg edgers to the jaunty default. (open sources.list with nano or vi rather than gedit) Be sure that, if it says it will remove any packages, that you look for anything that is libglu1 or mesa or anything else that looks like the stuff you are trying to downgrade. If so, cancel the operation then try again with downgrading those packages as well, so that you don't end up removing any packages. 

Then run an update and full upgrade to make sure you have the latest versions of everything

You will have to do all this from the command line, so make sure you have a wired internet connection (or some way to get wireless working, though its not really worth the effort)

Anyone know any more stable xorg packages that work about as well as the xorg edgers? They've worked great, but this is the second time this has happened. The new default packages are tolerable, but there's still some lag and artifacting in plasma.

Edit: Sorry, you're in a better position than I was. I couldn't get any gui. So, you won't have the editor or wireless issues, but otherwise, that's pretty much how to solve the problem until its fixed on the dev side.

---

### Post by Orographic on 2009-10-12
Something I did ages ago was to make a Clonezilla image of Jaunty prior to any fixes from this thread. I initially used the Safe Configuration and it still works fine with my 945GZM-S2 Gigabyte board after the latest updates for Ubuntu, which were pretty big. I can't remember the extent of them.

---

### Post by tormod on 2009-10-12
I am glad there are so many helpful people here and people willing to test out the latest development drivers. However there is a lot of misinformed and bad advice given in the forums.

[LIST=1]
[*] Read random postings with a great portion of skepticism and caution
[*] Be careful when posting information, at least take the time to look up information given in earlier posts and try to find official documentation
[/LIST]

Now, to the issues some people have with the latest -intel drivers from xorg-edgers:

[LIST=1]
[*] It is all explained on the xorg-edgers PPA page
[*] It has also been reported in launchpad #447181 (how I found this thread)  
[*] There is nothing wrong with the driver that needs to / will be fixed
[*] The latest -intel drivers have dropped support for UMS (user mode setting) and only use KMS (kernel mode setting) so the kernel has to run with KMS enabled
[*] The Jaunty kernel needs the "i915.modeset=1" boot option to enable KMS
[*] Karmic kernels have KMS enabled by default. They also contain many fixes to the kernel part of the intel driver stack.
[/LIST]
I see that some people simply refuse to look up the PPA page (it is linked from the instructions in the first post) so I will explain:

The xorg-edgers PPA tracks the work of the developers. It can be expected that it breaks for some users from time to time, since any developer can not test his changes on all hardware. You are providing this testing and it is highly appreciated. The idea is that you provide bug reports if something does not work. It is also expected that you know how to revert to the last working version in this case.

---

### Post by areskz on 2009-10-12
**SteveMcQwark**, thanks alot. Downgrading solved the problem. Updating is an evil.

---

### Post by samisomy on 2009-10-15
[SIZE=3][COLOR=Green]Hi,
am a new user on ubuntu have little situation here.

i installed ubuntu 9.0.4 and it installed the driver software for all cards automaticly ,
 but a got a problem which is the desktop resolution  is very low and the graphics looks badly.
even i makes comperhensive update to the system the problem still same.

i went to see the hardware i found it istalled correctly which is 

Nvidia geforce fx 5500 version 173


[COLOR=Blue]but am using WEGASONIC LCD monitor 21 Inch

[/COLOR]i entered the display option from the menu preferences it tells that the monitor is unknown !!!!  :confused:


how to install this monitor to solve the problem please ?????? 

 :(
[/COLOR][/SIZE]

---

### Post by psyke83 on 2009-10-15
> **samisomy said:**
> [SIZE=3][COLOR=Green]Hi,
am a new user on ubuntu have little situation here.
[/COLOR][/SIZE]

This thread only deals with Intel integrated graphics. I suggest you create a new thread with your problem [here]("http://ubuntuforums.org/forumdisplay.php?f=334") or [here]("http://ubuntuforums.org/forumdisplay.php?f=326").

---

### Post by samisomy on 2009-10-15
> **psyke83 said:**
> This thread only deals with Intel integrated graphics. I suggest you create a new thread with your problem [here]("http://ubuntuforums.org/forumdisplay.php?f=334") or [here]("http://ubuntuforums.org/forumdisplay.php?f=326").


thanks

---

### Post by tormod on 2009-10-15
I want to bump the -intel driver in the x-updates PPA to 2.9.0 (the last version with UMS support), and of course make sure it works with the Jaunty kernel (this PPA should have as few dependencies as possible).

I would therefore need some volunteers to test the packages I have pushed to the intel-gfx-testing PPA at [https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa) (libdrm and xserver-xorg-video-intel).

If feedback is good I'll move this to x-updates. Thanks.

EDIT: Done

---

### Post by alx818 on 2009-10-17
[quote=tormod;8110205]I want to bump the -intel driver in the x-updates PPA to 2.9.0 (the last version with UMS support), and of course make sure it works with the Jaunty kernel (this PPA should have as few dependencies as possible).

I had problems with xserver-xorg-video-intel version 2.9.0 on my notebook (Intel GMA 4500MHD):    
When the external monitor was connected, the maximum resolution was 960x600 pixels on the internal screen, the external monitor didn't work.  
When the external monitor was connected, the graphical output was completely unrecognizable (colored thin rectangles).    
I'm using Optimal Configuration from this forum post.    

Now, I reinstalled version 2.7.1 and it works fine again :-)    

If I should test 2.9.0, what infos would you need?

---

### Post by rbroom on 2009-10-17
I want to second problems with the 2.9.0 version of xserver-xorg-video-intel.

My Intel-based video (on the Asus P5Q-EM system board) on Jaunty went to 1280x1024 max, and couldn't detect the monitor type.

I reverted to the previous package version and the problem went away.

If you point me to the right spot for a bug report I'll file one and supply details.

---

### Post by SteveMcQwark on 2009-10-17
Yes, I also have issues with your version. I don't think you should keep this package in X-Updates, since it defeats the purpose of the ppa. You should have tested the functionality of your package before uploading it tbh.

---

### Post by TrevT93 on 2009-10-17
Fourthing (that's a word, right?) problems.  I'm using an Intel 945GMS Express, and unless I remove the packages we were supposed to upgrade to in the instructions, I cannot set my video resolution to anything higher than 1024 x 768.  Also using Optimal.

Any specific reason for this?  I've followed these instructions before (in Ubuntu, same computer, though I'm using Kubuntu now) and it has worked wonders on my graphics.

---

### Post by ednso on 2009-10-17
Hi,

Same problem here with Intel GM 965 and updated package xserver-xorg-video-intel, version 2.9.0.

What I did was to downgrade to the Jaunty official package, 2.6.3, and now every thing is working fine again, although I have had a hard system lock.

I am using kernel 2.6.30-02063009-generic. I was wondering if kernel 2.6.31-x would work better with the 2.9.0 version of Intel driver...

Thanks and bye.

---

### Post by baucha_linux on 2009-10-17
> **ednso said:**
> Hi,

Same problem here with Intel GM 965 and updated package xserver-xorg-video-intel, version 2.9.0...........



....I was wondering if kernel 2.6.31-x would work better with the 2.9.0 version of Intel driver...



I also confirm newer xserver-xorg-video-intel version 2.9.0 from X-Updates has problem. I am on intelGM965 and as soon as i updated, my screen size went to 880X600 display even though the system settings showed resolution of 1280X800 (resolution was infact 1280X800, only the display area was reduced to 800X600) :confused:.

I am using latest kernel 2.6.31.4. I tried with 2.6.28-15 kernel also but it's the same, no change. finally i had to downgrade the package to 2.70.1 which was working then everything was fixed. I warn user to be careful with 2.9.0 till it's fixed.

EDIT: It seems people were facing similar problems while this driver was in Edgers. I found the info in previous page 121 of this thread ;)

> 
   1.  It is all explained on the xorg-edgers PPA page
   2. It has also been reported in launchpad #447181 (how I found this thread)
   3. There is **nothing wrong with the driver that needs to / will be fixed**
   4. The latest -intel drivers have dropped support for UMS (user mode setting) and only use KMS (kernel mode setting) so the kernel has to run with KMS enabled
   5. **The Jaunty kernel needs the "i915.modeset=1" boot option to enable KMS**
   6. Karmic kernels have KMS enabled by default. They also contain many fixes to the kernel part of the intel driver stack.


So guys it  seems we have to enable KMS in jaunty kernel. good luck.

 Cheers!!

---

### Post by Orographic on 2009-10-17
Luckily I have a spare internal drive that I do my testing on. It has a fully up to date Jaunty image on it. I have the Safe Configuration here and I tried downloading the update that came this morning via Update Manager, named 'XServer-xorg-video-intel'. It has frozen me to a low resolution on my 22" Ben Q Screen. 

Monitor is not recognised anymore and I can't change the settings. I have a Gigabyte 945GZM-S2 with onboard intel graphics. The Safe Configuration has been working fine until now.

I will avoid the update on my main drive for now.

---

### Post by Orographic on 2009-10-17
I should also say that I tested the 'XServer-xorg-video-intel' update from Update Manager on a fully updated Jaunty drive that didn't have the Safe Configuration settings from this thread and everything seemed to work well at first.  When I tried full screen video via iView it still had tearing and stuttering. At about 80% fullscreen there does appear to be some improvement from prior to this update but not a lot.

---

### Post by scarf on 2009-10-17
WOW!

i notice a huge improvement with the 2.9.0 version!!  yeah!  my old laptop is finally performing like i was used to with intrepid!  in short, i think all problems are resolved!

i have the 82852/855GM and have followed the safe configuration.

with this new update:

- webpages are loading faster, nearly instantly again
- webpages are scrolling as fast as i want them to using the hyperscroll on my logitech mouse, and stopping on a dime (before there was so much lag, sometimes several seconds before the page view would catch up with me)
- scrolling in man pages (in gnome-terminal), openoffice, and evince is also working correctly again
- penguin racer now runs without turning my whole screen white!  i turned up all the settings and ran it at 1280x768, and i was getting 7-15 FPS.  i had to turn it down to 640x480 to get a significant improvement to 12-18 FPS

see this thread for my previous gtkperf results:
[http://ubuntuforums.org/showpost.php?p=7375827&postcount=616](http://ubuntuforums.org/showpost.php?p=7375827&postcount=616)

current results using same settings (1000 rounds and maximized):
```
GtkPerf 0.40 - Starting testing: Sat Oct 17 19:34:56 2009

GtkEntry - time:  0.93
GtkComboBox - time: 27.75
GtkComboBoxEntry - time: 18.74
GtkSpinButton - time:  4.73
GtkProgressBar - time:  8.09
GtkToggleButton - time:  5.12
GtkCheckButton - time:  4.04
GtkRadioButton - time:  7.88
GtkTextView - Add text - time: 165.50
GtkTextView - Scroll - time: 16.29
GtkDrawingArea - Lines - time: 47.55
GtkDrawingArea - Circles - time: 54.72
GtkDrawingArea - Text - time: 14.97
GtkDrawingArea - Pixbufs - time:  1.73
 --- 
Total time: 378.05
```

the "GtkTextView - Add text" test is still the (very) weak link.  why is it so slow to add text?

---

### Post by gboone on 2009-10-17
SOLVED but here's what happened.

I followed the safe instructions, then restarted. It beeped multiple times, and showed a white bar in the middle of the screen, beeps grew further apart, and monitor would turn on and off. Then, it just stayed black with white bar, no more beeping.

I restarted again, hit ESC to go to GRUB and selected Recovery Mode. Then, I selected "solve graphic problems", and then restarted. 

Everything works PERFECT. My kids watch nick jr videos and full screen works great. HULU, etc.

Thanks so much.:)

---

### Post by Orographic on 2009-10-17
Has anyone else had problems with having the Safe Configuration settings then updating with the 'XServer-xorg-video-intel' update that came through Update Manager today?

Edit: Also, I guess you can just lock the current working version in Synaptic Package Manager so you don't accidentally install the problematic, newest version.

---

### Post by baytuni on 2009-10-18
They removed xserver-xorg-video-intel 2:2.7 from x-swat repositories. Do you know where to find it? It was working better for me than 2:2.9

---

### Post by alx818 on 2009-10-18
> **baytuni said:**
> They removed xserver-xorg-video-intel 2:2.7 from x-swat repositories. Do you know where to find it? It was working better for me than 2:2.9

i downloaded the package from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=intel&field.status_filter=&field.series_filter=jaunty]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=intel&field.status_filter=&field.series_filter=jaunty")

---

### Post by baytuni on 2009-10-18
thanks a lot. I've been looking for it desperately. Somehow this 2:2.27 version is working like a charm with exa.

---

### Post by greg batmarx on 2009-10-18
Updating to the new intel driver caused me a pain!
The screen is white and i can't do anything...
I read it was needed to have enabled kms...
Then why they released this update to jaunty where kms is not enabled by default?:confused:
Please help me to restore the situation...
The problem seems to be widespread and have been posted in various new threads..
Fortunately I still can run kde so i can post the problem...

---

### Post by greg batmarx on 2009-10-18
I can also run xfce!
So the problem is strictly gnome related...
Is it recommended to upgrade to karmic beta?
How can i do this through the command line/

---

### Post by solitaire on 2009-10-18
Latest X-Org Edgers is VERY slow on my Intel GM965 graphics.
Xorg hits 100% when opening nautilus or Firefox and becomes very slow and unresponsive,
Also GDM crashes / resets every time I try to play ANY video. Also I've seem to have lost tty1-6 I just get a blank screen with a frozen mouse pointer on it (no terminal in sight!)

Theres 1 good thing out if this... it's pushed me to install Karmic tomorrow morning since its the ONLY usable version of Ubuntu with this graphics card that can put out 1080p to an external monitor....

---

### Post by tormod on 2009-10-18
> **alx818 said:**
> [quote=tormod;8110205]
I had problems with xserver-xorg-video-intel version 2.9.0 on my notebook (Intel GMA 4500MHD):    
When the external monitor was connected, the maximum resolution was 960x600 pixels on the internal screen, the external monitor didn't work.  
When the external monitor was connected, the graphical output was completely unrecognizable (colored thin rectangles).    
I'm using Optimal Configuration from this forum post.    

Now, I reinstalled version 2.7.1 and it works fine again :-)    

If I should test 2.9.0, what infos would you need?
Can you check if you have the same problem on a Karmic live CD, booting with i915.modeset=0 (or nomodeset)? (Karmic uses KMS by default, so disabling it should give a similar situation as in Jaunty.) If yes, please file a bug, where you attach Xorg.0.log

---

### Post by tormod on 2009-10-18
> **SteveMcQwark said:**
> Yes, I also have issues with your version. I don't think you should keep this package in X-Updates, since it defeats the purpose of the ppa. You should have tested the functionality of your package before uploading it tbh.
I asked for testing and did not get any negative responses. The x-updates PPA is for stable releases, and 2.9.0 is a stable release. From the various feedback we have now (after I pushed it to x-updates of course), it seems to work well for some people and worse for others. Anyway, not everybody has to update, they can stay with the old if they prefer.

Also some people seem confused about which PPAs they are subscribed to. If you are only using the x-updates PPA, you don't need a new kernel or enable KMS. That said, it is possible that it would help...

---

### Post by Catharsis on 2009-10-18
The xserver-xorg-video-intel update to 2.9.0 won't load the login screen for me. It sends me to a terminal instead. I had to downgrade to 2.7.1 (thanks to alx818 for the link) to get X working.

Here's the bug report I filed. Let me know if I need to move it.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/455010](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/455010)

---

### Post by paxmark1 on 2009-10-18
I got the white screen also for a desktop in gnome.
  Shifting to a xfce session worked to view a desktop
I Used in a terminal 

apt-cache show xserver-xorg-video-intel

AND THEN for me

sudo aptitude install xserver-xorg-video-intel=2:2.6.3-0ubuntu9

appears back to normal now in gnome.

NOTE:  I still need use aptitide to pin to 2.2.6.3
  

I will be looking for info about this for Karmic.  I haven't tried the beta yet. Might be time to set up a usbstick and try.

---

### Post by Orographic on 2009-10-18
I tried Karmic Beta via the live CD and enabled multiverse repos (I think) to install Flash and Ubuntu Restricted Areas. Fullscreen video seemed to work notably better in ABC iView and YouTube.

---

### Post by tormod on 2009-10-19
***x-updates:***

It turns out that the intel 2:2.9.0-1ubuntu2~xup~1 package was missing a PCI ID file, so many of you ended up using the vesa driver instead of the intel driver. This would explain missing modes and wrong resolution. This should be fixed in 2:2.9.0-1ubuntu2~xup~3. Please check your Xorg.0.log if there are still problems. See bug #454029. This also demonstrates that filing a bug is much more efficient than complaining in a forum...


***xorg-edgers:***

Since so many people use xorg-edgers on Jaunty without knowing it, or knowing what they are doing, I have uploaded a 2.9.0 version with UMS. It will replace the previous post-2.9.0 version (which happened to have a 2.9.0~ version number so it will smoothly "upgrade" although it is a downgrade). See bug #447181.

---

### Post by Orographic on 2009-10-19
I'm not sure people were complaining. They were just making forum readers aware of a situation. Posting information in this forum is good as it helped me not install this update, initially. Bug reports are good no doubt but there is value in the forum approach as well.

---

### Post by aboutblank on 2009-10-19
Today I updated to 2:2.9.0-1ubuntu2~xup~3 from the x-updates repo, and it broke compositing. I have a T61 laptop with GM965 / X3100 integrated video. When I enable compiz, screen actions like moving windows slow down to the point of being unusable.

I get ~300 FPS on glxgears. Looking at Xorg.0.log, it appears that the DRI module is loading too.

I'm not sure what the problem is. Running the fixmtrr.sh script did not help. Perhaps something in my xorg.conf?

Xorg.0.log and xorg.conf are attached. Will tweak xorg.conf to set:
Option		"AccelMethod"			"uxa"

and update to let you know if that fixed it. I had this line commented out because with it enabled, graphics were unusable (same slow problem) with compiz when I first set it up.

Update: Using AccelMethod "uxa" did not change anything. It's unclear to me if the kernel module is loading. How do you check? What is the module name?

Gosh I *sure* hope this is fixed in Karmic. I was never able to get tear-free fullscreen video, which I would really like. I should download the beta and test it...

---

### Post by Orographic on 2009-10-19
Read my post, above. I've had Karmic running full screen video fine and yesterday installed the Beta version on my spare drive and it worked well at full screen.

---

### Post by tormod on 2009-10-19
> **Orographic said:**
> I'm not sure people were complaining. They were just making forum readers aware of a situation. Posting information in this forum is good as it helped me not install this update, initially. Bug reports are good no doubt but there is value in the forum approach as well.
Yes, you are right. But a bug should be filed as well. Not just "I'll just wait for this to be fixed".

---

### Post by tormod on 2009-10-19
> **aboutblank said:**
> I'm not sure what the problem is. Running the fixmtrr.sh script did not help. Perhaps something in my xorg.conf?

Try without any xorg.conf at all. And yes, the log shows that DRI2 is correctly set up, so the kernel module seems to work.

---

### Post by aboutblank on 2009-10-19
> **tormod said:**
> Try without any xorg.conf at all. And yes, the log shows that DRI2 is correctly set up, so the kernel module seems to work.

Thanks tormod, I can run compiz when I start without an xorg.conf (or with all the option lines under Section "Device" for "Configured Video Device"). I tried enabling each of these options one by one, but enabling any of them caused the xserver to not load with the login screen.

So now the only problem is that when running compiz, the beginnings of animations seem slow or stuttered. For example, with compiz disabled, glxgears gets 353 - 359 FPS every 5 second interval, including the first. With compiz enabled, glxgears gets around 360 FPS on the first 5 second interval, then 430 - 440 FPS for the next 10 intervals. This is obvious in everyday use when using the cube animation or in avant window manager animations. Is this possibly caused by the default migration heuristic?

Thanks for your help!

---

### Post by StaRetji on 2009-10-19
> **tormod said:**
> ***x-updates:***

It turns out that the intel 2:2.9.0-1ubuntu2~xup~1 package was missing a PCI ID file, so many of you ended up using the vesa driver instead of the intel driver. This would explain missing modes and wrong resolution. This should be fixed in 2:2.9.0-1ubuntu2~xup~3. 

I have Ubuntu Jaunty with kernel 2.6.28-11-generic

Do I have to upgrade the kernel in order to use x-updates 2:2.9.0-1ubuntu2~xup~3 :confused:

When I tried xorg-edgers in the past it was complaining about kernel mode setting, so I was downgrading.

Is it ok to use this driver 2:2.9.0-1ubuntu2~xup~3 with 2.6.28.11-generic ?

Thx for all the hard work!

---

### Post by Orographic on 2009-10-19
> **tormod said:**
> Yes, you are right. But a bug should be filed as well. Not just "I'll just wait for this to be fixed".

Yes, good point. That makes sense to me. I'm quite new to Ubuntu and am still learning about the bug reporting process in between working with 70 students and doing my postal run. I will get there.

---

### Post by tormod on 2009-10-20
> **StaRetji said:**
> Is it ok to use this driver 2:2.9.0-1ubuntu2~xup~3 with 2.6.28.11-generic ?
Yes, the packages from x-updates are supposed to work with the normal kernel.

But since the whole video driver stack is spread between the -intel driver, mesa (for OpenGL) and kernel (the i915 module), some bug fixes and improvements will be in the kernel so a new kernel might help for some issues.

---

### Post by StaRetji on 2009-10-20
> **tormod said:**
> Yes, the packages from x-updates are supposed to work with the normal kernel.

Great work!!!

I can confirm that driver significantly improved performance of the Intel 945 on old kernel   :guitar:

Respects and gratitude for hard work!


I have just two more questions:

1. Do we still have to use fixmtrr.sh script or we can drop it now?
2. Is there going to be an update of mesa in x-updates soon?

Thx!!!

---

### Post by GNUbee40 on 2009-10-20
Hi!

I am using Optimal Configuration, but without UXA Acceleration activated, as this gave errors when sending laptop to sleep.
After latest updates from Ubuntu I experience that my screen is now listed as unknown and screen resolution cannot be set higher then 1024*768 anymore.
Is this related to the changes in the Xorg.conf?

What will happen to these modifications when upgrading to Karmic? Will I need to undo them?

All best

---

### Post by tormod on 2009-10-20
> **GNUbee40 said:**
> I am using Optimal Configuration, but without UXA Acceleration activated, as this gave errors when sending laptop to sleep.

Not sure what you mean by "optimal configuration", but since 2.8 EXA and XAA is gone so UXA is the only choice and always enabled AFAIK.
> 
After latest updates from Ubuntu I experience that my screen is now listed as unknown and screen resolution cannot be set higher then 1024*768 anymore.
Is this related to the changes in the Xorg.conf?

You are using the latest version right? Try without an xorg.conf.
> 
What will happen to these modifications when upgrading to Karmic? Will I need to undo them?

Generally, try without an xorg.conf, or a minimal one with as few options as possible.

---

### Post by GNUbee40 on 2009-10-20
Thanks for the reply!

Ad UXA: As long as I had it enabled in Xorg.conf, my session was ended and all programs forced quit when the laptop went into sleep mode. If UXA now is enabled by default I conclude that these problems have been solved as I am no longer experiencing them.

Ad Optimal Configuration: Refer to the first post of this thread. This was originally a HOWTO guide, and modifying Xorg.conf was part of the procedure. With the latest updates this might no longer be necessary.

Removing xorg.conf didnt make any difference however.

I ran update manager manually and x-server intel driver updates were installed. Resolution is now back to normal. 

The graphic performance is diminished though compared to before the recent updates. Full screen youtube will freeze as soon I move the mouse pointer. Hopefully the Karmic updates provide a solution.

Regards

---

### Post by StaRetji on 2009-10-22
Also, dmesg outputs this:

[   40.407996] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   42.011754] [drm:i915_setparam] *ERROR* unknown parameter 4
[   42.011827] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   43.014706] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   47.517027] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   53.772964] [drm:i915_getparam] *ERROR* Unknown parameter 6

I guess it should be harmless, but it delays  boot for 13 seconds...

Please, can you also comment should fix that is suggested in the first post (fixmtrr.sh)
be used or not.

Thx.

---

### Post by I_Like_Pie on 2009-10-22
> **tormod said:**
> ***x-updates:***
This also demonstrates that filing a bug is much more efficient than complaining in a forum..

With all due respect and patronization aside...the reason people went to the forum is that this bug is an intel chipset related issue.  Real pain in the bum in that there are a couple of custom changes required that create a non typical Ubuntu setup. 

Since, in the past, these chipsets involved tweaks only found within the ubuntu forum community to work efficiently (_*NOT*_ resolved by bug reporting as they have claimed as low priority at times)  the natural place for these users to migrate is back to the forum.

Thanks for the help and knowledge, but there is a very valid reason that many users created a 120+ page thread on this problem and its resolution on the ubuntuforum.  It is good to hear that there is a fix in the process.

---

### Post by triplesick on 2009-10-22
um, everything was fine, then i updated to 2.9.0 via update manager, now anything that tries to use 3d CRASHES AND BURNS!!  without a trace!!  what happened?

EDIT:

wait, not everything.  only quake live.  that's all i want to play though!!  :( :(

---

### Post by Aero-Z on 2009-10-25
I'm wondering why my 9.10 installation doesn't have xorg.conf at all by default.

---

### Post by psyke83 on 2009-10-25
> **Aero-Z said:**
> I'm wondering why my 9.10 installation doesn't have xorg.conf at all by default.

Karmic doesn't use an xorg.conf configuration file.

This guide is *only* for Jaunty users.

---

### Post by mirko123 on 2009-10-25
HI. 
I followed this guide and it caused ubuntu to freeze on restart.
it freeses on loading before i can input password.
I have asus p4sd MB with onboard Intel graphics. I think it's Intel 82865G.
I was trying to get desktop effects to work but no sucess.
Any help would be much appreciated.

---

### Post by Aero-Z on 2009-10-25
> **psyke83 said:**
> Karmic doesn't use an xorg.conf configuration file.

This guide is *only* for Jaunty users.
Ah ok :)

---

### Post by darkksyde on 2009-10-27
Great guide, thanks alot

---

### Post by Mularkey23 on 2009-10-28
> **psyke83 said:**
> Karmic doesn't use an xorg.conf configuration file.

This guide is *only* for Jaunty users.

So when I upgrade to Karmic tomorrow, I don't have to worry about reverting the xorg settings?

---

### Post by psyke83 on 2009-10-29
> **Mularkey23 said:**
> So when I upgrade to Karmic tomorrow, I don't have to worry about reverting the xorg settings?

None of the configuration options from this guide will affect the 2.9.0 driver. UXA is the default - and only - acceleration method, which also makes the EXA options useless.

You can delete your xorg.conf after upgrading to Karmic (but keep a backup, as Karmic no longer presents an easy way to generate blank xorg.conf files).

The fixmtrr.sh script is still useful if you restart Xorg (which is surprising; I thought the bug was fixed properly).

---

### Post by tony_chu on 2009-10-29
Any tips on what to do if you have upgraded to Karmic?

A couple of weeks ago i updated my xserver-xorg-video-intel drivers (still using jaunty 9.04) as it were a part of the system update program. Since then my graphics performace have been seriously degraded. I can not use anything other than 'None' under Visual Effects where I could previously use 'Extra' with not a hint of a glitch. Even when turning visual effects off, my system is extremely slow graphic-wise, i can't even move the mouse pointer smoothly.

I am using a laptop with Intel i45GM chipset and Intel GMA 4500MDH graphics card. I've been living with this problem for some weeks because i thought it would be sorted out in Karmic but obviously it has not.

---

### Post by StaRetji on 2009-10-29
> **psyke83 said:**
> The fixmtrr.sh script is still useful if you restart Xorg (which is surprising; I thought the bug was fixed properly).

Can confirm this.

After more than a week testing new driver, I must say that improvement is barely noticeable. 

Youtube standard videos are still working sadly, not to mention that HD trailers are seen like a slideshow.

To be honest, I gave up on Intel GPU Linux driver support, that I'll never buy a product with it again :(

Generally I'm optimistic, but regarding intel driver future, bah...

---

### Post by Mularkey23 on 2009-10-29
After upgrading to Karmic, I completely lost all of my graphic visual effects.  Karmic couldn't locate any drivers to turn them on.  I finally fixed this by editing my xorg.conf (which Karmic reset) and applied the fitmtrr.sh script again, poof! everything back to normal.

Can someone explain this to me, since Karmic doesn't use xorg, or uses it differently?

Oddly enough, I was having troubles before: brightness only adjusted randomly, screen flickered to different brightnesses whenever it wanted too, etc.. those have all gone away!  Why is this? 

Thanks

---

### Post by tormod on 2009-10-30
With regard to using a xorg.conf or not, from the driver perspective, nothing has changed from Jaunty to Karmic: It will work without one as well as with one.

The difference in the distribution is that Jaunty shipped a minimal xorg.conf (practically empty, it only had headers and identifiers and no options set) and Karmic ships without one.

---

### Post by tony_chu on 2009-10-30
> **tormod said:**
> With regard to using a xorg.conf or not, from the driver perspective, nothing has changed from Jaunty to Karmic: It will work without one as well as with one.

The difference in the distribution is that Jaunty shipped a minimal xorg.conf (practically empty, it only had headers and identifiers and no options set) and Karmic ships without one.

So I can use this guide with Karmic aswell?

---

### Post by Mularkey23 on 2009-10-30
> **tony_chu said:**
> So I can use this guide with Karmic aswell?

^ I had to after I updated, even after applying it to jaunty, but you're going to want to use the karmic kernel, of course :)  I'm not sure if it was the xorg.conf file or the fix.sh script that did it though.

---

### Post by ravi.xolve on 2009-10-31
My Intel graphics is this:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

I used this guide in jaunty to get back the KWIn (or compiz) effects. And karmic works fine, even better.

---

### Post by ravi.xolve on 2009-10-31
[@StaRetji]("http://ubuntuforums.org/member.php?u=933732")

for flash update your plugin. it worked for me.

---

### Post by g8rb8 on 2009-11-01
Ok, Ive searched and tried everything I can find in here and still can't get this to work so I'll try here since this thread seems closest to my situation.
 I'm trying to set up Ubuntu Mobile on my Fujitsu Stylistic 4110, which has an Intel 82830 graphics chip. The problem is it will only work on an external monitor. On the tablet's screen all I get is white vertical bars. If I switch to a TTY console it is a very low resolution and after a couple of commands I can't see what I typing any more. Everything works fine with only the external monitor enabled. 
 Weird thing I noticed when trying the memory script setup is lspci shows two video cards. Is that normal? Which memory range is the correct one? (I've tried both in the script with no luck)

---

### Post by tony_chu on 2009-11-02
What am I supposed to enter in my sources.list when using Karmic? Is it supposed to be "ubuntu jaunty main"?

> **psyke83 said:**
> 
1. Add the [X Updates PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") to your sources.list:

Edit /etc/apt/sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```Add these entries to the end of your sources.list file (if they do not already exist):
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
```[SIZE=1]
[/SIZE]

---

### Post by psyke83 on 2009-11-02
> **tony_chu said:**
> What am I supposed to enter in my sources.list when using Karmic? Is it supposed to be "ubuntu jaunty main"?

If you're using Karmic, you're not supposed to use this guide at all (with the possible exception of the part dealing with the fixmtrr.sh script). If you upgraded from Karmic, your PPA sources should have been disabled automatically - if not, you can simply erase the unwanted PPA lines in your /etc/apt/sources.list file.

---

### Post by StaRetji on 2009-11-02
> **ravi.xolve said:**
> [@StaRetji]("http://ubuntuforums.org/member.php?u=933732")

for flash update your plugin. it worked for me.

Did that a month ago, didn't help much...

Thx for the tip though, it may help to somebody else ;)

---

### Post by sparvik on 2009-11-04
I don't care about the acceleration performance as of now but since you seem to know a lot about the Intel video,  do you know how to get s-video out on a Intel 845g video card in either 9.04 or 9.10 or heck even 8.04?

---

### Post by Craig73 on 2009-11-04
> **sparvik said:**
> I don't care about the acceleration performance as of now but since you seem to know a lot about the Intel video,  do you know how to get s-video out on a Intel 845g video card in either 9.04 or 9.10 or heck even 8.04?

The current intel drivers do not (and as I understand it, there are no plans to) support TV-out (s-video) on older chipsets.  Intel does provide documentation for the community to implement the support themselves, should they so choose.

I believe the old i810 drivers did support TV-out (at least for the 855GME if I remember correctly), but those are not supported under current versions of Ubuntu.  (There was a PCI rework done in XOrg 1.6 that prevents these drivers from compiling;  I guess someone could re-write that part of the driver so they work again, should there be no other issues,  don't know the work involved.) 

One possible work-around here [http://sourceforge.net/projects/i810tvout/](http://sourceforge.net/projects/i810tvout/)
 (haven't tried it yet enough to comment on if it works, how difficult it is to use)

---

### Post by scummy on 2009-11-05
I did the reversion trick in Jaunty, and it fixed my GMA950 problems(this is in Xubuntu, by the way). After upgrading to Karmic, the problems came back (basically, simple games like World of Goo and GFCEU run terribly slowly. Video playback is fine, as far as I can tell). Is there something else I need to do to get my performance back? I don't want to fresh install until the next LTS.

---

### Post by StaRetji on 2009-11-06
I've noticed Mesa updates do not apply for Jaunty?
Why is that?

Is it safe to upgrade mesa manually?

Cheers...

---

### Post by sparvik on 2009-11-07
Thank you, 
> The current intel drivers do not (and as I understand it, there are no plans to) support TV-out (s-video) on older chipsets

I did find the info about the driver + xrandr not supporting the tv-out option several months back when I was trying with 8.04, but since I seen that pre 7.10 some people had succes I hoped at least one perrson might have made it work.  :(

I will try the lenny driver but I am not to hopeful.

---

### Post by scummy on 2009-11-09
weird, i tried installing xserver-xorg-video-intel, which i had wrongly assumed had been re-installed when i unreverted the jaunty fix and upgraded to karmic. world of goo now plays like a champ, and the problems i had with gfceu seem to be specific to gfceu, as fceu runs great.

---

### Post by ravi.xolve on 2009-11-10
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Above is the output of lspci for my Intel graphics. I upgraded from 9.04 to 9.10 . I didn't look at xorg.conf later and the graphics still worked good.

Today I just checked xorg.conf anf found the following lines still there which I had edited into xorg.conf for Device section in 9.04 :

> 
Driver          "intel"
        Option  "Accelmethod"   "UXA"
        VideoRam        258048

---

### Post by itoffshore on 2009-11-12
With optimal settings on:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I get 30-35 fps with pracer - I also had to add the following kernel setting :


[https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")

As a side note - skype 2.1 doesn't yet work under ALSA or pulse with intel mobile integrated boards - stick to Skype 2.0

---

### Post by jotie on 2009-11-12
I used this fix on Jaunty and it's working great. When I upgrade to Karmic Koala, the graphics is broken again. I manage to fix this by removing the fix from my Ubuntu installation. The revert process should be on the first post of this thread by psyke83.

Most people who upgrade from 9.04 to 9.10 will have no problem but that is not the case for me. I post the revert process on my blog credit for psyke83 [http://yonathanhalim.blogspot.com/2009/11/graphics-problem-after-upgrading-ubuntu.html]("http://yonathanhalim.blogspot.com/2009/11/graphics-problem-after-upgrading-ubuntu.html")

---

### Post by Sslaxx on 2009-11-15
After upgrading machine 2 to Karmic, the graphics resolution (i945) is limited to 1024x768 whereas previously it could support 1280x1024. Any ideas/workarounds for this? Not sure on performance issues yet, but as it's a secondary machine it's not terribly important.

---

### Post by tormod on 2009-11-15
> **Sslaxx said:**
> After upgrading machine 2 to Karmic, the graphics resolution (i945) is limited to 1024x768 whereas previously it could support 1280x1024. Any ideas/workarounds for this? Not sure on performance issues yet, but as it's a secondary machine it's not terribly important.
Maybe check that you are actually using the intel driver and not the VESA driver. Check both dmesg output and Xorg.0.log for resolution related messages.

---

### Post by Sslaxx on 2009-11-15
From /var/log/Xorg.0.log:```
(--) PCI:*(0:0:2:0) 8086:2772:1297:3140 Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfdf00000/524288, 0xd0000000/268435456, 0xfdf80000/262144, I/O @ 0x0000ff00/8
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel

(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 2.9.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
```

---

### Post by rob1015 on 2009-11-23
I'm having a problem. I have done the entire guide posted and it says my intel chip is accelerated by the UXA. I'm pretty sure that I did everything correct, but I still can't open a few apps that render 3D graphics. I downloaded and successfully installed the Frets on Fire and Neverball 3D games, and also Blender, but when I double click on the apps to open them from the menu nothing happens. Why? What do I do to correct this? I have an Intel 855GM graphics chip. And also, why is it that no drivers are found when I open the Hardware Drivers app? Any input would be appreciated. Thanks.

---

### Post by glaze on 2009-11-26
> **rob1015 said:**
> I downloaded and successfully installed the Frets on Fire and Neverball 3D games, and also Blender, but when I double click on the apps to open them from the menu nothing happens. Why? What do I do to correct this?

Try to launch the apps from terminal, so you can see any error messages.

---

### Post by tormod on 2009-11-26
> **rob1015 said:**
> And also, why is it that no drivers are found when I open the Hardware Drivers app? Any input would be appreciated. Thanks.

The Hardware Drivers is a stupid name because it is only for third-party, closed-source alternatives and such. If there's nothing there it is because all of your hardware is taken care of by the default, free software drivers.

---

### Post by StaRetji on 2009-11-27
I'm really not asking to much, just want h.264 flash videos to work.
Simple 640x480 streaming is unwatchable.
I even forced screen resolution to 640x480, it's a bit better, but still a lot tearing, vsync problem, videos lags.

Tried flash optimization recommendations, followed this performance guide.
It must be something we can tweak.

Any suggestion on how to make flash h.264 videos work is highly appreciated.

Cheers...

---

### Post by _mikec_ on 2009-11-27
how to install the graphics in Ubuntu Karmic 9.10 ?

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by tormod on 2009-11-27
> **_mikec_ said:**
> how to install the graphics in Ubuntu Karmic 9.10 ?
Why do you ask about this in a "Jaunty performance" thread? Anyway, there is no "graphics" to install for your card, it should be supported by the default, included drivers.

---

### Post by ticket on 2009-12-04
Can't seem to resolve this - does mtrr need to be set up for karmic, in the same manner as described here for Jaunty?

---

### Post by tomchiverton on 2009-12-04
resolve what ? this thread is jaunty-specific. karmic has none of the problems and runs fine out of the box on the same hardware.

---

### Post by gentracer on 2009-12-10
Hi,

I am very much a novice, but my system rebooting multiple times per day is absolutely driving me crazy.  I've read a lot of posts and yours was the best at telling me what to do.  I have implemented the series of steps in the 'safe' method, but the system crashed again just a few minutes ago.  I don't play games - just trying to get some work done..  I am running 9.04 and version 7 of Vmware with a Windows XP guest on a Dell Inspiron 1505 Intel GMA X4500HD that is less than 1 month old.  I did install an upgrade to adobe flash player today, but other posts make it sound like that is irrelevant.

Output from syslog just prior to the crash:
Dec 10 17:29:06  gdm[3149]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Dec 10 17:29:06  bonobo-activation-server (mgm-11786): could not associate with desktop session: Failed to connect to socket /tmp/dbus-OPkqOJX5vm: Connection refused
Dec 10 17:29:08  acpid: client 3153[0:0] has disconnected 
Dec 10 17:29:08  acpid: client connected from 11855[0:0] 
Dec 10 17:29:09  kernel: [ 6183.276620] [drm:i915_setparam] *ERROR* unknown parameter 4

Any help would be greatly appreciated!

Thank you.

---

### Post by pink_book7 on 2009-12-13
Hi

I thought I had followed the instructions correctly but something has gone wrong...

I have two kernels installed on my netbook, sickboy kernel, customised for my Acer Aspire One, and the standard generic kernel shipped with Jaunty.  The graphics now work fine under the sickboy kernel, but under the generic kernel the screen flickers occasionally and eventually goes blank forcing me to reboot.  Somehow I've managed to get a different configuration between the two kernels, the output of cat /proc/mtrr is quite different between the two.  Can anyone help me make the generic kernel stable again, I need it to use my 3G dongle.

Thanks

Sickboy kernel
```
claire@claire-laptop:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f500000 ( 1013MB), size=    1MB, count=1: uncachable
reg02: base=0x03f600000 ( 1014MB), size=    2MB, count=1: uncachable
reg03: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg04: base=0x040000000 ( 1024MB), size=  256MB, count=1: write-combining
```Generic kernel
```
claire@claire-laptop:~$ cat /proc/mtrr
reg00: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg01: base=0x0fffc0000 ( 4095MB), size=  128KB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg03: base=0x020000000 (  512MB), size=  512MB, count=1: write-back
reg04: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg05: base=0x03f600000 ( 1014MB), size=    2MB, count=1: uncachable
reg06: base=0x03f500000 ( 1013MB), size=    1MB, count=1: uncachable
reg07: base=0x000000000 (    0MB), size=  128KB, count=1: uncachable
```

---

### Post by Mike.lifeguard on 2009-12-14
> **tomchiverton said:**
> resolve what ? this thread is jaunty-specific. karmic has none of the problems and runs fine out of the box on the same hardware.

That's not true. I still get font corruption.

---

### Post by ryouji_shiki on 2009-12-27
> **Mike.lifeguard said:**
> That's not true. I still get font corruption.

And I still get this: [http://ubuntuforums.org/showthread.php?t=1331057](http://ubuntuforums.org/showthread.php?t=1331057)

---

### Post by Charkel on 2009-12-28
I have nothing in "Harware Drivers" and i got no xorg.conf and "sudo dpkg-reconfigure -phigh xserver-xorg" doesn't creat one :(

---

### Post by jpkotta on 2009-12-29
Great guide, worked for me on the first try (I chose optimal).  I have a few suggestions.  

I put the symlink to fixmtrr.sh in /etc/X11/Xsession.d, which should make it work regardless of the display manager you use.
```

sudo ln -sf /usr/local/bin/fixmtrr.sh /etc/X11/Xsession.d/99fixmtrr

```

Also, I recommend adding an Apt .list file like /etc/apt/sources.list.d/x-updates.list.  That way sources.list is always kept clean.

---

### Post by mfainter on 2009-12-29
Thank you so much!  I was about to throw my Ubuntu machine out the window after searching for intel drivers, and going through numerous lines of code in bash.  This thread got my display fixed!  Thank you again!

---

### Post by zonefull on 2010-01-03
hello thx alot for this thread it worked for me but there are some defeats 
well for me i got no sound anymore so anyway how can i resolve that ?

---

### Post by salttalk on 2010-01-24
My son and I are having trouble getting the graphics card to work properly in his computer. 

The resolution is good, but the graphics card is not fully functioning. He works on animation and graphics of several kinds, and the graphics programs cannot run without a fully functioning graphics card.

The computer will not run Blender and other graphics programs. Nor will it even allow for the "normal" "Visual Effects" in the "Appearance Preferences." (It comes up with the error: "Desktop effects could not be enabled," after it tries to find the driver.)

The system is:

[COLOR="Blue"]**Graphics Card:** nVidia G92, GeForce 8800 GT
**System:** Ubuntu 9.10 Karmic, 2.6.31-17-generic, 4.4.1 (x86_64-linux-gnu)
**Processor:** AMD Athlon 64 X2 Dual Core 4200+ (3 Gigs RAM)[/COLOR]

We know the graphics card works because it works in Windows. (We set up the computer to boot off of either of two hard drives -- either in Windows XP or Ubuntu 9.10, karmic.)

Neither my son nor I understand much of the terminology on your forums, although I have been using Ubuntu for some years and have read quite a bit. (I also have the "Beginning Ubuntu Linux" book.) I love Ubuntu, but sometimes I just cannot figure out how to get some things running.

We have tried many different ways of installing the drivers and setting up the xorg.conf file. We have followed the instructions on this and other threads. We also installed NVIDIA-Linux-x86-64-190.53-pkg2.run, as well as 173 and 185.

The screen will only work at a proper resolution when we set the "Driver" to "nv" in the xorg.conf file. The screen goes completely blank and dead if we set the "Driver" to "nvidia." Then we need to reboot in safe mode and edit the xorg.conf file with VIM.

When we set the driver to "nv," the Xorg log shows only this one error:

[COLOR="Blue"](EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)[/COLOR]

But when we set the driver to "nvidia," the Xorg log gave the following errors before the screen went dead:

[COLOR="Blue"](EE) Jan 20 16:04:32 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jan 20 16:04:32 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jan 20 16:04:32 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/COLOR]

I don't understand this because, with the "nvidia" setting, it says it successfully loads the driver:

[COLOR="Blue"](II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.18  Wed Jul 22 16:35:50 PDT 2009
(II) Loading extension GLX[/COLOR]

I have tried the "How to Install nVidia driver" thread and just about everything else I can find. Will this nVidia card even work on Karmic?

Thanks. Hope to hear from someone.

---

### Post by NT4usB on 2010-01-25
> **salttalk said:**
> My son and I are having trouble getting the graphics card to work properly in his computer....
The system is:

[COLOR="Blue"]**Graphics Card:** nVidia G92, GeForce 8800 GT
**System:** Ubuntu 9.10 Karmic, 2.6.31-17-generic, 4.4.1 (x86_64-linux-gnu)
**Processor:** AMD Athlon 64 X2 Dual Core 4200+ (3 Gigs RAM)[/COLOR]...

Probably have better luck starting a new thread since this one is all about Intel graphics and not Nvidia.

fwiw, I've had good luck using envyng for installing nvidia drivers.
It's in the repositories (for Jaunty anyway... don't know about Karmic)
Read about it [here.]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by salttalk on 2010-01-25
Hi. Thanks for your reply. I tried reinstalling EnvyNG and running it, but I had the same problem. After the EnvyNG installed, and I rebooted, the screen went dead. So I had to reboot in safe mode to reset the xorg.conf driver to "nv" again.

I guess I'll take your advice and start a new thread. Thanks again.

---

### Post by VirusCollector on 2010-02-02
Hey so I'm sorry if this has been repeated in this thread already... I didn't browse all 130-something pages, but what does this mean for Karmic? What kind of performance should I expect? Has this fix been included in Karmic?

Running an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) on Karmic (2.6.31-17-generic). 

I just recently installed updates from the xorg-edgers PPG and that made it sooo much better. I can exit games now without them just hanging, my Compiz Cube works seamlessly, and Youtube works a lot better too. But should I be expecting better?

---

### Post by Dreakon on 2010-02-03
Yeah, would this guide improve the desktop performance for my Intel GMA 4500HD in 9.10?  Right now, it's pretty sluggish opening folders and menu's and whatnot (and nothings eating up CPU or RAM).

---

### Post by Mularkey23 on 2010-02-07
it helped for me, but as far as intel goes i swear i had the best performance on hardy.  now im wishing i had created a /home partition before so i can get 3d graphics up to speed

---

### Post by night-wing on 2010-02-11
For me, this "how to" worked great! (when using the optimal/bleeding edge - version). EXA worked on my thinkpad x60, but the softmaker office - program isn't compatible with it, so I was forced to use uxa und there I could not play dvds or openarena. No I can - hurrah! :D

---

### Post by basilwatson on 2010-02-14
Hi all 

this is about my MSI Wind 100 u 

not the signature computer 

Anyway it seems to be working ok ( the graphics card that is )  my #d accl is ok you tube is ok 

but the screen flickers once in a while and SOMETIMES will shut down

its a little annoying 

I am running on 80 % cpu at the moment to see if it will help 

anyone else had this happen?

any ideas? 

Stephen 

here is my card and  cfconf

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 0110
        Flags: bus master, fast devsel, latency 0
        Memory at dfe00000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

snip  


#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

---

### Post by mrhippieguy on 2010-02-19
ah, so this is why my 3D work is going 350-650 fps slower than it used to. switching back to intrepid now. good thing this thread was here, i was going to post a new one just for this question.:roll:

---

### Post by foresthill on 2010-03-10
Could someone PLEASE update these instructions for 9.10 and 10.4. The ones on the first page are a complete waste of time in those two distros. Either that or take this thread down as a sticky.

I have been fighting with trying to get out of 1024 x 768 on an Intel GMA 500 netbook in both 9.10 and 10.4 for half a day now. There were some drivers on altervista.net that worked before but those have been taken down, and I have not been able to find anything that comes close to working.

---

### Post by psyke83 on 2010-03-10
> **foresthill said:**
> Could someone PLEASE update these instructions for 9.10 and 10.4. The ones on the first page are a complete waste of time in those two distros. Either that or take this thread down as a sticky.

I have been fighting with trying to get out of 1024 x 768 on an Intel GMA 500 netbook in both 9.10 and 10.4 for half a day now. There were some drivers on altervista.net that worked before but those have been taken down, and I have not been able to find anything that comes close to working.

No, this guide doesn't need to be updated for Karmic (or especially for Lucid, which is still in alpha status). The drivers shipped with Jaunty were unusually slow, which warranted this guide.

What I do agree on, however, is that the guide should be un-stickied (unless there's a larger base of Jaunty users still in existence than I imagine to be the case).

P.S. This guide is useless to you, anyway. Your GMA 500 is really a Imagination Industries PowerVR SGX 535 core, which does not have properly-maintained open-source drivers. See [here]("http://en.wikipedia.org/wiki/Intel_GMA#GMA_500") and [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo").

---

### Post by foresthill on 2010-03-10
> **psyke83 said:**
> No, this guide doesn't need to be updated for Karmic (or especially for Lucid, which is still in alpha status). The drivers shipped with Jaunty were unusually slow, which warranted this guide.

What I do agree on, however, is that the guide should be un-stickied (unless there's a larger base of Jaunty users still in existence than I imagine to be the case).

P.S. This guide is useless to you, anyway. Your GMA 500 is really a Imagination Industries PowerVR SGX 535 core, which does not have properly-maintained open-source drivers. See [here]("http://en.wikipedia.org/wiki/Intel_GMA#GMA_500") and [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo").

Thanks I will try that. Much appreciated, I thought i was losing my mind.

---

### Post by ericdano on 2010-04-03
Ok, I made the "mistake" of upgrading my MSI Atom computer with built in Intel graphics (945G I believe) to 10.04 beta 1. Now, it boots fine. All the server stuff works fine. But I can't get it to start Gnome or Xorg or anything. It hangs at the "Checking battery state..." thing.....

I tried installing the new kernel from the ppa mainline. I also put in the grub lines mentioned to enable the drivers (i915.modeset=1)

So.....any ideas on what to do to get some sort of Gnome or graphical interface working again?

---

### Post by WhiteHorse on 2010-04-03
> **ericdano said:**
> Ok, I made the "mistake" of upgrading my MSI Atom computer with built in Intel graphics (945G I believe) to 10.04 beta 1. Now, it boots fine. All the server stuff works fine. But I can't get it to start Gnome or Xorg or anything. It hangs at the "Checking battery state..." thing.....

I tried installing the new kernel from the ppa mainline. I also put in the grub lines mentioned to enable the drivers (i915.modeset=1)

So.....any ideas on what to do to get some sort of Gnome or graphical interface working again?

Same problem here. I re-installed from the cd which wipes all the config files but leaves all your home directories intact. Works perfect now. :)

---

### Post by psyke83 on 2010-04-04
> **ericdano said:**
> Ok, I made the "mistake" of upgrading my MSI Atom computer with built in Intel graphics (945G I believe) to 10.04 beta 1. Now, it boots fine. All the server stuff works fine. But I can't get it to start Gnome or Xorg or anything. It hangs at the "Checking battery state..." thing.....

I tried installing the new kernel from the ppa mainline. I also put in the grub lines mentioned to enable the drivers (i915.modeset=1)

So.....any ideas on what to do to get some sort of Gnome or graphical interface working again?

Discussion of Lucid issues belong in the [Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=377") forum.

---

### Post by e-San on 2010-04-11
I have read about 1/3 posts.

Ok, guys, but how to compare our performance?
Since glxgears is useless beacose, for example, we do use other cpu's on our platforms.

I've been wondering if my performance is good enougth and i do not know how to check this.

I get ~60FPS on compiz benchmark, 
I use spare drivers and my xorg.conf differs only for Tiling option (thanks!).
I use ubuntu 9.10 at the moment. On 9.04 I got ~120FPS with compiz benchmark.

My GPU: Intel GMA i915.

Regards.

BTW. I'll ask some questions.
```
san@eeepc:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg02: base=0x0d0000000 ( 3328MB), size=  256MB, count=2: write-combining
```
As far as i know, my i915 can use at last 128MB, why there is 256MB?
I own only 2GB of RAM memory. Does not he say that those 256MB's are registered on FOURTH GB?

----

Grand edit xD
> **scarf said:**
> WOW!

i notice a huge improvement with the 2.9.0 version!!  yeah!  my old laptop is finally performing like i was used to with intrepid!  in short, i think all problems are resolved!

i have the 82852/855GM and have followed the safe configuration.

with this new update:

- webpages are loading faster, nearly instantly again
- webpages are scrolling as fast as i want them to using the hyperscroll on my logitech mouse, and stopping on a dime (before there was so much lag, sometimes several seconds before the page view would catch up with me)
- scrolling in man pages (in gnome-terminal), openoffice, and evince is also working correctly again
- penguin racer now runs without turning my whole screen white!  i turned up all the settings and ran it at 1280x768, and i was getting 7-15 FPS.  i had to turn it down to 640x480 to get a significant improvement to 12-18 FPS

see this thread for my previous gtkperf results:
[http://ubuntuforums.org/showpost.php?p=7375827&postcount=616](http://ubuntuforums.org/showpost.php?p=7375827&postcount=616)

current results using same settings (1000 rounds and maximized):
```
GtkPerf 0.40 - Starting testing: Sat Oct 17 19:34:56 2009

GtkEntry - time:  0.93
GtkComboBox - time: 27.75
GtkComboBoxEntry - time: 18.74
GtkSpinButton - time:  4.73
GtkProgressBar - time:  8.09
GtkToggleButton - time:  5.12
GtkCheckButton - time:  4.04
GtkRadioButton - time:  7.88
GtkTextView - Add text - time: 165.50
GtkTextView - Scroll - time: 16.29
GtkDrawingArea - Lines - time: 47.55
GtkDrawingArea - Circles - time: 54.72
GtkDrawingArea - Text - time: 14.97
GtkDrawingArea - Pixbufs - time:  1.73
 --- 
Total time: 378.05
```

the "GtkTextView - Add text" test is still the (very) weak link.  why is it so slow to add text?

It seems that i have foud answer for my question.
My benchmark at 8bit (GreyScale, propably compiz refuzed to load, 100 repeat):
```
GtkPerf 0.40 - Starting testing: Mon Apr 12 19:25:31 2010

GtkEntry - time:  0,37
GtkComboBox - time: 14,64
GtkComboBoxEntry - time:  7,36
GtkSpinButton - time:  4,06
GtkProgressBar - time: 18,26
GtkToggleButton - time: 11,73
GtkCheckButton - time:  2,55
GtkRadioButton - time:  3,20
GtkTextView - Add text - time: 11,96
GtkTextView - Scroll - time:  5,16
GtkDrawingArea - Lines - time: 27,89
GtkDrawingArea - Circles - time: 39,91
GtkDrawingArea - Text - time: 61,39
GtkDrawingArea - Pixbufs - time:  8,39
 --- 
Total time: 216,90
```

Good?


----
On normal concdition
- 1000 repeat
- i915 o EEEPc (Pentium M 900MHz)
- 1024x600@60Hz
- maximized
- Ubuntu 9.10
```
GtkPerf 0.40 - Starting testing: Mon Apr 12 19:37:37 2010

GtkEntry - time:  4,27
GtkComboBox - time: 69,03
GtkComboBoxEntry - time: 53,78
GtkSpinButton - time: 20,61
GtkProgressBar - time: 15,96
GtkToggleButton - time: 15,46
GtkCheckButton - time:  9,58
GtkRadioButton - time: 14,50
GtkTextView - Add text - time: 344,45
GtkTextView - Scroll - time: 26,24
GtkDrawingArea - Lines - time: 113,30
GtkDrawingArea - Circles - time: 210,67
GtkDrawingArea - Text - time: 133,55
GtkDrawingArea - Pixbufs - time: 22,96
 --- 
Total time: 1054,41
```

Scarf's time seems to be very good or GtkPerf is not goot benchmark too.

ANOTHER BIG THING
> **relgames said:**
> Finally, I added the next lines to kernel boot options:
```
enable_mtrr_cleanup mtrr_chunk_size=256M mtrr_gran_size=256M
```

And after reboot /proc/mtrr looks like:
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg04: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg05: base=0x400000000 (16384MB), size=16384MB, count=1: write-back
reg06: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining

```

And Flash fullscreen video goes smoothly! So the problem is solved.

Yes, that's Linux way - spent a lot of time to solve issues that Windows users do not have at all :)

BTW, there is a bad effect also: now system detects only 3355 MB...

AWESOME (1000 repeat too):
```
GtkPerf 0.40 - Starting testing: Mon Apr 12 22:15:16 2010

GtkEntry - time:  1,75
GtkComboBox - time: 22,96
GtkComboBoxEntry - time: 18,09
GtkSpinButton - time:  7,02
GtkProgressBar - time:  6,90
GtkToggleButton - time:  7,11
GtkCheckButton - time:  5,14
GtkRadioButton - time:  6,83
GtkTextView - Add text - time: 202,53
GtkTextView - Scroll - time: 14,10
GtkDrawingArea - Lines - time: 64,35
GtkDrawingArea - Circles - time: 115,01
GtkDrawingArea - Text - time: 91,28
GtkDrawingArea - Pixbufs - time: 13,67
 --- 
Total time: 576,75
```

I removed mtrr script from first post.

Sorry for very long post, hope you do not mind. To complete information for you i have to add something more. Hope it help. Since now even 480p YT works good on full screen. Before this modyfications 360 was snappy.

```
san@eeepc:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x020000000 (  512MB), size=  256MB, count=1: write-back
reg02: base=0x030000000 (  768MB), size=  128MB, count=1: write-back
reg03: base=0x0d0000000 ( 3328MB), size=  256MB, count=2: write-combining

san@eeepc:~$ cat /proc/meminfo
MemTotal:         904628 kB
(...)
```

Seems that memory for OS is reg00:02, rest (128MB) is reserved for GPU (I set 128MB for mtrr in grub, since my gpu can not use more than this).

---

### Post by SaintDanBert on 2010-04-15
I have the Intel GM965/GM960 integrated graphics card in my laptop.
My existing /proc/mtrr shows five registers.
When I look at /proc/mtrr, it is owned by root and is owner writable.
The contents report as five registers:
```

reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x13c000000 ( 5056MB), size=   64MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg04: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg05: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable

```

The script does not designate a register. Does it need to?

When the script tries to write /proc/mtrr I get "permission denied".
When I try to write from the command line, I get the same thing.
YES, I do all of this using sudo for testing before I alter my boot.

Do I need specific driver editions or kernel editions before the script
will work properly? [NOTE -- If so, does it make sense for the script to check for these pre-requisits?]


Cheers,
~~~ 0;-Dan

---

### Post by e-San on 2010-04-16
[strike] "sudo echo 'text' > file" wont work, beacose 'sudo' works only for 'echo' command. you do '>' as regular user. find workaround for this. [/strike] forget it, i am bit tired ;)

reigames sugested (quoted in my post) to add "enable_mtrr_cleanup mtrr_chunk_size=256M mtrr_gran_size=256M" to your grub, kernel command line. it worked for me. find if 256M is for you (for i915 128M is enought).

---

### Post by K.Mandla on 2010-05-01
Unstickied at the author's request. ;)

---

### Post by pckid on 2010-05-07
can i do this then upgrade to lucid?

---

### Post by psyke83 on 2010-05-07
> **pckid said:**
> can i do this then upgrade to lucid?

Are you asking because you want to follow the guide, or because you already followed the guide? You can't upgrade from Jaunty -> Lucid, as it's not possible to skip distributions (well, you can upgrade between LTS releases, such as Hardy -> Lucid, but that doesn't apply to you).

If you've already followed this guide, and you're upgrading from Jaunty -> Karmic -> Lucid, you should be safe (though I wouldn't recommend to do that anyway, as there is quite some potential for breakage). As far as I understand, all PPA repositories will be disabled during the upgrade process.

If you haven't yet followed the guide, then it will give you absolutely no benefit to follow it (as the upgrade will overwrite the packages).

---

### Post by SaintDanBert on 2010-05-07
Folks,
   I'm really missing something because things are not making sense.
When I look at my /etc/X11/xorg.conf, I find the following
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
#++
# Enable CTRL+ALT+BACKSPACE to restart X-server
#--
Section "ServerFlags"
        Option  "DontZap" "false"
EndSection

#++
# All of the "generic" display and input sections
#--
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

# EOF -- /etc/X11/xorg.conf

```

I'm running a Thinkpad laptop with an Intel PM965/GM965 video.
I appreciate any help.

~~~ 0;-Dan

---

### Post by fktt on 2010-05-27
This may be a stupid question, but would this quide be of use on 10.04 with a gma 950?

ps. I'm running the acer apire one(AOA150) zg5.

---

### Post by WhiteHorse on 2010-05-27
> **fktt said:**
> This may be a stupid question, but would this quide be of use on 10.04 with a gma 950?

ps. I'm running the acer apire one(AOA150) zg5.

No, 10.04 has the latest kernel, DRM, and Intel drivers which fix the problems with 3D speeds. There is a more recent driver from intel which fixes a lot of speed issues but it may not be in the repos yet.

---

### Post by .zolder on 2010-07-11
Hello,

I've got me a "new" laptop which is a Dell Inspiron 1150 with an Intel 82852 gfx chip. I'm experiencing some problems with videoplayback (youtube 0.5 to 10 FPS). I've run both Gnome and XFCE, and turning on compositing works great.

I installed 10.04. At first I booted into a blank screen preventing me to do anything. Next I installing a CMI system and dpkg'ing another kernel before installing a GUI fixed that ([**thanks**](http://ubuntuforums.org/showpost.php?p=9236684&postcount=6)). I even got the proper resolution! Now I've got to get it's videoperformance up to par with 8.04.

I tried both Safe and Optimal config described in the topicstart but to no avail. Is there anything else i can do?

---

### Post by tormod on 2010-07-11
> **.zolder said:**
> I tried both Safe and Optimal config described in the topicstart but to no avail. Is there anything else i can do?
You noticed that the topicstart (and the whole thread) is about 9.04 and that you are using 10.04? And you read the last comment before your post?

---

### Post by .zolder on 2010-07-11
I did, but this topic was the only one that i could find that comes close to the problems I'm experiencing and actually supplies a possible fix. I also read that there IS a driver, but it doesn't come with this distro. As I understand things, there should be a way to load those..
edit: would [**this**](http://intellinuxgraphics.org/install.html) help for instance?

---

### Post by tormod on 2010-07-11
> **.zolder said:**
> I did, but this topic was the only one that i could find that comes close to the problems I'm experiencing and actually supplies a possible fix. I also read that there IS a driver, but it doesn't come with this distro. As I understand things, there should be a way to load those..
edit: would [**this**](http://intellinuxgraphics.org/install.html) help for instance?

You are allowed to start new threads :) If you run maverick + xorg-edgers you can be pretty sure you run the latest (and unreleased) versions of the driver. But that's stuff for another thread.

---

### Post by robb. on 2010-08-31
> **Charkel said:**
> i got no xorg.conf and "sudo dpkg-reconfigure -phigh xserver-xorg" doesn't create one :(

i had this problem, too.  i tried "sudo apt-get install xserver-xorg".  the response was that xserver was already installed and at the latest version.  however, once i tried "sudo dpkg-reconfigure -phigh xserver-xorg" again after that, it populated the file "xorg.conf.failsafe" in the X11 folder.  so i did "sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf" to copy the contents of xorg.conf.failsafe to a newly created xorg.conf.  now i am ready to follow the rest of the procedure.

robb.

---

### Post by nutznboltz on 2010-09-05
> **robb. said:**
> i had this problem, too.  i tried "sudo apt-get install xserver-xorg".  the response was that xserver was already installed and at the latest version.  however, once i tried "sudo dpkg-reconfigure -phigh xserver-xorg" again after that, it populated the file "xorg.conf.failsafe" in the X11 folder.  so i did "sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf" to copy the contents of xorg.conf.failsafe to a newly created xorg.conf.  now i am ready to follow the rest of the procedure.

robb.

For Lucid:

sudo service gdm stop
Press Alt-F1 and log in
sudo X -configure
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start

(note that you will still be logged on use Ctrl+Alt+F1 and log out then Ctrl+Alt+F7)

---

### Post by averlon on 2010-09-05
> **j0hn00 said:**
> it's actually
 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
 
Hi,
I am new on Ubuntu.
Tried the command since on my installation also no xorg.conf does not exist.
 
No error messages but also no xorg.conf.
 
Kind regards
Karl-Heinz

---

### Post by SaintDanBert on 2010-09-18
On my laptop, **lspic** reports
```

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

[highlight]Q1:[/highlight] How do I discover which hardware and software features are supported by this card?

[highlight]Q2:[/highlight] How do I discover what are the problems with this card and drivers?

[highlight]Q3:[/highlight] How do I discover the land mines in a manual kernel update -- one not provided through update-manager?
I'd like to move to the 2.6.30 kernel. (Jaunty updates seem to stall at 2.6.28-19.)

On the useful side, I approach PPA additions a little differently.
You can put small separate files in **/etc/apt/sources.list.d/** instead of editing the main file in **/etc/apt/sources.list** itself.
For this posting, I created a file called "X-updates.list" with the following contents"
```

#++
#  TITLE:  X-upates.list
#
#  DESCRIPTION:
#    PPA access to X-11 and Xorg updates
#
#  PROGRAMMER NOTES:
#  1.  security (Ubuntu Jaunty)
#        $ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
#        $ sudo apt-get update
#        $ sudo apt-get dist-upgrade
#--

#=== name the repositories
deb     http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main      #X-Updates PPA
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main      #X-Updates PPA

# EOF -- X-updates.list

```

When package manager runs, it scans /etc/apt/sources.list (the file) and then /etc/apt/sources.list.d/*.list (the folder & contents). It becomes trivial to find and manage individual repository changes by
managing these files.  Also, after an update, one needs to move these files to the next workstation and edit {ubuntu edition} to use the newest codename (jaunty, Lucid, etc).

Merci d'avance,
~~~ 0;-Dan

---

### Post by lithopsian on 2010-12-16
Is gtkperf a meaningful benchmark?  I think I have my Intel 865G finally working sensibly if not perfectly, after finding and removing some symlinks to old nVidia drivers.  At least full screen video now displays without breaking up.  I still can't set UXA without X crashing, so maybe there is more improvement to come.

100 iterations:
```
GtkPerf 0.40 - Starting testing: Thu Dec 16 19:01:53 2010

GtkEntry - time:  0.16
GtkComboBox - time:  1.87
GtkComboBoxEntry - time:  1.59
GtkSpinButton - time:  0.41
GtkProgressBar - time:  0.20
GtkToggleButton - time:  0.35
GtkCheckButton - time:  0.24
GtkRadioButton - time:  0.92
GtkTextView - Add text - time:  1.27
GtkTextView - Scroll - time:  0.53
GtkDrawingArea - Lines - time:  1.67
GtkDrawingArea - Circles - time:  1.41
GtkDrawingArea - Text - time:  4.47
GtkDrawingArea - Pixbufs - time:  0.62
 --- 
Total time: 15.73

```

No MTRR problems here, so presumably this has been fixed.  I have the Mesa 7.4 drivers and a custom built 2.6.30 kernel.

Seems pretty fast to me.  Maybe it is just testing 2D stuff that the Intel chips can do OK?  I did notice that the test maxed my CeleronD 2.8 CPU.  Not sure if that is the software direct renderer or just gtkperf itself.  I made a comparison with an nVidia 5200FX on a much slower CPU (400MHz Pentium II!) and it was 5-6 times slower.

---

### Post by lithopsian on 2010-12-17
In a strange twist, I ran the test using an nVidia driver with the Intel video chip.  Actually the libGL library from nVidia got symlinked by mistake.  CPU was virtually untouched during the test but it took about twice as long as with the correct driver.  Amazing that it worked at all really!  I guess it bypassed the software rendering and somehow libGL made enough of the right calls to make things happen on the card.

---

### Post by lithopsian on 2010-12-24
I finally found a stable fast configuration.  Penguin Racer is now 20-40fps instead of 2!  3D is obviously only so-so but 2D is great.  Full screen HD video runs smooth with Xvideo which didn't work at all before.

Still Jaunty, but with a custom kernel built from 2.6.30.10 source.   And maybe a patch?  I applied [a patch]("http://lists.freedesktop.org/archives/intel-gfx/2009-September/004122.html") that might have had an affect.  The exact same config with 2.6.30 is unstable.  xorg Intel drivers 2.9.0.  libdrm 2.4.14, Mesa 7.4.  Kernel drivers are built in, but I also tested with them as modules.  i915 selected for drm, mode setting not compiled in, nomodeset also specified.  Framebuffer is obviously enabled, but the intelfb module is not being used so far as I can see.  xorg.conf options: Tiling &quot;true&quot; is maybe the default anyway? UXA is not specified in xorg.conf since it is the only method in the 2.9 driver.

The UXA acceleration, and so obviously the 2.9 driver, uses dramatically less memory since the EXA method grabs a whole chunk of memory when X starts because it isn't good at allocating it dynamically.  For the first time you might actually say I'm happy with this graphics chip.  This is far from the latest driver, but I think it's as far as I can easily go with Jaunty.  Maybe it will help someone else to improve their graphics.

---

### Post by DarkTide on 2011-04-07
I formatted and installed 8.10.  Game's working again.  Sad that Jaunty  was released and crippled intel's already poor 3d graphics.  I tried  both rc2 and rc3 kernels.  And a few different "fixes" from this thread.   I've installed the latest version of Ubuntu each time they release one  since 6.04.

---

### Post by JohnBonne on 2011-05-23
Streaming instructions. Most lights are green. I have to test moe and continue my unending search for tweaks. 

Bravo Ubuntu!

---

