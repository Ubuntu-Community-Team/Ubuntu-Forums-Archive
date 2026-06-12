---
title: "Wireless networking doesn't work after battery died"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by richard_hughes2 on 2013-08-25
My laptop was running on battery and shut down when the battery died.  After connecting to the mains the computer restaterted with Ubuntu (after a while) but the wireless networking no longer works.  It tries to connect, waits about a minute, then disconnects.  It worked fine before the battery died.  Any suggestions?

---

### Post by wildmanne39 on 2013-08-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by richard_hughes2 on 2013-08-25
Returning to it after about an hour I find that wireless networking works again (this was after repeated failed attempts to connect). It even continues to work after a reboot.

Scratching my head.

---

