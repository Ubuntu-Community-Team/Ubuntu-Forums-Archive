---
title: "Is it my router?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Hawkman on 2009-01-19
Day 10 of my attempt at an Ubuntu 8.10 install on an oldish desktop system, and I'm now wondering if my connection problems are due to my router. After having no luck getting my Linksys WUSB11 v2.6 network adapter working, I moved the system to my router and plugged directly into ethernet. Ubuntu recognizes connection "Auto eth0" but when I click on it to connect it returns the following error code:

six repeats of DHCPDISCOVER, followed by
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have a D-Link DIR-625 router. Could the fault lie in the router? I got the same "no DHCPOFFERS received" message while trying to connect the wlan0.

---

### Post by eatberrys on 2009-01-19
Have u tryed connecting with a static ip via hard wire ?
are any other computers able to get online?
what are the settings on the wireless router ?

---

### Post by Hawkman on 2009-01-19
> **eatberrys said:**
> Have u tryed connecting with a static ip via hard wire ?
are any other computers able to get online?
what are the settings on the wireless router ?

I have two laptops in the house running Vista, both connect fine by wireless, including this one that I am using here. 

How do I connect with a static IP? Do I just pull one out of the air like 192.168.0.200 and assign it to the eth0 connection?

Edit: my router firmware 1.09 is the latest available.

---

### Post by cariboo on 2009-01-20
Do you have MAC address filtering turned on?

Jim

---

### Post by eatberrys on 2009-01-22
Yes mac filtering would but a damper on you being able to get online(since u cant get a dhcp response that could very well be it) yes use a ip address towards the end of your subnet so its least likely to be assigned by the Dhcp server on the router or u can sometimes specify an address in the router config that you don't want to to be taken from the pool.

If u do assign  a static ip make sure u put in the right subnet mask and the right default gateway and the correct dns servers or it wont work

---

### Post by Coreigh on 2009-01-22
First rule of thumb when troubleshooting; 1) Remove as many variables as possible.

Does the machine work when you completely bypass the router? Temporarily run an ethernet cable from the internet source (cable modem DSL etc.) straight to the box. Connectivity yes? good.

Add the Router back in. Run the cable from the router to the box. Connectivity no? Router is mis-configured or has a bad ethernet port.

If the answer was no in the first step then the problem lies with the box, either the ethernet adapter or the network config, because you already know that your laptop can connect wirelessly.

---

### Post by Hawkman on 2009-01-29
> **Coreigh said:**
> First rule of thumb when troubleshooting; 1) Remove as many variables as possible.

Does the machine work when you completely bypass the router? Temporarily run an ethernet cable from the internet source (cable modem DSL etc.) straight to the box. Connectivity yes? good.

Add the Router back in. Run the cable from the router to the box. Connectivity no? Router is mis-configured or has a bad ethernet port.

If the answer was no in the first step then the problem lies with the box, either **the ethernet adapter** or the network config, because you already know that your laptop can connect wirelessly.

Thanks for the logical step-by-step. I think the source of the problem must be the ethernet adapter itself, because hooking directly to the cable modem did not give me connectivity.

Fortunately, a new wireless NAU and a fresh install of 8.10 has the old desktop humming now. I'll table the original issue and consider the problem to be isolated to the ethernet adapter and the old Linksys WUSB11 v2.6 device. Just a bad combination of equipment. Thanks for the help, everyone. Should I mark this thread as [Solved]?

---

### Post by spegru on 2009-01-29
FYI I had similar problems with a BT HomeHub2 DSL box (made by Alcatel I understand). Connected via wireless ok (good signal strength etc) but often got no IP address from DHCP.

But here's the weird part: I tried several PCs with this DSL box with Ubuntu (3 different ones), XP (2 different ones)  and Vista. (I got 4 physical PCs, some with dual boot).

Ubuntu: 100% success on 3 PCs
XP: 50% success on one machine, 25% success or less on the other
Vista: 75% success on one PC

Could be down to this particular DSL box being faulty, I guess, but it does tend to prove they can be temperamental and behave differently with different PC hardware and/or OS

---

