---
title: "HowTo Sitecom USB WL012 (Prism2 WLAN device)"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by windorah on 2006-01-25
Just installed my Sitecom card and though it might be of interest for all using usb prism2.x cards. 

**Sitecom WL-012 with Prism2.x under Kubuntu 5.10**

In the following I describe my installation of the Sitecom WL-012 (USB-Wlan device with prism2.x) under Kubuntu 5.10 with 2.6.12 kernel. You need to be root to do this, of course.

(1) Install the linux-wlan-ng package included in the repositories.

(2) The prism drivers are already included in the 2.6.12 kernel and you won't have to build a new kernel. Check with lsmod and you should see the prism2_usb module (The card must be plugged in). 

(3) After installing the linux-wlan-ng package you find /etc/modutils/linux-wlan-ng which defines the aliases that identify the wlan0 interface with the prism driver. For the Sitecom WL-012, uncomment 

alias wlan0 prism2_usb

The device needs to be reset when the driver is loaded. Enter a line 

options prism2_usb prism2_doreset=1

before the alias command above. The linux-wlan-ng package is not yet fully adapted to the 2.6 kernel, but to the 2.4 kernel. The 2.4 kernel uses /etc/modutils, while the 2.6 kernel wants the /etc/modprobe.d directory. To make Ubuntu find the alias, do

cp /etc/modutils/linux-wlan-ng /etc/modprobe.d/linux-wlan-ng.modprobe

(4) The linux-wlan-ng package does not support configuring the device with iwconfig, so don't waste your time trying it out.

(5) Now go to /etc/network/interface and configure the wlan0 interface. Enter

auto wlan0
iface wlan0 inet dhcp
        pre-up /etc/init.d/wlan start
        post-down /etc/init.d/wlan stop

(6) Go to /etc/wlan. The /etc/init.d/wlan script calls /etc/wlan/shared. The latter tries to source all files /etc/wlan/shared.* This will fail if there is no such file... Furthermore, the non-existent /etc/wlan/shared.* are supposed to provide functions prism2_fwload() and prism2_mibset() which are called by /etc/wlan/shared and not checked for existence prior to calling. All of these issues are cured by creating a file /etc/wlan/shared.prism2 with the following contents:

#!/bin/bash
prism2_fwload ()
{
        /bin/true
}

prism2_mibset ()
{
        /bin/true
}

This is enough to satisfy /etc/wlan/shared. 

(10) The remaining work is well documentated in the internet so I post my configuration uncommented:

/etc/network/wlan.conf

WLAN_DEVICES="wlan0"
ChannelList="01:02:03:04:05:06:07:08:09:0a:0b:13:00:00"
ChannelMinTime=200
ChannelMaxTime=250
WLAN_SCAN=n
SSID_wlan0="your ssid"
ENABLE_wlan0=y

do 
cp wlancfg-DEFAULT wlancfg-your ssid
and for a Wlan with a 128bit WEP key 
/etc/network/wlancfg-your ssid

lnxreq_hostWEPEncrypt=false     
lnxreq_hostWEPDecrypt=false     
dot11PrivacyInvoked=true        
dot11WEPDefaultKeyID=0          
dot11ExcludeUnencrypted=false   

PRIV_GENERATOR=/sbin/nwepgen    
PRIV_KEY128=false               
PRIV_GENSTR=""

dot11WEPDefaultKey0=            put your wep here
dot11WEPDefaultKey1=
dot11WEPDefaultKey2=            
dot11WEPDefaultKey3=            
#=======SELECT STATION MODE===================
IS_ADHOC=n                      

AuthType="opensystem"           

BCNINT=100                      
CHANNEL=6                       
                                
BASICRATES="2 4"                
OPRATES="2 4 11 22"             

With this configuration, the Sitecom WL-012 is started automaticly when switching on the computer. When the card is plugged in while Kubuntu is running it can be activated by

ifup wlan0

Accordingly type

ifdown wlan0

for switching of.

---

### Post by scottt106 on 2006-05-20
Thanks for the little tutorial.  This configuration worked for me using a Microsoft MN-510, with one exception.  Each time I restart the computer, I lose my network connection.  However, running
```
sudo ifup wlan0
```
seems to fix it.  Is there any way to fix it automatically?  I am configuring it on a fresh install of ubuntu 5.10.  The only other alterations I have made to the syster were in following another tutorial, at:

[http://doc.gwos.org/index.php/DWL122Prism](http://doc.gwos.org/index.php/DWL122Prism)

---

### Post by tormod on 2006-06-17
I have put together some up-to-date information about the prism2_usb drivers on [https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb](https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb)

The support has become better in Ubuntu 6.06, almost out-of-the-box...

---

### Post by Peturrr on 2006-11-08
I struggled a whole day with the wl-012 using edgy. I could get connected but it disconnected after a little traffic. I found out that it is very important to update the firmware of the wl-012. It now works extremely well!
Instructions from : [http://ta.twi.tudelft.nl/DV/Staff/Lemmens/Wireless/wireless-linux.html](http://ta.twi.tudelft.nl/DV/Staff/Lemmens/Wireless/wireless-linux.html) (adapted to ubuntu)
> 
 Note that many standard Sitecom WL012 adapters only work with 2.4 kernels because of a flaw in the firmware : if you need to run it on 2.6 kernels *(ubuntu)* you need to apply a firmware patch from Sitecom !!  
 This could be done as follows :[LIST]
[*] Fetch firmware updates   po010102.hex and su010506.hex   They can be found on [http://linux.junsun.net/intersil-prism/firmware/1.5.6/](http://linux.junsun.net/intersil-prism/firmware/1.5.6/)
[*]install the latest wlan-ng driver
[*] Load the driver (prism2_usb ) and check the firmware numbers using **dmesg**.  ```
sudo modprobe prism2_usb
``````
dmesg | grep ident
```Mine were
 ident: nic h/w: id=0x8010 1.0.0
ident: pri f/w: id=0x15 1.0.8    (primary firmware release)
ident: sta f/w: id=0x1f 1.3.5    (secondary firmware release)
[*] Turn the USB adapter off and then put it in firmware upgrade state :    
```
wlanctl-ng wlan0 lnxreq_ifstate ifstate=disable
``` ```
wlanctl-ng wlan0 lnxreq_ifstate ifstate=fwload
```
[*] Check if you can read the PDA using **prism2dl** :    
```
prism2dl -s wlan0
```  This should give you just a lot of numbers.
[*] Now comes the real thing : double check if you really have downloaded the right  firmware, cross your fingers (!!) and send it to the USB adapter !!!!!!    
```
prism2dl -f /tmp/po010102.hex -f /tmp/su010506.hex wlan0
```
[*] Unload the drivers and reload them again (prism2_usb) and check the new firmware numbers using **dmesg**. 
```
sudo rmmod prism2_usb
``````
sudo modprobe prism2_usb
``````
dmesg | grep ident
```Mine are now :    
ident: nic h/w: id=0x8010 1.0.0
ident: pri f/w: id=0x15 1.1.2
ident: sta f/w: id=0x1f 1.5.6
[*] After this procedure the USB adapter is working just fine, both under 2.4.x and   2.6.x !! Many thanks to Prism2/Intersil, Sitecom and of course the   linux-wlan developers for their fix ![/LIST]

---

### Post by tormod on 2006-11-08
Automatic firmware loading works fine for me in edgy. Did you try to install the firmware packages as explained on the wiki page?

Edit: Sorry I forgot, it doesn't work out-of-the-box, you'll still need the updated udev rules and wlan-udev.sh from [https://launchpad.net/bugs/29706](https://launchpad.net/bugs/29706)
Edit2: That bug is not confirmed by the way. It would help if someone could confirm to the developers that automatic firmware loading is broken in edgy.

---

