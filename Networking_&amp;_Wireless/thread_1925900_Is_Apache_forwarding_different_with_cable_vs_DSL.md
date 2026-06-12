---
title: "Is Apache forwarding different with cable vs DSL?"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-02-15
I used to live at my parents where they had cable and a WRT54G router. Since then, I have moved out, and I happen to also have a WRT54G but I went with DSL.

In /var/www I created a folder. That folder my user has permission to. That way if I want to send a friend something quick, I can drop the file in /var/www/folder and then if I link him to my external IP/folder, he magically sees an Apache listing with those files visible.

Now that I'm on DSL, I just get a 404 Not Found. I'm using the same desktop, same setup as before. I'm wondering if it has something to do with my modem. You see, I had a Netgear DSL Modem already, so I hooked that up until Verizon's modem/router came. Well it turns out Verizon's choice of modem/routers absolutely suck (port forwarding flat out doesn't work, a lot of the menu options are unpredictable, etc.), so I wanted to go back to the Netgear/WRT54G. But like I said, I get no where.

Is there anything different? All of my internet services work fine. I just can't get forwarding port 80 to my local machine to work.

In summary:
Cable Service - Motorola Surfboard Modem - WRT54G Router - [http://external.ip.of.household/folder](http://external.ip.of.household/folder) = Success.
DSL Service - Netgear Modem - WRT54G Router - [http://external.ip.of.household/folder](http://external.ip.of.household/folder) = Bust.

In order to test the Netgear, someone told me to put the Westell (Verizon's modem/router they gave me) into bridge mode, which evidently turns it into "modem only" mode. Does anybody know how to do that offhand?

---

### Post by jonobr on 2012-02-15
In your machine
 open a terminal and type

```
sudo tcpdump -i any port 80
```

leave it running and connect externally to your webserver

If you see nothing, nothing is hitting your webserver, and you will have to look at your router or ISP.

If you see a packet come in, but no response, there could be an issue with apache or a firewall on your machine dropping packets.


One dopey wuestion for you,
Im guessing you have changed external ip of household with the new IP your getting from your ISP

---

