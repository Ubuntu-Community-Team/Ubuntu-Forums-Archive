---
title: "help me with these instructions for wireless"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-01-03
on this site 
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

I get to 'Enable support in udev' and I don't know exactly what they are doing, the line runs on, so how do you enter it?
Are you logged here as root?? They dont mention these details.
So confusing it is.

> Enable support in udev

root@ubuntu:~# cat /etc/udev/rules.d/95-W331M.rules 
SUBSYSTEM=="usb", SYSFS{idVendor}=="148f", SYSFS{idProduct}=="5370", RUN="/etc/W311M.sh"

root@ubuntu:~# cat /etc/W311M.sh 
#!/bin/sh
modprobe rt2800usb
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id

---

### Post by chili555 on 2012-01-03
Let me see if I can help. Please do in a terminal:```
sudo su
gedit /etc/udev/rules.d/95-W331M.rules 
```A new empty document will open. Copy and paste the text as follows:```
SUBSYSTEM=="usb", SYSFS{idVendor}=="148f", SYSFS{idProduct}=="5370", RUN="/etc/W311M.sh"
```Proofread carefully, save and close gedit. Now do:```
gedit /etc/W311M.sh 
```Copy and paste this text:```
#!/bin/sh
modprobe rt2800usb
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id 
```Proofread carefully, save and close gedit. Now do:```
chmod +x /etc/W311M.sh
exit
```You should be all set. Post back if you get stuck.

---

### Post by sdowney717 on 2012-01-03
thanks, that makes perfect sense.

Can we get those instructions repaired so people wont be confused?

this little usb wireless n device I bought off ebay for $5 and it works fine after I did these first set of instructions.

Got hung up with the udev commands
What does udev deal with?
reboots and it is there?

---

### Post by chili555 on 2012-01-03
> Can we get those instructions repaired so people wont be confused?I'm not the original author so I can't but you might try to contact them.> What does udev deal with?udev is a generic kernel device manager. It listens to events the kernel sends out if a new device is initialized or a device is removed from the system. The system provides a set of rules that match against exported values of the event and properties of the discovered device. A matching rule will possibly name and create a device node and run configured programs to set-up and configure the device. Right up your alley, eh?

In your case, it says, if old Downey wants to use a device with a usb.id of 148f:5370, we know what to do; load up the driver rt2800usb and attach it to his device.> reboots and it is there? That's the intent. How about rebooting and letting us know? If so, please use Thread Tools at the top and Mark Solved.

---

### Post by sdowney717 on 2012-01-04
yes, it boots up and the wireless is ready and connected.

here is the device and it is really nice.
has a little blue led that flashes
came in a retail like plastic pack with a windows miniature driver disk

[http://www.ebay.com/itm/220901618854?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_3780wt_1250](http://www.ebay.com/itm/220901618854?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_3780wt_1250)

So far works and price is very good.


> Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. 


---

### Post by mindlessgr on 2012-02-14
I have written a blog post with clean enough install on older kernels, hope this helps someone :)


[http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/](http://wp.mindless.gr/2012/02/installing-tp-link-tl-wn727n-usb-wireless-n-150mbps-adapter-on-debian-squeeze/)

---

### Post by anymoose on 2012-03-19
Ok Chili555 post #2 above is definitive! This makes the generic Ubuntu 11.10 out-of-box work
with a TP LINK TL-WN727N(V3) USB Wifi Adapter stick.

Notice that *nothing* needs downloading and nothing needs compilation, just apply the
Chili555 fix to the live filesystem through an interactive terminal shell, and reboot.

ls /lib/modules/

3.0.0-12-generic

The above kernel version is the only one *this post* will work for, especially it will not work
with for the Ubuntu 11.04 release. But other patches will. I am running Ubuntu 11.10 from an
HP 16GB flash drive in USB#1, and the WN727N in USB#2, PC HD is unused and unmodified
I recommend that you bring up the Wifi interface hardware up under MS-Win XP or equivalent
with the included CD disk to test the hardware first, if at all possible. I am posting this over
the now working wn727 Adapter to a Public Wifi network while running in the Ubuntu browser.

I have gone over many google posts to find that this one as definitve. Hopefully this problem will
be fixed in kernels versions beyond 3.0.0-12

---

By the way Chili555, logic dictates that the first file should be named "95-W311M.rules" rather than
"95-W331M.rules" but this won't make any difference to the computer. Thank you for your excellent
analytic assistance based in your previous posts...TNX.

:S:Anymoose

---

