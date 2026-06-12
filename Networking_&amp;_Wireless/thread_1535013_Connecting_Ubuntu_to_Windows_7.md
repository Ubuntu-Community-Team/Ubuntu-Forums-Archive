---
title: "Connecting Ubuntu to Windows 7"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by forsterb01 on 2010-07-20
Right, so, I have 2 computers, one running Windows 7 (and connected to my router wirelessly) and another running the latest Ubuntu Server version and I am just wondering, since I've already got the windows machine to share the internet connection via their LAN connection, how would I get the Ubuntu to use it?

Cheers for any help!

---

### Post by zorglubx on 2010-07-20
Make the ubuntu server use the internal interface on your windows 7 as gateway, and you're set, i would think.

---

### Post by forsterb01 on 2010-07-20
Ok, so, as someone who has almost no practical experience using Ubuntu, how would I do that?

---

### Post by pricetech on 2010-07-20
Start with a crossover cable between the wired connection on your Win7 box and the wired connection on you Linux box.  Windows ICS uses DHCP so your Linux box should pick up an IP from it and use it.

---

### Post by TBABill on 2010-07-20
I see you said "Ubuntu Server version" but do you just mean 64 bit? Is this just a regular PC you want to connect to your wireless router? Or are you really using it as an in-home server?
 
I assume you are using it as a standalone PC and want to connect to the Internet. If that's the case, there is an icon on the upper Gnome panel to the right. It's a network icon and you can left click it to see if 1) wireless is enabled and 2) if it detects your home network. It should display the name of your home network if Ubuntu is already configured for your particular brand/model of wireless network card. If not, you have other steps you'll need to take by providing a bit more explanation of what you are trying to do and what steps you have tried already.
 
If you do not have a wireless adapter on the card, have you tried plugging an ethernet cord directly from your computer to the router? Most wireless routers also have wired ports you can plug into. Mine is a Netgear and has 4 ports on the rear.
 
If you can provide a little more info about your setup and goal you'll get lots of experienced help here, along with instructions to help in the event you need to use the "terminal" to enter some commands to discover what hardware you have, which determines what steps have to be taken to enable the device.

---

### Post by forsterb01 on 2010-07-20
Unfortunately when I say Server Version I mean the 32-bit version that is designed for servers, the plan is to learn a little bit about server admin as I put this together, and as such is command line only. I've connected the two with an Ethernet cable, yet the Linux machine, when I check whether it has an Internet connection by using the "sudo apt-get update" command it cannot connect to any of the online locations.

Any other suggestions?

---

### Post by TBABill on 2010-07-20
My apologies for misunderstanding your issue. I'll have to defer to others with admin experience on server versions for this one. Best of luck though!

---

### Post by pricetech on 2010-07-20
Are you positive that ICS is set up on your Win7 box and the the firewall allows for it ??  I haven't used it in Win7, so I don't know how different it might be from previous versions.

Once you're sure that's working try pinging things, starting with your Win7 box.  Should be 192.168.0.1 if I remember right and MS hasn't changed it.

Then pings the Win7 box's default gateway which would be assigned by your ISP (probably).

Beyond that, try to ping one of the DNS servers your ISP assigns.

Give us the results of that and we'll go from there.

---

### Post by varunendra on 2010-07-22
Log on to your Windows machine, open command prompt and enter this command:
```
ipconfig /all > "%userprofile%\desktop\ipconfig.txt"
```
This will generate a text file named "ipconfig.txt" on your desktop. Post here its contents.

Similarly, log onto your ubuntu box, run & post the outputs of following commands:
```
ifconfig -a
```
```
sudo dhclient
```
```
route
```

Please mind that I'm not an expert in this, but the above outputs would help suggesting you a manual configuration through commandline.

---

