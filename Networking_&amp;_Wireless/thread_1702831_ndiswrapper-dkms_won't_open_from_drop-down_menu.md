---
title: "ndiswrapper-dkms won't open from drop-down menu"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by pottzie on 2011-03-08
I have (had?) ndiswrapper-dkms installed, and used it to get a wireless card working. After a kernel update, the card stopped working, and I tried to re-install it. Part of the directions included doing -r to about everything connected to the original install. Now I still show "Windows Wireless Drivers" in the drop-down menu, but when I click on it, it "flashes" for a split-second, and then disappears. I've tried re-installing it from Synaptic, and doing "sudo apt-get install ndiswrapper-dkms" but it just returns saying that I already have the latest version. I can't get it to load or run.

---

### Post by pottzie on 2011-03-09
Solution provided by downloading ndisgtk, ndiswrapper-common and ndiswrapper-utils, and moving them to a directory I created in my home directory. Then going to that directory using the "cd" command and running "sudo dpkg -i *.deb"
 
 Thanks to K3ltO1 and linuxquestions. org

[http://www.linuxquestions.org/questions/showthread.php?p=4283512&posted=1#post4283512](http://www.linuxquestions.org/questions/showthread.php?p=4283512&posted=1#post4283512)

 I have trouble reinstalling every time a new kernel installs, and I have to redo the driver. Hope Linux gets N type receivers going someday.

---

