---
title: "Only 800x600 in Lucid"
date: 2010-05-23
forum: Multimedia Software
---

### Post by The-REV on 2010-05-23
Folks, want help on video problem. I was running just fine my Karmic and upgraded to Lucid. All appears O.K. But after reboot all applications started appears minimized at left, top, without decoration. I tried all tips found in forums and nothing! Then I formatted my HDD, installed Lucid by CD and the same problem occurs. I returned to Karmic, installed VMWare, tried both Lucid and Isadora Linux Mint on VMW Workstation and the problem cannot be solved. I was thinking that the problem is a metacity bug:  but no - the problem is the video resolution.  I'm using a Gigabyte mobo with onboard videocard and all other OS installed here runs just fine in all video resolutions.
Entering <compiz replace> and <metacity --replace>  I found a error messages as follows:
macarlo@macarlo-desktop ~/Desktop $ compiz --replace
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted
macarlo@macarlo-desktop ~/Desktop $

macarlo@macarlo-desktop ~/Desktop $ metacity --replace
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)

After these steps I discovered that te problem is: my videocard for Lucid only support 800x600 and I've reconfigured to 1200x1024...

My videocard spec:
*-display
description: VGA compatible controller
product: 82G33/G31 Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 10
width: 32 bits
clock: 33MHz
capabilities: msi pm bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:27 memory:e1200000-e127ffff ioport:e000(size= memory:d0000000-dfffffff(prefetchable) memory:e1000000-e10fffff

Karmic, Jaunty etc and all other OS runs fine in all resolutions with this Intel onboard videocard but Lucid not. Only in 800x600 windows manager runs normally. Purge nvidia and reinstall nvidia current does not solve the problem. How can I do to fix this?! Can anyone in this forum help me?

---

### Post by oldfred on 2010-05-23
Check the intel info, I had nvidia:

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line


if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by The-REV on 2010-05-23
[QUOTE=oldfred;9349071]Check the intel info, I had nvidia: (...)

Thanx for this tut!!

---

