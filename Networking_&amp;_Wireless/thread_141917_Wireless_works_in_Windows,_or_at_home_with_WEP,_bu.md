---
title: "Wireless works in Windows, or at home with WEP, but not otherwise"
date: 2006-03-09
forum: Networking &amp; Wireless
---

### Post by rjray on 2006-03-09
This is a weird one to me. I'm no newbie, but it has me stumped.

I set up wireless when I first installed Breezy, on my home network which uses WEP. I'm travelling at the moment, so I brought up the network-admin tool to set a second profile that wasn't encrypted, so I could use the airport's feed. Wouldn't connect. Got to my hotel, another open network. Wouldn't connect. Here at the client site, another open network (!). Won't connect. I try running "ifup wlan0" manually, and I get several messages wherein it broadcasts the DHCP request, but at the end it says it got no offers.

Now, when I switch profiles, it doesn't seem to be updating /etc/network/interfaces. I have to go in and modify that by hand. I wonder if the card (this is a Broadcom, built in to my HP zd7000) just isn't switching off the encryption key no matter what I tell it in the interfaces file. Running iwconfig on the interface doesn't seem to have any effect-- if I run it to see the settings, it says the ESSID is "any", but when I run "iwconfig wlan0 essid <something>", the "any" never changes.

Thing is, this works fine under WinXP, and I'm currently having to use that side of the machine to check mail and stuff while I'm on the road. Not very happy about this.

Any help appreciated. E-mail is ideal.

Randy

---

### Post by sdb2028 on 2006-03-09
When you add a location in your admin-network-wireless connection-properties, do you set the network name to "any"? or use the drop down box to choose an available network?
I set my main connection to "Home" then add a new location to "mobile", then use the drop down box to configure to any open location it finds.

---

### Post by rjray on 2006-03-09
I created a new profile, other than "Home". I then tried to configure the wlan0 interface by using the drop-down menu of detected access points. Once I click "OK", it spins for a while trying to make the connection. But it never gets a DHCP lease.

---

### Post by sdb2028 on 2006-03-09
Did you blank out the wep password when you try'd that?
I was at my sons the other day trying to fix his puter, I couldn't connect with my laptop for a while.Then I realized I forgot to blank out the wep password in the properties box when I try'd to connect to his wireless.

---

### Post by Nick C on 2006-03-10
I'm having exactly the same problem as rjray, with it connecting fine to my home wep-enabled network, but refusing to connect to any networks elsewhere. I'm using a Linksys (Broadcom :( ) card with the standard Windows drivers under ndiswrapper.

---

### Post by sdb2028 on 2006-03-10
I don't use the ndiswrapper, just the original configuration. Works great.
I also use wifi radar, configured to "s" in sysv-rc-conf.

---

