---
title: "Help for a first timer."
date: 2010-04-21
forum: Mythbuntu
---

### Post by Beastofomous on 2010-04-21
So I recently decided to buy my first home, and being a frugal geek I've decided on using a Mythbuntu box with an internet connection and a OTA tuner for all of my media needs. Unfortunately I'm no linux master by any means, and so I come to you, the wonderful community of experts hoping that you can help me set up a decent budget system that fits my needs. So let's get to it, here's what I'm looking for.

[LIST]
[*]Living in the US so I believe I'll need an ATSC tuner for OTA
[*]Backend needs to have plenty of space for my current media collection as well as future recordings
[*]I have 2 televisions that will need to get to the myth setup, not sure what the cheapest route is for a frontend so hoping for some advice on that
[*]Would like to be able to watch 2 shows while recording 2 shows at the same time (just in case, that would probably be my max usage scenario)
[/LIST]
And I believe that really sums it up. I would like to record and play HD on both televisions, but if that's not possible on one or all of them it is definitely not a deal breaker. And of course the cheapest I can get it while satisfying my needs is preferred as I still have some college debt and I'm getting into a mortgage so I'm going to have to keep the belt a bit tight (however even if the initial hardware costs are expensive I realize I'll be saving $60-$100 every month with this setup)

So I'm kinda mythtv, PVR, DVR, TV in general noobish so if i've left out any vital information just let me know.

Thanks in advance!

---

### Post by My Name on 2010-04-21
well I would suggest getting two acer revo mechines (about $200 i think). they are small (abouit the size of 2 full size hard drives) and they can be attached to the back of most LCD TVs or computer monitors. they have HDMI output also. I have one set up as a FE/BE with all of my DVB-T tuners attached. I recon you should get a couple of nova-tD usb sticks as they are dual tuners and will give you the 4 you need. That is if you want DVB-t, I'm sure there are many USB TV alternatives to suit.
You may also need an external HD. I have one which has an E-SATA output. The revo has an E-SATA input.
I currently use a broken laptop as a remote FE in the bedroom. The keyboard and HD are broken so I removed them. I also removed the lid, as i have it attached to a 22" widescreen monitor. Also it has a wireless card so If I need to, I can remove it from the wired network and it will still be good to go.

---

### Post by Beastofomous on 2010-04-21
Wow... that actually looks exactly like what I was looking for.

So if I used one of these [http://www.hauppauge.com/site/products/data_hvr850.html](http://www.hauppauge.com/site/products/data_hvr850.html)
per unit it would allow me the functionality that I was looking for correct?

Thank you so much for the wise and timely response.

---

### Post by LowSky on 2010-04-21
First off lets get started on what you will need

The Backend where all your recording, and storage will be can also be one of the front ends, to save some money.

You will need at least 2 dual-tuner cards. My favorite is the [Hauppauge HVR-2250]("http://www.hauppauge.com/site/products/data_hvr2250.html"). the only issue is thety are the newer PCI express x1, which most PC dont have many slots for. Newer Motherboards should have 1, and if it also has a PCIex16 slot you can use that for a second if you have onboard video. The card is about $100 on newegg.com

This card does take some work to get running, but luckily I wrote a very good [tutorial]("http://ubuntuforums.org/showthread.php?p=7344302#post7344302"). supposedly 10.04 will support the card automatically, but I cannot confirm that yet.

As for a secondary front end, buy something that can run HD video. My Name's suggestion is ok, but is kinda lacking HD support, even with its HDMI port. It will run it but not always so great. Best option is a old machine with a $50 new video card.

If you need any help PM me

---

### Post by LowSky on 2010-04-21
> **Beastofomous said:**
> Wow... that actually looks exactly like what I was looking for.

So if I used one of these [http://www.hauppauge.com/site/products/data_hvr850.html](http://www.hauppauge.com/site/products/data_hvr850.html)
per unit it would allow me the functionality that I was looking for correct?

Thank you so much for the wise and timely response.

more like 4 to watch 2 and record 2 more.

---

### Post by Beastofomous on 2010-04-21
> **LowSky said:**
> more like 4 to watch 2 and record 2 more.
ok so the one I linked is a single not a dual tuner? My bad sorry I am new to tuner cards completely.

---

### Post by LowSky on 2010-04-21
> **Beastofomous said:**
> ok so the one I linked is a single not a dual tuner? My bad sorry I am new to tuner cards completely.
Yeah its single tuner.

try this one,like I said it probably the best out there, but it needs some TLC to get working, which I linked in my other post
[http://www.hauppauge.com/site/products/data_hvr2250.html](http://www.hauppauge.com/site/products/data_hvr2250.html)

Don't worry about being a new to this stuff, I've only been in this game under two years.

Oh A great thing to point out is if you own a PS3 (maybe a Xbox360) they can stream the recordings as well. So that might save you a frontend.

SiliconDust HDHomeRun is a great option if you want two tuners but are running out of space with USB or PCI ports. It works off the network instead So it doesn't need to be near the computer. And it has MythTV support. Which makes it a great choice..
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815327005](http://www.newegg.com/Product/Product.aspx?Item=N82E16815327005) 

My setup includes the following, which to some might seem a bit over the top, but my PC is also used as a regular computer too.

AMD Phenom 9950 x4
4GB of RAM
750GB & 500GB hard drives for storage
HVR-2250 dual tuner for record two shows at one time.
ATI 4550 video card for HDMI out
DVD-RW for ripping/playing DVDs
USB Windows media center remote and receiver

I will probably add a SiliconDust HDHomeRun to gain a few more channel to record a tone time, but right now I'm more than fine with my setup.

---

### Post by Beastofomous on 2010-04-21
Alright thanks for the insight LowSky, I'm going to attempt to put together a build on Newegg here in a minute, would you mind reviewing it for me when I'm finished to point out anything that could prove problematic?

---

### Post by My Name on 2010-04-21
> **LowSky said:**
> First off lets get started on what you will need

The Backend where all your recording, and storage will be can also be one of the front ends, to save some money.

You will need at least 2 dual-tuner cards. My favorite is the [Hauppauge HVR-2250]("http://www.hauppauge.com/site/products/data_hvr2250.html"). the only issue is thety are the newer PCI express x1, which most PC dont have many slots for. Newer Motherboards should have 1, and if it also has a PCIex16 slot you can use that for a second if you have onboard video. The card is about $100 on newegg.com

This card does take some work to get running, but luckily I wrote a very good [tutorial]("http://ubuntuforums.org/showthread.php?p=7344302#post7344302"). supposedly 10.04 will support the card automatically, but I cannot confirm that yet.

As for a secondary front end, buy something that can run HD video. My Name's suggestion is ok, but is kinda lacking HD support, even with its HDMI port. It will run it but not always so great. Best option is a old machine with a $50 new video card.

If you need any help PM me

I for one will disagree with that. Many other people are using this box and have full HD 1080p. and I have the single processor version.
VDPAU works flawlessly with mythtv... well with a couple of very simple tweaks.

---

### Post by Beastofomous on 2010-04-21
Alright My Name, from a price perspective I like your idea better, but I don't know jack about VDPAU so you lost me there, fill me in. Does your setup have flawless HD?

---

### Post by LowSky on 2010-04-21
> **My Name said:**
> I for one will disagree with that. Many other people are using this box and have full HD 1080p. and I have the single processor version.
VDPAU works flawlessly with mythtv... well with a couple of very simple tweaks.

Flash support is still an issue for some people who like to run things like Hulu Desktop or Boxee, especially with the processor as flash isn't supported by Nvidia. Also I'm trying to save him some money  using older equipment he might have lying around and buying only required parts.

VDPAU  is a process for Nvidia hardware to take the strain of video off the processor and put it solely on the video chip. its works well, but in low end solutions like Atom powered hardware it doesn't work well on web based content.

---

### Post by Beastofomous on 2010-04-21
In the mean time this is what my newegg build would come out to for the BE/FE

[LIST]
[*] Case - [http://www.newegg.com/Product/Product.aspx?Item=N82E16811119195](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119195) - 39.99
[*] Hard Drive - [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136490](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136490) - 69.99
[*] MoBo - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131626](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131626) 54.99
[*] Tuners - [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116037](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116037) - x2 229.98
[*] Memory - [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134637](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134637) - 56.99
[*] CPU - [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103681](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103681) - 64.99
[/LIST]
TOTAL = 516.93 before shipping

Still would have to figure something out for another FE, which makes this the more expensive route I think

---

### Post by LowSky on 2010-04-21
Beastofomous Lets take a step back:

The best thing to ask is how much money do you want to spend.


First you will need a backend with a ton of storage, think of how big you current media takes up. Also HD recording can be rather large, about 3-4GB an hour at 1080i. A 1TB hard drive is under $100 now. Dont forget the backend can be used as a Frontend as well, which can save money too.

the front end can be really light, frontends dont store any recorded data, so the hard drive can be a 4-8GB Flash drive if you wanted it to be. I'm not joking. My Name's choice is decent, but if you have old laptop or PC lying around, I would use those in a heartbeat. Especially if a cheap upgrade will make them work with a HDTV.

If you want the frontends to be wireless, use the newest Wireless N standard, the older G speed is not so great at streaming HD from one PC if there is other network traffic. If you are using wired conneciton you will be fine.

---

### Post by LowSky on 2010-04-21
I would get a different hard drive, those green drive are kinda slow, I just built a PC for a family member and used the same drive and was rather disappointed in how often it spins down which can slow the PC down and if used in a back end might be annoying.
I like this one for 10 buck more
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145304](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145304)


save a few $$$ on the CPU too
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103688](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103688)
you wont notice the difference, trust me

---

### Post by Beastofomous on 2010-04-21
ok excellent thanks for the tips LowSky

Honestly my budget is flexible, I would like to keep it as cheap as possible but functionality is important to me, I don't want skipping or slowing framerates at all, so spending a hundred dollars more on a solid BE/FE and then skimping on the other FE is certainly an option for me.

Also I do have a 360, and as long as it is DECENT as a mythbuntu FE It would suffice for me I think. I just don't want anything too clunky.

---

### Post by My Name on 2010-04-21
> **Beastofomous said:**
> Alright My Name, from a price perspective I like your idea better, but I don't know jack about VDPAU so you lost me there, fill me in. Does your setup have flawless HD?

yeah, flawless. VDPAU enables the video chip to do all the hard work when decoding mpeg video, rather than the main processor. This means you can have a small and therefore cheap processor. it also means the heat generated is lower and therefore no noisy fans. The revo does have a processor fan, but it only really kicks in when booting up... maybe when at other times, but it is very quiet so I never notice it.
Just google acer revo mythtv, or mythbuntu and you should see plenty of threads.
The other bonus with using a box like this is that other people will be using exactly the same hardware and if any problems appear, there is a good chance someone else will either have the same problem or you will be able to track down the fault more easily.

---

### Post by My Name on 2010-04-21
yeah i agree, if you have old hardware lying around it would be good to re-use it, especially if you have a knackered laptop like me. If you are starting from scratch though, the revo is hard to beat.
Also a combined FE/BE does get noisy if you are using a conventional desktop PC.

---

### Post by LowSky on 2010-04-21
> **My Name said:**
> 
Also a combined FE/BE does get noisy if you are using a conventional desktop PC.

I will amdit it can but with some procautions, like using better fans or controllers, things can be pretty quiet. for example My video card is fanless, my processor uses a Arctic Cooler tower heatsink with a 92mm fan, and the other 4 fans are controlled by a fan controller, set to low. The system never gets very hot. Even with it being in a HTPC case.


and the Xbox360 wont use Myth, it will see the Backend as a network drive and you can watch the stuff easily from that

---

### Post by tgm4883 on 2010-04-21
> **LowSky said:**
> I will amdit it can but with some procautions, like using better fans or controllers, things can be pretty quiet. for example My video card is fanless, my processor uses a Arctic Cooler tower heatsink with a 92mm fan, and the other 4 fans are controlled by a fan controller, set to low. The system never gets very hot. Even with it being in a HTPC case.


**and the Xbox360 wont use Myth, it will see the Backend as a network drive and you can watch the stuff easily from that**

This has not been my experience, although I haven't tested it since I was on 0.21

AFAIK, the 360 doesn't support playing mpeg2 files, which is what your HD files will be in unless you get the HDPVR

---

### Post by Beastofomous on 2010-04-21
hmm ok so now I'm going to have a tough time deciding on whether I should use the build that I posted earlier and just use my 360 as a second FE for now, or use 2 acer's, one as a BE/FE with 4 USB tuners and one as a FE.

---

### Post by Beastofomous on 2010-04-21
unless there are dual usb tuners for ATSC, I couldn't seem to find any though

---

### Post by My Name on 2010-04-21
It can be both it's saint and it's devil. The choices!!!

---

### Post by laffinet on 2010-04-21
> **LowSky said:**
> I would get a different hard drive, those green drive are kinda slow

I have to disagree with this. My combined frontend/backend is running on WD Green Caviars, never had performance issues. Disk I/O is usually not the bottleneck of a myth machine.

OT: Think about running a combination. One larger machine as your primary frontend/backend, which could be made up of old components, so it's cheap. Should give you plenty of space for expansion, storage etc.
One small machine (like the Revo), as a second frontend. Neat, low power, quiet.

---

### Post by My Name on 2010-04-22
Just to add, the revo doesn't handle flash very well. I thought I would test it with bbc iplayer and it player maybe 2 frames a second. I am currently using 9.10 so maybe it is improved in 10.4

---

### Post by Lepy on 2010-04-22
Two things to try for better flash performancce 1.) turn off compositing 2.) lower your resolution before playing flash.

---

### Post by My Name on 2010-04-22
> **Lepy said:**
> Two things to try for better flash performancce 1.) turn off compositing 2.) lower your resolution before playing flash.

ah... i'll give the compositing a try but the resolution drop may not be practical.

Thanks matey

---

### Post by Lepy on 2010-04-22
> **My Name said:**
> ah... i'll give the compositing a try but the resolution drop may not be practical.

Thanks matey

Yeah, dropping the resolution isn't really viable for a desktop system, mainly for a stand-alone programs like boxee or hulu, but this is the mythbuntu section after all!

---

### Post by Beastofomous on 2010-04-22
the only problem with running a backend on spare parts is I don't have too many spare parts to go around, I would need a new MoBo, processor, memory, hard drive, and tuner cards... although now that I actually type that out it seems like that isn't too big of a deal at all.

---

