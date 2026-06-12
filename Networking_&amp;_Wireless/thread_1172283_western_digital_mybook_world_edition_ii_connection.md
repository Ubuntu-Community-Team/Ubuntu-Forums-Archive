---
title: "western digital mybook world edition ii connection"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by matthiayer on 2009-05-28
i have the same drive,
its connected to my network switch.
when i connect straight to the switch i can connect to the drive.

but when i connect to the wlan (connected to the switch too) i can't connect to the drive!

yesterday this was still possible..

i tried rebooting the drive, pc,.. power off wlan router, switch, modem.
searching in win xp, vista, ubuntu..

nothing works!!

does anyone know what's wrong?

---

### Post by dmizer on 2009-05-28
> **matthiayer said:**
> i have the same drive,
its connected to my network switch.
when i connect straight to the switch i can connect to the drive.

but when i connect to the wlan (connected to the switch too) i can't connect to the drive!

yesterday this was still possible..

i tried rebooting the drive, pc,.. power off wlan router, switch, modem.
searching in win xp, vista, ubuntu..

nothing works!!

does anyone know what's wrong?
Are you sure you're connected to your own wireless network?

---

### Post by matthiayer on 2009-05-28
yes, very sure!!

---

### Post by dmizer on 2009-05-28
I broke these posts out so we could discuss this without hyjacking the other thread. Your problem is a bit different.

Just out of curiosity (not that I doubt you), how do you know you are connected to your own wireless network? Also, what kind of configuration changes have you made between then (when it was working) and now.

You may have success with this thread: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by matthiayer on 2009-05-28
i have 2 wireless networks at my place: 
one of those has my name, and it says its connected to this one..

i took a look at that link, but i have the same problems in win xp.
while i have no problems when i connect via lan..

---

### Post by dmizer on 2009-05-28
If you have the same problems both in XP and Ubuntu (can connect wired, but not wireless), then I can say with about 99% certainty that you have a network configuration problem.

How is your network physically built? What's connected to what?

---

### Post by matthiayer on 2009-05-28
motorola modem from the provider is connected to switch
my book and wireless router connected to switch

switch : dwl-G700ap
router: DES-1005D

---

### Post by dmizer on 2009-05-28
Disable NAT on your wireless router. That should correct your problem.

Alternatively, you could reconfigure your network this way:

modem -> router -> switch -> rest of network

But, you may run into problems with IP address conflicts (actually, you probably are anyway) depending on what IP address you're getting from your modem vs. the IP address you're getting from your router.

---

### Post by matthiayer on 2009-05-28
okay,

i tried before, and i cant seem to get in to the router web interface.
searched for ip, but the it says "page cannot be ..."
i connected straigt to the switch..

i cant connect my router in between switch and modem, so that's not an option!

---

### Post by dmizer on 2009-05-28
You probably can't get into the router interface because both your router and your modem are trying to serve the same IP address range. You'll need to solve that. You could probably just disconnect the router from the switch, and then browse to your router's config page.

---

### Post by matthiayer on 2009-05-28
update..
i got in to my router, after resetting it and a lot of problems.

but i lied..
i have: modem------switch-----wireless acces point          
                      
my book world is also connected to the switch

i didn't find anything about nat
dhcp is off

---

### Post by matthiayer on 2009-05-29
update:
i'm able to acces the web-interface of the disk via a windows vista pc on wlan
but unable to acces the disk itself

i'm unable to see it on a ubuntu laptop/windows laptop


SOLVED

no router, wont work!!

---

