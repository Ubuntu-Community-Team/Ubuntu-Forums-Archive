---
title: "Have 2 Wifi Cards Installed"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by gsgkill on 2010-07-12
Purchased a Comfast 300M usb 1000mw Wifi adapter. Had a hell of a time figuring out how to get it to work. The CD driver was missing from the package. Took it apart and saw chip set Rt2870F. Installed virtual box and installed winxp. Tracked down the drivers to china [www.ralink.com.tw]("http://www.ralink.com.tw") which was an execute file and ubuntu would not run it. So I installed them in XP under virtual box. Enabled looking in hidden files under view options. Searched for rt2879.* Found the rt2870.cat, rt2870.sys, rt2870.inf.  Went to hotmail and attached the files to an email back to myself. Hotmail would not send the INF for security reasons. So I open a dos command window under XP and renamed the inf file to rt2870.xxx, then attached it to the email and sent it to myself. Under Ubuntu 10.04 I used the windows wireless drivers to install the INF.
It works, I can see the wifi adapter working the windows wireless driver program sees it is there. But I have yet to figure out how to point to it instead of the PCI d-link in my computer. Do I have to take the d-link out? Or is there a way to point to the comfast adapter for my wifi connection?

---

