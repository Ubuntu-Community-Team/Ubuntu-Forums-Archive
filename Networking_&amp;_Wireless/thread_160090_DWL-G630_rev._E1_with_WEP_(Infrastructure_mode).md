---
title: "DWL-G630 rev. E1 with WEP (Infrastructure mode)"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by vinfred on 2006-04-14
Hardware: Sony Vaio GR214MP, D-Link DWL-G630 rev. E1
Software: Ubuntu Breezy, RT61 Ralink driver
Use sudo as needed or start with $sudo -s

1/ Install required package as specified in ndiswrapper documentation section 4-1 of
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

2/ install kernel package
I've installed also linux-tree, but I don't know if this is required
(I used synaptics instead of apt-get)

3/ install sysutils package (for dos2unix)

4/ cd to your home directory
$mkdir RT61
$cd ./RT61

5/ download the RT61 driver for linux from
[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

6/ extract the files
$tar -zxvf  RT61_Linux_STA_Drv1.0.3.0.tar.gz

7/ 
$cd ./RT61_Linux_STA_Drv1.0.3.0_200512230/Module

get the readme and follow steps 1 thru 5 included (skip step 3 as it is for Kernel 2.4)
(create the directory /etc/Wireless/RT61STA if needed)

8/ 
$gedit rt61sta.dat

Specify your SSID (SSID=) Your network type (NetworkType=Infra) you channel, Authorization (Authmode=WEPAUTO) your encryption  (EncrypType=WEP) and your WEP key (Key1Str=xxxxxxxxxxxxx)

As I don't understand anything to the other parameters, I didn't change them

10/ 
$fromdos -f  rt61sta.dat

(I had to use the '-f' to get it work)

$cp rt61sta.dat /etc/Wireless/RT61STA/rt61sta.dat

11/ Load the module
$insmod rt61.ko

12/ Activate the network
$ifconfig ra0 up
$dhclient ra0

You should be connected (I hope):p 

Now, tidy up

13/ copy the rt61 module to its target directory
$cp rt61.ko /lib/modules/2.6.10.12-386/drivers/net/wireless

14/ add to /etc.modprobe.d/aliases the following line

alias ra0 rt61

(use $gedit /etc/modprobe.d/aliases)

15/ check if it is working
either
    $rmmod rt61
or
   reboot your system

$depmod -a
$modprobe ra0

To connect to your network use after each  reboot
$ifconfig ra0 up
$dhclient ra0

---------------------------
I hope I've not forgotten one step
BTW, I've seen that there is a new version of the firmware on ralinktech site dated 2006/03/23
It might be worth downloading it !

I'm still looking for a way to get it activated automagically at startup](*,) 
And may-be a way to get it managed by wireless-tools (e.g. to change the key or the SSID):confused: 

Hope this helps
vinfred

---

### Post by vinfred on 2006-04-20
discussion continued on thread [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

Vinfred

---

