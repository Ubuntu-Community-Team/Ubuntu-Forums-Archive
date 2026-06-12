---
title: "How to share internet connection in Ubuntu 10.04 between switched LAN?"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by spicyraj on 2010-09-10
Hi
I want to share Internet connection which is Reliance Mobile broadband. I have followed these [https://help.ubuntu.com/10.04/internet/C/connecting-wired.html]("https://help.ubuntu.com/10.04/internet/C/connecting-wired.html") steps to connect 2 computers. It works successfully. I can ping now. I connected through switch. Internet connection works well in case of Windows XP(I need to set up proxy at Internet Explorer). But How to set up in Ubuntu 10.04?
Please Help!

---

### Post by viralmeme on 2010-09-10
> **spicyraj said:**
> I want to share Internet connection

[Howto Share internet connection]("http://ubuntuforums.org/showthread.php?t=91370")

---

### Post by dmizer on 2010-09-10
> **viralmeme said:**
> [Howto Share internet connection]("http://ubuntuforums.org/showthread.php?t=91370")

That information is outdated and unnecessarily complicated.
> **spicyraj said:**
> Hi
But How to set up in Ubuntu 10.04?
Please Help!
For an Ubuntu client, you probably only need to add DNS servers.

[LIST]
[*]Right click on your network configuration applet in your tool bar and select [COLOR="Red"]Edit Connections[/COLOR].
[*]Select your network adapter and click [COLOR="Red"]Edit[/COLOR].
[*]Click on [COLOR="Red"]IPv4 Settings[/COLOR], and change the method to [COLOR="Red"]Automatic (DHCP) Addresses only[/COLOR].
[*]Then either add your ISP DNS servers, or you can use OpenDNS -> 208.67.222.222
[/LIST]

---

### Post by perspectoff on 2010-09-10
> **viralmeme said:**
> [Howto Share internet connection]("http://ubuntuforums.org/showthread.php?t=91370")

Oh gawd yes. Those instructions are far too unnecessarily complex and outdated.

I personally have used the instructions at:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29)

or

[http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29](http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29)

---

### Post by dmizer on 2010-09-10
> **perspectoff said:**
> Oh gawd yes. Those instructions are far too unnecessarily complex and outdated.

I personally have used the instructions at:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29)

or

[http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29](http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29)

Firestarter should be avoided. Especially considering the fact that Ubuntu's default Network-manager can do internet sharing with a few clicks. The OP already linked this howto: [https://help.ubuntu.com/10.04/internet/C/connecting-wired.html](https://help.ubuntu.com/10.04/internet/C/connecting-wired.html) and that's currently the best method unless you are using a CLI only server.

The way I read the first post is that the connection is working from Ubuntu to Windows, but not from Ubuntu to Ubuntu as the Ubuntu client is not connecting. This is likely caused by the lack of proper DNS routing, which can easily be solved by manually adding DNS servers in network-manager.

---

