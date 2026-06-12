---
title: "Ati Help Please Edgy"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by hvc123 on 2006-12-21
Hi all my 3d works crap i get 460 frames of fgl_glxgears i have a x700 on a p4 2.6 .5gb rambus

heres my dmesg | grep fglrx

dmesg | grep fglrx
[17179600.596000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179600.596000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179600.596000] [fglrx] module loaded - fglrx 8.31.5 [Nov  9 2006] on minor 0
[17179601.936000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179601.936000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179601.936000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179601.940000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179601.948000] [fglrx] total      GART = 268435456
[17179601.948000] [fglrx] free       GART = 252440576
[17179601.948000] [fglrx] max single GART = 252440576
[17179601.948000] [fglrx] total      LFB  = 126873600
[17179601.948000] [fglrx] free       LFB  = 116387840
[17179601.948000] [fglrx] max single LFB  = 116387840
[17179601.948000] [fglrx] total      Inv  = 134217728
[17179601.948000] [fglrx] free       Inv  = 134217728
[17179601.948000] [fglrx] max single Inv  = 134217728
[17179601.948000] [fglrx] total      TIM  = 0
[17179818.696000] [fglrx:firegl_rmmap] *ERROR* map 0xf176f550 still in use (map_count=1)
[17179818.696000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf176f540 still mapped (user_handle = 0x00011000)
[17179818.700000] [fglrx:firegl_rmmap] *ERROR* map 0xf176f550 still in use (map_count=1), force it to be removed anyway
[17179818.908000] [fglrx:firegl_rmmap] *ERROR* map 0xf63926d0 still in use (map_count=1)
[17179818.908000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf63926c0 still mapped (user_handle = 0x0000d000)
[17179819.016000] [fglrx:firegl_rmmap] *ERROR* map 0xf63926d0 still in use (map_count=1), force it to be removed anyway
[17183095.776000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17183095.776000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!
[17186619.032000] [fglrx:firegl_rmmap] *ERROR* map 0xf3c4e7d0 still in use (map_count=1)
[17186619.032000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf3c4e7c0 still mapped (user_handle = 0x00026000)
[17186619.032000] [fglrx:firegl_rmmap] *ERROR* map 0xf3c4e7d0 still in use (map_count=1), force it to be removed anyway
[17186619.300000] [fglrx:firegl_rmmap] *ERROR* map 0xf3c4e4d0 still in use (map_count=1)
[17186619.300000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf3c4e4c0 still mapped (user_handle = 0x00023000)
[17186619.348000] [fglrx:drm_vm_close] *ERROR* map not found -> inconsistent kernel data!!!



cheers

---

