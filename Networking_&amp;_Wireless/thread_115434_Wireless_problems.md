---
title: "Wireless problems"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by Jammy_Stuff on 2006-01-10
I have recently installed Ubuntu and have my wireless up and running. However, when I boot up the computer, it freezes on the Starting Hotplug System stage. When I pull out the wireless USB adapter, it carries on. I can then plug it back in but I have to go into networking and manually activate the WI-Fi. Sometimes that doesn't appear and I have to reboot until it does. Anybody know what has happpened?

Please help as this is stopping me from moving totally.

---

### Post by gosh on 2006-01-10
What kind of adapter is it?

---

### Post by Jammy_Stuff on 2006-01-10
A Belkin model number F5D7050.

---

### Post by dotdot on 2006-01-10
could be firmware - i had this a while ago - fixed it now - however.. don't hit me - it was a different adapter.

..best of luck

---

### Post by Jammy_Stuff on 2006-01-10
I don't think you can update the firmware on my adapter. Any other ideas?

---

### Post by Jammy_Stuff on 2006-01-11
Sorry to bump but I really need this to work. Do you think upgrading to the newest version of Ndiswrapper will help?

---

### Post by Jammy_Stuff on 2006-01-12
I upgraded to version 1.7 and now ndiswrapper recognises my adapter. lspci however doesn't. According to ndiswrapper it's all been installed fine and there are no problems at boot up anymore. However, I can't activate or configure it at all as it doesn't show up anywhere.

Help.

---

### Post by nijinsky on 2006-01-12
[QUOTE=Jammy_Stuff]I have recently installed Ubuntu and have my wireless up and running. However, when I boot up the computer, it freezes on the Starting Hotplug System stage. When I pull out the wireless USB adapter, it carries on. I can then plug it back in but I have to go into networking and manually activate the WI-Fi. Sometimes that doesn't appear and I have to reboot until it does. Anybody know what has happpened?

Please help as this is stopping me from moving totally.[/QUOTE]

Bump....... it is the exact same as me. It halts after the hotplug initialisation

I'm  a newbie, however, I was thinking about how this could be scripted.

Perhaps by not having the offending module loaded on boot and loading after boot.

Idon't know how to do this though.

ATB
Bob

---

### Post by Jammy_Stuff on 2006-01-13
I'm going to make one final plea for help. If no one can help me, Ubuntu wont be going on my Desktop. I have a beta copy of Windows Vista that can take its place if I can't get Wi-Fi to work. If so I'll just have to hope I have better luck with my laptop and its card.

---

### Post by nijinsky on 2006-01-13
[QUOTE=Jammy_Stuff]I'm going to make one final plea for help. If no one can help me, Ubuntu wont be going on my Desktop. I have a beta copy of Windows Vista that can take its place if I can't get Wi-Fi to work. If so I'll just have to hope I have better luck with my laptop and its card.[/QUOTE]

Hi Jammystuff

I thought that you just had problems with booting because of your Belkin USB.

Just to let you know that I have the same and have the machine working.

Go to here and follow these instructions.
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Then when you start the machine you will still get the bootup sticking at the hotplug. Simply unplug the stick and reinsert it when you get the login screen. I know it is a pain reinserting it but this is the only way I know how.

Now when you go to system-networking manager you may not see a wlan0 entry. Don't worry. 

Open a terminal and type 
sudo ifup wlan0

then you should connect to your wan.

Hope this helps

Bob

---

### Post by nijinsky on 2006-01-13
[QUOTE=nijinsky]Hi Jammystuff

I thought that you just had problems with booting because of your Belkin USB.
[/QUOTE]

BUT I should have read your post properly. Sorry. Since you dont see the wan entry in networking, then this is easy.

open a tetrminal and type 

sudo ifup wlan0

you should either be connected or have an entry in networking.

cheers
bob

---

### Post by Jammy_Stuff on 2006-01-14
I'll have to check what the error message is again but when I type sudo ifup wlan0 I just get an error message and it still doesn't appear. I think that lspci still isn't detecting it so Ubuntu thinks it isn't there.

---

### Post by nijinsky on 2006-01-14
[QUOTE=Jammy_Stuff]I'll have to check what the error message is again but when I type sudo ifup wlan0 I just get an error message and it still doesn't appear. I think that lspci still isn't detecting it so Ubuntu thinks it isn't there.[/QUOTE]

Try lsusb

lspci lists the pci devices but the f5d7050 is a usb stick.

On my machine I sometimes have to put the stick in and out of the various usb slots to have it listed.

Once you have a listing from lsusb then use sudo ifup wlan0

All the ebst
Bob

---

