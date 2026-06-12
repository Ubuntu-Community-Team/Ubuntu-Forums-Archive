---
title: "Wifi connects but no internet (Driver problem?)"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by Davste on 2010-11-23
Let me start by saying that I am new to ubuntu, and that I always use forums as a last resort.

I installed ubuntu 10, and immediately after the Wifi card deected my network name, and actually connected to it, but then I opened up firefox and....no internet.

Since then I have been trying to fix this problem, and after some research I found out that my card (PCI Cwp-905)  is RT2760 based, and I downloaded the linux RT2760 drivers for it.

The driver folder contained a readme file with commands you should enter to install it, and other setup files.
The problem: every command I typed in didn't work. I tried "make", and then "sudo make", but just got permission denied each time. I am now at a dead end. (Please note that I changed my directory to the folder location before doing this)

Does anyone know what I am doing wrong? If you want I can attach the driver files. Thank you in advance for your help.

---

### Post by iponeverything on 2010-11-23
prefix your commands with "sudo"

i.e.

sudo make

etc.

---

### Post by Davste on 2010-11-23
Thank you for your reply. I already tried, sudo make and make gave me the exact same result, with the exception that sudo asked me for a password. I typed it in, then same thing :(
When I get home I will post the exact error.

---

### Post by Davste on 2010-11-23
Yes! I reinstalled Ubuntu, followed these instructions, and they worked like a miracle!
Internet is up and running and blazing fast!

Note: Internet did not work until restart
Note2: In step 8, I replaced 
      ```
sudo cp rt2860sta.ko /lib/modules/2.6.*/kernel/drivers/staging/rt2860/ 
```to
     ```
 sudo cp rt2860sta.ko.dist /lib/modules/2.6.*/kernel/drivers/staging/rt2860/  
```> 
Step 1 
Download latest RT2860 driver source code from Ralink. 
 
 
Step 2 
Open and extract the downloaded file to your home directory - do not change the name. 
 
Open a terminal window and perform the following commands: 
 
    cd ~/2010* 
    gedit ./os/linux/config.mk 
 
 
Step 3 
Find the following lines (by default set to "n") and set them to be "y": 
 
    HAS_WPA_SUPPLICANT=y 
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y 
 
Save and close the file. 
 
 
Step 4 
Back in the terminal window perform the following command: 
 
    gedit ./common/cmm_wpa.c 
 
For the warning message choose "Western" then "Retry". 
 
Use the find command to locate "MIX_CIPHER_NOTUSE". Replace the entire line with this code: 
 
    WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES; 
 
Save and close the file. 
 
 
Step 5 
Make sure gcc is installed (usually is by default but if not install it via synaptic) then from the terminal window perform the following commands: 
 
    sudo make 
    sudo make install 
    sudo ifconfig wlan0 down    (on some hardware it is ra0) 
    sudo rmmod rt2860sta 
    sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist 
 
NOTE: Replace the * in the last command with the actual directory name of the current kernel (if you are unsure what it is, navigate to the directory in nautilus to check). 
 
 
Step 6 
Still in the terminal window perform the following commands: 
 
    sudo depmod -a 
    sudo modprobe rt2860sta 
    sudo ifconfig wlan0 up        (on some hardware it is ra0) 
 
 
Step 7 
Check that network manager can now select networks and connect to them. 
 
 
Step 8 
Back in the terminal window perform the following command: 
 
    sudo cp rt2860sta.ko /lib/modules/2.6.*/kernel/drivers/staging/rt2860/ 
 
NOTE: Replace the * in the last command with the actual directory name of the current kernel (if you are unsure what it is, navigate to the directory in nautilus to check). 
 
 
Step 9 
In the terminal window perform the following command: 
 
    gksudo gedit /etc/modules 
 
Add "rt2860sta" on a line at the end of the file then save and close it. 
 
 
Step 10 
Reboot and check that wireless still works.


Credits go to [scokem]("http://ubuntuforums.org/member.php?u=889174") for these awesome instructions

---

