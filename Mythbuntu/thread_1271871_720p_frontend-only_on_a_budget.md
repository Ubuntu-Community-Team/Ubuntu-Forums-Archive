---
title: "720p frontend-only on a budget?"
date: 2009-09-21
forum: Mythbuntu
---

### Post by viridari on 2009-09-21
Hey folks. I just got an HDTV and would like to build a lightweight front-end box to attach to it.

* TV only goes up to 720p. I don't need to be able to handle 1080p or 1080i.
* I'd really like audio & video to work through HDMI.
* I don't need any optical disc capabilities on this box. I just want to play recorded TV shows and HD movies from my back end infrastructure.

Can anyone in-the-know recommend a good shopping list that will be Mythbuntu-friendly and achieve these objectives without breaking the bank?

Thank you!

---

### Post by ian dobson on 2009-09-21
Hi,

OK start off with a NVIDIA graphic card (9000 series) a bottom of the range Core 2 Duo, a bottom of the range motherboard 1Gb ram and whatever harddisk you've got laying around.


Maybe have a look at the Zotac nForce 9300 motherboard (Onboard everything including a 9300 graphic card with CUDA support).

My frontend runs on a e5200 underclocked to 1.2GHz with a NV9300 pasive graphic card. Even playing HD videos the CPU load is less than 20% using the VDPAU 0.21 backports.

Regards
Ian Dobson

---

### Post by bekind2thenoob on 2009-09-21
Acer Aspire Revo

Its a mini desktop pc runs integrated Nvidia Ion graphics (9400 chipset for notebooks) and has built in hdmi output.

(Can't link to the page cos its javascripted the Revo's in the third column.)
[http://www.acer.co.uk/acer/product.do?link=oln85e.redirect&changedAlts=&kcond48e.c2att101=-1&CRC=2759084358#wrAjaxHistory=0]("http://www.acer.co.uk/acer/product.do?link=oln85e.redirect&changedAlts=&kcond48e.c2att101=-1&CRC=2759084358#wrAjaxHistory=0")

[http://www.ebuyer.com/product/167153](http://www.ebuyer.com/product/167153)

---

### Post by Slate8 on 2009-09-22
I would second the Acer Aspire Revo too. Check out [http://popey.com/blog/2009/08/06/acer-aspire-revo-ubuntu-boxee-and-remote-control/](http://popey.com/blog/2009/08/06/acer-aspire-revo-ubuntu-boxee-and-remote-control/)

---

### Post by newlinux on 2009-09-22
> **viridari said:**
> Hey folks. I just got an HDTV and would like to build a lightweight front-end box to attach to it.

* TV only goes up to 720p. I don't need to be able to handle 1080p or 1080i.
* I'd really like audio & video to work through HDMI.
* I don't need any optical disc capabilities on this box. I just want to play recorded TV shows and HD movies from my back end infrastructure.

Can anyone in-the-know recommend a good shopping list that will be Mythbuntu-friendly and achieve these objectives without breaking the bank?

Thank you!

I agree with the others about an acer aspier or other nvidia ION based product.

I would like to point out that just because your TV doesn't do 1080 i/p doesn't mean your frontend doesn't have to be able to handle it. If the source file you are trying to display is 1080i/p you'll still have to have the horsepower to decode it aand then scale it to 720p (same would be true if you were displaying to a SD TV). So really it is the format of the file you are trying to display (resolution, codec, bitrate) that determines your CPU/GPU needs, not your display device.

Luckily, if you get a VDPAU capable card/system (like the ION based systems) and stick to any of the popular codecs you will be fine - except for HD full screen flash video.

---

### Post by newlinux on 2009-09-22
for more ION based options, take a look at:

[http://www.linuxtech.net/features/nvidia_ion_products_overview.html](http://www.linuxtech.net/features/nvidia_ion_products_overview.html)

---

### Post by williammanda on 2009-09-22
After the info supplied by newlinux:

[http://www.linuxtech.net/features/best_linux_htpc_motherboards.html]("http://www.linuxtech.net/features/best_linux_htpc_motherboards.html")

I would buy this board:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500022&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Motherboards+-+Intel-_-ZOTAC-_-13500022]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500022&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Motherboards+-+Intel-_-ZOTAC-_-13500022")

Put a C2D or C2Q cpu and you have a sweet small form factor htpc that can view flash content like hulu.

---

### Post by viridari on 2009-09-24
Wow thanks so much for the great suggestions.

---

### Post by SiHa on 2009-09-24
Just a quick note.

First, thanks to Newlinux for the tips, I've been loking for just such a list.

I was seriously looking at the cheaper of the two AMD boards (Asus), until I checked the availability of Socket AM2 / AM2+ processors. Unless you going the eBay route, there's not much about - everything has moved onto AM3, so the Gigabyte board is probably the best bet.

---

### Post by viridari on 2009-09-24
OK I put something together in Newegg:
Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811120015](http://www.newegg.com/Product/Product.aspx?Item=N82E16811120015)
CF/SATA adapter: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812186051](http://www.newegg.com/Product/Product.aspx?Item=N82E16812186051)
4GB CF card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134514](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134514)
Memory: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227058](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227058)
System Board: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813500029](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500029)

I already have a 4GB CF card laying around so I won't actually be ordering one.

Cost of this system is about **$240**. It doesn't address the need for a remote control. I'm thinking of using my universal remote provided by Time-Warner Cable with the Scientific Atlanta 8300HD DVR plus an RS-232 IR receiver.

---

