---
title: "Problem with EeePc 1215B"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by hostkernel on 2012-10-28
Hi guys ... I've a problem with my EeePc 1215B.
I've installed Ubuntu 12.10 with Gnome-shell interface a couple of days ago...

My problem is that during the day, for like 4-5 times per day, my computer remain connected to my router (with wifi) but I can't surf the net.
I tryed to ping google or static IP but nothing happen.

The only thing I can do is ifconfig wlan0 down and wlan0 up. And Network re-working good.

When I write dmesg | tail (when it doesn't work) this is what I read:

hostkernel@h0stk3rn3l-1215B:~$ dmesg | tail
[   19.923026] wlan0: associated
[   19.923499] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  629.474022] audit_printk_skb: 54 callbacks suppressed
[  629.474037] type=1701 audit(1351424567.591:30): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2265 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb37dd424 code=0x50000
[ 3194.338351] type=1701 audit(1351427132.965:31): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2471 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb372a424 code=0x50000
[ 6426.476919] type=1701 audit(1351430365.677:32): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2881 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb37e3424 code=0x50000
[ 6696.324273] type=1701 audit(1351430635.573:33): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=3115 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb377c424 code=0x50000
[ 8048.729730] type=1701 audit(1351431988.217:34): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=3959 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb37c4424 code=0x50000
[10756.274862] type=1701 audit(1351434696.241:35): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=4606 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb373d424 code=0x50000
[14314.919794] type=1701 audit(1351438255.517:36): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=5232 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb3819424 code=0x50000

Anyone can help me or suggest me something to read? because I surfed the net to find a solution but i don't find nothing.

Thanks everyone!!
(If I wrong the section... forgive me :) )

---

