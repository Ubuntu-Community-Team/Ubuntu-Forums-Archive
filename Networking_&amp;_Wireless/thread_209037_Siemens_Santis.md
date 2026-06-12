---
title: "Siemens Santis"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by tenyardfede on 2006-07-04
Hi, I was wondering if any one can help me installing or configurating my ADSL, model siemens santis.

I'm new to linux, ubuntu v6.06, and it's all day that I'm trying to find out how to install internet on linux. Hope one of you can help me.

Thanks cya

---

### Post by lullebakman on 2006-07-05
Are you Belgian? (Because the Siemens Santis WLAN Routers are commonly used by Skynet, an ISP in Belgium.) 
 
I have a Siemens Santis ADSL 50 Router Modem (WLAN).
 
The only thing I had to do to get it working was filling in my IP address, gateway and DNS address. 
I don't use DHCP but I assume that you use [DHCP]("http://en.wikipedia.org/wiki/DHCP") (Dynamic Host Configuration Protocol, you get your IP address automatically...)
 
Open the network settings, not network tools,
deactivate every interface in the Connections List except your Wireless Connection and activate the Wireless Connection if it isn't. Click Properties.

Fill in your network name (SSID).
To find it, type the IP address of your router in your browser (probably 192.168.1.1) click Advanced Configuration, enter password, probably ancapitalized or lowercase 'Admin' or 'WebAdmin' and 'admin' as password, again: I don't remember the exact spelling because I changed them. Then, go to Configuration > WLAN and you'll see your network name in the box labeled as 'Wireless SSID').

If you use a WEP key, fill it in, if not leave it blank. (you can find your wep key on the page where you found your SSID).

If you have DHCP as I mentioned before, select DHCP as Configuration and you won't have to fill in the other options and you can click OK.

If you use a Static IP address then select Static IP address as configuration.
Fill in your IP address, the subnet mask (default and use it: 255.255.255.0) and the gateway address, probably 192.168.1.1 Click OK.

DNS Server:

Click the DNS tab, select the first blank option and delete it (if there is one).
Click Add and fill in the gateway address (192.168.1.1)

That should do it and did it in my case.

---

