---
title: "Having to turn Wired Network Adapter On/Off"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by momspcs on 2012-05-14
I just got through installing Ubuntu 12.04. FYI it works a lot better out of the box than Ubuntu 11.10. When I attempt to open Mozilla it tells me that the server can't be found. I then click on System Settings, Network, turn the wired adapter "OFF" then "ON" and Mozilla works. I can surf the net. 
I have an Intel D845EPI/D845GVSR (both number are on the board) Motherboard. I went to Intels website and downloaded the Red Hat 9.0 Linux drivers. I unzipped them, they were ".GZ" files. I "chmod +x" the ".sh" file. I then "sudo ./filename". 
The routine errors:
 
Intel(r) Desktop Board Installer.

Starting installer, please wait...
tail: cannot open `+72' for reading: No such file or directory

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
./intel-100LAN-2.3.27.sh: 57: ./intel-100LAN-2.3.27.sh: ./install.sh: not found

Does anyone have any idea why I have to turn off then back on the wired adapter?
Does anyone have any idean about how to install the intel driver?

When working the wired adapter works flawlessly. The Ubuntu 12.04 printer routine went out and found my Windows Shared printers, something Ubuntu 11.10 would not do. 
I was able to share files and folders between Windows and Ubuntu flawlessly, something Ubuntu 11.10 would not do.
There are no issues surfing the net or downloading files

Thanks
MOM's PC's

---

### Post by roelforg on 2012-05-14
Redhat drivers (rpm based) aren't going to work on ubuntu (debian->deb based).
But check for a hw-switch on the pc, hp-laptops tend to have those on a location where you toggle them when you pick it up. Maybe you've got a similar thing?

---

### Post by bleriot13 on 2012-05-23
Hi!

I'm experiencing exactly the same situation. The only difference in my case is that I'm running a fresh Xubuntu 12.04 install.

So,to summarize, when I boot the computer the wired connection is apparently "on" but I can't reach the internet. Simply turning the wired connection off and on solves the problem. Then, everything works flawlessly.

Is there any information you want me to post? Before connecting, after, or in both cases?

Thank you!

---

### Post by momspcs on 2012-06-22
This issue has resolved itself. I can only assume that one of the numerous Ubuntu updates that I recieve on a daily basis resolved the issue.
Wish I knew who to thank.
MOM's PC's
;)

---

