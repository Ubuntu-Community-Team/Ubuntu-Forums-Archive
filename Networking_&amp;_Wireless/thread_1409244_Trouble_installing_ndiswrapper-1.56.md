---
title: "Trouble installing ndiswrapper-1.56"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by egims on 2010-02-17
I have been trying to install ndiswrapper-1.56. I am using ubuntu 9.10
 
I have been following the installation instructions to a tee, but each time I run:
 
make install
 
...in order to install ndiswrapper-1.56 it goes through most of the process and then gives two errors that I can not figure out how to correct. They are:
 
install: cannot create regular file '/lib/modules/2.6.31-14-generic/misc/dniswrapper.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/desktop/Downloads/ndiswrapper-1.56/driver'
make: *** [install] Error 2
desktop@Desktop-home:~/Downloads/ndiswrapper-1.56$ make uninstall
 
I am a quick study, but new to ubuntu linux. I would really appreciate any help in getting this installed without errors. Thanks

---

### Post by chili555 on 2010-02-17
The super-user, or root, has permission to write to system files; the ordinary user does not. Simply precede your commands with sudo:```
[COLOR="Red"]sudo [/COLOR]make install
```

---

### Post by egims on 2010-02-17
Hello, and thank you.

Well, here is what happened...

After the command:

sudo make install

...ndiswraper-1.56 seemed to install without a flaw. HOWEVER after checking to see if the install was successful:

ndiswrapper -l

...the result said that ndiswrapper could not be found. I then went ahead anyway and installed the wireless driver, which also seemed to install. By that I mean that the command executed without an error message. However, upon reboot I still have no wireless internet, nor can the computer even see the router.

I did check and my Belkin USB wireless adapter is quite workable with ndiswrapper, so I guess something is still not right.

Again, any help is appreciated.

---

### Post by chili555 on 2010-02-17
Please do:```
ndiswrapper -l
```Be sure the driver and hardware show as present. Next:```
sudo modprobe ndiswrapper
iwconfig
```Is a wireless interface there, wlan0, perhaps? Now can you click the Network Manager icon and connect?

---

### Post by egims on 2010-02-17
Thank you again for your continued help...I appreciate it.

ndiswrapper -l

rt73 : driver installed
device (050D:705A) present (alternate driver: rt2500usb)

Following After:

sudo modprobe ndiswrapper
iwconfig

lo   no wireless extensions
eth0   no wireless extensions
wmaster0   no wireless extensions

wlan0  IEEE 802.11bg Mode: Managed  Frequency:2.462 GHz
Access Point: Not-Associated   Tx- Power=20 dBm
Retry   long limit: 7   RTS thr:off   Fragment thr:off
Power Management: on
Link Quality:0  Signal lever: 0  Noise level: 0
Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0   Missed beacon: 0

Yes, a wireless interface is present:
Auto eth0   Last Used: Never

But no, I can't connect.

---

### Post by chili555 on 2010-02-17
> (alternate driver: rt2500usb)This suggests that rt2500usb needs to be blacklisted. 

wlan0 is your wireless interface. When you click the icon, don't you see something like the attached? Do you see wireless networks?

---

### Post by egims on 2010-02-17
Per the image you provided: It does indicate a belkin network:

Wired Network
  disconnected
Wireless Network
  disconnected

-------Available--------
belkin54g  (with good signal)
-------------------------
and so on below.

"This suggests that rt2500usb needs to be blacklisted. "

How is that done?

Thanks.

---

### Post by egims on 2010-02-17
rt73 : driver installed
device (050D:705A) present (alternate driver: rt2500usb)

It was suggested to me that I still don't have any wireless because the alternate driver needs to be blacklisted.

I tried adding both "rt2500usb" and "050D:705A" to the blacklist at separate times, but each time after running:

ndiswrapper -l

...it still said: 

rt73 : driver installed
 device (050D:705A) present (alternate driver: rt2500usb)

I guess meaning the blacklist was not successful. If anyone can tell me how to do this I would really appreciate the help.

---

### Post by chili555 on 2010-02-17
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or vim or any text editor if you don't have gedit. Add a single line:```
blacklist rt2500usb
```Proofread, save and close gedit. Next do:```
sudo rmmod -f rt2500usb
```>  	
Wired Network
disconnected
Wireless Network
disconnected

-------Available--------
belkin54g (with good signal)
-------------------------Is 'belkin54g' your network? Can you click on it and connect?

---

### Post by egims on 2010-02-17
Hi Chilli,

REALLY appreciate your help.

Ok, here is the kicker....

After adding rt2500usb to the blacklist and then running:

sudo rmmod -f rt2500usb
I get the reply:

ERROR: Removing 'rt2500usb': No such file or directory!!!!

Yet, if I again run:

ndiswrapper -l

I get the same message:

rt73 : driver installed
 device (050D:705A) present (alternate driver: rt2500usb)

If I attempt to connect to the network by clicking on the connection it simply tries and fails every time.

I saw another post about searching for aliases. I searched to see if rt2500usb may be an alias of something else, and it draws nothing. Pulling my hair out at this point.

---

### Post by egims on 2010-02-17
SUCCESS!!!!!!!!!

The final glitch was a router issue.

Thank you for ALL your help.

---

### Post by 2blade30 on 2010-11-06
hi all, i got the same problem while im instaling ndiswrapper 1.56 on ubuntu remix(for netbook) 10.10 on my lap top and i tried the sudo make install and i still get the [all] Error 2,
 anyone could help me, i dont know what to do and im new on linux
thanks for fast reply

---

