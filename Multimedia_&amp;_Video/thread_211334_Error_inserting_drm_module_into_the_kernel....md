---
title: "Error inserting drm module into the kernel..."
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by narandill on 2006-07-08
I have this error, when i executed install.sh from radeon driver (CVS 20060403)

dri.log:
> 
make DRM_MODULES=radeon.o modules
make[1]: Wej&#347;cie do katalogu `/home/mieszko/radeon-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.15-25-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.15-25-686'
  Building modules, stage 2.
  MODPOST
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.15-25-686'
make[1]: Opuszczenie katalogu `/home/mieszko/radeon-20060403-linux.i386/drm/linux-core'
[B]WARNING: Error inserting drm (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B]


dmesg:

> 
mieszko@mieszko:~$ dmesg | grep drm 
[17180148.976000] radeon: Unknown symbol drm_open
[17180148.980000] radeon: Unknown symbol drm_fasync
[17180148.980000] radeon: Unknown symbol drm_poll
[17180148.980000] radeon: Unknown symbol drm_get_resource_len
[17180148.980000] radeon: Unknown symbol drm_core_get_reg_ofs
[17180148.984000] radeon: Unknown symbol drm_irq_uninstall
[17180148.984000] radeon: Unknown symbol drm_get_dev
[17180148.984000] radeon: Unknown symbol drm_ioctl
[17180148.984000] radeon: Unknown symbol drm_exit
[17180148.988000] radeon: Unknown symbol drm_debug
[17180148.988000] radeon: Unknown symbol drm_core_get_map_ofs
[17180148.988000] radeon: Unknown symbol drm_init
[17180148.992000] radeon: Unknown symbol drm_addmap
[17180148.992000] radeon: Unknown symbol drm_get_resource_start
[17180148.992000] radeon: Unknown symbol drm_vbl_send_signals
[17180148.992000] radeon: Unknown symbol drm_cleanup_pci
[17180148.996000] radeon: Unknown symbol drm_ati_pcigart_init
[17180148.996000] radeon: Unknown symbol drm_mmap
[17180148.996000] radeon: Unknown symbol drm_order
[17180148.996000] radeon: Unknown symbol drm_ati_pcigart_cleanup
[17180149.000000] radeon: Unknown symbol drm_core_reclaim_buffers
[17180149.000000] radeon: Unknown symbol drm_release
[17180731.712000] radeon: Unknown symbol drm_open
[17180731.712000] radeon: Unknown symbol drm_fasync
[17180731.712000] radeon: Unknown symbol drm_poll
[17180731.712000] radeon: Unknown symbol drm_get_resource_len
[17180731.712000] radeon: Unknown symbol drm_core_get_reg_ofs
[17180731.712000] radeon: Unknown symbol drm_irq_uninstall
[17180731.712000] radeon: Unknown symbol drm_get_dev
[17180731.716000] radeon: Unknown symbol drm_ioctl
[17180731.716000] radeon: Unknown symbol drm_exit
[17180731.716000] radeon: Unknown symbol drm_debug
[17180731.716000] radeon: Unknown symbol drm_core_get_map_ofs
[17180731.720000] radeon: Unknown symbol drm_init
[17180731.720000] radeon: Unknown symbol drm_addmap
[17180731.720000] radeon: Unknown symbol drm_get_resource_start
[17180731.720000] radeon: Unknown symbol drm_vbl_send_signals
[17180731.720000] radeon: Unknown symbol drm_cleanup_pci
[17180731.720000] radeon: Unknown symbol drm_ati_pcigart_init
[17180731.720000] radeon: Unknown symbol drm_mmap
[17180731.720000] radeon: Unknown symbol drm_order
[17180731.720000] radeon: Unknown symbol drm_ati_pcigart_cleanup
[17180731.724000] radeon: Unknown symbol drm_core_reclaim_buffers
[17180731.724000] radeon: Unknown symbol drm_release
[17182299.908000] radeon: Unknown symbol drm_open
[17182299.908000] radeon: Unknown symbol drm_fasync
[17182299.908000] radeon: Unknown symbol drm_poll
[17182299.912000] radeon: Unknown symbol drm_get_resource_len
[17182299.912000] radeon: Unknown symbol drm_core_get_reg_ofs
[17182299.912000] radeon: Unknown symbol drm_irq_uninstall
[17182299.912000] radeon: Unknown symbol drm_get_dev
[17182299.924000] radeon: Unknown symbol drm_ioctl
[17182299.924000] radeon: Unknown symbol drm_exit
[17182299.928000] radeon: Unknown symbol drm_debug
[17182299.928000] radeon: Unknown symbol drm_core_get_map_ofs
[17182299.928000] radeon: Unknown symbol drm_init
[17182299.928000] radeon: Unknown symbol drm_addmap
[17182299.960000] radeon: Unknown symbol drm_get_resource_start
[17182299.960000] radeon: Unknown symbol drm_vbl_send_signals
[17182299.960000] radeon: Unknown symbol drm_cleanup_pci
[17182299.960000] radeon: Unknown symbol drm_ati_pcigart_init
[17182299.964000] radeon: Unknown symbol drm_mmap
[17182299.964000] radeon: Unknown symbol drm_order
[17182299.964000] radeon: Unknown symbol drm_ati_pcigart_cleanup
[17182299.964000] radeon: Unknown symbol drm_core_reclaim_buffers
[17182299.968000] radeon: Unknown symbol drm_release
[17182482.836000] radeon: Unknown symbol drm_open
[17182482.836000] radeon: Unknown symbol drm_fasync
[17182482.836000] radeon: Unknown symbol drm_poll
[17182482.840000] radeon: Unknown symbol drm_get_resource_len
[17182482.840000] radeon: Unknown symbol drm_core_get_reg_ofs
[17182482.840000] radeon: Unknown symbol drm_irq_uninstall
[17182482.852000] radeon: Unknown symbol drm_get_dev
[17182482.852000] radeon: Unknown symbol drm_ioctl
[17182482.852000] radeon: Unknown symbol drm_exit
[17182482.852000] radeon: Unknown symbol drm_debug
[17182482.940000] radeon: Unknown symbol drm_core_get_map_ofs
[17182482.944000] radeon: Unknown symbol drm_init
[17182482.944000] radeon: Unknown symbol drm_addmap
[17182482.944000] radeon: Unknown symbol drm_get_resource_start
[17182482.944000] radeon: Unknown symbol drm_vbl_send_signals
[17182482.948000] radeon: Unknown symbol drm_cleanup_pci
[17182482.948000] radeon: Unknown symbol drm_ati_pcigart_init
[17182482.948000] radeon: Unknown symbol drm_mmap
[17182482.948000] radeon: Unknown symbol drm_order
[17182482.952000] radeon: Unknown symbol drm_ati_pcigart_cleanup
[17182482.952000] radeon: Unknown symbol drm_core_reclaim_buffers
[17182482.952000] radeon: Unknown symbol drm_release


> mieszko@mieszko:~$ dmesg |grep -i agp
[17179599.060000] Linux agpgart interface v0.101 (c) Dave Jones
[17179599.064000] agpgart: Detected an Intel i815 Chipset.
[17179599.068000] agpgart: AGP aperture is 64M @ 0xd8000000


Maybe change some values in the .config ? This is my orginal .config file:
> 
mieszko@mieszko:~$ grep -i agp /usr/src/linux-headers-2.6.15-25-686/.config
CONFIG_AGP=m
CONFIG_AGP_ALI=m
CONFIG_AGP_ATI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m
CONFIG_AGP_EFFICEON=m


ATI Radeon 7500
xorg 7
common - installed
linux-headers-2.6.15-25-686

> mieszko@mieszko:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No


Can anyone please help me to resolve this problem ?

---

