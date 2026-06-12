---
title: "Fiesty - Intel High Definiton Audio/Realtek - No sound from on Travelmate 3275WXMi"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by veeraa on 2007-08-26
I've a acer 3275WXMi Travelmate with Fiesty. I upgraded recently from edgy. With both, sound has never worked. Although everything works out of the box, even the acer function keys are working.But no sound either from Intel HDA(ALSA) or Realtek(OSS). Both the devices are detected but dmidecode says

[I]Handle 0x000C, DMI type 10, 6 bytes
On Board Device Information
        Type: Sound
        Status: Disabled
        Description: HD-Audio
[/I]

I've used alsa mixer and Gnome Volume control to unmute and set the volume to maximum but to avail. Everything from 3d acceleration to wifi  works except for sound. Please help me guys. I on't wanna change to another distrib  just for sound. Apart from this issue Ubuntu really rocks.

---

### Post by veeraa on 2007-08-26
My lspci output

[I]veera@veera-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/I]

lshw says:
[I]veera@veera-laptop:~$ sudo lshw -class sound
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: iomemory:d2500000-d2503fff irq:22[/I]

---

### Post by ddrichardson on 2007-08-26
There are several things you can try - but you may be unlucky as some of the 2nd revision cards are still not working.

Other distros have the same problem.

First check all the options are available for unmuting - by ticking them all from the volume control's preferences - there are two configurations that require either the mic turned off or the surround sound turned on.

Second check dmesg for any reference to "unable to allocate XXXX.XX midi" - if you have this then you're stuck.

Next, you can append options to /etc/alsa-base, there is an acer option - which I can't remember  off hand.

Next try downloading and compiling the latest version of alsa - 1.0.14a.

There is a huge howto on the forums regarding sound and it's the best [place ]("http://ubuntuforums.org/showthread.php?t=205449&highlight=intel+hda+sound")to start.

---

### Post by veeraa on 2007-08-26
Thanks ddrichardson. I'll try the same. It seems to be the 2nd revision firmware as per lspci's output. I'll continue invesigating.

---

