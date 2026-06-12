---
title: "Mythtv Box suggestions"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-06-19
I am looking to build a new Mythtv box that is not an ATX format.  Something that looks less ... nerdy, and that will fit in my component stand.

Check out my newegg build:  [https://secure.newegg.com/NewVersion/WishList/MySavedWishDetail.asp?ID=4727552](https://secure.newegg.com/NewVersion/WishList/MySavedWishDetail.asp?ID=4727552)

[ nMEDIAPC HTPC 100 SA Silver Steel]("http://www.newegg.com/product/product.asp?item=N82E16811204001")
 [ASUS M2NPV-VM Socket AM2 NVIDIA GeForce 6150]("http://www.newegg.com/product/product.asp?item=N82E16813131014")
[ GIGABYTE GV-NX71G512P8-RH GeForce 7100GS]("http://www.newegg.com/product/product.asp?item=N82E16814125047")
500Gb HD,
PVR 150
AMD Atholon 64 3200
2x512mb Ram

Any suggestions on where I can cut down on expense, or on how to make this build better is greatly appreciated.

Thanks,
Hans

---

### Post by hansoffate on 2007-06-21
Any Suggestions?  Please?

Thanks,
Hans

---

### Post by lionsnob on 2007-06-21
Hello, I have one suggestion.  Why get a separate video card when you have DVI and VGA built in already?  Is it for TV out?  That could save you $43.

---

### Post by hansoffate on 2007-06-21
For svideo out, but that is a good point.  I can just get a cable that converts vga -> composite (I don't have HD) or should I just get a dvi->HDMI

Thanks for that catch.  I didn't actually notice it had DVI.

-Hans

---

### Post by BillDozer on 2007-06-22
Nice looking case. I especially like the LCD and the card reader, I don't have them in my case. 

But as I stated in my other [thread]("http://ubuntuforums.org/showthread.php?t=478229"), it is really important to have a quiet frontend. Here I come to three moving parts that all will give off some noise, two fans and a HDD.

It all depends on how you want to use this machine. Should it be a dedicated mythtv box or do you also want to use it as an ordinary desktop, looking at the specs it looks like you also want to use it for other purposes than only a mythtv box.

My mythtv box only uses about 18 watt when showing a recording and recording something at the same time, so a 300 watt power supply may be overkill. But again, it all depends on how you wish to use the machine

---

### Post by hansoffate on 2007-06-22
This will be 100% mythtv.  I wont' be using this box for any other purpose but mythtv.  Do you feel the other case would be a better choice because of the external power supply?

I want to make this a frontend/backend secondary server setup with a 400-500 gb hard drive.  Can I do this with the case you suggested in the other thread?

Or maybe I should just make a frontend only box and stick the 400 gb hard drive in the other server with another pvr 150, or maybe a 500 so I get the added recording space that I wanted and more tuner cards like I wanted.  What do you think sounds like a better plan?

If I did do the frontend only solution I would probably get the EX10000EG (fanless).  I am a bit scared to because I have to compile a driver from openchrome and do this [http://ubuntuforums.org/showthread.php?t=443589](http://ubuntuforums.org/showthread.php?t=443589)

Thanks for the help and suggestions,
Hans

---

### Post by BillDozer on 2007-06-27
I would go for the frontend if I were you and put the HDD (and tuner card) into the server machine.

Regarding to the case, here I would try to find a fanless one, just to keep the noise down. My next frontends will be as small as possible, preferrably only a case, VIA motherboard/CPU + memory, that start over the network.

I do not think you have to be scared to compile the driver, as you can see in the post you linked to, he got it working when using the experimental branch drivers (just like I did). I also was a bit scared about this part, but following the [openchrome compile guide ]("https://help.ubuntu.com/community/OpenChrome?highlight=%28openchrome%29") and downloading the experimental branch drivers as specified [here]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Work%20In%20Progress"). I only did the 2D driver and that was good enough.

To start of I would find a small HDD (maybe an old one you have lying around). Put it in and get the system to work. After it works and you got the experience on how all the components have to be set up, I would go and figure out how to start it as a diskless frontend (I haven't tried this yet, but this will be my own ultimate frontend). Instead of a diskless frontend you could also choose to start from a flash drive (haven't tried this either ;-), but it should work).

In the end, to give you sort-of-an-answer, it's all up to you. I do not know what is the best solution, I can only tell how I plan to do it myself and what looks like the right way to me (at least for the moment). But I think you will become most happy with a dedicated noisless frontend, eventhough it will be a bit harder to setup if you keep it completely noise free (when using it as a diskless frontend).

---

### Post by louistan3 on 2007-06-27
i havent used mythTV before but i suggest you look for a cheaper processor.

if im thinkin of this right, i believe an athlon 64 3200 is a bit overkill for a dedicated box.

but i might be wrong and am underestimating the resource demands of mythTV.

but if not, maybe changin it might save you some money.

hope this helps :)

---

