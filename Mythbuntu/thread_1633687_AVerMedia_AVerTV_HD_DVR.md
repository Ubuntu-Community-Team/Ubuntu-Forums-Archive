---
title: "AVerMedia AVerTV HD DVR"
date: 2010-11-29
forum: Mythbuntu
---

### Post by madsciencecoder on 2010-11-29
Hello, I am in the process of building my first mythbox.  I was wondering if anyone knew if the AVerMedia AVerTV HD DVR will work under linux.  Here's the link for the product [http://www.newegg.com/Product/Product.aspx?Item=15-100-049&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=3#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=15-100-049&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=3#scrollFullInfo)

Also any other recommendations for a good tuner/capture card would be appreciated.  I do however have a requirement of it being able to decode encrypted cable through either a cablecard or letting my cable box decrypt the signal.

---

### Post by EggoubHTPC on 2011-02-20
Did you ever find an answer to this? I have the same card and am having trouble finding a driver.

---

### Post by nickrout on 2011-02-20
It does not have linux drivers and is never likely to.

Also it's usefulness would be limited to streams that your provider has okayed to be recorded/copied.

---

### Post by madsciencecoder on 2011-02-20
I have not found a driver for it, sorry.  I did some more research and I believe that mythtv doesn't support an hdmi capture card or even a cablecard anyway, something to do with those crazy cable companies wanting to control everything and protect it and linux being completely open so they are unable to support it.

---

### Post by nickrout on 2011-02-20
> **madsciencecoder said:**
> I have not found a driver for it, sorry.  I did some more research and I believe that mythtv doesn't support an hdmi capture card or even a cablecard anyway, something to do with those crazy cable companies wanting to control everything and protect it and linux being completely open so they are unable to support it.

you got it in one. There are many threads about it on the mythtv mailing list.

---

### Post by sxe4ever on 2011-07-09
I was hoping to use this to be able to connect my PS3 to my computer using the HDMI connection. Has anyone had any luck with this card, or know of anyway that I can do this?

---

### Post by itlarson on 2011-07-10
Have you looked at the [HDHomeRun PRIME]("http://www.silicondust.com/products/models/hdhr3-cc/")?  It's a cable-card device which will allow you to record digital cable, and is supported by mythtv.  This only for "copy freely" channels, so you need to check which channels your cable provider flags this way.  You can find a bit more info [here]("http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime").

---

### Post by nickrout on 2011-07-10
> **sxe4ever said:**
> I was hoping to use this to be able to connect my PS3 to my computer using the HDMI connection. Has anyone had any luck with this card, or know of anyway that I can do this?

Read above, this card does not have linux drivers and is never likely to.

---

### Post by o0 avid 0o on 2012-06-18
Hi there.. I'm new to this forum and somewhat new to Linux.. well I used to use UNIX back in the day but I'll admit sometime after being a Commodore Amiga only user dabbled in UNIX and Linux before going headlong into winblows. I wish I'd stuck with Linux from the beginning but hindsight is 20/20 they say.. anyways i have scoured the Internet for info regarding this issue as I have an Avermedia AverTV HD DVR PCI-E card and I use it purely for playing my Playstation 3. Now I've asked questions here and there other places and have gotten replies like "well why don't you just.." then the stupidity spews forth like connect it directly to your monitor or get an adapter or buy a new.. I don't want to. I WANT to use Ubuntu Linus i HATE windows, have for years and I want to use my AverTV card on my computer in Ubuntu.. that said, answers like "this card does not have Linux drivers and is never likely to" are discouraging and honestly, kind of silly. I mean why WOULDN'T someone create drivers for it? something to do with legality issues ie copying copyrighted media etc? I'm not at all interested in recording stuff, I just want to play my Playstation 3 without having to keep a windows installation on my computer. The software that comes with my card isn't the greatest but it works. it will NOT let me record anything from my Playstation 3 AT ALL.  I've tried only because I wanted to see if it would. I don't care in the least that it doesn't. Also, I've tried a million times a million different ways to get VLC to use this card and it won't. in fact I haven't got ANY other software to work with this card. I'm sure there is something that may work, I don't know.. 

Anyways, If i knew more than C=64 BASIC and Amiga C (even though its been YEARS and I forget it all lol) or stayed in college longer than a term and half in programming perhaps I'd write it myself but I can't so.. can anyone here tell me if there is ANY possible way to use this card within Ubuntu? I'd be forever grateful. Even if its like a hacked up version of some other thing whatever, I am newish to Linux but still know my way around a little..

Thanks in advance.. and so far, I'm glad to be apart of a tight knit community that seems super nice and willing to help, it makes me reminiscent of my Amiga days :) I hope to stick around..

---

### Post by nickrout on 2012-06-18
> **o0 avid 0o said:**
> Hi there.. I'm new to this forum and somewhat new to Linux.. well I used to use UNIX back in the day but I'll admit sometime after being a Commodore Amiga only user dabbled in UNIX and Linux before going headlong into winblows. I wish I'd stuck with Linux from the beginning but hindsight is 20/20 they say.. anyways i have scoured the Internet for info regarding this issue as I have an Avermedia AverTV HD DVR PCI-E card and I use it purely for playing my Playstation 3. Now I've asked questions here and there other places and have gotten replies like "well why don't you just.." then the stupidity spews forth like connect it directly to your monitor or get an adapter or buy a new.. I don't want to. I WANT to use Ubuntu Linus i HATE windows, have for years and I want to use my AverTV card on my computer in Ubuntu.. that said, answers like "this card does not have Linux drivers and is never likely to" are discouraging and honestly, kind of silly. I mean why WOULDN'T someone create drivers for it? something to do with legality issues ie copying copyrighted media etc? I'm not at all interested in recording stuff, I just want to play my Playstation 3 without having to keep a windows installation on my computer. The software that comes with my card isn't the greatest but it works. it will NOT let me record anything from my Playstation 3 AT ALL.  I've tried only because I wanted to see if it would. I don't care in the least that it doesn't. Also, I've tried a million times a million different ways to get VLC to use this card and it won't. in fact I haven't got ANY other software to work with this card. I'm sure there is something that may work, I don't know.. 

Anyways, If i knew more than C=64 BASIC and Amiga C (even though its been YEARS and I forget it all lol) or stayed in college longer than a term and half in programming perhaps I'd write it myself but I can't so.. can anyone here tell me if there is ANY possible way to use this card within Ubuntu? I'd be forever grateful. Even if its like a hacked up version of some other thing whatever, I am newish to Linux but still know my way around a little..

Thanks in advance.. and so far, I'm glad to be apart of a tight knit community that seems super nice and willing to help, it makes me reminiscent of my Amiga days :) I hope to stick around..

This thread is quite old and I can't recall why I said drivers were unlikely. Whether because mythtv has no hdcp support, or the manufacturer doesn't supply any chipset info I do not know. I suggest you ask somewhere like LKML or Devib at kernellabs.

---

### Post by cariboo on 2012-06-20
Ubuntu has changed quite a bit since this thread was created. I'd suggest you start a new one, as this one is closed.

---

