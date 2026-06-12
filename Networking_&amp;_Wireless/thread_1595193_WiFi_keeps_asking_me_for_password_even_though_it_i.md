---
title: "WiFi keeps asking me for password even though it is correct"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by cycrosism on 2010-10-13
I try to connect to my access point and after a long wait of maybe 30 seconds to a minute it will prompt me to enter my password. I entered it correctly and it still keeps on asking me to enter it. So just then I entered it with the password showing and double checked over it before trying again and it still didn't connect.

I need to have internet on my netbook working by tonight or I will have to go back to windows.

What can I do to make my laptop connect to my access point? Its not a problem with my access point, my desktop running windows, it connects just fine to my wireless.

Here is part of my syslog

> 
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto vor' has security, 
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  Config: added 'ssid' value 'vor'
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Oct 13 15:46:04 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 13 15:46:09 mark-eeepc wpa_supplicant[813]: Trying to associate with 00:1e:b5:a2:b6:00 (SSID='vor' freq=2447 MHz)
Oct 13 15:46:09 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 13 15:46:09 mark-eeepc wpa_supplicant[813]: Association request to the driver failed
Oct 13 15:46:14 mark-eeepc wpa_supplicant[813]: Authentication with 00:1e:b5:a2:b6:00 timed out.
Oct 13 15:46:14 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Oct 13 15:46:14 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 13 15:46:19 mark-eeepc NetworkManager: <info>  wlan0: link timed out.
Oct 13 15:46:19 mark-eeepc wpa_supplicant[813]: Trying to associate with 00:1e:b5:a2:b6:00 (SSID='vor' freq=2447 MHz)
Oct 13 15:46:19 mark-eeepc wpa_supplicant[813]: Association request to the driver failed
Oct 13 15:46:24 mark-eeepc wpa_supplicant[813]: Authentication with 00:1e:b5:a2:b6:00 timed out.
Oct 13 15:46:24 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Oct 13 15:46:24 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 13 15:46:29 mark-eeepc wpa_supplicant[813]: Trying to associate with 00:1e:b5:a2:b6:00 (SSID='vor' freq=2447 MHz)
Oct 13 15:46:29 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 13 15:46:29 mark-eeepc wpa_supplicant[813]: Association request to the driver failed
Oct 13 15:46:34 mark-eeepc wpa_supplicant[813]: Authentication with 00:1e:b5:a2:b6:00 timed out.
Oct 13 15:46:34 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Oct 13 15:46:34 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 13 15:46:39 mark-eeepc wpa_supplicant[813]: Trying to associate with 00:1e:b5:a2:b6:00 (SSID='vor' freq=2447 MHz)
Oct 13 15:46:39 mark-eeepc NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 13 15:46:39 mark-eeepc wpa_supplicant[813]: Association request to the driver failed
Oct 13 15:46:43 mark-eeepc NetworkManager: <info>  (wlan0): device state change: 5 -> 3 (reason 39)
Oct 13 15:46:43 mark-eeepc NetworkManager: <info>  (wlan0): deactivating device (reason: 39).
Oct 13 15:46:44 mark-eeepc wpa_supplicant[813]: Authentication with 00:00:00:00:00:00 timed out.


I never use to have wifi problems when I used windows, so if I cannot fix this problem by tonight (Currently 4PM where I am) then I will have to install windows back onto my netbook

---

### Post by wilee-nilee on 2010-10-13
right click on the wireless icon-edit connections, open your wireless and click on always allow and all users.

---

### Post by viper250 on 2010-10-13
your password may be correct  is your essid typed in correctly?
had this problem setting up wireless before and it turned out one of the characters was a capital letter (it gave me fits for a few minutes until I figured it out)

anyway your eepc detected the wireless so we know its working but its deactivating it
this may be a driver issue.
what version of ubuntu are you using?
you should also post the info of your hardware.
this will give us a better idea of whats going on

---

### Post by cycrosism on 2010-10-13
> **viper250 said:**
> your password may be correct  is your essid typed in correctly?
had this problem setting up wireless before and it turned out one of the characters was a capital letter (it gave me fits for a few minutes until I figured it out)

anyway your eepc detected the wireless so we know its working but its deactivating it
this may be a driver issue.
what version of ubuntu are you using?
you should also post the info of your hardware.
this will give us a better idea of whats going on

I didnt need to type in the essid it detected it fine, so yes it is correct. Are there some special drivers or something I need for this to work?

I am using: Ubuntu 10.04 - Lucid Lynx

I don't know much about the info of my hardware, but this netbook has a wireless adapter which has a rt2860 chipset if I recall correctly. The name of my netbook is an "Asus EEEPC 1000H" If I recall correctly.

Edit - This wifi problem also existed when I used 9.04. I removed 9.04 and installed windows because i was sure this problem would be fixed in later releases. From 9.04 to 9.10 to 10.04 this problem still exists

---

### Post by viper250 on 2010-10-13
> **wilee-nilee said:**
> right click on the wireless icon-edit connections, open your wireless and click on always allow and all users.

try his suggestion

---

### Post by cycrosism on 2010-10-13
That didn't work.

This problem is becoming really frustrating as I have to complete some work and I need my wifi to work soon

---

### Post by AggravatedGestalt on 2010-10-13
Well, I see no one has posted in a while, so I will litter the thread with a link: [http://www.uluga.ubuntuforums.org/showthread.php?t=1477392](http://www.uluga.ubuntuforums.org/showthread.php?t=1477392)
I am beneath this issue and have no good ideas, but you might at least have a look at the link above, and do the following: Google-ing  "rt2860 ubuntu solved" yielded results discussing WPA errors, so I suspect you might find some info there if you are in a rush. Good luck, until someone saves the day.

---

### Post by cycrosism on 2010-10-13
Thank you for that link, but I am unable to change any encryption settings on my access point, so all the changes I have to do must be done on Ubuntu in order to get that to connect, as it is not a problem with my access point, it is a problem with Ubuntu.

The reason I say I cannot change it is because I do not know the password to my access point and am not allowed to change it is my dads.

---

### Post by cycrosism on 2010-10-13
Ok well if there is no solution but for me to change my encryption type then I will have to go back to windows. Unless, someone can tell me how to fix it?

---

### Post by Grenage on 2010-10-13
Given how many times you've said "I will have to go back to windows", you should probably go back to windows.

---

### Post by cycrosism on 2010-10-13
> **Grenage said:**
> Given how many times you've said "I will have to go back to windows", you should probably go back to windows.

I really want to stick to Ubuntu, but it is a bit hard without any internet access .... My WiFi was working great for 1-2 weeks after I installed Ubuntu but now it won't even connect ... like at all...

I want to keep going back to windows as a very last resort, only if I absolutely have to

---

### Post by Grenage on 2010-10-13
Can you not gain access to the router 'at all'?  Your Dad can always reset the password again afterwards.

---

### Post by cycrosism on 2010-10-13
I can't gain access to my router or access point, so it is not possible for me to change the encryption type - the most I can do is try to fix the problem at the source

---

### Post by Grenage on 2010-10-13
The problem is, the source might not be Ubuntu.  I've had issues with wireless access points that worked fine on one OS, but wouldn't connect with iphones or other kit (kept asking for the password) - simply because the channel or encryption type was causing problems.

Short of deleting the access point in Ubuntu and adding it manually, I don't know what to suggest.  You *could* try installing wicd. and use that to connect.

---

### Post by cycrosism on 2010-10-13
I've tried deleting the entry for it and reconnecting but the password box keeps popping up asking me to enter it ... :(

Oh and I can't really install anything since I have no internet on it

---

### Post by Grenage on 2010-10-13
Can you not plug a cable in?

---

### Post by cycrosism on 2010-10-13
No I cannot as I have no spare cables. I hope this problem gets fixed soon though because I want to keep using Ubuntu

---

### Post by Grenage on 2010-10-13
You could download wicd as a deb, but there may well be dependencies.  You're pretty much stuck unless you can plug in the machine, or get access to the router.

It's not necessarily an Ubuntu-specific fault, and you're working with one hand tied behind your back.

---

### Post by cycrosism on 2010-10-13
While searching around for a spare cable I found a USB wifi dongle, and I plugged this into my netbook and I got the password prompt and after I entered the password prompt, success. It works.

But the original problem is still alive. Well I did some googling and found a page which recommends I installed the following package

```
aptitude install linux-backports-modules-wireless-lucid-generic
```

I installed it, and restarted and took the USB wifi dongle out and it connected with my original netbook card, so it works!!!

This problem has been solved (For now). If it stops working again ill either post in this thread or made a new one. Thanks for all the help guys. It is much appreciated.

---

### Post by Grenage on 2010-10-13
Glad it works.  I've had issues with wireless on an old laptop, but I can always get it working with a wired connection, followed by an update.

---

