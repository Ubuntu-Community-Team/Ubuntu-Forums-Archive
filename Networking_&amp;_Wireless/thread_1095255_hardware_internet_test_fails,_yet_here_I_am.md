---
title: "hardware internet test fails, yet here I am"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by mrl777 on 2009-03-13
Hello,

I think my system is messed up.  I did a hardware test and it came up with this (see below).  I rebooted and now it says there's no Internet connection, yet here I am on the Internet.

I have a bad feeling about this.


==============
hardware test

Testing your connection to the Internet:

ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
    sys.exit(main(sys.argv[1:]))
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main
    host = route.get_default_gateway()
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
    t1 = self._get_default_gateway_from_bin_route()
  File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
    if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment

Are you connected to the Internet?

====================

---

