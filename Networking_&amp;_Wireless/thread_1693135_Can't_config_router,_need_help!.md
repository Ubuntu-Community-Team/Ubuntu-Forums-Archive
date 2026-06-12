---
title: "Can't config router, need help!"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by helios16v on 2011-02-22
My brother owns a chain of photo studios and we've just converted the computers over from Windows Vista to Ubuntu 10.10

We're setting up a wireless router at one of them right now and I can't log into the router via chrome or firefox by typing in 192.168.0.1

It just tells me there is no network connection. From what I remember I don't need internet to connect to the router to configure it.

Why is this happening!? On windows or osx it's generally a plug and play operation to getting the wireless all setup and secure.

Any idea's?, tips I could use?, methods I could try?

Thanks
-Ben

---

### Post by frankduffey on 2011-02-22
> **helios16v said:**
> My brother owns a chain of photo studios and we're just converted the computer over from Windows Vista to Ubuntu 10.10

We're setting up a wireless router at one of them right now and I can't log into the router via chrome or firefox by typing in 192.168.0.1

It just tells me there is no network connection. From what I remember I don't need internet to connect to the router to configure it.

Why is this happening!? On windows or osx it's generally a plug and play operation to getting the wireless all setup and secure.

Any idea's?, tips I could use?, methods I could try?

Thanks
-Ben
Many routers are reached by either the Web address "http://192.168.1.1"  or "http://192.168.0.1" Consult your router's documentation to determine  the exact address for your model. Note that you do not need a working  Internet connection for this step. you will also have touse the Networking Tools under Administration  MAKE A NEW WIRELESS  connection for the router. be sure to use the correct name for the connection and the SSDI password default if yiu have not changed it You will need to peknow all information about your connection to set this up yiu can go to the terminal type if config and write down the dns servers You should be able to use automatic connections but to be sure write down the information anyway.
from article at [http://compnetworking.about.com/od/homenetworking/ht/routerconfigure.htm](http://compnetworking.about.com/od/homenetworking/ht/routerconfigure.htm)
you will need to connect the CAT 5 cable directly to the computer or yiou will not be able tio make a connection for the Router and have the correct SSDI name and passwaord which is on the router as the default SSDI number.

---

### Post by thesavager on 2011-02-22
Hi Ben ... are you trying this wireless or with a cable attached to it ?
While when you try this wireless, and you dont get an ip-adress then .... maybe some settings are wrong from your wireless network card ... or the router is brand new , and wireless is not activated yet. 

When you try to config the router using a cable is much easier, and your network card should get an ip-adress and you can login as usual.

pls ...give some info on how you try this .

regards , Pascal

---

### Post by helios16v on 2011-02-22
I've set up routers countless times but it's always been on Windows or OS X. This is where I hit trouble..
> **Step 5:**
Open the router's administration tool. From the computer connected to the router, first open your Web browser. Then enter the router's address for network administration in the Web address field and hit return to reach the router's home page.

Many routers are reached by either the Web address "http://192.168.1.1" or "http://192.168.0.1" Consult your router's documentation to determine the exact address for your model. Note that you do not need a working Internet connection for this step.

When I type in 192.168.0.1 as instructed by the PDF that came with on the CD, both browsers tells me it can not connect to a network. I don't understand why this is happening?!

Every other computer I've done this with, it just works. I called tech support for my provider here and they said to call the router company, I did that and they can't figure it out either. I called the Company I bought it from and they want $80 to come set it up for us and refused to give us help over the phone for free.

I'm about ready to bring this thing back, it's not working at all and I'm completely out of ideas. The only thing I was told was to bring it home and set it up on my home computer which is the iMac or my laptop with Windows 7 and Ubuntu 10.10 and if it doesn't work there then to bring it back. That won't work though as I have cable internet at home and its DSL here.

I need to be able to configure it here on Ubuntu and Set it up to DSL.

**EDIT:**
Internet -> Modem
Modem -> WAN
LAN -> Computer

What am I doing wrong?

---

### Post by drdos2006 on 2011-02-22
We need more information. 
What is the brand and model number of the modem ? 
Do you have an ethernet cable connection to the modem ?

regards

---

### Post by wojox on 2011-02-22
> **drdos2006 said:**
>  
Do you have an ethernet cable connection to the modem ?

That's what we need to know. You need to install the driver for wireless to work and without an internet connection with an Ethernet cable you are stuck in a loop. :p

---

