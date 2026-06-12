---
title: "Wireless WEP problems."
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by mpthrapp on 2011-04-11
I'm trying to connect to the wireless network at my dad's house but can't, it keeps asking for the password. The password has been entered correctly and I can connect to the network at my mom's place, and both use the same security.

Any help would be much appreciated.

---

### Post by mpthrapp on 2011-04-11
If any additional information is needed, I can supply it, I'm just still very new to Linux and I don't know what might be needed.

---

### Post by spinydelta on 2011-04-12
what happens when you try to connect?

Does it give you an error like " Incorrect password "
if not, are there any errors you get? and if so, what are they?

Josh

---

### Post by mpthrapp on 2011-04-12
It shows the network manager icon trying to connect for a little bit then it asks me for the password. It does this 3 or 4 times then gives up.

EDIT: I changed it from an open system to a shared key and now it'll take the password as correct, but it still won't connect.

---

### Post by josephmills on 2011-04-12
please go to applications--> accessories-->terminal. then  type in ```
ifconfig
``` if you see a wlan0 tell us . Also you could always connect to the router via cat5 (ethernet)cable then log into the router to make sure that no on has changed the setting of the password. you could also "beef up" your password byu changing it to wpa2 thanks

---

### Post by mpthrapp on 2011-04-12
I'm logged on to the router through this computer and I did check that.

EDIT: I had it on WPA2 before but that wasn't work either.

EDIT 2: $ iwconfig

IEEE 802.11bg ESSID: (Correct SSID)
Mode: Managed Frequency:2.413 GHz Access Point: 94:44:52:87:6B:C1

---

### Post by josephmills on 2011-04-12
> **mpthrapp said:**
> I'm logged on to the router through this computer and I did check that.

EDIT: I had it on WPA2 before but that wasn't work either.
that's great did you see your wireless card when you looked at ifconfig?
Also have you tried to reset the modem and start from scratch?

---

### Post by d3v1150m471c on 2011-04-12
you should try removing the encryption from it all together and see if it will even connect.
```

# please post the output of the following, and remove any personal info such as a private ip
ifconfig

# additionally, you should post this:
lspci | grep -i network

```

---

### Post by mpthrapp on 2011-04-12
Yes, the wireless card shows up.

Yes, I tried resetting the modem.

EDIT: Removing the security is not an option, my dad won't allow it.

EDIT: lspci | grep -i network and lsusb | grep -i network return nothing.

---

### Post by josephmills on 2011-04-12
and you can get on to other networks fine?

---

### Post by mpthrapp on 2011-04-12
Yup.

---

### Post by josephmills on 2011-04-12
> **mpthrapp said:**
> Yup.
can you use any other machines to connect to your dads net?

---

### Post by mpthrapp on 2011-04-12
Yes, I'm using his laptop right now, and our communal desktop, wii, roku, brother's computer, step-mom's computer, and mine when I had windows 7 can all connect. The only difference is I'm the only Linux machine.

---

### Post by d3v1150m471c on 2011-04-12
I'm not suggesting you remove the security permanently, **only temporarily to debug the problem**. He'll probably be more understanding if he knows it's changing for five minutes to see if you can even connect. if `lspci | grep -i network' returns nothing it would appear your wireless card isn't being detected, which makes little sense given the dialogue here. make sure you used `lspci | grep -i network' verbadum. also, post ifconfig please.

```

lspci # by itself will work, too

```

the output should look something similar to this:
```

d3v11@d3v11m4ch1n3:~$ lspci | grep -i network
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
d3v11@d3v11m4ch1n3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:dc:54:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4568 (4.5 KB)  TX bytes:4568 (4.5 KB)

mon0      Link encap:UNSPEC  HWaddr 00-24-2B-28-04-E6-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69643536 (69.6 MB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:28:04:e6  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe28:4e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42050752 (42.0 MB)  TX bytes:5031601 (5.0 MB)


```

---

### Post by josephmills on 2011-04-12
> **mpthrapp said:**
> Yes, I'm using his laptop right now, and our communal desktop, wii, roku, brother's computer, step-mom's computer, and mine when I had windows 7 can all connect. The only difference is I'm the only Linux machine.

please post ```
rfkill list
``` thanks

---

### Post by mpthrapp on 2011-04-12
When I run lsusb it picks up the card (I have an external wireless card) 
Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]

Also, what part of ifconfig do you want? I'm not posting this from my desktop so I need to manually type out anything from the terminal.

---

### Post by josephmills on 2011-04-12
> **mpthrapp said:**
> When I run lsusb it picks up the card (I have an external wireless card) 
Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]

Also, what part of ifconfig do you want? I'm not posting this form my desktop so I need to manually type out anything from the terminal.
he said take out the ipaddress and mac address we just want to see if it see the card

---

### Post by mpthrapp on 2011-04-12
ifconfig does pick up the card.

Both hard and soft blocked say no with rfkill.

---

### Post by josephmills on 2011-04-12
connect the computer to the router with a cat5

---

### Post by mpthrapp on 2011-04-12
I don't have a PCI wireless card though, I can do lsusb if you want.

---

### Post by d3v1150m471c on 2011-04-12
This is good but it's going to be difficult to debug this without knowing if your external wireless device can even connect.  It seems a lot of people need to patch that particular device: some of which have solved their problem. see here:

[http://www.linuxforums.org/forum/wireless-internet/64463-installing-wusb54g-ubuntu-wireless-adapter.html](http://www.linuxforums.org/forum/wireless-internet/64463-installing-wusb54g-ubuntu-wireless-adapter.html)

[http://www.ubuntugeek.com/howto-setup-linksys-wusb54g-v4-wireless-in-ubuntu-gusty.html](http://www.ubuntugeek.com/howto-setup-linksys-wusb54g-v4-wireless-in-ubuntu-gusty.html)

[http://ubuntuforums.org/showthread.php?t=188573](http://ubuntuforums.org/showthread.php?t=188573)

the one on ubuntugeek looks a bit more promising.

---

### Post by josephmills on 2011-04-12
> **mpthrapp said:**
> I don't have a PCI wireless card though, I can do lsusb if you want.

what would be cool is if you would connect the computer to the **[B]router**[/B]and post the things that we ask you too. We are trying to help

---

### Post by d3v1150m471c on 2011-04-12
> **josephmills said:**
> what would be cool is if you would connect the computer to the **[B]router**[/B]and post the things that we ask you too. We are trying to help

Aye, he's gonna have to plug it into the router at some point if he wants to use one of the link solutions above.

---

### Post by mpthrapp on 2011-04-12
I'm going to pick up a long enough cat5 in the next day or two to plug into the router and I'll let you know when that's done.

---

### Post by d3v1150m471c on 2011-04-12
I've subscribed to the thread so just make a post when you get yourself setup. Oh and you mentioned your dad is tight on security. FYI, you should let him know that using wep encryption might as well be no encryption at all. I've cracked wep passwords in less than a minute. WPA/PSK is the one you want, with a strong password.

and don't use something like this: [http://webtoolsandtips.com/tips/create-hack-proof-strong-passwords-easily/](http://webtoolsandtips.com/tips/create-hack-proof-strong-passwords-easily/)

I wrote a bruteforcer that will eat "wep$16^" alive. you want to use something like, RrFG&*#!n1n3rn1n3r() or something similar that's valid for wpa.

---

### Post by josephmills on 2011-04-12
> **d3v1150m471c said:**
> I've subscribed to the thread so just make a post when you get yourself setup. Oh and you mentioned your dad is tight on security. FYI, you should let him know that using wep encryption might as well be no encryption at all. I've cracked wep passwords in less than a minute. WPA/PSK is the one you want, with a strong password.

look at post #5 I guess that he put it down wrong.

---

### Post by crispy_420 on 2011-04-13
Second that on the security of WEP. All the security of moist toilet paper.

---

### Post by 3177 on 2011-04-13
check to make sure your entering the right kind of password. (wep, psk ect.)

---

### Post by d3v1150m471c on 2011-04-13
> **crispy_420 said:**
> Second that on the security of WEP. All the security of moist toilet paper.

I just lol'd hard, dude. :)

---

