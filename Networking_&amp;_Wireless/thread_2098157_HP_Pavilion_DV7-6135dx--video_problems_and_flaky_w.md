---
title: "HP Pavilion DV7-6135dx--video problems and flaky wireless"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by stevewilson on 2012-12-25
I've got a Pavilion dv7-6135dx.  It has two graphics chips - a lower power and quality Intel and a high quality and power ATI.  I installed Kubuntu 12.04.1 and after doing all the upgrades, installing 'other drivers' and then finally doing a 'sudo aticonfig --initial' finally got the video working off of the ATI chip - an important thing since much of what I got that laptop for IS video.  So that was working, but every time I put the laptop to sleep, as soon as it woke up, the wireless was gone.  I tried every solution I could find online and every one I could think of, but nothing helped.  Then I read on here about a SIMILAR problem and the possible solution of upgrading to 12.10.  So I tried it.  When I restarted, my X display was gone - the server just failed.  So I logged on in text mode and went to /etc/X11 and copied the backup xorg*conf back to xorg.conf and did a startx.  The xserver started fine, but of course there was no ATI driver section, so I went through installing the driver and the 'sudo aticonfig --initial' again.  I restarted and again had no xserver.  So, just for the hell of it, I recopied the xorg*.conf backup again and restarted the xserver and put the computer to sleep and woke it to see if THAT part had worked.  It hadn't.  So, long story short, upgrading to 12.10 not only didn't solve the wireless loss issue but it lost me the ATI use that 12.04.1 had made possible.  So, the only choices I see open to me now are re-installing 12.04.1 or sticking with Windows.  
Happy holidays!

---

