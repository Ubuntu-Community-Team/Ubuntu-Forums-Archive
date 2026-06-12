---
title: "Wireless Works on Live-CD but not after Install"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by A4orce84 on 2010-01-13
Hey Everyone,

So I recently installed Ubuntu 9.10 on to my machine, and my wireless card worked fine under the Live CD so I was like w00t, let's install this sucker.

However after installing, my wireless card is not recognized at all (System --> Admin --> Hardware) and I'm a bit frustrated and trying to get it to work.

The wireless driver that it uses under the Live CD to connect to the internet is:

Broadcom STA wireless Driver


Just for reference here is the actual wireless adapter I am using on my desktop (WMP300N):
[http://www.amazon.com/Linksys-Cisco-Wireless-N-Adapter-WMP300N/dp/B000FDDUXG](http://www.amazon.com/Linksys-Cisco-Wireless-N-Adapter-WMP300N/dp/B000FDDUXG)


I tried following the DIY located below but to no avail:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

My wireless still refused to work after installing the driver. =(

Any help would be greatly appreciated! =(

Thanks!

--Asif


Update:

Was working once, but after I restarted it could not find any wireless networks again. =(

Not sure what's happening...

---

### Post by A4orce84 on 2010-01-14
Update:

Seems that it may be intermittently working if that makes sense. Disabled the adapter (uninstalled the driver) and re-enabled (re-installed) and it worked again.

However, after restarting it disappeared...I tried the same disable/enable step, to no avail.

It somewhat reminded me of the following post:

[http://ubuntuforums.org/showthread.php?t=1070978](http://ubuntuforums.org/showthread.php?t=1070978)


Does anyone have any advice / tips / help they can provide please?

Thank you in advance!


--Asif

---

### Post by A4orce84 on 2010-01-14
Anyone?

---

### Post by A4orce84 on 2010-01-14
Ttt

---

### Post by warfacegod on 2010-01-14
Go to: System> Admin.> Hardware Drivers and activate the recommended wireless driver.

---

### Post by A4orce84 on 2010-01-14
> **warfacegod said:**
> Go to: System> Admin.> Hardware Drivers and activate the recommended wireless driver.


However after installing, my wireless card is not recognized at all (System --> Admin --> Hardware) and I'm a bit frustrated and trying to get it to work.

---

### Post by d3v1150m471c on 2010-01-14
stupid question. do you have wireless enabled in your network manager? It's on the icon tray, you should be able to rightclick and select it if it's not.

---

### Post by warfacegod on 2010-01-14
> **A4orce84 said:**
> However after installing, my wireless card is not recognized at all (System --> Admin --> Hardware) and I'm a bit frustrated and trying to get it to work.

Reboot.

---

### Post by bigal50 on 2010-01-14
You didn't mention what version your using, for me and 9.10 what I have to do to get my Broadcom working is install the system then using an ethernet connection and a terminal I do 
```
sudo apitiude update
suod apitude upgrade
```
Reboot
Then using System/Administrator/Hardware Drivers and activate the STA driver
Reboot again
You should now see your wifi network in the network manager now.

---

### Post by A4orce84 on 2010-01-16
> **bigal50 said:**
> You didn't mention what version your using, for me and 9.10 what I have to do to get my Broadcom working is install the system then using an ethernet connection and a terminal I do 
```
sudo apitiude update
suod apitude upgrade
```
Reboot
Then using System/Administrator/Hardware Drivers and activate the STA driver
Reboot again
You should now see your wifi network in the network manager now.


neither of these commands worked in terminal. =(

--Asif

---

### Post by warfacegod on 2010-01-16
> **A4orce84 said:**
> neither of these commands worked in terminal. =(

--Asif

They are spelled incorrectly it should be:

```
sudo aptitude update
```

---

### Post by JBAlaska on 2010-01-16
1 Open Synaptic Pacakage Manager
2 Ensure 9.10 LiveCd is in CD drive
3 Settings > Repositories > Ubuntu Software
4 Check the "installable from cd" Box and close
5 Refresh
6 Search for "bcmwl-kernel-source"
7 Mark for installation
8 Install it
9 Reboot computer

Now you should have Broadcom STA driver listed in Hardware drivers, Enable and reboot.

---

### Post by A4orce84 on 2010-01-16
> **JBAlaska said:**
> 1 Open Synaptic Pacakage Manager
2 Ensure 9.10 LiveCd is in CD drive
3 Settings > Repositories > Ubuntu Software
4 Check the "installable from cd" Box and close
5 Refresh
6 Search for "bcmwl-kernel-source"
7 Mark for installation
8 Install it
9 Reboot computer

Now you should have Broadcom STA driver listed in Hardware drivers, Enable and reboot.

Thanks JBAlaska I did that the other day, and got the wireless driver to work. The issue now is that it seems that its "active" but only every now and then will it detect any wireless networks and connect.

It seems that if I restart into ubuntu, 1 out of the 5 times will the wireless adapter actually detect any wireless networks. The majority of the time it's just am empty list. =(

My situation reminds me / sounds like the following post:
[http://ubuntuforums.org/showthread.php?t=1070978](http://ubuntuforums.org/showthread.php?t=1070978)


Any other ideas?  Thanks in advance for all the help so far guys, it is greatly appreciated !!

--Asif

---

### Post by JBAlaska on 2010-01-16
Try this:
Remove any other drivers for the Broadcom wireless.

There are several open source drivers that are used to drive Broadcom 802.11 chips such as b43 and ssb. If any of these are present they need to be removed before this driver can be installed.  Any previous revisions of the wl driver also need to be removed.

```
lsmod  | grep "b43\|ssb\|wl"
```

If any of these are installed, remove them:
```
rmmod b43
```
```
rmmod ssb
```
```
rmmod wl
```

To blacklist these drivers and prevent them from loading in the future:
```
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
```

Then this:

```
sudo modprobe lib80211
```
```
sudo insmod wl.ko
```

wl.ko is now operational.  It may take several seconds for the Network Manager to notice a new network driver has been installed and show the surrounding wireless networks.

---

### Post by A4orce84 on 2010-01-16
Hey JBAlaska,

Tried following your steps and ran into some issues:


[IMG]http://img.photobucket.com/albums/v405/A4orce84/Untitled-1.jpg[/IMG]

Sorry I'm such a Linux newb. =(  

I did get a long enough Ethernet cable to actually have internet on my Ubuntu OS, so hopefully it will be easier to debug / troubleshoot now.

Thanks again!


--Asif

---

### Post by warfacegod on 2010-01-16
Try using gksudo or sudo su

---

### Post by A4orce84 on 2010-01-16
sudo su worked, here is the latest output:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/Untitled-2.jpg[/IMG]

Thanks!



--Asif

---

### Post by warfacegod on 2010-01-16
Try putting a / in front of wl.ko

---

### Post by A4orce84 on 2010-01-16
Same result:

root@asif-desktop:/home/asif# sudo insmod /wl.ko
insmod: can't read '/wl.ko': No such file or directory



Also I'm still getting the error with the lib80211 line (screen shot in previous post documented this as well):

root@asif-desktop:/home/asif# sudo modprobe lib80211
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


Any other ideas?  Thanks!


--Asif

---

### Post by warfacegod on 2010-01-16
> Also I'm still getting the error with the lib80211 line (screen shot in previous post documented this as well):

That may need to be: lib802.11

---

### Post by A4orce84 on 2010-01-16
results:

asif@asif-desktop:~$ sudo modprobe lib802.11
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module lib802.11 not found.
asif@asif-desktop:~$ 



=(

---

### Post by warfacegod on 2010-01-16
Did you do an update after trying the CD sources install you spoke of in post #13?

---

### Post by A4orce84 on 2010-01-16
Yeah did a full update on all of Ubuntu after plugging in with my Ethernet cable.

---

### Post by warfacegod on 2010-01-16
Allright, I think you're going have to hang tight for JBAlaska to walk you through this. He's offline at the moment. In the mean time.

[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by A4orce84 on 2010-01-16
sounds good, all hope is on your now JBAlaska !  =)

---

### Post by A4orce84 on 2010-01-17
bump anyone else have any luck with this wireless adapter?

---

### Post by warfacegod on 2010-01-17
I'm still here so don't feel abandoned.

---

