---
title: "DWA 140 restricetd to 54mbps"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by foxem2001 on 2011-02-21
Hi i am new to all this,

i have and issue my wireless card a usb DWA-140 B1 will not operate above 54mbps to start with it was not working all the time would drop out bu i solved that by black listing rt2800usb from loading and that stopped the frequent drop outs,

i have used iwlist and iwconfig in SUDO mode with no affect and my device in wireless manager states i am using a driver:USB,

Now normally the speed would not matter but i have a 50Mbit Internet connection soon to go up-to a 100Mbit connection, 

any help would be much apprciated.

david@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux


david@ubuntu:~$ sudo iwlist wlan0 rate
wlan0     unknown bit-rate information.
          Current Bit Rate:54 Mb/s

david@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     Ralink STA  ESSID:"50mbps"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:26:5A:21:81:04   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:320C-E2BC-3E78-B70A-2669-849E-E6D8-A9AB
          Link Quality=100/100  Signal level:-53 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by add1kt on 2011-12-26
I am not sure if you have tried using the ralink rt3070sta driver yet.  But it might be worth a try.  I had the same issue with the rt2870sta driver, It won't connect at 802.11n speeds, 802.11g only (54 Mb/s). Be advised this is a little hackish :-)

try in this order:

(requires sudo) add the following to /etc/modprobe.d/blacklist.conf 

> blacklist rt2870sta
blacklist rt2800usb

reboot (if it doesn't help continue)



This is an asus driver but may work as they are similar chipsets
[http://www.asus.com/Networks/Wireless_Adapters/USBN13/#download](http://www.asus.com/Networks/Wireless_Adapters/USBN13/#download)

1. extract the file anywhere in your home directory (or wherever you want)

2. cd into the new directory and copy a missing file
cp RT2870STA.dat RT3070STA.dat

3. lsusb to check your id, add the ids into file common/rtusb_dev_id.c
-the syntax in the file will be a bit different than the one from lsusb here is mine: 0b05:1784  you will make it look like this 0xB05,0x1784.  Follow the syntax from the other entries.

4. Compile and install the driver.
make (you&#8217;ll see one error that related &#8220;tftpboot&#8221;, ignore it.)
sudo make install

5. Add a missing symlink.
sudo mkdir /etc/Wireless/RT2870STA; sudo ln -s /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

6. Load the driver, if failed rmmod rt2800usb related kernel modules.
sudo modprobe rt3070sta

reboot



what package installs rt2870?  firmware-ralink
(if you screw something up just re-install this package)

Now if this all fails or something goes wrong in between, and you at least want your slower "g" speeds, work in reverse to restore all previous modules and configs.

1. cd in the directory you created when you extracted the driver source code.

2. sudo make clean
sudo make uninstall

3. use synaptic to re-install firmware-ralink pakage

4. comment out the /etc/modprobe.d/blacklist.conf entries by adding a # in front of the entries you don't want. (requires sudo)

> #blacklist rt2800usb
#blacklist rt2870sta


5. reboot or 
 -sudo ifconfig wlan0 down
 -sudo rmmod rt3070sta
 -sudo modprobe rt2870sta
 -sudo ifconfig wlan0 up

***your wifi device may be named something else....with the new ralink driver the device name is ra0***
you should at least have the internet at this point.

---

### Post by add1kt on 2011-12-26
here is living proof n speeds are capable!

---

