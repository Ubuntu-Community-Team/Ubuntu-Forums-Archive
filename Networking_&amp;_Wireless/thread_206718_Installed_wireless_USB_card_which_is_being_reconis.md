---
title: "Installed wireless USB card which is being reconised but i cant connect to the web"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by statue12 on 2006-06-30
Ive recently installed ubuntu on my laptop and got the app which lets you install windows driver.  I installed a wireless USB card which is being reconised by the system.  I have a wireless router and want to get on the internet through the wireless usb card.  Even if i set the IP's myself it just comes up saying page cannot be displayed.  My router is called cable and wireless 11g ADSL router.


If anyone could help it would be much appriciated.

Thanks alot:)

---

### Post by jarland on 2006-06-30
It does say found when you do a ndiswrapper -l command right?

---

### Post by statue12 on 2006-06-30
When i done that it come up with a list of instructions saying 

l. install dirvers


and so on, but when i press l it says unknown command.


Thanks for such a quick reply pete

---

### Post by statue12 on 2006-06-30
ive just typed ndiswrapper -l and it did list the driver as installed for my usb lan card.

Cheers

---

### Post by jarland on 2006-06-30
I'm just reaching at this point, but try typing "ndiswrapper -m" and then "modprobe ndiswrapper" if my memory serves correctly. Then restart & see if it's any different.

---

### Post by statue12 on 2006-06-30
i done what you said and it said FATEL: inserting ndiswrapper (/lib/modules/2.615-23-386/kernal/drivers/net/ndiswrapper/ndiswrapper.ko): operation not permitted

Also when i run ndiswrapper -m it said modprobe already contains alia directive

Thanks for your help
Much apprciated:)

---

### Post by statue12 on 2006-06-30
ive just accesed the tool which monitors the signal strenght it says 100% signal and its under the right device wlan0 but it says status disconnected.

---

### Post by statue12 on 2006-06-30
it continously say its disconnected even though the signal strenght is 100%

---

### Post by jarland on 2006-06-30
Hmm...I'm gonna have to throw in the towel on this one. Hopefully someone else can tell what the problem is. I wanna say that error you got could be the problem, but if it's showing your signal strength we're obviously past that part. If no one else replies, you may search the forum for the model of your card & see if you can find out if anyone else has had a similar problem.

---

### Post by statue12 on 2006-06-30
Thanks alot for all your help much appriated

cheers

---

### Post by az on 2006-06-30
Why ndiswrapper?  Did you try the thing without it?  It is probably not working with ndiswrapper because you cannot have two drivers trying to access the same device.

If the native linux driver does ot work, you need to blacklist it before you can get ndiswrapper to work with it.

What happens when you boot without the thing plugged in, open a terminal and type

tail -f /var/log/messages

and then plug the thing in?  Post the output.

---

