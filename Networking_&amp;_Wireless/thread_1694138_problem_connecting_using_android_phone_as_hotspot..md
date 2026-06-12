---
title: "problem connecting using android phone as hotspot..."
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by jjb945025 on 2011-02-23
Hello all.I was wondering if anyone out there could figure out what's wrong when I attempt connecting to the web using this android 2.2 phone I got from sprint..I am using ubuntu lucid lynx and sprint hasn't a clue when it comes to linux OSs..anyway I enable the phone as a hotspot,but this turns off wifi on the phone for some reason I'm unfamiliar with, then I open network conn. In linux..I'm not sure wether to goto the wireless or the mobile broadband tab to change things..I tried punching in commands I've seen in these forums into terminal to make something happen but have no luck.I am posting in this forum using my only connection to the web,the android phone which is a samsung intercept so I cannot copy and paste the outputs of codes entered in terminal,though can't I post a .jpeg of the monitors screen to let you guys know what's happening?, I. Will try that..I've also ,when attempting to connect, had the droid phone near a window but this I will try to continue to do as much as possible,as there is no data connection,only power,when I connect all of the usb cables. Together to get the phone near the window.thus I have to stay near the desktop,using 1 usb cable between the computer and the droid phone.any help would be greatly. Appreciated..thanks in advance..

---

### Post by taiang on 2011-02-24
When you use your phone as a wi-fi hotspot, it will operate exactly like a wireless router; so, to manage this connection on your ubuntu box you'll be messing with the Wi-Fi tab, not the Wireless Broadband. Wireless broadband is usually for USB modem type devices, which is not the case.

Also, the phone turning off the wi-fi to enable wireless routing is the expected behavior, nothing off there. All it means is the device is ceasing to use the wi-fi radio to connect itself to a network, and is operating as a wi-fi hotspot instead.

I had to mess around with the portable wi-fi hotspot settings to get my HTC going as a hotspot. What I did was go into Settings -> Wireless and Networks -> Portable Wi-Fi hotspot settings, and started doing tests from there, working one thing at a time. You can access more settings by pressing the menu key and selecting 'Advanced'. In the end, the following settings worked for me:

Basic settings:
Router name (SSID): I did not have to change this.
Security: WEP (128)
Password: Left it on the default, which is '1234567890abc'. Please don't steal my wi-fi if you're sitting next to me :D.

Advanced settings:
Wi-Fi channel: Worked just fine on auto. Just as a side note, you can change this to a channel you know is less used by other nearby networks, so as to get less collisions/interference. There's a host of apps on the market to scan the wireless channels around you and tell which are less occupied.

Lan settings:
IP address: used 192.168.1.1, which is the default, I believe.
Subnet mask: 255.255.255.0
DHCP: enabled
Starting IP: 192.168.1.10
Power mode: Disable after 10 mins of inactivity

Those were the exact settings I used, but you may find that you have to try different settings on your setup. A few ideas:
- disabling DHCP and manually configuring the connection on your linux box, giving it a local IP address (such as 192.168.0.100), and using your phone's IP address as gateway.
- Trying out all different wireless security settings. You may find this works fine if you just leave security off, though this is less than ideal.

I hope you manage to sort it out!

---

### Post by jjb945025 on 2011-02-25
Thanks for your feedback but I still have no luck.don't I need drivers for wireless?did they come with the install of the os? Also, do I need to disable. The ethernet port? If so,how? I also can't find out how to turn wifi on/off in lucid lynx..

---

### Post by jjb945025 on 2011-03-03
yeehaw!!! i figured it out. thanks for the help anyway people...

---

### Post by cjpetrie on 2011-06-14
Could you please post your fix? Sony Vaio X upgraded to 11.04 with 2.6.38-8-generic i686 which improved some features but which introduced a serious WiFi problem: while my office WiFi works well, connecting via my DROID hotspot fails consistently despite reboots of everything and renaming of SSID. I also disabled security. No change. But Wifi works well at my office. Another laptop running 10 still works fine on the Droid. One hint: upon upgrading, there was the warning that the laptop hardware did not support Unity and I always get the classic Gnome display.
Atheros AR9285 Wireless Network Adapter
Qualcom Sony Gobi 2000 Wireless Modem
ifconfig shows no packets with wlan0 or any connectivity.
iwconfig shows correct SSID and other info.
dmsg shows "wlan0: direct probe to f8:7b:7a:2b:a7:d1 timed out"
Restarting the network has no effect but there is a message that 
"Running /etc/init.d/networking restart is dprecated because it may not enable again some interaces"
I don't find this same problem in the forum so perhaps it is some configuration error on my part. Please comment if you have any clues.

---

