---
title: "Internet Issues"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by TheGimpAddict on 2010-10-26
Hello All,

Yesterday I installed Ubuntu in dual boot with Windows 7, and the internet worked fine from the beginning. However, today my wired connection no longer works in Ubuntu, but it does work in Windows, which mean there is nothing wrong with my internet service. If you people could help me through the process of getting it back up and running that would be cool.

Thanks,
Daniel

---

### Post by MrOzBarry on 2010-10-26
Did you install any updates or change any settings?  And how do you connect to the internet?  Through an external router, or from a connection directly from your computer?
Regardless of how you connect, do you get any option in the ubuntu network manager on the desktop?  If so, right click -> Edit Connections
Check to make sure it's getting the ip right (DHCP or manual?), and that you have any of the proper security switches on.

I can't think of any update that would change your network settings without your consent, and by windows connecting properly, I'd assume it's a linux software setting.
Do you have to use a third-party driver for your ethernet card?

Take care,
-Oz

---

### Post by TheGimpAddict on 2010-10-26
> **MrOzBarry said:**
> Did you install any updates or change any settings?  And how do you connect to the internet?  Through an external router, or from a connection directly from your computer?
Regardless of how you connect, do you get any option in the ubuntu network manager on the desktop?  If so, right click -> Edit Connections
Check to make sure it's getting the ip right (DHCP or manual?), and that you have any of the proper security switches on.

I can't think of any update that would change your network settings without your consent, and by windows connecting properly, I'd assume it's a linux software setting.
Do you have to use a third-party driver for your ethernet card?

Take care,
-Oz

I'm connected to the internet via a CAT6 cable. I'm on DHCP auto. I'm pretty sure that I didn't update drivers or anything that would have made me unable to connect to the internet. I put my computer on suspend at about 11:00 pm and when I got home a few hours ago it simply wouldn't connect.

---

### Post by Guilherme S Silva on 2010-10-26
Same with me! Did a fresh install of 10.10. Internet worked for a while now ... nothing! ifconfig dysplays eth0. lspci shows ethernt controller Intel 82578DC.
It works on and off. Thanks!

---

### Post by irv on 2010-10-26
> **TheGimpAddict said:**
> I'm connected to the internet via a CAT6 cable. I'm on DHCP auto. I'm pretty sure that I didn't update drivers or anything that would have made me unable to connect to the internet. I put my computer on suspend at about 11:00 pm and when I got home a few hours ago it simply wouldn't connect.

First, has the computer been restarted or powered off and back on again?
Next, right mouse click on the network icon in the panel and select Network information, and post it here like this:
[ATTACH]173580[/ATTACH]
You can do this by going to Applications> Accessories> Take Screen Shot.

---

### Post by TheGimpAddict on 2010-10-26
> **irv said:**
> First, has the computer been restarted or powered off and back on again?
Next, right mouse click on the network icon in the panel and select Network information, and post it here like this:
[ATTACH]173580[/ATTACH]
You can do this by going to Applications> Accessories> Take Screen Shot.

If you're talking about where it says "Connection Information", I can not access it for some reason. Probably because I have no connection.

---

### Post by night_fox on 2010-10-26
Go to the terminal and type 
> ifconfig

post the results.

Also, possibly 

> lshw -C network

---

### Post by TheGimpAddict on 2010-10-26
> 
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:64:45:e6  
          inet6 addr: fe80::92e6:baff:fe64:45e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4277 (4.2 KB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr (IP ADDRESS)  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2176 (2.1 KB)  TX bytes:2176 (2.1 KB)

These are my results for ifconfig.

---

### Post by night_fox on 2010-10-26
try

```
sudo dhclient eth0
```

if that doesn't work, post the output of

```
dmesg | tail
```

---

### Post by Iowan on 2010-10-26
Right-click Network Manager and verify Networking is enabled. For some reason, that tends to get turned off. [Here]("http://ubuntuforums.org/showthread.php?t=1505217") is another thread that might be useful. From a terminal (Applications>Accessories>Terminal) you can try **sudo dhclient eth0**, but I suspect you'll see something like "...no DHCP offers ... sleeping"

---

### Post by faheemezani on 2010-10-26
> **TheGimpAddict said:**
> These are my results for ifconfig.

Looks fine but where is the IP address? Type in:

```
dhclient eth0
```

See if you get the IP address now.

---

### Post by TheGimpAddict on 2010-10-26
I actually did get an IP, I just didn't share it for security lol.

---

### Post by TheGimpAddict on 2010-10-26
When I ran sudo dhclient eth0, it told me that nothing was received and that it was sleeping.

---

### Post by night_fox on 2010-10-26
1) I don't blame you for not sharing your ip.
2) If you got an ip, theres no point in running dhclient.
3) excuse me, i'm drunk.
4) what happens if you ping your router, or google?

---

### Post by TheGimpAddict on 2010-10-26
> **night_fox said:**
> 1) I don't blame you for not sharing your ip.
2) If you got an ip, theres no point in running dhclient.
3) excuse me, i'm drunk.
4) what happens if you ping your router, or google?

I know it might me an extremely stupid question, but exactly how do I ping my router?

---

### Post by TheGimpAddict on 2010-10-26
Bump

---

### Post by Iowan on 2010-10-26
> **TheGimpAddict said:**
> Bump
Once/day is generally adequate for bumps - 30 minutes is a tad impatient... :)
I *suspect* your IP address will be in the 192.168.x.x private subnet. Most routers claim the .1 address - although some use .254 (eg. 192.168.1.1 or 192.168.0.254)... the router documentation should give a default address. This is usually the address you use to access the router setup page.

---

### Post by TheGimpAddict on 2010-10-26
> **Iowan said:**
> Once/day is generally adequate for bumps - 30 minutes is a tad impatient... :)
I *suspect* your IP address will be in the 192.168.x.x private subnet. Most routers claim the .1 address - although some use .254 (eg. 192.168.1.1 or 192.168.0.254)... the router documentation should give a default address. This is usually the address you use to access the router setup page.

So what do I need to do with my IP address after I find it?

---

### Post by irv on 2010-10-27
One thing to check. goto: System> Preferences> Network Connections. Then go to the "Wired" tab select the "Auto eth0" Then the "Edit" Button.
Make sure there is a "check mark" in the box by the "connect automatically".
[ATTACH]173637[/ATTACH]  [ATTACH]173638[/ATTACH]

---

### Post by TheGimpAddict on 2010-10-27
[LEFT]Should I just reinstall Ubuntu? Do you think we could figure out a way to solve this or would it just be easier to start over?
[/LEFT]

---

### Post by irv on 2010-10-27
> **TheGimpAddict said:**
> [LEFT]Should I just reinstall Ubuntu? Do you think we could figure out a way to solve this or would it just be easier to start over?
[/LEFT]

If this is the only problem, I wouldn't do a reinstall yet.
You might want to open a terminal and type:
```
ping 192.168.1.1
```
or
```
ping 192.168.0.1
```
I would start here to see if you are seeing your router.
You do have a router don't you?
This will tell us if you are seeing your router.
I know these are default ip address' of a Dlink and a Linksys routers.
If you have something else we will have to determine that ip address.
I won't be at my computer for a while because I have a meeting tonight so maybe someone else could jump in here and help. Will be back later.

---

### Post by TheGimpAddict on 2010-10-29
Good news everyone, my internet started to work again so everything is fine now. :D Thanks for all the help anyways.

---

### Post by irv on 2010-10-29
> **TheGimpAddict said:**
> Good news everyone, my internet started to work again so everything is fine now. :D Thanks for all the help anyways.

What was the problem? Was your problem your Internet and not the computer? Would be nice to know. Also just mark this thread solved.
[ATTACH]173909[/ATTACH]

---

