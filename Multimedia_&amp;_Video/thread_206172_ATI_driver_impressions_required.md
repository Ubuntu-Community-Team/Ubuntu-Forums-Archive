---
title: "ATI driver impressions required"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by xrchris on 2006-06-29
Hi there i have the ear of one of the guys at ATI in Canada who is canvassing for opinions on another forum i hang out on regarding their current Linux drivers.

He specifically said 
[quote="ATI_Mobile_Guy"]Has anyone tried the linux driver posted over a month ago?  There was some initial feedback I got on this thread early on about the state of our linux support, and it was before we released a driver for the current X1000 family.  Just looking for anything (positive or negative) I can pass onto folks internally.[/quote]

**Please only give honest and constructive replies and no nonsense - Thanks.**

---

### Post by doog on 2006-06-29
I have a Compaq R4000 with ATI Radeon Express 200m with 128MB onboard memory.  2D and 3D support back in the ATI driver version 8.13.4 was just fine. Shortly after that driver, DRI stopped working with the onboard video memory and hasn't worked since.

There has probably been hundreds to possibly thousands of hours wasted by Linux users trying to get this working. And the things that have to be done to even get 2D working have turned a bunch of new Linux users away from Linux because they just couldn't get the ATI driver working on these laptops. 

So, I'd be very happy to see the ATI driver once again working like it used to a year ago but with the current release of kernel and Xorg.

Thank you.

---

### Post by evil_elman on 2006-06-30
2D is sloooooow... 3D is fine...

What would be REALLY nice are the following:
* Replace 'aticonfig' with a graphical tool for those settings which changes the xorg.conf for me.
* Some wordings doesn't mean anything. For example, I've got an S-video out on my laptop but all the settings for TV out are called SCART, VIDEO or YUV. Which one is S-video?
* What kind of TV-system is PAL-SCART?
* I would like to be able to have video overlay on both external screen (VGA/S-video) and laptop screen... Currently I have to choose all the time.

Laptop used: Acer TravelMate 4601LCi with a Mobility Radeon X600 (64 MB).

---

### Post by ltmon on 2006-06-30
By far the best source for real information on ATIs linux drivers:

[http://www.phoronix.com/scan.php?page=article&item=501&num=1](http://www.phoronix.com/scan.php?page=article&item=501&num=1)
[http://www.phoronix.com/redblog/](http://www.phoronix.com/redblog/)

L.

---

### Post by doog on 2006-07-01
[QUOTE=ltmon]By far the best source for real information on ATIs linux drivers:

[http://www.phoronix.com/scan.php?page=article&item=501&num=1](http://www.phoronix.com/scan.php?page=article&item=501&num=1)
[http://www.phoronix.com/redblog/](http://www.phoronix.com/redblog/)

L.[/QUOTE]
WOW, it sounds like ATI actually acknowledged the Express 200M( R200 ) problem with using onboard( Sideport ) video memory!  There is hope after all. And the dynamic display changing stuff sound cool too but just give me fullspeed 3D and I'll be happy.

Thanks for the link(s)

---

