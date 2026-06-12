---
title: "Help with WiFi installation driver"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by Panati on 2013-08-04
Hello guys!


Im a superb noob into the Linux OS and its distros. I've been using windows for ages but now I want a safer and lighter OS so here I am! 


The thing is that my old notebook HD just died on me and I installed Ubuntu 12.04 on a 16GB pendrive to boot the PC and use it from there, however I cannot seem to get the wireless drivers for it. I've been reading the forum for a while but since the coding thing isn't in my nature I decided to ask... Here's the code I got from running the "wireless_script.txt" file.


[http://pastebin.ubuntu.com/5949583/](http://pastebin.ubuntu.com/5949583/)



Any help is greatly appreciated.



Thanks.



Panati.



PS. English isn't my mother tongue therefore I apologize in advance for any grammar mistake.



edit: I have 4gbs for persistence memory so i guess it should be fine. Btw (sorry if this is a silly question) isn't there a way to use the whole pendrive memory (or at least more than the 4GB allowed by the FAT32 partition?).

---

### Post by wildmanne39 on 2013-08-04
Hi, it says it is hard blocked which ususally means your wireless switch is off, if you do not have a wireless switch then it is probably turned on by a key combinaton for example fn+f5.
Thanks

---

### Post by carl4926 on 2013-08-04
The driver is there
Just try
```
sudo [COLOR=#000000][FONT=Droid Sans]rfkill unblock all[/FONT][/COLOR]
```

These Fn switches can be problematic

Also worth trying > power off > pull the power cord and the battery > wait a min > reconnect and re-try>>...

---

