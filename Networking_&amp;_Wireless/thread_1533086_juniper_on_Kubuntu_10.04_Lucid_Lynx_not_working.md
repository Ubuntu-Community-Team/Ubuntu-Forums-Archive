---
title: "juniper on Kubuntu 10.04 Lucid Lynx not working"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by ssottile70 on 2010-07-17
Hello,

I have installed Kubuntu 10.04 on my 64 buit laptop (EliteBook 8540w).
Command uname -a shows:

[FONT="Courier New"]2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux[/FONT]


I have troubles to make juniper working on this distro. I have connected to my company vpn via Firefox so that I could get the executables installed in my ~/.juniper directory. Now I'm trying to run command (after browsing some forums)

./ncsvc -h <host> -u <username> -p <password> -r <Realm> -f ~/.vpn.default.crt -L 4

but keep getting this errors in the ncsvc.log file:

[FONT="Courier New"]20100717111240.859892 ncsvc[p7482.t7482] dsclient.error state host checker failed, error 10 (dsclient.cpp:282)
20100717111240.860038 ncsvc[p7482.t7482] ncapp.error Failed to authenticate with IVE. Error 10 (ncsvc.cpp:192)[/FONT]


Any help?

Thanks
Salvo

---

