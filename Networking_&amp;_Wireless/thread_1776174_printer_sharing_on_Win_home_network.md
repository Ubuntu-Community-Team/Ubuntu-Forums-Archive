---
title: "printer sharing on Win home network"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by Nick29 on 2011-06-05
Printer sharing on my Win home network.

The problem is it won't. I have an Ubuntu (11.04) computer cabled to a Belkin wireless router. The Brother printer is usb connected to the Ubuntu box - there is no problem printing directly. However, I need to print from a separate wireless connected Win7 box to the printer on the Ubuntu box and this does not work.

The Win7 can see all other Win computers on the network, but not the Ubuntu. Answers at my level gratefully received (eg: it took me two weeks, many hours and 3 re-installs to get dvds to play on Ubuntu 10). Current printer sharing information on the internet is either hopelessly above my head or outdated.

---

### Post by terrykiwi83 on 2011-06-05
do you have samba installed?

---

### Post by drdos2006 on 2011-06-05
Windows 7 will not print to a Ubuntu box with attached printer because Microsoft has removed Internet Printing Protocol from Windows 7. IPP still exists for XP so XP will connect. Microsoft wants you to connect Windows 7 to a Microsoft print server with IIS switched on in the print server.

regards

---

### Post by demonipuch on 2011-06-05
> **Nick29 said:**
> Printer sharing on my Win home network.

The problem is it won't. I have an Ubuntu (11.04) computer cabled to a Belkin wireless router. The Brother printer is usb connected to the Ubuntu box - there is no problem printing directly. However, I need to print from a separate wireless connected Win7 box to the printer on the Ubuntu box and this does not work.

The Win7 can see all other Win computers on the network, but not the Ubuntu. Answers at my level gratefully received (eg: it took me two weeks, many hours and 3 re-installs to get dvds to play on Ubuntu 10). Current printer sharing information on the internet is either hopelessly above my head or outdated.

Hello,

Here is how you can use ipp protocol to share your printer over your local network :

Ubuntu :

Open firefox, go to CUPS web interface : [http://localhost:631](http://localhost:631). In Administration, check Share printers connected to this system and Allow printing from the Internet. Click Change Setting.

Win7 :

Follow this article : [http://nogitech.wordpress.com/2010/04/28/using-printers-over-the-internet-with-ipp-in-windows-7/](http://nogitech.wordpress.com/2010/04/28/using-printers-over-the-internet-with-ipp-in-windows-7/)

URL in step 4 should be : [http://ubuntu_ip_address:631/printers/your_printer_name]("http://ubuntu_address_ip:631/printers/your_printer_name")

---

### Post by Nick29 on 2011-06-07
Terrykiwi83 - How do I find out if I have Samba installed? And how do I get to use it, if it is?

Regards
Nick29

---

### Post by Nick29 on 2011-06-07
demonipuch - I followed your method as far as I can, but what is "ubuntu_ip_address:631"? What does it look like filled in correctly, where do I get it from, and what part(s) do I add in where to get the url to work? I used "ifconfig" in Terminal but got 15 lines of gobbledegook. I tried 192.XYZ.2.4 and 192.XYZ.2.4:631, but neither worked.

Regards
Nick29

---

### Post by Morbius1 on 2011-06-07
> **Nick29 said:**
> but what is "ubuntu_ip_address:631"? What does it look like filled in correctly, where do I get it from, and what part(s) do I add in where to get the url to work? I used "ifconfig" in Terminal but got 15 lines of gobbledegook. I tried 192.XYZ.2.4 and 192.XYZ.2.4:631, but neither worked.
How about this way from Windows:

Open a browser and type:
```
http://192.168.0.100:631/printers
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of your ubuntu box which you got from ifconfig.*[/COLOR]

If everything is working you should get a list of printers. Click on one and the url should change to something like this:
> [http://192.168.0.100:631/printers/HP970](http://192.168.0.100:631/printers/HP970)

That's the URL you want in the step demonipuch referenced above.

---

### Post by walt.smith1960 on 2011-06-07
Is the Brother printer network enabled? If so, is it practical to plug the printer into a router LAN port, or establish a wireless network connection between the router and printer?  If so, the Ubuntu machine would not have to be on for other users to print to the Brother printer and network configuration of Brother printers is pretty easy in my experience.  I have 3 network enabled scanner and/or printers working great.  I'm no Linux or networking genius by any means so if I can do it, so can you.

---

### Post by Nick29 on 2011-06-14
walt.smith1960

My printer does not have network capability, unfortunately.

---

### Post by Nick29 on 2011-06-16
demonipuch and Morbius

Thank you. I have finally managed with your sage advice.

---

