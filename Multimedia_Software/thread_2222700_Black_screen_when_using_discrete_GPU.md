---
title: "Black screen when using discrete GPU"
date: 2014-05-07
forum: Multimedia Software
---

### Post by a.markiewicz on 2014-05-07
Hi all!

Yesterday I've made a clean install of Kubuntu 14.04 on my HP dm3 notebook. In previous versions I've struggled to disable discrete GPU to improve battery life and reduce overheating issuses, but today my problem seems to be the opposite. :)

I have MUXed ATI/ATI graphics. Normally system starts with only the integrated GPU enabled, and runs without a problem. However when I try to switch to dicrete GPU (using vgaswitcheroo) I get completely black screen (no image, no backlight) and I have to reboot to bring everything back to normal.

```

uname -a

Linux spark 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```

lspci -k (partial)

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780M [Mobility Radeon HD 3200]
        Subsystem: Hewlett-Packard Company Device 3657
        Kernel driver in use: radeon
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4330/4350/4550]
        Subsystem: Hewlett-Packard Company Device 3657
        Kernel driver in use: radeon
```

```

cat /sys/kernel/debug/vgaswitcheroo/switch (after system boot)

0:IGD:+:DynPwr:0000:01:05.0
1:DIS: :DynOff:0000:02:00.0
2:DIS-Audio: :Off:0000:02:00.1
```

```

cat /sys/kernel/debug/vgaswitcheroo/switch (during black screen)

0:IGD:+:DynPwr:0000:01:05.0
1:DIS: :DynPwr:0000:02:00.0
2:DIS-Audio: :Pwr:0000:02:00.1
```

When restarting X server I get a message:
```

vga_switcheroo: client 101 refused switch
```

I can switch to text mode with Ctrl+Alt+Fx and back, but my X session remains black. I can also log to KDE by typing my password blindly. I've also checked X.org log and everything seems to be in order. Outputs are detected corretly (check that also with an external screen), and descrete GPU is used (as far as I can tell).

Currently, I'm out of ideas. I'd be thankful for any hints on how to pin down this issue.

---

