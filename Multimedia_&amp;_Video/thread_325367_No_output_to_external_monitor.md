---
title: "No output to external monitor"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by pedromdsantos on 2006-12-25
I am using Ubuntu 6.10 in a Asus L4500 (L4R) with an ATI Radeon Mobility 9100.

I need to make presentations with my notebook using an external monitor. All function keys (volume, brithness, etc) work fine except Fn+F8 that allows the output to the external monitor.

For now the solution is to plug the monitor on boot but I loose the output to the LCD, it is very annoying because I must reboot and only have one monitor with the output.

I try to change xorg.conf adding two option lines but without sucess, simply loose the output for the LCD.

[INDENT]Option "MonitorLayout" "CRT,LFP"[/INDENT]
[INDENT]Option "Clone" "true"[/INDENT]

Can anyone give me some help to solve this problem.

Thanks

Pedro Santos

---

