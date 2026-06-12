---
title: "Weird wireless problem"
date: 2006-02-16
forum: Networking &amp; Wireless
---

### Post by RonJohnson on 2006-02-16
I'm having this odd wireless problem that I can't figure out. I have a D-Link DWL-G630 card in my laptop. Ubuntu recognizes it without a problem. If I shut my laptop down for any amount of time though the card it unable to find my AP. I disable and then enable the card which doesn't work. If I do dhclient ath0 I get  no dhcpoffers. Drives me crazy!!

I have learned that if I just do a reboot it works perfectly. So that is what confuses me so badly. Why does my card not work right off the bat but a warm boot fixes the issue?

Any ideas?

---

### Post by Lambert on 2006-02-16
>  If I shut my laptop down for any amount of time though

Elaborate on this statement more. Do you mean suspend or hibernate?

Just a guess but sounds like pcmcia slot is powered down and when you awake pc, there's no script restarting the networking activity . 

Try this to see if this brings network activity to life instead of rebooting.

```
sudo invoke-rc.d networking restart
```

---

### Post by dsmoney on 2006-02-16
Also, you might try

sudo iwconfig 'device name' key open

---

### Post by RonJohnson on 2006-02-16
[QUOTE=Lambert]Elaborate on this statement more. Do you mean suspend or hibernate?[/QUOTE]

I don't mean suspending or hibernating. I am completely shutting my laptop down. Could be for 5 minutes or it could be for 5 hours. When it first boots up the wireless card doesn't get the connection. Once I do the warm boot it works just fine. :-k

I will try the sudo iwconfig "device name" key open on the next reboot and let you know the results.

---

### Post by RonJohnson on 2006-02-20
Sorry it's been awhile since my last post. I tried both the of the following:

sudo invoke-rc.d networking restart - running this did the same thing as usual... appears that it's trying to get a ip addy from the dhcp server yet is unable to.

sudo iwconfig "device name" key open - I forget what happened when I ran this as it was a few days ago. I do know that it didn't fix the issue.

So I am left to booting up the system and as soon as I see the login screen for Gnome I am forced to hit reboot. After that the wireless connection works normally.

Any other ideas? I'll give a week before I reformat the drive as I reckon it could be something I installed since I can't remember when the problem started.

---

