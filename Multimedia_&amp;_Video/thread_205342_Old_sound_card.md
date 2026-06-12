---
title: "Old sound card"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by treehopper29 on 2006-06-28
I have a pretty old sound card that ubuntu didnt recongnize during the install.

Analog Devices
AD1845JP
soundport
9524
B35572.1-0.6

thats all the info I got of the card. Is there any way to get it to work?

---

### Post by LordRaiden on 2006-06-28
It says support undetermined on the ALSA page.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Analog_Devices#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Analog_Devices#matrix")

Though looking at 1847 and 1848 you could try the ad1848 driver.

Type this into a shell: ```
sudo modprobe snd-ad1848
``` 
Wait a few seconds (30 sec), then do ```
aplay -l
```

If a soundcard is listed, then try to play something (make sure master channels aren't muted). If it works, add the line "snd-ad1848" to your /etc/modules file.

---

### Post by treehopper29 on 2006-06-28
When i did the sudo modprobe... command i got the "no such device"
I'm not very adept at thiss kinda thing do i need to download the driver from that site

---

### Post by LordRaiden on 2006-06-28
Try this, I'll be adding it to my post here [http://www.ubuntuforums.org/showthread.php?t=205449]("http://www.ubuntuforums.org/showthread.php?t=205449") shortly. You'll be installing 2 debs.


```
sudo apt-get install build-essential alsa-source linux-headers-$(uname -r) module-assistant
sudo dpkg-reconfigure alsa-source
``` 

You'll now be presented with a big list of drivers to choose from. Deselect all with the Space Bar, then select ad1848 with the space bar then press enter.

Finally, follow these commands

```
sudo module-assistant a-i alsa-source
``` 
Got the instructions from here [http://ubuntuforums.org/showthread.php?t=181186]("http://ubuntuforums.org/showthread.php?t=181186")

---

