---
title: "Perfect Set-Up for Mythbuntu?"
date: 2008-08-30
forum: Mythbuntu
---

### Post by acrousey on 2008-08-30
I am kind of curious to see what some of you think the perfect Mythbuntu set-up would be (hardware-wise). Like, what kind of CPU, RAM, HDD, video card, etc. I know my computer would barely even be able to handle it. Not necessarily what you guys have. Maybe your "Dream Set-Up". Again, I'm just curious.
-Thanks!

---

### Post by DemonBob on 2008-08-30
My dream setup. 

First Box: NAS - Network Attached Storage (FreeNAS)
14~15 HDD Case, loaded all with 1TB drivers, RAID 5
512 Ram
1000/100/10 Ethernet NIC
Headless no monitor. 

Second Box: Backend (Mythbuntu)
Headless no monitor
NAS is mounted on /var/lib/mythtv
1000/100/10 Ethernet NIC
2~4 GB of Ram
Mutipule Tuners. 
Hauppage 150
Hauppage 1800
HDHomerun


Third/Forth/Fifth/ETC Box: Frontends (Mythbuntu)
[http://system76.com/product_info.php?cPath=27&products_id=81](http://system76.com/product_info.php?cPath=27&products_id=81)
System76: Sable Performaces
Setup: 
Core 2 Duo 2.4Ghz
2GB Ram
1000/100/10 GB Ethernet
IR Blasters
Best PCIexpress low profile Nvidia/ATI card i can find that supports S-Video/HDMI Out.

What i have: 
Backend/Frontend Combo (Mythbuntu)
Custom Build PC
Gigabyte Motherboard
PVR-150
HVR-1800
2 GB Ram
80GB HDD
500GB HDD (mounted to /var/lib/mythtv)
10/100 NIC
Gyratation MCE Remote
Nvidia Geforce 7300LE

---

### Post by acrousey on 2008-08-31
I'm about to sound like a huge noob, but what are the differences between frontend and backend in Mythbuntu?

EDIT: BTW, I think the computer in my sig could maybe make a good NAS machine someday if I can afford anything else.

---

### Post by DemonBob on 2008-08-31
Mythtv is split into two parts. This is the basic's but it does more then that

Backend: This Records the shows, writes information to the database, manages the tv tuner cards, also downloads your guide data. 

Frontend: GUI, For viewing the media/watching tv/music and such.

The backend runs sliently in the background. The accual part you see when you watch movies and such is the frontend. 

They can be on seprate machines. You can have multipule frontends connect to one central backend. You can also have Slave backends, which help slit the load to the main backend.

---

### Post by ReddogOne on 2008-09-02
> **DemonBob said:**
> My dream setup. 

First Box: NAS - Network Attached Storage (FreeNAS)
14~15 HDD Case, loaded all with 1TB drivers, RAID 5

Second Box: Backend (Mythbuntu)
Headless no monitor
NAS is mounted on /var/lib/mythtv

I was wondering about whether to use a separate NAS for mass storage (I have a 75% empty Buffalo Terastation) or whether it should all be in one box with the tv cards.

Not sure how mythtv works but was thinking that if the content needed to pass from the PC recording to the NAS and also have stuff being watch going from the NAS to the backend then to the front end on another PC that the limit of the network could be reached twice as quick.

---

### Post by openivo on 2009-10-14
I am buying a laptop to use as a combination FE/BE and mobile entertainment.

I prefer to buy a preloaded Ubuntu model.

My choices is between System76 Pangolin or Dell Studio XPS 13:

Pangolin Performance  Price: $759.00
Display: 15.6" WXGA (1366 x 768) or
15.6" WSXGA+ (1600 x 900)
Graphics: 512 MB DDR2 nVidia GeForce G105M
Audio Output: Intel High Definition Audio
Networking: Gigabit LAN (10/100/1000), WiFi
Wireless: 802.11 agn, Bluetooth
Expansion: Express Card 34/54 slot
Ports: VGA, HDMI, 3 x USB 2.0, eSata Port, Headphone Jack, Microphone Jack, S/PDIF Output Jack, SD Reader
Camera: Built-In 2.0 MP Webcam
Security: Fingerprint Reader (beta),
Kensington® Lock
Power Management: Suspend & Hibernate
Battery: includes one 6 Cell Lithium Ion
AC Adapter: includes one AC adapter
Dimensions: 14.75" x 10.125" x 1.5" (WxDxH)
Weight: 5.8 lbs. 


PROCESSOR Intel® Core™ 2 Duo P7350(3MB cache/2.0GHz)	
OPERATING SYSTEM  Ubuntu Desktop Edition version 9.04	
WARRANTY AND SERVICE	1Yr Ltd Hardware Warranty, 
HD DISPLAY Edge-to-Edge 13.3" HD WXGA LCD with 2.0 Megapixel Camera	
MEMORY	3GB DDR3 SDRAM at 1067MHz (2 Dimms)	
HARD DRIVE	250GB 7200 RPM SATA Hard Drive	
INTERNAL OPTICAL DRIVE	Slot Load DVD+/-RW (DVD/CD read/write
VIDEO CARD	NVIDIA® GeForce® 9400M G	edit
WIRELESS CARDS	Dell Wireless 1397 802.11a/g Half Mini-Card	edit

---

### Post by blackoper on 2009-10-14
I'm pretty happy with my setup.
[http://mythtv.org/wiki/User:Blackoper]("http://mythtv.org/wiki/User:Blackoper") but the mainboard and processor use a lot of power. With hard drives I'm pulling close to 180 watts which for me is about $8 a month.

The pefect frontends to me are the zotac ion 230 boards in the M350 case that attaches to the vesa mount of an lcd panel so it's invisible. 20 watt power draw and can play most things (it's getting flash hardware acceleration soon as well in the flash 10.1 release). If you use mythbuntu's diskless system, you then have a completely silent frontend. i've only got one of the ion boards/m350 cases currently but will transition all my frontends to them over time.

Currently available ion based products:
[http://www.linuxtech.net/features/nvidia_ion_products_overview.html]("http://www.linuxtech.net/features/nvidia_ion_products_overview.html")

---

### Post by Keithamus on 2009-10-28
My TV setup is very close to blackoper, and I would say close to perfect, but I have two identical frontends and a backend server:

[http://mythtv.org/wiki/User:Keithamus]("http://mythtv.org/wiki/User:Keithamus")

I would say a backend server is worthwhile, if you can afford it (don't just think the cost of parts, think the cost of electricity, the cost of maintenance time, cost of speccing time etc).

I've spent lots of time and money on my setup to get it working just how I want it. I got a Athlon processor + 740g chipset for my server because under clocked it outputs under 50w, so about £4 a month in electricity costs. The server is the biggest expense to think about, as tempting as it is to get a Xeon or even a lowly Q6600, these will kill your electricity bill. 

My frontends are the 330, which uses about 4w more power. The extra core doesn't actually do much, so if I had to do it again I would go for the 230. These would cost about £2 a month to run 24/7 but obviously these are shut off when not in use.

I want to get my frontends running diskless. Blackoper, how did you find setting this up? Any advice for someone with a very similar setup?

Going diskless I feel is important if you have any more than 1 frontend. The task of maintaining 2 or more frontends can quickly become a chore. The benefits of a diskless system is that you'll only have one "system" to maintain, which is standardised across all frontends, and, as long as you standardise on the frontends, you can drop in new frontends in minutes (...about 30 minutes including build time).

So some takeaway tips are:

[LIST]
[*]Think low power, server CPU specs rarely matter (My setup would get by on 500mhz)
[*]The M350 + Zotac Ion is an absolutely killer combination
[*]If you require more than one frontend, diskless is a great way forward.
[*]Oh, and, go gigabit ethernet! Wireless is only really good for web browsing
[/LIST]

---

### Post by blackoper on 2009-10-30
hmm well I did the official 9.10 upgrade and the mythbuntu control center no longer has the diskless menu options in system roles.. strange. I'll create a new forum thread

---

