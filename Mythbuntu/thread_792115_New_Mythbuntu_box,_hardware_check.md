---
title: "New Mythbuntu box, hardware check"
date: 2008-05-12
forum: Mythbuntu
---

### Post by campbecf on 2008-05-12
Hi all, I was planning on building a Mythbuntu box soon and wanted to check the compatibility of the following hardware and ask advice on filling in the gaps:

I'm going to be using the SiliconDust HD Homerun as my TV Turner and using the "ASUS M3N78-EMH HDMI AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard" as my motherboard.

Will the HDMI out work from that motherboard in linux? What kind of processor and RAM will I need to handle HD using the HDHomeRun as my tuner.

Am I correct in assuming I will be able to hook my digital cable box (Time Warner) to HDHomeRun to my computer then to my HDTV via HDMI?

Thanks

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> Hi all, I was planning on building a Mythbuntu box soon and wanted to check the compatibility of the following hardware and ask advice on filling in the gaps:

I'm going to be using the SiliconDust HD Homerun as my TV Turner and using the "ASUS M3N78-EMH HDMI AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard" as my motherboard.

Will the HDMI out work from that motherboard in linux? What kind of processor and RAM will I need to handle HD using the HDHomeRun as my tuner.

Am I correct in assuming I will be able to hook my digital cable box (Time Warner) to HDHomeRun to my computer then to my HDTV via HDMI?

Thanks

3 GHZ minimum.  AFAIK, you can't do audio over HDMI.  Not exactly sure why you would want to hook your digital cable box up to a HDHomeRun, use a PVR-500 instead (or PVR-150)

---

### Post by Weidbrewer on 2008-05-14
Well, I took a look at that mobo on newegg, and it certainly has an HDMI out connector, so aside from any software shenanigans I don't see why it wouldn't work.  However, I'm never sure about onboard graphics.   But here's the good news:  It sounds like you've already got the board, so if it works, great - if it doesn't, you just need to add a graphics card with HDMI out.

As for processor and RAM, I believe that the recommended minimum is for HD stuff 3.0 Ghz (or equivalent), and a 1G RAM.  For the CPU, something [like this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103775") should do the trick.  RAM, more is better.  If you're not sticking to "as cheap as possible," I probably wouldn't go with the minimums since you're doing HD.  Grab at least 2G of RAM from a reliable company like Crucial, Corsair, Patriot, etc.

As for your capture card, I'm sorry but I don't have any experience with that one.  Also, I haven't run my digital cable box in, though I know it can be done.

A further thought:  Again, since you're doing HD, which is about 7GB an hour, if memory serves, and you want to keep recordings around - get yourself a nice big, fat drive and format it with a format-type that plays nice with deleting large files, like jfs/xfs

Hope this helps!

---

### Post by campbecf on 2008-05-14
HDHomeRun was listed on the Mythbuntu wiki under Recommended Tuners for High Definition. I figured it was the best option because of that.

Are you sure you can't do sound over HDMI? 

I was also considering using this (  MSI Media Live ) [http://www.newegg.com/Product/Product.aspx?Item=N82E16856167020](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167020) and HDMI instead of the Asus. Does anyone have comments on the MSI Media Live?

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> HDHomeRun was listed on the Mythbuntu wiki under Recommended Tuners for High Definition. I figured it was the best option because of that.

Are you sure you can't do sound over HDMI? 

I was also considering using this (  MSI Media Live ) [http://www.newegg.com/Product/Product.aspx?Item=N82E16856167020](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167020) and HDMI instead of the Asus.

Ok, you need to do a little more research before you try to do this.  At this time (until the Hauppauge HD PVR ships) you can't output from your cable box and get HD.  Your cable box will not output HD over coax.  Wait until the hauppauge HD PVR gets released and get that instead.

The HDHomerun is for HD, but not from a cable box.

---

### Post by campbecf on 2008-05-14
Few questions regarding this:

If coax can't carry HD then how does the HD reach my cable box? Its got a coax connection. 

If my cable provider encrypts then isn't it necessary to use the cable box?

What can I use to get HD from my cable box to my Myth box?

---

### Post by whosmatt on 2008-05-14
> **campbecf said:**
> Few questions regarding this:

If coax can't carry HD then how does the HD reach my cable box? Its got a coax connection. 

If my cable provider encrypts then isn't it necessary to use the cable box?

What can I use to get HD from my cable box to my Myth box?

I think what they mean is that the RF modulator output from your cable box is an analog connector and does not output HD.

You are correct in thinking that you won't be able to tune the encrypted channels without the cable box.  The HDhomerun tuner should tune the unencrypted ones just fine.

As someone above pointed out, Hauppauge is about to release an HD capture device that has component inputs.  Until this is released and supported in MythTV, you are probably out of luck as far as getting an HD signal from your cable box into myth.

---

### Post by campbecf on 2008-05-14
Isn't the HD PVR out ? 

[http://www.hauppauge.com/site/products/data_hdpvr.html](http://www.hauppauge.com/site/products/data_hdpvr.html)

Is that what is being talked about above? It sounds more like a device in itself rather than something to use as a tuner.

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> Isn't the HD PVR out ? 

[http://www.hauppauge.com/site/products/data_hdpvr.html](http://www.hauppauge.com/site/products/data_hdpvr.html)

Is that what is being talked about above? It sounds more like a device in itself rather than something to use as a tuner.

That is what everyone is talking about and if you pre-ordered early then it might have started shipping.  If you order now, it will not ship until after May.

It is not a tuner, but an external MPEG4 hardware encoder that will take component in.  There is no other device on the market for what you want to do. (yet)

---

### Post by campbecf on 2008-05-14
Can you link me to the product page or give me the exact product name?

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> Can you link me to the product page or give me the exact product name?

Exact product name of what?

---

### Post by campbecf on 2008-05-14
Hauppauge HD PVR

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> Hauppauge HD PVR

I'd be happy to link you to the product page for the Hauppauge HD PVR.  It is located [here]("http://www.hauppauge.com/site/products/data_hdpvr.html")

---

### Post by campbecf on 2008-05-14
So I Go CableBox ---Component Cables--> HD PVR -- ???? --> PC

What do I use to go to the PC? USB? Is MythTV Going to support HD PVR input via USB?

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> So I Go CableBox ---Component Cables--> HD PVR -- ???? --> PC

What do I use to go to the PC? USB? Is MythTV Going to support HD PVR input via USB?

Yes, the HD PVR plugs into the PC via USB.  From what I hear, MythTV will support the HD PVR, perhaps soon after it is released (perhaps right out of the gate)

---

### Post by campbecf on 2008-05-14
The linked to page has a buy order, doesn't say anything about shipping dates or pre-ordering, are you sure its not already out?

---

### Post by tgm4883 on 2008-05-14
> **campbecf said:**
> The linked to page has a buy order, doesn't say anything about shipping dates or pre-ordering, are you sure its not already out?

Been following this thing since it was announced at CES.  It's out, but you must understand that they have to fulfill the pre-orders first.  I'm kinda busy right now and can't look it up, but IIRC people who preordered got an email explaining this situation.  Order now and yours will ship in the beginning of June.

---

### Post by tgm4883 on 2008-05-14
I did a quick search and this is what I found
[http://brentevans.blogspot.com/2008/04/hauppauge-hd-pvr-shipping-delayed-to.html](http://brentevans.blogspot.com/2008/04/hauppauge-hd-pvr-shipping-delayed-to.html)

I've seen this echoed around in mailing lists so it seems to be true

---

### Post by campbecf on 2008-05-14
Has anyone, or could anyone, with the product reported on compatibility with linux and MythTV?

---

