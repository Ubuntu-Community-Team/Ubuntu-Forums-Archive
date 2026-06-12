---
title: "Wired connection doesn't work"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Uewd on 2011-07-06
These days I wanted to connect to the internet on my laptop using a wired connection. When I inserted the ethernet cable, I was surprised to see that it doesn't work on Ubuntu 11.04. So I decided to boot into Windows and see if it works or not. And I found that it works without problems on Windows. Please help me solve this problem in Ubuntu.

---

### Post by dandnsmith on 2011-07-06
I'm willing to bet that you had to set up Internet Connection Sharing to get the Windows version to work - why should Ubuntu be any different.

There is help [here](https://help.ubuntu.com/community/Internet/ConnectionSharing). Have a read, and then come back with any questions you have unanswered.

---

### Post by Iowan on 2011-07-06
From a terminal (Applications>Accessories>Terminal) you can check **sudo lshw -C network** for information about your hardware. **ifconfig -a** will show interfaces (whether active or not) - you cn see if the wired connection is getting an IP address. More information about your network might be helpful - are you connecting to a router, modem, or another computer?

---

