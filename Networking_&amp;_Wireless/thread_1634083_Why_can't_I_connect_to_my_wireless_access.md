---
title: "Why can't I connect to my wireless access?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by alephhat on 2010-11-30
So I have a functioning driver. I just enabled the proprietary driver under system-admin-hardware drivers. My wireless is a BCM4322. I pointed it at my invisible access point by filling in the SSID and setting the mode (infrastructure). I then set the the security to WPA & WPA2 Personal and put in the appropriate key (noticing that they didn't have an option to set TKIP or AES). 

When I click on it from the menu to connect it animates the wireless signal as though it is looking for a bit and then a window pops up stating that the connection requires authentication. I know that I have that right... I even changed the password at the access point just to be sure on one of my attempts. I don't understand why it is unable to establish a connection.

I am using Ubuntu 10.04 LTS Desktop

---

### Post by uncaspi on 2010-11-30
You have probably not downloaded the latest STA driver.It isn't in the repository yet. The file is 
hybrid-portsrc_x86-32_v5.60.246.6.tar.gz  from Broadcom site.
This is version 5.60.246.6 and should work if you follow the instructions
in the README.txt file.

---

### Post by bkratz on 2010-11-30
Also, you might check your access point again and see if it is set up for combination wpa/wpa2 or just wpa or just wpa2. Sometimes the combination mode doesn't seem to work correctly. I have to set mine to WPA2 with AES only to get a reliable connection.

---

### Post by TBABill on 2010-11-30
Will it connect without encryption of any kind? Worth trying just to be sure there is no conflict, then just tweak the security settings till they work.

---

### Post by alephhat on 2010-11-30
> **bkratz said:**
> Also, you might check your access point again and see if it is set up for combination wpa/wpa2 or just wpa or just wpa2. Sometimes the combination mode doesn't seem to work correctly. I have to set mine to WPA2 with AES only to get a reliable connection.


Sure enough, apparently combination mode doesn't work properly. Unfortunately now I have to make sure all of my other devices are set to work with the change, but thats the nature of the beast lol... On the plus side that shouldn't be too much of a problem and now the wireless is working :)

---

### Post by uncaspi on 2010-11-30
Hi, just remember to put solved on the thread. Goto thread tools.;)

---

