---
title: "wireless can't detect my wireless connection"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by mzrk7 on 2012-11-26
I have this strange issue with my laptop so that I can detect the wireless connection of most of my neighbors, but I can't detect my own (which is like 5 meters far). The thing that's even stranger is that I could connect to it flawlessly a couple of days ago.
My laptop is an aspire 5560 with an amd a4-3300m processor. I am using xubuntu 12.10 right now.
Thank you very much!

---

### Post by Bucky Ball on 2012-11-26
What's changed in the last couple of days? Done any updates or installed new software? Changed any hardware or upgraded?

---

### Post by mzrk7 on 2012-11-26
I don't remember of any update. But hardware didn't change, and I did not any upgrade.

---

### Post by mzrk7 on 2012-11-27
This is quite annoying. Do you have any hints?

---

### Post by Y^2om&amp;#7sgP on 2012-11-27
I have found in Xubuntu 12.04, that occasionally my laptop will not pick up my wifi, If I then disable wifi from the icon, then re-enable it, it'll pick it up and connect OK.

Not sure why though??

---

### Post by NikTh on 2012-11-27
Hi ,

try to use this command to see if scan can be performed 
```
iwlist scanning
```Also you can try to manual fill the info needed at network-manager connection editor. 
```
nm-connection-editor
```Fill your ESSID and in "Wireless security" section your password and see if that helps.

Thanks

---

### Post by mzrk7 on 2012-11-27
@hattpa the problem is not that I can't find wifis. The issue is that I can find wifis of most of my neighborhood, and I could even connect to them if I had the password, but my laptop can't find my own wifi.
@Nikth  iwlist gave me
iwlist scanning
eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.
I don't know what it means actually. Anyway my password is already stored in the network manager since I had not any issues until a couple of days ago.

---

### Post by Pyrophorus on 2012-11-27
After a power failure, and trying to connect through my Blackberry
the 12.10 wifi icon, is just blank, and it won't even search, or
recognize networks

---

### Post by NikTh on 2012-11-27
Can you see your WiFi (SSID) from other devices ? (eg: mobile phone or other wireless PC) 

Are you sure that your Wifi is not switched of via the router ? 

Thanks

---

### Post by mzrk7 on 2012-11-28
Yes, I can  detect and connect to my wireless with my cellphone, and with another pc. Actually I can connect even with my laptop if I use a live cd.

---

### Post by aronwalker on 2012-11-28
What i would do is pulg your laptop into your router and look at the web based interface there - you can do this by opening up your web brouser after you have pluged it in with a standed network cable. type in something like 192.168.0.1 Or 192.168.1.1 - they vary according to the brands and models of the router. Enter your username and password and then look any settings that seem not usual. look in your advanced settings if you have to as this will show. look if your ip has been baned. (evil children or partners can sometimes do this)

---

### Post by kurt18947 on 2012-11-28
> **mzrk7 said:**
> Yes, I can  detect and connect to my wireless with my cellphone, and with another pc. Actually I can connect even with my laptop if I use a live cd.

Can you create another user account temporarily and try to connect using the temporary account?  Do you have two accounts now, one account with sudo privileges  and another for normal usage?  I'm wondering if something in a user account is causing problems.  If a fresh account can't connect either,  did an update cause the problem?   That you can connect with a live CD indicates the driver/firmware are okay.

---

### Post by mzrk7 on 2012-11-28
@aronwalker looking at the router configuration didn't show anything unusual
@kurt I created a new account, but even with that I couldn't find my wifi

---

### Post by NikTh on 2012-11-28
Hi , 
Lets see if the results of the script tell us something. Weird problem.

Please open a terminal (CTRL+ALT+T) and execute the commands below, one at time. (_Active Internet connection required, via Ethernet or something else._)

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
sudo ./wirelessinfo
```The last command will produce a file named **netinfo.txt** inside your /home folder.
Click on **"New Reply"** and attach the file. [See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

_Above is a script for debugging proposes. All your sensitive-personal data are hidden for security reasons. _

Thanks

---

### Post by mzrk7 on 2012-11-30
My issue eventually solved by itself. And the solution was the stupidest EVER. There was a blackout in my neighborhood, and after that, I could connect to my wireless:lolflag:
I want to thank all of you who helped me out in this situation, and showed me some solidarity :D

---

### Post by Bucky Ball on 2012-12-01
The blackout would have power cycle devices like the router and modem by switching off and back on again and then ... connection! Not so far fetched and glad it sorted. Good luck. ;)

---

