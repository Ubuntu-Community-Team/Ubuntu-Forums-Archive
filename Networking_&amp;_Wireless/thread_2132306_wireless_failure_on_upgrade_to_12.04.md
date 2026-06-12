---
title: "wireless failure on upgrade to 12.04"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by bugbear6502 on 2013-04-04
I have a sad little old laptop:

[http://www.immortalsgate.com/dkauk/Laptops/Siemens_Amilo_Pro_V2000.htm](http://www.immortalsgate.com/dkauk/Laptops/Siemens_Amilo_Pro_V2000.htm)

The internal wireless was not working very well for me (insensitive, kept dropping connections),
so I bought a TP-LINK  TL-WNN722N (wireless USB adapter) and plugged it in. I was running Ubuntu 11.04 at
the time. It connected immediately, and my only problem was finding
out how to permanently turn off the internal wireless. Easy.

I have now "upgraded" to Lubuntu 12.04, and simply cannot make wireless operate.

I will attempt to anticipate some requests for information:

 uname -a
Linux bugbear-fs 3.2.0-39-generic #62-Ubuntu SMP Wed Feb 27 22:05:17 UTC 2013 i686 i686 i386 GNU/Linux

 sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse

 rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

  BugBear

---

### Post by wildmanne39 on 2013-04-04
It says hard blocked that usually means the wireless switch is off.
Thanks

---

### Post by bugbear6502 on 2013-04-04
> **Wild Man said:**
> It says hard blocked that usually means the wireless switch is off.
Thanks

Yes, but that's the internal wireless. I actually want that one to be turned off, and want my USB/wireless adapter to ... do something!

Further, my laptop doesn't even have a switch - under 11.04 I had a fair bit of research to find the
code to turn the internal wireless off.

After some more flaiing around I have arrived at this (I've been rebooting and mod-probing
after googling)

```

 rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
2: phy4: Wireless LAN
        Soft blocked: no
        Hard blocked: no

 sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

```

Despite this, the network manager thing in the task bar shows BOTH wireless
interfaces as disabled by hardware switch.

 BugBear

---

### Post by wildmanne39 on 2013-04-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

I believe as long as that says blocked your usb adaptor will not work either but it may depend on the device.
Thanks

---

### Post by bugbear6502 on 2013-04-04
[ATTACH]240944[/ATTACH]

Done (I hope!)

 BugBear

---

### Post by wildmanne39 on 2013-04-04
Why do you have an eth1 connection?

Remove all of your wireless connections then reboot and see if network manager finds your wireless connection.
Thanks

---

### Post by bugbear6502 on 2013-04-05
> **Wild Man said:**
> Why do you have an eth1 connection?

Because I#m far from clear how to arrange NOT to have one.

> 
Remove all of your wireless connections then reboot and see if network manager finds your wireless connection.
Thanks

I have rebooted WITH the TL link plugged into the USB. It was not found on boot up.

I attach the results of re-running the "wireless_script"

Assuming I'm ignorant will serve you well :-(

  BugBear[ATTACH]240968[/ATTACH]

---

### Post by bugbear6502 on 2013-04-05
There's some kind of horrible cross-coupling going on.

Acting "on a hunch", I used my old knowledge to enable the built in (crappy) wireless

 sudo modprobe fsam7400 radio=1

Since I'm currently testing in the work office (near the router) this worked fine, and I could see various routers.

I then unplugged and re-plugged the USB wireless adapter.

 It worked, and showed in the network manager.

So it appears that somehow the DISABLED status of the builtin-wireless is
affecting the USB one.

   BugBear

---

### Post by wildmanne39 on 2013-04-05
Yes that is what I thought, you have to have he wireless button on for the usb adaptor to be able to work.
I believe if you have the usb plugged in at boot it will over ride the internal and be the one used.
Thanks

---

### Post by bugbear6502 on 2013-04-05
Dear $DEITY this is a common question;

I googled ***site:ubuntuforums.org internal wireless external disable***

and found an amazing variety of answers, all different.

  BugBear

---

### Post by wildmanne39 on 2013-04-05
So do you still want to disable the internal and use the usb? if so we can blacklist the internal driver and not disable the wireless with the switch.
We might could get the internal to work properly so let me know which you prefer.
Thanks

---

### Post by bugbear6502 on 2013-04-08
> **Wild Man said:**
> So do you still want to disable the internal and use the usb? if so we can blacklist the internal driver and not disable the wireless with the switch.
We might could get the internal to work properly so let me know which you prefer.
Thanks

Well, I have it working, to some extent. My current "best solution" is to enable the internal wireless (modprobe *fsam7400 radio*=1) but to then remove it from network manager, meaning it is not (practically) used (

iface eth1 inet manual in /etc/network/interfaces).

This is not a "true" solution (in that the internal card is on, but unused...) but it's certainly usable.

I should add that the whole reason for buying/using the external  USB wireless is that the internal card was insensitive and prone to dropping connections.

 BugBear

---

### Post by wildmanne39 on 2013-04-08
Please try:
```
echo "blacklist ipw2200" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Does the usb still work?
Thanks

---

