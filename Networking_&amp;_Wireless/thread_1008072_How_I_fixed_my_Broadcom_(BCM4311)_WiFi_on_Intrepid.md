---
title: "How I fixed my Broadcom (BCM4311) WiFi on Intrepid (8.10)"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by crossr1 on 2008-12-11
This might be a duplicate post.

I have been trying to get my Broadcom BCM4311 Wireless Card working for two days with WPA2 Encryption on a completely NEW install of Ubuntu 8.10 ( Intrepid ). I tried searching all the Ubuntu forums and bug reports with no avail. I discovered that my Wireless Card was running an old version of the F/W that is incompatible with the Broadcom drivers that are installed with Ubuntu 8.10 by default. Fortunately, I stumbled on this web-site to fix it:

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

:lolflag:

**_NOTES:_** 
- Ubuntu has its own command according to this web-site. I would recommend using it. 
- FYI Only --> I used "**sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh**".

**_The web-site doesn't talk about several things:_**
**1) What commands to run to fix the 'b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found' error that was being placed in the /var/log/kern.log file.**

_The Fix:_
sudo updatedb
locate ucode5.fw    (This is a check to make sure the update command took)

**2) When to reboot your system to make the Firmware load into the Wireless Card.**

_The Fix:_
Reboot after running the locate command that is in step 1.


Once I rebooted, the new F/W was loaded as my system and the card has been functioning fine ever since.


**_Laptop Configuration:_**
Dell D620
Intel T7200 CPU
2GB RAM (667Mhz)
160GB HDD (SATA 5400RPM)
Quadro NVS 110M
XVGA+ (1440x600) LCD Display
Broadcom NetXtreme BCM5752 Gigabit Ethernet PCI Express Card
[COLOR="Red"]**_Broadcom BCM4311 802.11b/g WLAN Wireless Card (AKA Broadcom 1390)_**[/COLOR]

Notes on H/W: 
- More detailed Hardware Listing and Log Files are attached if someone needs them. 
- I have zeroed all of the Serial Numbers and MAC numbers.

Thanks,
Richard

######################################################################

Broadcom Cards that are **_supported_** (From Web-Site):
    * bcm4303 (802.11b-only chips, uses b43legacy)
    * bcm4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43)
    * bcm4309 (only the 2.4GHz part)
    * bcm4311 rev 1 / bcm4312
    * bcm4311 rev 2 / bcm4312 (needs patches for 2.6.24)
    * bcm4312 (only the 2.4GHz part)
    * bcm4318
    * Note: Broadcom has used some of the BCM43XX designations for more than one flavor of card. To tell for sure if your card is supported, use the command 'lspci -n' and find the line that has the string "14e4:XXXX'. If XXXX is 4301, 4307, 4311, 4312, 4318, 4319, 4320, 4321, 4324, or 4325, the card is supported. All others are NOT supported. 

Please read the web-site for more information. FYI, I included this list to provide tags for searching only. So, I expect it might change.

---

### Post by Ayuthia on 2008-12-11
Just to clarify, Ubuntu does not come with the firmware installed for the b43 driver because the firmware is propietary.  Because of this, the error message about missing firmware occurs.  To fix the issue, you can enable the b43 driver by going through System->Administration->Hardware Drivers and select the Broadcom b43 option.  You will need a working internet connection to make it work.  Once this is installed, the missing firmware message will go away.  

The updatedb command is not needed.  The kernel attempts to load the firmware file and if it can't find it, it will post the message.

---

