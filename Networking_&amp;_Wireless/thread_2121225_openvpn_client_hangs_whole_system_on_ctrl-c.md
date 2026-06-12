---
title: "openvpn client hangs whole system on ctrl-c"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by grigglestone on 2013-03-01
I start and use an openvpn connection just fine. However infrequently I need to drop the vpn connection for a while and to stop the connection in the past I have used ctrl-c, which seemed to work fine. Now (after several recommended updates) when I do this the whole system hangs (everything) so I can't take and screen shots or look at any status.

Can anyone suggest ways I can help to diagnose the issue?

[update] Just found that it only happens when I have accessed a SMB path to a Wondows share through Nautilus. If I don't open that share I am able to exit openvpn with no problems. Based on this info anyone have any suggestions for diagnosing or even know what the problem is?

---

### Post by kabala on 2013-03-05
Hello,

I have experienced the same problem with ubuntu 12.04 - I can confirm, that openvpn hangs the system. But in my case I don't need to press ctrl+c - it just happens during openvpn usage in background.

mm@mm-Vostro-3560:~$ uname -a
Linux mm-Vostro-3560 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
mm@mm-Vostro-3560:~$


Other programs running during that time:

Chrome,
Dropbox,
Skype


#===== Update ======

I have noticed, that there is an update for kernel. The problem persists after kernel update:

mm@mm-Vostro-3560:~$ uname -a
Linux mm-Vostro-3560 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



Same applications running in background.

---

