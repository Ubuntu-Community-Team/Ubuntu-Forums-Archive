---
title: "WinTV USB2 (not PVR!) crashes X and more problems"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by scotty64 on 2007-03-24
I am having problems to use my WinTV USB2 (no PVR version) under Dapper.
At first I am only getting the options "TV" and "S-Video" as video sources, although there is a working composite input as well.
Then when I try to change the video source within some applications, e.g. kdetv or Ekiga the whole X-Server crashes or sometimes even the entire system freezes.

My Sytem is a HP ZV6090 laptop with Radeon Xpress 200 graphicscard. I am using the latest ATI binary driver 8.34.8. The driver works fine (including 3D and Sideport) and I have disabled DGA in xorg.conf to avoid further trouble.

When I check the em28xx entries in the log it looks as the device is initialized properly.
The following appears in /var/log/messages at the point when X crashes:

Mar 24 17:44:40 localhost kernel: [17180344.284000]  [schedule+2461/3360] schedule+0x99d/0xd20
Mar 24 17:44:40 localhost kernel: [17180344.284000]  [__wake_up_common+67/112] __wake_up_common+0x43/0x70
Mar 24 17:44:40 localhost kernel: [17180344.284000]  [__wake_up+64/96] __wake_up+0x40/0x60
Mar 24 17:44:40 localhost kernel: [17180344.284000]  [pg0+950363329/1069171712] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
Mar 24 17:44:40 localhost kernel: [17180344.284000]  [pg0+950360459/1069171712] firegl_takedown+0x89b/0xba0 [fglrx]
Mar 24 17:44:40 localhost kernel: [17180344.284000]  [pg0+950355967/1069171712] firegl_release+0x12f/0x190 [fglrx]
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [__fput+169/416] __fput+0xa9/0x1a0
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [filp_close+82/144] filp_close+0x52/0x90
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [put_files_struct+145/224] put_files_struct+0x91/0xe0
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [do_exit+273/1056] do_exit+0x111/0x420
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [do_group_exit+64/176] do_group_exit+0x40/0xb0
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [get_signal_to_deliver+551/832] get_signal_to_deliver+0x227/0x340
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [do_signal+111/384] do_signal+0x6f/0x180
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [dput+509/528] dput+0x1fd/0x210
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [mntput_no_expire+28/144] mntput_no_expire+0x1c/0x90
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [__fput+338/416] __fput+0x152/0x1a0
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [sigprocmask+130/256] sigprocmask+0x82/0x100
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [sys_rt_sigprocmask+257/288] sys_rt_sigprocmask+0x101/0x120
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [sys_rt_sigprocmask+257/288] sys_rt_sigprocmask+0x101/0x120
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [do_notify_resume+40/56] do_notify_resume+0x28/0x38
Mar 24 17:44:40 localhost kernel: [17180344.288000]  [work_notifysig+19/25] work_notifysig+0x13/0x19
Mar 24 17:44:40 localhost gconfd (mark-6338): Received signal 15, shutting down cleanly
Mar 24 17:44:40 localhost gconfd (mark-6338): Exiting
Mar 24 17:44:46 localhost kernel: [17180350.436000] [fglrx] PCIe has already been initialized. Reinitializing ...
Mar 24 17:44:46 localhost kernel: [17180350.468000] [fglrx] total      GART = 130023424

:confused: :confused: :confused:

---

### Post by scotty64 on 2007-04-17
Compiling a non-preemptive kernel solved this problem and other video related crashes with "scheduling while atomic" errors.

---

