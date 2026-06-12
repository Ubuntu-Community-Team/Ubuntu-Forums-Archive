---
title: "pulseaudio eating too much cpu in 9.10 release"
date: 2010-01-05
forum: Multimedia Software
---

### Post by mbadola on 2010-01-05
pulseaudio in this new "karmic" release eating too much cpu, and make the system's response time higher.
without playing any audio file here is the top output::
----------------------------------------------------------------
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 1713 manoj     20   0  155m 4980 3676 S **50.9**  0.2  23:25.29 **pulseaudio                                                                                      **
  434 syslog    20   0 34720 1644 1004 S 47.6  0.1  20:49.71 rsyslogd                                                                                        
 1089
----------------------------------------------------------------
I was looking for workarounds and came to know that there exists some memory leak bugs too for this same pusleaudio ([Bug #424655]("https://bugs.launchpad.net/ubuntu/karmic/+source/pulseaudio/+bug/424655"))
Is someone also notice or face this problem, if anybody knows any workaround please let me know.

---

