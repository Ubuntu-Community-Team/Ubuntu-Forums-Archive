---
title: "wire less routers not recognized by ubuntu 10.04."
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2010-06-23
Hello All

This post may appear else where under different miss leading titles. 

A few weeks ago my HP lap top's wireless connection was fine with Ubuntu 9.10. I installed updates a few days before Ubuntu 10.4 came out. Thats when the different wire less routers ( mine and the 3 or 4 others in the neighborhood disappeared form the wireless pull down menu. I have not been able to connect to my Netgear router since. (I could and can connect with a wire.)

I tried a reinstall of the router. (Reinstalling the WEB Key) No luck.

So I installed Ubuntu 10.4 hoping that would recognize the routers again. No luck.

One of the local Linux experts at wlug said I should report the bug. Sadly I was unsuccessful in navigating the web site he suggested. But I thought others would make the report any way. I did see similar post at the Ubuntu web site for bugs. I thought the next update would include the fix. 2 or 3 updates later my computer does not recognize the router.

I installed another update just before posting the note. Now the wire less icon on the panel is gone. 

I have very limited experience with computers. Please help.


gordon33

---

### Post by 10snoopy1 on 2010-06-23
> **gordon33 said:**
> Hello All

This post may appear else where under different miss leading titles. 

A few weeks ago my HP lap top's wireless connection was fine with Ubuntu 9.10. I installed updates a few days before Ubuntu 10.4 came out. Thats when the different wire less routers ( mine and the 3 or 4 others in the neighborhood disappeared form the wireless pull down menu. I have not been able to connect to my Netgear router since. (I could and can connect with a wire.)

I tried a reinstall of the router. (Reinstalling the WEB Key) No luck.

So I installed Ubuntu 10.4 hoping that would recognize the routers again. No luck.

One of the local Linux experts at wlug said I should report the bug. Sadly I was unsuccessful in navigating the web site he suggested. But I thought others would make the report any way. I did see similar post at the Ubuntu web site for bugs. I thought the next update would include the fix. 2 or 3 updates later my computer does not recognize the router.

I installed another update just before posting the note. Now the wire less icon on the panel is gone. 

I have very limited experience with computers. Please help.


gordon33






Try booting from a 9.04 disc and installing 9.04 if one of these doesn't work:

GO to: System -> Administration -> Update Manager

Click on where is says "Settings..."
Now select all of the Lucid options on the "Updates" tab.

Reload and if that doesn't work, go to System -> Administration -> Hardware Drivers

If there are any drivers, install one of the latest or recommended for each piece of hardware that has a driver available.

I think you should also try making sure you have the wireless card in or try another wireless card. If you say this is a laptop 5 years old or newer, it most likely has integrated wireless.

Try using one of the supported UBuntu USB wireless cards and see if it works. 

As a last resort, I would try using 10.10 by going to Applications -> Accessories -> Terminal

In Terminal, type in


```
sudo update-manager -d

```

It will ask for your password and open update manager. If no upgrade is found, make sure it is set to Normal Releases on the Updates tab under Settings...
Reload and install.


Hope this works, 

10snoopy1

---

### Post by 10snoopy1 on 2010-06-23
Also, try having no security on your router password wise. Do this only if the Wireless option is showing up under connections.

---

### Post by gordon33 on 2010-06-24
Hello 10snoopy1

The HP G60T lap top is about a year old.

I down loaded Ubuntu 9.10 I did not have a copy of 9.04.  The Wireless light stayed red when connected to 9.04.  

When connected to 10.04 it turned blue.  Still no go.

The Lucid options on the "Updates" tab were selected.  No change after rebooting.

Nothing shows in the box when I get to Hardware Drivers.

Could not find "Normal Releases" on the Updates tab under Settings.

giordon33

---

### Post by gordon33 on 2010-06-29
SEE
[http://ubuntuforums.org/showthread.php?t=1520352](http://ubuntuforums.org/showthread.php?t=1520352)

---

