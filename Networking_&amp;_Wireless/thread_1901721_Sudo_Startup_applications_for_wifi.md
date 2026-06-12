---
title: "Sudo Startup applications for wifi"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by marisdembovskis on 2011-12-29
My problem:
When pc starts, it does not connect ad-hoc wifi network. I need manually go to Network-Manager and clck wireless, then choose needed one, Edit, Apply. So then it connect.
How to make it connect automatically?


1. sudo su
2. gedit /etc/rc.local
3. Paste this:
/etc/init.d/network-manager stop
rfkill unblock wifi
/etc/init.d/network-manager start
4. Save 
5. Reboot

---

