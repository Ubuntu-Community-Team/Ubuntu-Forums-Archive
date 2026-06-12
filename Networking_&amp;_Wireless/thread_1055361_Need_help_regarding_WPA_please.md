---
title: "Need help regarding WPA please"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by switchover on 2009-01-30
Hi,
Thought i'd jump back into the ubuntu world with version 8.10, a while ago I used version 7. Okay so I used wubi to install ubuntu 8.10. Eventaully got the Netgear WG111T adapter to work (even though  drivers have to be uninstalled and reinstalled after restart) however  WPA2 Personal is not available from  the drop down list, even though I manually added the wireless network previously.

I understand there is something called wpa-supplicant, but I don't understand how this is installed. Any help please would be greatly appreciated.

Thanks

---

### Post by Coreigh on 2009-01-30
```
sudo apt-get install wpasupplicant
```
From the command line, or you can find it in synaptic and maybe add and remove programs.


There is also a package called 'wpagui' which sounds like it is a graphical interface for wpasupplicant. I have not used it though.

From the command line you can always use the -s option with apt-get to do a 'dry run' to see what will get installed or removed. i.e.
> sudo apt-get -s install <packagenames>

---

### Post by switchover on 2009-01-30
Thanks. I'll give it a try and let you know what the outcome is.

---

### Post by switchover on 2009-01-30
Right once, I enter the first command you mentioned, I get the following:

> Reading package lists...Done
Building Dependency tree
Reading state information...Done
wpasupplicant is already the newest version.
0 upgraded. 0 newly installed, 0 to remove and 0 not upgraded.

However, it's WPA2 is still not on the list

---

### Post by switchover on 2009-01-31
I found [THIS]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") guide. I'll give it a try.

ALso installed ubuntu on my laptop and on second restart the built in intel wireless adapter was recognized and WPA2 was picked up straight away.

---

### Post by kevdog on 2009-01-31
wpa_supplicant (if you install it) will not change the behavior of network manager at all (since it uses a library of this program). wpa_supplicant is needed if planning on using WICD or making a manual connection at the command line.  You could troubleshoot your wireless connection using the command line manually to see in which part of the process your connection is failing.  You them might get a good idea of what is going on!

---

