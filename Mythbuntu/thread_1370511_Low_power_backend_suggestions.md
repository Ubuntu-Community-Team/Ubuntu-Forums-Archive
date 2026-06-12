---
title: "Low power backend suggestions"
date: 2010-01-02
forum: Mythbuntu
---

### Post by stevanbt on 2010-01-02
Hi,
I bought one of those electricity usage meters recently - and have since become obsessed with reducing power usage of my PCs.  The Antec Fusion frontend has gone and has been replaced with an Acer Revo R3600 (and it works brilliantly, inc HD).

Now on to the backend, and this is where I'm looking for suggestions.  The new backend has to be financed, as much as possible, by the sale of the old backend.  So I'd like to keep costs down as much as possible.  The following is a minimum spec:-
[LIST]
[*]Low power (under 100 watts would be nice)
[*]2 x PCI slots (I have two Hauppauge DVB-S cards to rehouse)
[*]2 x SATA (two HDDs to rehouse)
[*]gigabit LAN
[*]No need for beefy CPU as I don't transcode recordings
[*]Graphics isn't an issue as it's backend only
[/LIST]

I've looked at ITX motherboards, but from what I can see they only have one PCI slot - or does a two slot ITX MB exist?

Thanks in advance, Steve.

---

### Post by kevinatkins on 2010-01-02
Hi,

Mini-ITX might be the way to go - one of the Via Epia models would work pretty well. I built a PVR up a few years ago and went this route. You can use a 'riser' to expand on the single PCI slot on these boards.

I can't remember the exact details of the Epia model I used, but it featured a low-power processor, TV-Out, hardware MPEG2 decoding (required, in view of the lowly processor), etc.. It worked well - not a rocket ship, but enough for the purpose.

To keep your power consumption down still further, you might want to consider dropping to just one hard drive. Also be aware that some of the DVB cards can have surprisingly high power consumption

---

### Post by tonycollinet on 2010-02-07
Search just dug up this thread.

To me 100W seems pretty high power for a backend - remember this thing is on all the time. 100W will cost about £100/year in leccy.

I've just measured my combined frontend/backend, and it is only running at 85W now, and this was just an old PC from Mrs TC's work with various bits thrown in it.

I will be looking to get somthing down at the 10-20W range (excluding tv card) if possible. It doesn't have to be quick, as it is only dumping data from a digital card to disk.


Any and all alternate suggestions welcome.

---

### Post by volkswagner on 2010-02-07
I am also curious here.  

Will an old pentium 2 machine be up to the task?  

From what I have around, the most RAM in my Pent2 400 would be 768MB.  With 5 PCI slots, I could add a SATA card, and a couple tuners.  I believe at idle with on HD, and no tuners the box was drawing about ~35 watts, which was nearly a third of a pentium4 box.

I had researched a while back, how to install mythbackend without X, seemed a little involved, but that was when I first entered the Linux arena.

So could a Pentium2 400MHz with 768MB RAM run a backend for two frontends?

I just may try it.  If not I'll be moving my Atom 330 box to the task and just use one tuner.

---

### Post by ian dobson on 2010-02-07
Hi,

Maybe have a look at a M-ATX motherboard with a low power cpu. Maybe a intel chipset board with onboard graphic and an underclocked C2D CPU.

Note: DVB tuner cards quite often use about 10watts, harddisks 10-15watts so your 100watt budget is quite tight.
 
Regards
Ian DObson

---

### Post by 4dognight on 2010-02-07
I originally used a P3-600, which worked fine. Its power consumption is very low.
But, perhaps you should be looking into having your BE and FE shutdown when not in use. Even if its down for just overnight( approx 8 hours) , you will have a power savings of 30%. Also, if your buying new hard drives, look into the low power versions. 

I used a killawatt meter on all my equipment and realized it was using quite a bit of power(I have 1-BE and 2-FE). I had it setup to shutdown when not in use, when I was running 8.04, but there have been new changes in 9.10, and have to go over and reconfigure it again.

---

### Post by stevanbt on 2010-02-07
Thanks to all for the information.  

My BE currently uses acpi wake and wake-on-lan so is only on when either recording or one of the FEs is on.

If the PCI cards draw 10 watts each and HDDs draw 10-15 then I'm already up at 40-50 watts (2 x DVB-S PCI cards and 2 x HDD).  So 100 watts does seem tight.

I decided to recycle an old SFF P4 and did a lot of prep to get everything swapped over only to find that the DVB-S cards were too tall - nice.  Back to the drawing board!

I do use an atom processor with Nvidia ION on the FE - absolutely no complaints there.

Thanks, Steve.

---

### Post by ian dobson on 2010-02-07
Hi,

My measurement's might have been abit off. Just found this:-

For the green conscious, be aware that the Caviar Black does draw more power from the PSU than, say, the Caviar Green line (which is to be expected). The Caviar Black draws approximately 8.4 watts of power when performing read and write operations while pulling 7.8 watts while idling. In contrast, the Caviar Green line pulls 7.4 watts during read and write operations and only 4 watts while idling. In terms of standby and sleep modes, each drive is about 1 watt, with the Caviar Green taking a slight lead drawing 0.98 watts. This is still better than Segate's Barracuda 7200.11, which requires 11.6 watts while performing reading and writing operations and a not so eco-friendly 8 watts while simply idling.

from: [http://www.gamingshogun.com/Article/3623/Western_Digital_Caviar_Black_1TB_Hard_Drive_Review.html](http://www.gamingshogun.com/Article/3623/Western_Digital_Caviar_Black_1TB_Hard_Drive_Review.html)

Regards
Ian Dobson

---

### Post by sniffton on 2010-02-08
Has anyone thought about setting up a uber low powered-pc that could wakeup other myth-boxes as needed?

N

---

### Post by 4dognight on 2010-02-08
That feature is builtin to mythtv already.

---

### Post by cascade9 on 2010-02-08
> **ian dobson said:**
> Maybe have a look at a M-ATX motherboard with a low power cpu. Maybe a intel chipset board with onboard graphic and an underclocked C2D CPU.

Note: DVB tuner cards quite often use about 10watts, harddisks 10-15watts so your 100watt budget is quite tight.

Or a AMD 'e' series (45watts) or even better, one of the new 'u' series (25watts).(for dual core, some of the triple and quad core 'e' series are 65watts)  Yep, that is full load TDP, with a bit of underclocking you that would drop even lower. Pity that at the moment the 'u' series CPUs appear to be OEM only, but knownign AMD there will be some form of retail version at soem point. You might be able to find them at some 'online marketplace' though ;) 

BTW, you might find this worth having a look at- 

[http://www.xbitlabs.com/articles/coolers/display/system-wattage.html](http://www.xbitlabs.com/articles/coolers/display/system-wattage.html)

> **ian dobson said:**
> For the green conscious, be aware that the Caviar Black does draw more power from the PSU than, say, the Caviar Green line (which is to be expected). The Caviar Black draws approximately 8.4 watts of power when performing read and write operations while pulling 7.8 watts while idling. In contrast, the Caviar Green line pulls 7.4 watts during read and write operations and only 4 watts while idling. 

Different article with the same message- 

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_21.html#sect0](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_21.html#sect0)

The Green Power drives arent just nice from the power consumption point of view, they also run very cool and are pretty quiet into the deal. Great drives IMO.

---

### Post by movieman on 2010-02-08
> **cascade9 said:**
> The Green Power drives arent just nice from the power consumption point of view, they also run very cool and are pretty quiet into the deal. Great drives IMO.

Yeah, my Green Power drives are hardly audible at all. Certainly with the MythTV backend by the side of the TV I've never heard the disks in operation from the sofa.

However, note that WD are in the process of switching to 4k sectors, which may not play nice with Linux at this moment. If possible, get the 512-byte EADS models rather than the 4k EARS models, for best compatibility.

---

### Post by laffinet on 2010-02-09
> **movieman said:**
> However, note that WD are in the process of switching to 4k sectors, which may not play nice with Linux at this moment.

Can you elaborate ? Just bought an EARS model, but haven't unpacked or installed it yet.

---

### Post by movieman on 2010-02-09
> **laffinet said:**
> Can you elaborate ? Just bought an EARS model, but haven't unpacked or installed it yet.

Here's a decent article on the subject:

[http://www.anandtech.com/storage/showdoc.aspx?i=3691&cp=8](http://www.anandtech.com/storage/showdoc.aspx?i=3691&cp=8)

The new WD drives use sectors that are 4k in size rather than 512 bytes: that means either the operating system has to support big sectors, or the drive has to do read/modify/write for small writes to the drive.

I still haven't been about to determine whether or not Linux does support 4k sectors natively yet.

---

### Post by laffinet on 2010-02-09
> **movieman said:**
> 
I still haven't been about to determine whether or not Linux does support 4k sectors natively yet.

That's obviously exactly the bit I'm interested in ;)

---

### Post by cascade9 on 2010-02-10
> **movieman said:**
> Here's a decent article on the subject:

[http://www.anandtech.com/storage/showdoc.aspx?i=3691&cp=8](http://www.anandtech.com/storage/showdoc.aspx?i=3691&cp=8)

The new WD drives use sectors that are 4k in size rather than 512 bytes: that means either the operating system has to support big sectors, or the drive has to do read/modify/write for small writes to the drive.

I still haven't been about to determine whether or not Linux does support 4k sectors natively yet.

From your link- 

> Notably, Linux and Mac OS X are not affected by this issue. Western Digital has tested both of these operating systems, and officially classifies them as not-affected. Ultimately we suspect that if you went back far enough you could find older versions of these OSes that are affected, but unlike Win 5.xx, there’s not a significant legacy user base to worry about. Along these lines, Linux and Mac OS X drive imaging products are similarly unaffected. In their testing, imaging tools such as SuperDuper didn’t run in to any alignment issues, so Linux and Mac OS X users are not affected in any way by 4K sectors. It’s only Windows and Windows imaging products that are affected.

Should be fine running a WD EARS on any currently supported linux version.

---

### Post by movieman on 2010-02-10
> **cascade9 said:**
> Should be fine running a WD EARS on any currently supported linux version.

Yeah, but I believe that was only referring to the alignment and not to actually working with 4k sectors on the disk. 

Presumably using the 512 byte emulation mode won't matter for streaming large amounts of data to the disk since they'll typically end up being written as sequential blocks that can be concatenated, but it could be a dog if you're writing a lot of small blocks. The most recent comments I found on the subject were from last spring talking about the kernel requiring significant changes to remove the assumption that disk blocks are always 512 bytes.

---

### Post by laffinet on 2010-02-10
Well, I found [this]("http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395;jsessionid=628A1577464CB0414EAABA1F999C6A58") thread, which does talk about problems quite recently. 

I'm currently running through the "parted" procedure (the fdisk one still left me with start blocks at 63, which from what I understand is not good.

Let's see how we go...

---

