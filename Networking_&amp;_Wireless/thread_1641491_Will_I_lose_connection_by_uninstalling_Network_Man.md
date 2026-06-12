---
title: "Will I lose connection by uninstalling Network Manager?"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by demonboy on 2010-12-09
Hi,

In the Ubuntu 10.10 documentation it suggests Wicd Network Manager as an alternative to the native Network Manager. However the install instructions suggest removing Network Manager first before installing Wicd. 

Surely this doesn't make sense, does it? If I uninstall Network Manager first will I not then lose my internet connection in order to apt-get Wicd?

---

### Post by 73ckn797 on 2010-12-09
Using Synaptic select Wicd for installation then Network Manager to be uninstalled. It will download Wicd first then make the changes properly. I have done this on every install across 4 computers.

You will have to configure the connection but in most cases it will see available wireless connections or wired connection. I have actually gone back to Network Manager in 10.04 on a desktop unit because on restarts Wicd would not always connect to my wired Internet.

You could also install Wicd and leave NM alone but you would have to go to System/Preferences/Startup Applications and disable NM on the next boot.

---

### Post by demonboy on 2010-12-09
> 
I have actually gone  back to Network Manager in 10.04 on a desktop unit because on restarts  Wicd would not always connect to my wired Internet.


Interesting. For me Network Manager plays up every time there is some kind of update. It never wants to connect automatically, which I have to do manually, and since reinstalling 10.10 after testing it I have once again the recurring problem of only being allowed to be either on my Broadband connection or on my wireless LAN, but never both. I was hoping Wicd would be intuitive enough to get round these problems.

I've had a look in Synaptic and there are loads of instances that say Network Manager. I'm a Linux newb so I really don't know what I should be ticking and unticking in Synaptic in order to uninstall Network Manager. I have:

network-manager-gnome
network-manager
lots of libnm's
network-manager-pptp

and so on. WIth your comments and with me not knowing what the hell I should be ticking in Synaptic I wonder if I should leave it all alone and try and work out my current problems.

---

### Post by 73ckn797 on 2010-12-09
I would only install Wicd and disable NM like I mentioned. NM will still be there but only disabled. If you have problems with Wicd you can go back into System/Preferences/Startup Applications and disable Wicd and re-enable NM.

To remove NM you would only need to select "network-manager" for complete removal and all other dependencies would be removed. The same applies to installing Wicd, only select "wicd" and all necessary dependencies will be installed with it.

My problems may only be related to my hardware. Wicd is working flawlessly on several other computers I have.

---

### Post by demonboy on 2010-12-10
Thanks for that, I'm going to have a play with this next week. Cheers.

---

