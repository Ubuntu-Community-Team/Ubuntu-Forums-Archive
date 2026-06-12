---
title: "Static Wireless IP with Network Manager"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by SneakPeak on 2011-07-03
Hi All,

I have been using google and the forum searches all afternoon without success.  So here goes:

I want to set up a static IP on my laptop that connects via **_wireless_** to my home network.  

I have 11.04 installed on my laptop.  When I try to use the manual IPv4 setting in the network manager the save option gets greyed out.  I tried to edit the /etc/network/interfaces file but all the examples I could find on the net refer to eth0.  I tried replacing this with wlan0 but this did not work.  

I tried installing wicd but I kept getting "Bad Password" errors even though I know the password is correct.  A number of people recommended uninstalling network manager to get wicd to work but many other posts said that uninstalling network manager didn't help so I didn't want to go ahead and uninstall unnecessarily.  Besides I figure if Ubuntu is distributed with network manager there must be a reason for having it.

So what do I do to get a static IP address for the client on a wireless connection?

Thanks for your help

Adrian

OK.  I think I have solved this with the following steps.

1. I went to network manager and selected "Connection Information"  On the information window I saw the following:
IPv4
IP Address:  192.168.1.6 (This is the item I wanted to change and make static)
Broadcast Address: 192.168.1.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.1.1
Primary DNS: 192.168.1.1

2. I went to network manager and selected "Edit Connections"
3. I selected the wireless tab and then the wireless network I wanted to edit
4. I clicked on the edit button and then I clicked on the IPv4 settings tab.
5. I changed method from Automatic (DHCP) to Manual
6. Under addresses I clicked Add
7. Under Address I input the static IP address I wanted:
192.168.1.4
8. Under netmask I put the same as Subnet Mask in step 1 above. 
9. Under gateway I put the same as Default Route in step 1 above.
10. Under primary DNS I put the same as Primary DNS in step 1 above.
11.  I disconnected and reconnected and everything seems to work.

Cheers

Adrian

---

### Post by colin.p on 2011-07-03
I presume you have a router? Is it set up for DHCP? Some routers will allow a static DHCP that will give you the same IP all the time. However, I don't think (at least non-commercial) routers will allow DHCP and static set up at the same time.

---

### Post by chili555 on 2011-07-03
Here is a working perfectly example. Be sure you set up the address outside the range used by the DHCP server in the router. For example, if the router assigns ten addresses from 192.168.1.100 to 192.168.1.109. you can safely use 192.168.1.115 for a static IP.

Be sure you set address, netmask, gateway and DNS nameserver.

---

### Post by SneakPeak on 2011-07-03
Yes I have a Belkin Router and the DHCP server is on.
So if the DHCP is on is there no way to get a static IP address?

---

### Post by SneakPeak on 2011-07-03
> **chili555 said:**
> Here is a working perfectly example. Be sure you set up the address outside the range used by the DHCP server in the router. For example, if the router assigns ten addresses from 192.168.1.100 to 192.168.1.109. you can safely use 192.168.1.115 for a static IP.

Be sure you set address, netmask, gateway and DNS nameserver.

As soon as I select manual my "save" button is greyed out.

---

### Post by SneakPeak on 2011-07-03
Ok, I was a moron.  As soon as I started filling in the IP address and the netmask the greyed out button was no longer greyed out.  How do I figure out what my gateway is?  I can "connect" with a static IP setting but although the system indicates that I am connected I can't connect to the internet.  I suspect my gateway setting is incorrect but I don't know what I should use for the gateway.  I tried 192.168.1.254.  That did not work.

Thanks

Adrian

---

### Post by chili555 on 2011-07-03
> I don't know what I should use for the gateway.The gateway address is the IP address for your router. It may be 192.168.0.1 or some such. Can you look at the settings on another computer on the network? *ipconfig /a* for example on a Windows machine.> So if the DHCP is on is there no way to get a static IP address?Not at all; please see:> Be sure you set up the address outside the range used by the DHCP server in the router. For example, if the router assigns ten addresses from 192.168.1.100 to 192.168.1.109. you can safely use 192.168.1.115 for a static IP.

---

### Post by SneakPeak on 2011-07-03
Thanks for the reply.  The problem is now solved.  Refer to the edit in the first post.

Thanks again

Adrian

---

### Post by Chris Richard on 2011-07-03
FYI:

Disclaimer: I'm a Linux noobie too, but have been dealing with a combined wireless/Ethernet LAN for quite a while now.

If you plan to keep using DHCP on your router, with one or more static addresses for any devices on the LAN, it's a good idea to set the static addresses to high numbers (192.168.2.100 and above, for example).

The simple reason for this is that if you ever boot up a DHCP device while the static IP device is not connected, you will very likely end up with an IP conflict because the static IP is available, and so will be used if needed. Then, when you boot up  your static device, you've instantly got a conflict, and things stop working correctly.

Setting static IP to high numbers leaves many possible lower numbered addresses free for DHCP devices and avoids IP conflicts due to improper booting order.

Hope this helps. ;)

---

