---
title: "Need Guidance for First HTPC Build"
date: 2009-02-03
forum: Mythbuntu
---

### Post by Great Blue Heron on 2009-02-03
I've decided that I want to build an HTPC. This will be my first HTPC build so, I'm trying to feel the waters in deciding what hardware and software I will need.

On my main PC I am dual booting Ubuntu 8.10 and Windows XP. I've enjoyed playing around with Ubuntu so, I've decided that I want to use Linux on the HTPC. I will probably try Mythbuntu unless, someone has a better suggestion.

My goals for the HTPC:
1)Play my DVD collection. I don't have any Blu-Rays at the moment.
2)Play videos stored on the hard drive. Some are 1080p h.264 and mkv.
3)Function as a DVR. 
4)Optional – FM Tuner

The only piece of hardware I have on hand for this build is an ATI 3850 that is capable of HDMI output.

Here are the hardware specs I am considering:
1)CPU: [AMD X2 4850e]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103255&Tpk=4850e")
2)Motherboard: [Biostar TA790GX A2+]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138128")
3)RAM: 4GB DDR2-800
4)HD: [Seagate 1.5TB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148337")
5)Case: [Apevia X-MASTER-BK/500]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811144231") (It has a 500W PSU)
6)TV Tuner: Need Suggestion (The Hauppauge WinTV-HVR-2250 looks good)

Please provide feedback on the software and hardware specs. Remember that I am a newbie so, feel free to give a detailed explanation in you replies.

---

### Post by movieman on 2009-02-04
Be wary of the Seagate 1.5TB drive; they've had some serious reliability problems recently.

I think the CPU should be fine, but haven't tried 1080 playback on that model.

---

### Post by nicoloks on 2009-02-04
I've just built a new HTPC for a mate using a AMD 5600+ (2.9Ghz dual core) based on the Nvidia 8200 Asus M3N78-VM motherboard, and it just barely manages to play 1080p content with one of the cores being pegged at 90%+ usage nearly all the time. Xine is actually the only player that will play 1080p content without servere audio sync or video stutter issues, and even then it just barely does the job.

So looking at your specs I'd say you'll need to upgrade your CPU and RAM. For a CPU I would be looking at something like the [89w X2 6000+ (3.1Ghz)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103272"), and for RAM I would look DDR2 1066 (even if you have to drop back to 2GB). Reason for this is when using a motherboard with IGP your main memory is used as video memory, so the slower this is the less performance.

As for the Nvidia Vs AMD chipset depate, this thread might be of some help;

[http://www.redflagdeals.com/forums/showthread.php?t=681944](http://www.redflagdeals.com/forums/showthread.php?t=681944)

---

### Post by Great Blue Heron on 2009-02-04
Thanks for the replies.

> **"movieman"]Be wary of the Seagate 1.5TB drive said:**
> 

Thanks for the heads up. I was looking at the reviews on Newegg.com and it looks like Seagate may have fixed the firmware issue. However, I will search alternative manufacturers for high capacity drives.

[QUOTE="nicoloks"]So looking at your specs I'd say you'll need to upgrade your CPU and RAM. For a CPU I would be looking at something like the 89w X2 6000+ (3.1Ghz), and for RAM I would look DDR2 1066 (even if you have to drop back to 2GB). Reason for this is when using a motherboard with IGP your main memory is used as video memory, so the slower this is the less performance.

I have an ATI 3850 on hand that I had planned to use so, I didn't care about the IGP. I'll have to do some research to find out how well this video card will work in Linux. 

It looks like people using Windows as their OS are doing fine with the 4850e CPU. Do you think this may be due to better video drivers in Windows? Do you think I should splurge and get an AMD X2 7750?

Thanks...:popcorn:

---

### Post by movieman on 2009-02-04
> **Great Blue Heron said:**
> It looks like people using Windows as their OS are doing fine with the 4850e CPU. Do you think this may be due to better video drivers in Windows?

I think the biggest problem is that all the MythTV codecs appear to be single-threaded; so if a single core in the CPU can't handle the decoding, you're stuffed even though you have one or more idle cores which could be helping out.

But yes, the Windows systems probably also have GPU-assist for the decoding in the video drivers, which offloads more work from the CPU.

---

### Post by newlinux on 2009-02-04
> **movieman said:**
> 
But yes, the Windows systems probably also have GPU-assist for the decoding in the video drivers, which offloads more work from the CPU.

Another reason to go with a nvidia GPU that supports VDPAU. I'd stay away from ATI for now personally if you are choosing from scratch. With VDPAU the processor needs for 1080p h.264  drop significantly.


[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Take a look at user results from using VDPAU at the end of following:

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by nicoloks on 2009-02-04
> **Great Blue Heron said:**
> 
It looks like people using Windows as their OS are doing fine with the 4850e CPU. Do you think this may be due to better video drivers in Windows? Do you think I should splurge and get an AMD X2 7750?

Thanks...:popcorn:

Great Blue Heron, it looks as if I may have given you a bit of a bum steer. I was under the false impression that I had VDPAU support simply by installing the Nvidia 180.22 drivers. You also have to patch Mplayer to take advantage of VDPAU which I did following [this simple guide]("http://zacgarrett.com/software/installing-mplayer-vdpau/index.html").

After that I ran my test video which is a high quality VC1 rip of the Matrix and saw my CPU usage drop from approx 90%+ to only around 10%. VDPAU _really does_ make that much difference! 

So to revise my advise; Stick with the 4850e as it is only 45w (you can passively cool this with a Scythe MINI NINJA heatsink), but as others have suggested get a motherboard with either an Nvidia 8200 or 8300 IGP and you'll have no issues at all playing full 1080p content. Half thinking of upgrading my Nvidia 6150 board now so I can take advantage of VDPAU!

---

### Post by Great Blue Heron on 2009-02-04
Thanks for the responses.

Well it sounds like the 4850e will work okay as long as I get a nvidia video card. I like that the 4850e only draws 45 watts. From what I've read onboard nvidia graphics 8200 and 8300 are VDPAU capable. Has anybody tried on of these? Does anyone have a particular motherboard for recommendation?

What remote would you recommend? Would I be better off going with a wireless keyboard and mouse?

:-\"

---

### Post by newlinux on 2009-02-04
There are a few over on AVSforums who have tried 8200 IGP boards. Below are a couple 8200 and an 8300. You could always just buy a fairly inexpensive VPDAU GPU for whatever board you get.

ASUS M3N78-EM
ASUS M3N78-VM
GIGABYTE GA-M78SM-S2H

I can't personally vouch for these, but I tend to prefer ASUS and Gigabyte.

A remote has a higher WAF... it's really a personal choice. you can use whatever remote you want. The  receiver is the important part. I use MCe receivers with my harmony universal remotes. As far as remote packages (remote and receiver) go

snapstream and MCE remotes are popular and are easy to configure

---

### Post by 4dognight on 2009-02-05
I have 2 systems running the 4850e. It humms along playing back HD content with CPU to spare. I also have the older 2300be and it works fine too.

---

### Post by neilevan814 on 2009-02-06
For your tv tuner card I would suggest the pchdtv 5500 [http://pchdtv.com/]("http://pchdtv.com/").  I am starting my own HTPC build and am planning on the same processor.  Here is the rest of my build specs
-COOLER MASTER ELITE 335 RC-335-KKN1-GP Black SECC Steel ATX Mid Tower Computer Case
-ASUS M2N68-VM AM2+/AM2 NVIDIA GeForce 7050PV HDMI Micro ATX AMD Motherboard
-Rosewill RG430-2 430W 80Plus Certified,ATX12V v2.3/EPS12V v2.91, Active-PFC Power Supply, UL,FCC,CE,TUV,ROHS
-G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit 
-Western Digital Caviar SE WD1600AAJS 160GB 7200 RPM SATA 3.0Gb/s Hard Drive
-ASUS VH242H Black 23.6" 5ms HDMI Full 1080P Widescreen LCD Monitor
-EDIMAX EW-7128G PCI Wireless Card
-LITE-ON 22X DVD±R DVD Burner with Smart Erase Black IDE Model iHAP322-08
-Logitech LX310 Black USB Cordless Standard Desktop Laser

---

### Post by Great Blue Heron on 2009-02-06
Here are the updated hardware specs:
1)CPU: AMD X2 4850e
2)Motherboard: [ASUS M3N78 PRO AM2+/AM2 NVIDIA GeForce 8300 HDMI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320") 
3)RAM: 4GB DDR2-800
4)HD: 1TB (Samsung/Western Digital/Hitachi) Whichever is best buy ATM
5)Case: Apevia X-MASTER-BK/500 (It has a 500W PSU)
6)TV Tuner: Still Researching

[QUOTE="neilevan814"]For your tv tuner card I would suggest the pchdtv 5500[/QUOTE]

I will research this card.

I think it would be best to get one that can do NTSC/ATSC/QAM. It looks like the Haup HVR-1800 and Divco FusionHD7 may work okay with some tinkering.

What tv tuners are you  currently using? Can you guys post the ones that work well without a lot of work?

Thanks...\\:D/

---

### Post by newlinux on 2009-02-07
check my signature for my hardware. All are pretty easy to get working.

---

### Post by itlarson on 2009-02-07
Due to a motherboard failure,I just re-built my htpc around the AMD 4850e, ASUS M3N78-EM mobo (Geforce 8300), and dual pchdtv tuners.  Everything seems to work well,  although There is some weirdness with the spdif- It works fine for dtv recordings, and dvd playback with kaffeine,  but not for mythdvd, standalone mplayer, or amarok.  This has to be a configuration issue though.  Look for my post on this.
   I have to thank newlinux for his post on VDPAU.  I was not even aware of it's existence, and I have been meaning to try 1080p for a sharper picture. My TV is only 1366x768, but The manual says takes 1080p input.

---

### Post by movieman on 2009-02-07
> **itlarson said:**
> My TV is only 1366x768, but The manual says takes 1080p input.

The only real benefit of feeding a 1080p picture into a 720p TV is that it saves you having to scale down the picture to 720p on the host PC; which may or may not save you much depending on how it's done (e.g. CPU scaling is slow, but a decent GPU will hardly notice the extra workload if the scaling is done there).

---

### Post by frafu on 2009-04-27
Hi,

For hdtv by satellite, they are using 1080i and not 1080p (at least in europe). And as far as I know, the budget nvidia cards that manage vdpau, don't have enough power to do spatial or spatial temporal deinterlacing (these are said to be of better quality) without framedrops. For example my asus 8400 manages bob deinterlacing (lesser quality) without framedrops only as long as it does not have to do anything else. (For example, there are framedrops as soon as I move a window.)

I don't know how well the nvidia IGPs handle the deinterlacing of 1080i...

In any case, I think that the deinterlacing of 1080i is also a point to consider when building a htpc, especially if a dvb-s2 card is used.

Cheers

---

