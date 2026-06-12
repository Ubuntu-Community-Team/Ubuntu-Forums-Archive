---
title: "Can't see network printer"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by Mawg on 2010-02-25
I have 4 desktops on a sub-net of someone else's network. One of those has a Samsung SCX-4521F attached and can happily print to it. 

My other desktops do not see this printer, however, they do the other printers on the (windows) machines elsewhere on the 192.xxx.xxxx.xxxx

I previously had everything set up and sharing nicely, but then had to reinstall on the desktop with the printer - this could have been at the time I upgraded everything from Jaunty to Karmic, but I am no longer certain.

On the desktop with the printer, I select system/administration/printing and right click the printer and check "enabled" and "shared". Then I "Server/settings" and check "publish printers" and "allow printing from the Internet". 

But when I go to my other desktops, I only see the other printers, not belonging to me, not this one.

I guess I am doing something really dumb, but am not sure if it I sprinter related or network related. 

The PCs can all ping each other and they all use the one with the printer for backup, so network seems ok. Otoh, looking at CUPS in localhost:631, everything looks ok there too.... 

I'm stumped. Thanks very much in advance for any help.

---

### Post by JohnE1 on 2010-02-26
Get the printer's IP address (from another PC or on the printer directly--usually via a menu option to print network settings) and set it up manually. That's what I would do.

---

### Post by Mawg on 2010-03-01
> **JohnE1 said:**
> Get the printer's IP address (from another PC or on the printer directly--usually via a menu option to print network settings) and set it up manually. That's what I would do.

I'm not so sure that it _has_ an IP address. It just hangs off of a USB port.

---

### Post by JohnE1 on 2010-03-02
> **Mawg said:**
> I'm not so sure that it _has_ an IP address. It just hangs off of a USB port.

The machine it's connected to has an IP address and the printer must have been assigned a name on that PC when someone configured the printer driver. Go into the printer settings on that machine and make sure that printer is configured as a network shared printer. Write down the IP address of that machine and the Printer name as it's being called on that machine. That's for starters.

See if you can connect to the printer with either IP address, Printer name, or both. You may have to try various formats (socket, device uri, etc.) Is CUPS installed on that PC? What O/S is it running? If you can access that PC as an administrator, then you should be able to get it to do what you want on the network.

For help with CUPS, there are newsgroups you can access via the web or via a newsreader (I use Mozilla Thunderbird, for example).

Web access: [Cups Newsgroups on the web]("http://www.cups.org/newsgroups.php")

News server: news.easysw.com

Since I'm the only one so far replying here, you might end seeking help on the CUPS newsgroups. There are CUPS engineers and users there who can help you for sure.

John

---

