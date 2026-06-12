---
title: "connecting to neighbors wifi but not mine"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by newguy1 on 2010-01-08
Hi I am a newbie trying to setup wifi using 9.10 on a compaq nx9010 . The driver is activated for the broadcom 4320 rev 2 chipset. the wifi light is on.I can connect to my neighbors's unsecured network, but not mine which is using personal WPA2 security.

I am using a lynksys Wireless-N Broadband Router WRT160Nv2
[FONT=Arial][SIZE=2][FONT=Arial][SIZE=2] 
[/SIZE][/FONT][/SIZE][/FONT]I have installed WICD and removed the gnome network manager

WICD tries to validate authentication which fails. then it tries to obtain an ip address which fails. finally it says: CONNECTION FAILED: UNABLE TO GET IP ADDRESS". meanwhile it is showing the wireless network at 100% signal. 

last nite tried changing wifi channel, changing to WEP, installed and tried WPASUPPLICANT and WPA_GUI. Unfortunately , nothing worked. The wifi controller was able to assosciate with the network but could not authenticate. I'm wondering if the passphrase that I type in on the computer is somehow being turned into a hexidecimal or something so that it does not match what the router has as the pass phrase. 
 
I would appreciate any help. thank you.

---

### Post by llawwehttam on 2010-01-08
Not sure how to fix this on the linux end. I'm not to good with the networking front on linux but why don't you remove the password on your router but set dhcp to only assign ip addresses to your computers MAC addresses the you can connect but no-one else can.

Just to warn you broadcom have never mixed well with linux.

---

### Post by Grenage on 2010-01-08
While I haven't seen this problem before; I would just like to warn the OP that MAC locking as the sole form of defence, is about as secure as a paper safe.

---

### Post by newguy1 on 2010-01-08
> **llawwehttam said:**
> Not sure how to fix this on the linux end. I'm not to good with the networking front on linux but why don't you remove the password on your router but set dhcp to only assign ip addresses to your computers MAC addresses the you can connect but no-one else can.
 
Just to warn you broadcom have never mixed well with linux.
 
Can you give me more detailed instructions on how to do this. Sorry to be dense but I'm new at this.

---

### Post by Darce on 2010-01-08
> why don't you remove the password on your router but set dhcp to only assign ip addresses to your computers MAC addresses the you can connect but no-one else canYour talking about MAC address filtering, which is next to useless as a security measure !

Message to OP : Only do this if your happy to share your network and Internet access with all your neighbours and anyone that happens to be driving down your neighbouring streets.

Can I ask why your running WICD ?

---

### Post by newguy1 on 2010-01-08
> **Darce said:**
> Your talking about MAC address filtering, which is next to useless as a security measure !
 
Message to OP : Only do this if your happy to share your network and Internet access with all your neighbours and anyone that happens to be driving down your neighbouring streets.
 
Can I ask why your running WICD ?
 
I tried the gnome network manager which also did not work. another troubleshooting guide recommended that I try WICD so I did.

---

### Post by Darce on 2010-01-09
Try going back to basics and plug your wired network port back to your router. I assume this is how you set your router up in the first instance. Now you can log into your routers control panel double/triple check your settings.
If all else fails, disable encryption/security on the router, and try again just to see if you can make a connection at all. But PLEASE DON'T leave it like that ! If you can connect to your neighbours, your neighbour will be able to connect to yours !!!!!!

Cheers,

Tim

---

