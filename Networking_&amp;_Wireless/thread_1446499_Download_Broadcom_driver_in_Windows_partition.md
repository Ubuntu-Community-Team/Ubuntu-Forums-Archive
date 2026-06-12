---
title: "Download Broadcom driver in Windows partition"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by evadwolrab on 2010-04-04
I have a desktop with a wireless card and no way of getting my machine online. I have a Windows 7 partition which works fine though.

Is there any way to download Broadcom drivers as executable files, so I can boot into Ubuntu and find it on the Windows partition?

---

### Post by chili555 on 2010-04-04
It depends entirely on what Broadcom you have. There are four, that I know of, ways to get Broadcom cards working, depending on the version. This thread may give you some insight:  [http://ubuntuforums.org/showthread.php?t=1438038](http://ubuntuforums.org/showthread.php?t=1438038)

I have always wanted to find an adventurous dual-booter like you, to see if a little cheat might work. The only thing that keeps your Broadcom from working is not the driver, but the proprietary firmware. If your card is working in Windows, then you must have the firmware on there, right? Maybe it's different and maybe it won't work, but we will never know until you try.

If you are game, let's find out what firmware your Broadcom is missing. If this is a laptop, be sure the wireless switch or key combination are pressed to activate the wireless radio. Open Applications > Accessories > Terminal and do: ```
dmesg | grep firm
```You will probably learn that your Broadcom wanted and failed to load ucode5.fw or some such.

Now look for that file on your Windows 7 partition. Can you find it, make a copy of it and move it over? Let me know and we'll proceed. This might be pretty slick!

---

