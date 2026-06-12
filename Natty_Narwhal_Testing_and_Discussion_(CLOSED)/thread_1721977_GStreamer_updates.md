---
title: "GStreamer updates"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-04-05
Anyone having issues with the ugly GStreamer plugins?

---

### Post by dinamic1 on 2011-04-05
> **mdhollis said:**
> Anyone having issues with the ugly GStreamer plugins?

installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 316491 files and directories currently installed.) 
Preparing to replace gstreamer0.10-plugins-ugly 0.10.17-1 (using .../gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_i386.deb) ... 
Unpacking replacement gstreamer0.10-plugins-ugly ... 
dpkg: error processing /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_i386.deb (--unpack): 
 trying to overwrite '/usr/share/locale/af/LC_MESSAGES/.mo', which is also in package gstreamer0.10-plugins-bad 0.10.21-1ubuntu10 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_i386.deb

---

### Post by yorkie on 2011-04-05
gstreamer ulgy update failed to down load wait for next updates it may be fixed

---

### Post by FoundmyTux on 2011-04-05
Yes. Get the following error message:

Preparing to replace gstreamer0.10-plugins-ugly 0.10.17-1 (using .../gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_amd64.deb) ...
Unpacking replacement gstreamer0.10-plugins-ugly ...
dpkg: error processing /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/locale/af/LC_MESSAGES/.mo', which is also in package gstreamer0.10-plugins-bad 0.10.21-1ubuntu10
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mdhollis on 2011-04-05
Same here.  When I tried to report it to launchpad I encountered Bug 741370	aptd crashed with OSError in _copy_io_master(): [Errno 9] Bad file descriptor.

---

### Post by thiebaude on 2011-04-05
I just got those updates like 5 minutes ago, but i did not get any error messages.

---

