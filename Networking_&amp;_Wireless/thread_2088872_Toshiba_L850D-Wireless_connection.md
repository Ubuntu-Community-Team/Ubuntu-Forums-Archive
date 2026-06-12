---
title: "Toshiba L850D-Wireless connection"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by capateke on 2012-11-27
I am running Ubuntu 12.04 from a USB stick in demo mode and cannot get a wireless connection. The Network menu does not show "Enable Wireless". The wireless cards installed on the Toshiba L850D are Realtek RTL8101E/RTL8102E. The wired connection is working fine. Any suggestions would be welcome. PS  The host OS is Windows8

---

### Post by Abhinav Kumar on 2012-11-27
> **capateke said:**
> I am running Ubuntu 12.04 from a USB stick in demo mode and cannot get a wireless connection. The Network menu does not show "Enable Wireless". The wireless cards installed on the Toshiba L850D are Realtek RTL8101E/RTL8102E. The wired connection is working fine. Any suggestions would be welcome. PS  The host OS is Windows8
Hi capateke,
Type in the following code in a terminal to see if your wlan and bluetooth are unblocked
```

sudo rfkill list

```

If everything is ok, check if you have proper wireless drivers or not. 12.04 is having some problems with realtek 8101 drivers. Try looking at this thread
[http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200)

Regards,
Abhinav

---

### Post by wildmanne39 on 2012-11-27
Hi, this>  Realtek RTL8101E/RTL8102Eis your ethernet card.

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by capateke on 2012-11-28
Thanks for the quick response Wild Man. Is this the file you need?

---

### Post by wildmanne39 on 2012-11-28
Hi, do what is in post 6 of this link and it should get you going.
[http://ubuntuforums.org/showthread.php?t=2040656](http://ubuntuforums.org/showthread.php?t=2040656)
Thanks

---

### Post by capateke on 2012-11-30
Hi Wild Man,
After entering second command I got message "unable to locate package linux-headers-uname -r" What next? Incidentally I have now gone for the full installation of 12.04LTS and ditched Windows8.

---

### Post by capateke on 2013-01-16
Problem solved. Driver downloaded
[I]wget -o- http:/dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar. gz | -xz
[/I]and installed
[I]cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
sudo make install

[/I]

---

### Post by ncsailor on 2013-03-02
I have a Toshiba L850D and have tried the suggestions here, without success.  When I loaded 12.04lts I could not get a wired or wireless network connection.  Going through the forums here I was finally able to get a wired connection, and then a wireless connection through a Netgear WG111v2 USB device.  It appears that some peopl have the built-in device working.  As I said, I have done what was suggested with no success.  Does anyone have any other suggestions or places to look?  This laptop was custom built and I just received it.  So the problem is probably that it has an updated realtek chipset.

---

### Post by jaber426 on 2013-03-03
thank

---

