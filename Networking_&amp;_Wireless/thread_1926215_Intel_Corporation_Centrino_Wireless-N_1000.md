---
title: "Intel Corporation Centrino Wireless-N 1000"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by Tawrtoise on 2012-02-15
My problem is that my centrino wireless-n 1000 is not working with Ubuntu 11.10. I know this problem has come up a lot in the past, however, after hours of research, I am finding that my situation is actually unique (as far as I can tell, and I'm running out of patience to continue googling). In Ubuntu, all of the normal wireless connections are showing available, but when I try to connect to any of them it simply times out (every time). I know a previous work around would be to use an older kernel and whatnot, but what makes my situation a bit unique is that earlier today (when I was running WIndows 7) it did not work either. On Windows 7, when I was troubleshooting it gave me the message that the IP address could not be configured (that is not verbatim). Upon looking this up online, I finally came to ipconfig in cmd prompt to see the lovely message of "Media Disconnected" (and all other attempts at trouble shooting came to an end with a helpful message only Windows could provide stating, "There may be a problem") which I could find no fix for. 

If any of you have any ideas as to how I could fix this it would be greatly appreciated.

---

### Post by chili555 on 2012-02-16
Let's get the easy stuff out of the way first. Please open a terminal and run and post:```
rfkill list all
dmesg | grep iwl
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by Tawrtoise on 2012-02-16
Well, nevermind. In spite of all the evidence towards the issue being inside my computer, it was actually the modem (which doesn't make any sense because there were three other computers working last night, while mine was not, but oh well) and it was fixed this morning.

Thanks anyways.

---

