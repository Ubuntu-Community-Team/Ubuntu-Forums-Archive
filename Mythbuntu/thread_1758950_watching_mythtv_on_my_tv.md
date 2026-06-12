---
title: "watching mythtv on my tv"
date: 2011-05-15
forum: Mythbuntu
---

### Post by rudy1094 on 2011-05-15
I have mythbuntu 11.04 installed on my computer and I can watch tv on my computer monitor, but I would like to watch tv on my television. I bought a VGA to s-video cable to connect the computer to the tv. I have an older standard definition tv with RCA connectors and s-video connectors. When I plug the computer into the tv, I'm getting some white/grey horizontal lines that scroll up the black screen. I'm not getting the image that I get when I use the computer monitor. What do I need to do to configure my mythbuntu system to display on my television?

---

### Post by klc5555 on 2011-05-15
A VGA to S-video cable is probably not going to do it.

The issue is likely what video card you have, what driver it uses, whether it supports old-style TV out at all, and, if so, whether through an S-cable port or through composite or component output. You might want to read the myth wiki page on the subject here: [http://www.mythtv.org/wiki/TV_Out](http://www.mythtv.org/wiki/TV_Out)

---

### Post by LowSky on 2011-05-15
A lot of the VGA to S-video cable you can buy on ebay are garbage and don't work. 

Sorry if you wasted your money

---

### Post by uteck on 2011-05-16
You could try the cable but after you change the resolution on the computer to something the TV can handle.  Try 1024x768 or 800x600, anything higher on a standard def TV will not work.

---

### Post by dallas8101 on 2011-05-17
Only a few video cards support the mode that the svga to svideo cable works with.

I have used these, PC to TV Converter VGA to RCA S-Video, in the past:
[http://www.amazon.com/gp/product/B000X3FAJU](http://www.amazon.com/gp/product/B000X3FAJU)

---

### Post by klc5555 on 2011-05-17
If the OP is going to have to buy a new video card, he might want first to try to find online one of the older NVidia GeForce series from the analog era (like some of the 6xx series) that support s-video out directly and even provide a port on the card for the purpose. That way he could just use a standard s-video cable and avoid the whole VGA/S-Video adapter issue altogether.

---

### Post by rudy1094 on 2011-05-17
I had a dell optiplex gx520 with a geforce 6200 video card that I was using, but the high def channels were very choppy. So I bought an AMD Phenom x4 kit from tigerdirect with a geforce 210 video card. This computer can handle the HD channels, but it doesn't appear that my tv can handle the output from my video card. It looks like I'm going to have to upgrade my tv. So for now I can watch mythtv on my computer monitor.

---

### Post by crbnrod on 2011-05-17
I'm not really a videophile, but if at all possible, I'd recommend a videocard upgrade over a VGA -> TV converter. I have [this thing]("http://www.amazon.com/Sewell-PC-VGA-RCA-Converter/dp/B002PXFJ2O/ref=sr_1_2?s=electronics&ie=UTF8&qid=1305667721&sr=1-2"), and while it does what it says it will do, it's pretty distractingly bad, quality wise, on the TV.

Of course, all of this is a good excuse to upgrade a television, too.

---

### Post by klc5555 on 2011-05-18
> **rudy1094 said:**
> I had a dell optiplex gx520 with a geforce 6200 video card that I was using, but the high def channels were very choppy. So I bought an AMD Phenom x4 kit from tigerdirect with a geforce 210 video card. This computer can handle the HD channels, but it doesn't appear that my tv can handle the output from my video card. It looks like I'm going to have to upgrade my tv. So for now I can watch mythtv on my computer monitor.

A GeForce 6200 can handle HD. I used to use an AGP version of one for this purpose, until the MoBo it was on died. The odds are the dell Optiplex didn't have the CPU horsepower to go along with the 6200, at least without old-fashioned XvMC implemented.

If you've retained your old 6200 card with S-Video out, and if your new MoBo has a slot the 6200 fits, you will probably experience success with it on the HD channels until such time as your TV gets upgraded.

---

### Post by faginbagin on 2011-05-19
I suggest spending your money on an nVidia card that has an HDTV out connector. These look like S-Video connectors, and you can plug in an S-Video cable to them. But they also accept a dongle that allows you to connect them to your old standard definition TV using either composite or component cables. You don't have to use something as old as the 6x00 nvidia series. You can find 9x00 series cards that will allow you to use vdpau in mythtv. This one should do the job:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130395)
Same card, $10 less here:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4111742&CatId=3669](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4111742&CatId=3669)

---

