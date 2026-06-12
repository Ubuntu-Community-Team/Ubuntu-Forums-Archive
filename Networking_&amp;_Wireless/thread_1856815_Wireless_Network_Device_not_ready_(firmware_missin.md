---
title: "Wireless Network Device not ready (firmware missing) Ubuntu 11.04 Dell Inspiron 11z"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by godrama on 2011-10-09
Hi,

I Installed Ubuntu 11.04 32-bit on my Laptop Dell Inspiron 11z 1110.

It got installed, but the Wireless doesn't work.

At the time of installation, it threw an error:

"Wireless Network Device not ready (firmware missing)"

Please let me know what I have to do for getting the Wireless working on my computer.

Screenshot of the error massage is attached to this post.

Thanks for your time,
Rama

---

### Post by binary00mind on 2011-10-09
What kind of wireless card is on your computer. 

Also do you have any access to internet from your newly installed Ubuntu (like by cable)

---

### Post by godrama on 2011-10-09
> **binary00mind said:**
> What kind of wireless card is on your computer. 

Also do you have any access to internet from your newly installed Ubuntu (like by cable)


At the following link:  [http://www.dell.com/us/p/inspiron-11z/pd](http://www.dell.com/us/p/inspiron-11z/pd) 

The Vendor website of my Laptop says that it is a

Wireless

    * Wi-Fi

      Dell 1397 WLAN 802.11a/b/g - Half mini-card
      Dell 1520 WLAN 802.11a/b/g/Draft-n - Mini-card

Is this the information that you were looking for, regarding my wireless network hardware component?
If it isn''t, then please let me know how to fetch the information through a command at the terminal.

Presently I do not have access to a Wired Internet Connection but I could get on to it if it is essential.

I did the Installation by copying the ubuntu .iso image to USB and eventually by booting through the USB PenDrive.

I did not install Ubuntu with a wired connection to the Internet, Would it have installed or updated the firmware or wireless drivers from the Internet at the time of installation had  there been a working wired Internet connection? If that is the case I will try reinstalling Ubuntu with a working wired Internet connection.

Please let me know how to proceed further.


Thank you for helping me.

---

### Post by binary00mind on 2011-10-09
I'm kinda behind with the Wi-Fi revolution since everything is working on my computers. 

The trick that I will offer to you is as follows (last time I used myself 3 years ago)
You will need internet access for 5-30 minutes.

When you have internet working,  
open the terminal and type this command
```
 sudo apt-get install ndisgtk 
``` 

You can do this all without terminal by going to Ubuntu software Center and search for 
"Windows wireless Drivers" 

Then go to your computer vendor support page with drivers downloads. Download the one that applies to you. 
if it is executable file, extract to folder using for example 7zip...
Not every archive manager is capable of extracting *.exe files. 

Then use this new Linux app "Windows Wireless Drivers" 
Click new (or add cannot remember now) and navigate to Win folder with your downloaded Windows Wi-Fi driver. 

Click on .inf file and as soon you do this you will get a pop up window if the device is present or not, of course we hope that it is so just save and that is it. 

I don't know if you have x64 or x32 bit version of Ubuntu. 
Choose what applies to you.

---

### Post by godrama on 2011-10-09
> **binary00mind said:**
> I'm kinda behind with the Wi-Fi revolution since everything is working on my computers. 

The trick that I will offer to you is as follows (last time I used myself 3 years ago)
You will need internet access for 5-30 minutes.

When you have internet working,  
open the terminal and type this command
```
 sudo apt-get install ndisgtk 
```You can do this all without terminal by going to Ubuntu software Center and search for 
"Windows wireless Drivers" 

Then go to your computer vendor support page with drivers downloads. Download the one that applies to you. 
if it is executable file, extract to folder using for example 7zip...
Not every archive manager is capable of extracting *.exe files. 

Then use this new Linux app "Windows Wireless Drivers" 
Click new (or add cannot remember now) and navigate to Win folder with your downloaded Windows Wi-Fi driver. 

Click on .inf file and as soon you do this you will get a pop up window if the device is present or not, of course we hope that it is so just save and that is it. 

I don't know if you have x64 or x32 bit version of Ubuntu. 
Choose what applies to you.


I tried it but, doesn't help, nothing works.
Yes I have x32 bit version of Ubuntu.

---

### Post by pdc on 2011-10-09
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by wildmanne39 on 2011-10-09
Hi, welcome to the forum! please copy and paste these commands in the terminal by hitting ctrl+alt+t then paste the results here :
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by godrama on 2011-10-10
Thank you all for helping me, I appreciate you spending time.

I finally got it resolved.

I Re-Installed Ubuntu on my Laptop with a working cable Internet connection, Looks like Ubuntu downloaded the required Updates / Firmware that is required for the wireless hardware component from the Internet at the time of Installation.

Thank you all once again.:P

---

