---
title: "How to Start lirc at hte same time as MythTv"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Dragonflyoh on 2007-09-04
I have mythtv frontend installed and it starts at boot up. I need lirc running to use my remote control. If I use a terminal and run:
sudo lircd -H udp -d 5000
followed by:
hdhomerun_config 10129D3B set /ir/target "192.168.1.124:5000 no_clear"
and then start the frontend everything is wonderful. All help would be appreciated.

---

