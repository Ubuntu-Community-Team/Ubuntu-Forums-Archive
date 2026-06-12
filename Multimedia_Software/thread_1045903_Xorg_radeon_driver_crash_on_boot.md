---
title: "Xorg radeon driver crash on boot"
date: 2009-01-20
forum: Multimedia Software
---

### Post by Oni029 on 2009-01-20
1.
      Broken output of /var/log/Xorg.0.log:
   2.
       
   3.
      (II) Loading /usr/lib/xorg/modules//libint10.so
   4.
      (II) Module int10: vendor="X.Org Foundation"
   5.
              compiled for 1.5.2, module version = 1.0.0
   6.
              ABI class: X.Org Video Driver, version 4.1
   7.
      (II) RADEON(0): initializing int10
   8.
      (II) RADEON(0): Primary V_BIOS segment is: 0xc000
   9.
      (II) RADEON(0): Legacy BIOS detected
  10.
      drmOpenDevice: node name is /dev/dri/card0
  11.
      drmOpenDevice: open result is -1, (No such device or address)
  12.
      drmOpenDevice: open result is -1, (No such device or address)
  13.
      drmOpenDevice: Open failed
  14.
       
  15.
      Backtrace:
  16.
      0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
  17.
      1: [0xb7fe0400]
  18.
      2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a60c27]
  19.
      3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a2e55a]
  20.
      4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a314fc]
  21.
      5: /usr/X11R6/bin/X(InitOutput+0x96f) [0x80aac9f]
  22.
      6: /usr/X11R6/bin/X(main+0x279) [0x8071b19]
  23.
      7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7be3685]
  24.
      8: /usr/X11R6/bin/X [0x8071101]
  25.
      Saw signal 11.  Server aborting.
  26.
       
[B]      Commands to make it work:
      sudo modprobe radeon
      sudo /etc/init.d/gdm restart[/B]



------------------------------------------------------

Basically every time the computer boots I'm put into console mode, and have to use the above command to get into the GUI. Problem started occuring after first time I tried to hibernate

---

