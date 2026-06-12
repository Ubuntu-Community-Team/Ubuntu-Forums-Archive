---
title: "Connecting to Windows L2TP VPN"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by octbit on 2009-11-04
My company runs an L2TP VPN on a Windows server without using IPSec shared secrets or certs.  For every windows client they bring onto the VPN, they add the following registry hack:

```

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\RasMan\Parameters]
"ProhibitIpSec"=dword:00000001
```

I did some research on what this really does in Windows, and found this:

> When the ProhibitIpSec registry value is set to 1, your Windows 2000-based computer does not create the automatic filter that uses CA authentication. Instead, it checks for a local or Active Directory IPSec policy.

I'm not a Windows AD or VPN guru, so I'm sort of stuck here trying to figure out how to emulate this in Ubuntu.  Has anyone else run across this?

Thanks!

---

