---
title: "Cannot connect to wireless adhoc network created with windows"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by efi93 on 2011-10-22
Hi guys
I have installed ubuntu 11.04 (x64) alongside windows 7. 
My sister's laptop is running windows vista, and I've created an adhoc wireless network on it with WPA2-Personal security. In my laptop, it shows the network but it can't connect to it. Can anyone give me a hand with this please?

---

### Post by efi93 on 2011-10-22
guys please help me about this

---

### Post by efi93 on 2011-10-25
I'm new to ubuntu friends, need some help...!

---

### Post by dandnsmith on 2011-10-25
> **efi93 said:**
> Hi guys
I have installed ubuntu 11.04 (x64) alongside windows 7. 
My sister's laptop is running windows vista, and I've created an adhoc wireless network on it with WPA2-Personal security. In my laptop, it shows the network but it can't connect to it. Can anyone give me a hand with this please?

Your laptop is, presumably, the PC with ub/Win7.
Can you connect to the ad-hoc network with Win7?
Are you trying to work with wireless directly from one laptop to the other - if not, what other hardware is 'in the loop'?

With the advent of Vista and Win7, networking between linux and Windows moved from the tricky to the often-difficult (in my opinion), as M'soft seem to delight in create obstacles which hinder *even* between different versions of Windows (and heaven help you if you try to undo things, as there seem to be irreversible steps taken which necessitate a clean re-install to get things to work).

---

### Post by efi93 on 2011-10-25
Yes I can connect with windows 7 to the network.
And in Ubuntu, I can see it in the list of networks, but I can't connect to it.
I'm trying to connect my laptop to internet in this way.

My wireless adapter is Atheros AR5B93
but in Ubuntu, it's shown as Atheros AR928X

---

### Post by praseodym on 2011-10-25
Internet connection sharing normally only works in Ubuntu with WEP encryption (firmware issues most of the time, blame the manufacturers)

---

### Post by dandnsmith on 2011-10-25
> **efi93 said:**
> Yes I can connect with windows 7 to the network.
And in Ubuntu, I can see it in the list of networks, but I can't connect to it.
I'm trying to connect my laptop to internet in this way.

My wireless adapter is Atheros AR5B93
but in Ubuntu, it's shown as Atheros AR928X

Those Atheros chipsets are often the problem - and can sometimes be got to work by utilising the Windows drivers with *ndiswrap* - if you google, you should find multiple sources of advice on how to do this.
I used this for my Asus Aspire One netbook before there was proper support (I was using Mint first, as the first ubuntu related distro for which it was easy to do - Mint had instructions on how to do it).

HTH

---

### Post by dandnsmith on 2011-10-25
> **praseodym said:**
> Internet connection sharing normally only works in Ubuntu with WEP encryption (firmware issues most of the time, blame the manufacturers)

Sorry - misread this

---

### Post by efi93 on 2011-10-26
Thanks for the reply.
How can I install drivers with *ndiswrap*? 
Should I block other drivers first? And if I should, how can I do that?

---

### Post by Weirdy on 2011-10-26
Just to check, can you actually connect? if so, do you get an IP address? In my experience of Windows ad-hoc networks, it sets up the network but doesn't set up DHCP for IP distribution. on the other hand, if you cant, what error do you get?

---

### Post by efi93 on 2011-10-26
No I can't connect at all. 
If I try to connect using connect hidden wireless, it prompts over and over for network password, and it doesn't connect.

---

### Post by LordDelta on 2012-01-13
Sounds the same as my issue...(though related in a different manner...)

I'm trying to create a wpa2 adhoc network between two linux boxes (both debian based, one is ubuntu 11.10 one is crunchbang 10), and I have similar issues with the password when I attempt to connect.

Everything I've been reading seems to hint at wpa2 over ad-hoc being not possible, or it being a driver issue...however its definitely the latter (if at all, if there's not an easy non-driver related fix), since I check with the OFFICIAL IEEE 802.11i standard (as of 2007), which SPECIFICALLY STATES that WPA2 over RSNA/CCMP (the WPA2 encryption scheme which replaced WPA) is possible for ad-hoc and mesh networks.

So, yeah, the drivers (still suck). AFAIK.

And its not for lack of trying. I've gone into /etc/network/interfaces, on both computers, killed off the (partially) brain-dead NetworkManager, and run the wifi network that way, run ifup, ifconf, iwconfig...to no avail (although to get adhoc networking working at all, without encryption, I had to kill NetworkManager on one of the machines, a testimony to its suckiness).

---

### Post by praseodym on 2012-01-14
Internet connection sharing (ICS) only works with WEP encryption, few times (depends on driver/firmware combination) with WPA(1), but not with WPA2.

---

