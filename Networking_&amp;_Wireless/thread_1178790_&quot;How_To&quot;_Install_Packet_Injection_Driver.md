---
title: "&quot;How To&quot; Install Packet Injection Driver for Linksys WUSB54GC"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by HunterThomson on 2009-06-04
[SIZE="3"][COLOR="Blue"]_"How To" Install the Enhanced rt73 - k2wrlz Driver for Linksys WUSB54GC_[/COLOR][/SIZE]
By, HunterThomson - HowTo's that WORK F\/C|<**!**

[COLOR="Red"][B][U]DO NOT PLUG IN THE LINKSYS WUSB54GC UNTILL I TELL YOU TO !!!
If you alredy did, Unplug it and reboot.[/U][/B][/COLOR]

[COLOR="Blue"][B]OK, I added a the new driver and attached to the thread. But Ubuntu is on Kernel 2.6.28 so you shold still use the rt73-k2wrlz-3.0.2.tar.bz2. HOWEVER, if your installing this in BackTrack4 "PR" then you need to use the new driver 3.0.3.tar.bz2<<< Because BackTrack4 is on Kernel 2.26.29.

If you like you can download at this link below. But, I remeber when I downloaded the driver I attached to this thread that it had even more patches to make it work.. I would suggest using the driver I attached...[/B][/COLOR]
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)

O_k, I know there are like 100 other HowTo's for this and other drivers for this card [COLOR="Red"]but none of them ever worked[/COLOR] for me_. So, I wrote this one and even attached the driver I use. This has worked for me in Ubuntu 7.10 8.04 8.10 9.04 & Archlinux. I love it :) All you do is install it really... Owe, and blacklist some conflicting drivers... Well, and install WICD because NetworkManager will not work with this driver!
Also, pleas don't cut and past this into some blog so you make advertising money off of my work with out even giving me credit.

[SIZE="3"][COLOR="Blue"]This is the Enhanced rt73 driver with Packet Injection & Support for Fragmentation Attack & Sniff WAP HandShake :guitar:[/COLOR][/SIZE]

```
[xxxxx@Linux-Box ~]$ sudo aireplay-ng -9 -i wlan0 rausb0
17:19:09  Trying broadcast probe requests...
17:19:09  Injection is working!
17:19:11  Found 1 AP 

17:19:11  Trying directed probe requests...
17:19:11  00:12:0E:3B:D4:46 - channel: 6 - '06B403335111'
17:19:11  Ping (min/avg/max): 0.278ms/2.147ms/3.884ms Power: -67.30
17:19:11  30/30: 100%


17:19:11  Trying card-to-card injection...
17:19:11  Attack -0:           OK
17:19:12  Attack -1 (open):    OK
17:19:12  Attack -1 (psk):     OK
17:19:12  Attack -2/-3/-4/-6:  OK
17:19:16  Attack -5/-7:        Failed

```

[COLOR="Green"][B]Quote form the website I got the driver form 
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)...[/B][/COLOR]
> RaLink RT73 USB Enhanced Driver
* Support for Fragmentation Attack
* Interface is called rausb0 instead of wlan0 to prevent some tools incorrectly detecting it as wlanng or hostap driver
* Injection speed can be selected with iwconfig <interface> rate command. The default speed yet is 54 MBit. You may want to lower it to 1 MBit before injection with iwconfig rausb0 rate 1M
* NEW: ToDS packets aren't dropped by the driver anymore. WPA handshake captures are finally possible!
IMPORTANT!
Version 3.0.0 is a new fork from the current serialmonkey CVS. It has fixes for 2.6.24 and 2.6.25 and does not need setting a MAC Address before bringing the interface up. This version includes all the enhancement of the 2.0 series of this driver. If you unplug the card while its still in use, it may crash your system. So close all applications accessing it, bring the interface down and then remove the device.
IMPROVEMENT!
There is a tiny extra in the 3.0.0 driver. Maybe you can find it with iwpriv
YOU MAY HAVE WAITED FOR THIS:
Version 3.0.1 has an updated base version from serialmonkey CVS. It is patched with all the features of 3.0.0 and it has been successfully tested with 2.6.26 vanilla kernel.
Version 3.0.2 provides kernel version 2.6.27 compatibility. NOTE: You may also try the mac80211 drivers included in 2.6.27 since these drivers are pretty nice too
Version 3.0.3 provides kernel version 2.6.29 compatibility. It uses default kernel memory allocation for devices' private data area. This may fail on 64bit platforms (according to RaLink). In previous versions the driver allocated its own memory and hacked it into the netdev structure. This hack failed in 2.6.29 and has been removed. However, the new mode works for me quite well. Please report if any problems occur.

_**> First get rid of that NetworkManager and install WICD. All you have to do is install WICD and it will uninstall NetworkManager for you.**_
[COLOR="Green"]Note, if you want to use this wireless card and driver for war-driving you don't need to install WICD. You only need this if you want to use this card as your normal wireless interface.[/COLOR]

[COLOR="Blue"]I just coppied this form the wicd web site so look there if this is broken or out of date.[/COLOR]

_**>In Ubuntu Jaunty all you have to do is**_

```
sudo apt-get install wicd
```

_**> In older vertions of Ubuntu you should folow the instructions on there web page.**_

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)


_**[COLOR="Blue"]>You mite have to add "wicd-client" to gnomes startup applications. here..[/COLOR]**_

```
System/Preferences/Startup Applications 
```

---------------------------------------------------------

[COLOR="Blue"][SIZE="3"]Ok now that WICD is installed and it removed that NetworkManager[/SIZE][/COLOR]


[SIZE="3"][COLOR="Red"]Do NOT connect the wifi card...[/COLOR][/SIZE]

_**>OK, with the WUSB54GC "[COLOR="Red"]Unpluged[/COLOR]" [COLOR="Blue"]Download the driver I have attached to this thread. The rt73.tar.bz2[/COLOR]...**_

_**>Alright, Now Unpack that thing like this if it is in your home folder**_

```
tar xvjf rt73-k2wrlz-3.0.2.tar.bz2
```

_**>Now, move into the directory it created.**_

```
cd rt73*
```

_**>Now, move into the "Modules" directory**_

```
cd Modules
```

_**>Now make and make install**_

```
make && sudo make install
```

_**>Now lets blacklist the drivers that will confict with this hacking driver**_

Just add...

```
#Conflicts with the good rt73 dirver
blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00usb
blacklist rt2x00lib

```

To this file...

```
/etc/modprobe.d/blacklist
```

**_[COLOR="Blue"]>Lets reboot now just to get WICD up and running and stuff...[/COLOR]_**

```
sudo reboot
```

_**[COLOR="Red"]Still with the Linksys WUSB54GC  Unpluged ![/COLOR]**_

_**>Now lets load the driver...**_

```
sudo modprobe rt73
```

**_[COLOR="Blue"]>Ok Now plug in the Linksys WUSB54GC[/COLOR]_**

_**>Now run this command and you should see rausb0 listed**_

```
ifconfig -a
```

----------------------------------------------------------

[SIZE="3"][COLOR="Blue"]Ok, Now just configure WICD to use this card.[/COLOR][/SIZE]

[COLOR="Green"]Note, Only have WICD set to use this wireless card if you want to use it as your wireless interface. If you want to do some war-driving with this card and driver then [COLOR="Red"]DO NOT[/COLOR] have WICD managing this card, instead have it set to your normal wireless interface. Or not... I found it best when cracking WEP to listen with my integrated Intel card and inject with the WUSB54GC. Or you can fire up WiFiZoo and listen with the inegrated Intel card and then be connected to the AP with the WUSB54GC to make use of the cookies and info....Nice having two wifi cards....[/COLOR]

[COLOR="Green"]One of the nice things about WICD is you can set the wireless interface to "blabla" and that way you will not have it trying to put your card into managed mode or bringing it up and down when your trying to get your packet sniffing on.[/COLOR]


_**> You "should" see the WICD icon in your system tray... If you do not you need to add wicd-client to your "startup applications" Or you can just run this command to get it up so you can see that your WUSB54GC is working now.**_

```
wicd-client
```

_**>OK Now that the WICD-client Icon is in your system tray. Click on it to bring up its Wicd Manager window. **_

_**>Then click on "Preferences"**_

_**>Now you see the thing "Wireless Interface"? You need to change that to...**_

```
rausb0
```

**[COLOR="Blue"][SIZE="3"]OK, Now click "OK" and then in the Wicd Manager window click "Refresh"[/SIZE][/COLOR]**

**[COLOR="Blue"]Now you can connect to any wireless network. Even if you don't know the WEP key or WPA-PSK pass-phrase ;). However, the signal bar in WICD will not work but it dose work in conky and iwconfig.[/COLOR]**

---

### Post by Sophism on 2009-09-12
Great post! However I was wondering if these drivers etc work for V3 of this device? I was unlucky enough to get a v3 one and was unable to get the card working by following your instructions.

---

### Post by HunterThomson on 2009-09-15
> **Sophism said:**
> Great post! However I was wondering if these drivers etc work for V3 of this device? I was unlucky enough to get a v3 one and was unable to get the card working by following your instructions.

[http://www.modem-help.co.uk/Linksys/WUSB54GC-v3-Wireless-G-Compact-USB-Adapter.html](http://www.modem-help.co.uk/Linksys/WUSB54GC-v3-Wireless-G-Compact-USB-Adapter.html)

If that link is your device. I was lucky enough to find what chipset it is.

**_Linksys WUSB54GC v3_**

chipset = RT2800U 11bgn

driver = rt2870sta


quote form this link
[http://www.******************/debian-user/345111-linksys-wusb54gcv3.html](http://www.******************/debian-user/345111-linksys-wusb54gcv3.html)
> ...
Install the firmware-ralink package from non-free and the kernel should
pick the right driver automatically.
...

Check out this link with the quote. He was on Debian so that package should be in Ubuntu too. Or it should be called something vary close to it.

Anyway, if that dosn't work. Your looking for instructions to install the driver... rt2870sta

---

### Post by HunterThomson on 2009-09-15
here is that link aging. I hope it works this time....

[http://www.******************/debian-user/345111-linksys-wusb54gcv3.html](http://www.******************/debian-user/345111-linksys-wusb54gcv3.html)

[http://www.******************/debian-user/345111-linksys-wusb54gcv3.html]("http://www.******************/debian-user/345111-linksys-wusb54gcv3.html")

I don't know what is going on??? I'll try to brake it up over two lines and you can cut/past the URL back to gather.

[http://www.******************/](http://www.******************/)
debian-user/345111-linksys-wusb54gcv3.html

Ok three lines......

[http://www.linux-archive](http://www.linux-archive).
org/debian-user/
345111-linksys-wusb54gcv3.html

NICE it worked this time.

---

### Post by SimonTemplarmagician on 2010-03-14
Great tutorial. I've tried to install using it a few times but I'm stomped on what to do after I do next. I attached a screenshot



***Update etc/modprobe.d/ralink alias for wlan*
***Install firmware in  /lib/firmware...
***Check old config...


Thanks alot I'd love to finally get online with this and start learning new things.

---

### Post by HunterThomson on 2010-03-25
> **SimonTemplarmagician said:**
> Great tutorial. I've tried to install using it a few times but I'm stomped on what to do after I do next. I attached a screenshot



***Update etc/modprobe.d/ralink alias for wlan*
***Install firmware in  /lib/firmware...
***Check old config...


Thanks alot I'd love to finally get online with this and start learning new things.

Hum, I just installed it on backtrack4 and followed my guide to the letter. It works fine. Maybe it is getting messed up because your changing the alias for the rt73 card. The reason the creator of this driver is setting the alias to rausb0 is because when it is wlan0 it confuses the kernel into thinking it is a AP driver or something. I don't know if that is true or not but I would just do what I have in this HowTo and nothing ells.

Make sure you are blacklisting all toughs drivers too. You can also use this command to remove the kernel modules. This way you don't have to reboot after you blacklist these... but you still do have to blacklist them.


sudo modprobe -r rt73usb
sudo modprobe -r rt2500
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00usb
sudo modprobe -r rt2x00lib

---

### Post by Makliugas on 2010-04-12
Whats wrong  ? When I'm trying to sudo modprobe rt73 ???
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. 

CAN't FIGURE IT OUT !

---

### Post by HunterThomson on 2010-04-13
It's not a problem. It is still loading the rt73 Kernel module.

[quote=Makliugas]Whats wrong ? When I'm trying to sudo modprobe rt73 ???
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. [/quote]
That is just a deprecation warning.

You just do this...
```
sudo mv /etc/modprobe.d/ralink /etc/modprobe.d/ralink.conf
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by familiozo on 2010-06-10
Thank you work in my tp-link 321g..

---

