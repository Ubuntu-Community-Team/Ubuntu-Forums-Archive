---
title: "HP Pav tx1000 Wifi not working"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by electronetics on 2009-10-16
First of all I'm still new to Linux. I just have installed Ubuntu on my laptop

HP Pavilion tx1000 (TX1213)
Dual boot with Vista

Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

On my System>Administration>Hardware Drivers shows that "Broadcom STA wireless driver" is enabled. But it is not working so I'm currently connecting using a wired network.


```
lspci -vnn | grep 14e4

03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```


What is the easieast and safest way to get my wifi working?

---

### Post by Ayuthia on 2009-10-16
You can try the following from the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If that works, you can make it permanent:
```
echo blacklist b43 | sudo tee -a /etc/modules/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modules/blacklist.conf
echo wl | sudo tee -a /etc/modules
```
The first set of commands will remove the current wireless module installed, install the Broadcom STA version, then scan for wireless sites.  The second set of commands will then blacklist the non-working modules (b43 and ssb) and then load the Broadcom STA version (wl) when the system boots up.

Hope that helps.  It is some kind of bug with the 4328 card where the system keeps loading the b43 module.

---

### Post by electronetics on 2009-10-17
I have done the first part and here is the result
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:C6:0E:D2:F5
                    ESSID:"LeeWiFi"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-27 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1E:2A:DE:3F:3C
                    ESSID:"steve"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-85 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


```
Then it asked for the keyring password, after I have typed in the password it automatically connect to my wifi.

Bottom line it worked. Thanks!!!
I need to do now is the second part to make it permanent.

---

### Post by electronetics on 2009-10-17
I have tried the second part but I have no success.

This is what I get upon trying
```
$ echo blacklist b43 | sudo tee -a /etc/modules/blacklist.conf 
tee: /etc/modules/blacklist.conf: Not a directory
blacklist b43
$ echo blacklist ssb | sudo tee -a /etc/modules/blacklist.conf
tee: /etc/modules/blacklist.conf: Not a directory
blackelist ssb
$ echo wl | sudo tee -a /etc/modules
wl

```
So since the response is: Not a directory, I have tried to look for the blacklist.conf file manually by:
```
find / -name blacklist.conf
/etc/modprobe.d/blacklist.conf
```

After I have found it I just modify the path to the commands and here are the result:
```
$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist b43
$ echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist ssb
$ echo wl | sudo tee -a /etc/modules
wl

```

So I rebooted the computer but still I have no luck, the wifi did not automatically start. So for the mean time I'll be using this to connect my my wifi
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```

Well at lease I'm not bounded by the LAN cable anymore.

Now I'm just thinking if I can just make  a script that I could click to execute or include in the start up so I could connect in my wifi automatically. But if modifying the blacklist.conf is better I'll still go with it.

For now I'll just wait for an advice. Thanks!!!

---

### Post by Ayuthia on 2009-10-17
If that is the case, you can try the following after you have it connected:
```
sudo update-initramfs -u
```
That will hopefully remove the b43 from loading up when the system starts up.  If this does not work, you can add the commands without the sudo into /etc/rc.local:
```
gksu gedit /etc/rc.local
```and add:
```
modprobe -r b43 ssb wl
modprobe wl
```before the exit 0 line.

---

### Post by electronetics on 2009-10-19
My wifi is now automatically connecting but this did not work
```
sudo update-initramfs -u
```

So by editing my  /etc/rc.local and adding 
```
modprobe -r b43 ssb wl
modprobe wl
```

is the solution.

Many Thanks

---

### Post by DigitalWolf333 on 2010-01-03
i had the same problem a while ago, and still do. but instead my wifi comes on once every month or two(seriously), and when it does work it work for a few days or less then dies again, the same applies to windows 7 (i have dual boot).

now it stopped working around he time i first installed ubuntu then windows 7(RC) later, so i thought it was software related, but deeper reaserch (in the weeks after it first went out) says its hardware related...

i find this 5 months later tried it and it doesn't work :(

---

### Post by Alejandro Nova on 2010-01-04
This is legendary.

**Never buy HP again**. Simple as that.

In the meantime, look for a capable technician able to resolder your broken NVIDIA 6150 southbridge (this is definitely a hardware issue)

BTW, if it's software, Ubuntu can work with the STA driver and with the b43 one. I recommend the b43 one.

---

