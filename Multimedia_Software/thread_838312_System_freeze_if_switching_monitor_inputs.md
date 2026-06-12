---
title: "System freeze if switching monitor inputs"
date: 2008-06-23
forum: Multimedia Software
---

### Post by VChief on 2008-06-23
I hope it's ok for me to post this here. This has to do with Linux Mint, but nobody there seemed to know a fix for this. I figure that since Mint is based on Ubuntu, I would ask here. I'm hoping someone here has had experience with this.

I installed Mint a few weeks back, really liked it and recommended it to a friend who wanted to try Linux. Ubuntu is a great distro and Mint just helped out a little more with the little extras they added. Anyway, things are working pretty good except for one (well two, but I'm working on his X-fi stuff) problems.

He is using an amp that has both his computer and DVD player as inputs and a projector and speakers as output. The projector works without a problem as his display, however if he switches the input on the amp to the DVD player, X is frozen when he comes back. If it's a short period of time, he can just restart X and it works. However, if it's a longer period of time, the whole system is frozen and he has to do a hard reboot. Included is a snippet from /var/log/messages. The snippet repeats itself every 12 seconds for about 15 minutes before it appears to just give up. This is the very end of it so you can see when it logs the restart. Any ideas? I e-mailed him and told him to go down to a console next time to try a temp workaround until I can get some answers. If he tries that before I get any fixes, I'll post results for that. This only happens if the amp inputs are switched or the amp is turned off. If the projector is turned off, no issue. I hope someone can help. Again, if this is the improper place to post, I apologize. I'm hoping that Mint is close enough to Ubuntu that it's ok. :) If not, I apologize.

System info: AMD Phenom Quad Core 2.6GHZ, 4GB RAM, Radeon HD3870 512MB RAM (drivers installed, working flawlessly --as far as we can tell: compiz and WoW work like champs)
```

    Jun 18 08:53:29 HAL9000 kernel: [25149.226004] BUG: soft lockup - CPU#0 stuck for 11s! [skyrocket:11751]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226007]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226009] Pid: 11751, comm: skyrocket Tainted: P        (2.6.24-16-generic #1)
    Jun 18 08:53:29 HAL9000 kernel: [25149.226013] EIP: 0060:[<f8c995bb>] EFLAGS: 00000246 CPU: 0
    Jun 18 08:53:29 HAL9000 kernel: [25149.226079] EIP is at _ZN4Asic18isTimeStampExpiredE14_LARGE_INTEGERj+0x12b/0x150 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226081] EAX: 00000000 EBX: eda21d88 ECX: 00000000 EDX: f8886000
    Jun 18 08:53:29 HAL9000 kernel: [25149.226082] ESI: 00000000 EDI: f8fde020 EBP: eda21d10 ESP: eda21cf8
    Jun 18 08:53:29 HAL9000 kernel: [25149.226084]  DS: 007b ES: 007b FS:00d8 GS: 0033 SS: 0068
    Jun 18 08:53:29 HAL9000 kernel: [25149.226086] CR0: 80050033 CR2 a4afe000 CR3: 2ce26000 CR4: 00000690
    Jun 18 08:53:29 HAL9000 kernel: [25149.226087] DR0: 00000000 DR1:00000000 DR2: 00000000 DR3: 00000000
    Jun 18 08:53:29 HAL9000 kernel: [25149.226089] DR6: ffff0ff0 DR7:00000400
    Jun 18 08:53:29 HAL9000 kernel: [25149.226106]  [<f8c99de0>]_ZN4Asic22ElapsedTS_PollingUntil19ConditionSuccessfulEv+0x30/0x80[fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226190]  [<f8c996e8>] _ZN4Asic9WaitUntil15WaitForCompleteEv+0x38/0xf0 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226274]  [<f8c98776>]_ZN4Asic19PM4ElapsedTimeStampERK23PM4_TS_INTERRUPT_PARAMSj14_LARGE_INTEGER+0x166/0x200 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226385]  [<f8c7b4b6>] QSSubmitList+0x146/0x150 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226480]  [<f8c8d030>]_Z19uQSTimeStampRetiredjjj14_LARGE_INTEGER+0xf0/0x100 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226567]  [<f8c8a42f>]_Z8uCWDDEQCjjjPvjS_+0x2cf/0x11a0 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226654]  [<f8c7adf4>]CMMQS_uCWDDEQC+0x34/0x40 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226733]  [<f8c41e48>firegl_cmmqs_CWDDE_32+0x238/0x340 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226808][proc_coredump_filter_write+0xc6/0x110] proc_coredump_filter_write+0xc6/0x110
    Jun 18 08:53:29 HAL9000 kernel: [25149.226812]  [<f8c40e06>]firegl_cmmqs_CWDDE32+0x76/0x110 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226896]  [<f8c40d90>]firegl_cmmqs_CWDDE32+0x0/0x110 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.226961]  [<f8c334be>]firegl_ioctl+0x19e/0x220 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.227023][proc_coredump_filter_write+0xc6/0x110] proc_coredump_filter_write+0xc6/0x110
    Jun 18 08:53:29 HAL9000 kernel: [25149.227031]  [snd_pcm_oss:__wake_up+0x3e/0x1f10] __wake_up+0x3e/0x60
    Jun 18 08:53:29 HAL9000 kernel: [25149.227042][proc_coredump_filter_write+0xc6/0x110] proc_coredump_filter_write+0xc6/0x110
    Jun 18 08:53:29 HAL9000 kernel: [25149.227046]  [<f8c2885c>]ip_firegl_ioctl+0x1c/0x30 [fglrx]
    Jun 18 08:53:29 HAL9000 kernel: [25149.227106][proc_coredump_filter_write+0xc6/0x110] proc_coredump_filter_write+0xc6/0x110
    Jun 18 08:53:29 HAL9000 kernel: [25149.227112]  [do_ioctl+0x78/0x90]do_ioctl+0x78/0x90
    Jun 18 08:53:29 HAL9000 kernel: [25149.227121]  [vfs_ioctl+0x22e/0x2b0]vfs_ioctl+0x22e/0x2b0
    Jun 18 08:53:29 HAL9000 kernel: [25149.227131]  [sys_ioctl+0x56/0x70]sys_ioctl+0x56/0x70
    Jun 18 08:53:29 HAL9000 kernel: [25149.227139]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
    Jun 18 08:53:29 HAL9000 kernel: [25149.227143][proc_coredump_filter_write+0xc6/0x110] proc_coredump_filter_write+0xc6/0x110
    Jun 18 08:53:29 HAL9000 kernel: [25149.227168]  =======================
    Jun 18 23:11:41 HAL9000 syslogd 1.5.0#1ubuntu1: restart.

```

---

### Post by VChief on 2008-06-25
Ok...update. Found out that neither X nor the system freezes up if he switches to the console before switching inputs from the computer to the DVD player.

---

### Post by markbuntu on 2008-06-25
Skyrockets is a screensaver, turn off the screensaver.

---

### Post by VChief on 2008-06-27
> **markbuntu said:**
> Skyrockets is a screensaver, turn off the screensaver.

Unfortunately, that didn't fix the problem.

---

### Post by VChief on 2008-06-30
/bump

I'm bumping this in hopes that maybe someone new will see it and have an idea.

---

