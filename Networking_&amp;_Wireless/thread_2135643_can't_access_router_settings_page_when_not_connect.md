---
title: "can't access router settings page when not connected to a modem"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by tuxonapogostick on 2013-04-14
Hi all.

I would like access my wireless router (Belkin F6D...) to change its configuration/settings.
My question is "how can one properly connect to a router which is not connected to a modem(internet)?

When the router was connected to a modem, I could access router configuration webpage via address [http://192.168.1.0](http://192.168.1.0) or so, which was the ip address of this router. However, currently the router isn't connected to a modem, and therefore either (i) I can't connect it if dhcp method is used, or (ii) I can connect it via ad-hoc* or local-link** methods but I can't seem to find the (local?) ip address for the router. 
I would appreciate any help. Thanks.

*Edit
the problem is solved thanks to ubuntu community.
Here are the steps:
Step 1:  create a manual wired connection profile: set ip,netmask, gateway manually (no dns is necessary)
Step 2:  reset the router.

---

### Post by Iowan on 2013-04-15
Are you trying to access the router via wifi, or via wire (cable)? 
If via wire, does computer get IP address? (you might set up static address via Network Manager)
If not, do you have a cable that you could try?

---

### Post by Hadaka on 2013-04-15
Hi, just cable it from the computer to one of
the 4 router ports.
[]-----------[]
computer~~~~~~router
open the browser, and enter 192.168.2.1
viola! no internet needed to configure.

---

### Post by tuxonapogostick on 2013-04-16
Re:Hadaka: Thas was one the first things I tried. It ditd't work unfortunately.

---

### Post by Hadaka on 2013-04-16
Hi, did you try different ip's
192.168.1.1
192.168.0.1
192.168.0.101
I just did a Netgear today that way
direct plug in...192.168.1.1 and went right in.
search around, there is most likely a way in.
*edit.
did you reset the router by pressing the small
reset button in the back? I did a search and it says
the belkin router is 192.168.2.1 by default...reset
and try again.

---

### Post by steeldriver on 2013-04-16
The only case I can think of where you'd experience this is if your 'modem' is actually a router-modem with its own DHCP server, and you'd configured your 'router' as a simple switch / access point (turning off *its *DHCP server, and most likely connecting it to the 'modem' via one of its LAN ports instead of the usual WAN port).

If that's the case, and you can't connect it to the router-modem (or another equivalent router/DHCP server) to get it to pick up an IP address, then your best option may be to hard reset the router back to its factory settings and go from there.

---

### Post by tuxonapogostick on 2013-04-16
> **Iowan said:**
> Are you trying to access the router via wifi, or via wire (cable)? 
If via wire, does computer get IP address? (you might set up static address via Network Manager)
If not, do you have a cable that you could try?
I tried both wifi and wired. I guest fixing wired connection should be easier than wifi.
As you suggested I tried static ip.
I set ipv4 settings to manual, and set:
address:192.168.2.100 netmask:255.255.255.0 gateway:192.168.2.1
Then I did an nmap search giving
```

nmap -sP -n 192.168.2.0/24

Starting Nmap 5.21 ( http://nmap.org ) at 2013-04-16 21:44 EDT
Nmap scan report for 192.168.2.100
Host is up (0.00023s latency).
Nmap done: 256 IP addresses (1 host up) scanned in 32.68 seconds

```
meaning only my computer is up. the router is no where to be found.

---

### Post by tuxonapogostick on 2013-04-16
> **Hadaka said:**
> Hi, did you try different ip's
192.168.1.1
192.168.0.1
192.168.0.101
I just did a Netgear today that way
direct plug in...192.168.1.1 and went right in.
search around, there is most likely a way in.

nmap -sP -n 192.168.1.0/24 gives that there are 0 hosts up.
> 
*edit.
did you reset the router by pressing the small
reset button in the back? I did a search and it says
the belkin router is 192.168.2.1 by default...reset
and try again.
I couldn't really find a reset button in my router. I just turned its power off for 30s and then turned it on.
The result is still the same.

---

### Post by Hadaka on 2013-04-16
Hi, most routers have a small hole in the back.
sick a toothpick,paperclip in and hold the micro button
down for 20 seconds while the unit is powered up.
just powering it off wont reset it to factory default.

[http://www.ehow.com/how_8506079_can-unlock-belkin-router.html](http://www.ehow.com/how_8506079_can-unlock-belkin-router.html)

how to...

---

### Post by tuxonapogostick on 2013-04-16
> **steeldriver said:**
> The only case I can think of where you'd experience this is if your 'modem' is actually a router-modem with its own DHCP server,...
I don't have access to the modem.
So, neither my wireless router nor my netbook is connected to internet.
Then, I am trying to do a wired connection between my netbook and the router in a way that the router acquires an ip. Then I can access the router settings and configure it.

---

### Post by lisati on 2013-04-16
> **tuxonapogostick said:**
> I don't have access to the modem.
So, neither my wireless router nor my netbook is connected to internet.
Then, I am trying to do a wired connection between my netbook and the router in a way that the router acquires an ip. Then I can access the router settings and configure it.

Are you saying that you have a *router* which you have physical access to, but you don't have physical access to the *modem*?

---

### Post by Hadaka on 2013-04-16
hi, i think we posted at the same time..
read post #9..click the link on how to.
good luck, hope you get it going.

---

### Post by tuxonapogostick on 2013-04-16
> **Hadaka said:**
> Hi, most routers have a small hole in the back.
sick a toothpick,paperclip in and hold the micro button
down for 20 seconds while the unit is powered up.
just powering it off wont reset it to factory default.

[http://www.ehow.com/how_8506079_can-unlock-belkin-router.html](http://www.ehow.com/how_8506079_can-unlock-belkin-router.html)

how to...
After you mentioned, I double checked it found the location of the reset button which is indicated by the word "reset" in very tiny letters. Anyways, resetting combined with manual ipv4 settings did the job. I can access to the router now with no problems. Thank you all.

---

### Post by tuxonapogostick on 2013-04-16
> **lisati said:**
> Are you saying that you have a *router* which you have physical access to, but you don't have physical access to the *modem*?
Yes which is sort of strange I understand. The situation is that I am renting a basement, and modem is at upstairs where my landlord lives. Asking her for access to the modem would not only be an elegent solution to the problem but also  a minor pain for the landlord.
In any case, the problem is solved. Now that I have access to the spare router I will be trying to set it up as a bridge to the wireless router at the upper level.

---

### Post by Hadaka on 2013-04-16
Great ! please mark this thread SOLVED

---

### Post by tuxonapogostick on 2013-04-16
> **Hadaka said:**
> Great ! please mark this thread SOLVED

An emberessing question: how do i mark it as solved? Is changing message title is sufficient?

---

### Post by Hadaka on 2013-04-16
click go advance and change the title from Ubuntu...to solved
there is a drop down, you'll figure it out.

---

