---
title: "Can't Dial-Up With ThinkPad in Pangolin with Gnome-PPP"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by jimwg on 2013-07-17
Greetings:

I have a third-hand hand-me-down Thinkpad R60e whose internal modem works well on dial-up (via FreeDialUp and Juno) when running on its hard drive's Windows XP, but I can't achieve dial-up when I run the laptop with Pangolin installed on a flash drive with Gnome-PPP. All I get is a pop-up box stating "Connecting...cannot open modem." When I used 'Detect' it states "No modem was found on your system."

In Set-Up I have
```

Device: /dev/modem
Type: Analog modem
Speed 460800
Phoine: Tone
IP Dynamic IP Address
Ignore Terminal Strings
Check Default Route
Abort Connecting if No Dialtone
Auto reconnect

```
Skimming Ubuntu sites, I was instructed to use scanMode, and the results are below:
```

Only plain text email is forwarded by the [email]Discuss@Linmodems.org[/email] List Server,
as HTML can contain viruses. Use as the email Subject Line:
YourName, YourCountry Linux Mint 13 Maya kernel 3.2.0-23-generic
With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
YourCountry will enable Country specific guidance. Linux experts in YourCountry
can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org)
-------------------------- System information ----------------------------
CPU=i686, Linux , ALSA_version=1.0.24
Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012
scanModem update of: 2010_05_29

Distrib_ID=LinuxMint
DistribCodeName=maya


The dkms driver upgrade utilities are installed,

There are no blacklisted modem drivers in /etc/modprobe* files

Potentially useful modem drivers now loaded are:
snd_hda_intel

Attached USB devices are:
ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
ID 047d:104b Kensington
ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is: [http://linmodems.technion.ac.il/bigarch](http://linmodems.technion.ac.il/bigarch) ... 00578.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

Candidate PCI devices with modem chips are:
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
High Definition Audio cards can host modem chips.

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
PCI slot PCI ID SubsystemID Name
---------- --------- --------- --------------
00:1b.0 8086:27d8 17aa:2010 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller

Modem interrupt assignment and sharing:
45: 451 0 PCI-MSI-edge snd_hda_intel
--- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[ 0.290137] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[ 0.290169] pci 0000:00:1b.0: reg 10: [mem 0xee240000-0xee243fff 64bit]
[ 0.290307] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.290317] pci 0000:00:1b.0: PME# disabled
[ 76.945480] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 76.945552] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[ 76.945592] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[10123.808241] snd_hda_intel 0000:00:1b.0: PCI INT B disabled
[10123.824133] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 119.748 msecs
[10124.412460] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
[10124.455999] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[10124.456567] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[10124.456623] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X

The PCI slot 00:1b.0 of the modem card may be disabled early in
a bootup process, but then enabled later. If modem drivers load
but the modem is not responsive, read DOCs/Bootup.txt about possible fixes.
Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
if help is needed.



===== Advanced Linux Sound Architecture (ALSA) diagnostics =====
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The modem cards detected by "aplay -l" are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
00-01: AD198x Digital : AD198x Digital : playback 1

about /proc/asound/cards:
------------------------
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xee240000 irq 45
29 [ThinkPadEC ]: ThinkPad EC - ThinkPad Console Audio Control
ThinkPad Console Audio Control at EC reg 0x30, fw 7EHT15WW-1.07

PCI slot 00:1b.0 has a High Definition Audio Card
The drivers are in the kernel modules tree at:
/lib/modules/3.2.0-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko

The HDA diagnostics did not recognize a modem chip on the audio subsystem,
though a Conexant chip modem might not be recognized.

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
Modem chipset detected on
NAME="Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=17aa:2010
IRQ=45
HDA2=00:1b.0
SOFT=8086:27d8.HDA
ArchivedChip=0x14f12bfa
CodecClass=14f1
IDENT=hsfmodem
Driver=hsfmodem-drivers

For candidate modem in: 00:1b.0
0403 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller
Primary device ID: 8086:27d8
Subsystem PCI_id 17aa:2010
Softmodem codec or chipset from diagnostics:
from Archives: 0x14f12bfa



Support type needed or chipset: hsfmodem


Writing DOCs/Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt


For all code packages from Linuxant.com, either a driver set matching the boot kernel will be installed,
or the drivers will first be compiled and then installed. The expert on modem software for Linux is
"Support (Jonathan)" <modem.support@linuxant.com>

Start at [http://www.linuxant.com/drivers/hsf/full](http://www.linuxant.com/drivers/hsf/full) for
eventually download of a hsfmodem-7.68.00.12full_k.???.zip package
with ??? the package type (deb, rpm, tar etc)
These packages have compiled drivers but will also compile a driver,
if there is a mismatch between the resident kernel and provided driver.
The generic hsfmodem-7.68.00.12full.tar.gz package only provides compiling support


Start at [http://www.linuxant.com/drivers/hsf/dow](http://www.linuxant.com/drivers/hsf/dow) ... icense.php to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion: 3.2.0_23_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, the needed drivers
will be auto compiled anyway. Alternatively, one of the
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
dpkg -i hsf*.deb
while for .rpm suffix it is, with:
rpm -i hsf*.rpm
Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


Completed candidate modem analyses.

The base of the UDEV device file system is: /dev/.udev

Versions adequately match for the compiler installed: 4.6.3
and the compiler used in kernel assembly: 4.6

linux-headers-3.2.0-23-generic resources needed for compiling are not manifestly ready!

If compiling is necessary packages must be installed, providing:
kernel-source-3.2.0-23-generic


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$ apt-get update
$ apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
-rwsr-xr-- 1 root dip 273272 Feb 4 2011 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
[http://linmodems.technion.ac.il/linmode](http://linmodems.technion.ac.il/linmode) ... 02637.html

To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
chmod a+x /usr/sbin/pppd

Checking settings of: /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch](http://linmodems.technion.ac.il/bigarch) ... 04656.html

For guidance on FAX usage, get from [http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/) get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0
Which can interfere with Browser naviagation.

Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

Checking for modem support lines:
--------------------------------------
/device/modem symbolic link:
slmodemd created symbolic link /dev/ttySL0:
Within /etc/udev/ files:

Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
Within any ancient /etc/devfs files:

Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

Any assist to help me get Pangolin up and running on dial-up which is my system's emergency internet mode will greatly appreciated! The assorted solutions and hints plastered all over Ubuntu sites are a confusing mess for us non-techies!

Thanks!

Jim in NYC

---

### Post by Irihapeti on 2013-07-17
Please user ```

``` tags when displaying code or error/output messages. It makes them easier to read.


On the topic of your question, the Linuxant drivers used to work very nicely on earlier versions of the kernel, but since vers. 3.0 have apparently required various bits of compiling to get to work. Like you, I tried tracking it all down and failed.

It might even be that you'd be better off using a distro that uses the vers. 2 kernel, such as centOS.

---

