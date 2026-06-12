---
title: "Network configuration for eth0 and PPPoE"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by abhilash82 on 2009-08-06
I have an Ethernet modem (from BSNL broadband) that is working in Bridged mode and is connected to my interface eth0. The network requires authentication so I created another connection using PPPoE to dial with the user name and password information.

This setup worked fine til the time I installed a Network manager tool which corrupted the settings that I had done via the Network Manager Applet. Now for whatever reason, I am not able to connect to the internet with the settings in my Network manager applet.

I checked the contents of the "interfaces" file and it seems to be alright. I also tried running pppoeconf via command line and setup the dial up connection via my ethernet interface(eth0) and this also didn't work.

Can someone help me out to restore the network parameters for Ubuntu 9.04?

Thanks.

---

### Post by superprash2003 on 2009-08-06
are you able to access your modem? [http://192.168.1.1](http://192.168.1.1) ?

---

### Post by lswb on 2009-08-06
What is the "Network manager tool" you installed and have you removed it?

---

### Post by abhilash82 on 2009-08-06
> **superprash2003 said:**
> are you able to access your modem? [http://192.168.1.1](http://192.168.1.1) ?

Yes it is possible and I solved the issue by running 

```
sudo pppoeconf
```

and then I changed the network manager setting by running

```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

and changed ```
managed=false
``` to ```
managed=true
``` 
Now my network manager applet is up and running and detects both my eth0 and ppp0 connections.

I am able to connect/disconnect via the network manager applet itself without running pon or poff commands.

---

### Post by abhilash82 on 2009-08-06
> **lswb said:**
> What is the "Network manager tool" you installed and have you removed it?

I had installed the old Network manager from synaptic. This tool was used to configure network settings in earlier versions of Ubuntu.

---

