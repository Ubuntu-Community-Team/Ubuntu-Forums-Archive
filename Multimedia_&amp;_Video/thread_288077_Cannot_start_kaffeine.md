---
title: "Cannot start kaffeine"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by samad on 2006-10-29
Hey guys,
I have just installed Edgy Eft amd64 desktop. Xorg is using the i810 driver. I did a clean install where I removed Dapper. Everything worked fine in Dapper. All of my configurations are the same, except I have turned off DDC in the Monitor section in xorg.conf. (I have entered in all of my monitor information manually.) Xorg works fine. However I cannot start kaffeine. The loading cursor remains for a few seconds, then disappears. I ran kaffeine in the terminal, and it will immediately exit. No error or informational messages are displayed. I checked the return result (echo $?), and it is 0. I have turned off all transparency and shading options in System Settings and restarted the X server. None of this seems to have fixed the problem. Any help would be appreciated.

Samad

---

### Post by ardnut on 2006-10-30
ps -ef | grep kaffeine, is it already running?  I have to kill it on every reboot before I can run it.  I have it set to start in the  kde system tray but this cripples it on every boot for some reason.

---

### Post by B-Minus on 2006-11-05
> **ardnut said:**
> ps -ef | grep kaffeine, is it already running?  I have to kill it on every reboot before I can run it.  I have it set to start in the  kde system tray but this cripples it on every boot for some reason.

tnx i had the same issue going on, now its fixed with your help
tnx a lot

---

