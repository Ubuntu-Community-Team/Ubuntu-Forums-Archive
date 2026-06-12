---
title: "VLC jerky stream"
date: 2011-07-11
forum: Multimedia Software
---

### Post by vodas89 on 2011-07-11
Hello,

Im trying streaming video with vlc and this is how i do it:

**sudo -u user vlc --vlm-conf vlm_export --intf telnet -vvv --file-logging --logfile vlc_log --file-caching 5000 --daemon **

vlm_export:
new bunny1 broadcast enabled loop
setup bunny1 input "big_buck_bunny_pal.ts"
setup bunny1 output #udp{dst=224.1.1.1:11111}

new bunny2 broadcast enabled loop
setup bunny2 input "big_buck_bunny_pal.ts"
setup bunny2 output #udp{dst=224.1.1.2:11111}

This command is executed every startup. My problem is that sometimes (and i don't know why) **stream is jerky and chopped**. Basically it is very very bad. Another time everything is O.K. BTW I've got two streams, every has 15Mbps bitrate. Here is error from my logfile: 

**access_output_udp warning: send error: Resource temporarily unavailable**

Have you guys some advice what i can do with it ? Do you think it could by network capacity problem ? Or network switch? Igmp?

---

### Post by vodas89 on 2011-07-12
I get this answer on VideoLan forum .. 

**"Weird error. I guess the kernel output buffers are full. Try to increase the limit in /proc/sys/net/whatever"**

Can someone help me with this ... i think this is beyond my knowledge of linux :/

---

