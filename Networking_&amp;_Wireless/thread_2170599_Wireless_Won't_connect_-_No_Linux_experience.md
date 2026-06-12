---
title: "Wireless Won't connect - No Linux experience"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by leah2 on 2013-08-26
I got a computer for my son in which the previous owner had installed Ubuntu 12.04.  The factory OS is Windows 7.  We are completely unfamiliar with Linux/Ubuntu.  When trying to connect to our wireless the wireless light flashes endlessly until eventually the computer gives up trying to log on.  What can we do?  I have seen postings asking similar if not same question, but I am having trouble following the answers as I have NO experience with Linux.  The laptop is a HP Elitebook 6930.

---

### Post by wildmanne39 on 2013-08-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by nico7 on 2013-08-27
Here is the information, thank you so much for your help. I changed accounts, just so there is no confusion I'm the same person...

---

### Post by wildmanne39 on 2013-08-27
Please copy and paste for accuracy one line at a time:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

It should try to connect now, it is still best to change the other settings as well.

Also:
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless
```

I recommend that you go into your router and change the encryption to just wpa2 if you have that option it works best with ubuntu.

If you change the encryption in the router also go into the network manager settings in the top right corner of the screen and click on the internet icon then edit connection, wireless and change security settings to wpa/wpa2

In a lot of cases you can enter the router set up by typing 192.168.0.1 into your web browser but you will need to be wired to the router first.
Reboot
Thanks

---

