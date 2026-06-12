---
title: "amd64 nvidia related? 169.12 freezes requiring restart Quadro NVS 135m"
date: 2009-07-14
forum: Multimedia Software
---

### Post by misha680 on 2009-07-14
uname -a output:
```

Linux misha-d630 2.6.24-24-generic #1 SMP Tue Jul 7 19:10:36 UTC 2009 x86_64 GNU/Linux

```

I get syslog messages such as the following. Notably even when I restart the computer sometimes BIOS does not seem to come on without several power on/off iterations and I get screen corruption:

```

Jul 14 07:45:12 misha-d630 kernel: [  250.626737] NVRM: Xid (0001:00): 6, PE0001 
Jul 14 07:45:12 misha-d630 kernel: [  250.652966] NVRM: Xid (0001:00): 6, PE0001 
Jul 14 07:45:12 misha-d630 kernel: [  250.678924] NVRM: Xid (0001:00): 6, PE0001 
Jul 14 07:45:12 misha-d630 kernel: [  250.705365] NVRM: Xid (0001:00): 6, PE0001 
Jul 14 07:45:16 misha-d630 gdm[7014]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 14 07:45:29 misha-d630 kernel: [  264.874148] NVRM: Xid (0001:00): 43, CMDre 00000000 00000088 0100cb03 00000007 00000000
Jul 14 07:45:29 misha-d630 kernel: [  264.874180] NVRM: Xid (0001:00): 43, CMDre 00000000 0000008c 00000000 00000005 00000008
Jul 14 07:45:33 misha-d630 kernel: [  268.906395] NVRM: Xid (0001:00): 43, CMDre 00000000 00000088 0100cb0c 00000007 00000000
Jul 14 07:45:33 misha-d630 kernel: [  268.906451] NVRM: Xid (0001:00): 43, CMDre 00000000 0000008c 00000000 00000005 00000008

```

This is a Dell Latitude D630. Any help appreciated. 

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/399426](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/399426)

Thank you
Misha

p.s. Another related thread:
[http://www.nvnews.net/vbulletin/showthread.php?t=134181&goto=newpost](http://www.nvnews.net/vbulletin/showthread.php?t=134181&goto=newpost)

---

