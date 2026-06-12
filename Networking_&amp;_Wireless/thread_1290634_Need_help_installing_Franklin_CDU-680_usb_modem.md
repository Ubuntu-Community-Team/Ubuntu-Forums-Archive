---
title: "Need help installing Franklin CDU-680 usb modem"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by AKDriller on 2009-10-13
I am very new to Ubuntu and I currently have 9.04 installed. I have been using windows all my life so this is all pretty new to me. I have a great understanding of the Windows O/S and feel quite confident on most everything but I want to switch over. I know this will at first be a slow a learning curve but the thing I need to do first is get my internet working which is this USB modem.
 
I will try to give you as much info as I can but if I am missing something please let me know.
 
This is the info inside the text file that gives instructions on how to install
 
Copy the Linux Folder from your device to your Desktop
Open terminal 
Run "cd Desktop/Linux"
Run "sudo ./connect"
Enter root password
Device will switch to modem mode and attempt to connect. 
Press Ctrl-C twice to disconnnect
FOR SIP/MIP Preferr(QCMIP=0 or 1) Carriers
SIP carrier case, you may need to modify following part at ¡°execute.sh¡± file.
Please replace Username and Password with your Service providers (SIP User ID and Password) 
"Phone = #777\nUsername = broadband\nPassword = broadband" >> cdu680config
Username= broadband -> see followings
Password= broadband -> see followings
ACS Alaska
Security (Simple IP, 1xEVDO) 
Login(User Name or Account Name): [EMAIL="MDN@acsalaska.net"]MDN@acsalaska.net[/EMAIL] (MDN: 10 digit Phone Mumber)
Password: MDN (MDN: 10 digit Phone Mumber)
 
after I run "sudo ./connect" in terminal it says 
 
"680d interface changer-1.0.1
Segmentation fault"
 
I believe there will be a few problems along the way but I am willing to put some time into this if needed. I have done alot of reading on this but none of which led me to the solution.
 
Whatever questions, solutions, or suggestions you may have please put in "newby" language because like I said this is WAY different from what I am used to.
 
Thanks for any help you have to offer

---

### Post by 2TallSwede on 2009-10-25
AKDriller, I assume based on the mention of ACS Alaska that you're using the units sold by ACS. If so, the instructions included with the card won't really help you a whole lot. I'm not sure what the segmentation fault really means and I haven't been able to get Franklin to tell me either. I think I read at some point that the included instructions are for an old Ubuntu version. It hasn't worked for me since 8.04.

The first part about copying the Linux folder to the desktop is the only part that is relevant. From there you need to do the following after you plug in the modem.

1. Open up terminal
2. Type in 'dmesg'
3. Find the device listed by the CMOTECH device entry. You should have a listing along the lines of [sdb] or something like that. 
3. Go to 'Desktop/Linux' as described in included instructions.
4. Execute the following: 'sudo ./itfchg /dev/sdb' - please substitute sdb for whatever it is on your particular system. Running that command will change the mode of the 680 and activate the modem. Within about 15 seconds or so, you should now see a new entry for the modem called something along the lines of "CDMA Modem". Simply click Connect and you'll be connected within seconds.

I have the same unit and I've been doing this for the last year. It can be automated using a few scripts so you don't have to type this stuff in every time but either way, it doesn't take that long. You'll only need steps 3 and 4 once you figure out what your device is.

One other note: I've used this most recently on 9.04 32-bit. On installing 9.10 64-bit it didn't work. I had to follow the instructions here for that to work: [http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10](http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10)

Anyway, that's a different issue...

Hope that helps.

---

### Post by 2TallSwede on 2009-11-18
Clarification: it used to work on 9.10RC but with 9.10 final, this method no longer seems to work. As of right now, I have to do this:

Found this solution over in another thread ([http://ubuntuforums.org/showthread.php?t=1304745&highlight=wireless+broadband+karmic](http://ubuntuforums.org/showthread.php?t=1304745&highlight=wireless+broadband+karmic))

Type this into terminal:

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x16d8 product=0x6803

It should now appear in your connections manager.

---

