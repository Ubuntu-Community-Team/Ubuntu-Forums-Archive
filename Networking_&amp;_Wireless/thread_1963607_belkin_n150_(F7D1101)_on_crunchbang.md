---
title: "belkin n150 (F7D1101) on crunchbang"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by shalomiehomie on 2012-04-22
> **b k said:**
> Hi there, I am no expert and what I am going to suggest to you is info I have read on this forum - amended slightly to suit your wireless adapter.
 
Try at your own risk !!!
 
It is strongly recommended that you copy the code that needs to be executed (from a Terminal window) below to a .txt file to your Ubuntu machine via a usb dongle to miminise human typo errors.
Open this .txt file and copy and paste the code into the Terminal window of the Ubuntu machine (with the wireless adapter problem).
 
Go to :
*Applications, Accessories, Terminal*
 
```
lsusb
```Check the output to make sure that your device ID is:
 

 
If it matches, do this:
 
```

sudo gedit /etc/udev/rules.d/network_drivers.rules

```Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread carefully(ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=red]save[/COLOR] and close gedit.
 
Next do this:
 
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully(ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
Reboot
 
Good luck and let us know if it works.
 
PS: most of the above info is modified from this link posts #32 and #58 [http://ubuntuforums.org/showthread.php?t=1419504&page=6](http://ubuntuforums.org/showthread.php?t=1419504&page=6)
 
**_Update: _**
The above procedure works - see post #6

I'm having the problem with the belkin n150 (F7D1101) on crunchbang. Could this work for it just as well even though you did this with a different model? if it works on ubuntu it should work on crucnhbang crunchbang is a ubuntu based. please let me know!

---

