---
title: "Intrepid does not connect with WEP passphrase"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by cactaur on 2009-02-23
Hey, I just did a fresh install of Intrepid, over a Hardy install, and the wifi is killing me. My home network has a router with a WEP-encrypted passphrase. My network card is a D-Link DWL-G520, worked excellently with atheros drivers. Before the install, with Hardy, the computer connected just fine, and all of the other computers can connect to the network, but Intrepid is causing problems. When I select my network, I put in the passphrase and connect. The two green lights come on in the applet, and it says it's trying to get an IP address. However, after about twenty seconds, it prompts me with a password again, but this time it has a 40/128 WEP key, which is not what I put in. Even if I keep correcting it and putting in my passphrase it keeps doing it. This even happens when I edit the network entry in NetwworkManager. It has the 40/128 WEP key, and as much as I try to change it to use a passphrase, it reverts back to the key.

I've tried connecting via the command line, and I haven't had much luck there either. It worked once, and then dhclient started acting weird. The output was
```
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.0.197 on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPREQUEST of 192.168.0.197 on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received
No working leases in persistent database - sleeping
```

It seems like dhclient is getting the ip from the router, but isn't doing anything with it for some reason. This is really frustrating, and if anyone has some info on it, it'll really be great. Thanks!

EDIT: Oh, and there's no problem connecting to an unsecured network. When encryption gets involved, things get messy.

---

### Post by pdtpatrick on 2009-02-23
You have to enter the information your router provides. when you created your wep seucity key, you probably put your paraphrase in and clicked generate and it create about 4 sets of keys? Input the one that has the box next to it checked. 

I don't putting in your praraphrase is going to work unless you are using WPA.

---

### Post by cactaur on 2009-02-23
Well, the passphrase worked for all of the other releases of ubuntu, and all the windows machines also on the network also use that key. So I'm really hoping the problem isn't with Intrepid's WEP passphrase support, because there are still networks that use it; for one thing, it's easier to remember.

---

### Post by cactaur on 2009-02-25
So I tried updating my packages. This hasn't been fixed. Any idea what package it could be in?

---

### Post by tb87670 on 2009-02-26
I have the same problem, I keep typing in my proper WEP key and Ubuntu just refuses to accept it and asks for the key again. No one on this forum seems to be getting a straight answer to this problem.

---

### Post by cactaur on 2009-02-26
Well, I managed to find a workaround to it. The bug still needs to be fixed, but as of right now, you can use WICD, which worked for me, and now I'm online with wireless. (YES!)

[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

But anyway, I'm definitely gonna keep working on Launchpad to get this bug fixed. Turns out I managed to get the best of both worlds, I can switch between WICD and NetworkManager, and get my internet! Hope this helps for all others who have this problem, you don't have to go back to Hardy.

---

### Post by tb87670 on 2009-02-28
WICD still doesn't work with my MN-510, it doesn't even detect my device at all, only the ethernet port on the back of my PC. I'm to the point of giving up on Ubuntu and getting SUSE on my PC because I wasted so much of my time on this and gotten headaches over the past week over this.

---

### Post by Yashiro on 2009-02-28
I had similar issues with Hardy using WEP. WPA/2 worked fine. 
You should be using WPA2 if you can though. WEP is garbage now, really.
Suse and Fedora both use Network Manager too. I'm not sure you'd resolve any issues unless they have a 'later' version.

---

