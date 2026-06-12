---
title: "Belkin F6D4050 v1"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by satyanash on 2010-06-14
i have this Wireless USB adapter from Belkin 

Belkin F6D4050 v1

and i need to use it to connect to a wireless network when i plug it in, ubuntu does not recognize it and does nothing how to get it to work

---

### Post by b k on 2010-06-14
> **sattu94@gmail.com said:**
> i have this Wireless USB adapter from Belkin 
 
Belkin F6D4050 v1
 
and i need to use it to connect to a wireless network when i plug it in, ubuntu does not recognize it and does nothing how to get it to work
 
Hi there, I am no expert and what I am going to suggest to you is info I have read on this forum - amended slightly to suit your wireless adapter.
 
Try at your own risk !!!
 
It is strongly recommended that you copy the code that needs to be executed (from a Terminal window) below to a .txt file to your Ubuntu machine via a usb dongle to miminise human typo errors.
Open this .txt file and copy and paste the code into the Terminal window of the Ubuntu machine (with the wireless adapter problem).
 
Go to :
*Applications, Accessories, Terminal*
 
```
lsusb
```
 
Check the output to make sure that your device ID is:
 
> 050d:935a
 
If it matches, do this:
 
```

sudo gedit /etc/udev/rules.d/network_drivers.rules

```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta"
```
 
Proofread carefully(ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=red]save[/COLOR] and close gedit.
 
Next do this:
 
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id
```
 
Proofread carefully(ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
Reboot
 
Good luck and let us know if it works.
 
PS: most of the above info is modified from this link posts #32 and #58 [http://ubuntuforums.org/showthread.php?t=1419504&page=6](http://ubuntuforums.org/showthread.php?t=1419504&page=6)
 
**_Update: _**
The above procedure works - see post #6

---

### Post by satyanash on 2010-06-15
Am I supposed to do all of this with the USB adapter plugged in ? Or plug it in later, after everything has been done?

And thanks for the reply..

---

### Post by b k on 2010-06-15
> **sattu94@gmail.com said:**
> Am I supposed to do all of this with the USB adapter plugged in ? Or plug it in later, after everything has been done?
 
And thanks for the reply..
 
Hi, try plugging in later after everything has been done.
 
If unsuccessful, leave the wireless adapter in and reboot again.
 
Worst case scenario, you can 'undo' the process by executing the code again and removing the lines that you have added into the two files ie *network_drivers.rules* and 
 *network_drivers.conf *
 
Good luck and post back.

---

### Post by satyanash on 2010-06-15
lsusb:> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



With the Adapter not plugged in.




And with it plugged in :
> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:935a Belkin Components 
Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by satyanash on 2010-06-15
So, yea i plugged the adapter in, and then did lsusb and it can see that it is a Belkin Component. Then without removing the Adapter i followed the two following ways to put the lines in the folders. While doing so, i noticed that those files didn't already exist. When i was done with that i just rebooted my machine and Voila it worked although i had to put in the WPA key but after that everything went superb and now i am replying through that very network..

Thanks a lot and a lot and a lot.. :guitar: ):P

---

### Post by b k on 2010-06-15
Hi there am wondering if your output of lsusb :
 
Bus 001 Device 004: ID 050d:935a Belkin Components 
 
was obtained before or after you executed the code lines.
 
Please also post the output of *lsmod *if you still cannot connect to wireless network.
 
Thanks
 
Update: ignore above. Congratulations.

---

### Post by satyanash on 2010-06-15
well the output of the Belkin Component was obtained before putting the commands in the files.. and as you can see in my earlier post i can connect to the network..thnx again :KS

---

### Post by satyanash on 2010-06-15
sorry i forgot to ignore the above... :-)

---

### Post by b k on 2010-06-15
> **sattu94@gmail.com said:**
> i have this Wireless USB adapter from Belkin 
 
Belkin F6D4050 v1
 
and i need to use it to connect to a wireless network [COLOR=red]when i plug it in, ubuntu does not recognize it[/COLOR] and does nothing how to get it to work
 
As I do not own the wireless adapter that you have and for the benefit of readers, could you explain what you meant in red above.
 
 
 
If your wireless adapter was recognised by *lsusb* [COLOR=red]be[/COLOR][COLOR=red]fore[/COLOR] executing the two code lines*,* the procedure in post #2 [COLOR=red]may not be necessary[/COLOR].
 
A simpler way [COLOR=red]could be[/COLOR]:
 
Go to : *Applications > Accessories > Terminal*
 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
 
The text editor gedit will open the file blacklist.conf
Add the following line to the end ot the opened file.
 
 
```
blacklist rt2800usb
```
 
Proofread carefully. [COLOR=red]Save[/COLOR] and close gedit.
 
Reboot.
 
Thanks
 
**_UPDATE:_**
The above simpler method does not work - based on feedback (see post #12)

---

### Post by satyanash on 2010-06-15
By > "does not recognize" i meant that it does not give any visual indication of anything being attached to the computer..yea probably according to lsusb it was recognized..but it did not inform the user..anyway this is linux and not windows..and thats the way it works i guess..silent

---

### Post by satyanash on 2010-06-15
Okay,
like you mentioned in post #10 i removed all the things i had done like mentioned in post #2 , and followed the post #10 method and rebooted. and plugged it in.. i was not able to connect as i had no option in the notification area.. then i did lsusb which seemed to recognize my Belkin Component.. then i decided to stick to the method in post #2 and made all those files again, but this time with the adapter plugged out..and rebooted..now when i checked the notification area there was still no option of wireless network.. now i plugged in the adapter then automatically the the option appeared.. and i was able to connect..

In Short Method in Post #2 worked [COLOR="Red"]for me[/COLOR] while the one in post #10 did not..

Satyajeet

---

### Post by b k on 2010-06-15
> **sattu94@gmail.com said:**
> Okay,
like you mentioned in post #10 i removed all the things i had done like mentioned in post #2 , and followed the post #10 method and rebooted. and plugged it in.. i was not able to connect as i had no option in the notification area.. then i did lsusb which seemed to recognize my Belkin Component.. then i decided to stick to the method in post #2 and made all those files again, but this time with the adapter plugged out..and rebooted..now when i checked the notification area there was still no option of wireless network.. now i plugged in the adapter then automatically the the option appeared.. and i was able to connect..
 
In Short Method in Post #2 worked for me while the one in post #10 did not..
 
Satyajeet
 
OK thanks - will amend post #2 and #10 to reflect your feedback so other future readers will not be confused.

---

### Post by Armadillo Kilr on 2010-06-24
@b k: what would i have to amend on the gedit for a Belkin F7D2101 surf n share usb adapter? the network is showing. it is not connecting though. 

Bus 001 Device 004: ID 050d:845a Belkin Components

---

### Post by kaboodle_fish on 2010-06-26
Thanks. This worked for me as well. Just to add you need to have WPA security set to AES only as well.

---

### Post by jezzabart on 2010-07-13
Thank you to everyone for your help.  I don't pretend to understand it but I am now connected using the method in Posts 2 and 15.  

Sadly, this means that my PDA cannot connect as it requires WPA-TKIP.  Is there any way that I can leave the router set to WPA-TKIP and WPA2-AES which is what I was using before and works for Windows XP and my Windows Mobile 6.1 PDA?

---

### Post by b k on 2010-07-14
> **jezzabart said:**
> Thank you to everyone for your help. I don't pretend to understand it but I am now connected using the method in Posts 2 and 15. 
 
Sadly, this means that my PDA cannot connect as it requires WPA-TKIP. Is there any way that I can leave the router set to WPA-TKIP and WPA2-AES which is what I was using before and works for Windows XP and my Windows Mobile 6.1 PDA?
 
If you need to use TKIP encryption, try setting your router to 'broadcast' your wireless network name - I am assuming that your wireless network name is currently 'hidden'.
 
In terms of security, I believe it does not make much of a difference between a 'visible' or 'hidden' network to a determined cracker.
 
Hope the info is helpful.

---

### Post by jezzabart on 2010-07-14
> **b k said:**
> If you need to use TKIP encryption, try setting your router to 'broadcast' your wireless network name - I am assuming that your wireless network name is currently 'hidden'.
 
In terms of security, I believe it does not make much of a difference between a 'visible' or 'hidden' network to a determined cracker.
 
Hope the info is helpful.

Thank you for the suggestion, sadly my router has always been set to broadcast the network name (SSID), so that is not the answer.  

As far as I understand it, WPA-TKIP is the interim version of WPA which is less secure than the final WPA2-AES, but does work with older wireless cards.  Initially, my router was set to use either WPA-TKIP or WPA2-AES, depending on the capability of the wireless card connecting to it.  This meant my PC (running XP) connected with WPA2-AES and my PDA with WPA-TKIP.  However, to get my PC to connect when running Ubuntu 10.04, I had to switch off the router option to offer WPA-TKIP as instructed in Post 15.

So what I need is a way to get Ubuntu to connect with WPA2-AES without being distracted (technical term!) by the simultaneous availability of the WPA-TKIP option from the router.

---

### Post by satyanash on 2010-07-28
> **jezzabart said:**
> Thank you for the suggestion, sadly my router has always been set to broadcast the network name (SSID), so that is not the answer.  

As far as I understand it, WPA-TKIP is the interim version of WPA which is less secure than the final WPA2-AES, but does work with older wireless cards.  Initially, my router was set to use either WPA-TKIP or WPA2-AES, depending on the capability of the wireless card connecting to it.  This meant my PC (running XP) connected with WPA2-AES and my PDA with WPA-TKIP.  However, to get my PC to connect when running Ubuntu 10.04, I had to switch off the router option to offer WPA-TKIP as instructed in Post 15.

So what I need is a way to get Ubuntu to connect with WPA2-AES without being distracted (technical term!) by the simultaneous availability of the WPA-TKIP option from the router.
i think you should start a new post for this problem, since this this thread has has been marked solved.

---

### Post by trusktr on 2010-07-28
Thank you, i'm in Arch Linux and post #2 solved my problem!

---

### Post by All.coholic on 2010-08-15
> **sattu94@gmail.com said:**
> So, yea i plugged the adapter in, and then did lsusb and it can see that it is a Belkin Component. Then without removing the Adapter i followed the two following ways to put the lines in the folders. While doing so, i noticed that those files didn't already exist. When i was done with that i just rebooted my machine and Voila it worked although i had to put in the WPA key but after that everything went superb and now i am replying through that very network..

Thanks a lot and a lot and a lot.. :guitar: ):P
  Just One question for you, what would help me a lot. How did you managed to get WPA key?

---

### Post by satyanash on 2010-08-15
> **All.coholic said:**
> Just One question for you, what would help me a lot. How did you managed to get WPA key?

well i already had the network configured and knew the WPA key..

---

### Post by Oxwivi on 2010-08-24
I was able to use the method mentioned on post two without restarting. Restarting the Network Manager (nm-applet) did the trick.

Currently, I use these two commands to restart the Network Manager:

```
killall nm-applet
nm-applet
```If you want to make a network available to all users, add sudo in the second command.

b k, edit and add this to your post if you will. And will work even if the USB is plugged in - I've reformatted quite a few times and used your solution while the USB was plugged in.

---

### Post by philipgm on 2010-10-05
Thanks for this - works in Maverick too - Post 2 that is.

---

### Post by CommuneOfLoon on 2010-10-14
> **b k said:**
> Hi there, I am no expert and what I am going to suggest to you is info I have read on this forum - amended slightly to suit your wireless adapter.
 
Try at your own risk !!!
 
It is strongly recommended that you copy the code that needs to be executed (from a Terminal window) below to a .txt file to your Ubuntu machine via a usb dongle to miminise human typo errors.
Open this .txt file and copy and paste the code into the Terminal window of the Ubuntu machine (with the wireless adapter problem).
 
Go to :
*Applications, Accessories, Terminal*
 
```
lsusb
```
 
Check the output to make sure that your device ID is:
 

 
If it matches, do this:
 
```

sudo gedit /etc/udev/rules.d/network_drivers.rules

```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta"
```
 
Proofread carefully(ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=red]save[/COLOR] and close gedit.
 
Next do this:
 
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id
```
 
Proofread carefully(ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
Reboot
 
Good luck and let us know if it works.
 
PS: most of the above info is modified from this link posts #32 and #58 [http://ubuntuforums.org/showthread.php?t=1419504&page=6](http://ubuntuforums.org/showthread.php?t=1419504&page=6)
 
**_Update: _**
The above procedure works - see post #6


Hi, I'm having this same issue with a Dell Dimension 5100 I just install Ubuntu on. I'm using the same model Belkin but v2, and the output of lsusb is 050d:935b instead of 050d:935a. As long as I appropriately modify the above commands, will this work for me? Thanks.

EDIT: Nevermind, I just tried it and it worked beautifully! Thank you! 

FYI I did enter 935b instead of a because that was the output I got. Cheers.

---

### Post by teeron on 2010-10-30
Hi

I did what [CommuneOfLoon]("http://ubuntuforums.org/member.php?u=1161883") wrote and its almost fine.  Almost.

After reset, network manager detect my network but every few minuts is keep asking me about authorisation key. Im using wpa/wpa2 personal  authentycation type and im sure i have put correct key.

Pls help.

---

### Post by teeron on 2010-10-31
> **teeron said:**
> Hi

I did what [CommuneOfLoon]("http://ubuntuforums.org/member.php?u=1161883") wrote and its almost fine.  Almost.

After reset, network manager detect my network but every few minuts is keep asking me about authorisation key. Im using wpa/wpa2 personal  authentycation type and im sure i have put correct key.

Pls help.


.

---

### Post by rubberduck1968 on 2010-11-29
Just to add, followed instructions as posted by BK and connection worked first time!

Many thanks.

---

### Post by mfrost on 2010-12-07
i have this same usb adapter. i followed the steps here and managed to get the lights to show up on the adapter and the indicator on the top of the screen animates when i sellect connect to hidden network and then try my router. but no connection. also it does not see any broadcasting routerrs in range at all. so i think there is still a failure in the running of the ralink driver rt2870sta. how can we diagnose this and fix?

did the download of ralink driver
expanded the archive.
blacklisted rt drivers
went into new driver folder and did  make and make install
created the new lines as described here in the two files as described
still cannot push data through adapter.

using 10.04 on a dell desktop

---

### Post by satyanash on 2010-12-07
> **teeron said:**
> Hi

I did what [CommuneOfLoon]("http://ubuntuforums.org/member.php?u=1161883") wrote and its almost fine.  Almost.

After reset, network manager detect my network but every few minuts is keep asking me about authorisation key. Im using wpa/wpa2 personal  authentycation type and im sure i have put correct key.

Pls help.

> **mfrost said:**
> i have this same usb adapter. i followed the steps here and managed to get the lights to show up on the adapter and the indicator on the top of the screen animates when i sellect connect to hidden network and then try my router. but no connection. also it does not see any broadcasting routerrs in range at all. so i think there is still a failure in the running of the ralink driver rt2870sta. how can we diagnose this and fix?



I had this same kind of problem and when i tried to connect to the hidden network, it would ask me for a password but would never connect. I then noticed that the procedure mentioned in this thread results in working of adapters only when the wireless key for that network is set to WPA-AES and not WPA-TKIP..Maybe you could try setting the key to AES and then try connecting.
Just a suggestion. O:)

Satyajeet

---

### Post by mfrost on 2010-12-07
unfortunately this does not work, changing to aes. i still cannot see any local broadcasting networks. i can ask to connect to a hidden netowrk and select the profile i made for my own router but it fails to connect. i still think it is a driver problem as the adapter still sees no networks at all.

m

---

### Post by na_ka_na on 2010-12-16
I followed the the instructions on post#1 of this thread and it worked w/o any problems!

Thanks you guys are awesome!

---

### Post by hedbone on 2011-02-22
The info in post #1 worked for me in 10.04, then I upgraded to 10.10 and tried a bunch of newer 'fixes' including the 'just plug it in and go' one.  They didn't work. ndiswrapper crashed when I tried to install the adapter (of course it was a shot in the dark because the adapter isn't covered by ndiswrapper).

Remembered this fix, looked it up, cut and pasted and bam. WiFi.

I'm on a Dell Latitude C610
512k
dual boot XP/Ubuntu 10.10
PCMCIA USB 2.0 card with the Belkin F6D4050v1 plugged into it
Half the 80Gb hard drive for each OS

This setup with the Belkin adapter plugged into the USB 2.0 card locks up XP more often than not.

I'm happy. Thanks!

---

### Post by demitsos_th on 2011-03-21
Those info were unbelievable helpful!! Suddenly in two minutes i had wireless connection!! :-) :-)
You are awesome!! thank you!!:guitar:

---

### Post by psych107 on 2011-03-22
I'm running Kubuntu 10.10, I already have a compatible adapter, just wanted to test wireshark so I thought I'd see if promisc works with the Belkin adapter.  

followed the instructions (using kate instead of gedit: There was nothing in the files--not sure if there was supposed to be? and changing 935a to 935b as my adapter is the second version), reset my comp, sudo airmon-ng ... it doesn't show up, just my other adapter... lsusb returns

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 050d:935b Belkin Components 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


any suggestions?

---

### Post by maurizioparme on 2011-04-27
Hello to all. This is my fist visit on this beatiful forum.
I had follow istruction for install the wirless belkin model F6D4050 v1 and after this the sistem recognize the unit and searc to connect  but after a lot of time ask the WPA password . Off course the WPA password it is correct . I have installed ubunto10.04 and on Ubunto 10.10 (on other pc) work regolary. Now Can I have the unit  in funcion witout install the new release on this laptop. 
Thank 
maurizio

---

### Post by mikef187 on 2011-04-27
Just in case you have the **050d:945a **Belkin dongle. 

Thank you, this informaion worked perfectly on my 10.10 64.
However I have the belkin usb 050d:9**4**5a note the 45 instead of 35. 

I change the **rules **and **conf **file to reflect the 050d:945a id instead of 050d:935a and it worked flawlessly.

---

### Post by maurizioparme on 2011-04-29
silvia@silvia-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 050d:935a Belkin Components 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
silvia@silvia-laptop:~$ 
 this is the answer on my laptop. the belkin is 935a type.
the sistem " see " the item   but not aknowlage the system key "WPA" also if it is correct.
On version 10.10 ubunto work correctly.
someone same advise
thanks

---

### Post by normanp on 2011-07-08
Hi - I followed the instructions in post 2 and there is no sign that the device is recognized (nothing in the notification area network applet). The driver appears to be there though:

lsusb:
```
Bus 001 Device 006: ID 050d:935a Belkin Components
```

from lsmod:
```
crc_ccitt               1351  1 rt2870sta
```

When I do dmesg | egrep 'rt28|usb|Phy' the end of the file is:
```
[   21.894557] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   21.981211] rtusb init --->
[   21.981605] usbcore: registered new interface driver rt2870
[  246.944898] usb 1-4: USB disconnect, address 4
[  259.888031] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  998.378476] usb 1-4: USB disconnect, address 5
[ 1003.808019] usb 1-4: new high speed USB device using ehci_hcd and address 6
```

The last few lines appear as I connect & disconnect the device.

Also iwconfig gives:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

Any ideas would be really appreciated.
I'm running Linux Mint 10 (based on Ubuntu 10.10)
Many thanks

---

### Post by babusar on 2011-09-01
> **b k said:**
> Hi there, I am no expert and what I am going to suggest to you is info I have read on this forum - amended slightly to suit your wireless adapter.
 
Try at your own risk !!!
 
It is strongly recommended that you copy the code that needs to be executed (from a Terminal window) below to a .txt file to your Ubuntu machine via a usb dongle to miminise human typo errors.
Open this .txt file and copy and paste the code into the Terminal window of the Ubuntu machine (with the wireless adapter problem).
 
Go to :
*Applications, Accessories, Terminal*
 
```
lsusb
```
 
Check the output to make sure that your device ID is:
 

 
If it matches, do this:
 
```

sudo gedit /etc/udev/rules.d/network_drivers.rules

```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta"
```
 
Proofread carefully(ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=red]save[/COLOR] and close gedit.
 
Next do this:
 
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id
```
 
Proofread carefully(ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
Reboot
 
Good luck and let us know if it works.
 
PS: most of the above info is modified from this link posts #32 and #58 [http://ubuntuforums.org/showthread.php?t=1419504&page=6](http://ubuntuforums.org/showthread.php?t=1419504&page=6)
 
**_Update: _**
The above procedure works - see post #6
This worked perfectly. Thank you!

---

### Post by Levo2012 on 2012-01-28
I have looked to this thread many times to install my own Belkin F6D4050 

Recently I have just changed my PC to act as a backend MythTV box. Using Mythbuntu 10.04

But it doesn't let me install the drivers for this using the commands above. 

Anyone any suggestions?

---

### Post by Iowan on 2012-04-22
Closed.

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.Original thread is two years old - and marked [SOLVED]

---

