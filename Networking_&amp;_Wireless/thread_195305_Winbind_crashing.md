---
title: "Winbind crashing"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by wedge2k on 2006-06-12
Fresh install of Kubuntu 6.06, desided I would try to get winbind going with our NT network. I'm using a very standard winbind config.  Joined the domain without any problems.  However when I go to do wbinfo -u it says it couldn't find any users.  

Finally i found the log file and this is what it contained:

```
[2006/06/12 13:32:06, 0] lib/fault.c:fault_report(36)
  ===============================================================
[2006/06/12 13:32:06, 0] lib/fault.c:fault_report(37)
  INTERNAL ERROR: Signal 11 in pid 7338 (3.0.22)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2006/06/12 13:32:06, 0] lib/fault.c:fault_report(39)

  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2006/06/12 13:32:06, 0] lib/fault.c:fault_report(40)
  ===============================================================
[2006/06/12 13:32:06, 0] lib/util.c:smb_panic2(1544)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 7338]
[2006/06/12 13:32:06, 0] lib/util.c:smb_panic2(1552)
  smb_panic(): action returned status 0
[2006/06/12 13:32:06, 0] lib/util.c:smb_panic2(1554)
  PANIC: internal error
[2006/06/12 13:32:06, 0] lib/util.c:smb_panic2(1562)
  BACKTRACE: 27 stack frames:
   #0 /usr/sbin/winbindd(smb_panic2+0x78) [0x80dc868]
   #1 /usr/sbin/winbindd(smb_panic+0x19) [0x80dca65]
   #2 /usr/sbin/winbindd [0x80cab75]
   #3 [0xffffe420]
   #4 /usr/lib/libnss_mdns.so.2 [0xb79f4728]
   #5 /usr/lib/libnss_mdns.so.2 [0xb79f49cd]
   #6 /usr/lib/libnss_mdns.so.2(mdns_query_ipv4+0x99) [0xb79f4ab0]
   #7 /usr/lib/libnss_mdns.so.2(_nss_mdns_gethostbyaddr_r+0x18a) [0xb79f6d72]
   #8 /lib/tls/i686/cmov/libc.so.6(gethostbyaddr_r+0x156) [0xb7d8c1f6]
   #9 /lib/tls/i686/cmov/libc.so.6(getnameinfo+0x41c) [0xb7d9428c]
   #10 /usr/lib/libldap_r.so.2(ldap_pvt_get_hname+0x5a) [0xb7e0cf24]
   #11 /usr/lib/libldap_r.so.2(ldap_host_connected_to+0x132) [0xb7e08bc9]
   #12 /usr/lib/libldap_r.so.2(ldap_int_open_connection+0x1bb) [0xb7df52a5]
   #13 /usr/lib/libldap_r.so.2(ldap_new_connection+0x7d) [0xb7e06544]
   #14 /usr/lib/libldap_r.so.2(ldap_open_defconn+0x3d) [0xb7df4c71]
   #15 /usr/lib/libldap_r.so.2(ldap_open+0x43) [0xb7df4fa0]
   #16 /usr/sbin/winbindd(ldap_open_with_timeout+0x42) [0x8191c41]
   #17 /usr/sbin/winbindd [0x808b5fa]
   #18 /usr/sbin/winbindd [0x808c13b]
   #19 /usr/sbin/winbindd [0x807d850]
   #20 /usr/sbin/winbindd [0x807dd4a]
   #21 /usr/sbin/winbindd [0x807e6f4]
   #22 /usr/sbin/winbindd(winbindd_list_users+0xc4) [0x8076fe3]
   #23 /usr/sbin/winbindd [0x8073e4d]
   #24 /usr/sbin/winbindd(main+0x660) [0x807499c]
   #25 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7cc2ea2]
   #26 /usr/sbin/winbindd [0x80731e1]
[2006/06/12 13:33:02, 1] nsswitch/winbindd.c:main(978)
  winbindd version 3.0.22 started.
  Copyright The Samba Team 2000-2004
[2006/06/12 13:33:02, 0] nsswitch/winbindd_util.c:winbindd_param_init(787)
  winbindd: idmap uid range missing or invalid

```

Any thoughts?

---

### Post by wedge2k on 2006-06-15
Just reinstalled winbind and now its working... *shrug*
----
Scrach that, still crashing.. =(

---

