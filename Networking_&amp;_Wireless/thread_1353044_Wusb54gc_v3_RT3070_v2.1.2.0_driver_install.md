---
title: "Wusb54gc v3 RT3070 v2.1.2.0 driver install"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by b k on 2009-12-12
INSTALLATION INSTRUCTIONS FOR 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 RALINK DRIVER FOR LINKSYS WUSB54GC V3
 
(these instructions are a compilation of input from everyone who posted on the thread Wireless Issues with WUSB54GC v3 started by radixor and credit should go to them. These instructions are a refinement - hopefully! of those found on post #182 of that same thread. This write-up is strictly on my own initiative and is not sanctioned by Linksys or Ralink). 
Try At Your Own Risk !!! - b k
 
&& **Last edited on 17th Jan 2010**: &&
&& **PROCEDURE C-1 added**.                                                                 &&
&& Ensure that your gateway/router is configured to broadcast your SSID or network name &&
&& Certain steps in the PROCEDUREs require you to copy and paste some code/commands into&&
&& some Ubuntu files. The attached Typical Output Screens for the Various Steps during  &&
&& RT3070 driver install.tar.gz file at end of Post #1 gives an indication of where to  &&
&& insert those codes/commands.                                                         &&
 
&& Zipped text **file 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall_edited_20100117.txt.zip supercedes** 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall_edited_20091216.txt     &&

 
There are **five** PROCEDURES listed below.
 
**Check the pre-requisites** for each procedure and decide for yourself which one to follow. 
 
 
SPECIAL NOTES :
 
- Once your wireless connection is working, EACH time that you use the Update Manager in Ubuntu to update to a higher generic kernel number will cause your WUSB54gc v3 to stop functioning again.
 
- Again choose and proceed with the relevant set of procedure (paying special attention to the 2.6.31-xx generic kernel number that you have just updated to.
 
- Your wireless adapter should function normally again at the end of the relevant procedure.
 
 
 
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
start of Procedure A
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 
********************************
**PROCEDURE A**
********************************
 
Pre-requisites:
 
- FRESH install of Ubuntu 9.10 desktop 32 bit version with **2.6.31-14-generic kernel**.
- (Go to: Applications, Accessories, Terminal and type uname -r to check).
- NetworkManager must be installed (this is usually installed by default during Ubuntu OS installation).
- You DID NOT manually install ndiswrapper, Wifi radar and wicd
- (Go to: System, Administration, Synaptic Package Manager and use the search to check)
- You DID NOT previously use other procedures and other Ralink drivers from OTHER posts/threads.
 
 
Before starting:
 
- Copy the attached .txt file and Ralink driver file (2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2) to your Ubuntu machine.
- This enables you to open the .txt file which contains the instructions and code/commands
- later on and use Copy and Paste technique to transfer the code into a Terminal window.
- This saves you a lot of time and cuts down a lot of human typing errors.
 
 
- Place the Ralink driver file in /home/user/Downloads (my computer has this directory and path).
- (if yours is different, substitute the /home/user part to match your own).
 
- **Ensure that your gateway/router is configured to broadcast your SSID or network name**
 
 
Suggestions: 
 
- precede your code with sudo if permission denied message pops up at any stage.
 
- Ensure that you are in the correct directory and path before executing each step. 
 
 
Go to :
 
Applications, Accessories, Terminal to open a terminal window (say on workspace "Desk 1")
 
Switch to another workspace "Desk 2" and open the .txt file with the instructions and codes.
 
Use copy and paste method to get commands into Terminal window on "Desk 1".
 
DON'T FORGET TO SUBSTITUTE THE /home/user PART TO MATCH YOUR DIRECTORY AND PATH FOR EACH STEP
 
 
Step 1 
 
Code: 
sudo -i 
 
 
 
Step 2 
 
Code: 
cd /home/user/Downloads 
 
 
 
Step 3 
 
Code: 
tar xjf 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2
 
 
 
Step 4 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
 
 
 
Step 5 
 
Code: 
gedit os/linux/usb_main_dev.c
 
and add the following line 
 
Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
 
Save and close 
 
 
 
Step 6 
 
Code: 
gedit os/linux/config.mk
 
change all the stuff to do with WPA_SUPPLICANT to y 
 
 
Save and close 
 
 
 
Step 7 
 
Code: 
gedit /etc/modules
 
add this line 
 
Code: 
alias ra0 rt3070sta 
 
Save and close
 
 
 
Step 8 
 
Code: 
gedit RT2870STA.dat
 
and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK
 
save and close 
 
 
 
For info : 
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 
 
- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 
 
- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point 
 
- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 
 
- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 
 
 
 
 
Step 9 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 
 
Code: 
make && make install 
 
 
 
Step 10
 
Code:
mkdir /lib/modules/2.6.31-14-generic/updates 
 
 
 
Step 11
 
Code: 
cp -p /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-14-generic/updates/
 
 
 
Step 12 
 
Code: 
depmod -a
 
 
 
Step 13
 
Code: 
mkdir /etc/Wireless/RT2870STA
 
Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 
 
Step 14 
 
Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local
 
 
 
Step 15 
 
Code: 
gedit /etc/modprobe.d/blacklist.conf
 
and add this 
 
Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb
 
Save and close 
 
 
 
Step 16 
 
Code:
sudo reboot 
 
 
 
Step 17 
 
Code: 
sudo gedit /etc/NetworkManager/nm-system-settings.conf
 
set managed=false to true 
 
save and close
 
 
 
Step 18 
 
Code: 
sudo reboot
 
 
If successful, wireless network will auto connect after reboot.
All credit goes to Kjeldgaard, JordanL, lesnoland, radixor jimbob and others on this forum
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
end of Procedure A
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
start of Procedure B
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 
********************************
**PROCEDURE B**
********************************
 
Pre-requisites:
 
- Ubuntu 9.10 desktop 32 bit version with **2.6.31-15-generic kernel.**
- (Go to: Applications, Accessories, Terminal and type uname -r to check).
- NetworkManager must be installed (this is usually installed by default during Ubuntu OS installation).
- You DID NOT manually install ndiswrapper, Wifi radar and wicd
- (Go to: System, Administration, Synaptic Package Manager and use the search to check)
- You DID NOT previously use other procedures and other Ralink drivers from OTHER posts/threads.
 
 
Before starting:
 
- Copy the attached .txt file and Ralink driver file (2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2) to your Ubuntu machine.
- (skip above step if you had previously successfully completed Procedure A).
 
- This enables you to open the .txt file which contains the instructions and code/commands
- later on and use Copy and Paste technique to transfer the code into a Terminal window.
- This saves you a lot of time and cuts down a lot of human typing errors.
 
 
- Place the Ralink driver file in /home/user/Downloads (my computer has this directory and path).
- (skip above step if you had previously successfully completed Procedure A)
- (if yours is different, substitute the /home/user part to match your own).
 
- **Ensure that your gateway/router is configured to broadcast your SSID or network name**
 
 
Suggestions: 
 
- precede your code withsudo if permission denied message pops up at any stage.
 
- Ensure that you are in the correct directory and path before executing each step. 
 
 
Go to :
 
Applications, Accessories, Terminal to open a terminal window (say on workspace "Desk 1")
 
Switch to another workspace "Desk 2" and open the .txt file with the instructions and codes.
 
Use copy and paste method to get commands into Terminal window on "Desk 1".
 
DON'T FORGET TO SUBSTITUTE THE /home/user PART TO MATCH YOUR DIRECTORY AND PATH FOR EACH STEP
 
 
Step 1 
 
Code: 
sudo -i 
 
 
 
Step 2 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
cd /home/user/Downloads 
 
 
 
Step 3 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
tar xjf 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2
 
 
 
Step 4 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
 
 
 
Step 5 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
gedit os/linux/usb_main_dev.c
 
and add the following line 
 
Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
 
Save and close 
 
 
 
Step 6 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
gedit os/linux/config.mk
 
change all the stuff to do with WPA_SUPPLICANT to y 
 
Save and close 
 
 
 
Step 7 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
gedit /etc/modules
 
add this line 
 
Code: 
alias ra0 rt3070sta 
 
Save and close
 
 
 
Step 8 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
gedit RT2870STA.dat
 
and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK 
 
save and close
 
 
For info : 
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 
 
- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 
 
- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point 
 
- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 
 
- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 
 
 
 
 
Step 9 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 
 
Code: 
make && make install 
 
 
 
Step 10
 
Code:
mkdir /lib/modules/2.6.31-15-generic/updates 
 
 
 
Step 11
 
Code: 
cp -p /lib/modules/2.6.31-15-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-15-generic/updates/
 
 
 
Step 12 
 
Code: 
depmod -a
 
 
 
Step 13 
 
Code: 
mkdir /etc/Wireless/RT2870STA  (skip THIS LINE ONLY if you had previously successfully completed Procedure A)
 

Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 
 
Step 14 
 
Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local
 
 
 
Step 15 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
gedit /etc/modprobe.d/blacklist.conf
 
and add this 
 
Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb
 
Save and close 
 
 
 
Step 16 
 
Code:
sudo reboot
 
 
 
Step 17 (skip this step if you had previously successfully completed Procedure A)
 
Code: 
sudo gedit /etc/NetworkManager/nm-system-settings.conf
 
set managed=false to true 
 
save and close
 
 
 
Step 18 (skip this step if you had previously successfully completed Procedure A) 
 
Code:
sudo reboot
 
 
If successful, wireless network will auto connect after reboot.
All credit goes to Kjeldgaard, JordanL, lesnoland, radixor jimbob and others on this forum
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
end of Procedure B
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
start of Procedure C
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 
********************************
**PROCEDURE C**
********************************
 
Pre-requisites:
 
- Ubuntu 9.10 desktop 32 bit version with **2.6.31-16-generic kernel**.
- (Go to: Applications, Accessories, Terminal and type uname -r to check).
- NetworkManager must be installed (this is usually installed by default during Ubuntu OS installation).
- You DID NOT manually install ndiswrapper, Wifi radar and wicd
- (Go to: System, Administration, Synaptic Package Manager and use the search to check)
- You DID NOT previously use other procedures and other Ralink drivers from OTHER posts/threads.
 
 
Before starting:
 
- Copy the attached .txt file and Ralink driver file (2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2) to your Ubuntu machine.
- (skip above step if you had previously successfully completed Procedure A or B).
 
- This enables you to open the .txt file which contains the instructions and code/commands
- later on and use Copy and Paste technique to transfer the code into a Terminal window.
- This saves you a lot of time and cuts down a lot of human typing errors.
 
- Place the Ralink driver file in /home/user/Downloads (my computer has this directory and path).
- (skip above step if you had previously successfully completed Procedure A or B)
- (if yours is different, substitute the /home/user part to match your own). 
 
- **Ensure that your gateway/router is configured to broadcast your SSID or network name**
 
 
 
Suggestions: 
 
- precede your code with sudo if permission denied message pops up at any stage.
 
- Ensure that you are in the correct directory and path before executing each step. 
 
Go to :
 
Applications, Accessories, Terminal to open a terminal window (say on workspace "Desk 1")
 
Switch to another workspace "Desk 2" and open the .txt file with the instructions and codes.
 
Use copy and paste method to get commands into Terminal window on "Desk 1".
 
DON'T FORGET TO SUBSTITUTE THE /home/user PART TO MATCH YOUR DIRECTORY AND PATH FOR EACH STEP
 
 
Step 1 
 
Code: 
sudo -i 
 
 
 
Step 2 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
cd /home/user/Downloads 
 
 
 
Step 3 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
tar xjf 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2
 
 
 
Step 4 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
 
 
 
Step 5 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
gedit os/linux/usb_main_dev.c
 
and add the following line 
 
Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
 
Save and close 
 
 
 
Step 6 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
gedit os/linux/config.mk
 
change all the stuff to do with WPA_SUPPLICANT to y 
 
Save and close 
 
 
 
Step 7 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
gedit /etc/modules
 
add this line 
 
Code: 
alias ra0 rt3070sta 
 
Save and close
 
 
 
Step 8 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
gedit RT2870STA.dat
 
and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK 
 
save and close
 
 
For info : 
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 
 
- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 
 
- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point 
 
- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 
 
- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 
 
 
 
Step 9 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 
 
Code: 
make && make install 
 
 
 
Step 10
 
Code:
mkdir /lib/modules/2.6.31-16-generic/updates 
 
 
 
Step 11
 
Code: 
cp -p /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-16-generic/updates/
 
 
 
Step 12 
 
Code: 
depmod -a
 
 
 
Step 13 
 
Code: 
mkdir /etc/Wireless/RT2870STA  (skip THIS LINE ONLY if you had previously successfully completed Procedure A or B)
 
Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 
 
Step 14 
 
Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local
 
 
 
Step 15 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
gedit /etc/modprobe.d/blacklist.conf
 
and add this 
 
Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb
 
Save and close 
 
 
 
Step 16 
 
Code:
sudo reboot 
 
 
 
Step 17 (skip this step if you had previously successfully completed Procedure A or B)
 
Code: 
sudo gedit /etc/NetworkManager/nm-system-settings.conf
 
set managed=false to true 
 
save and close
 
 
 
Step 18 (skip this step if you had previously successfully completed Procedure A or B) 
 
Code:
sudo reboot
 
 
If successful, wireless network will auto connect after reboot.
All credit goes to Kjeldgaard, JordanL, lesnoland, radixor jimbob and others on this forum
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
end of Procedure C
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 

++++++++++++++++++++++++++++++++++++++++++++++++++++++++
start of Procedure C-1
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

********************************
**PROCEDURE C-1**
********************************

Pre-requisites:

- Ubuntu 9.10 desktop 32 bit version with **2.6.31-17**-**generic kernel**.
- (Go to: Applications, Accessories, Terminal and type uname -r to check).
- NetworkManager must be installed (this is usually installed by default during Ubuntu OS installation).
- You DID NOT manually install ndiswrapper, Wifi radar and wicd
- (Go to: System, Administration, Synaptic Package Manager and use the search to check)
- You DID NOT previously use other procedures and other Ralink drivers from OTHER posts/threads.
 
 
Before starting:

- Copy the attached .txt file and Ralink driver file (2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2) to your Ubuntu machine.
- (skip above step if you had previously successfully completed Procedure A, B or C).

- This enables you to open the .txt file which contains the instructions and code/commands
- later on and use Copy and Paste technique to transfer the code into a Terminal window.
- This saves you a lot of time and cuts down a lot of human typing errors.
     
- Place the Ralink driver file in /home/user/Downloads (my computer has this directory and path).
- (skip above step if you had previously successfully completed Procedure A, B or C)
- (if yours is different, substitute the /home/user part to match your own).     

- **Ensure that your gateway/router is configured to broadcast your SSID or network name**
    
 
Suggestions: 
 
- precede your code with sudo if permission denied message pops up at any stage.

- Ensure that you are in the correct directory and path before executing each step. 

 
Go to :

Applications, Accessories, Terminal    to open a terminal window (say on workspace "Desk 1")

Switch to another workspace "Desk 2" and open the .txt file with the instructions and codes.

Use copy and paste method  to get commands into Terminal window on "Desk 1".

DON'T FORGET TO SUBSTITUTE THE /home/user PART TO MATCH YOUR DIRECTORY AND PATH FOR EACH STEP


Step 1 
 
      Code: 
sudo -i 
 

 
Step 2  (skip this step if you had previously successfully completed Procedure A, B or C)
 
      Code: 
cd /home/user/Downloads 

 
 
Step 3  (skip this step if you had previously successfully completed Procedure A, B or C)
 
      Code: 
tar xjf 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2



Step 4    (skip this step if you had previously successfully completed Procedure A, B or C) 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0


 
Step 5    (skip this step if you had previously successfully completed Procedure A, B or C) 
 
      Code: 
gedit os/linux/usb_main_dev.c

and add the following line 
 
      Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */

save and close 

 
 
Step 6    (skip this step if you had previously successfully completed Procedure A, B or C) 
 
      Code: 
gedit os/linux/config.mk

change all the stuff to do with WPA_SUPPLICANT to y 

 
save and close 
         
 
Step 7    (skip this step if you had previously successfully completed Procedure A, B or C) 
 
      Code: 
gedit /etc/modules

add this line 
 
      Code: 
alias ra0 rt3070sta 
 
save and close

 
 
Step 8    (skip this step if you had previously successfully completed Procedure A, B or C) 
 
      Code: 
gedit RT2870STA.dat

and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK 


save and close
 
For info :  
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 

- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 

- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point  

- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 

- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 

 
 
Step 9 
 
      Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 
 
      Code: 
make && make install     


 
Step 10
 
      Code:
mkdir /lib/modules/2.6.31-17-generic/updates 
 
  

Step 11
 
      Code: 
cp -p /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-17-generic/updates/


 
Step 12 
 
      Code: 
depmod -a


 
Step 13  

      Code: 
mkdir /etc/Wireless/RT2870STA    (skip THIS LINE ONLY if you had previously successfully completed Procedure A, B or C) 

 
      Code: 
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
 

Step 14 
 
      Code: 
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local


 
Step 15    (skip this step if you had previously successfully completed Procedure A, B or C) 
 
      Code: 
gedit /etc/modprobe.d/blacklist.conf

and add this 
 
      Code: 
blacklist rt2x00usb 
blacklist rt2x00lib 
blacklist rt2800usb

save and close 
 
 

Step 16

      Code: 
sudo reboot

 

Step 17  (skip this step if you had previously successfully completed Procedure A, B or C)
 
      Code: 
sudo gedit /etc/NetworkManager/nm-system-settings.conf

set managed=false to true 


save and close 
 
 
Step 18  (skip this step if you had previously successfully completed Procedure A, B or C)

      Code: 
sudo reboot

If successful, wireless network will auto connect after reboot.
All credit goes to Kjeldgaard, JordanL, lesnoland, radixor jimbob and others on this forum
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
end of Procedure C-1
++++++++++++++++++++++++++++++++++++++++++++++++++++++++



 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
start of Procedure D
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 
********************************
**PROCEDURE D**
********************************
 
This section is for people who have read OTHER threads/posts, tried OTHER procedures and OTHER Ralink drivers with manually installed ndiswrapper, Wifi radar and maybe wicd and maybe with NetworkManager uninstalled but WITHOUT success in getting the WUSB54gc v3 to function.
You are also likely to have mixed drivers and procedures from OTHER different threads/posts.
 
1. STRONGLY SUGGEST YOU DO A RE-INSTALLATION OF YOUR UBUNTU OS AND START WITH PROCEDURE A if possible. REMEMBER to back up your data FIRST to an external hard disk or a secondary hard disk.
If doing re-installation, consider choosing manual hard disk partitioning and having a root, a home, and a swap partition during the reinstall.
 
2. If you do not wish to do a OS re-installation yet,
--- Uninstall ndiswrapper, Wifi radar and wicd from your system.
--- Reinstall NetworkManager.
--- (installation and removal of programs can be done from within Synaptic Package Manager).
--- Find out the current 2.6.31-1x-generic kernel number.(type uname -r in a Terminal window).
--- Based on your current generic kernel number, choose one of the relevant procedures above (ie PROCEDURE A, B, C or C-1) to try out.
 
 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
end of Procedure D
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

---

### Post by grief -l on 2009-12-12
Thanks B_K, I read it thru and I think I'll give it one more shot. Just one thing:
 
> consider choosing manual hard disk partitioning and having **a root, a home,** and a swap partition during the reinstall.

 
How do you do that? Have a root and home?
 
 
Thanks,
 
Gabe.

---

### Post by b k on 2009-12-12
> **grief -l said:**
> Thanks B_K, I read it thru and I think I'll give it one more shot. Just one thing:
 
 
 
How do you do that? Have a root and home?
 
 
Thanks,
 
Gabe.
 
If you choose to do this remember to **BACKUP** your personal data **BEFORE** proceeding preferably to an external or a secondary hard disk.
All existing data will be **wiped out !!!**
 
During installatio of Ubuntu Os there is an option to do manual partitioning of hard disk. This enables you to choose how many partitions you would like to have.
I suggest you create 3 primary partitions.
For the first partition choose **/** (ie root) as your mount point,
For the second partition choose **/home **as your mount point.
The third is a swap partition.
 
For more info go to link below or try googling for hard disk partitioning.
 
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by b k on 2009-12-12
Hi, anyone with say a fresh install of Ubuntu Os and who is unable to connect to the wireless network SHOULD NOT immediately go about installing **additional** software like wicd, ndiswrapper and wifi radar to try and solve their problem.

You already have NetworkManager installed (by default) during Os installation. and it is probably running in the background.

Installing the **additional** software above (which basically does the same function - that is managing and scanning for networks) will probably create **more** headaches for you as they are probably running in the background at the same time and may conflict with each other.

However I am in no way suggesting that the **additional** software is inferior.

I think what appears to be a more logical way to solve your wireless connection problem is to use what has been installed by default during Os installation and find a workable procedure (and try to stick to your chosen procedure - at least for a while) until your connection is up and running.

After that, you may experiment further with the other additional software (but probably making sure only **one** is installed on your computer **at any one time** - ie temporarily remove/uninstall the other network managing/scanning software).

I have personally used the above procedures (with the default installed NetworkManager **only**) and succeeded in establishing network connection every time - all the way from 2.6.31-14-generic to  2.6.31-16-generic kernels.

NetworkManager should be more than adequate for most users. 

Just my  two cents worth.

---

### Post by grief -l on 2009-12-12
> For the first partition choose **/** (ie root) as your mount point,
For the second partition choose **/home **as your mount point.
The third is a swap partition.

 
Okay, but I don't need it since I don't have or intend having any data stored on my HDD. Anyhow, don't want to hijack your thread with that. Will try doing the driver thing tomorrow if I get time.
 
Gabe

---

### Post by b k on 2009-12-13
> **grief -l said:**
> Okay, but I don't need it since I don't have or intend having any data stored on my HDD. Anyhow, don't want to hijack your thread with that. Will try doing the driver thing tomorrow if I get time.
 
Gabe

If you intend to use **this thread** post #1 as your starting point please ensure that you use the .txt file  (with the instructions and code/commands) and Ralink driver file **attached to the end of post #1**.

The reason for this is that Ralink changed the way they named their driver file from time to time and this affects the code/commands.

I am highlighting this to you because I noticed that you also posted on **another** thread (started by radixor). 
If you choose to start at #182 of that thread, please use the files attached to the end of that post #182.

If you follow the instructions carefully from a fresh Ubuntu 9.10 desktop 32 bits version install (remember to use copy and paste technique) - you will succed.

Could you help by posting so that if necessary the instructions on this thread post #1 can be refined to help more people.

Good luck

---

### Post by grief -l on 2009-12-13
I've downloaded the attachments already (as soon as you posted them) and bookmarked this page because I intend to reinstall fresh and use your instructions. I'll certainly post back, just don't know when. I have other stuff to do and this isn't a priority right now, but that in no way means it's not appreciated.
 
Gabe

---

### Post by Trifidlebock on 2009-12-14
I reformatted and followed up until step #9, then got the following message (no clue how to proceed):

root@user:/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make && make install 
make -C tools
make[1]: Entering directory `/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: In function ‘RTUSBWatchDog’:
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:758: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘ULONG’
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: At top level:
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or ‘(’ before ‘{’ token
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or ‘(’ before ‘,’ token
make[2]: *** [/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o] Error 1
make[1]: *** [_module_/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

---

### Post by b k on 2009-12-14
> **Trifidlebock said:**
> I reformatted and followed up until step #9, then got the following message (no clue how to proceed):
 
root@user:/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make && make install 
make -C tools
make[1]: Entering directory `/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
CC [M] /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: In function ‘RTUSBWatchDog’:
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:758: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘ULONG’
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: At top level:
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or ‘(’ before ‘{’ token
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or ‘(’ before ‘,’ token
make[2]: *** [/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o] Error 1
make[1]: *** [_module_/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
 
Hi, please do the following:
 
Ensure that your wireless gateway/router is configured to **broadcast your SSID** (ie your wireless network name).
I have personally found that 'hidden networks' will cause your connection to work erratically.
 
Redo Step 8
**save and close **(this was accidentally left out)
 
Step 16
**sudo** reboot (the word sudo was accidentally left out)
 
Step 17 (it is OKAY to redo this step
after setting managed=false to **true**
**save and close **(this was accidentally left out)
 
Step 18
**sudo** reboot (the word sudo was accidentally left out)
 
 
I just found out that if you start with **2.6.31-14-generic kernel **once your wireless connection works the **first** time and you use the update manager in Ubuntu, one of the recommended updates is to update straight away to **2.6.31-16-generic kernel.**
 
This means that you should be able to skip PROCEDURE **B**
 
The above amendments apply to the **relevant steps in all** the procedures.
 
My apologies for the omissions.
I am in the process of updating the post#1
 
Please post if you face anymore problems and I shall try my best to help (though I am also relatively new to Ubuntu).
**Trust me the procedure works**.

---

### Post by b k on 2009-12-14
To all the readers of this thread post #1 who have previously downloaded the 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall.txt file (containing the instructions and codes)  please be advised that I have removed that file and uploaded the new one incorporating the accidental omissions to tie in with the current code/commands shown in the edited post#1.

The new (latest) file name is 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall_edited_20091214.txt.

A summary of the omissions is as follows:

Step 8
**save and close **(this was accidentally left out)
 
Step 16
**sudo** reboot (the word sudo was accidentally left out)
 
Step 17
after setting managed=false to [B]true
[/B]**save and close **(this was accidentally left out)
 
Step 18
**sudo** reboot (the word sudo was accidentally left out)


Ensure that your gateway/router is configured **to broadcast your SSID** (this is your wireless network name).
Your wireless connection will perform erratically if your gateway/router is not configured to broadcast your SSID - i.e 'hidden'

[B]The ralink driver file remains unchanged.
[/B]
There is no problem if you have to redo the steps in the relevant procedure.
In this case, the information that you have changed/input into the files in the relevant steps previously are still there.
You should be able to skip Step 3 and the other code lines that start with mkdir........(mkdir means make directory) if you had successfully executed these code/commands previously.


THE PROCEDURE WORKS !!!

---

### Post by willrockformilk on 2009-12-14
> **Trifidlebock said:**
> I reformatted and followed up until step #9, then got the following message (no clue how to proceed):

root@user:/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make && make install 
make -C tools
make[1]: Entering directory `/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: In function &#8216;RTUSBWatchDog&#8217;:
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:758: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217;
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: At top level:
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token
/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
make[2]: *** [/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o] Error 1
make[1]: *** [_module_/home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

Trifidlebock,

I receieved this error at one point as well and found that when i added the line in stop 5 i added it to the wrong place. make sure you find where the rest of the devices are in that file and add the line to the END of that list. NOT the end of the file. 

The beggining of your file should look like this: 

```
/*
 *************************************************************************
 * Ralink Tech Inc.
 * 5F., No.36, Taiyuan St., Jhubei City,
 * Hsinchu County 302,
 * Taiwan, R.O.C.
 *
 * (c) Copyright 2002-2007, Ralink Technology, Inc.
 *
 * This program is free software; you can redistribute it and/or modify  * 
 * it under the terms of the GNU General Public License as published by  * 
 * the Free Software Foundation; either version 2 of the License, or     * 
 * (at your option) any later version.                                   * 
 *                                                                       * 
 * This program is distributed in the hope that it will be useful,       * 
 * but WITHOUT ANY WARRANTY; without even the implied warranty of        * 
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         * 
 * GNU General Public License for more details.                          * 
 *                                                                       * 
 * You should have received a copy of the GNU General Public License     * 
 * along with this program; if not, write to the                         * 
 * Free Software Foundation, Inc.,                                       * 
 * 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             * 
 *                                                                       * 
 *************************************************************************/

#include "rt_config.h"


// Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site(www.ralinktech.com) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
MODULE_LICENSE("GPL");
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //


/* module table */
struct usb_device_id rtusb_usb_id[] = {
#ifdef RT3070
    {USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
    {USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
    {USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
    {USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
    {USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
    {USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
    {USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
    {USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
    {USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
    {USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
    {USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
    {USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
    {USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
    {USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
    {USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
    {USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
    {USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
    {USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
    {USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
    {USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
    {USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
    {USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
   [COLOR=Red] {USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */[/COLOR]
#endif // RT3070 //
    { }/* Terminating entry */
};
```

Where you should add the entry is highlighted.

The error is basically saying that you have a syntax error in the code of the file which means you probably added it in the wrong place. or forgot the , after the driver but before the comment section.

Hope this helps.

BK you should probably mention that in your procedure somewhere.

---

### Post by b k on 2009-12-14
> **willrockformilk said:**
> Trifidlebock,

I receieved this error at one point as well and found that when i added the line in stop 5 i added it to the wrong place. make sure you find where the rest of the devices are in that file and add the line to the END of that list. NOT the end of the file. 

The beggining of your file should look like this: 

```
/*
 *************************************************************************
 * Ralink Tech Inc.
 * 5F., No.36, Taiyuan St., Jhubei City,
 * Hsinchu County 302,
 * Taiwan, R.O.C.
 *
 * (c) Copyright 2002-2007, Ralink Technology, Inc.
 *
 * This program is free software; you can redistribute it and/or modify  * 
 * it under the terms of the GNU General Public License as published by  * 
 * the Free Software Foundation; either version 2 of the License, or     * 
 * (at your option) any later version.                                   * 
 *                                                                       * 
 * This program is distributed in the hope that it will be useful,       * 
 * but WITHOUT ANY WARRANTY; without even the implied warranty of        * 
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         * 
 * GNU General Public License for more details.                          * 
 *                                                                       * 
 * You should have received a copy of the GNU General Public License     * 
 * along with this program; if not, write to the                         * 
 * Free Software Foundation, Inc.,                                       * 
 * 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             * 
 *                                                                       * 
 *************************************************************************/

#include "rt_config.h"


// Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site(www.ralinktech.com) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
MODULE_LICENSE("GPL");
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //


/* module table */
struct usb_device_id rtusb_usb_id[] = {
#ifdef RT3070
    {USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
    {USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
    {USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
    {USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
    {USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
    {USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
    {USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
    {USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
    {USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
    {USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
    {USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
    {USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
    {USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
    {USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
    {USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
    {USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
    {USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
    {USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
    {USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
    {USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
    {USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
    {USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
    {USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
    {USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
    {USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
    {USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
    {USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
    {USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
    {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
   [COLOR=Red] {USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */[/COLOR]
#endif // RT3070 //
    { }/* Terminating entry */
};
```Where you should add the entry is highlighted.

The error is basically saying that you have a syntax error in the code of the file which means you probably added it in the wrong place. or forgot the , after the driver but before the comment section.

Hope this helps.

BK you should probably mention that in your procedure somewhere.

Hello, I have also placed the line [COLOR=Red]{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */ [COLOR=Black] in that location.

For those who have not done it, place your pointer at the end of [/COLOR][/COLOR]{USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */ and left click, press enter, then press tab key once then paste [COLOR=Red]{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */  [COLOR=Black] - this will align it nicely.
Don't forget to save and close.

One question, have you succeeded in getting your wireless connection working on your Ubuntu machine or are you posting from another machine?

[/COLOR][/COLOR][COLOR=Red][COLOR=Black]Thanks for the input.[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]


[/COLOR][/COLOR]

---

### Post by willrockformilk on 2009-12-14
I still havent gotten it to work on 9.04 yet. im using the wired connection currently.

:-/

---

### Post by b k on 2009-12-14
> **willrockformilk said:**
> I still havent gotten it to work on 9.04 yet. im using the wired connection currently.
 
:-/
 
My starting point with all the procedures was Ubuntu 9.10.
I don't know how different version 9.04 is.
 
Nevertheless, I have uploaded another file containing  typical output screen shots at the end of the various steps during RT3070 driver install. Check post #1 attachments.
 
Hope that it can provide you with a little more clue to what is going on during the driver install process.
 
I am sure you will succeed eventually.
 
Good luck

---

### Post by willrockformilk on 2009-12-14
yup this procedure did not work for 9.04 jaunty fresh install(2.6.28-11-generic). dunno why but i guess ill install 9.10 tomorrow and give this procedure a try again.

---

### Post by b k on 2009-12-14
> **willrockformilk said:**
> yup this procedure did not work for 9.04 jaunty fresh install(2.6.28-11-generic). dunno why but i guess ill install 9.10 tomorrow and give this procedure a try again.
 
Hi there, if you are going to re-partition your hard disk can you read post #3 of this thread.
 
If you **follow** the partitioning scheme suggested there, you **need not modify anything** at all to the procedures posted in post #1 .
 
The pasting and copying of commands would then be a piece of cake!
 
Good luck.

---

### Post by b k on 2009-12-15
Hi, I tried everything from fresh install of Ubuntu 9.10 yesterday again from 2.6.31-14-generic kernel. Wireless connection worked very well.

Ubuntu's update manager then offered updates this time straight away to 2.6.31-16-generic kernel (ie skipping 2.6.31-15-generic kernel).

I accepted all the offered updates and at the end of the updating, the wireless connection failed as previously.

Skipping PROCEDURE B and doing PROCEDURE C got my wireless connection up and running flawlessly again.

I have just uploaded a new .txt file (containing the instructions and codes/commands) and edited post #1 accordingly to refine the PROCEDURES B and C.
The latest file is 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall_edited_20091216.txt.

These are the minor changes that allows you to skip some redundant steps.

%%% The following amendments/comments were added in on 16th Dec 2009 %%%
%%% Some redundant steps can be skipped in PROCEDURES B and PROCEDURES C if PROCEDURE A %%%
%%% was successful.                                                                     %%%
%%% For FRESH install of Ubuntu 9.10 after successful completion of PROCEDURE A your    %%%
%%% wireless network will work and the Update Manager will now offer to update your kernel    %%%
%%% to 2.6.31-16-generic kernel   straight away - that is you can                                                  totally skip PROCRDURE B%%%


Your wireless connection will continue to work as long as you do not update to a newer generic kernel number.

Any comments/feedback would be most appreciated.

---

### Post by grief -l on 2009-12-22
OK b k, here we go,

**EDITED**, see next post.
 
Fresh install, followed procedure 1:
 
> Step 3 

Code: 
tar xjf 2009_1110_RT3070_Linux_STA_**v2.1.2.0**.tar.bz2
Should read v2**[1].**1.2.0
 
I didn't understand anything about the choices in Step 8 but filled in what I thought prudent. Got as far as step 9 and here is all the content of the console
 
Gabe

---

### Post by grief -l on 2009-12-22
**Please ignore my previous post**

I realized after reading your reply to **willrockformilk** that I had to add the headers (?) to the Device List and not at the end of the file.

I am now posting this from ubuntu, so wireless is working. Please turn your cheek so I can kiss you! Your help is more appreciated than I can express in words so I'll just say **thanks!**

Gabe

---

### Post by grief -l on 2009-12-28
Update:

So far it works fine for casual browsing. However, the first thing it wanted to do was download updates. During the half-hour process it must have disconnected and reconnected 10 or 12 times. Since then I have found that I can browse while listening to music (live feed), but as soon as I try to download anything over 1 MB or watch video it cuts out. This gets progressively worse until simple browsing (forums) slows down and eventually disconnects repeatedly. A reboot fixes the problem.

It's not satisfactory but I can live with it till I find another dongle or a real driver appears.

Thanks again b k!

Gabe

---

### Post by janeeps on 2009-12-28
thanks b k. i was finally able to make my dongle work, thanks to this guide.

i followed Procedure C since i already followed other guides.
[http://ubuntuforums.org/showthread.php?t=1342593&highlight=linksys+wusb54gc](http://ubuntuforums.org/showthread.php?t=1342593&highlight=linksys+wusb54gc)
[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

these guides suggest that the Linksys WUSB54GC v3 uses Ralink 2870.
however, it was silly of me that i did not finish reading the thread by radixor, and good thing you created another thread and i saw this thread of yours that suggest using RT3070. 

here are the steps that i did:

1) installed network-manager and also uninstalled wicd in the process by using synaptic package manager

2) followed from Step 1 to Step 16 SKIPPING Step 8 (the one where you edit the RT2870STA.dat file)

3) i downloaded the RT2870 driver from the Ralinktech website, extracted it, and **sudo make clean** (note: you won't need "sudo" if you're running as root) then **sudo make && make install**
(this step was to simply overwrite my previous RT2870 installation)

4) i reinstalled wicd and uninstalled network-manager in the process


iwconfig shows "ra0" and so i just had to configure wicd and i was able to connect to our wireless network


what i am suggesting is.. i think that it should be a point to reinstall the previous driver that didn't work (in my case, RT2870) so that it doesn't conflict with the RT3070 driver :)

---

### Post by b k on 2009-12-28
> **grief -l said:**
> Update:
 
So far it works fine for casual browsing. However, the first thing it wanted to do was download updates. During the half-hour process it must have disconnected and reconnected 10 or 12 times. Since then I have found that I can browse while listening to music (live feed), but as soon as I try to download anything over 1 MB or watch video it cuts out. This gets progressively worse until simple browsing (forums) slows down and eventually disconnects repeatedly. A reboot fixes the problem.
 
It's not satisfactory but I can live with it till I find another dongle or a real driver appears.
 
Thanks again b k!
 
Gabe
 
Hi, try configuring your gateway/router to broadcast your SSID (ie network name) if your wireless network is currently 'hidden'. It may help.
 
 
In terms of security. I believe that it does not make that much difference.

---

### Post by grief -l on 2009-12-29
Hi b k,

The router is broadcasting. Do you know how to change to another channel? Or at least find out which channel it's using now?

Gabe

---

### Post by b k on 2009-12-29
> **grief -l said:**
> Hi b k,
 
The router is broadcasting. Do you know how to change to another channel? Or at least find out which channel it's using now?
 
Gabe
 
Hi, in Step 8 of post #1 if you had left or set channel to 0 and you set infra (infrastructure ) mode when you where modifying the file. you should be OK.
 
Setting channel to 0 enables auto selecting of broadcasting channels.
 
To find out which channel your router/gateway is broadcasting on, you need to read your router documentation.
The documentation will point you to a web address from which you can view/change the channel that it is set to broadcast on (you will need a password to make any changes to the router settings).
 
Hope this info is of help to you. Good luck

---

### Post by gnitram on 2010-01-16
~$ uname -r
2.6.31-17-generic-pae


Hi 

I would like to follow your procedure -  I have the rt3070 chipset, my kernel is as above, should this mean I follow PartC for a 32bit 16 kernel? I am not sure if mine is 32bit or 64bit though, is that important, because last time I tried to find out, it appeared that it could be 64.

Thanks in advance

---

### Post by gnitram on 2010-01-16
Hi again,

Does anyone know about this, which to follow A, B or C if you have kernel 17?
and then what if you have a 64bit version?

Sorry if my message sounded a little vague, it is just that I am new here and I have already learnt a lot through reading the Ubuntu docs and user threads. One thing I have also learnt is not to advance with steps, when you are not sure what you are doing, as this week I had to wipe the system and re-installl.

---

### Post by b k on 2010-01-17
> **gnitram said:**
> Hi again,

Does anyone know about this, which to follow A, B or C if you have kernel 17?
and then what if you have a 64bit version?

Sorry if my message sounded a little vague, it is just that I am new here and I have already learnt a lot through reading the Ubuntu docs and user threads. One thing I have also learnt is not to advance with steps, when you are not sure what you are doing, as this week I had to wipe the system and re-installl.

Hi, I have  personal experience only on  the 32 bit Ubuntu desktop 9.10 version OS.

Suggest you read post #1 which I have just edited again (added PROCEDURE C-1 for people who currently have 2.6.31-17-generic kernel). Please note the **pre-requisites** for each PROCEDURE.

My **guess** is that what you are using should not be significantly different (where wireless connectivity is concern) from the 32 bit version.

If you wish to give it a try, download all the files at the end of post #1 (except 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall_edited_20091216.txt. This file is superceded by 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2 driver HowToInstall_edited_20100117.txt.zip which contains all the latest instructions/codes/commands)  to a usb stick so that they are available to you on your Ubuntu machine. 

The file Typical Output Screens for the Various Steps during RT3070 driver install.tar.gz gives you an indication where to copy and paste certain codes/commands which is required in certain steps of the relevant procedure.

Remember to use copy and paste technique during execution of the various steps in the relevant procedure to minimise typing errors.

I have just used PROCEDURE C-1 with 2.6.31-17-generic kernel to successfully connect to the internet using Linksys WUSB54gc v3  usb wireless dongle/stick.

Good luck

---

### Post by gnitram on 2010-01-17
Hi B K

thanks for the response I have not followed the procedure yet, because I am not sure if I meet the pre-requisites given that I did previously follow the procedure on the HowTo about the rt2870 [http://ubuntuforums.org/showthread.php?t=13425930](http://ubuntuforums.org/showthread.php?t=13425930), and i therefore think that I have built a rt2870 driver that is not functioning and needs to be uninstalled before I go any futher.

Would you be kind enough again to let me know if I do need to uninstall this and if so how?

Here are some of my terminal logs, I thought may be useful for you:

desktop:~$ uname -r
2.6.31-17-generic-pae
asrock@asrock-desktop:~$ sudo modprobe -r rt2870sta
[sudo] password for asrock: 
FATAL: Module rt2870sta is in use.
asrock@asrock-desktop:~$ 

asrock@asrock-desktop:~$ dmesg |grep rt28
[   15.994027] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.009942] usbcore: registered new interface driver rt2870
[   16.077563] Error: Driver 'rt2870' is already registered, aborting...
[   16.077576] usbcore: error -16 registering interface     driver rt2870

asrock@asrock-desktop:~$ sudo modprobe -r rt2870sta
[sudo] password for asrock: 
FATAL: Module rt2870sta is in use.
asrock@asrock-desktop:~$

---

### Post by b k on 2010-01-19
> **gnitram said:**
> Hi B K

thanks for the response I have not followed the procedure yet, because I am not sure if I meet the pre-requisites given that I did previously follow the procedure on the HowTo about the rt2870 [http://ubuntuforums.org/showthread.php?t=13425930](http://ubuntuforums.org/showthread.php?t=13425930), and i therefore think that I have built a rt2870 driver that is not functioning and needs to be uninstalled before I go any futher.

Would you be kind enough again to let me know if I do need to uninstall this and if so how?

Here are some of my terminal logs, I thought may be useful for you:

desktop:~$ uname -r
2.6.31-17-generic-pae
asrock@asrock-desktop:~$ sudo modprobe -r rt2870sta
[sudo] password for asrock: 
FATAL: Module rt2870sta is in use.
asrock@asrock-desktop:~$ 

asrock@asrock-desktop:~$ dmesg |grep rt28
[   15.994027] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.009942] usbcore: registered new interface driver rt2870
[   16.077563] Error: Driver 'rt2870' is already registered, aborting...
[   16.077576] usbcore: error -16 registering interface     driver rt2870

asrock@asrock-desktop:~$ sudo modprobe -r rt2870sta
[sudo] password for asrock: 
FATAL: Module rt2870sta is in use.
asrock@asrock-desktop:~$

Hi, I do not know of a safe way to uninstall your rt2870 driver.
However the person posting in post #21 seems to have done the same thing in an indirect way by reinstalling the same driver and letting the process **overwrite** the previous driver.
I believe that you need to download and decompress the same driver to the same location that you had done previously. Then open a Terminal window, change directory to that location and then execute the **make && install** command.
Hope that can do the trick for you.

After that you can give PROCEDURE C-1 a go if you like.
Note that this procedure is written for Linksys Wusb54gc v3 usb wireless adapter with ID **1737:0077** Linksys .
You need to open a Terminal window and execute command** lsusb** (assuming you have a usb wireless adapter) to find out your ID and substitute your ID number in Step 5 if yours is different (follow the format in the file that you are inputting the info into).

Any feedback/comment will be must helpful.

Good luck!

---

### Post by Xog on 2010-01-19
Tagging for view in a few days.

---

### Post by gnitram on 2010-01-20
> Hi, I do not know of a safe way to uninstall your rt2870 driver.
However the person posting in post #21 seems to have done the same thing in an indirect way by reinstalling the same driver and letting the process **overwrite** the previous driver.
I believe that you need to download and decompress the same driver to the same location that you had done previously. Then open a Terminal window, change directory to that location and then execute the **make && install** command.
Hope that can do the trick for you.

After that you can give PROCEDURE C-1 a go if you like.
Note that this procedure is written for Linksys Wusb54gc v3 usb wireless adapter with ID **1737:0077** Linksys .
You need to open a Terminal window and execute command** lsusb** (assuming you have a usb wireless adapter) to find out your ID and substitute your ID number in Step 5 if yours is different (follow the format in the file that you are inputting the info into).

Any feedback/comment will be must helpful.

Good luck!

Hi B K

thanks for your advice it has been much appreciated and I have found the procedure to be quite straightforward to follow. I tried applying what post #21 did and also omit step 8, before then repeating from the top of Procdure C-1. It did not work for me, I was having trouble with error messages of incorrect directory pathways when it came to copying and pasting the "                                  rt3070sta.ko" file. I imagine it is either to do with my inexperience or the problem of having a previously installed 2870 driver. Anyway, my decision is to abandon my pursuit of wireless for the time being, because I want to set up partitioning like you have mentioned, only for me I was thinking of having 3 partitions a stand alone swap partition, Ubuntu 9.10 and thirdly XBMC to run from boot on my Asrock ion330. It is because I hope to be able to boot up the xbmc directly from the Logitech harmony remote, with a little tweaking if not too complicated for me! #-o. Perhaps after I have done this and re-installed Karmic, it will mean that the wireless chip-driver issue will be more straightforward to solve.


Many thanks!

---

### Post by Xog on 2010-01-20
Would this work with 64-bit ubuntu?

---

### Post by b k on 2010-01-20
> **gnitram said:**
> Hi B K
 
thanks for your advice it has been much appreciated and I have found the procedure to be quite straightforward to follow. I tried applying what post #21 did and also omit step 8, before then repeating from the top of Procdure C-1. It did not work for me, I was having trouble with error messages of incorrect directory pathways when it came to copying and pasting the " rt3070sta.ko" file. I imagine it is either to do with my inexperience or the problem of having a previously installed 2870 driver. Anyway, my decision is to abandon my pursuit of wireless for the time being, because I want to set up partitioning like you have mentioned, only for me I was thinking of having 3 partitions a stand alone swap partition, Ubuntu 9.10 and thirdly XBMC to run from boot on my Asrock ion330. It is because I hope to be able to boot up the xbmc directly from the Logitech harmony remote, with a little tweaking if not too complicated for me! #-o. Perhaps after I have done this and re-installed Karmic, it will mean that the wireless chip-driver issue will be more straightforward to solve.
 
 
Many thanks!
 
Hi, a pity your attempt failed.
 
JANEEPS in post #21 seems the only one who sort of succeeded in 'undoing/overwriting' his failed procedure/driver from initially following *other* threads, then following PROCEDURE C *here* and succeeding.
Unfortunately JANEEPS did not provide enough details of his 'undoing/overwriting'.
 
I was hoping that you could provide more details (if you had succeeded) on the 'undoing/overwriting' of previous failed procedure/driver from other threads so that the info can help others.
 
Yes you need to have some understanding of file directory/paths if your hard disk partitioning scheme is different so that you can made some minor modifications to the codes/commands mentioned in post #1 here.
 
Thanks for the feedback and good luck on your new adventure!

---

### Post by b k on 2010-01-20
> **Xog said:**
> Would this work with 64-bit ubuntu?
 
Hi, I have no personal experience with 64-bit ubuntu.
 
Georgeg at post #235 of this link [http://ubuntuforums.org/showthread.php?t=1155941&page=24](http://ubuntuforums.org/showthread.php?t=1155941&page=24) seems to have succeeded using 64bit version of Mint 8.
 
The procedures on this thread are much more 'refined' and up to date but is basically the same as post #182 of the above link which Georgeg followed.
 
Please use the attached files at the end of whichever thread you wish to follow.
 
Any feedback/comments would be most helpful,
 
Good luck!

---

### Post by janeeps on 2010-01-24
Technically, all I think I really did was to actually redownload and reinstall the RT2870 driver. That's it. Here's what I did.



1) I downloaded the RT2870 driver in the same directory and extracted it also in the same directory
(in my case, it is in /home/jan/Documents/Downloads)


2) I ran terminal, changed the directory to the RT2870 folder
(mine was [COLOR="SeaGreen"]RT2870_LinuxSTA_V2.3.0.0[/COLOR] this is also the one in the Ralink website as [COLOR="Red"]RT2870USB(RT2870/RT2770[/COLOR] which can be found here [COLOR="Blue"]**[http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)**[/COLOR])

3) Then type **sudo make clean**

I wasn't able to put this in my previous post, but come to think of it, this may be what was missing. Typing "make clean" is necessary when you have done a prior installation, which is the case here. The concept of "make clean" is to start from scratch. The problem with directories may have come up because of this.

4) and then **sudo make && make install**



Do note that if you have another version of the RT2870 driver, you will have to **undo** all changes you have done to it by retracing the steps you have followed in the other threads. Some threads even provide a modified driver; if that is the case, you may have to modify it yourself.

I thought it was necessary to reinstall the driver for a certain reason: conflict. Seeing to it that you have followed other threads, they would have suggested you to also put [COLOR="Blue"]{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */ [/COLOR] in some specific file

In RT2870 drivers, you will have to add that code in the file [COLOR="SeaGreen"]*RT2870*/common/rtusb_dev_id.c[/COLOR] also like the one we did *here* wherein we add that code to [COLOR="#2e8b57"]*RT3070*/os/linux/usb_main_dev.c[/COLOR]
(In my case, the complete pathnames would be [COLOR="#2e8b57"]/home/jan/Documents/Downloads/RT2870_LinuxSTA_V2.3.0.0/common/rtusb_dev_id.c[/COLOR] and [COLOR="#2e8b57"]/home/jan/Documents/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/usb_main_dev.c[/COLOR] respectively.) You will see that both drivers will be recognizing the usb dongle and I think that this is the root of the conflict.



I'm sorry if I wasn't very specific in my previous post. I hope this helps :)

---

### Post by davidtolo on 2010-02-02
Does this also work for the Belkin N150  .. if so do I have to modify anything?  also my kernel is 64 bit

TY in advance,
David

---

### Post by b k on 2010-02-03
> **davidtolo said:**
> Does this also work for the Belkin N150 .. if so do I have to modify anything? also my kernel is 64 bit
 
TY in advance,
David
 
Hi, bearing in mind that I am quite new to Linux and I am not a trained IT person I shall try to see if I can provide you with some help.
 
I do not have first hand knowledge on the 64 bit verson OS but I believe that the Ralink RT3070 driver at the end of #post 1 should be able to work with your usb wireless (probably draft 'N' ) dongle.
 
Assuming you HAVE NOT tried any workarounds from OTHER threads (if you have, try to uninstall your previous attempts):
 
Go to a Terminal window in Ubuntu and type **uname -r **to find out which generic kernel you are running. Pick the relevant PROCEDURE to follow.
 
Go to a Terminal window in Ubuntu and type **lsub **to find out your usb device ID.
The output is something like ID **1737:0077** Linksys.
Use *your* output for STEP 5 to paste in the os/linux/usb_main_dev.c file.
 
If you have partitioned your hard disk *differently* from mine (ie a root, a home, and a swap), you need to modify directory and path in each step to match your own.
 
Open the file Typical Output Screens ............ attached to end of post #1 to have an idea of what to expect for each of the steps before starting.
 
At STEP 5 you need to place *your own info* from **lsub **in place of {USB_DEVICE(0x**1737**,0x**0077**)}, /* **Linksys WUSB54GC** */ 
Follow the format strictly as shown in the os/linux/usb_main_dev.c file.
 
At STEP 6 when you are in the os/linux/config.mk file you probably need to in addition also change a line to do with support for draft N from **n** to **y** (ie no to yes).
 
At STEP 8 you need to input your own info when you are within the RT2870STA.dat file.
 
Other then what I have mentioned above, you should be able to follow the rest of the steps without change (provided your hard disk partitioning scheme is similar to mine).
 
Remember you are basically using the zipped text file at the end of post #1 (which you unzip, open and leave open) to copy and paste codes/commands into a Ubuntu Terminal window (which is simultaneously opened in another 'desktop').
 
My Ubuntu machine is dead at the moment and I am posting from a Windows machine.
 
Your feedback and comments are most welcomed.
 
Good luck

---

### Post by davidtolo on 2010-02-03
> **b k said:**
> Hi, bearing in mind that I am quite new to Linux and I am not a trained IT person I shall try to see if I can provide you with some help.
 
I do not have first hand knowledge on the 64 bit verson OS but I believe that the Ralink RT3070 driver at the end of #post 1 should be able to work with your usb wireless (probably draft 'N' ) dongle.
 
Assuming you HAVE NOT tried any workarounds from OTHER threads (if you have, try to uninstall your previous attempts):
 
Go to a Terminal window in Ubuntu and type **uname -r **to find out which generic kernel you are running. Pick the relevant PROCEDURE to follow.
 
Go to a Terminal window in Ubuntu and type **lsub **to find out your usb device ID.
The output is something like ID **1737:0077** Linksys.
Use *your* output for STEP 5 to paste in the os/linux/usb_main_dev.c file.
 
If you have partitioned your hard disk *differently* from mine (ie a root, a home, and a swap), you need to modify directory and path in each step to match your own.
 
Open the file Typical Output Screens ............ attached to end of post #1 to have an idea of what to expect for each of the steps before starting.
 
At STEP 5 you need to place *your own info* from **lsub **in place of {USB_DEVICE(0x**1737**,0x**0077**)}, /* **Linksys WUSB54GC** */ 
Follow the format strictly as shown in the os/linux/usb_main_dev.c file.
 
At STEP 6 when you are in the os/linux/config.mk file you probably need to in addition also change a line to do with support for draft N from **n** to **y** (ie no to yes).
 
At STEP 8 you need to input your own info when you are within the RT2870STA.dat file.
 
Other then what I have mentioned above, you should be able to follow the rest of the steps without change (provided your hard disk partitioning scheme is similar to mine).
 
Remember you are basically using the zipped text file at the end of post #1 (which you unzip, open and leave open) to copy and paste codes/commands into a Ubuntu Terminal window (which is simultaneously opened in another 'desktop').
 
My Ubuntu machine is dead at the moment and I am posting from a Windows machine.
 
Your feedback and comments are most welcomed.
 
Good luck


Thank you very much.. I will try .. only prob now is I want to try with the lastes version of the driver that is a little different

---

### Post by davidtolo on 2010-02-05
for step 9.. i get:

root@ubuntuStudio:~/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make && make install
make -C tools
make[1]: Entering directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-9-rt/build SUBDIRS=/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709: error: implicit declaration of function ‘init_MUTEX’
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [LINUX] Error 2
root@ubuntuStudio:~/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#

---

### Post by chili555 on 2010-02-05
Please try these steps in order, no &&, please:```
exit
sudo su
make clean
make
make install
```Any errors?

---

### Post by davidtolo on 2010-02-05
will try shortly.. I am installing open office and I am not sure if they will screw each other up

---

### Post by davidtolo on 2010-02-05
the error kind of looked like it didnt like the fact that this box has only 1 gig of RAM.. I am setting it up as a favor for someone who just got out of prison, so any help is greatly appreciated.. I would like to drive it down tomorrow.

---

### Post by davidtolo on 2010-02-05
make gives this

root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make
make -C tools
make[1]: Entering directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-9-rt/build SUBDIRS=/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709: error: implicit declaration of function ‘init_MUTEX’
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [LINUX] Error 2
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#

---

### Post by b k on 2010-02-05
To **chili555** : 
 
Thank you very much for helping Linux newbies like us. Please continue to assist **davidtolo **as diciphering Linux error codes is way beyond what I know.
 
 
To **davidtolo **:
 
As you have a different kernel from the writeup in post #1 please double check and subsitute your own the following the parts in **bold**:
 
Step 10

Code:
mkdir /lib/modules/**2.6.31-14-generic**/updates
 
 
 Step 11

Code: 
cp -p /lib/modules/**2.6.31-14-generic**/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/**2.6.31-14-generic**/updates/
 
 
Afaik, the error *make: *** [LINUX] Error 2 *refers to no such file or directory.
 
The other errors in your post #43 I do not know.
 
 
**chili555 **or anyone else more knowledgeable please help. Thanks

---

### Post by chili555 on 2010-02-05
Can you confirm, in Synaptic, that you have *build-essential* installed and, if not, please install it? Then please repeat the steps in my previous post.

---

### Post by davidtolo on 2010-02-05
yes.. I have it

[I]root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# 

[/I]I haven't got to the step with the kernell directories yet since the make step is giving me an error I stopped there

---

### Post by chili555 on 2010-02-05
Before we go further, please let me see:```
lsusb
sudo modprobe rt3070sta
iwconfig
```Just a little guesswork here...

---

### Post by davidtolo on 2010-02-05
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# lsusb Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 003: ID 050d:935b Belkin Components  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [EMAIL="root@ubuntuStudio"]root@ubuntuStudio[/EMAIL]:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#  root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# modprobe rt3070sta WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#    root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#

---

### Post by davidtolo on 2010-02-05
That was a little messy.. let me try again:

root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# modprobe rt3070sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#

---

### Post by davidtolo on 2010-02-05
these are all the steps I did so far.. I stped after make because of the error:

Step 1 
 
Code: 
sudo -i 
 
 
 
Step 2 
 
Code: 
cd /home/user/Downloads 
 
 
 
Step 3 
 
Code: 
tar xjf 2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2
 
 
 
Step 4 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
 
 
 
Step 5 
 
Code: 
gedit os/linux/usb_main_dev.c
 
and add the following line 
 
Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
 
Save and close 
 
 
 
Step 6 
 
Code: 
gedit os/linux/config.mk
 
change all the stuff to do with WPA_SUPPLICANT to y 
 
 
Save and close 
 
 
 
Step 7 
 
Code: 
gedit /etc/modules
 
add this line 
 
Code: 
alias ra0 rt3070sta 
 
Save and close
 
 
 
Step 8 
 
Code: 
gedit RT2870STA.dat
 
and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK
 
save and close 
 
 
 
For info : 
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone 
 
 
- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure) 
 
- 2.) set Channel to "0" for auto-select on Infra mode
 
- 3.) set SSID for connecting to your Accss-point 
 
- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE" 
 
- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES" 
 
 
 
 
Step 9 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 
 
Code: 
make

---

### Post by davidtolo on 2010-02-05
do you think this line is the culprit?  WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by davidtolo on 2010-02-05
for step 5 I have:

{USB_DEVICE(050d:935b)}, /* Belking Wireless USB N150 */


which is what my lsusb says

---

### Post by chili555 on 2010-02-05
> **davidtolo said:**
> do you think this line is the culprit?  WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Not at all. You can get rid of this by doing:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by chili555 on 2010-02-05
> **davidtolo said:**
> for step 5 I have:

{USB_DEVICE(050d:935b)}, /* Belking Wireless USB N150 */


which is what my lsusb saysPerfect. So what did 'make' do? Did it error out?

It 'make's for me with warnings but no errors.

---

### Post by davidtolo on 2010-02-05
i get 2 errors:

root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make
make -C tools
make[1]: Entering directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-9-rt/build SUBDIRS=/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709: error: implicit declaration of function ‘init_MUTEX’
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [LINUX] Error 2
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#

---

### Post by chili555 on 2010-02-05
> error: implicit declaration of function ‘init_MUTEX’That's the culprit. I have googled it but see no solution so far.

The exact same file, on my system, makes without error.

I wonder if this is an issue:> /usr/src/linux-headers-2.6.31-9-[COLOR="Red"]rt[/COLOR]What can you tell me? Do you have anything to confess to Dr. Chili??

---

### Post by davidtolo on 2010-02-05
I dont know enough to tell you one way or another.. here is whats in my src folder

root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# ls /usr/src/
linux-headers-2.6.31-17  linux-headers-2.6.31-17-generic  linux-headers-2.6.31-9-rt  linux-rt-headers-2.6.31-9  nvidia-185.18.36  RT2870_LinuxSTA_V2.3.0.0
root@ubuntuStudio:/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# 


do I need to uninstall something?

I tried using an ndis wrapper with that gui tool.. but I removed it

---

### Post by davidtolo on 2010-02-05
do I need to remove RT2870_LinuxSTA_V2.3.0.0 ?

---

### Post by davidtolo on 2010-02-05
can I just delete these?  RT2870_LinuxSTA_V2.3.0.0 linux-headers-2.6.31-9-rt  linux-rt-headers-2.6.31-9

---

### Post by chili555 on 2010-02-05
> RT2870_LinuxSTA_V2.3.0.0Yes, this may be deleted.> linux-headers-2.6.31-9-rt linux-rt-headers-2.6.31-9Please do not remove them yet. Please post:```
uname -r
```What is the purpose of the -rt series? Why were they installed?

---

### Post by davidtolo on 2010-02-06
those are my kernel.. I just updated my kernel.. maybe make will work now

uname -r
2.6.31-9-rt

---

### Post by davidtolo on 2010-02-06
Same thing.. somehow we have to get rid of that Mutex error

root@ubuntuStudio:~/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0# make
make -C tools
make[1]: Entering directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-9-rt/build SUBDIRS=/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709: error: implicit declaration of function ‘init_MUTEX’
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/bdukes/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [LINUX] Error 2
root@ubuntuStudio:~/downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0#

---

### Post by davidtolo on 2010-02-06
apparently mutex means mutual exclusion

[http://en.wikipedia.org/wiki/Mutual_exclusion](http://en.wikipedia.org/wiki/Mutual_exclusion)

Maybe something like this provides a clue?  [http://lwn.net/Articles/353005/](http://lwn.net/Articles/353005/)

that one thing that comes up right before the mutex declaration

/common/rtmp_init.c:3709:

---

### Post by chili555 on 2010-02-06
Now, with your updated kernel, you are erroring out at: /common/rtmp_init.c:3709: 

And guess what line 3709 says:> init_MUTEX(&(pAd->UsbVendorReq_semaphore));Our old buddy MUTEX!!!

May I please see, in an attachment to your reply, your *os/linux/usb_main_dev.c* file? 

Thanks.

---

### Post by janeeps on 2010-02-07
{USB_DEVICE(050d:935b)}, /* Belking Wireless USB N150 */

As far as I can see, your problem lies in the coding. There may have been some mistake regarding where you put that line. I also suggest posting the code here as an attachment and letting **chili555** (or me, if i have the time) to check it out. Missing a single parenthesis or semicolon creates the most intimidating errors. :lolflag:

---

### Post by chili555 on 2010-02-07
> **janeeps said:**
> {USB_DEVICE(050d:935b)}, /* Belking Wireless USB N150 */

As far as I can see, your problem lies in the coding. There may have been some mistake regarding where you put that line. I also suggest posting the code here as an attachment and letting **chili555** (or me, if i have the time) to check it out. Missing a single parenthesis or semicolon creates the most intimidating errors. :lolflag:My suspicion, as well, because of:> init_MUTEX(&(pAd->[COLOR="Red"]UsbVendorReq[/COLOR]_semaphore)); I'm not quite sure exactly what that is telling us, but I'd love to double-check *usb_main_dev.c*.

---

### Post by janeeps on 2010-02-08
Hold on a sec, are you quite sure that your device uses the Ralink RT3070 chipset? I tried searching for that particular device, but got no exact findings, however, these links show some relevant issues:

[http://ubuntuforums.org/showthread.php?t=1216846](http://ubuntuforums.org/showthread.php?t=1216846)
[http://ubuntuforums.org/showthread.php?t=1164538](http://ubuntuforums.org/showthread.php?t=1164538)

These links are for [COLOR="DarkSlateBlue"]{USB_DEVICE(050d:935**a**)}[/COLOR], which is definitely not your device, but somehow looks the same. Have you tried making it work with the RT2870 driver?

---

### Post by chili555 on 2010-02-08
> **janeeps said:**
> Hold on a sec, are you quite sure that your device uses the Ralink RT3070 chipset? I tried searching for that particular device, but got no exact findings, however, these links show some relevant issues:

[http://ubuntuforums.org/showthread.php?t=1216846](http://ubuntuforums.org/showthread.php?t=1216846)
[http://ubuntuforums.org/showthread.php?t=1164538](http://ubuntuforums.org/showthread.php?t=1164538)

These links are for [COLOR="DarkSlateBlue"]{USB_DEVICE(050d:935**a**)}[/COLOR], which is definitely not your device, but somehow looks the same. Have you tried making it work with the RT2870 driver?Do you think it will work?> $ modinfo rt2870sta | grep 050
alias:          usb:v[COLOR="Teal"]050D[/COLOR]p805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Teal"]050D[/COLOR]p815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Teal"]050D[/COLOR]p8053d*dc*dsc*dp*ic*isc*ip*I don't see a 935a or b.

---

### Post by janeeps on 2010-02-08
> **chili555 said:**
> Do you think it will work?I don't see a 935a or b.

I'm not really sure. Since I don't have my ext hd with ubuntu in it all I can really do right now is gather information and toss ideas around. I'm not that experienced as a user either. I guess we'll stick with the RT3070 driver first since that's where we started.

---

### Post by chili555 on 2010-02-08
We're not actually sure it *will* work. That's why we're trying to 'force' it with additions to the usb_main_dev.c file. We will know it works when it works...or doesn't. These Ralink devices pop out like popcorn, so some work is a bit experimental.

We appreciate new ideas! Thanks.

---

### Post by zos13 on 2010-02-21
I registered a user with this forum just to say thanks for the time and effort put into this tutorial. I have had nothing but problems with linux networking for years, and decided to give it another try with an old laptop and this tutorial. It definitely works, and this wifi dongle is one of the best I've used. Now I just need to wade through the pages to see more details on wicd usage and what to do after kernel upgrades, etc.

---

### Post by b k on 2010-02-21
> **zos13 said:**
> I registered a user with this forum just to say thanks for the time and effort put into this tutorial. I have had nothing but problems with linux networking for years, and decided to give it another try with an old laptop and this tutorial. It definitely works, and this wifi dongle is one of the best I've used. Now I just need to wade through the pages to see more details on wicd usage and what to do after kernel upgrades, etc.
 
Hi, thanks for your kind words.
 
Just wanted you to know that there is probably a bug in NetWorkManager that prevents one from connecting to a 'hidden' wireless network.
 
Each time, after you upgrade your kernel, your usb wireless adapter connection will fail. 
Open a Terminal window and type *uname -r *to find out which kernel number you are using at that point and **pick** the correct PROCEDURE to follow (you need the zipped txt file dated 20100117 at the end of post #1). Unzip and open this file and copy and paste the relevant codes like you did the first time.
Stick to NetWorkManager until your wireless connection is up and running again.
 
After that, you should uninstall NetWorkManager first if you want to try Wicd.
Refering to STEP 17, you may have to go into that file again to 'reset' the *set managed=false to true *to **false** if you are trying Wicd - could someone more knowledgeable please advise.
 
At some point in the future you may like to try a more 'permament' solution at this link [COLOR=#008000][https://launchpad.net/bugs/446889](https://launchpad.net/bugs/446889) (post #68 and #69). [/COLOR][COLOR=black]I have however not tried this yet.[/COLOR]
 
It would be most helpful if you could post back here on your change to Wicd once you have attempted it.
 
Good luck

---

### Post by loudnlownoma on 2010-03-15
Thank you so much!  I dunno what I was doing wrong before with other threads or attempts - but did a fresh install tonight and started with this thread and my wireless is working perfectly!  :D

---

### Post by hollowbankai on 2010-04-01
Hey b k ! Thank you very much for your terrible job! I was stucked to install my wusb54gc driver for few days; tryed many ways I've found on web, don't even remeber how many times reInstalled Ubuntu but this one is The One! Thanks a lot!

Just one thing: after updating Ubuntu, when I rebooted PC I got choice to run Ubuntu kernel 2.6....14 and 2.6.....20 when I boot on 14 evrything works perfectly but when I choose the .20 kernel the welcome screen of Ub freezes. Is it harmful in any ways for .14 version that I use?

P.S.: thanks radixor for your solution  (...even if it's didn't worked for me :p)  that inspired these steps :D


Ah I got another question: is there is a way to make some kind of érestore point" like on windows in case if I mess with my Uby to be able to cancel changes and restore system? thanks in advance

---

### Post by b k on 2010-04-01
> **hollowbankai said:**
> 
 
Just one thing: after updating Ubuntu, when I rebooted PC I got choice to run Ubuntu kernel 2.6....14 and 2.6.....20 when I boot on 14 evrything works perfectly but when I choose the .20 kernel the welcome screen of Ub freezes. Is it harmful in any ways for .14 version that I use?
 
Bearing in mind that I am a Ubuntu newbie and assuming that you are in 'recovery mode', the answer is probably no.
 
>  
Ah I got another question: is there is a way to make some kind of érestore point" like on windows in case if I mess with my Uby to be able to cancel changes and restore system? thanks in advance

 
I know that Ubuntu automatically makes 'restore points' of important system changes eg kernel updates but I am not sure if we can maually create one as and when we want like in Windows. See this link for some idea how to go into recovery mode during Ubuntu bootup [http://swiss.ubuntuforums.org/showthread.php?t=1339562](http://swiss.ubuntuforums.org/showthread.php?t=1339562) .
 
Hope the info is of some help to you.
 
Thanks for the compliments of a 'terrible job' :)

---

### Post by hollowbankai on 2010-04-02
Thanks! That's a usefull link :)

---

### Post by spike53 on 2010-04-06
I just wanted to share what I found out with this code. I did a fresh install a few days ago then ran procedure A. Everything worked until Ubuntu installed updates. The 2.6.31-XX folder had changed. All I had to do was run procedure A again but change the "2.6.31-14-generic" (yours may be different) in the code I was entering to the terminal to the updated folder, "2.6.31-20-generic". I ran all of the codes with that change and after I rebooted, my card works again. 
Big thanks to you b k for this post, I would have abandoned Linux altogether if I didn't get any Internet functionality.

---

### Post by spaol on 2010-04-11
thank you, followed procedure A and now i'm posting this using my WUSB54GC v3

thanks a lot man!!!

you :guitar:

---

### Post by rcarreon on 2010-04-11
I am an Ubuntu noob and I was able to get my NIC installed thanks to you.

---

### Post by svkndv on 2010-04-27
Does it work in similar way for ubuntu 10.04?

---

### Post by christ8 on 2010-04-28
This works for me for my Belkin F5D8055 Ver2010.

Thanks to OP for attaching the file (it is gone from Ralink now and replaced with one that does not work), and instructions for the patch.:P

---

### Post by b k on 2010-04-28
> **christ8 said:**
> This works for me for my Belkin F5D8055 Ver2010.
 
Thanks to OP for attaching the file (it is gone from Ralink now and replaced with one that does not work), and instructions for the patch.:P
 
Thank you for sharing the info.
 
For any one who is interested in getting the Belkin F5D8055 v2 to work, you need the Ralink RT3070 driver at the end of post #1 of this thread (the other files may also be useful).
Choose one of the procedures mentioned there but you need to modify STEP 5 as per this link [http://ubuntuforums.org/showthread.php?t=1387483](http://ubuntuforums.org/showthread.php?t=1387483)

---

### Post by b k on 2010-04-28
> **svkndv said:**
> Does it work in similar way for ubuntu 10.04?
 
I have not tried Ubuntu 10.04 yet.
 
For readers who are using Ubuntu 10.04, **svkndv** has mentioned at this link [http://swiss.ubuntuforums.org/showthread.php?t=1464255](http://swiss.ubuntuforums.org/showthread.php?t=1464255) that the Linksys Wusb54gc can work by just blacklisting rt2800usb in the blacklist.conf file
 
Thank you for sharing the info.

---

### Post by mankidavu on 2010-04-29
Just wanted to say a thanks to this thread.

Today I was able to configure a new WUSB54GC V3 card on ubuntu 9.10,after trying all methods.
I'd to freshly install Ubuntu and start from square 1. :) ,as I messed up all config by trying the new drivers from ralink site.

I couldn't make it integrated to the native network manager.
So finally installed wicd([http://wicd.net/](http://wicd.net/)) and everything works perfect.

Now ,need to test this adapter on my wdtv.

---

### Post by mankidavu on 2010-04-29
I think this is one of the main hurdles Linux has to overcome,to grow popular as a user friendly operating system.

The same adapter worked without any issues with the drivers in windows 7 and windows XP.
People expect everything out of the box in today's plu g n play world.

The steps mentioned in this thread and various threads are tedious one for a n00b.I'm sure any n00b learning linux will give up linux, if he has to do these many steps just for configuring a wireless usb adapter.

Also one thing to notice is, even after linux desktop became a popular OS, these companies are not making a good driver. Somehow linux community is not able to put more pressure to get these leading companies release drivers for linux.

Everytime, people make their own work around and there is no collective effort to get this thing fixed up from the horse's mouth.

Unless that happens and common man can just "plug an play" any device, linux desktop idea,will remain to hard core linux people and hobbyists.

---

### Post by mankidavu on 2010-05-15
hmm.
After upgrading to ubuntu 10, the issue is back again.

I can see my wlan0 and it scans and finds the access point also.But not connecting.

iwconfig:
```
aah@aah-desktop:~$ iwconfig wlan0
wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig wlan0
```
aah@aah-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:25:9c:6f:31:59  
          inet6 addr: fe80::225:9cff:fe6f:3159/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24426 (24.4 KB)  TX bytes:65212 (65.2 KB)

```

iwlist wlan0

```
aah@aah-desktop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:08:5C:53:3A:3B
                    Protocol:802.11b/g
                    ESSID:"myessid"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-45 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

If I give a dhclient wlan0, it doesn't get one from my router. :(

Anymore helps?

---

### Post by chili555 on 2010-05-15
> If I give a dhclient wlan0, it doesn't get one from my router.
I doubt it ever will with Network Manager installed. Does NM see your network? Does it try to connect?

---

### Post by mankidavu on 2010-05-15
> **chili555 said:**
> I doubt it ever will with Network Manager installed. Does NM see your network? Does it try to connect?


I've manged to get it working with wicd network manager.
Infact,I was having trouble as earlier I put an alias ra0 in the /etc/modules file and wicd was looking for that.
I changed it to wlan0 in the wicd preferences window and it picked up my wireless network.


Everything working perfect now.
I think ubuntu should prefer it,than NM with its base packaging.

---

### Post by ip3t on 2010-05-18
i've an question:
-i've a 2.6.30.9 linux kernel
-i've the wusb54gc v3
-in many sites it's racommended to install the rt2870sta driver so i've tried to install the rt2870sta 2.3.0.0 version but don't works properly..


do you know why?

ps. : the rt3070 driver works only with 2.6.31.* kernel?

---

### Post by b k on 2010-05-18
> **ip3t said:**
> i've an question:
-i've a 2.6.30.9 linux kernel
-i've the wusb54gc v3
-in many sites it's racommended to install the rt2870sta driver so i've tried to install the rt2870sta 2.3.0.0 version but don't works properly..
 
 
do you know why?
 
ps. : the rt3070 driver works only with 2.6.31.* kernel?
 
 
Hi there, afaik the rt3070 actually contains a less buggy version of the rt2870sta driver when the former was first released.
 
Both the drivers can work for the Linksys wusb54gc v3 once you have applied the correct patches and workarounds to overcome the bugs.
 
Several versions of the rt3070 driver have been released (the one at the end of post #1 is version 2.1.2.0 dtd 20091110) whilst the most current one is version 2.3.0.2 dtd 20100412.
 
According to Ralink, the rt3070 supports linux kernels 2.4 and 2.6 series.
I have attached two text files which are extracted from the latest rt3070 which provide much more details.
 
If your 2.6.31.* kernel is part of Ubuntu 9.10, PROCEDURE A from post #1 (with some modifications for your kernel number at the relevant parts) should work for you.
However it is important to uninstall any other previous failed workarounds and use the files at the end of post #1.
 
Hope the info is of some help to you.

---

### Post by ip3t on 2010-05-21
i'm not a experct ..
how can i do to apply te correct patches and so on?

---

### Post by b k on 2010-05-21
> **ip3t said:**
> i'm not a experct ..
how can i do to apply te correct patches and so on?
 
Hi there, as I am also quite new to Ubuntu may I suggest that you post the output from a Terminal window of the following commands as per [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) (after removing sensitive info like passwords) so that someone here eg chili555 can assists you.
 
My post #1 is primarily for people with a fresh install of Ubuntu 9.10 (who have preferably partitioned their harddisk as per PROCEDURE D.
If you have tried other workarounds and failed and do not know how to undo the failed workarounds, it would probably be faster to do what I suggested earlier on.
 
Hope that this info will get you one step further to solve your problem.

---

### Post by ip3t on 2010-05-22
@ b k :
the file called "README_STA_usb_Ralink_RT3070 v2_3_0_2 dtd 20100412" you've attached it referred to the 2870sta driver...evenif the title include the word "..rt3070 v2_3_0_2.."
why?

the guide considers the Ralink Hardware: Ralink 802.11n Wireless LAN Card;
but i've a model taht support only b/g ! (wusb54gcv3)

---

### Post by b k on 2010-05-22
> **ip3t said:**
> @ b k :
the file called "README_STA_usb_Ralink_RT3070 v2_3_0_2 dtd 20100412" you've attached it referred to the 2870sta driver...evenif the title include the word "..rt3070 v2_3_0_2.."
why?

the guide considers the Ralink Hardware: Ralink 802.11n Wireless LAN Card;
but i've a model taht support only b/g ! (wusb54gcv3)

Probably only the people at Ralink can answer the first part of your query.
If you poke around within the RT3070 drivers (just double click to decompress and explore the individual files within by right clicking and opening the selected file of interest with a basic text editor eg gedit).
You will find that at the core of the RT3070 drivers is the rt2870 drivers.

As long as your wireless adapter uses the same (I presume rt2870 chipset), the Ralink RT3070 drivers can work (but you have to tweak the parameters within the driver to suit the capability of your wireless b, g or n adapter).

For ***Ubuntu 9.1****0*** see post #18 of this link [http://ubuntuforums.org/showthread.php?t=1372323&page=2](http://ubuntuforums.org/showthread.php?t=1372323&page=2) if you are wanting to use the Ralink_RT3070 v2_3_0_2 dtd 20100412 ,
For step c) of that post the code probably needs to be changed to some thing like :

{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */

to suit the linksys wusb54gc v3 adapter,

For*** Ubuntu 10.04 LTS*** you may be interested in posts #2 and #3 of this link [http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883) to get your adapter to work.

See this link if you are interested in people who are trying to provide a permanent solution [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

Good luck

---

### Post by pobri19 on 2010-05-23
Hi guys, I just wanted to let you know this works with Ubuntu 10.4 Desktop on a 64 bit platform for the F5D8055 V2. I followed procedure C1, but used the following replacement for step 5: [http://www.backports.ubuntuforums.org/showthread.php?p=8704426#post8704426](http://www.backports.ubuntuforums.org/showthread.php?p=8704426#post8704426)

Which states what code to use in the .c file for a F5D8055 V2. I also changed the directories in the steps for the kernel version I'm using. I'm using: 2.6.32-21-generic

Perhaps you could update your thread to indicate this as there are a lot of people looking for a solution for this model and Ubuntu release.

---

### Post by ip3t on 2010-05-23
as i wrote in [this]("http://ubuntuforums.org/showthread.php?p=9346218#post9346218") post it doesn't works :(
is there another way to do the work?'

---

### Post by b k on 2010-05-23
> **ip3t said:**
> as i wrote in [this]("http://ubuntuforums.org/showthread.php?p=9346218#post9346218") post it doesn't works :(
is there another way to do the work?'
 
You are trying to get the linksys wusb54gc v3 wireless adapter to work in your link [http://ubuntuforums.org/showthread.php?p=9346218#post9346218](http://ubuntuforums.org/showthread.php?p=9346218#post9346218) for [COLOR=red][COLOR=black]Ubuntu[/COLOR] 10.04LTS[/COLOR] I presume and chili555 is helping you out there - trust me, you are in very good hands.
 
Post #1 of this thread is for people trying to get the same adapter to work for Ubuntu [COLOR=blue]9.10 [/COLOR][COLOR=black](it works if you read the pre-requisites carefully - I tried each and every one of those steps before posting :)).[/COLOR]
 
If you have tried something from post #1 of this thread and was unsuccessful, please provide some details here and I will try to help if I can.
 
Thanks
 
 
[COLOR=#0000ff][/COLOR]

---

### Post by b k on 2010-05-23
> **pobri19 said:**
> Hi guys, I just wanted to let you know this works with Ubuntu 10.4 Desktop on a 64 bit platform for the F5D8055 V2. I followed procedure C1, but used the following replacement for step 5: [http://www.backports.ubuntuforums.org/showthread.php?p=8704426#post8704426](http://www.backports.ubuntuforums.org/showthread.php?p=8704426#post8704426)
 
Which states what code to use in the .c file for a F5D8055 V2. I also changed the directories in the steps for the kernel version I'm using. I'm using: 2.6.32-21-generic
 
Perhaps you could update your thread to indicate this as there are a lot of people looking for a solution for this model and Ubuntu release.
 
Hi there, may I suggest that you document your successful attempt to get the F5D8055 V2.1 for Ubuntu 10.4 Desktop on a 64 bit platform (ie with the necessary steps and terminal codes/commands etc) in a ***text file*** and post it under a ***new*** thread (attaching any other necessary files & drivers).
 
The idea is for people needing help to download these files to a usb dongle, take the dongle to the machine without the wireless connection, open the text file and copy & paste the codes/commands into a Teriminal before execution.
 
Readers of the new thread will find it more credible if it is written my someone who has actually 'done it' if you know what I mean.
 
Thanks for posting

---

### Post by ip3t on 2010-05-24
@ b k : thanks !

---

### Post by b k on 2010-05-24
This post applies to people using ***Ubuntu 10.04 LTS***

For*** Ubuntu 10.04 LTS***  you may be interested in posts #2 and  #3 of this link [http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883)  to get your adapter to work.

If you are unable to auto connect at bootup or need to re-enter your wireless passwork every time you need to get on the internet (see post #10 of the above link for symptoms) and end of post #3 of the same link for the solution.

Thanks to mawil1013 at [http://ubuntuforums.org/showthread.php?t=1491965](http://ubuntuforums.org/showthread.php?t=1491965) for the tip.

---

### Post by ip3t on 2010-05-25
i'm not unable to install the other drivers.. 
but i've read many where the driver's issue is causes by 2.6.32.* kernel (ubuntu 10.04 LTS)..
do you suggest me to install 9.10 oe 9.04?

---

### Post by b k on 2010-05-25
> **ip3t said:**
> i'm not unable to install the other drivers.. 
but i've read many where the driver's issue is causes by 2.6.32.* kernel (ubuntu 10.04 LTS)..
do you suggest me to install 9.10 oe 9.04?
 
No kernel is perfect.
 
There are [COLOR=red]several[/COLOR] versions of the Linksys wusb54gc wireless adapters and each use a [COLOR=red]different[/COLOR] driver.
 
Getting  the wusb54gc [COLOR=black]v3[/COLOR] to work on Ubuntu 10.04 LTS is a piece of cake compared to Ubuntu 9.10 - see posts #2 and #3 of this link [http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883)
Connection to 'hidden' networks (at least on mine with WPA2-PSK with AES encryption) appears to work almost flawlessly so far.
 
You should first check the device ID of your wireless adapter (to properly identify your device) as advised by chili555 to solve your issues and try to stick to that thread unless chili555 gives up on you :)
 
Good luck

---

### Post by theluddite on 2010-05-29
Great instructions!  This thread has helped me a lot.  I've used the OP to successfully use my WUSB54gc on two different systems.  I'm now trying to use it with Virtualbox so that my Ubuntu guest can have its own dedicated IP, instead of having to port forward from the guest to the host.

When I first followed the instructions, everything worked perfectly.  The driver compiled fine, and when I rebooted the guest OS, I was able to connect to my wireless network on the first try.  I eventually had to restart my whole system and now the guest OS can't scan using the interface.  'ifconfig' and 'iwconfig' both list the ra0 device but when I do 'iwlist ra0 scan', I always get 'ra0     No scan results'.  One point that bears mention is that the guest kernel is 2.6.30.9.  Why would the driver work fine after being first compiled, but not be able to scan after my system was restarted?

---

### Post by Tonyr63 on 2010-07-21
Hi
 
I have been trying for several days to get this device to work and it appears completely dead unless I connect it to a Windows machine.  I though UDEV was designed to instantly recognise a USB device on connection however how can it be so hard to get it work.  What is all the crap I read in the architecture about HAL and plug and play?
 
I have a disk with a Linux folder but no install program so how do you install.
 
I have followed all the instructions using MAKE and MAKE INSTALL and I get NO Wireless Extensions.  Not a single flicker from the device and no response from the PC when it is inserted or disconnected.
 
How can 10.04 be so broken to not plug and play or at least have some usable mechanism to install drivers.
 
This is mind numbing and so frustrating becasue a USB wireless device is a standard piece of hardware in 2010.
 
To make matter worse is that the PC was originally installed from a blank HD with 10.04 with an internal PCI Netgear WG311v3 which Ubuntu did not detect on setup and I could not get working in any maner.  A completely clean install of UBUNTU and no wireless connectivity.
 
So I reverted to the much more recent RT3070 and still 4 days of frustration.
 
Does Ubuntu support wireless devices and what does SUPPORT mean in this environment?  Days and days of command line cryptic commands?
 
You really want to support the project but you keep getting kicked in the head but such poor design.  I also discovered the burning solution is also broken in this version so where has the release testing gone?

---

### Post by drewciferpike on 2010-10-13
Follow the scent of freshly connected wifi adapter if your WUSB54GC v.3 isn't connecting (at least with 10.4..., October of 2010...)... like post #102 said: I went to that thread, and the simple blacklist instructions had me good to go.

---

### Post by eychin on 2011-12-06
Originally my dongle worked and then it didn't in Lucid.  Spent a lot of time following various strategies to make my wusb54gc v3 dongle to work after it stopped working in Lucid 10.04 - nothing worked.  it was easier to reinstall lucid while the dongle was inserted (don't know if this was necessary, but it was insurance).  The light finally lit up on the dongle and all i had to do was blacklist rt2800usb to make it work.  This was also the only thing i had to do on my other 10.04 laptop installation.  I noticed others blacklist different modules - like the mentioned rt2870STA module - so just be aware. Save time and frustration, and reinstall.

---

