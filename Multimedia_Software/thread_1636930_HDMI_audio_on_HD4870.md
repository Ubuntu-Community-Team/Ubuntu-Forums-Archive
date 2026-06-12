---
title: "HDMI audio on HD4870"
date: 2010-12-03
forum: Multimedia Software
---

### Post by wbw on 2010-12-03
Hi everyone,

I have an ECS A785GM-M and the integrated HD4200 HDMI audio was working out of the box on a clean Ubuntu 10.04 install. After the updates and all, everything still worked just fine for a month.

Then, I installed a HD4870 with ATI DVI to HDMI adapter and the sound is not working (it works flawlessly on Windows 7, so it is not the hardware). The creepy stuff is that on Pulseaudio GUI configuration, everything looks right: ATI 48x0 HDMI is selected as output and when some sound is playing the bar moves, although there is no sound coming from the TV speakers.

I tried editing /etc/pulse/default.pa as suggested on this [link]("http://ubuntuforums.org/showthread.php?t=1009407"), but it didn't helped. I'm kind lost here, since it looks that there is nothing wrong and yet, it is not working.

Can anyone help me?

ps: I used the search box, but I couldn't find a similar thread, so I started a new one.

---

### Post by wbw on 2010-12-04
Just adding that audio is not working with both open-source and binary driver. The onboard HD4200 was tested only with open-source driver and worked perfectly.

---

