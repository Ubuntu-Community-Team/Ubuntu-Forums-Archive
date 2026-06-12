---
title: "Wireless Card Not Recogized"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by rtrahan on 2008-12-17
Wireless Card Not Recognized 

--------------------------------------------------------------------------------

I loaded Ubuntu over Vista a couple of hours ago and cannot get the wireless card to be recognized. I downloaded and loaded Device Manager but to no avail. I type in I think was a lsw command with some switches based of another website and I got the hardware info but still cannot get it to work. I also checked the hardware compatibility but no luck as I cannot tell exactly what my wireless card is, it does not specifically say wireless adapter..here's what I got, when I typed in the command; Network Unlcaimed; description Ethernet Conroller; Product AR242X, 802.11abg Wireless PCI Express Adapter. Also another adapter; Netlink BCM5787M Gigabit Ethernet PCI express. 
Any help would be greatly appreciated, I am intermediate computer user but never used Linux.
Thanks in advance.

---

### Post by lovelyvik293 on 2008-12-17
You have a atheros AR242X wifi card.To get it working have a look on:-
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)



Or you can install the MADWIFI drivers for this card,
[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by rtrahan on 2008-12-17
I downloaded mad-wifi to a USB how do I get I install it on Ubuntu?
Thanks in advance

---

### Post by lovelyvik293 on 2008-12-17
For Madwifi see:-

[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

If you have Ubuntu 8.10 you can also use this method:-
> 
if you are on Intrepid and still cannot use wifi with an Atheros card , you need to do two things, 1) install linux-backport-modules and 2) blacklist ath_pci and ath_hal.

To install the backport modules, just search for it on Synaptic or use apt-get or aptitude, it&#8217;s called linux-backports-modules-intrepid. Then on System/Administration/Hardware Drivers make sure Atheros driver is activated.

    sudo aptitude install linux-backports-modules-intrepid

To blacklist the old modules, do this:

    gksudo gedit /etc/modprobe.d/blacklist

And add the following lines At the bottom of the file save and exit

    blacklist ath_hal
    blacklist ath_pci 

Now you need to reboot your system.

IF after this steps you still cannot make it work, you probably have something left still blacklisting ath5k, thus making it not to load. You should search all the files on /etc/modprobe.d for all lines that had:

blacklist ath5k

And add a # before the start of the line, thus making it into a comment so the above one becomes

    # blacklist ath5k

Save and exit the file

I hope this help for some one to fix their wireless problem.

---

### Post by rtrahan on 2008-12-17
ok I'm getting closer I have madwifi copied to my desktop. how do I extract the files? I clicked on the madwifi folder and clicked extract but nothing. remember this is my second day with Linux so be gentle :0

---

