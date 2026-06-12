---
title: "If wired connection is abled, can't connect to internet"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by davisouzarj on 2009-06-16
Guys, see if you can help me with this.

I have a desktop with Ubuntu 9.04 in home, and it connects the internet through a 3G usb minimodem (ppp0).

This desktop is also connected to a wireless router through ethernet port (eth0), so I can share the 3G internet access to my and my wife's notebooks.

I think I had correctly configured Jaunty to share the internet connection (using static IP, masquareding ppp0 and configuring iptables), but when I enable the wired connection to the router through the Network Manager Applet, Ubuntu just can't access anything in the internet!

It is very funny because the 3G minimodem reaches correctly the provider, and the wired network also seens to work properly. But while the wired network is enabled, I just cannot access any website. If I delete the wired network through Network Manager, I can access websites again, just like magic.

Reading a lot in foruns, I began to suspect that it has something with the "default gateway" issue, because when I see the "connections properties" option in the Network Manager Applet, it always shows the wired connection as "default".

Is my suspicion right? Anyone has another explanation and/or a solution to this issue?

---

### Post by spazlon on 2009-09-17
I have the same issue. I have been in the #ubuntu chat room all day to no avail.

Anybody know what is wrong with this?

---

### Post by lswb on 2009-09-17
This might help
[http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

---

### Post by spazlon on 2009-09-17
> **lswb said:**
> This might help
[http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)
That really put me on the right track! Thanks!

I am able to use both eth0 and ppp0 at the same time now, but am unable to share my internet connect like the article says. I think this is because I have a router in the mix.

Here is how my network looks:

[IMG]http://diagrammr.com/png?key=dil5dSTFrGI[/IMG]

Here is my ifconfig: [URL="http://pastebin.com/f8976d93"]http://pastebin.com/f8976d93
[/URL]
Any suggestions?

---

### Post by lswb on 2009-09-17
Can you configure the router so that it behaves like a simple switch? That way all the DHCP & DNS stuff can be done by the server as described in the linked article. If the router has a dedicated "uplink" port it probably should not be used with this configuration.

---

### Post by spazlon on 2009-09-17
If I disable the router features and make it a switch it doesn't have WiFi. I need to maintain the WiFi capabilities.

Right now I have it running great on Vista using ICS. I am able to have all of my wired and wireless computers connect through the router to the media_pc and.

I'm sure if Vista can do it Ubuntu can do it, I just have no idea what I am doing.

---

### Post by lswb on 2009-09-17
I see what you need to do, but I don't know how to do it! I'm thinking iptables rules would be one way of having the server pass requests to/from the router on to the ppp0/internet connection but I don't know enough about it myself to advise on the details. 

You might try posting another thread with a new title that includes "internet connection sharing" (and perhaps "iptables" & "router" in the title as well) and  maybe some more knowledgeable people will respond. Good luck!

---

