---
title: "possible error in ndiswrapper guide"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by skale on 2006-07-13
Is the **sudo depmod -a** command really necessary? For starters, the man page does not show any -a extention. Second, I could not get ndiswrapper to work at all. **ndiswrapper -l** would show the driver, then after that nothing went right. I then emptied /etc/ndiswrapper/ and all, and followed the guide exactly, except I skipped that line, going straight to **sudo modprobe ndiswrapper **and it worked great. I don't know a whole lot about this, so I doon't know.

---

