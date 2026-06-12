---
title: "Radeon driver causing overheat, powersave modes?"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Noz3001 on 2010-09-06
I'm currently using Maverick beta and due to the lack of a functioning fglrx build from ATI, I've had to stick with the open source radeon driver. The only problem with this is that it runs the graphics card in performance mode at all times, causing the laptop to overheat and shutdown.

Does anyone know whether the radeon driver has any powersave mode parameters?

Here's the output of lsmod:
```
nathan@GLaDOS:~$ lsmod | grep radeon
radeon                906034  3 
ttm                    68180  1 radeon
drm_kms_helper         32836  1 radeon
drm                   206449  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
```modinfo on the loaded radeon driver:
```
depends:        drm,drm_kms_helper,ttm,i2c-algo-bit
vermagic:       2.6.35-19-generic SMP mod_unload modversions 
parm:           no_wb:Disable AGP writeback for scratch registers (int)
parm:           modeset:Disable/Enable modesetting (int)
parm:           dynclks:Disable/Enable dynamic clocks (int)
parm:           r4xx_atom:Enable ATOMBIOS modesetting for R4xx (int)
parm:           vramlimit:Restrict VRAM for testing (int)
parm:           agpmode:AGP Mode (-1 == PCI) (int)
parm:           gartsize:Size of PCIE/IGP gart to setup in megabytes (32,64, etc)
 (int)
parm:           benchmark:Run benchmark (int)
parm:           test:Run tests (int)
parm:           connector_table:Force connector table (int)
parm:           tv:TV enable (0 = disable) (int)
parm:           new_pll:Select new PLL code (int)
parm:           audio:Audio enable (0 = disable) (int)
parm:           disp_priority:Display Priority (0 = auto, 1 = normal, 2 = high) (int)
parm:           hw_i2c:hw i2c engine enable (0 = disable) (int)
```Thanks

---

### Post by Mark Phelps on 2010-09-06
Questions about the Betas do not belong in this forum.  This forum is for released versions of Ubuntu only.

Questions about the Betas are to be posted in the appropriate Development forum.

I'll be asking the Mods to move it there.

In future, post in the proper forums.

---

### Post by Jim March on 2010-09-07
You don't mention which ATI chipset you have.

I'm running an older ATI chipset, the X1700 (actually the FireGL V5250 variant of that) that only has open-source support, and it's fast, rock-solid and no signs of overheating.  I would go back to Lucid if you have an ATI card that is supported by their closed-source driver, at least for now.

---

### Post by Noz3001 on 2010-09-07
> **Mark Phelps said:**
> Questions about the Betas do not belong in this forum.  This forum is for released versions of Ubuntu only.

Questions about the Betas are to be posted in the appropriate Development forum.

I'll be asking the Mods to move it there.

In future, post in the proper forums.

It's not a question about the beta, it's about the radeon driver which is avaliable for all linux distributions so please do us all a favor and don't act like an elitist ****. Also, I've got it sorted.

I've used "options radeon dynclks=1" instead of "radeon.dynclks=1" in /etc/modprobe.d/radeon-kms.conf and everything is fine

---

### Post by antiram on 2010-09-08
read this post or thread
[http://www.phoronix.com/forums/showthread.php?p=145320#post145320](http://www.phoronix.com/forums/showthread.php?p=145320#post145320)

power_method is "dynpm" or "profile". "dynpm" reclocks automatically.
if you use "profile" then you can switch power_profile to "high", "mid", "low" or "auto". "auto" is for laptops and switch automatically to "low" for battery mode and "high" for  power supply mode.

---

### Post by Noz3001 on 2010-09-08
> **antiram said:**
> read this post or thread
[http://www.phoronix.com/forums/showthread.php?p=145320#post145320](http://www.phoronix.com/forums/showthread.php?p=145320#post145320)

power_method is "dynpm" or "profile". "dynpm" reclocks automatically.
if you use "profile" then you can switch power_profile to "high", "mid", "low" or "auto". "auto" is for laptops and switch automatically to "low" for battery mode and "high" for  power supply mode.

The directories and files are not the same on my system for some strange reason.

---

### Post by Untitled_No4 on 2010-09-08
[http://ubuntuforums.org/showpost.php?p=9752589&postcount=647](http://ubuntuforums.org/showpost.php?p=9752589&postcount=647)

---

### Post by Noz3001 on 2010-09-08
> **Untitled_No4 said:**
> [http://ubuntuforums.org/showpost.php?p=9752589&postcount=647](http://ubuntuforums.org/showpost.php?p=9752589&postcount=647)

Yeah, those files don't exist

---

### Post by antiram on 2010-09-08
maybe
mkdir /sys
mount -t sysfs sysfs /sys

or so, or do you use the old use mode setting?
then add to /etc/X11/xorg.conf some options:
```

Section "Device"
        Driver          "radeon"
...
        Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
EndSection
```

---

### Post by Noz3001 on 2010-09-08
> **antiram said:**
> maybe
mkdir /sys
mount -t sysfs sysfs /sys

or so, or do you use the old use mode setting?
then add to /etc/X11/xorg.conf some options:
```

Section "Device"
        Driver          "radeon"
...
        Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
EndSection
```

/sys/class/drm/card0/device/ exists, but there is no power_method file there.

---

### Post by bash on 2010-09-08
> **Noz3001 said:**
> /sys/class/drm/card0/device/ exists, but there is no power_method file there.

Then create one

---

### Post by Noz3001 on 2010-09-08
> **bash said:**
> Then create one

Not able too, probably because it's not a normal filesystem

---

### Post by antiram on 2010-09-08
make 
dmesg |grep -E "radeon|drm"
my lucid with backported maverick kernel and ati-r600 says
```

[    0.857938] [drm] Initialized drm 1.1.0 20060810
[    0.891044] [drm] radeon defaulting to kernel modesetting.
[    0.891047] [drm] radeon kernel modesetting enabled.
[    0.891090] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.891093] radeon 0000:01:00.0: setting latency timer to 64
[    0.892238] [drm] initializing kernel modesetting (RV620 0x1002:0x95C5).
[    0.892489] [drm] register mmio base: 0xF5000000
[    0.892490] [drm] register mmio size: 65536
[    0.892635] [drm] Clocks initialized !
[    0.892643] radeon 0000:01:00.0: VRAM: 512M 0x00000000 - 0x1FFFFFFF (512M used)
[    0.892645] radeon 0000:01:00.0: GTT: 512M 0x20000000 - 0x3FFFFFFF
[    0.892661] [drm] Detected VRAM RAM=512M, BAR=256M
[    0.892663] [drm] RAM width 64bits DDR
[    0.892745] [drm] radeon: 512M of VRAM memory ready
[    0.892746] [drm] radeon: 512M of GTT memory ready.
[    0.892787] radeon 0000:01:00.0: irq 45 for MSI/MSI-X
[    0.892791] [drm] radeon: using MSI.
[    0.892813] [drm] radeon: irq initialized.
[    0.892815] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    0.893470] [drm] Loading RV620 Microcode
[    0.929688] [drm] ring test succeeded in 1 usecs
[    0.929795] [drm] radeon: ib pool ready.
[    0.929860] [drm] ib test succeeded in 0 usecs
[    0.929862] [drm] Enabling audio support
[    0.929870] radeon 0000:01:00.0: Error during ACPI methods call
[    0.929890] [drm] Default TV standard: PAL
[    0.929893] [drm] Default TV standard: PAL
[    0.929919] [drm] Default TV standard: PAL
[    0.929994] [drm] Radeon Display Connectors
[    0.929995] [drm] Connector 0:
[    0.929996] [drm]   DIN
[    0.929997] [drm]   Encoders:
[    0.929999] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[    0.930000] [drm] Connector 1:
[    0.930001] [drm]   DVI-I
[    0.930002] [drm]   HPD2
[    0.930004] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    0.930005] [drm]   Encoders:
[    0.930007] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    0.930008] [drm]     DFP1: INTERNAL_UNIPHY
[    0.930010] [drm] Connector 2:
[    0.930011] [drm]   DVI-I
[    0.930012] [drm]   HPD1
[    0.930013] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    0.930014] [drm]   Encoders:
[    0.930015] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    0.930017] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[    1.034627] [drm] Internal thermal controller with fan control
[    1.034638] [drm] radeon: power management initialized
[    1.572336] [drm] fb mappable at 0xE0141000
[    1.572338] [drm] vram apper at 0xE0000000
[    1.572339] [drm] size 9216000
[    1.572340] [drm] fb depth is 24
[    1.572341] [drm]    pitch is 7680
[    3.223408] fb0: radeondrmfb frame buffer device
[    3.223409] drm: registered panic notifier
[    3.223517] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0

```
have yours "Clocks initialized","power management initialized", maybe "Loading blabla Microcode"?

which card?

---

### Post by andrewthomas on 2010-09-08
with the 2.6.36 kernel, one does not even need to use fglrx to monitor the temperature of the graphics card

```
andrew@790Fx:~$ uname -a
Linux 790Fx 2.6.36-rc3 #1 SMP PREEMPT Sat Sep 4 22:22:30 CDT 2010 x86_64 GNU/Linux
andrew@790Fx:~$ sensors
radeon-pci-0100
Adapter: PCI adapter
temp1:       +29.0°C  
```

---

### Post by Noz3001 on 2010-09-08
> **antiram said:**
> make 
dmesg |grep -E "radeon|drm"
my lucid with backported maverick kernel and ati-r600 says

have yours "Clocks initialized","power management initialized", maybe "Loading blabla Microcode"?

which card?

It wouldnt be because modesetting is being disabled, would it? =P
Card is a HD 3200 btw.

```
nathan@GLaDOS:~$ dmesg |grep -E "radeon|drm"
[    1.043157] [drm] Initialized drm 1.1.0 20060810
[    1.889278] [drm] VGACON disable radeon kernel modesetting.
[    1.890426] [drm] Initialized radeon 1.33.0 20080528 for 0000:01:05.0 on minor 0
[   13.591007] [drm] Setting GART location based on new memory map
[   13.591633] [drm] Loading RS780 CP Microcode
[   13.626740] [drm] Resetting GPU
[   13.626799] [drm] writeback test succeeded in 1 usecs
```


EDIT:

Yes! It was because I used nomodeset and I cant even remember why. Wow I'm an idiot, all of the files are there now, thanks =P

---

### Post by Untitled_No4 on 2010-09-09
Nevermind

---

