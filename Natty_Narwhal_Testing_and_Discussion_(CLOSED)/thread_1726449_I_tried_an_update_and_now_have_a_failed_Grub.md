---
title: "I tried an update and now have a failed Grub"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Oathanvil on 2011-04-11
I tried this!

**Get Ubuntu 11.04**

 **Upgrading from Ubuntu 10.10**

 To   upgrade from Ubuntu 10.10 on a desktop system, press Alt+F2 and type  in  "update-manager -d" (without the quotes) into the command box.  Update  Manager should open up and tell you: New distribution release  '11.04' is  available. Click Upgrade and follow the on-screen  instructions. 

From: [http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1)

In the Grub selection Screen I now have a new Ubuntu Boot option with a higher version number. If i select and run that new version it returns me to a black screen asking for my User: then login: I type those in correctly and then get a blinking @ubuntu curser.

It wont load the desktop automaticly. What command from that point can I enter to load Ubuntu? I am old school and tried run but that got me a scrolling text window of data however no boot.

Any help thank you.

---

### Post by Perfect Storm on 2011-04-11
Moved to Development & Testing Forum.

---

### Post by frankbooth on 2011-04-11
Not sure if there's a simpler way, but reinstalling Grub using the 'Rescue' option on a LiveCD should do the trick.

---

### Post by kansasnoob on 2011-04-11
Are you able to boot the older kernel?

---

### Post by Oathanvil on 2011-04-12
> **kansasnoob said:**
> Are you able to boot the older kernel?


Sorry in the delay yes I am able to boot to the old Kernal with no issues at all. The update simply provided another new Version of Ubuntu and it's partner recovery option.

I guess what I need to get is the command to start Ubuntu from DOS as it leaves me a working prompt, perhaps the new version will boot at that point with the correct command.

Would the command be \boot

---

