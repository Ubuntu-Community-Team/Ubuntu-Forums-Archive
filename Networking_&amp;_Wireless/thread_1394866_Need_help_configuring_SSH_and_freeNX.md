---
title: "Need help configuring SSH and freeNX"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by Lemiwinks on 2010-01-31
Hi,

I'm new to ubuntu and thus far I'm loving it! Ok, back on to topic:

**Scenario**: I have setup an old pc with ubuntu9.04 for our home server(More out of curiosity than necessity). It will be our print server, file server, ftp, vpn and more as soon as I find other things I can benefit from(suggestions welcome ;)).

Currently have an insufficient number of monitors and will be connecting to the server remotely from my PC(XP and on the same LAN). Currently using VNC, but if I am not mistaken then freeNX is faster than VNC(which is rather choppy) and can transfer files.

**Problem:** I have installed and configured openSSH on the server. I have also installed freeNX-server and configured it. All the configurations where done to the best of my knowledge but I fear that I cannot connect to the server from my PC(win XP) so logic tells me that the fault lies with the conifgurations.

Any help and/or suggestions will be appreciated. If it would help I could post the config files...

---

### Post by johnson.d on 2010-02-04
There is not much of a configuration in the FreeNX server and configurations lie on the client side. Before looking into configurations you can probably try the following:

1) Can use putty to connect through ssh to the server.Here we can confirm whether ssh connection is established, as it is needed for FreeNX to work

2) Check the error messages that the FreeNX client gives out.

---

