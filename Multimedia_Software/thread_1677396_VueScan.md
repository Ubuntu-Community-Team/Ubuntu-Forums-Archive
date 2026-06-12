---
title: "VueScan"
date: 2011-01-28
forum: Multimedia Software
---

### Post by TheropodWatcher on 2011-01-28
Just upgraded to 9.10 and lost the ability to use my scanner with VueScan. No help at their site or the Avasys Corp. site, where downloads of the "driver" refuse to load due to various conflicts. Has anyone gotten VueScan to work with 9.10 and how on earth did you do it? (Scanner is an Epson Perfection V500 Photo.)
 Thanks!,
 Brad:confused:

---

### Post by luigi_mb on 2011-01-28
The Avasys site had download problems, which have since been corrected.

/luigi

---

### Post by TheropodWatcher on 2011-01-29
Thanks for the reply. I have no trouble downloading the packages (.debs for 8,.10 or greater) but get the following error when installing:
Error: Dependency is not satisfiable: iscan-data
Interestingly, the plugin file installs fine.
Am I just out of luck with this combination of scanner and my version of Ubuntu?

---

### Post by xc3RnbFO8P on 2011-01-29
Did you see this thread:
[http://ubuntuforums.org/showthread.php?t=1655524]("http://ubuntuforums.org/showthread.php?t=1655524")

---

### Post by TheropodWatcher on 2011-01-29
@Ringi - thanks, that's something to keep in mind. I'm actually able to run VueScan itself (an older version) fine. It even finds the scanner but can't find the driver. It had no problems with the driver before the update. I tried installing what's available at Avasys but get the error noted in my first post. So it comes down to a driver issue for me. I can upgrade Ubuntu but will that resolve the driver issue? Looks like others made it work somehow.

---

### Post by TheropodWatcher on 2011-01-30
Whoops, looks like I didn't include the error message in my first post after all. My bad! Here it is:
Error: Dependency is not satisfiable: iscan-data
This happens when I try to load the driver from Avasys; iscan_2.26.1-3.ltdl7_i386, which is the one recommended for current versions of Ubuntu. Also I have updated to Ubuntu 10.04 LTS to see if that would help. Nope. (But I did lose my calendar program and all the windows gadgets moved to the left - what's up with that?? At least I found where my calendar data went. Never mind, those are questions for another time.)

---

### Post by TheropodWatcher on 2011-01-30
Dug some more. Looks like my problem is caused by inability to install the data package because it conflicts with the current data package already installed. So ... tried to remove that with dpkg. BUT it won't do it because it depends on the plugin which is still installed SO I tried to remove the plugin with the command suggested by Avasys and this is what happened:

sudo dpkg --remove iscan-plugin-$scanner
dpkg: warning: ignoring request to remove iscan-plugin- which isn't installed.

I'm thinking the $scanner isn't resolving to complete the name. Suggestions on how to figure out what that name is??

---

### Post by TheropodWatcher on 2011-01-30
Whoo hoo! Guessed that the $scanner should be gt-x770 based on the name of the .deb file (well, duh). It worked! and removed the plugin. Then I could use dpkg to remove the core and the data packages. Then could install the new versions of the iscan software. It all installed fine. Ran Vuescan - got my original "No driver loaded" error. Yikes. :-( However, after a reboot, everything is working fine.

Off to get a cherry RC Cola which I haven't allowed myself in weeks (counting calories ...) ;-)

---

