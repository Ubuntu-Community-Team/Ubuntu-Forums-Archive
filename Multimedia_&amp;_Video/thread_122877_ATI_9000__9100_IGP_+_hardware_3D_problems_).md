---
title: "ATI 9000 / 9100 IGP + hardware 3D problems :)"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by s'neil on 2006-01-28
Got one of these in my laptop, and would like to get hardware 3d support so I can play WoW over wine!

I've tried the ATI drivers off the site and had a look at the DRI project, but none seem to work!

here is my fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

and my lspci
```

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 583                           5

```

and some lsmod action
```

fglrx                 439168  7
agpgart                34792  2 fglrx,ati_agp

```

When i try and run the DRI installer for the R200 chipsets i get the following...
```

Installing files:
        DRI XFree86 modules...done
        kernel modules...done
        Copying extra files...done

Updating configuration:
        Removing old kernel module "radeon"...done
        Inserting new kernel module "radeon"...ERROR

```

and the log shows
```

WARNING: Error inserting drm (/lib/modules/2.6.12-10-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.12-10-686/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and dmesg reveals
```

[4297299.977000] radeon: Unknown symbol drm_open
[4297299.977000] radeon: Unknown symbol drm_fasync
[4297299.977000] radeon: Unknown symbol drm_poll
[4297299.977000] radeon: Unknown symbol drm_get_resource_len
[4297299.977000] radeon: Unknown symbol drm_core_get_reg_ofs
[4297299.977000] radeon: Unknown symbol drm_irq_uninstall
[4297299.977000] radeon: Unknown symbol drm_get_dev
[4297299.977000] radeon: Unknown symbol drm_ioctl
[4297299.977000] radeon: Unknown symbol drm_exit
[4297299.978000] radeon: Unknown symbol drm_debug
[4297299.978000] radeon: Unknown symbol drm_core_get_map_ofs
[4297299.978000] radeon: Unknown symbol drm_init
[4297299.978000] radeon: Unknown symbol drm_addmap
[4297299.978000] radeon: Unknown symbol drm_get_resource_start
[4297299.978000] radeon: Unknown symbol drm_vbl_send_signals
[4297299.978000] radeon: Unknown symbol drm_cleanup_pci
[4297299.978000] radeon: Unknown symbol drm_ati_pcigart_init
[4297299.978000] radeon: Unknown symbol drm_mmap
[4297299.978000] radeon: Unknown symbol drm_order
[4297299.978000] radeon: Unknown symbol drm_ati_pcigart_cleanup
[4297299.978000] radeon: Unknown symbol drm_core_reclaim_buffers
[4297299.978000] radeon: Unknown symbol drm_release

```

so, any ideas? :)

---

### Post by th2 on 2006-01-31
Did you try glxgears after the install was done?

I realized that the default drivers are working on mine, and I was shocked.

Try doing a clean install, then type "glxgears."

If the gears roll smoothly, and not stop, then close the window and type "glxinfo."  If it says yes for direct rendering, then you have 3D.  I have a similar video controller (Mobility variety for notebooks) and I used the default drivers provided by Ubuntu.

---

