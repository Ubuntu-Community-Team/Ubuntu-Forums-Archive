---
title: "Using iwconfig and ifconfig to connect to wlan hotspots?"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by del_diablo on 2009-09-04
The problem is that i must use Windows at school since wicd cannot connect to any hotspots(gnomes network manager was not able to connect either for the note, ive tested).
So i ask the question, how do i connect just using the terminal(cli)?

---

### Post by kerry_s on 2009-09-04
if the gui's don't work, what makes you think the command line will?

---

### Post by Bucky Ball on 2009-09-04
> **kerry_s said:**
> if the gui's don't work, what makes you think the command line will?

+1

You perhaps have something set up wrongly. If you can get on with Windows, you can get on with Ubuntu; you just need to get the finer details right.

Start with System->Administration->Network, unlock and check the properties for your wireless. You can set up different locations in there. Set one up for your school and just select that when you are there.

To do this you can get the details from your Windows network setup for ESSID, WEP (or otherwise) security key.

How you set it up really depends on how your school has their network setup. Schools are normally pretty secure and 'enable roaming' will not work; you need to be specific. Provide as much detail about the school's requirements and maybe we can help. :)

ps: This advice is only relevant if you know your wireless is working Ubuntu to start with. You use it at home?

---

### Post by del_diablo on 2009-09-04
> **kerry_s said:**
> if the gui's don't work, what makes you think the command line will?

The CLI does not have the flaws of the GUI's configs? The problem is that WICD settup is flawed for hotspots, and that is the issue.
To be honest, i feel like just creating a small script using bash which just sets up the connection when i click it.
I used Ubuntu, got tired of it since it was way to bloat and the config system was a complete mess(don't ask). So i removed it and set up Openbox, which in my opinion is ages  better.

Also, read it: "Hotspot", not "secured/unsecured network".
So i want to use the cli because of the fine print, it will work. So please help me instead of the random minor bickering about the fine print?

---

### Post by kerry_s on 2009-09-04
alright, it's simple:

**sudo iwconfig** = check the settings

**sudo iwlist scan** = that will tell you whats out there & shows you the essid

**sudo iwconfig essid any** = "any" would be the essid name you want to connect to.

**sudo dhclient wlan0** = this is where you make the actual connection, get an address & should be able to get on the net. replace "wlan0" with your connection, see iwconfig.


now if you want a gui that uses the commands given, try **network-config**(sudo apt-get install network-config)run it with "gksudo network-config" it's just a clickable gui that runs those commands for different profiles you set up.

---

### Post by PeonDevelopments on 2009-09-29
> **kerry_s said:**
> 
**sudo iwconfig essid any** = "any" would be the essid name you want to connect to.


**sudo iwconfig [interface] essid any**

(kerry_s, you forgot the interface specification.)

Where [interface] is generally wlan0 or ath0.

---

