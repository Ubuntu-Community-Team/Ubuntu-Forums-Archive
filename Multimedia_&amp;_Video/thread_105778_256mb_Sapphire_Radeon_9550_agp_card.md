---
title: "256mb Sapphire Radeon 9550 agp card"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by Fibre on 2005-12-19
in Ubuntu device data base I'm getting this

	Vendor: GenuineIntel
Speed: 2679.162 MHz
Model: Intel(R) Celeron(R) CPU 2.66GHz 	
		Memory: 776 MB
Swap: 835 MB	
		Videodriver: "ati"
Colordepth: 24
Videomodes: "1024x768" "800x600" "640x480"
Videoram: 131072 kByte

Now if my card is a 256mb saphire radeon 9550, should it be shown as 131,072 kbyte's? doesn't that mean that it's seeing it as a 128mb card instead of a 256mb card?

If so how can I overcome this problem and also I noticed it say's that I've got 776mb of ram - I've got 768 of ram or is it measured slightly different for some reason.

If you've got  a 256mb ati card and know how to saught this out could you please help or if you know where i can look to saught it out.

Thank you for future help.

---

### Post by Zimmer on 2005-12-19
I have a Sapphire Radeon 9600 256mb

and the database is the same for me 

	Videodriver: "fglrx"
Colordepth: 24
Videomodes: "1024x768" "800x600" "640x480"
Videoram: 131072 kByte

? I must investigate....

Zimmer

---

### Post by Fibre on 2005-12-20
Yeah please let me know what you come up with zimmer, it doesn't look right to me.

My card has **128-Bit memory interface**, so whether this is actually meaning this I'm not sure. It's not one of my need to know area's but what is shown about my card is. I want to make sure it's running at it's full capacity for gaming etc.

Thanks for any help Zimmer. :)

One other thing Zimmer I noticed your driver is "fglrx" is this a better driver?

I'm having problems with a tv card and its saying something about YUY2 capabilities and drivers for my agp card? ( not sure exactly of the word but I think it was YUY2 ) you probably don't have a tv card but with that fglrx I would like to know your opinion plz.

---

### Post by Fibre on 2005-12-20
have you ever tried placing this into your terminal Zimmer:-

fglrxinfo

[COLOR="Red"]username@computer:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)[/COLOR]

This is what i get I'm going to have to update my drivers to the same as yours I think mine are out dated a little and could be causing minor problems.

But I still would like to know what it is referring to whether its the 256mb mix up or it relates to 128-Bit memory interface?

Oh yeah I read some where that our card have the same architecture so they might look the same apart from the thing I've just shown above in red might vary " check it out and let me know as I'm interested in the outcome as well".

---

### Post by Zimmer on 2005-12-20
Fibre..
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

So no difference there...
So far I have found this (old, 2003) snippet (I am not a graphics expert BTW, just a retired SAS  and Recital DB programmer)

[http://svn.uludag.org.tr/pardus/pardus-devel/desktop/freedesktop/xorg/files/1214_all_4.3.0-radeon-disable-VideoRAM-option.patch](http://svn.uludag.org.tr/pardus/pardus-devel/desktop/freedesktop/xorg/files/1214_all_4.3.0-radeon-disable-VideoRAM-option.patch)
Have Xmas shopping to do , so will have to delve more later..
EDIT.....
Well more delving, and 3 hours of it..
The snippet relating to the disable VideoRam option that I posted earlier popped up again in a Fedora C4 post in XFree drivers as Patch1214: XFree86-4.3.0-radeon-disable-VideoRAM-option.patch
then this:
[http://www.hardwaresecrets.com/article/131](http://www.hardwaresecrets.com/article/131)
[http://www.ati.com/products/radeon9600/radeon9600pro/compare.html](http://www.ati.com/products/radeon9600/radeon9600pro/compare.html) 
All tech specs show the 9600 series with a 128 interface (except 9600SE 64).
The Sapphire 256mb cards exist. You can still buy them...if you look hard enough.
So, is the driver recognising and autodetecting the card as a 9600 and only enabling 128, because the driver writers don't realise there is a 9600 with 256mb ?? (or is 256 enabled and we don't know it.?..still delving on that one...)
Who do we ask?

Zimmer
No point in using the config to try and over ride it..

 	xf86DrvMsg(pScrn->scrnIndex, X_INFO,
-		   "Video RAM override, using %d kB instead of %d kB\n",
+		   "VideoRAM override ignored, this driver autodetects RAM\n",

:( : ( :(

---

### Post by Fibre on 2005-12-22
I've been searching but not coming up with anything worth mentioning that you havn't already shown here.

I don't know either, if somebody does please post your input to us.

It's either talking about our memory interface or it's counting our 256mb's as half what they actually are.

I might be gone for a couple of days with christmas Zimmer. But let me know your findings I am interested. good luck.

I'm not to bright when it comes to this sought but I did find out that [COLOR="Red"]Videoram: 131072 kByte [/COLOR]Is referring to DRAM?

LOL is DRAM talking about the amount of mb's or memory Interface LOL

HELP US Somebody much help please.

Really just a tenee tiny bit actually, WHAT IS VIDEORAM (dram) referring to?

Will check in a couple a day.

---

