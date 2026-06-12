---
title: "ridiculously low FPS with motion"
date: 2013-03-21
forum: Multimedia Software
---

### Post by vaderj on 2013-03-21
not sure what is going on, but this is happening on both my server and my workstation (8 core AMD and 4 core AMD respectively) - both are running 12.04, fully updated.
Both have standard ebay USB webcams, both webcams run at a full 30FPS in Cheese with out issue, with out causing any stress on the CPU, yet when I fire up motion I get exactly 1FPS through the built-in web-server, no more, no less, regardless of any configuration options that I have so far thrown its way.
My motion.conf is as follows, and it is verified that motion is reading my config file:

webcam_port 8081
webcam_localhost off
width 640
height 480
output_normal off
low_cpu 0
framerate 10
#webcam_motion 10



anyone have any ideas? 1FPS is just unreasonable.
Thanks!

---

### Post by vaderj on 2013-03-22
Woot!  

After a few days of research, I finally found the answer here: [http://www.raspberrypi.org/phpBB3/viewtopic.php?t=36614&p=306592](http://www.raspberrypi.org/phpBB3/viewtopic.php?t=36614&p=306592)

By defining in motion.conf:

webcam_maxrate 25

the issue resolved

---

