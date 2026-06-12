---
title: "Wireless network can't connect after successfully routing X over PVR-350 tv-out"
date: 2007-11-26
forum: Mythbuntu
---

### Post by therealbrewer on 2007-11-26
Please help me troubleshoot my networking problem. Here's what I did:

1) Boot to mythbuntu cd, wireless works out-of-the-box, including WPA!!
2) Choose install. Default options mostly everywhere, use whole disk.
3) Select PVR-350 as capture card. Scan for channels.
4) Run Update Manager and get 60+ updates over the wireless connection.

At this point, wireless works flawlessly, roaming mode through network manager, big signal strength, couldn't be smoother. Then...

5) Follow instructions here [http://ubuntuforums.org/showthread.php?t=568074](http://ubuntuforums.org/showthread.php?t=568074) to get X running over the PVR-350 tv-out.

Everything looks good, live tv works, recording works, XFCE on my TV, BUT...now my wireless won't associate with the router. Several wireless networks (mine plus neighbors) are listed in the network manager dropdown list, but they all show no signal strength. If I choose my network, network manager tries to connect, but gives up and goes back to the wired connection after a little while. If I try to use a manual config, same thing happens when it tries to associate.

But wait, it gets weirder: While researching the trouble, I found a post that said that sometimes ACPI can interfere with this particular wireless card, so i set pci=noacpi in the grub boot menu.lst. After rebooting, the networks still show no signal strength, but then it appears that I can associate. However, although network manager indicates it is connected, I can't ping the router, can't surf, etc. i.e. not really connected.

Now, I admit that my wireless card is known to be somewhat troublesome (Eidemax with  RT61 chip), but there is no question it worked before the X over tv-out step. Sure, I could try installing serial monkey drivers or use ralink's with ndiswrapper, but it worked out of the box before! Is that too much to ask???

Does the fact that I can see all the networks, but they all show no signal strength indicate a particular type of networking problem?

I have not tried turning WPA off on my router to see if I can make a basic connection. BUT IT WORKED BEFORE...

Any ideas????

---

### Post by superm1 on 2007-11-26
Well, so can you narrow down which step from that 350 output caused it?  Perhaps do them incrementally to see if its say  the linux-ubuntu-modules package being installed or something like that.

---

