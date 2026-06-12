---
title: "Intel Graphics?"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by Elvish Legion on 2006-02-25
I know it isn't the best solution but I am trying to buy a notebook but I don't have the 1000+ USD most with nVidia cost...so does Intel work better than ATI?

---

### Post by audax321 on 2006-02-25
You might want to post what Intel and ATI cards you're specifically looking at. ATI will give you better performance in an integrated solution, but I really don't like their drivers. I had an ATI 9700 in my desktop and it kept locking up every 3 or so hours. After I put in an nVidia, didn't have a problem again. So when I bought a laptop I went with an Intel Graphics Media Accelerator 900 (integrated). It's not the fastest out there, but it gets the job done. It's supported with the i810 driver under Linux, but the performance could be better (for composite, etc.) and from what I've heard should be better under xorg 7.0 which Dapper will have.

---

### Post by Sirin on 2006-02-25
Well, you're going to have to do some tweaking to get Intel cards to work under Ubuntu (taken from personal experience) . You won't be able to play games like Enemy Territory, but if you don't play games, then you won't have that many problems. But it WILL require tweaking. Ubuntu is best done with an NVIDIA card, but since you don't have the money, prepare to start tweaking like hell. ;)

---

### Post by Sirin on 2006-02-25
[QUOTE=audax321]It's supported with the i810 driver under Linux, but the performance could be better (for composite, etc.) and from what I've heard should be better under xorg 7.0 which Dapper will have.[/QUOTE]

Intel cards SUCK when it comes to composite performance. They aren't made for special effects. ;)

---

### Post by audax321 on 2006-02-25
[QUOTE=Sirin]Intel cards SUCK when it comes to composite performance. They aren't made for special effects. ;)[/QUOTE]

That's what I thought too. But the GMA 900 with the new drivers in xorg is supposed to have full hardware acceleration (see here with Gentoo: [http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nc6220](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nc6220))

Also, when the GMA900 was marketed Intel said it was supposed to handle Vista effects. And it does play UT2004 fairly well at medium settings under Windows. It can't really play it under Linux. It's not a video card to use for gaming anyway.

That said, I personally haven't tried composite or XGL on it yet... I'm waiting till Dapper is final before I mess around with that. But the person at the above link supposedly has Transparency working without slowdown.

---

### Post by Elvish Legion on 2006-02-25
So I should try to go with an ATI card? I wish I had the money for an uber gaming laptop but this is going to be more for school and the games I play are kinda gentle on system (WoW is surprisingly light on system reqs)

---

### Post by audax321 on 2006-02-25
Well, when do you need it by? If you can wait a few months it would definitely be worth it for more Intel Duo Core laptops to come out. Also, just some advice from my experience with buying a laptop for school... go with something small and portable. I originally bought a Dell Inspiron 9300. It was an awesome laptop, nVidia GeForce Go with a huge 19" screen. Lugging it around got old really fast. Fortunately my sister needed a desktop replacement so I gave it to her. I went with a 14" HP DV1000. I think anything below 15" is perfect for portability... anything bigger and you really push it. If you have a desktop, just keep that for gaming. Laptops are nice to game on since they are portable, but they still don't perform as well as desktops and upgrading is almost impossible. Also, I think the next model of the HP DV1000 called the HP DV1000t is going to be really nice, Google it for the specs, but I believe it will have an integrated webcam w/microphone and dual core. It's video card is going to be an Intel 945GM though. I don't know if that will be good enough for games or not. If your school is heavily reliant on Windows, you might need to look around for any information you can get about Vista's system requirements although MS has been pretty tight lipped about it (and you probably won't be able to run Aero Glass from Vista on it unless it's got a really good video card).

---

### Post by Elvish Legion on 2006-02-26
I'd like to get it soon as I'm worried the longer I wait the more expensinve things will get (Dual core laptops will be pretty pricey for a while won't they? Even in a month or so I couldn't save enough money to get a great laptop (was looking about 1400 US from ibuypower.com but one of my dogs got sick so thats outta the picture now...family first)

---

### Post by audax321 on 2006-02-26
Wow. I just checked HP and the dv1000t is already out. They are selling it side-by-side with the single core one: [http://www.shopping.hp.com/webapp/shopping/computer_series.do?series_name=dv1000_series&catLevel=2&category=notebooks/hp_pavilion&storeName=computer_store](http://www.shopping.hp.com/webapp/shopping/computer_series.do?series_name=dv1000_series&catLevel=2&category=notebooks/hp_pavilion&storeName=computer_store)

Unfortuantely, there is a $350 price differance. :(  In any case, if you're not worried about gaming I would recommend the HP DV1000 only because just about everything works under Linux and you won't have to mess around with video card drivers since the i810 driver is included with most distros (if you have a Circuit City, Best Buy or something around where you live they should have display models set up you can go mess around with). Other good portable laptops are:

Dell Inspiron 710M. (but it has 12" screen and slower Intel Extreme graphics)
Dell Inspiron 600M (14" screen with ATi® MobilityTM RADEONTM 9000 4X AGP and not widescreen)

Also stick with Pentium M... you definitely don't want Celeron M if you want to keep the laptop around for awhile. And if you go with Dell, do a google search for DELL COUPONS because they frequently have 30-35% coupons floating around. HP normally has specials going on as well, but they normally just give you a free crappy priner :rolleyes: 

Anyway, I can't really be of much help with the whole ATI vs. Intel debate, I'm a bit parcial towards Intel because they seem easier to deal with. Hopefully someone can post their experiences with an integrated ATI laptop video card.

Also, if you haven't taken a look there is a wiki with a list of laptops that work well with Ubuntu (can't seem to find the link now though). Also, check out [http://www.linux-on-laptops.com](http://www.linux-on-laptops.com)

Sorry about your dog btw :(

---

### Post by Elvish Legion on 2006-02-26
What about

[http://www.newegg.com/Product/Product.asp?Item=N82E16834224045](http://www.newegg.com/Product/Product.asp?Item=N82E16834224045)

I can prolly have my mom help me buy it....

---

### Post by audax321 on 2006-02-26
Well the laptop looks good. All the parts look like they should run under Linux (except probably the card reader...the integrated ones almost never work). But, I couldn't find anything on Google about anyone using it under Linux. I don't know about the processor speed though, 1.6 seems kind of low to me. It's really a personal decision though and depends on how long you want to keep the laptop around. If you take good care of it a laptop can last you up to 3 years or more. I went for 2.0 when I bought mine because my laptop before that was almost 4 years old and I remember how much it could have benefited from a few extra megahertz. Also the extra Ghz will help keep some strain off of the video card. Definitely a nice laptop though, especially because the video card has dedicated RAM.

---

### Post by knalle on 2006-02-26
its only me, but my advice is to go with a nvidia card if you want to run it with linux, nvidia has better driver and opengl support in my opinion.

---

### Post by Elvish Legion on 2006-02-26
Well I ended up with an ATI card (Bleh I know) simply because it was the best deal I found.
[http://www.compusa.com/products/product_info.asp?product_code=51909313&pfp=cat3]("http://www.compusa.com/products/product_info.asp?product_code=51909313&pfp=cat3")

Specs for those that don't want to look

Proc: Intel Penitum M 1.4 (My understanding is that the clock speed for a Pent M is equal to the twice that of an equal Pent 4....not sure if thats true)
Ram: PC 2100 DDR SDRam 512 Install 2 gig max
HD: 5400 RPM 40 Gig 
DVD Rom: 8x Dvd Rom (Going to buy a USB one for burning and the like)
Graphics Card: ATI (BLAH!!!!) Mobility RADEON 7500 (32 mb expended to a 32 dedicated and 32 share from what I've read)


Weight is about 5 pounds (4.9)

14.1 screen (small and light)

I know the ATI Radeon 7500 Mobile isn't an uber card but the 7500 desktop verison can play WoW which is good enough for me.

I spent a total of 768.68 after taxes and 2 day (10.07 Shipping)'

What ya think? Not the best for linux but at 17 you have to kinda go with what you can afford no?

Elvish

---

### Post by audax321 on 2006-02-26
Okay, but also make sure that you are getting the newer Pentium M. There were two versions released and the older one underperformed. I think the new ones are based on the Sonoma core and the older ones were Dothan? :confused:

EDIT: I posted that before looking at the link. :) Anyway I don't know if it's old or new, but in any case, you got a good price for that. IBM is a good manufacturer.

---

### Post by Elvish Legion on 2006-02-26
[QUOTE=audax321]Okay, but also make sure that you are getting the newer Pentium M. There were two versions released and the older one underperformed. I think the new ones are based on the Sonoma core and the older ones were Dothan? :confused:

EDIT: I posted that before looking at the link. :) Anyway I don't know if it's old or new, but in any case, you got a good price for that. IBM is a good manufacturer.[/QUOTE]


Which year did the new ones start?

---

### Post by audax321 on 2006-02-26
According to this article: [http://www.pcworld.com/news/article/0,aid,116264,00.asp](http://www.pcworld.com/news/article/0,aid,116264,00.asp)

The new Pentium M's only came in 1.7 or higher when they were launched (I think they might have made a 1.6 version later on). The IBM appears to have the older Pentium M. Also, if you notice they don't mention the numerical processor number anywhere which is characteristic of the newer Pentium M's.

Another way to tell is that the newer ones have a L2 cache of 2MB... that IBM only has a L2 cache of 1MB.

---

### Post by Elvish Legion on 2006-02-26
[QUOTE=audax321]According to this article: [http://www.pcworld.com/news/article/0,aid,116264,00.asp](http://www.pcworld.com/news/article/0,aid,116264,00.asp)

The new Pentium M's only came in 1.7 or higher when they were launched (I think they might have made a 1.6 version later on). The IBM appears to have the older Pentium M. Also, if you notice they don't mention the numerical processor number anywhere which is characteristic of the newer Pentium M's.

Another way to tell is that the newer ones have a L2 cache of 2MB... that IBM only has a L2 cache of 1MB.[/QUOTE]


Well even if it is the older M class it is still a pretty good deal (best I found) I may up the ram to a gig later but not a concern right now...now comes the wait (2 day shipping could get here tuesday or as late as thursday depends how fast they process) 

Then comes the setting up ATI driver (gah its horrible!) shame automatix doesnt have the driver.

After that comes enjoying the fact I can leave my room and still use my comp!!!

I'm excited first notebook....do we all agree its at least a decent deal (seems these beasts retailed at like 3kish....)

Who knows it may have the newer core and just be a typo (though it appears to be like 3 years old its still ok)

---

### Post by kar-tar on 2006-03-21
You were smart to go cheap.

Laptops haven't gotten significantly better in about a year or a year and a half.  That's about to change.  Pretty soon, dual-core systems with more storage, and more ram installed are going to drop fast in price.  I think the smart thing to do right now is to go cheap, so that you'll have the money in a year or two to get something really cool.

Also gaming... eh... I think the moment the graphics cards got more expensive than the games was the moment I switched to consoles (that and the big publishers put all the wonderful independant houses of the 90s out of business, thus killing creativity on the PC platform) PC gaming used to be the budget option (you had the computer for work, why not buy a game or two) and now it's just for rich kids.  WoW were smart to keep requirements low, a whole lot of people out there aren't going to drop a couple of C-notes on nVidia's latest whatever.  I'm certainly not.

---

