---
title: "Internet Connection Problem in Ubuntu 9.04 Desktop Edition"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by nilanjangm on 2009-07-19
I have installed Ubuntu 9.04 Desktop Edition. While trying to connect to the internet using all the forum topics information from Ubuntu Forums, I could not find the "NetworkManager" icon in the system tray (system notification area). I tried to add it, however, to my surprise, it was not in the list of items to be added to the panel. :(
 
I have not added more details here as I do not know what is actually required to solve this problem. Please tell me what information to provide to solve this one.
 
I am using a USB wireless device.
 
Looking forward to you all. :D

---

### Post by DaVinci.033 on 2009-07-19
My suggestion would be to get rid of network manager. I did and installed Wicd from the synaptic package manager and havent had any wireless problems since, i manage to get a usb WG54GC to work and also my pci netgear WG311V3. Just navigate to System : Administration : Synaptic Package Manager.

---

### Post by nilanjangm on 2009-07-19
Well, I had navigated to the > Synaptic Package Manager and found that the wireless driver is installed properly ([SIZE=1]wireless-tools version: 29-1.1ubuntu2[/SIZE]). However, I don't know what to do next. Look guys, I am novice in configuration Ubuntu, therefore, you need to guide me :).
 
What I found by running ```
lsusb
``` before and after inserting the USB internet device is given below.
 
Before:
 
[SIZE=1]Bus 001 Device 002: ID 064e:a101 Suyin Corp. [/SIZE]
[SIZE=1]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE]
[SIZE=1]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/SIZE]
[SIZE=1]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/SIZE]
[SIZE=1]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/SIZE]
[SIZE=1]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]After:[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Bus 001 Device 002: ID 064e:a101 Suyin Corp.[/SIZE][SIZE=1] [/SIZE]
[SIZE=1]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][SIZE=1] [/SIZE]
[SIZE=1]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][SIZE=1] [/SIZE]
[SIZE=1]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][SIZE=1] [/SIZE]
[SIZE=1][COLOR=red]Bus 003 Device 003: ID 19d2:fffe[/COLOR][/SIZE][SIZE=1] [/SIZE]
[SIZE=1]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
[SIZE=1]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Don't know whether this throws any light on the problem.[/SIZE]

---

### Post by nilanjangm on 2009-07-20
[COLOR=black][FONT=Verdana]Well, I tried connecting my wireless device from the command line. What I did was mentioned below.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Before inserting USB Internet device.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
lsusb
```[/FONT][/COLOR]>  and the output was
[COLOR=black][FONT=Verdana]Bus 001 Device 002: ID 064e:a101 Suyin Corp. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]

 
[COLOR=black][FONT=Verdana]After inserting USB Internet device.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
lsusb
```[/FONT][/COLOR]>  and the output was
[COLOR=black][FONT=Verdana]Bus 001 Device 002: ID 064e:a101 Suyin Corp. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=red][FONT=Verdana]Bus 003 Device 003: ID 19d2:fffe[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]

 
[COLOR=black][FONT=Verdana]What I concluded that 19d2:fffe is the wireless USB device. So I executed the following.[/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]```
sudo iwlist 19d2:fffe scan
```[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The expected output was not displayed, in stead, the following result was displayed.[/FONT][/COLOR]
> 19d2:fffe Interface doesn't support scanning.
[COLOR=black][FONT=Verdana]Now, what to do?!! I have no clue :confused:.[/FONT][/COLOR]

---

