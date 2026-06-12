---
title: "AE 1000 Linksys driver disabled after auto-updates installed"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by elkingrey on 2010-12-09
Hello,

I recently had my AE 1000 linksys wireless adapter driver installed, the info for which can be found here:

[http://ubuntuforums.org/showthread.php?t=1630358](http://ubuntuforums.org/showthread.php?t=1630358)

But today I was presented with 142 automatic updates already downloaded waiting to be installed on my computer. I installed the updates and restarted my computer for the updates to take effect. Well, since then my wireless adapter no longer registers at all, it doesn't even recognize my router let alone connect to it. It is as inoperable as the day I got it. 

I am currently using a different computer in the house to get internet. Should I go about following the same directions I did before and reinstall the driver, or is there a more simple way?

Thank you.

---

### Post by chili555 on 2010-12-09
> Should I go about following the same directions I did before and reinstall the driver, or is there a more simple way?
Yes. Whenever a new kernel, known as linux-image, is installed, rebuild the driver against the new kernel, but add one step:```
cd download/folder/location
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe rt3572sta
```Post back if it doesn't work perfectly.

---

### Post by elkingrey on 2010-12-10
Okay. I was not sure if I needed to go back to the old thread and follow all of the directions or just follow the make clean make sudo make install sudo modprobe rt3572 commands. So I only did the few
commands you pointed out in the terminal. I was smart enough to replace the folder and location with the real folder and location names. Everything went well but when I plugged in the sudo modprobe rt3472sta command it did not do anthing. Was I supposed to plug in exactly rt3572sta or was that supposed to be replaced by an exact file or folder name? Anyways the adapter recognizes the router now but it does not connect to it so no internet.

---

### Post by elkingrey on 2010-12-10
Never mind. After some fiddling with it it is now working. Although, it seems to be showing the same network twice as being available in the network manager. I'll see what it looks like tomorrow after I start up the computer again. I'll also confirm to make sure the internet is still running well. If everything is good, I'll come back and mark as solved. Thanks again Chili! You're the man!

---

### Post by elkingrey on 2010-12-10
Okay, it seems to be back to normal now. I figured out what was wrong. I accidentally still had my OLD wireless adapter plugged in, so it was showing me one for each. 

On a side note, I have this other nagging problem that was with me since before I even upgraded. I wrote about it here:

[http://ubuntuforums.org/showthread.php?t=1636227](http://ubuntuforums.org/showthread.php?t=1636227)

Perhaps you could help me? Thanks again for the help!

---

