---
title: "Backend ideas"
date: 2008-12-04
forum: Mythbuntu
---

### Post by WrathofthePenguin on 2008-12-04
I'm considering a number of different possibilities for a backend. I'd really like something that looks decent, is very quiet and is low-power. 

I'd like a system that will work was a backend. I don't have HD yet, but may in the future.

I like the look of the Dell Studio Hybrid, but there are a number of problems, mainly with supported hardware and that I can't add a hardware encoder card.

I also like the look of the Dell Studio Slim Desktop, but it's a bit pricey.

I'm also considering building a fanless mini-itx system. I have a feeling that this is the way I'll end up going, if for no other reason than the cost and that I can use only supported parts.

Any ideas/advice would be very welcome.

---

### Post by ian dobson on 2008-12-04
Hi,

I'm currently in the process of building a slave backend (I've run out of PCI slots on my master backend). If you can hide the backend somewhere out of the way why not use an old PC you can pickup for afew dollars/euro or what ever (My slave backend is a Pentium 3 underclocked to 400MHz).

A master backend usually needs alot of disk space for all your recordings but not alt of CPU power (Unless you want to transcode).

I prefer to use PCI based tuner cards rather that USB, but that's just me (I had a USB tuner for a while and had nothing but problems until I noticed that the weight of the cable was enough to bend the USB plug just abit, which caused a contact/no contact problem).

Regards
Ian Dobson

---

### Post by WrathofthePenguin on 2008-12-05
> **ian dobson said:**
> Hi,

I'm currently in the process of building a slave backend (I've run out of PCI slots on my master backend). If you can hide the backend somewhere out of the way why not use an old PC you can pickup for afew dollars/euro or what ever (My slave backend is a Pentium 3 underclocked to 400MHz).

A master backend usually needs alot of disk space for all your recordings but not alt of CPU power (Unless you want to transcode).

I prefer to use PCI based tuner cards rather that USB, but that's just me (I had a USB tuner for a while and had nothing but problems until I noticed that the weight of the cable was enough to bend the USB plug just abit, which caused a contact/no contact problem).

Regards
Ian Dobson

The reason I don't want to use an old PC is that I have to convince my wife what a great idea this is. Unfortunately there is very little space to hide anything, so anything I put together has to improve upon the Tivo both in size and functionality, AND be inexpensive enough to pay for itself (no TiVo fee).  

I think that as a community we should do more for recommendations for low cost, wife-acceptable hardware - and I'm going to start by figuring out some of it and posting my findings.

---

### Post by volkswagner on 2008-12-05
If you do have access to an old pc, you can keep the cost down.  My first machine comprised of an old dell which I put in a nice case.

It appears you want a combined frontend/backend.

I do like the miniITX form factor, although it limits expansion (hard disk space, tuners, etc.)

So if you have a compatible microATX PC lying about, why not get this case (or similar)?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811121068]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811121068")

For a miniITX solution it is hard to beat the Intel Atom 330 board (has s-video out onboard)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359")

With one of these cases:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010090007%201054826848&name=Mini-ITX%20Tower]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010090007%201054826848&name=Mini-ITX%20Tower")

---

### Post by 4dognight on 2008-12-05
If you want it to be both a frontend/backend, then you will need it to be even more powerful than just a frontend. Remember it will also be your database server and apache server for mythweb. Also, it will have to do transcoding. If you ever think it will have to platback HD, then you really need it to be even more powerful. 

My master backend, had to do all of the above on a P4 1.6, and it could not keep up when I used it as a frontend. If it is just a backend, then you can use an older CPU. Although I found mythweb to be horribly slow at times when doing seaches for TV listings, on my old PC. 

I spent ~$100  and got a AMD low power 2.5 dual core, MB and 2GB mem. I used an old case, DVD and my HDs.

---

### Post by MartinusEx on 2008-12-05
Hi,

there are refurbished Office PC you can buy from €40 (make that about.. what?? US$ 50 or so??)

Dell, HP, IBM/Lenovo,  Siemens-Fujitsu
Mostly with a 2.5GHz Celeron CPU and only a small HD but ist really not costy.

Dell ist proprietary but has the most beautifull cases.
PCI/PCIe ist typically available.
You might enhance CPU power and RAM later on.
Well, in the end you can get good PC power rather cheap and goodlooking, but neither of these cases is made to fit into your HiFi rack. That might upset your wife. %-)

I run a  Siemens-Fujitsu Scenic N320 with a SIS chipset, 3 GHz Pentium, 1GB of RAM, 320GB internal and 1TB external HD as a BE/FE HTPC.

When transcoding it tends to get loud but while using it for watching TV or a recorded show you nearly hear nothing.

Not an easy decision...
Good Luck :^)

Martinus

---

