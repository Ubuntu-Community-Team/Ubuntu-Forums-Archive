---
title: "Ubuntu not detecting integrated intel graphics card"
date: 2011-06-24
forum: Multimedia Software
---

### Post by nbubis on 2011-06-24
Hi,

I have a dell E6410 with integrated Intel graphics (core i7 620M - GMA HD) as well as a dedicated Nvidia card. The Nvidia card is working fine with the proprietary driver, but I'd like to enable the Intel card as well, in order to try switching between them (to save battery life).

Running [FONT="Courier New"]lspci -v | grep -e VGA[/FONT]

```
01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2) (prog-if 00 [VGA controller])
```

Where is my Intel card and why doesn't it show up?


If this helps, the following shows up in my [FONT="Courier New"]kern.log[/FONT]:

```
[] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=2604a72d-9989-49dc-8431-6477af3494f2 ro quiet splash i915.modeset=1 vt.handoff=7
[] [drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!
[] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

```

Ideas anyone?

---

### Post by mrv on 2011-09-06
Same problem here, and I'd wish to get the Intel working as well. No luck yet at least. Also about the only thing googling has given me so far has been to add a "softdep intel_ips pre: i915" to eg. /etc/modprobe.d/intel-ips-dep-i915.conf file, but it was seemingly for not solving exactly this issue and doesn't help with getting the Intel graphics actually visible. However, it gives another i915 line in dmesg. I tried to also load intel_agp manually etc...

[SIZE="1"](note that this thread was a spin-off from [this thread](http://ubuntuforums.org/showthread.php?p=11223051))[/SIZE]

---

### Post by BicyclerBoy on 2011-09-06
I would guess you need a later kernel.
Your h/w is fairly cutting edge..

2.6.39 had a load of sandybridge stuff added.

You can run kernel 3.0.x with 11.04 etc.

---

### Post by mrv on 2011-09-06
I'm running Ubuntu 11.10 with Linux 3.0.x. It's not about that, it's more about the E6410's dual Intel+NVIDIA graphics and the possible impossibility of really enabling the Intel side. Also, E6410 is not Sandy Bridge but Arrandale.

---

### Post by BicyclerBoy on 2011-09-06
Sorry, you're quite right..just an old iCPU..
Optimus again.
Most optimus users have the opposite problem with new install; only the intel side works.

Have you had a look at Bumblebee & vgaswitcharoo projects.

---

### Post by nbubis on 2011-09-06
BicyclerBoy, 

The laptop in question is not an optimus. Moreover, vga switcharoo / bumblebee / ironhide cannot be use because the kernel is not detecting the intel card - you can't switch something that the kernel doesn't think is there. 

Perhaps we could file a kernel / intel driver bug ?

---

### Post by BicyclerBoy on 2011-09-06
I'm surprised you can buy a laptop (?) with dual video that is not optimus.
Is the nVidia card plugged into miniPCIe ?

From what I have read it is optimus ..from Dell marketing release:
"Display is driven either by the integrated graphics on the processor, or a discrete NVIDIA NVS 3100M 512MB solution"

The OP had a GRUB option to force kms on.
Kernel mode switching is required by the intel driver.
And kms requires acpi to be working.

So maybe try
acpi_force in the GRUB command..
or in the appropriate file
GRUB_CMDLINE_LINUX="acpi=force"


Related to post #2 intel_ips driver loading before the i915
Did you find this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569)
The last post
"The workaround boot in recovery mode then
sudo vi /etc/modprobe.d/blacklist.conf
add line:
blacklist intel_ips
 finally reboot"

---

### Post by mrv on 2011-09-06
> **BicyclerBoy said:**
> I'm surprised you can buy a laptop (?) with dual video that is not optimus.


Optimus means switching on the fly between integrated and discrete graphics. Latitude E6410, which is Arrandale and predecessor to E6420 which is Sandy Bridge, doesn't have Optimus but still has both the integrated-to-CPU Intel graphics and the discrete graphics. Now the on-the-fly switching is out of question, but the real question is that is the switching possible at all. And another related problem is that if we're stuck with the NVIDIA, is there some extra power drain from the integrated GPU that could be done something about.

It's a side-effect of the first generation of Intel GPU-on-CPU-chip and the fact that manufacturers still wanted to offer discrete graphics even though there were no on-the-fly switching technology implemented yet.

> 
The OP had a GRUB option to force kms on.
Kernel mode switching is required by the intel driver.


KMS is also required by nvidia (I'm using nouveau, not the proprietary driver). KMS is working fine with it.

> 
Related to post #2 intel_ips driver loading before the i915
Did you find this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569)
The last post
"The workaround boot in recovery mode then
sudo vi /etc/modprobe.d/blacklist.conf
add line:
blacklist intel_ips
 finally reboot"

Actually yes I found this as well. It basically gets rid of the error message, but I do not know if it affects anything. It's funny, though, how there is that amount of i915 and intel_ips lines even though the Intel integrated graphics otherwise looks like non-existent from Linux side. But because there are those lines, I as a E6410 owner still hope that there is some possibility to enable the Intel graphics. And others who do not care about the Intel graphics care about power usage, and if there is something to fix somewhere.

I now underclock the NVIDIA chip and power usage starts to look a bit better now. Still I wonder if it'd be better not to blacklist intel_ips since it is a power management module for Intel graphics after all, or to blacklist it in case the module actually awakens something...

---

### Post by BicyclerBoy on 2011-09-06
Off topic but the laptop has just one form of optimus..the marketing info states it switches.
Is it not dynamic switching ?
Very off topic..
The optimus driver/bumblebee works with DIY PCIexpress video cards & intel iCPU (& AMD fusion).
This is working in linux & windows. You can make your own optimus graphics solution with any laptop/notebook that has a miniPCIe or PCIe slot. some adaptor & a PCIe graphics card.
Yes it can drive/accelerate the internal panel.


It is possible this problem relates to late start KMS after kernel is bootstrapped. (probably by udev rule).
The i915 module can be loaded with KMS during the kernel by adding the line
MODULES="**i915**"
into one of the /etc/modprobe.d/*.conf files & rebuilding the boot image with initramfs etc..
Exactly which file in ubuntu setup is not clear to me.

---

### Post by mrv on 2011-09-07
The problem is not that (adding i915 to /etc/modules which is the file that initramfs creation takes into account AFAIK), since there is no Intel card from Linux's point of view, other than that somehow the i915 module still tries to load but fails. It may be something caused by CPU detection letting the system know that there is integrated graphics, while actually the intel gfx device does not exist to software (as far as lspci is concerned).

So it's not KMS, module or any such mundane thing. The question merely is if the Intel graphics can be enabled at all, and that has to be done before any i915 module comes into picture since currently the hardware does not exist for the kernel. So either there is an ACPI call that can be used or the Intel gfx is simply hardware disabled by not wiring some needed paths.

There has been a Dell representative saying in the other thread's quoted chat that the Intel chip in the Nvidia variant of the Dell Latitude E6410 could output graphics, but so far there is no proof about it. It may be that it's only nvidia that can be used, and I've at least so far turned my interest into trying to cut down the power usage of nvidia via nouveau settings instead.

(I wouldn't have wanted nvidia laptop anyway, but I had no choice since this one only one left)

---

### Post by BicyclerBoy on 2011-09-07
That makes sense, except for the i915 driver being (trying) loaded.
What's reported by dmesg about agpgart-intel ?

Not as mundane as lack of memory in the boot process in 32 bit kernel ?
The little I know, this would effect the i915 driver from loading & not the intel-agp.

Is the nVidia GPU a plugin card ?
Only ask because Dell has same model range without discrete graphics..
Do they still make laptops with graphics card anymore ?
Can you disable the discrete graphics in BIOS & still boot ?
BIOS update.

---

