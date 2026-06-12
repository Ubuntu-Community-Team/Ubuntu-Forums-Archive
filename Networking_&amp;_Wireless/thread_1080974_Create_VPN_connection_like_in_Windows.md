---
title: "Create VPN connection like in Windows"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-02-26
Hi,

I would like to remote control some Windows machine from from to work.
Usually I use Windows XP:

1. connect to VPN. 

2. I start the WinXP Remote Desktop client. And the remote screen comes up and then I login and start using the remote machine.

Can I do the same using Ubuntu 8.10?

[COLOR="Red"]**Q1.**[/COLOR] What should I install to have the same kind of VPN connection than the one in Windows XP?

Note: in XP, the VPN connection is created from the Windows Network Applet, just create new network connection of type VPN. The only thing I customize is the address of the company network (vpn.mycompany.org)

[COLOR="Red"]**Q2.**[/COLOR] Can I use Applications / Internet / Terminal Server Client to remote control a Windows machine?

Thanks in advance for any help.

---

### Post by AcidHawk on 2009-02-26
Absolutely.  

The only VPN connection I still cannot get right is one using RSA SecureID tag authentication.  Other than that in Gnome you simply configure VPN connections in NetworkManager.  As for Managing windows servers with a terminal services client I need to do that all the time.  I prefer the Terminal Services Client (Under Applications->Internet)  Works a charm.

Good luck.

---

### Post by UranUtan on 2009-02-26
> **AcidHawk said:**
> Absolutely.  

The only VPN connection I still cannot get right is one using RSA SecureID tag authentication.  Other than that in Gnome you simply configure VPN connections in NetworkManager.  As for Managing windows servers with a terminal services client I need to do that all the time.  I prefer the Terminal Services Client (Under Applications->Internet)  Works a charm.

Good luck.

Glad to know that it work for you. But **HOW** did you set up a VPN connection? In my NetworkManager, when clicking on the VPN tab, the Add button is grayed out. When I go to Add/Remove program, there are many plug ins for VPN, which one should I select?

---

### Post by superprash2003 on 2009-02-26
[http://niftybits.wordpress.com/2008/06/12/vpn-into-windows-from-ubuntu-intrepid/](http://niftybits.wordpress.com/2008/06/12/vpn-into-windows-from-ubuntu-intrepid/)

---

### Post by UranUtan on 2009-02-26
To good to be true, I followed the instructions from the link you suggested. It doesn't work for me.

A lot of people mention "Network Manager" what is this exactly?

In Ubuntu 8.10 I am using. There are:
- System / Preferences / Network Configuration
- System / Admin / Network
- System / Admin / Network Tools

Amog the above, only "System / Preferences / Network Configuration" has a tab that say "VPN" so I use it to create a new VPN connection. I select the type = PPTP. And I enter the Windows credentials, login, domain, pwd.

After that I would like to connect, I don't know where is the best place to tell Ubuntu I want to establish the VPN connection. There is a little icon on the top left, I clicked on it, there are a "VPN Connections" item. I select it and a submenu popup, to allow me to select the VPN connection I just created. The icon spins for a minute or two and a notification pops up saying "VPN Connection failed"

How can I find out what was the reason of the failure?

---

