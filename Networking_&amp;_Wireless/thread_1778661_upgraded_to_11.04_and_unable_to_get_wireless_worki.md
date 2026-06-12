---
title: "upgraded to 11.04 and unable to get wireless working"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by GrandVizier on 2011-06-09
I read through a bit of the other posts suggesting solutions to this problem:
[LIST]
[*][Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal)]("http://ubuntuforums.org/showthread.php?t=1604868") [*][No wifi after upgrade to 11.04 on Acer Travelmate]("http://ubuntuforums.org/showthread.php?t=1737996") 
[*][Wireless "device not ready"]("http://ubuntuforums.org/showthread.php?t=1478181")
[/LIST]
but I'm still without wireless.

One issue that I've seen a bit and might have something to do with the problem is that in the dropdown from the status bar, the Wireless Network sometimes says "wireless is disabled by hardware switch". Other times is either "device not ready" or "wireless disabled".

From the Solution to Broadcom 43xx Card Problem post, I tried
> System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close
and received the error message: [COLOR="DarkRed"]E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1[/COLOR] This is what I found when I viewed details on that message:
```
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4357
14e4:1690)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
	                                                      Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4357
14e4:1690)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
```


Running [FONT="Courier New"]lspci -vvnn | grep 14e4[/FONT] 
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57760 Gigabit Ethernet PCIe [14e4:1690] (rev 01)

```

---

### Post by TBABill on 2011-06-09
Can you open the dashboard and search for "Additional Drivers"? That's the ubuntu app that will search for your hardware and offer you any available drivers to install. 
 
If you want to test whether it will work WITHOUT changing your machine at all, just boot the live CD, go to additional drivers (while NOT hooked to the net) and select the driver and activate it. Once it is done it will tell you to reboot....but DONT!! Instead, if you chose the b43 driver, just ```
sudo modprobe b43
``` and wait for about a minute and see if the system then recognizes any networks. If you installed the STA driver, then instead of doing modprobe b43, do a ```
sudo modprobe wl
``` and see if you get any networks offered.
 
Edit: if this works and you can see networks with one of the drivers, then you can just go back into your normally installed Ubuntu confident that following the same steps while connected via wired ethernet will result in the same performance.
 
Note: the reason for not being connected in the live environment is that the LiveCD actually has firware and drivers available. You CAN connect and do the same if you'd like, but the LiveCD option is nice if you don't want to be connected but still try to install drivers. For some reason, this does NOT work for me in Kubuntu or Xubuntu, but works fine in Ubuntu with my BCM4312 Broadcom.

---

### Post by GrandVizier on 2011-06-11
thanks for your reply but there was no resolution from that 

here is a screenshot of the Additional Drivers app - it had the same setup in Maverick as well - [http://postimage.org/image/2jro2h2uc](http://postimage.org/image/2jro2h2uc)
[IMG]http://postimage.org/image/2jro2h2uc/[/IMG]

and executing the modprobe commands had no noticeable effect

Note: I have no problem connecting via wired ethernet

---

### Post by GrandVizier on 2011-06-14
Help!
So is it simply that the wireless card isn't supported because PCI ID is 14e4:4357 - and if so do I need to report it as a bug? And will it get fixed, or should I just reinstall 10.10 (which I don't have a copy of...)

---

### Post by bkratz on 2011-06-14
Post 44 of this thread has a pretty good description

[http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by GrandVizier on 2011-06-17
thanks bkratz - between post #44 and the subsequent post #55 on that thread, my wireless is now working

---

