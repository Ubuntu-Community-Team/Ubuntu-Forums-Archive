---
title: "No direct rendering with Intel GMA900"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by Sargonmetal on 2006-06-20
Hi,

For days I've been googleing info about getting direct rendering with an Intel GMA900 card, but I haven't found what I was looking for.

I'm using the i810 driver on my xorg.conf, and I also have installed the linux-dri-drivers for my kernel 2.6.15-25-686.

The thing is that when I do:

```
lsmod | grep 915
```

There's nothing in the output.

And when I try to do

```
sudo modprobe i915
```

I get:
```
WARNING: Error inserting drm (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting i915 (/lib/modules/2.6.15-25-686/volatile/i915.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

And the dmesg:
```
[17179600.652000] agpgart: Detected an Intel 915GM Chipset.
[17179601.936000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17183039.952000] i915: Unknown symbol drm_open
[17183039.952000] i915: Unknown symbol drm_fasync
[17183039.952000] i915: Unknown symbol drm_poll
[17183039.956000] i915: Unknown symbol drm_core_get_reg_ofs
[17183039.956000] i915: Unknown symbol drm_pci_alloc
[17183039.956000] i915: Unknown symbol drm_irq_uninstall
[17183039.956000] i915: Unknown symbol drm_get_dev
[17183039.956000] i915: Unknown symbol drm_ioctl
[17183039.956000] i915: Unknown symbol drm_exit
[17183039.956000] i915: Unknown symbol drm_debug
[17183039.956000] i915: Unknown symbol drm_core_get_map_ofs
[17183039.956000] i915: Unknown symbol drm_init
[17183039.956000] i915: Unknown symbol drm_vbl_send_signals
[17183039.956000] i915: Unknown symbol drm_cleanup_pci
[17183039.956000] i915: Unknown symbol drm_pci_free
[17183039.956000] i915: Unknown symbol drm_mmap
[17183039.956000] i915: Unknown symbol drm_core_reclaim_buffers
[17183039.956000] i915: Unknown symbol drm_release
```

which I don't know what it means...

So, I'm totally desperated and I'd really appreciate any help
I'm kind of newbie, so be patient with me please :)

Ask for any other outputs that you need!

Thanks in advice

---

### Post by Sargonmetal on 2006-06-21
After some hours touching things I should've never had touched, I completely broke my xserver. Hopefully, I successfully reinstalled and X work again!

But now I have another problem: I can't see any card at **/dev/agpgart** !!!

This is what I get from the X log:

```
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) I810(0): /dev/agpgart is either not available, or no memory is available
(--) I810(0): HW Cursor disabled because it needs agpgart memory.
```

Still no direct rendering. Any ideas? May I need the fglrx drivers or something?

I hope somebody could help me. Thanks!!!

---

### Post by rysiek on 2007-04-20
I had exactly the same problem. The thing was actually a b0rked install-cd (either the downliaded image was bad or the cd was scratched) and due to that - a few files were plain bad; and drm.ko (needed for direct rendering) among them.

You have two choices:
1. probably there are quite a few files b0rked on your system. I would suggest reinstalling it completely from a *new* cd (checked for errors *before* starting the installation).

2. if you haven't got the time and/or the strength (as I did), just do this:
```
sudo aptitude reinstall linux-image-2.6.20-15-generic
```

This will fix your problem, hopefully; you might have some b0rked files from some other packages as well, though, hence the first option is definitely the better.

cheers
mike

---

