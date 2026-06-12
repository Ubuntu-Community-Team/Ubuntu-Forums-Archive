---
title: "MSI Media Live HTPC"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Leo B on 2007-04-09
I have been waiting for something like this to make a media tv (music server, TiVo functionality via Myth TV with HDTV via ATSC/QAM tuner card):
[http://global.msi.com.tw/index.php?func=downloaddetail&type=manual&maincat_no=134&prod_no=1113](http://global.msi.com.tw/index.php?func=downloaddetail&type=manual&maincat_no=134&prod_no=1113)
Has anybody tried this yet (MSI Media Live with Ubuntu/Myth)?
From what I can tell, the the built in HDMI video via the NVIDIA GeForce 6150 LE Graphics should just work, as should the Realtek High Definition Audio.  I was wondering about secondary functions, like the supplied Remote Control.  Will this work under Ubuntu/Myth too?
Thank you for your help.

---

### Post by tgm4883 on 2007-04-09
400 and you still need, ram, cpu, hard drive, etc.  Seems like you could do better building yourself.  Not to mention that you can only add 1 pci card (only record 1 channel at a time).  If you were going to spend the money, a seperate front end and backend end is the way to go.  I think there's a via C3 that can play HD content.

---

### Post by Leo B on 2007-04-11
I don't think I could do cheaper (unless I went big noisy beige box) but I could do more expandable.  I would not mind 2 or 3 PCI Express slots and 3 or more drive bays (I could do RAID 5 then).  I have been looking (in vain) for  a dual digital video (ATSC/ATSC, ATSC/QAM or QAM/QAM) PCI card.  With a more capable system, I could just use 2 cards, but all the "more capable" systems are a lot larger, rather than the 17" x 12" footprint of the Media Live (which pretty much matches all of my other AV components) I would end up with some 17" x 17"+ monstrosity (i.e. Sonata).  With the Media Live, by best option is probably the Silicon Dust HDHomeRun for a dual digital tuner.  Not as integrated, but Ethernet broadcasting has its own advantages.  And it leaves that PCI slot open....

---

### Post by tgm4883 on 2007-04-11
your looking at at least $700 for that.  You could easily get all the parts for less than that.  I built one thats almost silent for around $500.  However it can also only have 2 pci card (has pcie slots too). 

But if money isn't the issue, and you like the looks of it then I don't see a problem with what your looking at.  Of course, if money isn't an issue, then you really should do a seperate backend with something like a via c7 running in your frontend.  Then you could hide the big backend, while keeping the frontend tiny looking.

---

### Post by Leo B on 2007-04-12
So tgm4883, are you suggesting a client-server model, where the server includes the tuner card(s) and could be remote from the AV rack (connected only by Ethernet or 802.11b/g) and the AV rack contains only a relatively thin client (CentrinoM or Sempron or even a ViaC3/C7 or Geode)?

I can see the advantages of such an architecture, but I am in a condo now and an extended stay in France may be in the near future (makes my condo look large, I realize I will have to change to or add a DTV-C tuner card for Europe but they have these things as USB dongles over there).  So for these reasons, I am tending toward a single smaller box rather than a two-box client-server model.  In fact, at one point I considered a Laptop with the HDHR (the USB DTV-C in Europe) and a big USB hard-drive or two for media.  Even my 3yr old Dell M60 has no problem serving up HDTV but it lacks an HDMI output (which is not an issue until I select a hi-def DVD player).

I would like to see a summary of your system, it sound like you put $500 to very good use.

---

### Post by tgm4883 on 2007-04-12
> **Leo B said:**
> So tgm4883, are you suggesting a client-server model, where the server includes the tuner card(s) and could be remote from the AV rack (connected only by Ethernet or 802.11b/g) and the AV rack contains only a relatively thin client (CentrinoM or Sempron or even a ViaC3/C7 or Geode)?

I can see the advantages of such an architecture, but I am in a condo now and an extended stay in France may be in the near future (makes my condo look large, I realize I will have to change to or add a DTV-C tuner card for Europe but they have these things as USB dongles over there).  So for these reasons, I am tending toward a single smaller box rather than a two-box client-server model.  In fact, at one point I considered a Laptop with the HDHR (the USB DTV-C in Europe) and a big USB hard-drive or two for media.  Even my 3yr old Dell M60 has no problem serving up HDTV but it lacks an HDMI output (which is not an issue until I select a hi-def DVD player).

I would like to see a summary of your system, it sound like you put $500 to very good use.

Athlon X2 3800+  	      $100
Gigabyte GA-M61VME-S2	$75 (Onboard Video, but plays HD just fine, Has PCIE 16x incase I want to upgrade, also, it's microATX, so I was looking at these cases [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010090007%201054821746&bop=And&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010090007%201054821746&bop=And&Order=PRICE) ) 
1 Gig Ram (533)		       $80 (On sale)
400GB HD		          $100
Case 			              $100-125 (Was looking at a few cases in this range, but used an old one I had instead)

pcHDTV 5500		       $129
PVR-150			           $80

So around $700* total

*estimate does not include TV

I forgot to add the cards when I was giving the estimates, but I forgot to add the cards when I quoted you $700.  I find that there are three things you need to consider when purchasing a system, and everyone has to order them to their own preferences.

1.  Performance
2.  Polish (had to bust open the thesauraus to get a p word for looks)
3.  Price

My main concern was price, so i went with a single frontend/backend solution.  I got a dual core as I wanted to be able to view HD content as well as be able to relegate this to a dedicated backend in the future (I live in an apartment now).  Polish was the last of my concerns which is why I chose an old case rather than a new one.

For your setup, if the price is right and you like the looks then go for it.  At least look at the other cases though and price some stuff out.  You may be able to save yourself a couple hundred (which could then be spent on another HD tuner :D )

---

### Post by frafu on 2007-05-08
@tgm4883

Thanks for listing the components of your htpc and now I have the following question: 

The gigabyte motherboard that you listed has a vga port! Is it not necessary to have a dvi/hdmi port to output hdtv?

Thanks in advance.

---

### Post by Leo B on 2007-05-10
No frafu, VGA will display HDTV just fine (heck, it can go way beyond HDTV, like on my computers 1920x1280 monitor).  

What you may be thinking of is restrictions that will only let you play HDTV on an HD disc (HDDVD or BluRay) content through HDMI.  If you try to play HDTV content from an HD disc through component or even DVI, the signal is degraded to SD (480p).  This is NOT a technical limitiation of DVI or VGA, it is strictly a sort of "copy protection" scheme built in to (supposedly) defeat copying digitally HD copyright material.  Very lame, and real kick in the nads for early adopters of large panel (and very expensive back then) HDTVs that predated HDMI (they will NOT play HDTV from an HD disc from a commerical HD disc player).  Major Bummer, and pretty stupid (in its combination of ineffectualness and annoyance).

---

### Post by frafu on 2007-05-11
Hello Leo B, 

Thanks for your explanation. 

By the way, I have found this site about [HTPC under Linux]("http://www.linuxis.us/linux/media/howto/linux-htpc/index.html") which might be interesting. 

Have a nice day.

---

