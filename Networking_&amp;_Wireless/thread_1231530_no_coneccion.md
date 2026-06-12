---
title: "no coneccion???"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by astra2000 on 2009-08-04
Hello :)

I have install apache + mysql +php on my server (Debian) , and now i have one problem,
sommetimes wenn i tried follow the adresse "www.mypage.com" (this is an example), i get a 404 error , but wenn i tried to follow the internal ip "192.168.1.102" the server works, and start to work as well by "external".


so i was go checking de log ( /var/log/messages/ )  and i see the folowing code:
```
Aug  2 07:35:02 Bit3 kernel: imklog 3.18.6, log source = /proc/kmsg started.
Aug  2 07:35:02 Bit3 rsyslogd: [origin software="rsyslogd" swVersion="3.18.6" x-pid="1817" x-info="http://www.rsyslog.com"] restart
Aug  3 07:35:12 Bit3 kernel: imklog 3.18.6, log source = /proc/kmsg started.
Aug  3 07:35:12 Bit3 rsyslogd: [origin software="rsyslogd" swVersion="3.18.6" x-pid="1817" x-info="http://www.rsyslog.com"] restart
Aug  3 19:44:40 Bit3 kernel: [272460.369389] e100: eth0: e100_watchdog: link down
Aug  3 19:44:54 Bit3 kernel: [272474.850213] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  3 19:44:58 Bit3 kernel: [272478.981221] e100: eth0: e100_watchdog: link down
Aug  3 19:45:00 Bit3 kernel: [272481.186027] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  3 19:45:08 Bit3 kernel: [272489.512926] e100: eth0: e100_watchdog: link down
Aug  3 19:45:10 Bit3 kernel: [272491.673126] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  3 19:46:48 Bit3 kernel: [272594.087381] e100: eth0: e100_watchdog: link down
Aug  3 19:48:02 Bit3 kernel: [272670.390138] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  3 19:48:14 Bit3 kernel: [272682.756204] e100: eth0: e100_watchdog: link down
Aug  3 19:48:16 Bit3 kernel: [272684.846126] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  3 19:51:06 Bit3 kernel: [272863.807449] e100: eth0: e100_watchdog: link down
Aug  3 21:56:28 Bit3 kernel: [280759.881800] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  4 07:35:01 Bit3 kernel: imklog 3.18.6, log source = /proc/kmsg started.
Aug  4 07:35:01 Bit3 rsyslogd: [origin software="rsyslogd" swVersion="3.18.6" x-pid="1817" x-info="http://www.rsyslog.com"] restart
```



and on the log " /var/log/apache2/access.log
i have this:
```
404 301 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; pt-PT; rv:1.9.1.1) Gecko/20090715 Firefox/3.5.1"
::1 - - [03/Aug/2009:18:44:17 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:44:18 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:44:19 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:45:41 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:45:42 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:45:43 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:45:44 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:45:45 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:45:46 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:46:13 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:46:44 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:46:50 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:46:53 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:46:54 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:46:59 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:47:03 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:47:06 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:47:08 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:47:09 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:18:47:10 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:18:24 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:18:41 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:18:42 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:18:43 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:18:44 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:20:00 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
::1 - - [03/Aug/2009:19:20:18 +0200] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_perl/2.0.4 Perl/v5.10.0 (internal dummy connection)"
```


i dont know why its appenig this...

It's possibel that someone was tried to hack whith DOS-Attack ???

someone can help me?

---

