---
title: "Removing the ndiswrapper driver to use the original."
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by Hralgmir on 2011-05-20
I had to spend a while to figure out how to do this, with Ubuntu 10.10 as the OS, so thought I would reveal my formula for success. I had installed ndisgtk 0.8.5-1 and it's related packages ndiswrapper common 1.56-3 and ndiswrapper-utils-1.9 1.56-3 with Synaptic. Loading the new driver with ndiswrapper was simple, but I wanted to go back to the original Linux version after trying it. Selecting and uninstalling the .inf file in the window was easy, but the previous driver would not work. In /etc/modprobe.d/ there is a file called ndiswrapper.conf which is ndiswrapper's alias for the wireless device, but it may forget to undo this when you remove the driver. Navigate to this folder in the terminal, type sudo gedit ndiswrapper.conf and comment out the contents with a # at the start of each line. Click save to save. Reboot, and the inbuilt driver works again. It should be possible to reverse this change easily too if you want to try something using ndiswrapper again.
I was using a Belkin F5D8013ED PCMCIA card. I copied the XP2K and Vista32 folders to /opt/Belkin, but they could go anywhere convenient. The Ubuntu 10.10 rt2800pci driver allowed b g n wireless, but the rt2860.inf one in XP2K on the CD only supported g. The netr28.inf file in Vista32 on the Belkin CD caused the OS to freeze whenever the card was inserted. If it was in place at boot up it wouldn't boot.
 Typing info ndiswrapper-1.9  into the terminal (info ndiswrapper and man-k ndiswrapper are also helpful) suggests ndiswrapper.conf is apparently the location where ndiswrapper writes an alias for wlan0 (or whatever number applies) so the ndiswrapper kernel module is loaded whenever this interface is used.
  I later noted some lines of code briefly appearing during boot up, that I had not seen before using a G - card.
This was due to the rt2800pci driver being loaded, which is not the correct one for this card, and it will only establish the wireless connection at short range. Once connected it then switches to N wireless. The solution was simple, add the line 'blacklist rt2800pci' to the end of the /etc/modprobe.d/blacklist.conf file and the rt2860 driver module is loaded instead on the next boot. This will connect and operate in N and works very well. The Belkin F5D8013ED has the Ralink 2760 chipset, but the rt2860 name is just an abbreviation as it covers a variety of chipsets, including the 2760.
There could be a better way to switch off ndiswrapper, although it does not appear in Boot Up Manager's list. It is useful for me though, as I was reluctant to uninstall ndiswrapper as if this had not restored operation of the inbuilt wireless drivers, I had no ethernet port to easily reinstall it. Having disabled ndiswrapper, it is clear uninstallation would have worked, but finding an off switch is useful. I have had ndiswrapper on my system now for some months disabled in this manner, with no ill effects noticed.

---

