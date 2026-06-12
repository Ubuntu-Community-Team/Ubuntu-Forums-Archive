---
title: "wireless driver"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by Hogeyfur on 2010-04-09
I have the source code to create a wireless driver. This came with the cd for my adapter but i dont know what to do. any help????

btw while i'm in ubuntu i will not have a wired conection to the net seeing as my routers down stairs and i dont have a cable long enough to reach

---

### Post by chili555 on 2010-04-09
Please tell us what the name of the file is. Maybe we have a better way. Is it a USB adapter? Please insert the device and open a terminal and do:```
lsusb
```Post the result and we can proceed.

---

### Post by Hogeyfur on 2010-04-09
yeah its usb

did that already 

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 004 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bc2:2300 Seagate RSS LLC 
Bus 002 Device 003: ID 05ac:1293 Apple, Inc. 
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by chili555 on 2010-04-09
> [COLOR="Red"]148f:3070[/COLOR] Ralink Technology, Corp.Your device is claimed by both rt2870sta and rt2800usb and they conflict. Let's do some tweaking. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three new lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and see if your wireless device is working.

---

### Post by Hogeyfur on 2010-04-09
partial succsess

wireless is now on and picking up connections but when i try and connect it just keeps displaying the small circle that shows it trying to connect and after about a minute a prompt comes up asking me to enter the password

when i do that it just loops the problem again 

any ideas???

---

### Post by chili555 on 2010-04-09
Is it WEP or WPA? How many characters?

---

### Post by skyeric on 2010-04-09
I'm at the same point picking up connections but not being able to connect, if i make my network open it works staight away but right now using WPA Personal security it loops the password again and again in exactly the same way as you describe.

---

### Post by Hogeyfur on 2010-04-09
Security type: WPA2-Personal
Encryption type: TKIP
8 digits in the password

---

### Post by chili555 on 2010-04-09
Assuming your wireless interface is wlan0, may we see:```
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```Thanks.

---

### Post by Hogeyfur on 2010-04-10
problem was the i entered the password in lower case when it wanted it in upper case (idiot)

only problem is it seems to run quite slow which is really annoying, were as in my windows partition its pretty fast and I'd rather be using Ubuntu instead of MS W7

---

### Post by 2hot6ft2 on 2010-04-10
> **Hogeyfur said:**
> Security type: WPA2-Personal
Encryption type: TKIP
8 digits in the password
If you want any N band speeds change it to
Security type: WPA2-Personal
Encryption type: AES

AES is more secure than TKIP and will make N band speeds possible.

And there is a guide for that chipset here:
[RALINK RT2870STA and RT3070STA USB WiFi Tutorial]("http://ubuntuforums.org/showthread.php?t=1342593")
You'll also need the 3070sta driver for N band speeds.
I have a Belkin with a Ralink chipset and that how to is how I got it to run right and run fast.

Also I would go with a longer passkey if it were me. No dictionary words and not just letters and numbers. You can go up to 63 characters long if you want some serious security.
Strong Passwords
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

---

