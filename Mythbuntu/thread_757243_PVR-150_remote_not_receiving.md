---
title: "PVR-150 remote not receiving"
date: 2008-04-16
forum: Mythbuntu
---

### Post by thoraxe on 2008-04-16
Having some issues.  I just installed 8.04 Beta and my PVR-150 ir receive does not seem to be working.  Here are some notes:

Once the system boots, dmesg has this nastyness in it:

```
[   53.114731] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   53.115306] lirc_dev: lirc_register_plugin: sample_rate: 10
[   53.337351] sysfs: duplicate filename 'i2c ir driver' can not be created
[   53.337360] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   53.337365] Pid: 5535, comm: modprobe Not tainted 2.6.24-12-generic #1
[   53.337394]  [<c01d39cf>] sysfs_add_one+0x9f/0xe0
[   53.337413]  [<c01d3f08>] create_dir+0x48/0x90
[   53.337423]  [<c01d3f79>] sysfs_create_dir+0x29/0x50
[   53.337428]  [<c021182f>] kobject_get+0xf/0x20
[   53.337434]  [<c0211cf3>] kobject_add+0x93/0x1b0
[   53.337445]  [<c0211ea1>] kobject_register+0x21/0x50
[   53.337450]  [<c027e251>] bus_add_driver+0x71/0x1e0
[   53.337465]  [<f89a0770>] i2c_register_driver+0x70/0x120 [i2c_core]
[   53.337482]  [<f9632088>] init_module+0x48/0x50 [lirc_pvr150]
[   53.337490]  [<c01516c6>] sys_init_module+0x126/0x19c0
[   53.337530]  [<f958ae00>] lirc_register_plugin+0x0/0x500 [lirc_dev]
[   53.337549]  [<c01053c2>] sysenter_past_esp+0x6b/0xa9
[   53.337569]  =======================
[   53.337575] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.
[   53.337580] Pid: 5535, comm: modprobe Not tainted 2.6.24-12-generic #1
[   53.337584]  [<c0211d73>] kobject_add+0x113/0x1b0
[   53.337595]  [<c0211ea1>] kobject_register+0x21/0x50
[   53.337600]  [<c027e251>] bus_add_driver+0x71/0x1e0
[   53.337610]  [<f89a0770>] i2c_register_driver+0x70/0x120 [i2c_core]
[   53.337621]  [<f9632088>] init_module+0x48/0x50 [lirc_pvr150]
[   53.337626]  [<c01516c6>] sys_init_module+0x126/0x19c0
[   53.337665]  [<f958ae00>] lirc_register_plugin+0x0/0x500 [lirc_dev]
[   53.337681]  [<c01053c2>] sysenter_past_esp+0x6b/0xa9
[   53.337699]  =======================
```

I also notice that if I open a terminal very quickly after boot there are several lircds trying to start/restart.  After a few minutes everything seems to stabilize:

```
thoraxe@festivemyth:~$ ps -ef | grep lirc
root      5521     2  0 17:43 ?        00:00:00 [lirc_dev]
root      6036     1  0 17:46 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0
thoraxe   6306  6233  0 18:16 pts/1    00:00:00 grep lirc
```

If I run irw nothing comes in.  However, if I run mode2 on /dev/lirc0 I can see the codes coming in, so I believe that my receiver itself is functioning properly.

The particular remote I have is the silverish one, and appears to have the same code set as the 350 remote looking at the lircd.conf files in the /usr/share/lirc/remotes/hauppauge folder.

I've tried numerous times to reconfigure my IR settings in MCC but to no avail.

I'm using an older Athlon XP motherboard (Asus or Abit I believe).

Any suggestions?  I'm open to try things.

---

### Post by thoraxe on 2008-04-17
well, I reinstalled everything for giggles, but this time I didn't enable the IR blaster functionality.  The remote appears to be working now.  I am guessing that there is some conflicting stuff happening with the 150 between receive and transmit.

There are some resources for the ir transmit functionality with the 150, so I'll probably hit those up.  Unfortunately I'm having some freezing video problems with live tv.

---

### Post by Kheops_74 on 2008-04-25
Do you find how to get the IR blaster work? I'm able to get the remote working but not the IR blaster.

---

### Post by thoraxe on 2008-04-25
I actually never did, but I can't say that I tried much.  Once I got the remote working I was having problems with live tv capture freezing up and I gave up.  I'll probably come back to it in a few weeks again.

---

### Post by natrixgli on 2008-04-25
Do you have desktop effects enabled? This caused freezing problems for me with MythTV with PVR-150 and nVidia GeForce 6100.

On an Intel board I have no such issues. Unfortunately I have nothing to offer on the IR Blaster issue, as I don't use it.

-n8

---

### Post by Kheops_74 on 2008-04-26
Thanks. I hope with the lauch of Hardy yesterday. Some people will try to use the IR blaster of the PVR150 card and found a solution.

K

---

