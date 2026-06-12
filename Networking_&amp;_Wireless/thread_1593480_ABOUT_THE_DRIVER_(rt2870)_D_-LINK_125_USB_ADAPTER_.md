---
title: "*ABOUT THE DRIVER (rt2870) D -LINK 125 USB ADAPTER CHANGED TO RAWLINK RT3070 DRIVER"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by johnsuffer on 2010-10-11
**MANY TKS TO *PYTHEAS22* HELPING ME NOT GETTING ME the newbe too  DISCOURAGED****

Here comes my problems  

step 1/ When i downloaded the new Ubuntu 10.04 lucid release  end of sept 2010 I installed duel on a pentium 133 with 512 mg ram machine choosing either XP family or Ubuntu platform at start. So far so good ! BUT WHEN WAS THE TIME TO CONNECT MY USB ADAPTER D-LINK  DWA 125 N ( id 07D1 :3C0D ) DRIVER DTR 2870. CONNECTION WENT ON RIGHT AWAY ??? BUT  WAS UNABLE TO CONNECT PROPPERLY ON INTERNET ??
tHE NETWORK MANAGER SHOWED ME A SOME TYPE OF LOOPBACK WITH A DEFAULT DRIVER(RT2800USB) Already installed as *Default* ??

step2/ Following instructions from the Ubuntu forum after lots of searching i found finally [B][U][I]some commands that make senses.
[/I][/U][/B]
step3/ **Doing this command to _put away the rt2800usb driver_ **(the default one installed in the ubuntu 10.04 lucid release)  [B]_So even though_ I performed the ndiswrapper installed and the ndisgtk software performing all steps at start to installed with windows drivers in *system admistration* the windows drivers screen helped me to install the drt2870.inf file With confirmation  of *DRT2870* INSTALLED AND PRESENT* Anyway i was still getting a message from the network manager*Connection information* with a live connection 
That i was using rt2800usb with wrong IP adddreses  etc  etc
SO i had to eliminate rt2800usb by doing this :
[/B]
**STEP 4/** **COMMANDS IN TERMINAL **


 **[COLOR=black]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]**
  




**adding thoses  lines**

 [COLOR=black]blacklist rt2800usb[/COLOR][COLOR=black]blacklist rt2x00usb
blacklist rt2x00lib


[/COLOR]
  
**STEP 5/**[B]
SO I DECIDED TO PURGE NDISWRAPPER AND NDISGTK ALSO MY DTR 2870 DRIVER !! and try to install a new *Replacement my adapter usb driver*     dtr2870 which was not *compatible* with the ubuntu 10.04 lucid platform
So by putting on google my usb id dwa125 usb adapter(* id 07D1 :3C0D*[/B] )[B]  i got a site to go at *rawlink*  they build the *chipset* for d-link so they gave me a download site to download the replacement driver for my rt2870 it was a TAR.bz2 file *DPO_RT3070_STA_V2....FILE. i EXTRACTED INTO MY * DOWNLOAD LINUX PLATFORM FILE* ALSO A COPY ON MY LINUX PLATFORM 

Than i did these command to purge my ndiswrapper and ndisgtk (before i removed my drt2870 with the windowsdriver help screen)

BY DOING THIS[/B] **: command**

[COLOR=black][FONT=&quot]sudo apt-get remove --purge ndiswrapper*[/FONT][/COLOR]


**STEP 5/**   I reboot  , my rt2870 is gone, the stupid default rt2800usb is gone ok

I[B] M REALLY *STUCK* NO INTERNET AT ALL AND *NO WAYS* TO INSTALL THE NEW DRIVER  *DPO_RT3070_STA_V2...  * FILE THAT I HAVE ON MY UBUNTU PLATFORM MACHINE  IN  DOWNLOADS FILES ALSO A COPY ON MY DESKTOP 
[/B] 
[B]*HOW CAN I INSTALL THIS NEW DRIVER NOW  **STEP BY STEP** PLEASE HELP ME?

THANK U ALL  FOR YOUR HELP AND SPECIALY TO *PHYTHEAS22* the linux *Gouru*[/B]  
Kindly yours

John the Newbe  :-)

No problem for emails

at Johnc_del AT hotmail.com







   
[COLOR=black][FONT=&quot]
[/FONT][/COLOR]

---

### Post by flash63 on 2010-10-11
Hi,
i think you can use the rt2870sta module. Test it.

Add the ID (command in one line):
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
Load the Module
```
sudo modprobe rt2870sta
iwconfig
```
Interface available? Try to connect!

The solution works? Ok, automatic driver load if the stick was plugged in:
```
sudo gedit /etc/udev/rules.d/10-d_link.rules
```
contents:
```
# UDEV-Rule for D-LINK DWA-125N ID 07D1 :3C0D
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c0d", RUN+="/sbin/modprobe rt2870sta"
```
make it ready to work
```
sudo service udev reload
```
.. or restart

---

### Post by pytheas22 on 2010-10-11
Please try flash63's suggestion above.  If that doesn't work, I can write out instructions for downloading, compiling and installing the RT3070 driver from Ralink's website.

---

### Post by johnsuffer on 2010-10-11
> **flash63 said:**
> Hi,
i think you can use the rt2870sta module. Test it.

Add the ID (command in one line):
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```Load the Module
```
sudo modprobe rt2870sta
iwconfig
```Interface available? Try to connect!

The solution works? Ok, automatic driver load if the stick was plugged in:
```
sudo gedit /etc/udev/rules.d/10-d_link.rules
```contents:
```
# UDEV-Rule for D-LINK DWA-125N ID 07D1 :3C0D
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c0d", RUN+="/sbin/modprobe rt2870sta"
```make it ready to work
```
sudo service udev reload
```.. or restart

------------------------------------------------------------------------------------------------------
 [SIZE=3]**HI  FLASH 63 TKS FOR YOUR HELP ** !  * HERE  WHAT HAPPEN AFTER  I DID YOUR COMMANDS*[/SIZE]
 [SIZE=3]YOUR 1ST COMMAND[/SIZE]
 

 [SIZE=3]echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf[/SIZE] 

 

 [SIZE=3]Load the Module[/SIZE]
  [SIZE=3]Code:[/SIZE]
 [SIZE=3]sudo modprobe rt2870sta  [/SIZE] [SIZE=3]iwconfig[/SIZE] 

 

  [SIZE=3][SIZE=4]**STEP 1  -Flash 63 !!here what i get  after doing the echo command* line above and loading the module after iwconfig  !!**[/SIZE][/SIZE]
 [SIZE=3]--------------------------------------------------------------------------------------------------------------------------------------------[/SIZE]
 

 [SIZE=3][sudo] password for john: [/SIZE] 
 [SIZE=3]install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id [/SIZE] 
 [SIZE=3]john@john:~$ sudo modprobe rt2870sta [/SIZE] 
 [SIZE=3]john@john:~$ iwconfig [/SIZE] 
 [SIZE=3]lo        no wireless extensions. [/SIZE] 
 

 [SIZE=3]wlan0     IEEE 802.11bgn  ESSID:"Belkin_N_Wireless_49F167"  [/SIZE] 
           [SIZE=3]Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: D6:16:4F:BE:FF:3E   [/SIZE] 
           [SIZE=3]Tx-Power=14 dBm   [/SIZE] 
           [SIZE=3]Retry  long limit:7   RTS thrff   Fragment thrff [/SIZE] 
           [SIZE=3]Power Managementn[/SIZE]
 

 [SIZE=3]------------------------------------------------------------------------------------------------------------------------------------------------[/SIZE]
 
 
 **[SIZE=3]STEP 2/[/SIZE]**
 

 

 [SIZE=3]Interface available? Try to connect!

The solution works? Ok, automatic driver load if the stick was plugged in:[/SIZE]
  [SIZE=3]Code:[/SIZE]
  

 

 [SIZE=3]sudo gedit /etc/udev/rules.d/10-d_link.rules[/SIZE] 

 [SIZE=3]Rule for D-LINK DWA-125N ID 07D1 :3C0D[/SIZE] [SIZE=3]SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c0d", RUN+="/sbin/modprobe rt2870sta"[/SIZE] 
-------------------------------------------------------


 [SIZE=3]john@john:~$ sudo gedit /etc/udev/rules.d/10-d_link.rules [/SIZE] 
 [SIZE=3]john@john:~$     **  RULES WERE SAVE   TWICE IN  **RULES FOLDER .D**[/SIZE]
 

 

 ---------------------------------------------------------------------------------------------------- 
 **[SIZE=3]STEP 3/[/SIZE]**
 

 **[SIZE=3]sudo service udev reload[/SIZE]**    
 [SIZE=3]**i did this an reboot   ?   *_nothing happen_***  ?   [/SIZE]

[SIZE=3]**Why do you suggest replacing drt2870 d-link driver by rt2870sta  ?  EXPLAIN ?**[/SIZE]
 

 

 
 [SIZE=3]-----------------------------------------------------------------------------------------------[/SIZE]
  

 

 [SIZE=3]**step 4/**
[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]
[/SIZE][B]
[SIZE=3]ANOTHER  COMMAND AGAIN [/SIZE][/B] **(AFTER I REBOOT)  **
 

 [SIZE=3]iwconfig  

**ANSWERS*[/SIZE]
 

 

 **[SIZE=3]john@john:~$ iwconfig [/SIZE]** 
 [SIZE=3]**lo        no wireless extensions**. [/SIZE] 
 [SIZE=3]wlan0     IEEE 802.11bgn  ESSID:"Belkin_N_Wireless_49F167"  [/SIZE] 
           [SIZE=3]Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: D6:16:4F:BE:FF:3E   [/SIZE] 
           [SIZE=3]Tx-Power=14 dBm   [/SIZE] 
           [SIZE=3]Retry  long limit:7   RTS thrff   Fragment thrff [/SIZE] 
           [SIZE=3]Power Managementn [/SIZE] 
            
 
[SIZE=4][B]tks for your help !  anymore suggestions !!

Regards  

John [/B][/SIZE]

---

### Post by johnsuffer on 2010-10-11
> **pytheas22 said:**
> Please try flash63's suggestion above.  If that doesn't work, I can write out instructions for downloading, compiling and installing the RT3070 driver from Ralink's website.
------------------------------------------------------------------------------------------------------
Hi Pitheas22 Has you can see (Below) i dis try every step of FLASH63 Look of what happen on step1/2/3/4  ???

So id love having Your INSTRUCTIONS Now !  I have already the full DPO_rt3070sta bz2 file  download from The rawlink site Its in my linux machine on my desktop But I cannot install it I tried everything The linux  (Archive installer) doesnt recongnize this type of file maybe
Tks for your help anyway 
John
Merci encore une fois :-)

---

### Post by flash63 on 2010-10-12
Hi,
the device was switched to Ad-Hoc Mode. That's wrong.
```
wlan0 IEEE 802.11bgn ESSID:"Belkin_N_Wireless_49F167"
[COLOR="DarkOrange"]Mode:Ad-Hoc[/COLOR] Frequency:2.412 GHz Cell: D6:16:4F:BE:FF:3E 
...
```
You probably build a "New Network" with the Network-Manager or there exist a manual configuration, but that's improbably. Delete this configuration. I think ist under System > Configuration > Network Configuration > Register WiFi or Wireless (I'm sorry, but i use a german localised Desktop). 

For a trouble free and save connection with the Network-Manager You previously switch your Router security configuration to pure WPA2-AES (CCMP) Encryption. 

Try to connect again now. Klick left on the NM Icon in the upper panel and then onto your desired network name. Enter the password (PSK - Pre-Shared-Key). The connection should be established automatically.

> Why do you suggest replacing drt2870 d-link driver by rt2870sta ? EXPLAIN ?
The rt2870sta supports both Chipset-Variants (rt3070 works only with 2,4GHz not 5Ghz and reduced bandwith).

---

### Post by pytheas22 on 2010-10-12
> So id love having Your INSTRUCTIONS Now ! I have already the full DPO_rt3070sta bz2 file download from The rawlink site Its in my linux machine on my desktop But I cannot install it I tried everything The linux (Archive installer) doesnt recongnize this type of file maybe
Tks for your help anyway
John

It looks like flash63's instructions worked for you, since when you type "iwconfig" you now see a wireless interface.  So I don't think it should be necessary to compile the driver from source.

As an explanation of what flash63's directions did, they told your computer that the rt2870sta module should be used to drive your wireless card.  Previously your computer would not have done this because it would have looked at the IDs of the devices that the rt2870sta driver says it should support, which did not include your particular wireless card.  However, it seems (and I've read this recently on another website) that the rt2870sta is actually capable of driving your device.  This is therefore an alternative solution to compiling the rt3070 module yourself.  It's preferable to avoid compiling that module manually, because it can cause frustrations whenever you upgrade your kernel.

As flash63 points out, your interface is shown in ad-hoc mode now, probably because you tried to create a network rather than joining one.  Unless you have non-traditional settings on your wireless network, you won't be able to connect to your wireless router in ad-hoc mode.

Are you able to connect to your network by left-clicking on the NetworkManager icon in the top-right corner of your screen and then clicking on the name of your network?  This should work.  If it doesn't, please post the output of:
```

dmesg | grep -e wlan -e rt2 -e rt3
sudo iwlist scan
iwconfig
lshw -C Network
```

---

### Post by johnsuffer on 2010-10-13
> **pytheas22 said:**
> It looks like flash63's instructions worked for you, since when you type "iwconfig" you now see a wireless interface. So I don't think it should be necessary to compile the driver from source.
 
As an explanation of what flash63's directions did, they told your computer that the rt2870sta module should be used to drive your wireless card. Previously your computer would not have done this because it would have looked at the IDs of the devices that the rt2870sta driver says it should support, which did not include your particular wireless card. However, it seems (and I've read this recently on another website) that the rt2870sta is actually capable of driving your device. This is therefore an alternative solution to compiling the rt3070 module yourself. It's preferable to avoid compiling that module manually, because it can cause frustrations whenever you upgrade your kernel.
 
As flash63 points out, your interface is shown in ad-hoc mode now, probably because you tried to create a network rather than joining one. Unless you have non-traditional settings on your wireless network, you won't be able to connect to your wireless router in ad-hoc mode.
 
Are you able to connect to your network by left-clicking on the NetworkManager icon in the top-right corner of your screen and then clicking on the name of your network? This should work. If it doesn't, please post the output of:
```

dmesg | grep -e wlan -e rt2 -e rt3
sudo iwlist scan
iwconfig
lshw -C Network
```
----------------------------------------------------
Tks i will try those commands !  But good news I AM CONNECTED NOW 
yes i am CONNECTED  no problems there ! But i had to disabled the *Security* wpa/WPA2  * in my router (Otherwise I cannot connect) so i have to find ways to get around this ?  I really cannot go online on an unsecured Router ?? Bcz We have 6 differents computers In my *Condo* Building using this network and now they are all UNSECURED I control the router anyway but If IM not using Linux platform I will automaticaly reinstall the security on the network You see !  But so far I was able to use Updates manager to update apx 165 new updates from my 10.04 lucid lynx platform  So so far so good!
 
If u have time   a little help on *Commands*  to install wpa/wpa2 on my linux line connection 
 Even if i try   pwa/wpa2  on the NM   it doent work ?? I tried many ways It doesnt want to connect ??
 
psssit (Comment est la temperature a Paris  Ici c'est le printemps a Montreal Canada)
See you aroud ok
Bye 
John  
 
Psssit merci pour ton aide 0

---

### Post by flash63 on 2010-10-13
> But i had to disabled the *Security* wpa/WPA2 * in my router (Otherwise I cannot connect) 
That's exactly what i wrote:
> For a trouble free and save connection with the Network-Manager You previously switch your Router security configuration to pure WPA2-AES (CCMP) Encryption. 

Don't use mixed encryption WPA1/WPA2!

---

### Post by edm00se on 2010-10-14
> **flash63 said:**
> Hi,
i think you can use the rt2870sta module. Test it.

Add the ID (command in one line):
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
Load the Module
```
sudo modprobe rt2870sta
iwconfig
```
Interface available? Try to connect!

The solution works? Ok, automatic driver load if the stick was plugged in:
```
sudo gedit /etc/udev/rules.d/10-d_link.rules
```
contents:
```
# UDEV-Rule for D-LINK DWA-125N ID 07D1 :3C0D
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c0d", RUN+="/sbin/modprobe rt2870sta"
```
make it ready to work
```
sudo service udev reload
```
.. or restart

This worked perfectly for me in Ubuntu v10.10 "Maverick Meerkat". My device id was 07d1:3c16 with a D-Link DWA-125 H/W Rev. A2. Thanks for the help and glad to confirm it working on 10.10!

---

### Post by flash63 on 2010-10-14
> **edm00se said:**
> This worked perfectly for me in Ubuntu v10.10 "Maverick Meerkat". My device id was 07d1:3c16 with a D-Link DWA-125 H/W Rev. A2. Thanks for the help and glad to confirm it working on 10.10!
Hello,
in this case you must probably block the module rt2800usb permanently to avoid a collision between this driver modules.

Check  the loaded modules:
```
lsmod | grep rt2
```
If rt2800usb was listed add the module to the blacklist file:
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Remove the Stick and unload the Module:
```
sudo modprobe -r rt2800usb
```
Reconnect the Stick.

---

### Post by johnsuffer on 2010-10-15
> **flash63 said:**
> That's exactly what i wrote:
 
Don't use mixed encryption WPA1/WPA2!
 
HEY FLASH63 TKS FOR U,R HELP
But since I am connected now OK ! And  I can surf the web ok
 But I still have a little *Glitch* in the connection ? As you suggest I disambled the wpa/wpa2 encription in my router to surf the web but that leaves out all my network UNSECURED ? We are 7 differents workstation in my builing ! Now to let me use Linux platform They all would have to leave the network *working* unsecured just for me ? I am the only  one assigned to control the *Router* But ethiquely talking I cannot let the network UNSECURED just for my pleasure to surf with linux Unbutu 10.04 lucid lyxn platform **So I need  solutions** with the***Right*commands** to get around this. Any suggestions would be appreciate !
Regards
Johnsuffer :-)

---

### Post by flash63 on 2010-10-15
> As you suggest I disambled the wpa/wpa2 encription in my router to surf the web but that leaves out all my network UNSECURED ?
Take a look at the security configuration at your Router. Don't switch off the encrytion, change it to pure WPA2-AES (CCMP). 

WEP - old an very unsave, cracked in minutes
WPA (WPA1) TKIP - based on WEP with automatich security key change (unsave)
WPA2-AES (CCMP) - the best 128bit key encryption for private networks (use this)

You use WPA1/WPA2-Mixed Mode. Many routers offer this option for older WiFi-Equipment that do not support WPA2, but the Network-Manager has some trouble to connect with this type of encryption. 

If ...
 * your Router does not allow to set WPA2 only
 * one of the other workstations supports only WPA(1)
... deinstall the NM and use Wicd instead.

```
sudo apt-get install wicd
sudo apt-get remove --purge network-manager network-manager-gnome
```
Restart.

What kind of router do you use (Manufacturer and type/model)?

---

### Post by johnsuffer on 2010-10-16
PROBLEM (**SOLVED**) IM FINALLY CONNECTED TO MY NETWORK 192.168.2.1

Here a short resume of what i did  With helps  from ** Pytheas22 (Ndiswrapper guide)**
and help of **Flash63    To install easy commands**.and  resolved once for all the  installation of the (**DLINK_DWA DRT 2870)** driver who will become (**rt2870sta.inf**)
(**For the newbees like me**) 

To join those masters of Ubuntu 10.04 lucid lynx  Just type 
in The forum   1/  **Wireless networking** and search by **Users names** **Pytheas22 and Flash63** in the Networking and wireless  department.


**Step1 **/ Making sure you removed once for all the default driver by doing the blacklist commands

 blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb


commands :

  
 sudo gedit /etc/modprobe.d/ blacklist.conf  blacklist rt2800usb   blacklist rt2x00usb   

clacklist rt200lib

---------------------------------------------------------------------------------------------
**SAVED  TWICE  TO MAKE SURE  THEY ARE GONE**


** NOTE  Those are the 3 modules attached to the default driver * rt2800usb * when you dowloaded and install ubuntu 10.04 Lucid Lynx  This is the driver always showing up after you install your** .inf file from the CD d-link driver file**( Of course You did this installation with **ndiswrapper 9.1** and** ndiswrapper common 1.50** and **ndisgtk 1.8)** All the complete installation is describe by **Phytheas22 Nice GUIDE** **  yOU REALLY HAVE TO INSTALL THOSE 3 PROGRAMS CORRECTLY IF YOU WANT TO USE A WINDOWS BASE DRIVER.  At the top menu pressing administration go menu down up to Windows Drivers installation **

**STEP 2/** Now the trick is to first **removed** the **dtr2870.inf file  **installed withe the windows drivers window install

Why ! Finally i found out this with helps from **Flash63**  That .inf  file is NOT GOOD !

So i copy it on my linux desktop and changed the name for this (Pls exactly like this)

**drt2870sta.inf**


**STEP 3/** Redo the procedure to install using the (Windows driver install) in admistration menu   and install the new file   =   **  drt2870sta.inf**

A screen will pop up stating  driver install but not sure if  present ?  Don't worry about this ok

**Step 4/**

command :

sudo  ls -C network

answer  

Finally it will show   ***USB***  as  **driver** instead of the **rt2800usb**  

So you are close to connect now  !

**Follow instructions   from Flash63  and  reboot and you will be connected  right away.**

[B]here they are ::  Tks   to   Flash63   and its working ! WOW 

---------------------------------------------------------------------------------

[http://ubuntuforums.org/showthread.php?t=1593480](http://ubuntuforums.org/showthread.php?t=1593480)

GOOD LUCK EVERYONE !

[/B]

---

### Post by EmreSevinc on 2010-10-17
Hello,

I'm trying to connect to my wireless connection using my D-Link DWA-125  (N 150) Wireless USB Adapter. So far I was able to download, compile and  install the driver provided by RALINK. The current situation is:

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I assume that I'm using the correct driver, right?:

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I'm trying to up the ra0 interface and then do a scan, but I cannot see any networks:

```
$ sudo ifconfig ra0 up

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:2f:e9:81:08  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fee9:8108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5241984 (5.2 MB)  TX bytes:886749 (886.7 KB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ra0       Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet6 addr: fe80::f27d:68ff:fe14:19b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:858032 (858.0 KB)

ra0:avahi Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet addr:169.254.6.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results
```I also tried to "down" the eth0, again  no list scan result. I even tried from the Network Manager to connect to  a hidden network (even though it is not hidden, e.g. I can see my  network when I click on the Network Manager applet running on another  laptop, it lists my network among available networks and I can easily  connect) but without success. The point is this: I cannot see any wireless networks when I click on the NM applet, I only see Wired Network Auto eth0  and then Wireless networks disconnected and no list of networks :(

Here's some probably relevant output from $ sudo cat /var/log/syslog | grep -i network:

```

Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'ssid' value 'emretanya'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'scan_ssid' value '1'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'psk' value '<omitted>'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:  nm_setting_802_1x_get_pkcs11_engine_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:  nm_setting_802_1x_get_pkcs11_module_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: set interface ap_scan to 2
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):  supplicant connection state:  disconnected -> scanning
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):  supplicant connection state:  associating -> disconnected
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):  supplicant connection state:  disconnected -> scanning
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): association took too long.
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): asking for new secrets
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0):  supplicant connection state:  associating -> disconnected
Oct 17 01:51:30 yusuf-desktop NetworkManager[1694]: <warn> (ra0): link timed out.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 6 -> 9 (reason 7)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0) failed for access point (emretanya)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> Marking connection 'emretanya' invalid.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn>  Activation (ra0) failed.
```Am I missing something, or doing  something wrong?

I'm using Ubuntu 10.10 with latest updates and:

```
$ uname -a
Linux yusuf-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

```Also the led light on my adapter is flashing constantly (I take  this as a sign that is somehow active because before I installed the  driver correctly it was not flashing).

I also copied RT2870STA.dat to /etc/Wireless/RT2870STA/ and did not change it, so it is as below:
```

#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
```

---

### Post by pytheas22 on 2010-10-17
**EmreSevinc**: have you had a look at [this thread]("http://ubuntuforums.org/archive/index.php/t-1518043.html")?  The solution there--which also comes courtesy of flash63--should apply to you, because it's the exact same hardware (your wireless chipset ID is "07d1:3c16", as indicated by the "lsusb" output; the chipset dealt with in that thread has the same ID).

The only reason that thread might not work for you is that you downloaded and compiled the driver from Ralink's site, which apparently is not working.  To get back to the version of the driver that ships with Ubuntu, and which should work once you run the commands given in that thread, you have a couple options.  First, of course, you could simply reinstall Ubuntu from scratch.  A second, less dramatic option would be to reinstall just your kernel by running:
```

sudo apt-get install --reinstall linux-image-$(uname -r)
```

Reinstalling the kernel should replace your custom version the rt2870sta module with the default Ubuntu version.

Once you have the default version, run flash63's commands from the other thread and you should be good to go.

**johnsuffer**: so I assume you're all set now and are able to connect to your secured network?

---

### Post by grasiatty on 2012-03-17
<a href="http://www.viziotvs.net">vizio tvs</a> That You Must Read or Be Left Out

---

