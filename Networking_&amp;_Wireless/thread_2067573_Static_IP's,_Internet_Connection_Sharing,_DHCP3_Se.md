---
title: "Static IP's, Internet Connection Sharing, DHCP3 Server and headaches!"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by gmspence on 2012-10-07
Bit of an unusual one hoping one of you people can help...

I have just moved house and been told by ISP that I will have to wait approx 2 months before I can get a working ADSL connection as they now have to dig up and lay new cable to my property.

Anyways my neighbour has kindly let me access her internet by sharing her wifi network key. Only thing being the signal is terrible. To combat this, I have an ubuntu laptop set up and perched on my window sill which connects to her network via wifi and via internet connection sharing through eth0 feeds that into an old wireless router i have set up to "boost" the signal in my property. When clients connect to wifi all works fine, addresses given by dhcp in the range 10.42.0.xx.

Here is my problem - I have a number of HTPC set up to access my ubuntu "server" which sits in a cupboard and has shares files via samba. All the HTPC's mount the samba shares in cifs directly in fstab by stating the IP address - used to work brilliantly! Main problem is I can't for some reason assign a static IP to my ubuntu server. I would ideally like to have this server in the ip range of 192.168.1.1 and any clients connecting to it assigned an address 192.168.1.XX from it's own dhcp server with the laptop on the window sill completely ignored and used only to "feed" internet connection into the network.

Have been quite comfortable playing about and setting up dhcp3 servers etc in the past but this one stumps me completely.

Any help would be appreciated!

---

### Post by MartyBuntu on 2012-10-07
> **gmspence said:**
> 
Anyways my neighbour has kindly let me access her internet by sharing her wifi network key.


I'm pretty sure this is a violation of your neighbour's ISP Terms Of Service...

---

