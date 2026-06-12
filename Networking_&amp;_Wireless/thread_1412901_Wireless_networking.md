---
title: "Wireless networking"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Moonlitflower on 2010-02-21
My mother has Windows Vista and i have linux ubuntu. She has a special verizon card that she inserts into her laptop for internet. My computer also has an internal wireless card, but the signal here is very poor. Supposedly, among windows computers, I would be able to get a flashdrive, and with a little program uploaded from my moms computer, set things up using the flashdrive on my computer to share the internet that she pays good money for =/ However, it wont work with ubuntu, which isnt in the windows inner circle. When I open the executable file with WINE it says that it cant run wireless network setup "on this version of windows". lawl. 
I was wondering, is there any way around that? Is there anyway to network with my mothers internet?

---

### Post by adam814 on 2010-02-21
If you don't mind being in the same room (and tethered with an ethernet cable) you could just use Windows Internet Connection Sharing.  I haven't used it in years, but that's exactly the sort of thing it's intended for.

---

### Post by northd_tech on 2010-02-21
> **Moonlitflower said:**
>  When I open the executable file with WINE it says that it cant run wireless network setup "on this version of windows". lawl. 
I was wondering, is there any way around that? Is there anyway to network with my mothers internet?

Your mother will need to go into Vista from one of the Administrator accounts into:

1.  Control Panel\Network Connections

2.  Then she will need to click on the appropriate wireless internet connection (mine shows as "Wireless Network Connection" with a router name and my WiFi adapter name under that).

3.  Then right-click on Properties.

4.  Then choose the "Sharing" tab.

5.  Check the box for "Allow other network users to connect through this computer's Internet connection."

5a/6.  Then she may or may not need to select "Settings" and check the services that she wants to grant you access to (I would think Web Server and Secure Web Server at minimum if you can't access anything from ubuntu).

Then you will need to install a Samba client on the Linux machine(s) in order to browse Windows Networks.  I have posted on a couple of threads in the Networking & Wireless forum tonight about Samba and there are links about that, or you could search here for "samba."

If it is anything like Printer Sharing, it will probably run better from Ubuntu to Windows than from Windows to Windows computers (in my experience).

Connecting to Macs is a similar (but different) kind of thing.

BTW- I wrote this from a 64-bit Vista machine that dual boots Jaunty 9.04 ubuntu, so that should be quite accurate on the instructions (I am in Vista right now).

edit:  Like Adam mentioned above, this is using the wireless flavor of windoze Internet Connection Sharing (ICS) and I found the details from the Vista Help system (more or less).

---

