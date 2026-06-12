---
title: "wireless broken after upgrade to 10.04 and after reinstall of 9.10"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by manfrom3004 on 2010-06-09
I recently upgraded Ubuntu 9.10 to 10.04 and my wireless stopped working. It can detect that there are networks around, what their signal strength is, and then try to connect to one, but it just keeps connecting. After around 5 minutes, this stops and nm-applet says no network connection.
After I try to connect, dmesg is spammed with hundreds of the same message. I can not post these here, as I am writing from a different computer and I have no internet access from my main computer.
Also, there is nothing in interfaces.conf other than lo. For some reason, my card is referred to as both wlan0 and wmaster0, with this changing depending upon where I look.

Most interesting of all is that, even after I reinstalled 9.10, wireless is still broken, even though it wasn't before. It also used to work under liveCD, but now it doesn't. I tried liveCDs all the way back to 8.10, but none work, even though they all worked before. I have no other systems installed on my computer, so I can not check there.

Thank you in advance

Also, I will be unable to access the Internet for up to a month, so please don't lock this thread just because I didn't reply for a while.

---

### Post by Iowan on 2010-06-09
I presume you've checked the BIOS to verify the adapter is enabled - I don't see why it would have changed, but it also seems odd that a re-install of an older, working versions no longer works.

---

