---
title: "rtl8192se not working after standby, Ubuntu 11.10"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by aleealz on 2012-04-15
Hi,

I have a Samsung N130 netbook, with a recently new install of Ubuntu 11.10.  The ethernet works fine. I can also sign in to my wireless network and surf the internet.

Here is the problem, if I go into standby or hibernate, I lose the wireless. It does not even see it or any others around.

I have to delete the wireless connection in the edit preferences box, reboot, reconfigure and I'm back on the wireless.

Here is my info:

Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
Subsystem: Askey Computer Corp. Device 7160

I've done many Google searches, but most of them address earlier versions of Ubuntu.  I think something is no getting reloaded after the standby.

Any help would be greatly appreciated.  I'm rather new to linux and find it unbelievably easy and faster than that other OS ;-)

Thanks

---

### Post by PaulW2U on 2012-04-15
I can't help solve your problem as I experienced exactly the same with my own N130 and Ubuntu 11.10 but it I've read that it can be fixed. I gave up after trying for far too many hours.

What I can say is that resuming from suspend mode on my N130 running a **development** version of the next Ubuntu release, 12.04, works perfectly. It'll be released on 26th April.

If you don't get the problem fixed before then, then that's something else you can try.

---

### Post by aleealz on 2012-04-15
Thanks for the response,  One thing I did do was blacklist all the other RTL8192XX drivers,  This got me to where I am now.  Maybe that will help?

Funny thing is, after suspend mode, When I click on the wireless network icon, I briefly see my network, then nothing.

Weird.

---

### Post by chili555 on 2012-04-15
> I think something is no getting reloaded after the standby.Yes, indeed. While the wireless is working, open a terminal and list the modules that are loaded and look (grep) for one with 8192 in the name:```
lsmod | grep 8192
```Jot down the *exact* name on ye olde Postit. Now suspend, wait a few moments and resume. Look again:```
lsmod | grep 8192
```I suspect the driver is missing. If that's the case, let's see if we can get it to load on resume:```
sudo gedit /etc/pm/config.d/config
```A new empty file will open. Add one line:```
SUSPEND_MODULES="rtl8192e"
```Of course, substitute the actual driver you found if it's not rtl8192e. Proofread, save and close gedit.

Now is it better? It may take a reboot.> One thing I did do was blacklist all the other RTL8192XX drivers, This got me to where I am now. Maybe that will help?It will not help or harm.

---

### Post by aleealz on 2012-04-16
Thanks for your help

First boot after configuring wireless network:


lsmod | grep 8192
r8192e_pci            234281  0 
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393421  2 rtl8192se,rtlwifi

After suspend is exactly the same, without wireless access:


lsmod | grep 8192
r8192e_pci            234281  0 
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393421  2 rtl8192se,rtlwifi

Point of interest...

My original information on my wireless was:

Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
Subsystem: Askey Computer Corp. Device 7160

This was copied from a small program called system info.  In my file system searches, I've come across both rtl8192se & SE. I know Ubuntu is case sensitive, could this have anything to do with my issue?

Thanks again.

---

### Post by chili555 on 2012-04-16
> In my file system searches, I've come across both rtl8192se & SE. I know Ubuntu is case sensitive, could this have anything to do with my issue?
None whatever.

Evidently the driver is not unloading. My sweet fix is not helpful! I know of no automated fix. When this happens, you might try:```
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
``` If it works, you might be able to make a little launcher for your panel. There is probably an elegant way to handle this in /etc/apm/suspend.d or something similar; I just have no idea how.

Sorry I couldn't be of more help.

---

### Post by aleealz on 2012-04-18
Thanks Chili555, but that didn't work either.  I got a "SIOCSIFFLAGS: No such device" error.  Just to be on the safe side. I did it as 2 commands: 

sudo ifconfig wlan0 down worked fine

sudo ifconfig wlan0 up - caused the error

---

### Post by aleealz on 2012-04-18
Also, when I ran ifconfig while on the wifi I got:

eth0
lo
wlan0

when I ran it without wifi the wlan0 was missing.  This probably makes sense, to those who know, but I just thought it was worth mentioning.

---

### Post by aleealz on 2012-05-06
Thank You to the developers who listened to all of our complaints on this subject.

This issue has been resolved for me by upgrading to 12.04.

---

