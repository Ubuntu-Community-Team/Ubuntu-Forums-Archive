---
title: "Can't Connect Wireless ):"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by ElHana0902 on 2010-10-14
I installed Ubuntu 10.10 yesterday and everithing was great, this morning I was installing a few apps and my pc turned off by overheat(wich is common on my laptop)
I left the laptop for a while and when I turned on to continue working in my Ubuntu
I found that my laptop cant stablish a wireless connection, I restarted the pc in my Windows7 partition and there was no problem at all, I checked with the live CD and even with the Live CD I cant connect to wireless
the network manager shows all the networks around but when attemping to connect mine just ask for the encription key over and over again, and I'm not typing any wrong key...
please help

---

### Post by kreggz on 2010-10-14
you could try power cycling the wireless router?

---

### Post by ElHana0902 on 2010-10-14
just the same, it just asks for the key over and over, and in windows(wich I want to stop using) I have no problems. 
I tought that maybe the wireless card stopped working and I have to reinstall Ubuntu 
but when I boot from the CD is just the same thing :@
I am posting thisn in windows by the way \:

---

### Post by kreggz on 2010-10-15
Do older versions of Ubuntu work on this laptop?

---

### Post by ElHana0902 on 2010-10-15
no man, I had installed lucyd and the wireless never worked, I just wanted to check Maverick and my surprise when it connected wifi, I wasnt checking the temperature of the pc and it just shuted down, so when I turned it on, it wasnt able to connect to any wireless network...
i already tried turning off the wireless card, and many things

---

### Post by silbak04 on 2010-10-15
Uninstall Network Manager, install Wicd, and try configuring your wireless with Wicd. If that still does not work, read me your output for

```

$ cat /etc/network/interfaces

```

---

### Post by ElHana0902 on 2010-10-15
damn, i dont know whats happening, when i try to uninstall network manager thru software centre it gives me a message... cant install/remove untill reparation is complete, when I click on repair, askes for online comunication, wich I am unable to stabilish, I have no acces to a wired network, just wireless...
tried the 
*sudo apt-get remove network-manager*
and it just gives me an error
and when trying to install Wicd, says that i have to uninstall ntwrk mngr
maybe i have to wait afew days to be able to connect wired

---

### Post by wcpon on 2010-10-15
I got the same problem also..
cannot enable my wireless at all... :(

---

### Post by silbak04 on 2010-10-15
Either you can wait for an ethernet cable, or you can temporarily hook your computer up to the router, and uninstall network manager and get wicd. Hope this helps!

---

### Post by wcpon on 2010-10-17
you may try this,
After I installed the wifi driver, it is working fine now. :)
Hope this is help.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by ElHana0902 on 2010-10-18
Hey bros, now I turn this as solved...
Since I've uninstalled network manager, I was not able to stabilish either a wired connection or any connection
a few minutes ago I uninstalled and installed Ubuntu and then it just connected
I will install Wcid and work with NM till disconnects :p 
hope that thing never happens again, so, thanks for your help, later.
                                                                ElHana0902

---

### Post by nklnsk on 2010-10-26
Hey guys, I had same problem. But one night, it just get connected. On 10.04. I didnt have any problems.

---

