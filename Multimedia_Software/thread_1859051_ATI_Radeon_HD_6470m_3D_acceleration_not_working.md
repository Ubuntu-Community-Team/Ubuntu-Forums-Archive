---
title: "ATI Radeon HD 6470m 3D acceleration not working"
date: 2011-10-13
forum: Multimedia Software
---

### Post by bugscripts on 2011-10-13
I have an HP laptop with dual Intel and ATI graphics. I think I have the switchable graphics set up correctly, but when using the ATI card, 3D acceleration performance is awful (worse than using the integrated graphics on windows.)

I'm using the open source driver from xorg; I tried the ATI driver but it kept causing kernel panics (and also had the 3D acceleration issue.)

2D acceleration works fine, and I'm fairly certain that the laptop is using the ATI card since the desktop seems to work more smoothly than when using the integrated GPU.

---

### Post by bugscripts on 2011-10-13
I think I found the source of the problem: The script I was using to switch cards during startup wasn't working, so it was actually using the integrated GPU.

I stopped X and went to a root shell and tried to switch manually. The card powered on, but when I tried to switch to it, the screen froze. I later found this in the kernel log:
```
Oct 13 15:01:20 Kubuntu kernel: [    3.164303] BUG: unable to handle kernel paging request at f9981ffc
Oct 13 15:01:20 Kubuntu kernel: [    3.165227] IP: [<f8ae98b9>] evergreen_cp_start+0x49/0xae0 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.166174] *pdpt = 000000000187f001 *pde = 0000000036518067 *pte = 0000000000000000 
Oct 13 15:01:20 Kubuntu kernel: [    3.167105] Oops: 0002 [#1] SMP 
Oct 13 15:01:20 Kubuntu kernel: [    3.168025] last sysfs file: /sys/devices/platform/radeon_cp.0/firmware/radeon_cp.0/loading
Oct 13 15:01:20 Kubuntu kernel: [    3.168974] Modules linked in: radeon(+) ttm i915 ahci libahci drm_kms_helper drm r8169 i2c_algo_bit video
Oct 13 15:01:20 Kubuntu kernel: [    3.169944] 
Oct 13 15:01:20 Kubuntu kernel: [    3.170875] Pid: 175, comm: modprobe Not tainted 2.6.38-11-generic-pae #50-Ubuntu Hewlett-Packard HP Pavilion g6 Notebook PC/1696
Oct 13 15:01:20 Kubuntu kernel: [    3.171864] EIP: 0060:[<f8ae98b9>] EFLAGS: 00010287 CPU: 2
Oct 13 15:01:20 Kubuntu kernel: [    3.172861] EIP is at evergreen_cp_start+0x49/0xae0 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.173844] EAX: 00000000 EBX: f75c5000 ECX: ffffffff EDX: f9981ffc
Oct 13 15:01:20 Kubuntu kernel: [    3.174830] ESI: 00000911 EDI: 00000011 EBP: f6ad5cf4 ESP: f6ad5cd4
Oct 13 15:01:20 Kubuntu kernel: [    3.175825]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Oct 13 15:01:20 Kubuntu kernel: [    3.176824] Process modprobe (pid: 175, ti=f6ad4000 task=f75ccbc0 task.ti=f6ad4000)
Oct 13 15:01:20 Kubuntu kernel: [    3.177841] Stack:
Oct 13 15:01:20 Kubuntu kernel: [    3.178835]  00000060 00000246 a736b7b4 f75c5000 00000000 f75c5000 00000911 00000011
Oct 13 15:01:20 Kubuntu kernel: [    3.179864]  f6ad5d08 f8aeca0b f75c5000 00000000 00000000 f6ad5d24 f8aee87f f8ac0ac1
Oct 13 15:01:20 Kubuntu kernel: [    3.180899]  f8b0e7b0 f6ad5d24 f75c5000 00000000 f6ad5d40 f8aefc97 c1349188 c16e9166
Oct 13 15:01:20 Kubuntu kernel: [    3.181938] Call Trace:
Oct 13 15:01:20 Kubuntu kernel: [    3.182988]  [<f8aeca0b>] evergreen_cp_resume+0x44b/0x660 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.184070]  [<f8aee87f>] evergreen_startup+0x10f/0x1d0 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.185161]  [<f8ac0ac1>] ? r600_pcie_gart_init+0x61/0x70 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.186254]  [<f8aefc97>] evergreen_init+0x187/0x2a0 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.187339]  [<c1349188>] ? vga_switcheroo_register_client+0x98/0xd0
Oct 13 15:01:20 Kubuntu kernel: [    3.188446]  [<f8a6999e>] radeon_device_init+0x41e/0x4a0 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.189561]  [<f8a680a0>] ? radeon_switcheroo_can_switch+0x0/0x50 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.190697]  [<f8a6ae54>] radeon_driver_load_kms+0x94/0x160 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.191835]  [<f87fc9c4>] drm_get_pci_dev+0x144/0x2b0 [drm]
Oct 13 15:01:20 Kubuntu kernel: [    3.192972]  [<c10359b8>] ? default_spin_lock_flags+0x8/0x10
Oct 13 15:01:20 Kubuntu kernel: [    3.194115]  [<f8af886b>] ? radeon_pci_probe+0x2f/0xc7 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.195254]  [<f8af886b>] ? radeon_pci_probe+0x2f/0xc7 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.196364]  [<f8af88fc>] radeon_pci_probe+0xc0/0xc7 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.197468]  [<c129f977>] local_pci_probe+0x47/0xb0
Oct 13 15:01:20 Kubuntu kernel: [    3.198564]  [<c12a0df8>] pci_device_probe+0x68/0x90
Oct 13 15:01:20 Kubuntu kernel: [    3.199668]  [<c134df8d>] really_probe+0x4d/0x150
Oct 13 15:01:20 Kubuntu kernel: [    3.200765]  [<c135617b>] ? pm_runtime_barrier+0x4b/0xb0
Oct 13 15:01:20 Kubuntu kernel: [    3.201864]  [<c134e22c>] driver_probe_device+0x3c/0x60
Oct 13 15:01:20 Kubuntu kernel: [    3.202965]  [<c134e2d1>] __driver_attach+0x81/0x90
Oct 13 15:01:20 Kubuntu kernel: [    3.204057]  [<c134e250>] ? __driver_attach+0x0/0x90
Oct 13 15:01:20 Kubuntu kernel: [    3.205140]  [<c134d388>] bus_for_each_dev+0x48/0x70
Oct 13 15:01:20 Kubuntu kernel: [    3.206219]  [<c12a0800>] ? pci_device_remove+0x0/0xf0
Oct 13 15:01:20 Kubuntu kernel: [    3.207294]  [<c134de3e>] driver_attach+0x1e/0x20
Oct 13 15:01:20 Kubuntu kernel: [    3.208357]  [<c134e250>] ? __driver_attach+0x0/0x90
Oct 13 15:01:20 Kubuntu kernel: [    3.209415]  [<c134da58>] bus_add_driver+0xb8/0x250
Oct 13 15:01:20 Kubuntu kernel: [    3.210466]  [<c12a0800>] ? pci_device_remove+0x0/0xf0
Oct 13 15:01:20 Kubuntu kernel: [    3.211516]  [<c134e516>] driver_register+0x66/0x110
Oct 13 15:01:20 Kubuntu kernel: [    3.212572]  [<c129ff15>] __pci_register_driver+0x45/0xb0
Oct 13 15:01:20 Kubuntu kernel: [    3.213643]  [<f87fce16>] drm_pci_init+0x96/0xc0 [drm]
Oct 13 15:01:20 Kubuntu kernel: [    3.214705]  [<f87f5124>] drm_init+0x54/0x70 [drm]
Oct 13 15:01:20 Kubuntu kernel: [    3.215766]  [<f850e0b7>] radeon_init+0xb7/0x1000 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.216813]  [<c1003165>] do_one_initcall+0x35/0x170
Oct 13 15:01:20 Kubuntu kernel: [    3.217853]  [<f850e000>] ? radeon_init+0x0/0x1000 [radeon]
Oct 13 15:01:20 Kubuntu kernel: [    3.218874]  [<c109240b>] sys_init_module+0xdb/0x230
Oct 13 15:01:20 Kubuntu kernel: [    3.219879]  [<c100ab5f>] sysenter_do_call+0x12/0x28
Oct 13 15:01:20 Kubuntu kernel: [    3.220861] Code: f0 0f 85 94 08 00 00 8b 83 c0 07 00 00 85 c0 0f 8e 6d 08 00 00 8b 83 b0 07 00 00 8d 14 85 00 00 00 00 83 c0 01 03 93 a8 07 00 00 <c7> 02 00 44 05 c0 8b 93 c0 07 00 00 23 83 d0 07 00 00 83 ab bc 
Oct 13 15:01:20 Kubuntu kernel: [    3.222999] EIP: [<f8ae98b9>] evergreen_cp_start+0x49/0xae0 [radeon] SS:ESP 0068:f6ad5cd4
Oct 13 15:01:20 Kubuntu kernel: [    3.224087] CR2: 00000000f9981ffc
Oct 13 15:01:20 Kubuntu kernel: [    3.225143] ---[ end trace a888468bb54bf1ce ]---
```

Can anyone tell what the problem is?

---

