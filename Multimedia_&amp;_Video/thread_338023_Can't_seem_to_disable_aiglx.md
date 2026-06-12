---
title: "Can't seem to disable aiglx"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by katzman on 2007-01-13
Hi;
I have noticed that since i reinstalled edgy about a month ago i can't disable aiglx. I am using the xorg file from my previous install when it would turn it off no problem.

how do i know it is still on?
beryl will run with --force-aiglx
if i vnc onto my server with a video running, the video image gets sent ot the vnc viewer rahter then just a blue box as it is with proper direct rendering. This is the symptom that orignally keyed me into the aiglx problem in my previous install

i have the server flag AIGLX off set in my xorg but this doesn't due it.

Specs
Edgy,
Nvidia geforce 6600 go with latest nvidia drivers
kernel compiled from vanilla 2.6.19


 cat /var/log/Xorg.0.log|grep -i aigl
(**) Option "AIGLX" "off"

---

