---
title: "I am convinced 10.04's wireless networking is broken"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by niw_uk1964 on 2010-05-30
Why?

My Dell Mini 9 has always had no problems at all connecting wirelessly to any of my two AP's using versions prior to 10.04.

I've done a fresh install of 10.04, I am using the correct Broadcom wireless drivers...connecting to either AP is now a very hit & miss affair, and it seems to just stop working regularly altogether..to the point of seeing no access points even when I set the APs to broadcast the SSD.

I deleted the existing connections, created new one and wireless networking started working again! For a little while until I next rebooted.

I then tried specifying the MAC address of the AP's in the connection details to lock the connection to a specific AP - this utterly broke wireless and the Dell then again refused to see any network - not even others in the neighbourhood. It resolutely refused to try to initiate any network connection until I again deleted the connections and made new ones.


I then tried my MSI Wind U100 netbook with pretty much the same behaviour. Now I know the U100's wireless performance has a bit of a bad rep', but given that the Dell had always been rock solid I would say that the problem lies elsewhere with the o/s itself.

AAMOI, my Windows machines (a Tosh A100-306 and a Dell 1545) have no problems at all.

Has anyone got any pointers because I don't want to have to roll back to 9.10 if I can avoid it? Wired networking is fine of course.

---

### Post by ankspo71 on 2010-05-30
Hi,
I'm brand new to wireless cards (belkin wireles router and usb card). Mine seems to work fine in Ubuntu/Kubuntu 10.04 but I learned right away that I never should do an improper shutown/reboot with wireless, because it is nearly impossible to get it connected again, even after rebooting a few times. Otherwise it connects and stays connected well enough. I can't use "sudo reboot" anymore :( I don't recommend try killing the network manager with an active connection either... 

I was having major problems with my hardware a week ago, but it was because of the current kernels not getting along with a perfectly good external dvd burner which still works great in every OS I use, but it caused other hardware problems (wireless internet and internal burner), but only in Ubuntu/Kubuntu Lucid. I was able to temporarily fix the issue by installing an experimental kernel, but that left me without proprietary graphics drivers. So I disconnected the external dvd drive and reinstalled kubuntu now everything works with the default kernal choices. Is there any hardware that you can temporarily unplug to see if the wireless problem continues?

Like you, wired connections worked flawlessly over here too.
Hope something I said helps.

---

### Post by niw_uk1964 on 2010-05-30
Hi,

Thanks for the feedback. Alas they are standalone laptops with nothing extra plugged into them so, there is no hardware I can remove to test your suggestion.

---

### Post by purelinuxuser on 2010-05-30
Exactly what wireless card do you have and what Broadcom driver are you using (b43, b43legacy, or STA)?  In my experience, b43/b43legacy have been slow and have had constant disconnections.  Broadcom STA worked OK but was still a little slow and was not always reliable.  Ndiswrapper was always the best route... not that it's very ideal :(

---

### Post by ugm6hr on 2010-05-30
I know it's always unhelpful to have people say, "Well it works for me," but my Mini 9 works fine with WPA and open networks.

I use Xubuntu 10.04 and Network Manager (same as Ubuntu) and the wl0 (Broadcom STA) driver.

Is it possible that the wifi card has become partially unseated? That might explain why the problem is intermittent.

---

### Post by niw_uk1964 on 2010-09-08
Update on this...

The Dell is now working fine again once I changed channels and had been through a raft of updates.

Neither U100's I have will connect reliably (see new thread posted elsewhere)

---

### Post by hermit on 2010-09-10
I too have found that my wireless connections are much flakier under Ubuntu 10.04. I have a IDU-2850UG-G2000 High Power USB Wireless Adapter based on a Realtek RTL8187 Wireless 802.1 b/g 54Mbps USB Network Adapter and my computer is a Dell Latitude D810. I am using the native driver for the RealTek 8187 as the card was immediately discovered and recognized.
For me the problem is that what is a usable connection under WindozeXP (and also *very* good connection on my friend's MacPro using this same wireless networking card of mine), in my Ubuntu partition the connection is very unreliable. I can't even get email. It shows the connection and it works a little bit occasionally but it is never stable or really usable.

yd@yd-laptop:~$ sudo lsmod | grep 8187
rtl8187                50680  0
mac80211              204922  1 rtl8187
led_class               2864  1 rtl8187
cfg80211              126485  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
~~~~~~~~~~~~
yd@yd-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
~~~~~~~~~~~~
Any suggestions for tweeks which might help to get this wireless iceberg to thaw and flow naturally would be very much appreciated.

---

### Post by roberj13 on 2010-09-13
My wireless had been working fine here for a long time (never has seemed to work as fast as ehn I am booted under win7) but has just recently stopped working consistently. Sometimes I can get it to connect for an hour or so, sometimes minutes, sometimes not at all. I haven't changed any settings since it worked but went through a few updates.. I really don't want to have to do a clean install b/c I have about 15 gb of data I would have to move but can't keep having to connect wired all the time. Btw, have been using the sta driver for broadcom since I've been on 10.04 but like I said just recently stopped working and I know hardware wise everything works since wifi works fine under win7.. Hope someone has some ideas..

---

### Post by ugm6hr on 2010-09-14
Intermittent wifi problems that occur mysteriously are often related to the wifi channel in use - if someone else is using the same frequency, it can interfere.

Try changing the router's channel.

Not sure why W7 works OK tho, unless coincidental.

---

### Post by cecetka on 2010-09-15
Hi,
Wireless problem here too - fresh install Ubuntu 10.04 on Laptop Medion akoya - connection is established one of ten times. If successful, the connection brakes after 1 min. Have to go back to 9.10 - there it worked OK. 
Martin

---

### Post by zdenal on 2010-10-11
Hallo,

to fix Lucid Broadcom WPA issue, i have written an how-to:

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

Maybe it can helps to solve your problem.

---

