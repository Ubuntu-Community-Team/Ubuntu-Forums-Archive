---
title: "D-Link DWA140"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Coruba67 on 2008-12-13
Hi Guys

Had some major problems trying to get this little D-Link Dongle working (it uses the RT2870 chipset from RA Link) so I thought I would share with ppl what I did to get it working...  I found bits and peices everywhere so hopefully others may find this useful.

Firts of all grab the new drivers from ralink. (google ralink - get linux drivers)


Unpack into a folder. 



Edit the file <your_folder_name>/os/linux/config.mk

Change the following lines:



-----------------------------------------

# Support Wpa_Supplicant

HAS_WPA_SUPPLICANT=y



# Support Native WpaSupplicant for Network Maganger

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=ynow go into the root of your folder and:

-----------------------------------------



Save the file and go back into terminal



sudo make && sudo make install



To autostart the interface just do the following:


Code:


sudo gedit /etc/init.d/rt2870up



Paste this into the File:
 (the file should be empty to start with)


#-------------------------------------------------------

#!/bin/sh



sudo ifconfig ra0 up

#-------------------------------------------------------



Save and go back to terminal



cd /etc/init.d


sudo chmod +x rt2870up

sudo ln - s /etc/init.d/rt2870up /etc/rcS.d/S33rt2870up

sudo rm /etc/Wireless/RT2870STA/RT2870STA.dat



Reboot

You should be good to go.  Hope this helps!

---

### Post by sidral on 2008-12-19
Hello,

I had the same problem but then I followed the instructions in this link and it worked perfect in my Network Manager:

[http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

I hope that can help.

---

