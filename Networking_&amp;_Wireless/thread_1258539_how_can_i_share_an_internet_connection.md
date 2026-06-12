---
title: "how can i share an internet connection"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2009-09-05
i am moving into a new house and have noticed that the 2 studys both have an ethernet connection (the same cable (its not in use at the moment and is just by itself no other hardware)) is there any way to share my connection through this cable or a wifi connection from one computer to another both running ubuntu.
also can i use this cable for sharing files.
what hardware will i need other than the 2 laptops to do this.
if using wifi what is the range.
thanks

---

### Post by jeffdunn on 2009-09-05
I cannot be sure about this, but there are homes that have a router installed within the walls somewhere in the home. For example, a friend of mine has an apartment in a building where all of the apartments have such a facility.
What you should do is just plug your laptop into the ethernet connection and if it is hooked up, you will be online as soon as you boot your computer. Then take the same or another computer to the other room and do the same thing.
I share a connection with my brother like this:
1) modem is in my brothers room.
2) modem is connected to a cisco router (bought it brand new for five bucks at FreeGeek Vancouver's computer thrift store).
3) Brother's computer connected to router by lan cable
4) My compuiter connected to router by lan cable.

As for file sharing, the basic setup I've described won't allow that. I suggest that after you have the computers set up and tested start a new thread to get info on how to configure your network if you really want a network. Personally, I'd rather avoid the hassel of networking and just email stuff to my brother or just walk over and hand it to him on a flash disk.

---

### Post by shredder12 on 2009-09-05
If you want to share internet connection between 2 computers then you can install a dhcp server on the one which already has internet access and 
use it to provide connection to the other computer using an ethernet connection.

---

### Post by jarrah-95 on 2009-09-06
ok thanks 
ive been thinking about it and i thing the best way would be to use a wifi connection is there any way to create a connection that will start when you boot and work like the one jeffdunn except only with wifi

---

### Post by ugm6hr on 2009-09-06
Invest in a wifi router.  Easier than messing about with connection sharing on the computers themselves.

If you need a modem to connect, get a wifi modem-router.

---

### Post by shredder12 on 2009-09-06
A dhcp server would be the easiest way... Jst establish one on the main computer (which is directly connected to Internet) and if a wifi router is connected to it.. then every body connecting to the router will be assigned an IP automatically...

---

### Post by jarrah-95 on 2009-09-06
is there a wireless router that will take a wireless broadband modem that connects via usb
thanks

---

### Post by ugm6hr on 2009-09-06
> **jarrah-95 said:**
> is there a wireless router that will take a wireless broadband modem that connects via usb
thanks

Sorry, I don't understand.  You have have a wireless broadband modem that connects via USB?  I didn't realise such things existed.

My suggestion: just replace it with a wifi modem-router that has at least 4 LAN ports and wifi.

If I have misunderstood what you are trying to achieve, please explain in a lot more detail.

---

### Post by jarrah-95 on 2009-09-06
sorry 
i have a optus wireless broadband (works off cell phone towers) and uses a dial up interface to connect but then connects with broadband speeds. 
details about my modem

ROAMER - USB modem (Huawei E220)
 
Features:
HSDPA 2100MHz only
SMS Services
Plug and Plan Auto Installation
System Requirements:
A computer with a standard USB interface
A USIM card with a data subscription
Check network coverage in your area.
Minimum PC requirements:
Processor	Pentium II processor
Internal memory	128 MB RAM
Disk space	50 MB
Interface	Standard USB
Operating System Support:
Microsoft Windows Vista 32
Microsoft Windows XP Professional (SP1, SP2)
Microsoft Windows XP Home Edition (SP1, SP2)
Microsoft Windows 2000 (SP3, SP4)
Mac OS X10.3.5 or above (Software/Firmware may be required for some model)
The PC must also have:
Remote Access Services components with TCP/IP protocol enabled
Microsoft Internet Explorer version 6 or above
You must be logged in to your computer with Administrator Privileges when you install the Optus Wireless Broadband software or a new modem.

btw it does support linux even though is does not say it does and i connect via the network manager applet but i can do it via wvdial
thanks

---

### Post by 3rdalbum on 2009-09-06
> **ugm6hr said:**
> Sorry, I don't understand.  You have have a wireless broadband modem that connects via USB?  I didn't realise such things existed.

Yes, it's mobile broadband. Works off the mobile phone towers. 3G.

Your provider will be able to sell you a router that accepts your mobile broadband stick, and creates a wireless network. Or you can plug it into your Ethernet port and the other Ethernet-connected computers will be able to access it.

If you're at a fixed address, you'll be happier to have ADSL because it's faster and more reliable.

---

### Post by jarrah-95 on 2009-09-06
ok thanks ill check it out and (if its not too expancive) buy one or if not then ill just atempt to connect it to my computer and then share it from there

---

### Post by ugm6hr on 2009-09-06
> **3rdalbum said:**
> Yes, it's mobile broadband. Works off the mobile phone towers. 3G.

Ahhhh. That makes sense.  Mobile broadband.

I have seen a few posts about USB modems in the recent past, and keep assuming they refer to the USB ADSL modems of old.

---

