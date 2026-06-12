---
title: "Network works, but can't access anything inside lan."
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by Gfurst on 2013-07-14
Hi guys, first of all, this isn't Ubuntu specific, so sorry about that, but it's one of the best places to get support.

So here's the deal, my network works as expected, i can access internet, open ports, everything else. 
I use a wireless lan router that connects directly with PPPoE through another wi-fi bridge to ISP.

The problem is that i cannot access any other thing inside the lan, I've tried pinging but says no route.
The weird part is that it used to work not so long ago. I was able to access different computers file system and even used remote control on android.
Not only the sharing part is important, but being able to control my Media Center with my phone.

Note:
My router is a belkin something, very limited router.
I've set manual IP addresses to both computers, but not to android.
Also to SSID is set to hidden, but all devices connect with no problems.
I've recently changed my network setup, but i couldn't connect before either, don't think it is relevant.

Thanks

---

### Post by anspectrum on 2013-07-14
Please check if your LAN device (switch / WiFi Router) is not blocking ARP protocol.

Also check that you can communicate between devices directly i.e., bypassing any connecting device.

Seems to me plain networking issue and should not take much time to get resolved.

Cheers.

---

### Post by Gfurst on 2013-07-14
Just made few ping tests, its seems i can ping all devices from my ubuntu notebook and they respond.
Pinging from iMac i cannot reach notebook, but reach android randomly. From notebook, android will also be unreachable randomly.
Tried actually connecting via applications, remote transmission, ssh.

I've disable the hidden SSID feature, just in case it had something to do.
My router is pretty limited, its does not seem to have any blocking option. Its so bad its boring :-s
Attached is the screen cap of the menu.

Its worth mentioning that I've set the mac and the note to manual IP addresses for obvious purposes.
The router does not have a reserve IP feature, so I've set them manually and taken them off the DHCP range.

Anything i should try? Maybe the Ubuntu is blocking connections?

---

### Post by Gfurst on 2013-07-20
Hey still having problems with this, anyone care to help?

I've found something though...
In a different network, I was fiddling and found that i could reach my laptop from my android( remote transmission ans'tuff)
Then I've set ip to manual for consistency. I've set ip manual, gateway and DNS, all right, internet working greatly ip assign, contacting with router.

This however made my laptop unreachable, same scenario as before, manual ip is probably the cause.
In my other network, the iMac had manual ip all set up but had no problems being reachable, this is only happening in this ubuntu laptop.

I've kept searching, and similar cases were only solved with re-installation of the system, which is just too much.
Now I know about the manual ip being the cause of it there just must be some easier way.

Ps.. still i've left out the ip set to manual from the DHCP range,

---

