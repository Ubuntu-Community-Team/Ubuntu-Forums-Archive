---
title: "buying a new machine -looking for recommendations"
date: 2010-09-23
forum: Multimedia Software
---

### Post by strider3700 on 2010-09-23
My current machine is well past it's end of life so I'm looking into a new PC.   This will be for work which is software development under windows these days.  I've been running ubuntu 10.04 on an athlon 3500 with 1 gig.  I run virtualbox with XP as a guest and do my work under there.   I'd like to keep the same setup.

My hope is that the new machine can be ubuntu with virtualbox running for development  and I'd like to use it with XBMC or equivalent to let the kids watch tv while I'm working on the pc.   

I'm hoping that a core 2 quad 8400 and 8 gigs of ram will let me get away with this power wise  but I'm lost where to go on the video cards.  Playing with a system builder the gt210 and the radeon 5450 are both inexpensive and have hdmi out for the tv.  I am not a gamer so 3d performance is not critical

Anyways I'm not sure if radeon is better then nvidia for linux support these days or not.   I only care about it working not it being open source drivers.

Also am I asking to much to think I can run visual studio in virtualbox at the same time xbmc is grinding away in the background?

thanks for any help

---

### Post by Ghost|BTFH on 2010-09-23
Howdy,

nVidia driver support is still a tiny bit better than ATi at the moment, but that being said, they both work pretty well in Ubuntu currently.

Running a quad core + 8gb of ram should do you well, depending on what the resources are you're requiring.  For example, if you're needing 2gb for VirtualBox and 4gb for your desktop and programs, you're fine.  But if you're needing 4gb for VirtualBox and 3-4 for the desktop, you should consider going up even higher.

For VirtualBox, whatever you give it in RAM is what it'll use - even if the OS isn't utilizing it.  Just keep that in mind.

Personally, if you're going with this serious of a setup, make sure your motherboard is top notch - I would go with one of the higher end quality ASUS boards that can handle the new SATA3 and 1600Mhz non-OC DDR3 RAM because if you're going to be doing a lot of grinding, you want your bottlenecks opened up as much as possible - those being the data transfer rate of your hard drive (6gb/s vs. 3gb/s is a big jump) and your RAM (a true 1,600 vs. 1,333 is another big jump).

Doing these things and making sure you're running Ubuntu 64bit should really make your system hum.

Cheers,
Ghost

---

### Post by cascade9 on 2010-09-23
Q8400 would be nice, but you might get a bit more performance from an Phenom II X4 945/955/965, or even an X6, they are only a bit more than the cost of a Q8400. 

> **Ghost|BTFH said:**
> Personally, if you're going with this serious of a setup, make sure your motherboard is top notch - I would go with one of the higher end quality ASUS boards that can handle the new SATA3 and 1600Mhz non-OC DDR3 RAM because if you're going to be doing a lot of grinding, you want your bottlenecks opened up as much as possible - those being the data transfer rate of your hard drive (6gb/s vs. 3gb/s is a big jump) and your RAM (a true 1,600 vs. 1,333 is another big jump).

You wont find many, if any SATA III ports on a socket 775 (to suit Core2Duo/Quad) motherboard...and if you dont find any, they will be via nasty cheap 'SATA RAID' controllers by marvel, or something equally junk. 

SATAIII is great for future upgrades, and/or if you want to run a SSD (some of the SSDs are already maxing out SATAII). For HDDs, it wont make any real difference at all....HDDs still havent broken through the maximum bandwidth of SATAI.  

DDR3 is nice as well, and there are some socket 775 motehrboards that use it. 

Personally, I'm not that impressed with the newer Asus boards, IMO they have been going downhill for a fairly long time. I perfer the gigabyte boards these days. I can see that is just my point of view though, and I'd rather have an asus than a ECS. ;)

---

### Post by cchhrriiss121212 on 2010-09-23
I agree with what is said above, though I think your proposed hardware is more than enough.
With a quad core and a gt210/220 you will barely notice XBMC running. If you use vdpau output you will only be using <5% cpu and only a small chunk of that 8GB RAM.

---

### Post by perspectoff on 2010-09-23
This is an expensive time of year to buy. If you wait another few weeks, prices ought to come down. They then go back up in November for the Christmas rush.

October and February are traditionally the least expensive times of year.

In October they move out inventory to make way for Christmas inventory, and in February they move inventory for tax purposes.

---

### Post by Ghost|BTFH on 2010-09-23
> **cascade9 said:**
> You wont find many, if any SATA III ports on a socket 775 (to suit Core2Duo/Quad) motherboard...and if you dont find any, they will be via nasty cheap 'SATA RAID' controllers by marvel, or something equally junk. 

SATAIII is great for future upgrades, and/or if you want to run a SSD (some of the SSDs are already maxing out SATAII). For HDDs, it wont make any real difference at all....HDDs still havent broken through the maximum bandwidth of SATAI.  

DDR3 is nice as well, and there are some socket 775 motehrboards that use it. 

Personally, I'm not that impressed with the newer Asus boards, IMO they have been going downhill for a fairly long time. I perfer the gigabyte boards these days. I can see that is just my point of view though, and I'd rather have an asus than a ECS. ;)

Good points made, especially since I wasn't paying attention and didn't notice he was talking about an Intel chip.  My bad.

On that note, my personal take on Intel is that they are much like buying a Jaguar - a whole lot of brand name and not a whole lot of performance for the price.  The best bang for the buck is indeed an AMD chip, a Phenom x4 would do nicely and would put to shame Intel chips similarly priced.

So, talking from an AMD point of view, Asus is still the way to go for motherboards, you can find one with a TRUE 1,600Mhz (non-OC) DDR3 capable board WITH SATA III riding high on the hog.

As for the hard drives, they haven't hit the top speeds - yet.  There is a small improvement from SATA II, which is a vast improvement over SATA I.  Not sure where you're getting your info from that HDDs haven't really broken through SATA I, but that's simply false.

With that in mind, granted the latest/greatest SATA III HDDs currently aren't going to fully take advantage of Asus's dual bandwidth chipset on the SATA channel currently, but they will utilize more of it than a SATA II HDD will.  So you WILL notice slight improvement over II, and later down the road when SATA III becomes more commonplace, you'll see HDDs that can actually utilize the full bandwidth that Asus has so nicely set up for us.

This information comes from benchmarking results that show Asus SATA III read/write speeds to be superior to Gigabyte's III and previous SATA II benchmark results (Which even Gigabyte's III beats).  Please refer to Tom's Hardware Guide, Legitreviews.com or other such websites for more information on this.

As with all information, arguing a fact requires contradicting fact.

These opinions come from 10 years professional experience doing computer repair and custom system building, as well as 30 years total experience with computers, just FYI.

As with all opinions however, take them for what they are - the ravings of a mind different from your own.

Cheers,
Ghost|BTFH

---

### Post by strider3700 on 2010-09-23
THanks for the information guys.   I'm not opposed to AMD,   I have been very happy with my 3500+ for the last 6 years.  I had heard that AMD has fallen behind lately  so I was mostly looking at intel.  Perhaps that isn't true.

 I haven't checked benchmarks  and I'm not really sure it matters.  my 3500+ was almost enough to do what I needed (except for the XMBC at the same time) however lately it's feeling a little slow, the hardware is slowly dying and I could use a write off for the company so a new machine makes sense.   Pretty much anything beyond bottom of the barrel is going to be a big improvement over what I have. I'm not sure that it will matter if I'm going sata II or sata III,  I'm currently running IDE... and 8 gigs of ddr 3 at 1300 or 1600 is going to destroy my 1 gig of ddr..  

Energy efficiency is a concern for me.  looking at some of these chips running at 125W is kind of shocking.  I see AMD has a x4 900e that uses 65W  which is nice for a machine that will be running 24/7 for the next 5+ years. 

Good point about waiting a few weeks.  I'm torn between building/ordering my own exactly like I'd like and buying a prebuilt from a big box store.    Assuming I want a specific cpu like the 900e I'll probably have to build.

---

### Post by cascade9 on 2010-09-23
> **Ghost|BTFH said:**
> As for the hard drives, they haven't hit the top speeds - yet.  There is a small improvement from SATA II, which is a vast improvement over SATA I.  Not sure where you're getting your info from that HDDs haven't really broken through SATA I, but that's simply false.

SATAI = max bandwidth 150MB/sec. SATA II = 300MB/sec, and SATAIII  600MB/sec. 

I'f your thinking of this test, I'm suspect on it- 

[http://www.tomshardware.com/reviews/amd-890gx-radeon,2571-7.html](http://www.tomshardware.com/reviews/amd-890gx-radeon,2571-7.html)

That shows a seagate barrcuda doing a minimum of 168000kB/sec. Odd, considerign that they have the same drive at 'max read throughput' @ 127MB/ec here- 

[http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/h2benchw-3.12-Max-Read-Throughput,1009.html](http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/h2benchw-3.12-Max-Read-Throughput,1009.html)

Its possible that test was on a different SATAII controller, and the SB850 in the GX890 coudl get a few % more than that, but the amount of difference is a bit too much for me to believe it. 

If your talking about this- 

> According to the demo, the SATA2 drive (a 7200.12 Barracuda) topped out around 288 MB/sec, running just below the standards top theoretical speed. The SATA 3 drive, a Seagate Barracuda SATA 3 prototype, reached a staggering 589 MB/sec, more than double the speed of the SATA 2 setup.[http://www.tomshardware.com/news/Seagate-AMD-SATA3-Standard,7223.html](http://www.tomshardware.com/news/Seagate-AMD-SATA3-Standard,7223.html)

Burst speed, yes, that has gone up. But very few drives can break 150MB/sec continuous, and they can only do it for the 1st part of the drive, as soon as you start going 'deeper' into the drive the speeds drop, as always with mechanical HDDs. Which is what I meant by 'HDDs still havent broken through the maximum bandwidth of SATAI' (depending on what benchmarking software you like, etc). Nothing short of an SSD can exceed SATAII bandwidth for continous reading or writing. 

Using burst speeds for measurement are like jacking up a tank, seeing how fast it can spin its tracks, and then deciding that max spin speed = real maximum speed. 

I'd agree in someways, if somebody is going AMD, the new 8XX northbridges + SB850 southbridge are a good option (the other option is a 7XX with ACC to unlock cores, if your trying to get the most possible power for your budget).  

> **Ghost|BTFH said:**
> With that in mind, granted the latest/greatest SATA III HDDs currently aren't going to fully take advantage of Asus's dual bandwidth chipset on the SATA channel currently, but they will utilize more of it than a SATA II HDD will.  So you WILL notice slight improvement over II, and later down the road when SATA III becomes more commonplace, you'll see HDDs that can actually utilize the full bandwidth that Asus has so nicely set up for us.

You migth notice a few % difference, but nothing amazing.  

> **Ghost|BTFH said:**
> This information comes from benchmarking results that show Asus SATA III read/write speeds to be superior to Gigabyte's III and previous SATA II benchmark results (Which even Gigabyte's III beats).  Please refer to Tom's Hardware Guide, Legitreviews.com or other such websites for more information on this.

I did a quick search around, and if you've got any links, go ahead, post em. I would like to see them ;) 

> **Ghost|BTFH said:**
> These opinions come from 10 years professional experience doing computer repair and custom system building, as well as 30 years total experience with computers, just FYI.

Just FYI, I've got a similar amount of computer expereince (I cant remember if I started in 1979 or 1980), and I've been building machines for over well 10 years now. ;)

BTW, that post read like an asus add :lolflag: 

> **strider3700 said:**
> THanks for the information guys. I'm not opposed to AMD, I have been very happy with my 3500+ for the last 6 years. I had heard that AMD has fallen behind lately so I was mostly looking at intel. Perhaps that isn't true.

 I haven't checked benchmarks and I'm not really sure it matters. my 3500+ was almost enough to do what I needed (except for the XMBC at the same time) however lately it's feeling a little slow, the hardware is slowly dying and I could use a write off for the company so a new machine makes sense. Pretty much anything beyond bottom of the barrel is going to be a big improvement over what I have. I'm not sure that it will matter if I'm going sata II or sata III, I'm currently running IDE... and 8 gigs of ddr 3 at 1300 or 1600 is going to destroy my 1 gig of ddr.. 

Energy efficiency is a concern for me. looking at some of these chips running at 125W is kind of shocking. I see AMD has a x4 900e that uses 65W which is nice for a machine that will be running 24/7 for the next 5+ years. 

Good point about waiting a few weeks. I'm torn between building/ordering my own exactly like I'd like and buying a prebuilt from a big box store. Assuming I want a specific cpu like the 900e I'll probably have to build.

Amd fallen behind? Sort of. If you like lloking at top of the line, $1000 chips and deciding where to spend your far more reasonable amoutn of money, they have. Intels do have the fastest CPUs now. Which is like deciding what car to buy based on who won the F1//Indycar/etc. But if you just want a machine, to do your computer work, AMD (as always) is ahead in 'bang for buck' 

X4 900es are hard to find. I've long thought that you could get a X965 BE (black edition) and underclock it down to 900e specs. You might actually find 900e is easier to get from one of he 'corporate' manufacturers than it is to try to find one from a store (I know newegg doesnt have them, no idea on bestbuy, tigerdirect, etc). 

Depending on just how close the 3500+ comes to doing what you want it to, you might be able to get away with a Athlon II X4 600e/605e. 45watts, quad core, not quite as much power as a Phenom II, but far, far more than the 3500+ ;)

---

### Post by Ghost|BTFH on 2010-09-23
> **strider3700 said:**
> THanks for the information guys.   I'm not opposed to AMD,   I have been very happy with my 3500+ for the last 6 years.  I had heard that AMD has fallen behind lately  so I was mostly looking at intel.  Perhaps that isn't true.

Energy efficiency is a concern for me.  looking at some of these chips running at 125W is kind of shocking.  I see AMD has a x4 900e that uses 65W  which is nice for a machine that will be running 24/7 for the next 5+ years. 

AMD still rocks very hard - rumors of its demise are greatly exaggerated.

As for energy efficiency, you need to focus on one major purchase - the PSU.  Your power supply should be 80+ bronze certified.  Silver and Gold are really don't offer THAT much benefit to justify the cost.  However, a bronze cert PSU would do you very well.

Secondly, make sure you get a PSU that's matched for your system - don't just say, "Well, it's all next gen product, so I should be looking at a 750w PSU or bigger..." - that kind of thinking is rubbish.

For example...using [Extreme PSU Calculator]("http://extreme.outervision.com/PSUEngine") and setting it for:

1 physical CPU - AM3 Phenom II x4 3000Mhz
2 sticks of DDR3
2 SATA 7200rpm drives
2 DVDRW drives
1 nVidia GeForce GTX280 video card
and 2x120mm fans for the system

we get a PSU suggested power of 455w, which means we could easily run a nice Antec 500w Earthwatts Green 80+ Bronze certified PSU (Which newegg has for about $65 right now) and it'll run VERY efficiently.

So, just keep that in mind when you're planning your build.  Oh, and may I make a suggestion for a case from personal experience?  The Rosewill Challenger case is absolutely fantastic.

Solid, reliable, sexy, FANTASTIC side mounts for the HDDs RIGHT in front of the LED 120mm fan and the 5.25 bays utilize screwless mounting, which is to die for as a system builder.  Not to mention the PSU mounts on the bottom, has a washable filter at the intake position and the case has a top mounted 120mm fan too.

I built a couple systems for clients recently using that case and well, it's my personal case now too - I liked it that much.

Hope these pieces of information help you on your build - the other poster is right though, wait until around Black Friday (The day after Thanksgiving) and the sales should start snowballing.

Cheers,
Ghost|BTFH

---

### Post by Ghost|BTFH on 2010-09-23
> **cascade9 said:**
> You migth notice a few % difference, but nothing amazing.  

Just FYI, I've got a similar amount of computer expereince (I cant remember if I started in 1979 or 1980), and I've been building machines for over well 10 years now. ;)

BTW, that post read like an asus add :lolflag: 


A few % difference is fine for now, will feel faster than what the previous setup did and considering the price comparison of a SATA HDD vs. an SSD, I still say it's a good idea.

However, whether you consider going with SATA II or SATA III drives, getting the SATA III motherboard NOW means taking advantage of SSD when it drops in price - hopefully in the near future.  You don't build a system for what it can do for you now - you build it for what it can do in the future.

Unless of course, you're into building cheap disposable computers that are amazing for all of about six months.

BTW, I noticed you didn't mention that you've been working with computers professionally for 10 years...so I'm guessing you've never done volume work.  My company (and by "my" I mean, the company I own and run) has a less than 1% hardware failure rate on custom built systems, repairs and upgrades.  This includes home systems as well as workstations and servers for small and mid-level businesses in two states.

So, I'm *pretty sure* I know all about SATA I, II and III speeds, burst speed, continuous speed, the difference between them, the performance differences between them and what's the best bang for your buck.  the bottom line is, they *have* broken the SATA I ratings with burst - granted, that's not the end-all-be-all for testing, and continuous speed is far more important, but if you go by continuous speed only, the speed differences are enough that the average user will notice an improvement - ESPECIALLY on larger, more disk intensive applications.

I mean really, with the way you're talking, we should all just stick with SATA I or switch to SSD, because there's no other options for performance increase available.

Considering I can currently pick up a Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive for about $90 compared to a Western Digital Caviar Black WD1001FALS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive for $88 and compared to a Crucial RealSSD C300 CTFDDAC128MAG-1G1 2.5" 128GB SATA III MLC Internal Solid State Drive for $260...I think I'll stick to my guns and say, "SATA III HDD is the way to go for a new system build at this time."

Your mileage may vary.:popcorn:

Cheers,
Ghost|BTFH

---

### Post by cascade9 on 2010-09-24
> **Ghost|BTFH said:**
> A few % difference is fine for now, will feel faster than what the previous setup did and considering the price comparison of a SATA HDD vs. an SSD, I still say it's a good idea.

I doubt that you would even get a few% different between a SATAIII mechanical HDD on a SATAIII controller vs a SATAII controller. 

> **Ghost|BTFH said:**
> 
However, whether you consider going with SATA II or SATA III drives, getting the SATA III motherboard NOW means taking advantage of SSD when it drops in price - hopefully in the near future.  You don't build a system for what it can do for you now - you build it for what it can do in the future.

Which is pretty much what I said to begin with, as far as SSDs go.  

Even then, the absolute fastest of SSDs is just breakign through SATAII bandwidth, and who knows how long its going to take for SSDs to get faster. Could be days, weeks, months or even years.
 
> **Ghost|BTFH said:**
> Unless of course, you're into building cheap disposable computers that are amazing for all of about six months.

The point of this was? 

> **Ghost|BTFH said:**
> BTW, I noticed you didn't mention that you've been working with computers professionally for 10 years...so I'm guessing you've never done volume work.  My company (and by "my" I mean, the company I own and run) has a less than 1% hardware failure rate on custom built systems, repairs and upgrades.  This includes home systems as well as workstations and servers for small and mid-level businesses in two states.

Wrong guess. I've done more than my share of computer assembly work, professionally, in volume. How much time was 'professional' and how much time was as a hobbist is debatable, but at least some of it (and well over 3 years) was professional. 

> **Ghost|BTFH said:**
> So, I'm *pretty sure* I know all about SATA I, II and III speeds, burst speed, continuous speed, the difference between them, the performance differences between them and what's the best bang for your buck.  the bottom line is, they *have* broken the SATA I ratings with burst - granted, that's not the end-all-be-all for testing, and continuous speed is far more important, but if you go by continuous speed only, the speed differences are enough that the average user will notice an improvement - ESPECIALLY on larger, more disk intensive applications.

Burst? Meh. Who cares if you can copy 30MB to your HDD (and not the actual platters, just to cache) in 0.1 seconds for SATAII and 0.05 seconds in SATAIII? 

I'd really like to see any speed differences, for a SATAIII HDD on SATAII controller vs SATAIII controller. Please. Link? 

> **Ghost|BTFH said:**
> I mean really, with the way you're talking, we should all just stick with SATA I or switch to SSD, because there's no other options for performance increase available.

Spurious argument, and something I never even suggested. 

> **Ghost|BTFH said:**
> 
Considering I can currently pick up a Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive for about $90 compared to a Western Digital Caviar Black WD1001FALS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive for $88 and compared to a Crucial RealSSD C300 CTFDDAC128MAG-1G1 2.5" 128GB SATA III MLC Internal Solid State Drive for $260...I think I'll stick to my guns and say, "SATA III HDD is the way to go for a new system build at this time."

I'll stick to my guns and say 'SATAIII for mechanical HDDs wont give you much, if anything at all....they just dont have enough speed (as yet).' 

I'm not saying 'dont get SATAIII', I'm just saying that right now, if you 'have' to get SATAII for whatever reason, its not going to make a huge amount of difference now...and IMO, unless SSDs get a major speed boost in the next few months to a year, and/or drop in price a huge amount, its not going to matter much in a year or two as well.

---

### Post by strider3700 on 2010-09-24
ok lets move beyond theoretical.   my "local" vendor I normally get everything from went from on order status to in stock on the x4 900e processors  so I added one to my cart.   

currently I have in my cart

AMD Phenom II x4 900E Processor AM3 2.4GHZ 8MB Cache 65W 45NM OEM

Antec Earthwatts Green 380W Power Supply ATX12V V2.0 Active PFC 80PLUS Bronze 80MM Fan 

Western Digital WD20EARS Caviar Green 2TB SATA2 3GBPS 64MB Cache 3.5IN Hard Drive OEM

I can reuse my old antec case just adding some new fans and the PS since it was quite nice when I got it and really why not save the money on another metal box. 

The remaining steps of course  are motherboard, video card and ram.   I figured there may be a mb with a built in nvidia card that will meet my needs but I've yet to track one down.  Any specific suggestions?   I came across lots of ddr2 mb's that limit out at 8 gb and I want the ability to move to 16 gb eventually.  sata 3 would be nice but the hd I've chosen is sata2.  I won't be going solid state anytime soon.  storage capacity is far more important to me then speed.

---

### Post by cascade9 on 2010-09-24
Wow, you got a 900e? Nice. I was looking for one of them for ages for a customer, but I just couldnt find one for a reasonable price (I did find 1, but at over $300 US it was way overpriced)  

The earliest nVidia chipset I'd be looking at now is the GeForce 8200. It should work OK,a nd if youget the right modfel they will go to 16GB. The only one I can think of offhand, that might still be in stock, is the ASrock K10N78.  

I think you would be better of getting a motherboard using the ATI 870 + SB850 chipset (yes, yes, SATAIII...seriously, I have nothing against it) and a low end nVidia card. Like a 8400GS, GT210, maybe a GT220 if your planning on using it for much in the way of HD video use...VDPAU (nVidia hardware video decoding) is a wonderful thing ;)

8XX is worth it for SATAIII, USB3.0 (both of which arent that useful now, but could very well be not to far in the furure) and DDR3. Since DDR3 is now pretty much the same price as DDR2, its a good move. 

BTW, your SATAII HDD should work fine on a SATAIII port. Ohh, and one other thing....the WD 'EARS' model drives are a b*tch. They moved to 4k secotors (not the standard 512b) so there is quite a bit of sodding around to get them setup. If you dont get the partitions 'aligned' then you could get lower speeds, and possibly a host of other problems. 

Once they are setup they run really well for a 5000RPM drive. :)  
I'd consider a slightly larger power supply as well. 380 should do it, but its a bit to close to comfort.

---

### Post by Ghost|BTFH on 2010-09-24
It looks like Cascade and I are in agreement pretty much across the board this time.

I'd recommend going with a separate video card - onboard is trash if you're doing anything with decent graphics.  Not to mention, even the GeForce 9 series is pretty cheap, so why not go for it?

I'd grab an [Asus Evo board]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131646") that allows for 1,600 non-oc, USB 3.0, SATA III and a built-in video card if you *really* have to go that route.

Just putting it out there, EVGA makes a nice [GeForce 9500 for pretty cheap...]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130378")

Beyond the motherboard, RAM is the next big deal.  I'm a personal fan of [Corsair]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145324") and they've got a nice 2x4gb pair available that would allow you to drop two more in later on to go up to 16gb.

As for the WD drive, I agree with Cascade, they're a pain.  Go with the WD Black series - it's one of the best on the market currently and I believe they all come with a 5 year warranty - not something you find too often in hard drives these days.  Not to mention they're a breeze to set up.

As for the PSU, according to [Antec]("http://http://www.antec.outervision.com/PSUEngine"), the 380w is just fine for your setup, and would allow you to expand up to 4 sticks, 2HDDs and 2DVDRWs without needing to step up the juice.  That 900e is a real power saver.

Overall, I think you have a good setup going, keep it up and you'll have a great box.

Cheers,
Ghost|BTFH

---

### Post by strider3700 on 2010-09-24
yeah the 900e is $223 cdn. a little pricey when a 965 is $195 on sale for $175...

I wonder how well the mb and OS will crank down the power when they machine isn't working hard.  At thermal design power over 5 years which is my typical system life the difference is $263 in electricity at my current rates.   Anyways my cart currently contains

AMD Phenom II x4 900E Processor AM3 2.4GHZ 8MB Cache 65W 45NM OEM
Gigabyte GA-870A-UD3 AMD870 ATX AM3 DDR3 1PCI-E 2PCI RAID HD Sound GBLAN SATA3 USB3.0 Motherboard 
Corsair XMS CMX8GX3M2A1333C9 8GB 2X4GB DDR3-1333 CL9-9-9-24 Dual Channel Memory Kit 
ASUS GeForce GT 220 625MHZ 1GB 800MHZ DDR2 PCI-E VGA DVI HDMI HDCP Video Card 
Antec Earthwatts Green 430W Power Supply ATX12V V2.0 Active PFC 80PLUS Bronze 80MM Fan 
Western Digital WD20EARS Caviar Green 2TB SATA2 3GBPS 64MB Cache 3.5IN Hard Drive OEM
LG GH22NS50 Black 22X SATA DVD Writer OEM (ditching the old 4x ide)

the 430 watt PS is actually cheaper then the 380 for some reason.
later today I'll look into changing up the HD to see how that 
affects things pricewise.  I see a couple of 1 tb open box returns listed for $60 instead of the $105 for the 2tb.  I'll also look into the asus mb recommended

just need to add a couple of 120mm fans that the mb can control and a 24 foot hdmi cable to hook up the tv. 

current total is $815 cdn + tax and shipping with 55 US in mail in rebates.     I think I'll either have to cut my wish list down or wait awhile longer for some more sales.   I can't hold off till black friday however,  the project will need me to get started in the next month or so.

---

### Post by cascade9 on 2010-09-27
> **Ghost|BTFH said:**
> It looks like Cascade and I are in agreement pretty much across the board this time.

I'd recommend going with a separate video card - onboard is trash if you're doing anything with decent graphics. Not to mention, even the GeForce 9 series is pretty cheap, so why not go for it?

I'd grab an [Asus Evo board]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131646") that allows for 1,600 non-oc, USB 3.0, SATA III and a built-in video card if you *really* have to go that route.

Just putting it out there, EVGA makes a nice [GeForce 9500 for pretty cheap...]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130378")


I, personally, hate motherboards with onboard video. 870, 790X with SB850 or 890FX are better choices IMO. (though the 890FX is a bit expensive, and has a lot of 'features' that most normal humans wont use, so the 890FX isnt that great for value). 

9XXX nvidia cards are OK, but the 8XXX cards and GT2XX cards have better VDPAU features (only really interesting if you watch a fair bit of video, particularly HD). 

BTW, "ASUS GeForce GT 220". This is an example of why I think asus is slipping. 

>     Memory   Effective Memory Clock800MHz   Memory Size1GB   Memory Interface128-bit   Memory TypeDDR2  [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121347](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121347)

> **Memory Specs:**  Memory Clock (MHz)790 Standard Memory Config1 GB DDR3  [http://www.nvidia.com/object/product_geforce_gt_220_us.html](http://www.nvidia.com/object/product_geforce_gt_220_us.html)

GT220 should have DDR3, not DDR2. Comon, is it that hard to follow the nVidia guidelines? Or do they really make enough profit from subing cheap DDR2 for not-quite-as-cheap DDR3? 

I'd go for something that has 'proper' DDR3. The EVGA model is only $5 more and comes with DDR3- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130522](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130522)


> **strider3700 said:**
> 
the 430 watt PS is actually cheaper then the 380 for some reason.

I'd be careful with that.....older PSUs tended to have much more 5v current,a nd less 12v. Newer computers want more 12v, and less 5v. So if its 'old stock' 430watt PSUs it migth not work well with your setup. 

I've seen a PhemonII X2 550/4GB DDR3/8400GS setup tryign to run an older thermaltake 430watt PSU. It was pretty unstable , and it was purely the fault of the power supply. Changed the PSU, flawless. 


> **strider3700 said:**
> current total is $815 cdn + tax and shipping with 55 US in mail in rebates.     I think I'll either have to cut my wish list down or wait awhile longer for some more sales.   I can't hold off till black friday however,  the project will need me to get started in the next month or so.

Ditch the GT220 for a GT210, use the old 4x IDE till you can get a newer drive, maybe think about getting 2 x 2 GB or 1 x 4GB RAM sticks, or a 'stopgap' CPU (even a very cheap Athlon II X2 will have a huge amount more power than a single core 3500+)

---

### Post by strider3700 on 2010-10-06
ok guys here is a question.  The asus ASUS M4A87TD/USB3 takes 16 gb of ram via 4 slots.  looking at it's memory qvl  for the corsair CMX8GX3M4A1600C9(XMP) which is 2x4gb under the column labelled dim socket support (optional)  It says 1 dim, 2 dim but not 4 dim.  I'm not sure what that means.

Does it mean that I can't buy 2 of the CMX8GX3M4A1600C9(XMP) and put all 4 in for 16 gb?  or does it mean it won't be as fast? or what?

if I get the CMX8GX3M4A1600C9(XMP) can I eventually get to 16 Gb or will it need to be pulled and  I buy 16 gb of something that works?

---

### Post by cascade9 on 2010-10-06
> **strider3700 said:**
> ok guys here is a question.  The asus ASUS M4A87TD/USB3 takes 16 gb of ram via 4 slots.  looking at it's memory qvl  for the corsair CMX8GX3M4A1600C9(XMP) which is 2x4gb under the column labelled dim socket support (optional)  It says 1 dim, 2 dim but not 4 dim.  I'm not sure what that means.

Does it mean that I can't buy 2 of the CMX8GX3M4A1600C9(XMP) and put all 4 in for 16 gb?  or does it mean it won't be as fast? or what?

if I get the CMX8GX3M4A1600C9(XMP) can I eventually get to 16 Gb or will it need to be pulled and  I buy 16 gb of something that works?

Sorry, CMX8GX3M4A1600C9 is 4x2GB, not 2x4GB. So with 4 sticks, you would still only have 8GB. 

Apart from the '4 x 2GB' I would assume that you can have 1 or 2 sticks of that RAM, but they havent tested 4 (or they tested it but it failed). 

I'm a bit shocked by that memory support list....most of the sticks are 1.65+ volts, and DDR3 has moved/is moving to 1.5v DDR3 (following intels guidelines on the voltage on RAM for core iX).

---

### Post by strider3700 on 2010-10-06
so although they list a 4x2 8 gig ram on their qualified list  they only support half of it 2x2?   I also note that they don't list ANY 2x4 which would there for make 16 gigs impossible on this 16 gig board.  Why do I get the feeling the chart isn't the be all end all.

---

### Post by cascade9 on 2010-10-06
> **strider3700 said:**
> so although they list a 4x2 8 gig ram on their qualified list  they only support half of it 2x2?   I also note that they don't list ANY 2x4 which would there for make 16 gigs impossible on this 16 gig board.  Why do I get the feeling the chart isn't the be all end all.

I agree, its confusing. 

The other weird thing is that there are 12GB (4x3GB) setups listed, and thats normally a LGA1366 (i7) only setup. 

I have the feeling that they are just tesing a standard set of RAM sticks they have, and arent bothering to update to new RAM sticks as they are released.  

BTW, there are 8GB ECC/registered RAM sticks (for servers) around now. AFAIK, 'desktop' RAM hasnt come out in 8GB stricks yet, but sooner or later, they will. 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007952+600006074&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=541&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007952+600006074&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=541&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by avacado on 2010-10-14
google linux netbook compatibility
there is a community contributed page with good advice
ubuntu have certified hardware page but that relies on sponsorship and so the hardware is ancient and I found the information unreliable.

I bought an ACER aspire one as advised by canonical support and dissapointed per
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

In other words, despite being certified hardware, there is no driver for the SD card reader.

take a usb loaded with UNR to the shop and try it out.

---

### Post by cascade9 on 2010-10-14
@avacado- did you even look at this thread? strider3700 was after a desktop system. No netbook even gets close to a desktop quad-core CPUs power....

---

### Post by strider3700 on 2010-10-21
ok guys,  the parts finally all got here and I've assembled it and I get the strangest issue.  I went with the m4a87TD/usb3

when I first turn on the system  it will sit there for 4 or 5 minutes doing nothing.  the fans all spin up and I hear the cd drive and harddrive kick as they get power  but the video card never "turns on" as the monitor sits there the same as the machine is turned off.    After the 4 or 5 minutes the bios screen will flash on screen then I'll get the error that I have no boot drives which makes sense since I don't at the moment.   

I went into the bios and went to update the bios but it was already at the newest version.  Loading the program to do it though was also super slow,  something like 10 minutes for it to verify that it was the same version.

So my thought is something is wrong with the motherboard.  Before I start the RMA process I figured I'd ask if anyone here has seen similar  or has suggestions as to what to check.   I tried every variation of ram that I could and that makes no difference.  When the bios did arrive it showed all 8 gigs as being available so I don't think that is the issue.

Thanks

---

### Post by avacado on 2010-10-21
I am building one too, but using the opportunity to push my issue
The title of the thread will draw potential netbook buyers

If considering Acer Netbook see first
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

---

