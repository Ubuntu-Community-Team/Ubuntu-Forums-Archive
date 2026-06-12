---
title: "Bluetooth printing - HP Laserjet 4 &amp; BT-200"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by mark bower on 2010-01-07
I hope with this post to help others and Eduardo Flores who tried to tackle the connection problem about a year ago.  I have been working the problem for months, asked for help in posts, but only now the solution which negates the need for BlueSoleil which i used with XP.  

The hardware of interest is BT dongle, BlueTake 200 printer adapter and a HP Laserjet 4.  The key to making the bluetooth connection in 9.04 and 9.10 is as follows:

1) Determine MAC addr of the BT-200 with "spdtool browse" in a terminal(retain for ref)
2) Sys/Pref/Bluetooth/<select the BT-200 when detected>/click fwd/close
3) Sys/Admin/Printing/New/<select your BT device shown/click "fwd"/select HP/select driver "hpijs pcl3,3.9.8[en]
[in the event that your BT device and printer are not automatically selected as in 3) then try:]
4) Sys/Admin/Printing/New/<select"Other"/<enter in the URI block "bluetooth://<Mac Addr of BT-200> without colons/continue the set-up by selecting HP LJ4 or LJ4P and driver "hpijs pcl3,3.9.8[en] 

i can now move completely to the linux (Ubuntu) platform save for ACAD2000 (which i still will try to get to work under WINE).

mark

---

