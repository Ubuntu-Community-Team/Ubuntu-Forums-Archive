---
title: "Broadcom Wireless Card Not Working on Ubuntu 10.10"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by ooooolalalalala on 2010-11-21
I have a Broadcom BCM4311 wireless card on my Dell D620 laptop.

```
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

My wireless works perfectly with my university networks. But I have problem connecting to my house router. The first time I installed Ubuntu 10.10, it connected to internet and worked well. After a restart needed by nVidia driver, my house wireless stopped working while my university wireless still works. I have tried reinstalling the driver using System/Administration/Additional Drivers and manually

```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```

None of them works. Anyone had such a problem? Any suggestions?

---

### Post by uncaspi on 2010-11-21
I don't know if this helps, but you could try to change channel and increase txpower

Suppose wlan0 is your wireless card. Check it with sudo iwconfig

then

sudo iwconfig wlan0 channel 1 txpower 20

---

### Post by ooooolalalalala on 2010-11-21
Thanks, but not working. iwconfig give me this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"YYY-YYY"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=24 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:17  Invalid misc:0   Missed beacon:0
```


I do not have any wlan0 and have eth1 instead! I am now sending this through my university wireless. So wireless is working! I tried this

```
sudo iwconfig eth1 channel 1 txpower 20
```

The txpower will change to 20 in eth1, which I am assuming is my wireless card. But still I cannot connect to my house router.

PS: I have a dual boot system (Windows 7 and Ubuntu 10.10). The house router works perfectly on Windows so the router is also working.

---

### Post by magnatron on 2010-11-21
It might be your house router needs a reboot.

---

### Post by ooooolalalalala on 2010-11-21
Restarting the router doesn't help. I have also tried upgrading the router's firmware!

---

### Post by johnmay on 2010-11-21
There are several threads about broadcom 43xx cards not being well supported. 

A few solutions have been reported for 32 bit, though I am still looking for 64 bit drivers. 

Try searching for bcm43 in the wireless forums.

Good luck!

---

### Post by Hippytaff on 2010-11-21
Also, if all else fails look into using the windows xp driver with Ndiswrapper

---

### Post by johnmay on 2010-11-21
Here is the thread that contains a solution, it does involve ndiswrapper, and the 32 bti driver... Not the same manufacturer, but I believe it is the same chipset. 
Support for Netgear WNA3100 USB Adapter

the posts from Victory Red are informative

---

### Post by ooooolalalalala on 2010-11-21
johnmay, Can you provide us with a link to the thread you mentioned? I have tried lots of these solutions, I'll try this one too! :D

---

### Post by ooooolalalalala on 2010-11-23
Finally solved! I removed the wireless security of my router which was WPA-PSK [TKIP] and enabled it again. Now it works with WPA-PSK [TKIP]. Seems weird!

---

### Post by Hippytaff on 2010-11-23
Excellent...well found, remember to mark the thread as solved so others can benefit from what you did :-)

---

### Post by johnmay on 2010-11-26
ooooooooooooooooolalalalalatida:

Sorry I didn't notice your post earlier. Glad that you have solved the problem though!

Look like that your solution might only work on the 32 bit version though. 

I will look for the post I was referring to, and post that link as an edit in this thread. sometime before the meteor hits.

---

### Post by zdenal on 2010-12-02
I had same problems with Broadcom driver on Lucid and Maverick.

In my post

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

I summarize some facts so you can check

a) If your Broadcom card is supported by the wl.ko driver
b) Use step by step HowTo to try fix your wireless problem

Hope this helps..

---

### Post by jacobsca on 2010-12-27
I am new to Ubuntu and installed 10.10. I have a Broadcom card and have spent the last day futzing to get wireless access. I followed the instructions at [http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html) and installed the sta driver. Voila - wireless access!

Now the confusing issue and question. 

If I log off and then log back on - no wireless. The driver is "not active."
 
If I uninstall (using "Additional Drivers") and then reinstall - wireless is back.

This is a pretty clumsy workaround. Can someone help me determine how to make this stick so that when I log on the wireless is present (which incidentally goes to eth1 after the reinstall...)

Thanks in advance!

---

### Post by bkratz on 2010-12-27
> **jacobsca said:**
> I am new to Ubuntu and installed 10.10. I have a Broadcom card and have spent the last day futzing to get wireless access. I followed the instructions at [http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html) and installed the sta driver. Voila - wireless access!

Now the confusing issue and question. 

If I log off and then log back on - no wireless. The driver is "not active."
 
If I uninstall (using "Additional Drivers") and then reinstall - wireless is back.

This is a pretty clumsy workaround. Can someone help me determine how to make this stick so that when I log on the wireless is present (which incidentally goes to eth1 after the reinstall...)

Thanks in advance!


When you say logoff do you mean actually shutting down the system and rebooting? If so, you might look at /etc/modules and see if it says wl along with the usual lp and a bunch of stuff commented out. If not the following should add it. Then reboot.

```
echo wl | sudo tee -a /etc/modules

```

or you can just do it with gedit. But look at it first and see if it is there and it is something else.

---

### Post by jacobsca on 2010-12-27
well, /etc/modules just has lp in it. nothing else.

what does the line in your reply?

---

### Post by bkratz on 2010-12-27
Well that file contains the modules that are loaded at boot time.
echo wl line above would append wl (which is the name for STA driver) there also so it would load at boot.

Another way would be to 

gksudo gedit /etc/modules

and add a line with just wl below the other one.  Gksudo would require your password which would not be seen on the screen at all, not even ****. Just put the password in and press return(enter).  It would look like this

[B]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
[/B]

Just save and reboot when done

---

### Post by jacobsca on 2010-12-27
thanks - works perfectly now. I very much appreciate it.

---

### Post by bkratz on 2010-12-27
Congratulations on getting it working and you got a little terminal experience in the process too!

---

### Post by lilbmorgan on 2010-12-28
With almost any OS, upgrading or adding a new OS will require you to reset your router ... and I do not mean simply turning it of then back on. I mean a factory reset and establishing a new encryption.

---

