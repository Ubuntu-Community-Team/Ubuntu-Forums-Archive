---
title: "AMD Apu vs Intel D2525"
date: 2011-07-20
forum: Mythbuntu
---

### Post by Jake.Debord on 2011-07-20
OK gang, about to order my motherboard to get this ball rolling for my first HTPC and now I cannot decide between these two mother boards:

1)
[http://www.newegg.com/Product/Product.aspx?Item=13-131-698&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=3#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=13-131-698&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=3#scrollFullInfo)

and 2)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500065](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500065)

I will be using this as a backend/front end and also end up using a usb tuner so the encodeing will be done on the cpu... Any suggestions? Good bad ugly? 

Thanks!

---

### Post by ian dobson on 2011-07-21
Hi,

AMD/ATI graphic cards are known to be not the best for Linux/Mythtv. Other than that both look like nice low power boards.

The ATOM board uses a NVidia chipset/graphic card which should work well with MythTV using the NVidia closed source driver for vdpau support (hardware acceleration of video playback).

Regards
Ian Dobson

---

### Post by Jake.Debord on 2011-07-21
The only thing I was worried about was if it would run the backend/frontend smoothly. Then decided if it cant I will just use it as a front end and throw something together for a backend. My case simply doesn't have enough room for anything with a fan on the heat sink. I ended up getting the atom board. I plan on writing something up on here when I'm done because there doesn't look to be a whole lot of reviews out for this board yet. I hope I'm not disappointed!

---

### Post by ian dobson on 2011-07-21
> **Jake.Debord said:**
> The only thing I was worried about was if it would run the backend/frontend smoothly. Then decided if it cant I will just use it as a front end and throw something together for a backend. My case simply doesn't have enough room for anything with a fan on the heat sink. I ended up getting the atom board. I plan on writing something up on here when I'm done because there doesn't look to be a whole lot of reviews out for this board yet. I hope I'm not disappointed!

Backend shouldn't be any problem for any PC that can run Linux. The frontend and video playback is always a problem. Without hardware acceleration you need a very fast CPU to handle the video stream, that's why I talked mainly about NVidia/ATI.

But I think you made the right choice, and I can't imagine you'll have too many problems with it.

Regards
Ian Dobson

---

### Post by Jake.Debord on 2011-07-21
Cool, thanks. I was just worried about the encoding/recording of TV I only have analogue cable here so nothing too crazy like digital or highdef channels other than over the air channels. But, if that becomes a problem then I may have to find a usb tv tuner that does encoding on it to keep it off the CPU and then should be fine :)

---

