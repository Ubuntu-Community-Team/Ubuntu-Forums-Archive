---
title: "aircrack injection problems"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by paveway on 2010-01-27
Hello to all, i've a problem with aircrack-ng. I've bought a ACER ONE D250 and i've installed ubuntu netbook remix. I do all the upgrades avaible for the system.I've installed the b43 driver and wireless card works fine, i've also installed aircrack-ng and i'm able to put the wireless card  broadcom ([COLOR=#000000][FONT=Times New Roman][FONT=Lucida Grande]**14e4:4315) **[/FONT][/FONT][/COLOR]into monitor mode. When i try to do injection i recive an error message. Can anyone help me?
Tanks in advance
Enrico

---

### Post by Crafty Kisses on 2010-01-27
What's the error message you get? You might need the injection patch and obviously apply the patch. You can look for what patch you need right **[here.]("http://patches.aircrack-ng.org/")**

---

### Post by paveway on 2010-01-28
when i do the injection test with the command
aireplay-ng -9 wlan0 
i recive the following answer
Trying broadcast probe request...
No answer...

In the link you suggested i searched for the b43 patch but it's only for kernels 2.6.25 and 2.6.26 but not for the 2.6.31-17, that's the one i've
I don't know what to do:-(

---

### Post by Crafty Kisses on 2010-02-05
Did you initially run the following?
```
airmon-ng start eth (channel here)
```

---

### Post by paveway on 2010-02-08
yes i did, here attached you can find the program answer

paveway@box:~$ sudo airmon-ng start wlan0 11
[sudo] password for paveway: 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
775    NetworkManager
789    avahi-daemon
790    avahi-daemon
1148    wpa_supplicant
10511    dhclient


Interface    Chipset        Driver

wlan0        Broadcom    b43 - [phy0]
                (monitor mode enabled on mon0)

---

### Post by jesrul on 2010-03-10
New user here and I seem to be running into the same issue except that my braodcom card is the 14e4:4318. Can anyone help.

---

### Post by 7x1x on 2010-06-14
Hi, I'm running b43 on the 14e4:4315 card with kernel 2.6.33 and this is what got it working for me:
```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
sudo airmon-ng start wlan0 6
    wlan0        Broadcom    b43 - [phy0]
                (monitor mode enabled on mon0)
sudo aireplay-ng -9 mon0

```
Note: You might not need the ifconfig and iwconfig commands.

---

### Post by purelinuxuser on 2010-06-14
> **7x1x said:**
> Hi, I'm running b43 on the 14e4:4315 card with kernel 2.6.33 and this is what got it working for me:
```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
sudo airmon-ng start wlan0 6
    wlan0        Broadcom    b43 - [phy0]
                (monitor mode enabled on mon0)
sudo aireplay-ng -9 mon0

```Note: You might not need the ifconfig and iwconfig commands.

You don't need to run the ifconfig/iwconfig comands (as 7x1x said), you just need the airmon-ng and aireplay-ng ones.  The problem is you were trying to run aireplay-ng on wlan0, but it should be run on mon0, which is the interface that airmon-ng creates ;)

---

### Post by henyongadik01 on 2010-07-13
thanks. this also helps me.

---

