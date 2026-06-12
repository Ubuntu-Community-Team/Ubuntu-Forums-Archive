---
title: "Mythtv 0.24 UPnP server settings for combined Mythtv FE/BE box?"
date: 2011-10-24
forum: Mythbuntu
---

### Post by samihs72 on 2011-10-24
Hi Everyone! I have combined FE/BE Mythtv box, which works well. I would like to use UPnP server for wathing TV recordings in other room with UPnP client.

My question is, should I add external IP address for either or both of "mythtv-setup" parameters:

"IP address for mythtv" (now 127.0.0.1)
"Master Server IP address" (now 127.0.0.1)

I will continue using this combined box Frontend as well.

I would be appreciated of Your help.

---

### Post by klc5555 on 2011-10-24
127.0.0.1 is the address of "localhost". It is not externally accessible. You will need an externally accessible IP address on the backend machine. Moreover, for the master backend this IP address should be a static IP: either set as such in Network Manager, or by configuring your home network router so that DHCP leases that specific address to to your backend machine at every boot.

You will also need to configure MySQL to accept remote connections. In Mythbuntu this is most easily done from from the Mythbuntu Control Center.

The myth backend settings are briefly recapitulated here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend) 

From a Mythbuntu perspective, your reference (although dated) is here: [http://mythbuntu.org/wiki/general-setup](http://mythbuntu.org/wiki/general-setup)

and here: [http://mythbuntu.org/wiki/mythbuntu-control-centre-mcc](http://mythbuntu.org/wiki/mythbuntu-control-centre-mcc)


Since you'll still be using the frontend on your master backend server, this frontend will also need to have its connection IP address changed from 127.0.0.1 to whatever you have configured for the backend's IP.

---

### Post by samihs72 on 2011-10-24
> **klc5555 said:**
> 127.0.0.1 is the address of "localhost". It is not externally accessible. You will need an externally accessible IP address on the backend machine. Moreover, for the master backend this IP address should be a static IP: either set as such in Network Manager, or by configuring your home network router so that DHCP leases that specific address to to your backend machine at every boot.

You will also need to configure MySQL to accept remote connections. In Mythbuntu this is most easily done from from the Mythbuntu Control Center.

The myth backend settings are briefly recapitulated here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend) 

From a Mythbuntu perspective, your reference (although dated) is here: [http://mythbuntu.org/wiki/general-setup](http://mythbuntu.org/wiki/general-setup)

and here: [http://mythbuntu.org/wiki/mythbuntu-control-centre-mcc](http://mythbuntu.org/wiki/mythbuntu-control-centre-mcc)


Since you'll still be using the frontend on your master backend server, this frontend will also need to have its connection IP address changed from 127.0.0.1 to whatever you have configured for the backend's IP.
Thanks for your quick reply, I'll try these.

---

