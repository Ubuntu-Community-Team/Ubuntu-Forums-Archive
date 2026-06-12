---
title: "Bridging connections Laptop xbox"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by MilesD on 2010-11-02
Hi Guys!
i&#7743;  new to this forum and let me start of with saying that Im real bad with computers. I know my way around windows but my Vista files got corrupted a few days ago and thats why i decided to use Ubuntu.
Well anyway, this is my problem.
Ive got a Acer5920 Laptop and an Xbox. My xbox is in the living room and Id like to connect it to the internet. When i had vista i used bridged connection. :Xbox   => ethernet port of my laptop bridged with wlan of laptop => router.
Bridging connections on vista is fairly easy but I have no clue how to bridge connections on ubuntu. Can someone please help me?

Regards,
Miles

---

### Post by firstEncounter on 2010-11-02
> **MilesD said:**
> Hi Guys!
i&#7743;  new to this forum and let me start of with saying that Im real bad with computers. I know my way around windows but my Vista files got corrupted a few days ago and thats why i decided to use Ubuntu.
Well anyway, this is my problem.
Ive got a Acer5920 Laptop and an Xbox. My xbox is in the living room and Id like to connect it to the internet. When i had vista i used bridged connection. :Xbox   => ethernet port of my laptop bridged with wlan of laptop => router.
Bridging connections on vista is fairly easy but I have no clue how to bridge connections on ubuntu. Can someone please help me?

Regards,
Miles

Bridging the connection is overkill. Simply setting the ethernet to be shared works. 

- Go to "System", "Preferences", "Network Connections"
- Select "Auto eth0" and press "Edit"
- Go to the tab "IPv4 Settings" and change the method to "Shared to other computers". 

Now reboot or run ```
sudo /etc/init.d/networking restart
```

---

### Post by MilesD on 2010-11-02
Thanks for you reply!
I did that and tried connecting but now i get the error &#262;an obtain ip adress from your router though my internet is working :/ Is there a way to solve this? Is it possible to connect an xbox to a linux pc? and is there a guide for connecting an xbox to linux pcs

---

