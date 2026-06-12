---
title: "TV Tuner / Capture Card Choices"
date: 2009-07-20
forum: Multimedia Software
---

### Post by DGortze380 on 2009-07-20
Hey All,

I'm building a media center box and have been researching capture cards for about a week now ... my head is spinning ... some help/advice would be much appreciated.

Basically I'm just trying to decide on a tuner card. Hauppauge seems to have the best support for Linux, so I've been focused there. I know I can get an older p-150 or p-350 but would really prefer to use more up-to-date hardware.

I'm looking at the hvr-1250 1196 and the hvr-1800 1128.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028)

[http://www.newegg.com/Product/ProductReview.aspx?Item=15-116-015&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=linux](http://www.newegg.com/Product/ProductReview.aspx?Item=15-116-015&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=linux)

Both seem to have mixed reviews, I'm looking for some definitive answers about both cards. I'd like to run them on Mythbuntu (MythTV) to tuner and capture Digital Cable (Comcast in Massachusetts / Cox in Rhode Island).

My big questions are:

1) Support - Are both cards well supported in Linux? Will they tune and record ATSC/NTSC/ClearQAM?

2) Am I correct in assuming that with these cards, I will be able to receive any channels that I would typically receive with a cable line straight to a cable-ready TV (no set top box)?

3) I'm running a Core 2 Duo at 3.0GHz with an Nvidia 8800GT. I'd prefer a card with a hardware encoder, but it's not in the budget I don't think. Will this set-up be able to reliable encode/decode in MythTV?

---

### Post by cb951303 on 2009-07-20
1) For TV card I would go with [this one]("http://www.pchdtv.com/"). It's a little bit expensive but at least it's designed for linux.

> 
The pcHDTVTM Hi Definition Television Card is the most popular and best supported 5th generation digital television card specifically designed for the Linux OS. The HD-5500 is a universal PCI card and is shipped with a custom HDTV version of Xine Media Player to provide playback on your computer monitor. **The popular Linux media center project, MythTV, includes complete support for the card and it's HDTV support was designed around pcHDTV HDTV cards.**

3) Your setup is more than enough for software decoding, I don't think you need a TV card with a dedicated decoder chip. Also, Xine and Mplayer supports Nvidia's hardware video decoding technology. In a way, you already have a hardware decoder :)

EDIT: Just like I thought. Another quote from the website: > Accelerated HDTV support with nVidia video cards. 

---

### Post by wbee on 2009-07-21
Hello,

Head spinning seems to be the norm getting a TV tuner card to work.

Here is a card that is well reviewed,uses USB, and provides Linux drivers:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3867990&CatId=1427](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3867990&CatId=1427)

It's at the top of my list when I get digital cable(in the US).

Let me say that I have not used this card but I learned a lesson with TV tuner cards.

A cheap one is a false economy(and I'm a cheapskate). I have an MSI TV Anywhere Plus(the plus is for the remote control option.) It's an analogue card that functions as a second sound card,with a bit rater OTHER than 44.1,16b.

Getting the sound to work was a pain--and it's still not good sound.

Good luck and keep us informed.

---

