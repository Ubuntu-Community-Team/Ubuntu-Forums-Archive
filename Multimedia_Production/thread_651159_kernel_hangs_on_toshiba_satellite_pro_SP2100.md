---
title: "kernel hangs on toshiba satellite pro SP2100"
date: 2007-12-27
forum: Multimedia Production
---

### Post by lodopidolo on 2007-12-27
Hi, I want to install ubuntu studio in my toshiba satellite pro SP2100 latop.

I downloaded ubuntustudio-7.10-alternate-i386.iso and began then install process.

In the install process there wasn't any problem (I want audio studio). Then when install process finish and reboot, appears this message (I think is a kernel message because appear inmediatily), and it hangs:

... pnp_auto_config_dev ...
... pnp_alloc ...
... kmen_cache_free ...
... pnp_activate_dev ...
... quirk_smc_enabe ...
... pnpacpi_option_resource ...
... vsnprintf ...
... pnp_fixup_device ...
... __pnp_add_device ...
... pnpacpi_add_decive_handler ...
... acpi_ns_get_decive_callback ...
... acpi_ns_walk_namespace ...
... acpi_get_devices ...
... acpi_ns_get_device_callback ...
... pnpacpi_add_device_handler ...
... pnpacpi_init ...
... __switch_to ...
... schedule_tail ...
... ret_from_fork+0x6/0x20
... kernel_init+0x0/0x3b0
... kernel_init+0x0/0x3b0
... kernel_thread_helper+0x7/0x10
==========================


What is the problem?
Thanks.

---

### Post by McLindy on 2008-01-04
I have the same (or at least a very similar) problem on a Satellite Pro 6100.  I switched off wireless, removed PCMCIA devices, removed DVD-ROM drive, removed battery but none of this seems to have had any effect.  

...
kernel_init+0x0/0x3b0
kernel_init+0x0/0x3b0
kernel_thread_helper+0x7/0x10
=======================


hangs with flashing cursor.

---

### Post by McLindy on 2008-01-07
It seems to be the realtime kernel, though I don't know why.  Here's what I did to get UbuntuStudio running on my Toshiba Satellite 6100:

Install regular Ubuntu 7.10 from regular (not alternate) CD.

Follow[ these excellent directions ]("http://www.r3uk.co.uk/content/view/50/61/index.php?option=com_content&task=view&id=174&Itemid=60")to get your nVidia drivers working well.  I did not do the further work to get my resolution to 1600.

Followed [these excellent directions]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") to upgrade to UbuntuStudio.  I also followed the directions on the same page to get the UbuntuStudio themes.

A word of caution!!!  Don't type in that last bit and install linux-rt in the upgrade step.  That will cause your system to hang like it's doing when you install from the alternate CD.  I don't know why this is happening on our Toshibas.

I had the apps installed but when I rebooted (I typed linux-rt because I didn't know any better) I got the same hang at the same place.

I had to reboot and hold down ESC to get options, then I was able to choose to boot from the regular kernel, not the RT kernel.  UbuntuStudio seems to be running fine without the realtime kernel.  However, I don't know how this will affect my audio and video work.

I hope this helps.  If anyone knows about the realtime kernel issue and how it might relate to these Toshiba laptops please leave a note.

---

### Post by ulgor on 2008-04-12
After having used the regular Ubuntu for a while, I decided to install ubuntu studio 7.10 ( I am interested in the realtime kernel for low latencies in audio software).

Now I have the same problem: Installation OK, but the first reboot after installation freezes here:
[121.8787][somenumbers] kernel_init +0x0/0x3b0
[121.1234][somenumbers] kernel_thread_helper +0x7/0x10

My setup: Acer Travelmate 290, centrino pentium 1.5 GHz, 1GB RAM, ATI radeon 9700 

I had to use "vga=771" in order to get the installer working, but I don´t think that is related to our kernel problem? I have no idea how to solve problems concerning the kernel at all... I know that I could also install ubuntu without rt kernel, and apply the steps mentioned above to install the studio software. 

My old ubuntu install ran fine, but now I would like to try the rt kernel. How can this be solved?

---

### Post by ulgor on 2008-04-12
i am currently downloading the 8.04 ubuntu studio image. it´s worth a try....

@some-linux-pro: is 8.04 using a different/better rt-kernel? we´ll find out...


edit: Alright, no problems with the new 8.04 Hardy beta studio! It appears to be quite stable, but you might want to wait until April 24th for the official release...

---

