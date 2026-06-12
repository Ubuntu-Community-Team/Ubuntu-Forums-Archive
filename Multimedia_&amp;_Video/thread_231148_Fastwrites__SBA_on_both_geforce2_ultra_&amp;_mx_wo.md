---
title: "Fastwrites / SBA on both geforce2 ultra &amp; mx won't work - WHY?"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by videodrome on 2006-08-07
I am so confused. Please help me to not kill my computers tonight.

Ok. Two different computers. No SBA or fastwrites no matter what I do on either machine. What am I doing wrong?

Computer #1: Dell Optiplex gx260, nvidia geforce2 ultra. Legacy drivers installed. Runs good, 2100 glxgears, but...

```
loomis@p4-2ghz:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     PCI device 8086:2560
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x00000104
```
```

loomis@p4-2ghz:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
```

```
loomis@p4-2ghz:~$ dmesg | grep NVIDIA
[17179589.668000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.672000] NVRM: The NVIDIA GeForce2 Ultra GPU installed in this system is
[17179589.672000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[17179589.672000] NVRM:  information.  The 1.0-8762 NVIDIA driver will ignore
[17179589.672000] NVRM: No NVIDIA graphics adapter found!
[17179589.756000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174 
```
No idea about above. Normal?

```

sudo nano /etc/X11/xorg.conf
Section "Device"
        Identifier      "NVIDIA Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"                 "1"
EndSection

```

I also blacklisted intel_agp in modprobe.d blacklist to disable agpgart

added
```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

to etc/modules, etc/modprobe.d/nvidia-kernel-nkc, and even created etc/modprobe.d/nvidia and added there. No luck!

Computer #2 is an athlon 1300 with the via_agp blacklisted, and has a geforce2 MX 440 and uses the regular geforce drivers. This machine can't get its SBA or FW working either.

This machine also locks up a few times a day with the agpgart loaded *I think*.

Why? Thanks

---

### Post by tseliot on 2006-08-07
> **videodrome said:**
> Computer #1: Dell Optiplex gx260, nvidia geforce2 ultra. Legacy drivers installed. Runs good, 2100 glxgears, but...

No idea about above. Normal?
Yes, it's ok.

> **videodrome said:**
> Computer #2 is an athlon 1300 with the via_agp blacklisted, and has a geforce2 MX 440 and uses the regular geforce drivers. This machine can't get its SBA or FW working either.

This machine also locks up a few times a day with the agpgart loaded *I think*.

Why? Thanks

Does your 2nd computer have an integrated card (in addition to the NVidia card?

---

### Post by videodrome on 2006-08-08
I'll check that soon. The first one has it turned off and has the newest mobo bios (A09).

Thanks

---

