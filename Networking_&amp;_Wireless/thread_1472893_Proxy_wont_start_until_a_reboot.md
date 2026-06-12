---
title: "Proxy wont start until a reboot"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by kenweill on 2010-05-04
Everytime i start my computer, proxy server (with transparent proxy) wont start at first boot. It produces an error when i tried to start it manually (from webmin).

```

2010/05/05 05:51:58| parseConfigFile: squid.conf:4970 unrecognized: 'httpd_accel_host'
2010/05/05 05:51:58| parseConfigFile: squid.conf:4971 unrecognized: 'httpd_accel_port'
2010/05/05 05:51:58| parseConfigFile: squid.conf:4972 unrecognized: 'httpd_accel_with_proxy'
2010/05/05 05:51:58| parseConfigFile: squid.conf:4973 unrecognized: 'httpd_accel_uses_host_header'


```

Rebooting the computer fixed it. 
Is there a way to make it work the first time i turn on my computer?

Those errors, httpd_accel, i enter those manually in squid.conf.

---

### Post by kenweill on 2010-05-04
Problem solved. I commented those lines and transparent proxy is still working, to my surprise.

Maybe Squid 2.7 don't need those lines anymore with transparent proxy.
Maybe "http_port 3128 transparent" is all it needs for transparent proxying.

---

