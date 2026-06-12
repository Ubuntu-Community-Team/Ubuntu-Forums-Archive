---
title: "First Mythbuntu build"
date: 2011-02-03
forum: Mythbuntu
---

### Post by TorturdChaos on 2011-02-03
I've used Ubuntu on my laptop for a while, and am somewhat familor with it.  Well now I'm looking at setting up a Mythbuntu system.
I have spent some time reading through the info on video cards and capture cards that work well with MythTv/Mythbuntu, and I think these should work - but I would welcome any input form more experienced peoples.

I already have part of the computer - 2.8ghz P4D - Dual Core, 2gigs DDR2 Ram, Case, 600watt PSU, and Asus Mobo.

Adding to that:
TV Tuner Card:
[Hauppauge WinTV-HVR-1600 ATSC/ClearQAM/NTSC TV Tuner PCI w/Remote 1199 PCI Interface]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033")

Video Card:
[HIS H467QR1GH Radeon HD 4670 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready CrossFireX Support Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161315")

Hard Drive: 
[Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136533") (Already have 2 of these, rather fond of them :D)

As for the exact use its going to be both the backend and the frontend, with 1 cable connection coming in to the tuner card, then going outa via HDMI to a 55" HDTV (not sure the exact one still shopping for that).  I'm pretty sure that the TV Tuner card I picked will work with Mythbuntu setup, but it would be nice if someone could confirm that.
Also I believe that graphics card should work well with my system, just not sure if the video decoding during play back will be offloaded to the video card correctly.  I couldn't really find an exact answer to that.
Also, does anyone know if the HDMI works well for out on the HD 4xxx cards with Mythbuntu?

Feed back would be great.

Thanks!

---

### Post by nickrout on 2011-02-04
NOOOOOO

Do not buy the radeon card.

Get an nvidia GT430, it WILL offload to the GPU using VDPAU, the radeon will not. Avoid ATI like the plague for mythtv display.

---

### Post by thatguruguy on 2011-02-04
> **nickrout said:**
> NOOOOOO

Do not buy the radeon card.

Get an nvidia GT430, it WILL offload to the GPU using VDPAU, the radeon will not. Avoid ATI like the plague for mythtv display.

this.

---

### Post by TorturdChaos on 2011-02-04
> **nickrout said:**
> NOOOOOO

Do not buy the radeon card.

Get an nvidia GT430, it WILL offload to the GPU using VDPAU, the radeon will not. Avoid ATI like the plague for mythtv display.

Oh man so glad I asked before ordering anything!!!
Ok so something like this should work fine:[ASUS ENGT430/DI/1GD3(LP) GeForce GT 430 (Fermi) 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready  Low Profile Ready Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121397")


Any other recommendations or things I out right buggered up :P

---

### Post by newlinux on 2011-02-04
For noise reasons, I personally look for fanless cards. The GT430 is great, but you may be able to save some money by going to a GT2xx series, which will do great in an HTPC, and supports VPDAU as well.

As for your TV, when you narrow down the models, a quick google for mythtv/linux/htpc and the TV might help determine if anyone's had any problems - but you are pretty safe with TVs these days.

---

### Post by TorturdChaos on 2011-02-04
> **newlinux said:**
> For noise reasons, I personally look for fanless cards. The GT430 is great, but you may be able to save some money by going to a GT2xx series, which will do great in an HTPC, and supports VPDAU as well.

As for your TV, when you narrow down the models, a quick google for mythtv/linux/htpc and the TV might help determine if anyone's had any problems - but you are pretty safe with TVs these days.

Ok thanks :D.  I'm not too concerned with noise, as its going to be in the same room as my desktop which well has a lot of fans :P.
Might go with a GT2xx card tho to save some money.


EDIT:
Think I have narrowed down the TV I want. Looking very hard at the Samsung UN-55C6500 TV.  Anyone ever had any troubles doing HDMI out from a Mythbuntu box to this TV??

Thanks

---

### Post by newlinux on 2011-02-04
One my tvs is a couple year old 32" Samsung which works wonderful (and has a wonderful picture) with my mythbox (via HDMI). I know it's not the same set - but just thought I'd offer that up. That one looks great and will probably work fine with little hassle.

---

### Post by TorturdChaos on 2011-02-06
> **newlinux said:**
> One my tvs is a couple year old 32" Samsung which works wonderful (and has a wonderful picture) with my mythbox (via HDMI). I know it's not the same set - but just thought I'd offer that up. That one looks great and will probably work fine with little hassle.

Thanks :D.  This is a new adventure for me, so any input helps.  Can't wait to order all the parts and the real fun to begin :P.

Also, I forgot to mention that the HDMI is going to be routed through a 5.1 surround sound reciver then into the TV.  I'm hoping that doesn't cause any problems ( I know how fickle S-Video can be when running to a TV......)

---

### Post by heckheck on 2011-02-19
You'll want to probably go with the GT430 card over the GT2xx if you plan on streaming high bitrate audio formats (as used in BluRay) to a receiver over the HDMI connection.  The 2xx cards do not support Dolby TrueHD or DTS-HD Master Audio (see here [http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2796&p_sid=2V2Ikojk&p_lva=2593&p_accessibility=0&p_redirect=&p_srch=1&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MiwyJnBfcHJvZHM9MiZwX2NhdHM9NTcmcF9wdj0xLjImcF9jdj0xLjU3JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1ndDI0MCBoZCBhdWRpbw!!&p_li=](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2796&p_sid=2V2Ikojk&p_lva=2593&p_accessibility=0&p_redirect=&p_srch=1&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MiwyJnBfcHJvZHM9MiZwX2NhdHM9NTcmcF9wdj0xLjImcF9jdj0xLjU3JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1ndDI0MCBoZCBhdWRpbw!!&p_li=)).

The GT430 is a slower card than the GT240, but that shouldn't matter much for decoding video.  There are currently some obscure cadence detection issues with the GT430 but that only really affects PAL (2:2 pulldown and some other weird cadences).

---

