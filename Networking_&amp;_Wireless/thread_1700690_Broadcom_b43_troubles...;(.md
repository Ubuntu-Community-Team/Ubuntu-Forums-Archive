---
title: "Broadcom b43 troubles...;("
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by xVx on 2011-03-05
I know this topic is done to death...But I've been through tons of tutorials and I'm still stumped.

I have a Broadcom 4311 wireless card. Have looked it up and I'm sure it's supported by B43. I know the b43 driver is installed. I have used b43-fwcutter to extract firmware files from broadcom-wl-4.150.10.5.tar.bz2 however it places a b43legacy folder in my /lib/firmware and the wireless card doesn't 'just work'. My question is, is there another package similar to broadcom-wl-4.150.10.5.tar.bz2 with b43 firmware instead of b43legacy firmware? If so I haven't been able to find it on the net. (I'm going back and forth to Windows to connect to the internet so I can't use apt-get)

Does it even matter that the firmware is b43legacy and the driver is b43, or do I have some other, different problem?

I'm also wondering if there's some other step I'm missing like initializing the driver or something....

The wireless card reads as present but doesn't connect. 
I've blacklisted wl, bcm43xx and ndiswrapper.

Thanks in advance!

---

### Post by xVx on 2011-03-05
Update::

I found b43-firmware_1.0-0cafuego0_all.deb which installed a b43 folder into my /lib/firmware directory. Now there is b43 firmware and a b43 driver installed. I've restarted both the driver and the computer. Now when I type iwconfig I get: 

wlan0     IEEE 802.11bg  ESSID:"Apt201"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:E0:57:91   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


which is different from before because there was no entry under access point before b43 firmware was installed. As well, in the GUI network manager the wireless card now shows up with a check mark whereas before it showed up with an empty box. 

However, no ping to the router and no pages loading in firefox =( What am I missing
?

---

### Post by Megaptera on 2011-03-05
I don't have a Dell Mini but I've used this broadcom fix with success, don't forget to reboot

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

Hope this helps?

---

