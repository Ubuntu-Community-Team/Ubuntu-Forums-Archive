---
title: "Share USB Port to get internet access"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by spindler on 2012-04-27
Hello,

I am running Ubuntu 11.04.

I have a clear wire internet service.  This is a 4G  (Wimax) system that allows me to get internet from anywhere in my city.   However, it is the only internet access I have and I need to setup my web server and I need to access the clear wire hub.

As I mentioned the Hub is a 4G device,  I can connect to the device in 1 of two ways.  Either through the USB port on the HUB or via WIFI, as the Hub is also a WIfi access point.

So my main issue is that my server is a tower computer and it does not have wifi.  It has an ethernet port and a USB port.   I also have several other computers I want to provide internet service too.  This means I need to access the router I have attached to the eth0 port of the linux machine. The linux machine will need to provide internet connectivity to the router from the usb0 port to the eth0 port.  

USB Sharing issue.

I need to plug in my  Clearwire HUB into a USB port on the Linux box  ( usb0).   What I need to do is "Share" this port so that other computers can access the hub via the router which is connected to the ethernet port of the linux machine. 

MY ISSUES.

1.  I do not have a keyboard or mouse.... (sad I know)  I need to access the server vias SSH  or some remote desktop utility I cannot find....  Anyone know of a MAC or Windows Software that will allow me to access the Linux GUI remotely through port 22 (ssh)?

2.  I need to make the USB port a shared port.  Does anyone know a terminal command that can do this?   I found a document that describes how to do this through the GUI but I cannot access the GUI....(see 1 above)...  Here is a link to the article I found. 

[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

3.  I need to make the Eth0 port sharing as well so that other computers on the network can access the server via the router and therefore access the internet through the USB port.... (  Ok  I do not really know if i need to do this or not...I am just attempting to be as complete as possible with my issue. )

Can anyone help?    \\:D/

---

