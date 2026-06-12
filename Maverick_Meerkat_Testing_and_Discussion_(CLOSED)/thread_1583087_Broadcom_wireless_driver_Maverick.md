---
title: "Broadcom wireless driver Maverick"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by AlanR8 on 2010-09-27
Just to advise.

Installed Maverick on my HP Mini over the weekend and was HUGELY disappointed by the wireless network performance from the Broadcom driver included within the release. 

Internal network transfers were horribly slow and the Net was sporadic to say the least.

This morning I've reinstalled Lucid and all is well again. That said, the Broadcom card is about half as fast as the wireless card in my Sony Vaio laptop.

---

### Post by roberj13 on 2010-09-28
That's interesting because I was having problems with the Broadcom STA drivers on Lucid, it was very intermittent. Ever since upgrading to Maverick beta, I haven't had a single problem. :::crosses fingers:::

I almost gave up on getting it to work and went with a usb stick or card, but now I don't have to. :D

---

### Post by TBABill on 2010-09-28
+1 - STA driver working great on my upgrade from 10.04 to 10.10. I upgraded tonight and the system was flawless, including Broadcom driver.

---

### Post by cariboo on 2010-09-28
It really depends on what chipset revision your netbook has. Some of the newer HP mini use the b43 driver, while the older versions use the wl driver. To find the revision number open a terminal and type:

```
lspci | grep Network
```

the result should have the revision number at the end of the line:

```
lspci | grep Network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

As you can see my chipset is rev 01.

To the others in this thread, I've been running UNE since alpha 1, The wl driver has worked with zero problems, since the original install.

---

### Post by roberj13 on 2010-09-28
Just for reference for others, mine is...

BCM43225 802.11b/g/n (rev 01)

---

### Post by Megaptera on 2010-09-29
I know your's is HP but ...You could try this for Dell/broadcom. Says Karmic & Dell Mini but works on Dell Inspiron in Lucid & Maverick too:

[http://www.ubuntumini.com/2009/11/br...in-karmic.html](http://www.ubuntumini.com/2009/11/br...in-karmic.html)

Don't forget the re-boot step.

---

### Post by davrosuk on 2010-10-01
I've checked my mini 10 and my wireless is about 50% slower in Maverick than Lucid. I even rebuilt 10.10 from the latest ISO to be sure.

Any one else with this?

---

### Post by zapp42 on 2010-10-01
I see this, too, with 10.10 on my MacBook Pro.

I found the following two things to try in Launchpad. The first one improved things for me. I did not try the second, yet.

1. sudo iwconfig ethX power off # X = your wifi adapter
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340)

2. On the kernel cmdline:
    [B]intel_iommu=off
[http://fedoraforum.org/forum/showthread.php?p=1366578](http://fedoraforum.org/forum/showthread.php?p=1366578)

HTH,
Z.
[/B]

---

### Post by AlanR8 on 2010-10-03
And the same on my Vaio now. Yesterday I suspected I was having Internet connection issues. Turned out it was wireless card issues. 

Have "Upgraded" to Lucid and all is well.....

---

### Post by cariboo on 2010-10-03
> **AlanR8 said:**
> And the same on my Vaio now. Yesterday I suspected I was having Internet connection issues. Turned out it was wireless card issues. 

Have "Upgraded" to Lucid and all is well.....

Did you at least create a bug report before re-installing? If the devs don't know about a problem, they can't fix it.

---

### Post by Junior_Sampa on 2010-10-03
Dear colleagues,

I'd like to verify with you all if the behavior I get with my laptop could be checked in your machines.

I have one Dell Inspiron 1564 with Broadcom BCM4312 according to bellow:

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

The problem is related to the wireless driver STA. When I'm connect to AC power supply, the transfer rate in internet is correct (my full connection). If I use it on battery, the connection is still alive but with about 10% from my full connection (tested in speedtest website).

Did you check something like this?

Thank you.
Junior

---

### Post by cariboo on 2010-10-03
I've been using the STA driver + Maverick/Unity for the last 6 months, both on A/C power and battery, there is no speed difference, whether my own access points or other ap's while out and about.

Chipset is BCM4312 rev. 01

---

### Post by Nanuq on 2010-10-04
> **Junior_Sampa said:**
> 
I have one Dell Inspiron 1564 with Broadcom BCM4312 according to bellow:

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

The problem is related to the wireless driver STA. When I'm connect to AC power supply, the transfer rate in internet is correct (my full connection). If I use it on battery, the connection is still alive but with about 10% from my full connection (tested in speedtest website).


Exact same problem here. Dell Mini 9, and this:

[   16.680732] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 

Fine on AC, dodgy on battery.

Advice?

---

### Post by davrosuk on 2010-10-04
> **Nanuq said:**
> Exact same problem here. Dell Mini 9, and this:

[   16.680732] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 

Fine on AC, dodgy on battery.

Advice?

Mini 10. Same issue. Its power saving that's causing it. To get full speed whilst on battery:

```
sudo iwconfig eth1 power off
```

---

### Post by Junior_Sampa on 2010-10-04
Hi, thanks for your reply.

Could you explain the idea of this command?
"sudo iwconfig eth1 power off"

Do you know if there is any bug related in launchpad? This is important to assure the failure is going to be correct.

Thank you.
Junior

---

### Post by davrosuk on 2010-10-04
That command tells the wireless card not to use power saving - I know it looks as if its switching the power off, but I can assure you it isn't!

I haven't logged a LP bug nor even searched as yet. The broadcom driver included with 10.10 is the latest one available, and although I haven't checked, I assume the problem is with that.

---

### Post by Junior_Sampa on 2010-10-04
Now it's clear.

Is it necessary to enter with this command every boot or it's saved in config file? If it's stored, where is the config file?

Thank you for your support.

Junior

---

### Post by aydee on 2010-10-04
Hi all,
I have a different problem! I can dectect wifi networks and start connecting but after 2 mins of trying to connect, it STOPS. I know it is not the wifi network as I can connect in **BLEH** windows! I have a dell latitude D630 with a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card and the driver is bcmwl5.inf

Thanks,
Aydee

---

### Post by davrosuk on 2010-10-04
> **Junior_Sampa said:**
> Now it's clear.

Is it necessary to enter with this command every boot or it's saved in config file? If it's stored, where is the config file?

Thank you for your support.

Junior

The setting is not saved. My best guess for how to make such a change 'permanent' would be to add the line (minus sudo) to /etc/rc.local

I say best guess, as I can't say for sure what the best way is.

---

### Post by Brownout on 2010-10-06
> **Junior_Sampa said:**
> 
Do you know if there is any bug related in launchpad? This is important to assure the failure is going to be correct.


[LP #651008]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008") seems related.

> **davrosuk said:**
> The setting is not saved. My best guess for how to make such a change 'permanent' would be to add the line (minus sudo) to /etc/rc.local
It won't work, you need to run it every time the NIC is brought up or switch to batteries. Not a real solution, just an ugly workaround.

---

### Post by cariboo on 2010-10-06
> **aydee said:**
> Hi all,
I have a different problem! I can dectect wifi networks and start connecting but after 2 mins of trying to connect, it STOPS. I know it is not the wifi network as I can connect in **BLEH** windows! I have a dell latitude D630 with a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card and the driver is bcmwl5.inf

Thanks,
Aydee

Have you tried the Linux driver, instead of using ndiswrapper?

---

### Post by rorschachwalter on 2010-10-06
> **cariboo907 said:**
> Have you tried the Linux driver, instead of using ndiswrapper?

I have the same problem (wireless tries to connect to networks, then simply fails), using the driver in the restricted drivers manager.

The same card worked in Lucid.
I can only connect to the first wireless network that this machine connected to since install.
The card can see the networks it is supposed to see, detect security settings, etc.

Is there perhaps some configuration file which is not being handled properly? For instance, in /etc/hosts, even when I am not connected to any network, I am given a 192.168... number which it says in a comment was determined by NetworkManager.

---

### Post by cariboo on 2010-10-06
If you have a default setup, the ip address is being assigned by your router, usually in the 192.168.X.X range. Can you connect without security turned on?

---

### Post by 23dornot23d on 2010-10-06
Wireless seems to have got messed up with the latest updates for me too .....
not sure how to isolate whats done it ..... 
but I loaded a lot of updates today ....

Wireless worked ok yesterday though ....... seems its just switched it off for me ....
 
I have just clicked on the wireless icon in the top bar and it seems ok .... its turned off from a clean start .....

---

### Post by Mills00013 on 2010-10-06
I love everyone in this thread. Thank you to EVERYONE. I'm on a 4,1 Macbook Pro, and this fixed the issue for me. I couldn't figure it out and it's been driving me nuts for days.

0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)

"sudo iwconfig eth1 power off" fixed it for me. Time to make a keystroke.

---

### Post by rorschachwalter on 2010-10-07
I can connect with or without security, but only to the original network this laptop connected to after install. I'm thinking that I should submit this as a bug, since the card worked in Lucid. It's likely not a "help forums" issue. Still, if there's some work around until the issue is fixed (if ever?), that'd be useful information.

I tried commenting out the 192.168 address in /etc/hosts, then rebooting the card to see if it would fix anything. Still not working though.

---

