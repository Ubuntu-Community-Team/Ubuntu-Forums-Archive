---
title: "Simple solution to wireless disconnects?"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by Shriner on 2011-03-13
I recently upgraded from JJ to LL. After the upgrade my wireless starting dropping a lot. I did some reading and found that this was a common occurrence. I seem to have solved the problem by turning off the power saving feature. (it been only an hour, but no drops yet)

Check  to see if it is on with "iwconfig"

My wireless interface was wlan0, yours may be different, note it and use yours in place of wlan0, if needed, in the following to turn it off.

"sudo iwconfig wlan0 power off"

Hope this works for those having the problem.

---

### Post by Shriner on 2011-03-15
I just found out that this solution doesn't hold through a reboot and must be repeated. :(

---

### Post by TBABill on 2011-03-15
Sometimes a conflicting driver can also lead to disconnects. Some users find they have a Realtek driver for their model plus the RT2x00 enabled and it doesn't always cause a "can't connect" situation, but sometimes does cause frequent, constant disconnects.

---

### Post by Shriner on 2011-03-15
I looked for conflicts and found none, but that's not to say that I didn't miss it. The only RealTek driver that I find installed is for my eth0 (correct) and one for my Linksys WUSB54G (correct) on wlan0. I found no others.

---

