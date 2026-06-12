---
title: "WICD does not show wireless nets"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by davelbarton on 2010-06-06
For some reason, wicd is not showing wireless nets.  The only network that appears on my Wicd Network Manager display is the wired connection; it shows no wireless at all (even when I unplug the wired connection).  Hitting refresh doesn't do the job.

This isn't a hardware problem; when I do "sudo iwlist scan" the wireless nets in range show up just as normal, clearly.  I cannot find any any switch that seems to turn the display of wireless nets on or off.

Can someone more knowledgeable please help here?

---

### Post by swimfish on 2010-06-07
try sudo iwconfig


find out the device name of your wifi.  

plug that into the device preference into wireless for wicd  something like wlan1  ath0  etc

if you see nothing except loopback when doing sudo iwconfig you should try sudo lsusb or sudo lspci  and try and get your wireless functional.  google is your friend, these forums too.

---

### Post by davelbarton on 2010-06-07
Swimfish, thanks so much for the reply and information!

Unfortunately, my "wlan0" is already plugged into the preferences for wireless under wicd --- that far I got!  However, it still does not see any wireless interfaces.  I know the interfaces are there because my HP IPAQ (PDA) can see them and connect to them.

So I fear I am still stuck.  Anyone have any other ideas, please?

I'm on Ubuntu Karmic, on an HP Pavillion dv7.

Thanks so much for any information, all!

---

### Post by davelbarton on 2010-06-08
Bump.

Please help!

---

### Post by davelbarton on 2010-06-14
One more bump, in the hopes that someone will know what is going on with wicd.

---

### Post by Fremont_Cunningham on 2011-05-22
Bump!
Acer Aspire4530/64-bit AMD/ Maveric. This 'no wireless network found' problem is still there.
Is anyone working on the Wicd problems?

---

