---
title: "Cannot connect to any wireless network, but can see them. Connects fine wired. Help?"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by oceano10000 on 2009-06-01
I am completely new with this, but i recently used wubi to dual boot vista, and Ubuntu 9.04. 
I am running a Dell Inspiron 1521, and have a Broadcom BCM4311 Wireless Card. I was able to get it to recognized with the Broadcom STA drivers. Now I attempted to use the Network Manager that came with this, and it doesn't connect to any wireless networks whether encrypted or not. It shows 2 green dots, and a blue swirl and then after a while says 'wireless disconnected'. My home wireless is WEP Encrypted, and when i attempt to use that, it continues to ask for the key multiple times until it says 'wireless disconnected'. It works fine wired though. 
I got tired and attempted to use WICD. The wired worked fine but once again, it would attempt connecting to any wireless network, and would get stuck at 'obtaining IP adress'. Even for unencrypted networks. I reinstalled the original network manager. I am at a loss now. I can't connect to any wireless networks, but can see them. If anyone would like to give a shot, im up for anything, ive been trying for a while now. 
Help please&thanks.

---

### Post by victor.gscardoso on 2009-06-18
I have a similar problem, but with an extra twist:
 - my 9.04 system can see the WLAN, my wireless router can see the netbook, and they just won't talk to each other...

I've installed ubuntu 9.04 on my freshly new eeePC 1000HE, and it works like a small rocket, except for the wireless connection. The eth0 offers no problem.
The weird part is that my SMC wireless router can see and accept the connection (I use MAC filtering, as there are no nearby houses). In the attached screenshot you'll see that the one named "pokoyo" is my small machine.
                        [IMG]file:///tmp/moz-screenshot.jpg[/IMG]
An old ACER that my wife uses at work also gives the same problem with Ubuntu - OK for eth0 but KO with WLAN.

As anyone have a solution on this?

BR.

---

### Post by Cacadril on 2009-06-18
I have the same problem since I updated the kernel to version 2.6.28-13 from 2.6.28-11. What kernels are you running?

Please post the output of the following commands: 

  uname -a
  lspci
  iwconfig

Please post some of the output of the following command:

  sudo grep -E "wlan|ath5|phy0" /var/log/kern.log

Select lines with date/time early in your current session.  Instead of or in addition to "ath5" you may use any label or word that is associated with your wireless cards. You may browse the file /var/log/kern.log to figure out what words to use. You can also use the number, e.g 06:02 that prefixes your wireless card in the output from lspci.

Thanks

---

### Post by victor.gscardoso on 2009-06-23
Hi Cacadril,

Bellow my elements.

> **Cacadril said:**
> I have the same problem since I updated the kernel to version 2.6.28-13 from 2.6.28-11. What kernels are you running?

Please post the output of the following commands: 

  uname -a
**Linux pokoyo 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux**

lspci
[B][...]
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)[/B]

  iwconfig
[B]lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:"VC_WLAN"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.[/B]

Please post some of the output of the following command:

  sudo grep -E "wlan|ath5|phy0" /var/log/kern.log

**On attached file "log.txt".**



I'va also find that there is a bug associated with  the ASUS 1000HE on Ubuntu Remix. Don't know if it is the same...

Hope that someone can give us a hand on this.

---

### Post by oceano10000 on 2009-07-22
I started taking my laptop places, and noticed i can connect fine to the university, starbucks, my friends house, and my sisters house. 

Borrowed a friends router, and I can connect fine to my home network. Switched back to the router i had and still can't connect. Its a new router. My wii, my ubuntu, my zune, and my friends Itouch can't connect to it, but windows connects fine. Its a NetGear WPN824 V3. 
Changed the settings multiple times, completely unencrypted, turned off wireless firewall, and nothing. 

I think im going to buy a new router. Solves my problem...

---

### Post by victor.gscardoso on 2009-07-26
> **oceano10000 said:**
> 
I think im going to buy a new router. Solves my problem...

Yes, I believe that it can be not only the best but the "only" solution. My SMC Barricade died yesterday, so I got the excuse to buy for a more recent router. I bought the BELKIN N+ Wireless Router, with USB connection. Just installed it and on my 3 GNU/Linux machines (1 "do-it-yourself" mid tower with Ubuntu 9.04; 1 ASUS 1000HE netbook with Ubuntu 9.04; and 1 ASUS Z53 laptop with Fedora 11) it works like a charm. Nevertheless I'm having some difficulties with a DELL Precision M65 that is running XP Professional - it connects but with "limited or no connection"... Maybe it needs some updates.

---

### Post by oceano10000 on 2009-07-26
Thats funny! Because we have 4 laptops running windows and they all connect to my router. Even my Vista partition connects to the damn router. But nope it hates Ubuntu, Zunes, and Wiis, and smartphones! But on the plus side with windows i can get signal on the street and its still pretty powerful. Too bad i never use Vista.

---

