---
title: "Knetworkmanager broken after upgrade to Jaunty ?"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by Tilex on 2009-04-25
Hi !

After I upgraded my system (Intel Dual core 64) to Jaunty, my Knetworkmanager icon disappeared from the menu and also, it would not load on startup as it usually did.

So I re-added the icon in my menu editor (with command: knetworkmanager) and it worked fine.

I then re-upgraded my system (because I had 2 upgradable packaged, network-manager-kde and something else), rebooted my system, and knetworkmanager stopped working.

I uninstalled network-manager-kde and re-installed an older knetworkmanager and it works.

Why isn't the new package working for Jaunty ?  Any thought ?
Thanks !

---

### Post by angelillo on 2009-04-27
network-manager has been replaced in Jaunty by the "Network manager plasma widget", which you can add to your panel. See the [what's new section on Kubuntu web]("http://www.kubuntu.org/news/9.04-release") for more info.

---

### Post by Pete051 on 2009-04-27
It doesn't seem to work, exits with an "Setting '802-1x' is empty, discarding" error, only way I can connect is through the ethernet :(
Pete

---

### Post by Tilex on 2009-04-27
> **Pete051 said:**
> It doesn't seem to work, exits with an "Setting '802-1x' is empty, discarding" error, only way I can connect is through the ethernet :(
Pete

Sorry about that.

I had purged the new knetworkmanager before re-installing the old package that I'd found.

My whole system was broken because of the upgrade to Jaunty so I just re-installed everything and everything is fine now. I took me about 3 hours to put my system back to the same customized state as it was though.

---

### Post by cytutchi on 2009-06-07
Hi

Because i am a bit of a newbie can you please tell me what did you do to fix this? Because i am having the same issue. Knetwork manager seems to work only with etherent or if wireless is open.
If there is a WPA Personal security it doesnt work at all.
i opened knetowrkmanager through konsole to see and i also saw:
  Processing Setting '802-1x'
  Setting '802-1x' is empty, discarding
and then nothing! :(

Also its wierd because when i click on the netowork that i want to connect, it seems that it completly ignores my action and in console i see this:
Activate Connection /org/freedesktop/NetworkManagerSettings/Connection/2 on Device /org/freedesktop/Hal/devices/net_00_12_f0_6e_43_7e

So i think it could be the same problem.
Do you have any idea how to fix this?? ..or should i start a new tread?

Thank you in advance

---

### Post by cytutchi on 2009-06-07
p.s. in my previous post when i said only went "wireless is open" i ment with no security.

---

### Post by Tilex on 2009-06-07
Hi,

In KDE 4.2, it's a widget that controls the network.  The widget is called Network Management, so you should right-click on your taskbar, "Add widget", and choose the Network Management one.

Hope you're using KDE 4.2 !

Alex

---

### Post by SuperSonic4 on 2009-06-07
I simply installed wicd over it, seemed much easier overall

---

### Post by cytutchi on 2009-06-18
Thenx a lot for the replies n help

Network Management widget seems to work just fine with an open network...I'll try it with the WPA at home n will let u know for the results but seemed pretty fast n steady so i think I'll be using that instead.

Thenx again

---

