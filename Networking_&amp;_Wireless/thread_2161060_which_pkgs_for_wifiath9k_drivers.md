---
title: "which pkgs for wifi/ath9k drivers?"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by mentos7 on 2013-07-09
hi there - i purchased an N PCIe wifi card from thinkpenguin  (Atheros AR9281) to put into my DELL inspiron.  i upgraded from 10.04 LTS to 12.04 LTS and all was good.  wlan0 was immediately recognized and i was on my wifi network.  however...  a few days later, i was trying to install and debug a citrix client issue and apt-get told me to autoremove several old pkgs which weren't needed anymore.  later that day, i had a power outage, and no more wifi.  iwlist doesn't see wlan0; lspci doesn't see wlan0.  my suspicion is that i removed a pkg containing drivers for wifi and/or ath9k, though it's possible these 2 events are not related.  i don't have a wifi pie shaped icon on my desktop anymore.  nm-applet still shows my wireless connection, there is simply no more wlan0.  any suggestions are much appreciated! thanks!

---

### Post by wildmanne39 on 2013-07-09
Hi, I suspect it was due to the power outage it probably corrupted part of your hard drive.

Please copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by mentos7 on 2013-07-09
ok, here's my system info

---

### Post by wildmanne39 on 2013-07-09
There is no wireless card showing up.

Can you check and make sure it is seated properly?

You may want to put it in another slot if you have one.

Check your bios and make sure wireless is on if you have that option, you may have to reset the bios.
Thanks

---

