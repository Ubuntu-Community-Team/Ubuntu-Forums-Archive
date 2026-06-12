---
title: "Help needed with network routing."
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by Beanmonster on 2009-05-16
So I finally get my CDMA **USB** modem up and running and use Gnome PPP (wvdial). So my internet connection is **ppp0** but I also connect through ethernet to the rest of the network, **eth0**. 

[SIZE=2]Problem is...[/SIZE]

[SIZE=2]Whenever my eth0 is connected I am unable to browse the internet (even though ppp0 dialled and connected). I need to repeatedly disconnect eth0 and redial ppp0 and hope that firefox or even DNS ping commands will realise that they now need to request through ppp0. 
[/SIZE]
[SIZE=2]My questions are:[/SIZE]

[SIZE=2]How can I be connected to eth0 and still browse the internet through ppp0?
 
Can I make ppp0 my permanent internet interface?


I would like to then share this connection over the network through eth0, I have tried using firestarter and iptables as described [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") but to no avail.[/SIZE]

Any help or advice is greatly appreciated. :)

---

### Post by spd106 on 2009-05-16
You should be able to modify the eth0 connection settings with the Network Manager utility, the one in the notification area in the top right of your desktop.

Right click on it and select Edit connections. You should be able to tell it to just use the local network resources i.e. not try to use it as the Internet gateway, which is the default. 

If you prefer "old school" text file editing, then an alternative is to add eth0 to your /etc/network/interfaces file. See the man pages for details. This will cause it to be ignored by Network Manager.

---

### Post by Beanmonster on 2009-05-16
Thank you for your response spd106.

Correct me if I'm mistaken, are you referring to a checkbox in the 'Routes' dialogue saying:

"Use this connection only for resources on its network" ?

I've been using wicd until Jaunty so I never knew it existed :) 

The internet seems to be flowing nicely whilst I'm connected to the network, thank you very much!

Its a bit late now so I haven't had a chance to test the ICS yet

---UPDATE---

Using the Ubuntu documentation on iptables and internet connection sharing. I have succesfully managed to share my USB CDMA internet with the entire network. 

The above works like a charm, thank you spd106, simple but effective :)

---

