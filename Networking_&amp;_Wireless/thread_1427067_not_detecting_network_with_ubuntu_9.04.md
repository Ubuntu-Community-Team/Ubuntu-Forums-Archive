---
title: "not detecting network with ubuntu 9.04"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Gatorade on 2010-03-11
ok, here's my situation, I'm trying to get my friend's laptop(acer travelmate 2200) to connect to his wireless network. I just installed a new hard drive and installed a dual boot windows xp/ Ubuntu 9.04 setup.

His laptop still connects fine with the old hard drive with windows XP installed, so I know the hardware is working.

when I click on the network manager , however, I don't see anything.
Normally , I'd just hit the network manager and I'd see the available connections , but on this laptop I'm not detecting any.

can anyone help me to diagnose this problem?

The only thing I can think of , is that Ubuntu doesn't have the proper drivers needed for the wireless card in the laptop. But I don't know how to go about checking this since whenever I've done this before it's always just worked automatically.

---

### Post by PRC09 on 2010-03-11
You can check for any drivers under System > Admin > Hardware Drivers and if it is there try and activate from there.....

You can also try the following....

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network)

---

### Post by Gatorade on 2010-03-11
thanks, I'll check it out and post back my results.

---

### Post by Gatorade on 2010-03-11
ok, I'm still having trouble.

it seems that Ubuntu isn't detecting the hardware.


this is what I tried

4.1.2. Non-recognized Card

    * Some devices are not recognized by the OS upon insertion. [Needs expansion.]
         1. If card doesn't show up immediately try these steps: 

    *

      Run the following command. Hopefully you'll get some output about the device.

        sudo pccardctl ident

IconsPage/IconExample48.png

    *

        Socket 0:
          product info: "Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN Reference Card", "00"
          manfid: 0x0271, 0x0012
          function: 6 (network)

      If you get no output then the memory on the card cannot be read. Now we need to open a configuration file and add this information to it:

        gksudo gedit /etc/pcmcia/config.opts


I opened a terminal and typed in the code , but it said no product info available.
how do I open a configuration file to do the next step?

---

### Post by PRC09 on 2010-03-11
Sorry I dont have anything with an Atheros card to check the following links with but when searching I found this,as it looks like you have an Atheros AR5001 card so hope this will help.......

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by Gatorade on 2010-09-15
still looking for some help here. if anyone can offer some suggestions/ advice I'm all ears.

---

