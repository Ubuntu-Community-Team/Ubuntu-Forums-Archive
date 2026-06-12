---
title: "Need a USB Print Server (wired)"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Daminator on 2009-11-03
Hello all,

I have a Canon IP5200 printer which I want to be accessible from all of my machines (Ubuntu and Windows). Every review I read about a USB print server seems to be mixed. Can anyone help me find one that will just work?

Cheers
Damian

---

### Post by Daminator on 2009-11-04
Any feedback on this?

I'm not expecting anyone to know for sure if a particular device works for my printer (although that would be great), but does anyone know of a USB print server that just works fine with Ubuntu once it's plugged into my network switch?

Am I asking this question in the right place?

Cheers
Damian

---

### Post by i.r.id10t on 2009-11-04
My Asus router has a USB port and a print server built into it ... You'll of course need the Linux drivers for the printer - if it works attached locally, it will work attached to a print server.

---

### Post by grandtoubab on 2009-11-04
maybe have a look here

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking)

and here

[http://www.cups.org/](http://www.cups.org/)

The CUPS web interface is available on your machine at the following URL: 
    [http://localhost:631]("http://localhost:631/")

---

### Post by Daminator on 2009-11-04
Thanks for that i.r.id10t. I could buy a new network switch for upstairs that has a usb print server included. I'll look into that, but assume it would be more expensive that a stand alone USB print server.

Grandtoubab, I tried searching for "USB print server" on the links you posted, but didn't find anything useful. I want to be able to print from any one machine without having to have any other machines switched on.

Thanks for the responses, any other tips?

Cheers
Damian

---

### Post by Daminator on 2009-11-04
Is no one else doing this? Or is my question to obvious to get much feedback on?

Damian

---

### Post by efflandt on 2009-11-04
We use an HP JetDirect 175x at work (but for HP OfficeJet G85xi ink jet printer), which also does lpr/lpd. If you go to [http://www.amazon.com/HP-JetDirect-175X-server-J6035D/dp/B00080E0MQ](http://www.amazon.com/HP-JetDirect-175X-server-J6035D/dp/B00080E0MQ) for example and scroll down the page you can see others for around $50.

Although, many print servers do not spell out their specific protocols, they all do lpr/lpd printing on port 515, likely jetdirect (raw) on port 9100, and probably ipp/cups directly on port 631.

---

### Post by stinger30au on 2009-11-04
i would have thought it would have been as simple as plugging in the printer to a pc running ubuntu

then install the printer driver and samba

then share the printer on the lan and then the entire lan can see it and print till your little printer has a heart attack and dies of old age

surely its no tougher then this?

---

### Post by untenops on 2009-11-05
> **stinger30au said:**
> i would have thought it would have been as simple as plugging in the printer to a pc running ubuntu

then install the printer driver and samba

then share the printer on the lan and then the entire lan can see it and print till your little printer has a heart attack and dies of old age

surely its no tougher then this?

Thats what I did.  Put together a old machine I had laying around, installed ubuntu, now that little box is my print server, a bit of NAS, and even a music server, while it crunches some numbers for boinc.  :)   him what else can I make it do, Linux is great.

---

### Post by Daminator on 2009-11-05
I have one linux machine on all the time, but the printer can not live in that room, so I need to plug it into a network switch in a different room.

Damian

---

### Post by Daminator on 2009-11-20
For anyone interested in this, the Netgear PS121 (v2) seems to work great.
(although only had it a day so far)

D

---

