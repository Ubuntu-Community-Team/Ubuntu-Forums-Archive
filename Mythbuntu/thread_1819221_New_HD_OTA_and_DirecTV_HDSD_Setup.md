---
title: "New HD OTA and DirecTV HD/SD Setup"
date: 2011-08-05
forum: Mythbuntu
---

### Post by hairymoot on 2011-08-05
I'd like to make a MythTV back end and front end for my house. I want to record OTA local HD channels. I would also like to record my Directv HD Channels and SD channels.  My house is going to be networked, so I'd put the Backend in my computer room.
 
The front end computer is actually my 3 year old Game Machine. I am planning to put in another Hard drive just for the MythTV to run from. I will dual boot with windows 7. So I could still play games on my 40 inch HDTV but when I wanted to watch MythTV I'd reboot for it.

**Front end / Game machine**

Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor BX80570E8400
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115037](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115037)

Zotac Geforce 9800 GTX PCI express 2.0
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500039](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500039)

ABIT IP35 Pro LGA 775 Intel P35 ATX Intel Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813127030](http://www.newegg.com/Product/Product.aspx?Item=N82E16813127030)

Creative 70SB088000004 7.1 Channels 24-bit 96KHz PCI Express 1x Interface PCI Express Sound Blaster X-Fi Titanium
[http://www.newegg.com/Product/Product.aspx?Item=29-102-024&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=%28keywords%29&Page=1](http://www.newegg.com/Product/Product.aspx?Item=29-102-024&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=%28keywords%29&Page=1)

4 gigs of memory

Maybe a Bluray player:
SAMSUNG Black 12X BD-ROM 16X DVD-ROM 48X CD-ROM SATA Internal Blu-ray Combo Model SH-B123L LightScribe Support - OEM
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827151222](http://www.newegg.com/Product/Product.aspx?Item=N82E16827151222)

**Back End:**

HP - Factory-Refurbished Pavilion Slimline Desktop / AMD Athlon™ II X2 Processor / 3GB Memory / 500GB Hard Drive
[http://www.bestbuy.com/site/HP+-+Factory-Refurbished+Pavilion+Slimline+Desktop+/+AMD+Athlon%26%23153%3B+II+X2+Processor+/+3GB+Memory+/+500GB+Hard+Drive/2918396.p?id=1218363392189&skuId=2918396](http://www.bestbuy.com/site/HP+-+Factory-Refurbished+Pavilion+Slimline+Desktop+/+AMD+Athlon%26%23153%3B+II+X2+Processor+/+3GB+Memory+/+500GB+Hard+Drive/2918396.p?id=1218363392189&skuId=2918396)

This HP has 4 expansion slots: 1 PCI Express x16, 2 PCI Express x1, 1 PCI

Star tech ST1000BT32 1 Port PCI 10/100/1000 32 Bit Gigabit Ethernet Network Adapter Card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833114004](http://www.newegg.com/Product/Product.aspx?Item=N82E16833114004)

I have no idea what tuner cards to purchase. I think I may spend the big bucks to get the HD channels from the Directv reciever:
Hauppauge HD PVR High Definition Personal Video Recorder 1212 USB 2.0 Interface
[http://www.newegg.com/Product/Product.aspx?Item=15-116-030&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=mythtv&Page=1](http://www.newegg.com/Product/Product.aspx?Item=15-116-030&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=mythtv&Page=1)

OTA Channels I'm not sure what to get. I'd like to be able to record 2 shows at once OTA.  I heard the HDHomerun is good but I also hear that they don't recieve a very strong signal OTA. This may be a problem because I have one or two weak network channels. They may be better now. I'm not sure.

**Other Thoughts:**

I am planning on using my PS3 to view the recorded stuff from my MythTV Back end in my bedroom. Or if the Xbox 360 will do the same thing I'd use it. I believe I've read the PS3 will do this but not sure about the Xbox 360

---

### Post by LowSky on 2011-08-08
I can verify that the PS3 will read the upnp server mythtv creates.

BUT when using the HD PVR you need to change the audio to AC3. The standard is AAC and the PS3 will not play it for whatever reason. to do so is easy

use this command in terminal... also place it in startup applications so it comes on automatically on a reboot.

```
v4l2-ctl --device=/dev/video0 --set-ctrl=audio_encoding=4
```

Note video0 is used on my system your may be a different value. use your mythtv backend settings.


The HD Homerun is probably the best at the moment for support. It also just recently was upgraded so the newer model will work better hopefully for channel scans.

---

### Post by hairymoot on 2011-08-08
Thanks for he reply. I'm thinking about putting this together in 3 months when I move to my house. 

I was getting a couple of weak OTA hd channels before with an antenna. I'm concerned that the HDhomerun's tuner may not be as strong. Now the outside antenna will be at a higher level than before. I may be able to pick up the OTA HD signal better with the increased in height. I'll only know when I get out there.

I have about a year left on my contract with DTV. I'm thinking about either canceling for U-verse or Dish OR just canceling pay tv altogether and watching the OTA free TV combined with streaming NetFlix for some variety. I'm thinking with my MythTV and OTA HD network stuff, I would be ok saving about $90 bucks a month.

---

### Post by LowSky on 2011-08-08
silicondsut, the makers of the hdhomerun have an amazing site that can tell you what channels to expect with OTA: [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

Also I see no need for the Ethernet pci csrd for the backend. the hdhomerun can be connected to your router.

---

