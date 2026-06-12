---
title: "No network access in 9.10"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by ccornett on 2009-10-29
I just installed 9.10 over 9.04 and now I have no network access at all. I did have both Ethernet and wireless in 9.04. The cards are detected but nothing works. Machine is a Sony Vaio FE-790P. Network card is an Intel PRO/100 VE, and the wireless card is Intel PRO/Wireless 3945ABG. The network card shows "disabled." Any help is appreciated. I am not quite a newbie but not advanced either.

---

### Post by BarisBlaq on 2009-10-29
Not too sure, but maybe this
[http://ubuntuforums.org/showthread.php?t=1304900](http://ubuntuforums.org/showthread.php?t=1304900)

---

### Post by ccornett on 2009-10-29
Thanks for the reply. I tried the procedure listed (downloaded new grub files) but it didn't fix the problem.

---

### Post by ticstah on 2009-10-30
This fix didn't work for me either. I'm currently reinstalling 9.04 until this bug is fixed or a better workaround is found. I'm bummed, 9.10 looks gorgeous! I hope this is resolved soon! It seems like a show stopper.

---

### Post by zeroseven0183 on 2009-10-30
I just finished fresh installing Karmic Koala on my laptop. It had 9.04 a while ago, worked so good for me. Initially after the installation, my wireless connection is not available. What I did is to hook it to wired connection, go to System > Administration > Hardware Drivers to check for available hardware drivers and thankfully, there's an available one for me. Downloaded it, restart the machine and I'm now good to go.

---

### Post by amebix01 on 2009-10-30
I experienced the same problem after a fresh install on a Vaio with similar hardware, I fixed the issue by manually changing the dns address via the network manager, I used Opendns and works well.
I think this problem is related to the last kernel version and probably is going to be automatically fixed with the next kernel update.

---

### Post by ticstah on 2009-10-30
> **amebix01 said:**
> I experienced the same problem after a fresh install on a Vaio with similar hardware, I fixed the issue by manually changing the dns address via the network manager, I used Opendns and works well.
I think this problem is related to the last kernel version and probably is going to be automatically fixed with the next kernel update.

That'll be great. However, if the version of the kernel that is on the installation disc won't let me get online, how would I receive the update?

---

### Post by ccornett on 2009-10-30
Gave up on Network Manager and uninstalled it. Installed Wicd [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/") and was up and running in five minutes on both wired and wireless. Had to download the deb pkg on another computer and write it to a cd (which Ubuntu recognized with no problem) and install it from there.:D

---

### Post by amebix01 on 2009-10-31
> **ticstah said:**
> That'll be great. However, if the version of the kernel that is on the installation disc won't let me get online, how would I receive the update?

Change the dns and then update.

---

### Post by halchen on 2009-11-12
I've experience the problem also! I'm sure it is a bug in 9.10. However, it is pretty easy to fix:
1. Configure IP to make network work temporarily:
o ifconfig eth0 x.x.x.x netmask 255.xxx.xxx.xxx
o route add default gw x.x.x.x eth0
o edit /etc/resolv.conf to configure DNS
o test to make sure Internet works.
2. Go to System->Administration->Update Manager to download the latest updates. My installation came from the iso downloaded a few days ago, I found it still has more the 40 updates need to be installed.
3. After completed the updated. Reboot computer.
4. Now, you are able to configure IP through the GUI interface. You need to uncheck "Enable Network", then check it again to reset the network.
Good luck!

---

