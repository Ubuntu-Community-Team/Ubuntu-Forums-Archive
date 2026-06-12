---
title: "MythTv Working, but I got unknown errors"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by drifting on 2007-04-01
Ubuntu just threw up a few beeps and errors.

I was wondering is this the problem with the Nova-T 500 that I read somewhere? I know it mentioned an oops message? but for the life of me I cannot find the page again.

I am so pleased to have got this far with Myth and Ubuntu, at least I have a semi working system, a couple of years ago all this was a nightmare with Fedora & Myth. Anyway error messages below :-

mythtv@Ubuntu:~$ 
Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] Oops: 0000 [#1]

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] SMP 

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] CPU:    0

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] EIP is at dvb_dmxdev_buffer_read+0x13/0x1b0 [dvb_core]

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] eax: 322e634c   ebx: 322e634c   ecx: ab532008   edx: 00000800

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] esi: 00000000   edi: cecbbfa4   ebp: 002b07a0   esp: cecbbf34

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] Process mythbackend (pid: 13004, threadinfo=cecba000 task=d580ea90)

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] Stack: cecbbf68 c013904e ab532008 00000800 00000001 00000000 cecbbf68 00000001 

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000]        c0139199 cecbbe58 cecbbfa4 ab532008 cecbbfa4 002b07a0 e0a4ede1 002b07a0 

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000]        cecbbfa4 d267c800 ab532008 c016af6c cecbbfa4 e0a4edb0 d267c800 fffffff7 

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] Call Trace:

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000]  <c013904e> hrtimer_cancel+0xe/0x20  <c0139199> hrtimer_nanosleep+0x49/0x120

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000]  <e0a4ede1> dvb_dvr_read+0x31/0x40 [dvb_core]  <c016af6c> vfs_read+0xbc/0x180

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000]  <e0a4edb0> dvb_dvr_read+0x0/0x40 [dvb_core]  <c016b4e1> sys_read+0x41/0x70

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000]  <c0102fbb> sysenter_past_esp+0x54/0x79 

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] Code: c7 04 24 e9 93 a5 e0 e8 8c 42 6d df eb 9c 8d 76 00 8d bc 27 00 00 00 00 55 57 56 31 f6 53 89 c3 83 ec 28 89 54 24 0c 89 4c 24 08 <8b> 10 85 d2 0f 84 07 01 00 00 8b 40 10 85 c0 0f 85 f3 00 00 00 

Message from syslogd@Ubuntu at Sun Apr  1 19:00:04 2007 ...
Ubuntu kernel: [17196696.200000] EIP: [pg0+542837779/1068893184] dvb_dmxdev_buffer_read+0x13/0x1b0 [dvb_core] SS:ESP 0068:cecbbf34
mythtv@Ubuntu:~$ 

Any help gratefully received.

Regards Paul

---

