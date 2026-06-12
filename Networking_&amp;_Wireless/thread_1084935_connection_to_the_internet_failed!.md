---
title: "connection to the internet failed!"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by hosseinian on 2009-03-02
hi,
I install ubuntu 8.10 last week, my ADSL modem is planet router modem and that is DHCP, so I don't need create adsl connection and insert user & pass. when I log in to the ubuntu first time, the networking program found a default ethernet connection in my computer. but I can't connect to the internet and not happen and connection failed. I attached my connection information screen shot here. 
on the other hand, when I testing my connection to the internet, I received this errors:
> ERROR:root:Could not find def gateway info in /proc Traceback (most recent call last): File "/usr/share/hwtest/scripts/internet_test", line 132, in <module> sys.exit(main(sys.argv[1:])) File "/usr/share/hwtest/scripts/internet_test", line 118, in main host = route.get_default_gateway() File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway t1 = self._get_default_gateway_from_bin_route() File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route if def_gateway: UnboundLocalError: local variable 'def_gateway' referenced before assignment Are you connected to the Internet?
[[IMG]http://www.gigaimage.com/images/by1m3cawhw05mdnofe_thumb.jpg[/IMG]](http://www.gigaimage.com/viewer.php?file=by1m3cawhw05mdnofe.jpg)

---

