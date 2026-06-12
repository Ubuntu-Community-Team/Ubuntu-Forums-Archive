---
title: "Getting an IP address a real struggle"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by HughJarse on 2010-08-20
Every time I turn on my ubuntu pc I have to go through a whole rigmarole of:

sudo dhconfig -r
sudo dhconfig

Turn the modem of, turn it on

sudo dhconfig -r
sudo dhconfig

Always get given the stupid 192.168.100.1
Turn the PC off, turn the PC on

sudo dhconfig -r
sudo dhconfig

It's a total ball-ache.
This is because I switch between my Windows PC and ubuntu PC regularly.
Why ubuntu can't get an IP Address from the DHCP server is beyond me.
The pc always gets an IP in 2 attemps.

---

### Post by Fire_Chief on 2010-08-20
Well, if the 192.168.100.1 address is not viable on your network, what should Ubuntu be getting? What IP address does the Windows side get from DHCP?
BTW, 192.168.100.1 is a valid LAN IP address for most home networks.

Cheers!

---

### Post by Iowan on 2010-08-20
**dhclient**?
The 192.168.X.1 address is *usually* a router address - but if the router is elsewhere...
Some routers just don't seem to play nice with Ubuntu. What one do you have?

Modem's sometimes require a power cycle to reset the address they've "locked onto".

---

### Post by HughJarse on 2010-09-24
The method I use now is:
Keep PC switched on.
Reset router (power off/on).

Run terminal

[FONT="Courier New"]sudo dhclient -r[/FONT]

then 

[FONT="Courier New"]sudo dhclient[/FONT]

Repeat until I get a valid ip address.

---

### Post by Steam. on 2010-09-24
Same here.Have to dhclient everytime i start Ubuntu.Happened right after i started using a router.

---

### Post by dallasWolf on 2010-09-24
Have you tried assigning an ip address to the box? This way the router will just use that one all the time as long as is not taken. 
When you finally get an IP address from your router/mode follow the instructions below and choose 192.168.100.75.

System>Preferences>Network Connections> Choose either wired or wireless depending on your configuration, highlight connection and hit edit>Choose IPV4 tab>double click on address to change the IP. >apply. Leave everything else the same. 

NOTE: Intructions are for 10.04. Other versions are very similar.

---

### Post by HughJarse on 2010-11-04
I can't describe how frustrated by this I am now.
This is happening as a matter of course now without any changes to the internet connections?
Man this is a big issue.
Tell you why. Because my crappy old Vista PC picks up an IP on the same network instantly - first time - everytime!!
You could not expect a non-techy person to figure this out.
I think this is a conspiracy by my ISP!
Does anyone in the UK get similar problems with Virgin Media on a dedicated connection?:mad:

PS This is not using any router - just a direct connection to the ISP supplied Modem.

---

### Post by HughJarse on 2010-11-04
Some kind of hardware problem this time. Noticed that there were no lights flashing on the network port, so did a reboot.
Could a USB drive be interfering with an Ethernet port?

---

### Post by CharlesA on 2010-11-04
> **HughJarse said:**
> I can't describe how frustrated by this I am now.
This is happening as a matter of course now without any changes to the internet connections?
Man this is a big issue.
Tell you why. Because my crappy old Vista PC picks up an IP on the same network instantly - first time - everytime!!
You could not expect a non-techy person to figure this out.
I think this is a conspiracy by my ISP!
Does anyone in the UK get similar problems with Virgin Media on a dedicated connection?:mad:

PS This is not using any router - just a direct connection to the ISP supplied Modem.

Sometimes those ISP supplied modems are a modem/router combo.

> **HughJarse said:**
> Some kind of hardware problem this time. Noticed that there were no lights flashing on the network port, so did a reboot.
Could a USB drive be interfering with an Ethernet port?

That wouldn't cause networking to stop working.

---

### Post by HughJarse on 2011-03-07
Happened again. 20 mins of fiddling to get an IP address. The only thing that happened since last power off was I ran some ubuntu updates.
Yet again the old PC boots in fine but ubuntu can't get a response from DHCP.
Are you saying modem/router combos are not as good?
I tried using a NETGEAR wireless router in between but the reliability was awful to the point I don't use it anymore.

---

### Post by CharlesA on 2011-03-07
I guess it depends on which model you use for an all-in-one. I haven't used one personally, since I'm still using the cable modem I got back in 2005.

Was it working when you were using the netgear?

---

### Post by HughJarse on 2012-02-04
Since getting an ISP provided wireless router things have been ok. And I used to think netgear were the best.

---

### Post by CharlesA on 2012-02-06
I guess it's a crapshoot. Some ones are good, some are bad.

Glad it's been going well after getting it replaced.

---

