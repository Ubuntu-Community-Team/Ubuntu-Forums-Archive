---
title: "Wireless not working (typical problem that I got fixed a while ago, but now persisten"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by arthurcolle on 2012-12-16
:lolflag:I installed Ubuntu 12.10 as my primary OS on my primary computer. I am currently using my sister's computer with Windows 7 on it to download files off the internet and put them on a USB (depending on what instructions I am told to do from you guys/ladies).

I was able to install ndiswrapper, ndiswrapper utils, bkms, and a bunch of other packages (because some had dependencies) from the LIVE CD that I used to install Ubuntu a few hours ago.

I am pulling my hair out trying to get my Broadcom b43 drivers installed.

I followed these instructions:
[http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)
but when I used the command "sudo rmmod -f b43" I got an error "No such file exists"

If anyone can help I would greatly greatly appreciate it.

Ethernet is not an option becuase I have no ethernet cable, but again, I have another computer that I am using to type this and get files that are requisite. So if anyone could not immediately tell me to use "sudo apt-get" to get stuff that would be appreciated haha.

Thanks!

---

### Post by chili555 on 2012-12-17
> but when I used the command "sudo rmmod -f b43" I got an error "No such file exists"That simply means the module b43 wasn't loaded, so couldn't be removed. Not a problem.

If you wouldn't object, I'd like to see some diagnostics to be sure we don't fix the wrong thing or miss something. Please run and post:```
lspci -nn | grep 0280
lsmod | grep -e ndis -e b43 -e wl
ls /lib/firmware/b43 | head -n3
```Thanks.

---

