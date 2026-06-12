---
title: "Can or cannot bridge Wlan0 to VirtualBox?"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by X_Splinter on 2009-06-27
I am exhausted, I been searching all over the net and this forum.

Is there any functional way to bridge the wireless card to VirtualBox.

I installed BackTrack 4 on it but I cant use the wireless card on it.

Seens so easy in the crappy Windows why not in Ubuntu?

Is there anyone tried out with success???

Thanks for any information.

---

### Post by DGortze380 on 2009-06-27
> **X_Splinter said:**
> I am exhausted, I been searching all over the net and this forum.

Is there any functional way to bridge the wireless card to VirtualBox.

I installed BackTrack 4 on it but I cant use the wireless card on it.

Seens so easy in the crappy Windows why not in Ubuntu?

Is there anyone tried out with success???

Thanks for any information.

In the settings menu for your virtual machine, add a bridged network adapter, specify wlan0.

Should be that simple.

---

### Post by X_Splinter on 2009-06-29
> **DGortze380 said:**
> In the settings menu for your virtual machine, add a bridged network adapter, specify wlan0.

Should be that simple.

I did that already but is not working, something must be missing

---

### Post by X_Splinter on 2009-06-29
I reed this in Virtualization Mega treath

> VMWare

With VMWare networking is configured during the installation. Potential advantages of VMWare are:

   1. VMWare will automatically set up NAT, Bridged, and Host-only networking for you.
   2. VMWare will bridge WIRELESS cards. Do not use the any-any updates as they will likely break your wireless bridge.


So VMWare can do the job for me?

Where can I get a ubuntu package of it?

---

### Post by steppres on 2009-07-18
I've got a bridged connection working under VirtualBox, but its slow and drops out after about 15 minutes. I tested the machine on Windows XP host with bridged networking and its fine, stays up forever (in fact, I'm in it right now). It seems like this is an issue with either Ubuntu or Vbox under Ubuntu. I read in a different thread that changing your virtual adapter to the Intel/1000 might help, but I didn't see any changes. Poopy.

---

### Post by Josh1216 on 2010-01-15
Hi.. sorry to re-open this thread .. but "steppres" can you please tell me how you got the wireless n/w to work  in Ubuntu ? 

My host is XP SP3 and have installed Ubuntu 9.10 in bridged networking mode. When I log into Ubuntu I do not find any icon on the panel specifically for wireless network. All I can see an icon for wired network (eth0) . I also noticed that if I disconnect from my access point in the host, Ubuntu is also disconnected By no means I can now connect to my access point from Ubuntu independently. The only way now to get the internet back in Ubuntu is by connecting to access point from Win XP.

Thanks for your help.

---

