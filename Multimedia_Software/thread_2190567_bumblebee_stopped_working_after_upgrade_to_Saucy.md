---
title: "bumblebee stopped working after upgrade to Saucy"
date: 2013-11-27
forum: Multimedia Software
---

### Post by king.knut on 2013-11-27
On my brandnew "Acer Aspire ASPIRE TIMELINEU M5-481TG-53314G52MASS - 14" Notebook - Core I5" I installed Kubuntu 13.04 about 3 month ago. Every thing worked like a charm and I even got the nvidia card working using bumblebee. That actually was pretty easy. I just added the ppa's and followed instructions in [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee").

Recently I upgraded to Saucy and all of a sudden bumblebee doesn't work anymore. Starting optirun I get following error message:

```
knut@knubuntu:~$ optirun glxgears

[ 3961.272545] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[ 3961.272621] [ERROR]Aborting because fallback start is disabled.

```
A little search in google and various forums showed, that other users had similar problems but obviously caused by different reasons. Neither editing the bumblebee.conf nor reinstalling all the bumblebee and nvidia packeges helped.

Running some tests to find out what hardware exactly is in my computer and which software is running I got the notion that obviously no nvidia kernel modules are being loaded:

```
knut@knubuntu:~$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Kernel driver in use: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M LE] (rev a1) (prog-if 00 [VGA controller])
```

Trying to start it manually I get following error message:

```
knut@knubuntu:~$ sudo modprobe nvidia-304

ERROR: could not insert 'nvidia_304': No such device
```

And in the kern.log I find this:

```
Nov 28 04:42:02 knubuntu kernel: [  680.610305] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=none
Nov 28 04:42:02 knubuntu kernel: [  680.610339] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:0fd3)
Nov 28 04:42:02 knubuntu kernel: [  680.610339] NVRM: installed in this system is not supported by the 304.88
Nov 28 04:42:02 knubuntu kernel: [  680.610339] NVRM: NVIDIA Linux driver release.  Please see 'Appendix
Nov 28 04:42:02 knubuntu kernel: [  680.610339] NVRM: A - Supported NVIDIA GPU Products' in this release's
Nov 28 04:42:02 knubuntu kernel: [  680.610339] NVRM: README, available on the Linux driver download page
Nov 28 04:42:02 knubuntu kernel: [  680.610339] NVRM: at www.nvidia.com.
Nov 28 04:42:02 knubuntu kernel: [  680.610373] nvidia: probe of 0000:01:00.0 failed with error -1
Nov 28 04:42:02 knubuntu kernel: [  680.610396] NVRM: The NVIDIA probe routine failed for 1 device(s).
Nov 28 04:42:02 knubuntu kernel: [  680.610397] NVRM: None of the NVIDIA graphics adapters were initialized!

```

Can this be the reason why bumblebee fails?

And why does the nvidia-304 driver not support my GeForce GT 640M LE as stated in its description?

Right now I'm running kernel 3.11.0-13-generic and nvidia-304.88. And I have set graphic to switchable In BIOS.

Would be grateful for any help fixing the problem.

Knut

---

### Post by king.knut on 2013-11-27
**Update:**

Just rebooted the the system and tried again. Couldn't get optirum working but after running it once I at least could get the nvidia kernel-module installed.

```
knut@knubuntu:~$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Kernel driver in use: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M LE] (rev ff) (prog-if ff)

knut@knubuntu:~$ optirun -b primus glxgears
[  383.137556] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  383.137631] [ERROR]Aborting because fallback start is disabled.

knut@knubuntu:~$ sudo modprobe nvidia-304
[sudo] password for knut: 

knut@knubuntu:~$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Kernel driver in use: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M LE] (rev ff) (prog-if ff)
        Kernel driver in use: nvidia

knut@knubuntu:~$ optirun -b primus glxgears
[  456.649002] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  456.649096] [ERROR]Aborting because fallback start is disabled.

knut@knubuntu:~$ primusrun glxgears 
primus: fatal: Bumblebee daemon reported: error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

```

The kern.log reads like that:

```

Nov 28 05:12:29 knubuntu kernel: [  377.794550] bbswitch: enabling discrete graphics
Nov 28 05:12:29 knubuntu kernel: [  377.859782] pci 0000:01:00.0: power state changed by ACPI to D0
Nov 28 05:12:29 knubuntu kernel: [  377.916775] nvidia: module license 'NVIDIA' taints kernel.
Nov 28 05:12:29 knubuntu kernel: [  377.916779] Disabling lock debugging due to kernel taint
Nov 28 05:12:29 knubuntu kernel: [  377.924240] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Nov 28 05:12:29 knubuntu kernel: [  377.924323] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
Nov 28 05:12:29 knubuntu kernel: [  378.196159] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:29 knubuntu kernel: [  378.196198] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:29 knubuntu kernel: [  378.196217] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:29 knubuntu kernel: [  378.196248] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:29 knubuntu kernel: [  378.196266] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:29 knubuntu kernel: [  378.196284] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:29 knubuntu kernel: [  378.196322] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.708185] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Nov 28 05:12:36 knubuntu kernel: [  384.708195] NVRM: os_pci_init_handle: invalid context!
Nov 28 05:12:36 knubuntu kernel: [  384.708198] NVRM: os_pci_init_handle: invalid context!
Nov 28 05:12:36 knubuntu kernel: [  384.708203] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Nov 28 05:12:36 knubuntu kernel: [  384.708207] NVRM: os_pci_init_handle: invalid context!
Nov 28 05:12:36 knubuntu kernel: [  384.708208] NVRM: os_pci_init_handle: invalid context!
Nov 28 05:12:36 knubuntu kernel: [  384.759614] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.759758] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.759854] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.759943] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760030] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760117] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760203] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760289] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760375] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760461] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760547] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760634] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760720] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760809] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760895] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.760981] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.761067] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.761291] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.761538] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.761777] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.762012] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.762256] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.762496] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
Nov 28 05:12:36 knubuntu kernel: [  384.772349] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1200)
Nov 28 05:12:36 knubuntu kernel: [  384.772372] NVRM: rm_init_adapter(0) failed
Nov 28 05:13:49 knubuntu kernel: [  458.360709] bbswitch: enabling discrete graphics
Nov 28 05:14:09 knubuntu kernel: [  478.435789] bbswitch: enabling discrete graphics
Nov 28 05:14:09 knubuntu kernel: [  478.435820] nvidia 0000:01:00.0: power state changed by ACPI to D0
Nov 28 05:14:09 knubuntu kernel: [  478.451301] nvidia 0000:01:00.0: Refused to change power state, currently in D3

```

Any clue what that means? BTW, before reboot I went into BIOS and switched graphics from "switchable" to "integrated" and back before saving settings.

Cheers

Knut

---

### Post by Linuxisfast on 2013-11-27
Bumblebee is now in software center so I suggest you purge remove nvidia and bumblebee as well as remove bumblebee ppa and then do a reinstall with nvidia-319-updates, linux-headers-generic, bumblebee and bumblebee-nvidia

---

### Post by king.knut on 2013-11-28
@Linuxisfast Thanks for your reply.

The ppa's of course were disabled during system upgrade. And as I afore mentioned I reinstalled - means purged and installed anew - all the stuff, bumblebee, bumblebee-nvidia, bbswitch and the nvidia packages including primus. Even tried to install nvidia-319 and the updates modules. Nothing helped. Always the same error messages.

---

### Post by king.knut on 2014-01-19
This is not a solution but maybe a hint that might help to fix the bug. To me it looks like a kernel issue. Recently I installed Chakra Linux on the same machine and Bumblebee works like a charm, as it used to under Raring. Chakra uses kernel 3.12.6-1-CHAKRA. Bumblebee is 3.2.1-1 and the nvidia driver is nvidia-bumblebee 331.20-1. Maybe updating the nvidia driver helps. But I tried that already and 331.20 wasn't in the repositories anyway. So I guess one has to be pacient and wait until more up-to-date kernel and/or nvidia driver find their way into the repositories.

---

