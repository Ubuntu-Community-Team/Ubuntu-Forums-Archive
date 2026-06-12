---
title: "ubuntu 13.10 freeze due to XBMC"
date: 2013-11-10
forum: Multimedia Software
---

### Post by fube00 on 2013-11-10
Hi there,

I'm using Ubuntu 13.10, and after some time XBMC is running (I always listen to radio) , the system feezes. i.e.: the display freezes, mouse & keyboard don't respond, and the last half-a-second of the song that was playing would loop. It happens both with xbmc in fullsreen mode and not.
The moment this happens is totally random, but it is systematic. 

I have seen a very similar post:
[http://ubuntuforums.org/showthread.php?t=2143839&highlight=xbmc+crash](http://ubuntuforums.org/showthread.php?t=2143839&highlight=xbmc+crash)
suggesting to have a look at log files:

here an excerpt of /var/log/syslog at the time the crash happened. Then I had to reboot:

Nov 10 12:21:05 fube-HPTC NetworkManager[730]: <info> (eth0): IP6 addrconf timed out or failed.
Nov 10 12:21:05 fube-HPTC NetworkManager[730]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 10 12:21:05 fube-HPTC NetworkManager[730]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 10 12:21:05 fube-HPTC NetworkManager[730]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 10 12:51:35 fube-HPTC dbus[581]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Nov 10 12:51:35 fube-HPTC dbus[581]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov 10 12:53:07 fube-HPTC dbus[581]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Nov 10 12:53:07 fube-HPTC dbus[581]: [system] Successfully activated service 'org.freedesktop.UDisks'
Nov 10 13:03:11 fube-HPTC kernel: [ 2558.905138] perf samples too long (2532 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Nov 10 13:17:01 fube-HPTC CRON[2667]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 13:21:37 fube-HPTC kernel: [ 3665.462627] perf samples too long (5012 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
Nov 10 13:24:49 fube-HPTC kernel: [ 3857.323861] [drm:i915_hangcheck_elapsed] ***ERROR* stuck on render ring**
Nov 10 13:24:49 fube-HPTC kernel: [ 3857.323868] [drm] capturing error event; look for more information in /sys/kernel/debug/dri/0/i915_error_state
Nov 10 13:24:49 fube-HPTC kernel: [ 3857.327446] [drm:i915_set_reset_status] ***ERROR* render ring hung inside bo (0x3417000 ctx 1) at 0x34171c8**

NB. log file: /sys/kernel/debug/dri/0/i915_error_state contains:
"no error state collected"

Is the system freeze due to the above error in bold? Are they related to what? Graphic management??

Any idea, suggestion or support is very welcome!

Thanks!

fube00

---

