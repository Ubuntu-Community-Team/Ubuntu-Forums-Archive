---
title: "Wireless will not connect with 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Yahtzee on 2010-04-30
I have been using Ubuntu for about 3 months.  I have a Dell Latitude C840 ( dinosaur ) and am dual booting 9.10 and 10.04 ( til I can get everything right!).  Have been perusing new threads all day to find solutions to wireless connections, but haven't quite found what I need.  

Problem:  Upon boot-up in 10.04, there is a "busy" icon displayed for the network connection while it tries to automatically connect, and it continues to spin around and around for a while, occasionally popping up a "Network Disconnected" box, until it just quits and displays the two monitors icon with a red "X".  When I click on the Network icon, the drop-down displays several possible connections including my router ( which I am connected to now through 9.10 ), so I know it is finding it, just won't connect.

                                 Terminal results:


                                  $ lspci  
 

 00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)  
 00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)  
 00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)  
 00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)  
 00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)  
 00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)  
 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)  
 02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller  
 02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller  
 02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller  
 02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)  
 

$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      IEEE 802.11b  ESSID:"05B407313310"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: None    
           Bit Rate:11 Mb/s   Sensitivity:1/0   
           Retry limit:8   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

                                   $ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:02:2d:7f:bc:b6   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:11 Base address:0xe100  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 





05B407313310 is my router.

 

This is the only machine I have, so I have had to restart and switch kernels to get an internet connection, then switch back to run Terminal and try solutions.  After about six hours of this back and forth, this is driving me insane, please help.

---

### Post by AmateurDev on 2010-05-06
I can't connect either after upgrading from 9.10. XP connects just fine.
EDIT:I have a Dell laptop infected with a virus on Windows, so I'm using the Live CD to boot 10.04, and that connects fine

---

### Post by Krovas on 2010-05-06
Here too. Got my RealTek antenna working, but it won't log in to my wireless with the key I've always used. Network Manager endlessly prompts me for the key.

---

### Post by AmateurDev on 2010-05-09
It seems that it is a bug with the Ralink Drivers, which is probably why my laptop works; it has an Intel chipset, but my desktop has a Ralink chipset.

---

### Post by AmateurDev on 2010-05-18
I have successfully connected. I followed the instructions here: [http://www.ctbarker.info/](http://www.ctbarker.info/) (You have to scroll down a little bit, but there are three posts in a row about it) At first it didn't work, it may for you, but I then changed my SSID from hidden to visible and changed the name and password. I still have WPA2 encryption, so the problem is solved. I hope it works for you

---

### Post by exXP on 2010-05-20
My problem is that on 10.04 I cannot connect automatically as I used to in 9.04 (I took a pass on 9.10) When I log on the icon says I am not on line and I have to type in the password (16 characters) to activate it.  I expect to do this first time I connect but not every time!  I have checked the 'Automatic' box but it makes no difference.  does any one have any suggestions?
exXP

---

### Post by PDA1 on 2010-05-20
Problem- no Networking enabled with Ubuntu 10.04. 



 Network connection was lost 1 day after I upgraded from 9.04. I couldn't connect to the web with wireless or ethernet and Networking was grayed and said it was “disabled” 
 The steps are numbered below (DO NOT enter the numbers when you're using Terminal)(anything in quotes marks doesn't need to be typed- they are there for reference only)
 
Here's how I fixed it- 
 Start TERMINAL 
 
[LIST=1]
[*]     sudo Nautilus
[/LIST]
 
[LIST=1]
[*]     Go to the folder /var/lib/NetworkManager/ 
[*]     Edit the file NetworkManager.state to read “setting NetworkingEnabled=true” 
[*]     Save the edited NetworkManager.state file 
[*]     Close Nautilus 
[*]     Using TERMINAL type “sudo restart network-manager”
[/LIST]
  This should enable networking again. I hope it works for you.....believe it or not it did for me.

---

### Post by AmateurDev on 2010-05-22
> **exXP said:**
> My problem is that on 10.04 I cannot connect automatically as I used to in 9.04 (I took a pass on 9.10) When I log on the icon says I am not on line and I have to type in the password (16 characters) to activate it.  I expect to do this first time I connect but not every time!  I have checked the 'Automatic' box but it makes no difference.  does any one have any suggestions?
exXP

The keyring might be broken. You have to go to Applications>Accessories>Passwords and Encryption Keys. Find the default keyring, then right-click and unlock it by typing in the keyring password(which you set up when you first typed in your network key). If this doesn't fix it permanently, then go back to the keyring, then delete the key for your network, this should work.

---

