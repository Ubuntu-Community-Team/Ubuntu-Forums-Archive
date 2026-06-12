---
title: "Please help Lubuntu no wireless diagnostics pasted"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by Flanmaster on 2012-01-30
I have no wireless in lubuntu.  The following is a summary of the system, the diagnostic commands I have run, and the results:
Samsung laptop amd vision A6 quad core cpu radeon agp integrated.

additional drivers only showed the proprietary drivers for the radeon, which I have enabled.  Nothing showed for the atheros dirver.

sudo lspci -nn | grep 0280
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev ff)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
$ sudo nano /etc/modprobe.d/blacklist-ath_pci.conf

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath_pci


I realize the nano is editing the blacklist-ath_pci.conf.  I have tried it with the ath_pci active and commented out. neither works.h

Please help me.  I have done both numerous searches in forum and with google.  I know that I need the ath9k drivers but I cannot find them.  I have done sudo apt-get update, and sudo apt-get upgrade but still cannot find anything in the repositories for the ath9k.  

Thank you for help.

---

### Post by Flanmaster on 2012-02-01
Bump.  Thanks. :)

---

### Post by Flanmaster on 2012-02-03
information and "solution" (workaround really)
I found several things.  Since no one offered guidance or information I figured I'd post this in case someone else has similar or same issues. Especially considering none of my issues were "cut and dried".


[LIST=1]
[*]I had installed version 11.04 with the working graphics but no wireless
[*]evidently the solution is to install version 11.10. I couldn't find any solution within 11.04
[*]This is an [all variants] issue regarding the atheros wireless, not just Lubuntu.
[*]I have the amd a6 quad core processor with the integrated radeon gpu so a clean install results in a completely different bug of having a blank screen on boot from the disk, and even AFTER finding the work around for that I STILL had a blank screen on booting, after instalation. so I had to search for another solution.
[/LIST]
I DID find a "work around".  I'll give a summary but details can be found in the thread about the blank screen:
 [http://ubuntuforums.org/showthread.php?t=1918920](http://ubuntuforums.org/showthread.php?t=1918920)


SO, I did a clean install of version 11.04 from disk, with WIRED connection to internet.  then I did "sudo apt-get upgrade" in a terminal. after doing what was needed to prepare for the graphics and then rebooting, I put the disk for the version 11.10 in the cd, opened the update manager from the system tools (NOT synaptic), selected the "upgrade" option at the top that indicated that version 11.10 was available. 



After upgrading in this fashion, I had wireless.  



of course I had several other things to do but this is the very basics on how to get wireless working.  Some folks may be able to resolve this simply with a clean install of 11.10 but I had to jump through hoops and this is how I managed it.

---

