---
title: "Ubuntu ! Wireless driver need help"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by sesipdo on 2011-03-03
Atheros AR5007 802.11b/g Adapter
Ubuntu Clean install !  Just reinstalled sence trying other things 

Need help with this ! 
Tried every bodys ideas from other threads and nothing at all ! 

Please help 

I'll supply any information that is needed and I have LAN connection ! 
(:

---

### Post by Koffeehaus on 2011-03-03
[http://ubuntuforums.org/showthread.php?t=1699233](http://ubuntuforums.org/showthread.php?t=1699233)

Try this:

 
sudo apt-get update
sudo apt-get install bcmwl-kernel-source 

Then go to System > Administration > Additional Drivers

Activate the drivers.

Then restart the wireless:

sudo modprobe -r b43 ssb wl
sudo modprobe wl

---

### Post by sesipdo on 2011-03-03
okay it will take me a second to do that ..

and thank you for such a quick reply :)

---

### Post by sesipdo on 2011-03-03
i have done the following 

sudo apt-get update
sudo apt-get install bcmwl-kernel-source 

Then go to System > Administration > Additional Drivers 
the when i went into additional drivers the wifi driver wasn't listed there just my video driver witch i installed when i reinstalled Ubuntu so that is not new .

:(

---

### Post by chili555 on 2011-03-03
> **Koffeehaus said:**
> [http://ubuntuforums.org/showthread.php?t=1699233](http://ubuntuforums.org/showthread.php?t=1699233)

Try this:

 
sudo apt-get update
sudo apt-get install bcmwl-kernel-source 

Then go to System > Administration > Additional Drivers

Activate the drivers.

Then restart the wireless:

sudo modprobe -r b43 ssb wl
sudo modprobe wlI don't believe the Broadcom drivers are going to help his Atheros AR5007 at all.

---

### Post by sesipdo on 2011-03-03
okay...

well i need this to work asap cuz my school server needs some work done on it and i can with out my wifi driver working ....... 


plz help

---

### Post by chili555 on 2011-03-03
Try this:```
sudo modprobe ath5k
```If there is any error or complaint, please post the result. If not and the wireless is still not working, post:```
dmesg | grep -i ath
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by sesipdo on 2011-03-03
when entering the code for  sudo modprobe ath5k i get this as a result 

shawn@shawn-ubuntu:~$ sudo modprobe ath5k

[sudo] password for shawn: 

shawn@shawn-ubuntu:~$ 

.........

should i continue with the next command ?

---

### Post by chili555 on 2011-03-03
> should i continue with the next command ?Yes, please. When you click the Network Manager icon, do you see networks?

---

### Post by sesipdo on 2011-03-03
shawn@shawn-ubuntu:~$ dmesg | grep -i ath
[    0.070593] CPU0: AMD Athlon Dual-Core QL-62 stepping 01
[    0.597795] device-mapper: multipath: version 1.1.1 loaded
[    0.597799] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.599253] powernow-k8: Found 1 AMD Athlon Dual-Core QL-62 (2 cpu cores) (version 2.20.00)
[   12.721439] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   12.721454] ath5k 0000:07:00.0: setting latency timer to 64
[   12.721507] ath5k 0000:07:00.0: registered as 'phy0'
[   13.221000] ath: EEPROM regdomain: 0x64
[   13.221004] ath: EEPROM indicates we should expect a direct regpair map
[   13.221010] ath: Country alpha2 being used: 00
[   13.221012] ath: Regpair used: 0x64
[   13.233028] Registered led device: ath5k-phy0::rx
[   13.233052] Registered led device: ath5k-phy0::tx
[   13.233056] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 1188.419107] ath5k 0000:07:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
shawn@shawn-ubuntu:~$ 

no network as shown in the picture 


that is the next command .. sorry for the wait it was lunch time :P

---

### Post by chili555 on 2011-03-03
That all looks pretty normal! What about:```
iwconfig
sudo iwlist wlan0 scan
rfkill list all
```Thanks.

---

### Post by sesipdo on 2011-03-03
i gave a couple of lines in between each command so that u can c the 3 of them better 




shawn@shawn-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
shawn@shawn-ubuntu:~$ 
shawn@shawn-ubuntu:~$ 
shawn@shawn-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

shawn@shawn-ubuntu:~$ 
shawn@shawn-ubuntu:~$ 
shawn@shawn-ubuntu:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
shawn@shawn-ubuntu:~$ 
shawn@shawn-ubuntu:~$ 
shawn@shawn-ubuntu:~$

---

### Post by chili555 on 2011-03-03
Please try:```
sudo rfkill unblock all
rfkill list all
```Have we gotten rid of soft blocked yes?```
sudo iwlist wlan0 scan
```

---

### Post by sesipdo on 2011-03-03
shawn@shawn-ubuntu:~$ sudo rfkill unblock all

shawn@shawn-ubuntu:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

shawn@shawn-ubuntu:~$ 



do you want me to run the 3rd code ? 
sudo iwlist wlan0 scan

---

### Post by chili555 on 2011-03-03
> do you want me to run the 3rd code ?
sudo iwlist wlan0 scanPlease do so. If you see your network, your wireless is ready to go. We'll have to amend one file to make the unblock permanent.

---

### Post by sesipdo on 2011-03-03
shawn@shawn-ubuntu:~$ sudo iwlist wlan0 scan 
wlan0     Interface doesn't support scanning : Network is down
 

that is what it returns to me when i did the code :P

but if i got to where ur suppose to be able to connect the the networks it says :

wireless networks 
Device not ready

---

### Post by chili555 on 2011-03-03
Is the ethernet cable attached? Please detach it and check again. If it still reports the device is not ready, run and post:```
dmesg | grep -e ath -e wlan
```Thanks.

---

### Post by sesipdo on 2011-03-03
it was yes so i repeated the step above :P

shawn@shawn-ubuntu:~$ sudo iwlist wlan0 scan 
[sudo] password for shawn: 
wlan0     Interface doesn't support scanning : Network is down

shawn@shawn-ubuntu:~$ dmesg | grep -e ath -e wlan
[    0.595481] device-mapper: multipath: version 1.1.1 loaded
[    0.595484] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.411542] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   15.411557] ath5k 0000:07:00.0: setting latency timer to 64
[   15.411612] ath5k 0000:07:00.0: registered as 'phy0'
[   15.910189] ath: EEPROM regdomain: 0x64
[   15.910194] ath: EEPROM indicates we should expect a direct regpair map
[   15.910199] ath: Country alpha2 being used: 00
[   15.910201] ath: Regpair used: 0x64
[   15.921506] Registered led device: ath5k-phy0::rx
[   15.921529] Registered led device: ath5k-phy0::tx
[   15.921533] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
shawn@shawn-ubuntu:~$ 


no problem :)

---

### Post by chili555 on 2011-03-03
I'll have to check in later; dinner date!!

---

### Post by sesipdo on 2011-03-03
do you passably think that you could call me ? i really want this fixed asap :P 


and okay thanks

---

### Post by sesipdo on 2011-03-03
it just started to work !!!!!!!!!!!!!!!!!!!!!!!!!!!!!   (: 

how do we make sure it stays working ??? u said amend some thing??

and then i need your help with something else if you have the time 

TY

---

### Post by chili555 on 2011-03-04
Awesome! We need to get the 'unblock all' to run as the computer is booting. Please do:```
sudo gedit /etc/rc.local
```Add a new line above exit 0```
rfkill unblock all
```Proofread, save and close gedit. You should be all set.

What else can I help you with?

---

### Post by sesipdo on 2011-03-04
im not going to do the next steps for the reason is that i ended up reinstalling the Ubuntu again and i didn't have to do any codes to get it to work !!!!! :PPPPPP 

and yea the other 2 installs never got it to work and that one that we did all the codeing on it made then wirless work as soon as the new format was over !! :P yaya thanks so much 


also i have a USB 300mbps wirless N card that i use and it is a 
Realtek RTL8191s 

and when i plug that thing in it says that it is disconnected  ?? 
):P

---

### Post by chili555 on 2011-03-04
> and when i plug that thing in it says that it is disconnected ?? Are you looking for help getting it going?

---

### Post by sesipdo on 2011-03-04
yea there is no buttons on the device anywhere and the cd says its Linux compat and it still wont work at all and when i had windows 7 on this it worked nice :P 

and i still need my internal card to still work (:

---

### Post by chili555 on 2011-03-04
> and i still need my internal card to still work (: I thought it did.> i ended up reinstalling the Ubuntu again and i didn't have to do any codes to get it to work !!!!!I'm confused.

By the way, why do you need two working wireless cards? Just to torture me??

---

### Post by sesipdo on 2011-03-04
okay .. catch you up lol 



the card in my laptop  does work..
My usb card doesn't  work.. it is an Realtek RTL8191s

---

### Post by chili555 on 2011-03-04
Please post:```
lsusb

```

---

### Post by sesipdo on 2011-03-04
shawn@shawn-pc-pc:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
shawn@shawn-pc-pc:~$ 


:) i think this is what u wanted me to do

---

### Post by chili555 on 2011-03-04
> ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN AdapterThis device works with the module r8192s_usb. There is a firmware bug.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

With an internet connection, remove the device and do:```
sudo mkdir /lib/firmware/RTL8192SU/
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

```Plug the device back in and you should be all set.

Network Manager will have difficulty connecting with two active wireless devices in place.

---

### Post by sesipdo on 2011-03-04
[LIST=1]
[*]shawn@shawn-pc-pc:~$ sudo mkdir /lib/firmware/RTL8192SU/
[sudo] password for shawn: 
shawn@shawn-pc-pc:~$ wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
--2011-03-04 20:49:02--  [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
Resolving launchpadlibrarian.net... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31817 (31K) [application/octet-stream]
Saving to: `rtl8192sfw.bin.gz'

100%[======================================>] 31,817      74.8K/s   in 0.4s    

2011-03-04 20:49:03 (74.8 KB/s) - `rtl8192sfw.bin.gz' saved [31817/31817]

shawn@shawn-pc-pc:~$ gunzip rtl8192sfw.bin.gz
shawn@shawn-pc-pc:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
shawn@shawn-pc-pc:~$
[*]it still says that the device is Disconnected :( as seen in the picture .. and the device flashes once a while
[/LIST]

---

### Post by chili555 on 2011-03-04
I believe it ***is*** connected. Isn't the name of your network TRENDnet652? The button is where you press to disconnect; it's not telling you it's disconnected.

---

### Post by sesipdo on 2011-03-04
not at all lol :P

the other network card is look at the picture close 

there is 
eth0  - Nvidia network controller 10\100\1000
wlan0  - Atheros AR5007 802.11b/g Adapter
wlan1 - Realtek RTL8191s 802.11b/g/n Adapter

---

### Post by sesipdo on 2011-03-04
HUmmmm ....

---

### Post by cve009 on 2011-03-04
I went through a similar exercise a couple of weeks ago.  I found this document helpful:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by sesipdo on 2011-03-05
can you help me narrow the absolute things that i need ..

because i dont want to mess this Ubuntu up i just got it working the way i want it to so yea :) thanks

---

### Post by chili555 on 2011-03-05
Remember I said that Network Manager will have trouble with two working wireless cards? You got it! I still wonder why you want two working wireless cards at one time. Is it for some kind of hacking/cracking exercise?

---

### Post by sesipdo on 2011-03-05
my internal network card is not that good to use in the other part of the house and when i go up the road i cant get my connection with the internal card...

the usb network adapter is what i have to use to make my internet work in the other part of my house and when i go up the road cuz they have no internet

---

### Post by chili555 on 2011-03-05
Let's temporarily stop the internal:```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
iwconfig wlan1
sudo iwlist wlan1 scan
```Now does Network Manager see your network and connect?

---

### Post by sesipdo on 2011-03-05
like im on wireless now with internal card ..

and do u want me to put in my usb one and then do them codes ?

---

### Post by sesipdo on 2011-03-05
well just now when i put it in the card just started to work with no issues ...

---

### Post by chili555 on 2011-03-05
> and do u want me to put in my usb one and then do them codes ?Yes, please.

---

### Post by chili555 on 2011-03-05
> **sesipdo said:**
> well just now when i put it in the card just started to work with no issues ...Awesome! Good job. Now can you mark the thread Solved?

---

### Post by sesipdo on 2011-03-05
thank you much.. and for sticking with me (:!

---

### Post by romanyiv on 2011-03-13
> **chili555 said:**
> Please try:```
sudo rfkill unblock all
rfkill list all
```Have we gotten rid of soft blocked yes?```
sudo iwlist wlan0 scan
```

I have a laptop - Comapq CQ50-210US....for the last few versions of Ubuntu I have wasted hours trying to get my Athero chipset to work - and then with Ubuntu 10.10 it worked!    It's not a laptop I used much and at some point in time it quite working.   The "rfkill unblock all" command fixed it.  I'll have to do some reading on that but my hat's off to chile555 on that one

---

### Post by chili555 on 2011-03-13
You can make it permanent on boot.```
sudo gedit /etc/rc.local
```Add one line above exit 0```
rfkill unblock all
```Proofread, save and close gedit; you should be all set.

---

### Post by conn0r on 2011-03-16
I can't connect to my wireless connection in Ubuntu, it says "Wireless Network Connections Disabled". I can use wireless just fine in Windows Seven which I'm dual booting with Ubuntu using Wubi. I've found that my Acer 5532 has a wireless button next to the power button. This enables wireless and it turns on (lights up orange) automatically while I'm booting up Windows Seven, but I can't even turn it on manually by pressing in Ubuntu it stays off.

[FONT="Arial Black"][COLOR="Red"][SIZE="3"]PLZ REPLY![/SIZE][/COLOR][/FONT]

---

### Post by chili555 on 2011-03-16
@conn0r--

Are you sure you have an Atheros ath5k wireless card? If not, please start a new thread. Send me a private message with the link if I don't catch it right away. Please include in your thread the results of these terminal commands:```
sudo lshw -C network
rfkill list all
```Thanks.

---

