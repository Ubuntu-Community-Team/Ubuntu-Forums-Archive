---
title: "Hardware for backend - newbie"
date: 2011-02-18
forum: Mythbuntu
---

### Post by vskatusa on 2011-02-18
Hi,

I am a newbie.....

I am planning to install with the following hardware for mythubuntu BACKEND. Would appreciate any critic on the hardware - Will it record HD etc...

1. Mobo Gigabyte K8M800-8237 
2. CPU AMD ATHLON64 3200+
3. 2 GB DDR memory
4. Nividia 8400 GS
5. Have HDHOMERUN 

I need a PCI tv card RECOMMENDATION (Most compatible card in USA) which has 1 ANALOG (yes analog) and 1 DIGITAL.

Are the above hardware enough for my needs? can it record HD stream from HDHOMERUN without a problem? Do I need the graphics card for backend? I am a newbie hence please be patient if I ask stupid questions

---

### Post by nickrout on 2011-02-18
> **vskatusa said:**
> Hi,

I am a newbie.....

I am planning to install with the following hardware for mythubuntu BACKEND. Would appreciate any critic on the hardware - Will it record HD etc...

1. Mobo Gigabyte K8M800-8237 
2. CPU AMD ATHLON64 3200+
3. 2 GB DDR memory
4. Nividia 8400 GS
5. Have HDHOMERUN 

I need a PCI tv card RECOMMENDATION (Most compatible card in USA) which has 1 ANALOG (yes analog) and 1 DIGITAL.

Are the above hardware enough for my needs? can it record HD stream from HDHOMERUN without a problem? Do I need the graphics card for backend? I am a newbie hence please be patient if I ask stupid questions

CPU requirements for a backend are very low, you are usually just transferring a stream from the tuner card to hard drive. A fast CPU is only required for framegrabber analogue cards (where the compression is being done on the CPU), for trancoding or for commercial detection. 

The main emphasis these days is power saving.

If this is truly just a backend you don't need the nvidia card, any old card will do.

---

### Post by mr_luksom on 2011-02-18
Or no graphics card. I have a similar system to the one you have specced, the only real cpu usage is when it is commercial flagging (5-10% of the time, 40% cpu) or transcoding (which I do not use).

Most of my backend cpu cycles go to my boinc projects - screw power savings :)

---

### Post by rhpot1991 on 2011-02-19
> **vskatusa said:**
> 
I need a PCI tv card RECOMMENDATION (Most compatible card in USA) which has 1 ANALOG (yes analog) and 1 DIGITAL.

Are the above hardware enough for my needs? can it record HD stream from HDHOMERUN without a problem?

Hardware looks good to me, and the HDHR will work fine with that.

Personally I'd just use the HDHR and grab a cheap Hauppauge pvr-xxx card off of ebay or something.  With multirec enabled on the HDHR odds are you will not need the extra digital.

If you really want to add another PCI card to do both then the Hauppauge HVR-1600 should work well: [http://www.amazon.com/gp/product/B001AZEHD0?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B001AZEHD0](http://www.amazon.com/gp/product/B001AZEHD0?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B001AZEHD0)

I am assuming you understand that on the digital end you will most likely only get your local channels, and most cable companies are doing away with analog feeds all together?

---

### Post by vskatusa on 2011-02-19
Thanks so much. My research tells me MYTHUBUNTU is the easiest install for a newbie - Is there any other flavor which is much easier than MYTHUBUNTU?

---

### Post by mr_luksom on 2011-02-20
I haven't tried Windblows Media center, however Mythbuntu is about as easy as MythTV gets.

---

