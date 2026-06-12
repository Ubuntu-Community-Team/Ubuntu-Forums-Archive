---
title: "Help with motherboard choice"
date: 2011-01-27
forum: Mythbuntu
---

### Post by HarrisonFan on 2011-01-27
Hi,

I tried posting this in the Hardware / Laptop forum but it hasn't generated any responses yet. So, I figured I woud try here too.

I am putting together a Mythbuntu system and am looking for a MB with these specs but have been unable to find one. Any advice would be appreciated:

Form: MicroATX
CPU Socket: AMD3
HDMI output: 1 (or more)
PCI Express x1: 1 (or more)
Integrated Graphics: something that supports VDPAU (this seems to be the tricky one, I can find many MBs that have ATI for integrated graphics, but not very many with NVIDEA VDPAU support)
Integrated Audio: Yes

Thanks!

---

### Post by thatguruguy on 2011-01-27
Does it HAVE to be an AMD CPU?  An ION-based motherboard may work for you w/r/t all the other factors, except that it would use the intel Atom CPU.

---

### Post by HarrisonFan on 2011-01-28
Technically I suppose it doesn't have to be AMD, but I wanted something with enough power to be able to do Transcoding and commercial detection for two streams as well as be able to display 1080p over HDMI.  I chose AMD over Intel just because I have always had good experiences with AMD and it has always seemed to me that you get more for your $ than with intel.

I had thought a little about ION based combos and it seemed to me like it probably wouldn't have enough power for what I was wanting to do with it.

Thanks,
Zac

---

### Post by bb_145 on 2011-01-28
There is a fairly new motherboard from Zotac that uses a Celeron processor (instead of the Atom) and the ion graphics processor that might be interesting.

[http://www.zotacusa.com/zotac-ionitx-p-e-intel-celeron-su2300-1-2ghz-dual-core-mini-itx-intel-motherboard.html]("http://www.zotacusa.com/zotac-ionitx-p-e-intel-celeron-su2300-1-2ghz-dual-core-mini-itx-intel-motherboard.html")

Though I don't have any experience with it.

---

### Post by cascade9 on 2011-01-30
AFAIK there are no microATX AM3 motherboards with nvidia 8100/8200/8300 chispets. All the 'AM3' 8100-8300 chipsets I've seen are not 'true' AM3 anyway, they all use DDR2 (not DDR3, which 'real' AM3 uses)

IMO they arent worth it anyway, I have not been impressed with the newer nvidia chipsets. How the mighty have fallen.... 

A 880 + SB850 (not SB7XX, lots of the cheaper 880s have a SB7XX southbridge) would be your best bet for microATX. Sure, its got the onboard ATI video, but you can disable that and use a nice, cheap VDPAU capable GT210/GT220. 

890GX would work as well, but then you are paying more for the better onbaord video, which you wont use. 

If you decide to go full ATX, AMD 870 chipset boards + GT210/GT220 (again!) are what to look for.

---

### Post by LowSky on 2011-01-30
cascade9 brought up a great idea with the 880 chipset boards.

I can't state this enough but onboard graphics are hardly ever a good choice if you need it for HD video and transcoding. They use up precious onboard RAM and create more heat because the extra communication being done.

Realistically just get the cheapest AM3 board you can find, and then buy a Nvidia graphics card. In the end it might be the smae price as a higher end MB. People think they need all the extra features of a high end board but most never even use the options. 

here is a great option for a MB
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130295](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130295)
And here is one of the newer 430 chipsets for graphic cards (newer version of VDPAU)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162067](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162067)

---

### Post by nickrout on 2011-01-30
> **LowSky said:**
> cascade9 brought up a great idea with the 880 chipset boards.

I can't state this enough but onboard graphics are hardly ever a good choice if you need it for HD video and transcoding. They use up precious onboard RAM and create more heat because the extra communication being done.



Well I beg to differ. A revo makes a fantastic frontend. True you need 2G of RAM so you can allocate 512M to the video, but that's not a steep requirement.

---

### Post by HarrisonFan on 2011-01-31
What are your thoughts on this MB: [MSI ATX MB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813130235") ?

This appears to have everything that I was looking for, except in ATX form instead of microATX.

Thanks,
Zac

---

### Post by cascade9 on 2011-01-31
> **LowSky said:**
> I can't state this enough but onboard graphics are hardly ever a good choice if you need it for HD video and transcoding. They use up precious onboard RAM and create more heat because the extra communication being done.
 
 OK, I do find this sort of funny..you've said "get the cheapest AM3 board you can find" ubt thats a long way from the cheapest :lolflag: 
 
 You sort of have a point about the shared RAM, but its possible to find some onboard video using 'sideport' RAM (ie, RAM mounted onto the motherboard). As far as heat goes, using onboard wont make any extra 'communication' vs a PCIe card, and wont create any more heat from that. Any extra heat would be due to more powerful video chips (more MHz, more processors = more heat)

> **HarrisonFan said:**
> What are your thoughts on this MB: [MSI ATX MB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813130235") ?

This appears to have everything that I was looking for, except in ATX form instead of microATX.

Thanks,
Zac

Personally....I wouldnt touch it with a bargepole. 

I'll admit my bias, MSI has burnt me too many times. I'm also not a fan of the newer nVidia chipset, though I havent burnt myself with them I've help a few people out with them and its never been nice (worst case- a fairly 'top end' asus board that was returned 3 times, and still doesnt work....). 

I do find it interesting that MSI has given the motherbaord that LowSky posted a 3 year warranty, and that board only 1 year...which says a lot about the expected lifespan IMO. 

I wouldnt get to hung up with onbaord video, for a similar level card to what you get with onbaord 8100-8300 chipsets the power useage would only be a tiny bit higher. With a newer, smaller process and low power card (GT210, GT220, GT430) the power use from a standalone video card might be lower than with onboard video.

---

### Post by HarrisonFan on 2011-01-31
> Personally....I wouldnt touch it with a bargepole.

oh man, that's too bad. :( 

I pulled the trigger on that MB last night while there was still a rebate for the board.  I guess I should have posted it here earlier. Now I feel foolish.

Well, live and learn.  I guess I will have to hope that I don't have any problems with it and everything works great.  

I am planning to pair this with an AMD Triple core 3.1 Ghz. I believe this should have more than enough power for what I am looking for. 

Here's hoping that my build turns out alright!

Oh, and I looked at the MSI website and it appears that all their Motherboards are covered by a [3 year warranty]("http://us.msi.com/html/popup/CustService/General_war.html").  So, maybe Newegg is wrong?

---

### Post by HarrisonFan on 2011-01-31
Here are the other components I am looking to use:

CPU: [AMD Athlon II X3 445 Rana 3.1GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103872")

RAM: [CORSAIR XMS3 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333]("http://www.newegg.com/Product/Product.aspx?Item=20-145-251&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=AMD#scrollFullInfo")

Case: [APEVIA Black / Silver SECC Steel / Aluminum X-MASTER-AL/500 ATX Media Center / HTPC Case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811144230")

CD/DVD Burner: [Sony Optiarc]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827118039&cm_re=sony_optiarc-_-27-118-039-_-Product")

Additionally, I already have:

Western Digital 2Tb Caviar Green drive
Hauppauge 2250 Dual Tuner


Anyone see any other problems with this setup?

Thanks,
Zac

---

### Post by HarrisonFan on 2011-01-31
Looks like I could still cancel that MSI motherboard order.  I would need to find an alternative quick.  Basically looking for: a great MB ATX or microATX with

1. VDPAU capable either integrated video or low power video card with HDMI Out that would easily work in mythbuntu
2. Integrated audio (audio over HDMI)
3. Socket AM3 

All for around 80$ or slightly more if it is worth it.

Thoughts?  Should I cancel my order while i still can?

---

### Post by cascade9 on 2011-02-01
> **HarrisonFan said:**
> Oh, and I looked at the MSI website and it appears that all their Motherboards are covered by a [3 year warranty]("http://us.msi.com/html/popup/CustService/General_war.html").  So, maybe Newegg is wrong?

Possibly. I _think_ from what a sales rep once told me that MSI offers 3 years on new parts, but its possible its not exactly 'new', that its a used motherboard thats been refurbished. 

I'd have no way of telling that for sure. 

It is also interesting that if you search for "NF750-G55 warranty" (without quotes) it seem that there is more than just newegg giving a 1 year warranty on that board (though most offer 3).

> **HarrisonFan said:**
> Looks like I could still cancel that MSI motherboard order.  I would need to find an alternative quick.  Basically looking for: a great MB ATX or microATX with

1. VDPAU capable either integrated video or low power video card with HDMI Out that would easily work in mythbuntu
2. Integrated audio (audio over HDMI)
3. Socket AM3 

All for around 80$ or slightly more if it is worth it.

$80 for a board, easy, $80 on a board + video....not really. 

I'll put in what I would look at anyway ;) 

Buget option- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179)

Nicer but more expensive-
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128451](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128451)

Same board as above with USB 3.0 for an extra few dollars- 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128431](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128431)

If it was me, I'd get the gigabyte. 

As for cheap, VDPAU capable video-
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600007321&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600007321&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

I'd probably get the MSI or Asus GT210 with passive cooling. 

You wont need 4GB, 2GB should be fine..but you'll only save $15 so I'd probably get 4GB. Unless of course it stops you from getting something else you want. 

I was talking to the only person I know who uses myth much, and from what he was saying it seemed like a dual-core should do commercial detection just fine. Again, I'm not sure if its 'worth' dropping to a dual core, you only get a small amount of money saved, but same as above. BTW, the new Athlon II dual cores have 1MB cache per core, not 512k like all the other current AMD desktop CPUs. So I'd guess that there would be some situations where the dual core would be faster, if only due to cache.

---

### Post by HarrisonFan on 2011-02-01
cascade9, Thanks for the help!  

One other quick question (well 2).  By using the HDMI out on a video card will I still be able to send both audio and video over that connection?

And thoughts on this one [GIGABYTE GA-880GM-D2H AM3 AMD 880G]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128458&nm_mc=EMC-IGNEFL020111&cm_mmc=EMC-IGNEFL020111-_-EMC-020111-Index-_-AMDMotherboards-_-13128458-L08A")?  

Thanks!

---

### Post by cascade9 on 2011-02-01
No problem ;) 

Yes, you can.

---

