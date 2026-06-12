---
title: "What's a good cheap printer/scanner that works with 10.10?"
date: 2010-08-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2010-08-15
We were able to manually setup drivers for Epson Stylus NX215 on 9.10, but it stopped working on 10.10 and Epson uses 3rd party company Avasys.jp for their Linux drivers.


Can anyone give recommendations for a printer/scanner brand with strong Linux drivers support?

---

### Post by cariboo on 2010-08-15
Cheap and good shouldn't be used in the same sentence. I've always paid between $200.00 and $400.00 for printers, and never had a problem with drivers.

Usually you can't go wrong with HP, but I have a Epson r340 and a Brother HL-5052dn, both are a snap to set up, the Brother even automagically fetches the drivers for it self.

I saw that Lexmark now has Linux drivers for their printers too.

---

### Post by ronacc on 2010-08-15
I have a brother mfc-7440n (print/scan/fax/copy) that works good with all flavors of ubuntu I have tried it on , brother provides linux drivers  for their stuff on their website .The only problem I have had is that my damn router changes its address every time I poweroff and restart the router .keep an eye on office supply stores for sales ( officemax ,staples , etc )

---

### Post by bennachie on 2010-08-15
Any of the basic HP 2200 or 4200 "all-in-one" series will do the job quite adequately, at least in a "light-duty, modest-expectations" context. Both variants work fine with 10.04 and 10.10 (and many other distros), and can be purchased very cheaply. In Australia, it seems to be easier to find inexpensive generic replacement cartridges for the 2200 series. YMMV.

---

### Post by ktp on 2010-08-15
> **cariboo907 said:**
> I saw that Lexmark now has Linux drivers for their printers too.

If you going for linux, then I still won't get lexmark.  Their driver for linux has limited "features" and only works for specific models.  HP is the best for linux in my option.

---

### Post by ranch hand on 2010-08-15
> **ktp said:**
> If you going for linux, then I still won't get lexmark.  Their driver for linux has limited "features" and only works for specific models.  HP is the best for linux in my option.
I have some problems with HPs approach to "support" of their product if you have a problem but their support of OSS drivers is just great.  I do not like to get any other kind of printer at all.

---

### Post by sparker256 on 2010-08-15
I have had a HP 4780 for about 3 months an and very happy with it. It is wireless and was set up completely in Ubuntu and is less that $100.00. It prints from Linux and windows machines with no problems at all. I wanted wireless so that whatever computer is on in the house it has a printer to print to. It is working with Ubuntu 10.04 10.10 and windows xp.

Bill

---

### Post by SoFl W on 2010-08-15
> **TDK800 said:**
> We were able to manually setup drivers for Epson Stylus NX215 on 9.10, but it stopped working on 10.10 and Epson uses 3rd party company Avasys.jp for their Linux drivers.
Can anyone give recommendations for a printer/scanner brand with strong Linux drivers support?

I was able to get my Epson all-in-one working with Ubuntu, wireless over the network.
What kind of problems are you having?
See [THIS]("http://ubuntuforums.org/showthread.php?t=1393162") thread for help or ask.

---

### Post by SoFl W on 2010-08-15
> **ktp said:**
> If you going for linux, then I still won't get lexmark.  Their driver for linux has limited "features" and only works for specific models.  HP is the best for linux in my option.
I have heard both positive and negative things about Lexmark on these forums, supposedly the printer's box says it supports Linux where most other companies do not mention Lnux.

---

### Post by ktp on 2010-08-15
> **SoFl W said:**
> I have heard both positive and negative things about Lexmark on these forums, supposedly the printer's box says it supports Linux where most other companies do not mention Lnux.

"supports" can be it can print blank and white over usb-only.  I am not saying all Lexmark printers are like that in linux, but my experience is Lexmark drivers are new and very limited in linux compared to their windows versions.  My all-in-one wireless lexmark printer is "paperweight".  I guess I could get it to work over usb, but kind of useless since I got it for wireless support.  The irony in all this is, lexmark uses linux for it's wireless support. =)

HP has provided great linux support for their printers; for while now.

---

### Post by SoFl W on 2010-08-15
I will agree that HP is probably the best choice although I am very happy with my Epson.  If we can get the original poster's Epson working without him buying another printer that is even better.

---

### Post by M93 on 2010-08-15
i have HP all in one 4200 and its just fine.
worked with it on: (ubuntu, kubuntu, xbuntu)10.04, ubuntu 10.10, winXP, win vista and win7.
u can get it in a very good price :)

---

### Post by lonniehenry on 2010-08-15
hp Photosmart D110 all-in-one works- took almost a minute to set up, test page and scan first page in Maverick (also print from the web).  Took much longer for me to set it up in Win7.  About $100.00 and uses less expensive ink than the Deskjet 952 it replaced.

---

### Post by SoFl W on 2010-08-15
> **lonniehenry said:**
> (location).

Saranac Lake?  Has it warmed up there yet, or has it started to cool down for the winter?

---

### Post by lonniehenry on 2010-08-15
About average for this time of year- been a really hot summer tho.  
Avasys lists a driver for the OP's Epson- I can't tell if it will do him any good tho it looks like a newish page on their site.

---

### Post by Reiger on 2010-08-15
What you want is CUPS support rather than &#8220;Linux&#8221; support. So the easy answer is to go to:
[http://localhost:631/](http://localhost:631/) (which is the CUPS control panel).

Provide your Ubuntu username & password (you are logging on under your user account at the CUPS control panel); and use the Add Printer button under the Administration tab (or whatever equivalent name it has now) to set up a dummy printer to the point where it asks for make & model and scroll through the (pretty long) list which enumerates all &#8220;known&#8221; printers. Simply cancel the whole at that point if you do not have a printer to setup yet.

Also you can take the predicate &#8220;works with Mac&#8221; to mean &#8220;works with CUPS&#8221; and by extension &#8220;works with Linux&#8221;.

---

### Post by ktp on 2010-08-15
> **Reiger said:**
> Also you can take the predicate “works with Mac” to mean “works with CUPS” and by extension “works with Linux”.

Just word of caution, "works with Mac" doesn't mean it will be "plug-and-play with CUPS or Linux".  There are many printers which "works with Mac" but you will have hard time getting them to be even recognized in linux.

---

### Post by Col-1023 on 2010-08-16
How about stand-alone scanners, I have a hp colour laser printer, and am thinking of either getting a new scanner, or a second hand scanner.

Cannon & Epson seem to make most of the stand-alone scanners, though hp made them years ago, so which brand of scanners works best with linux?

TIA

---

### Post by VMC on 2010-08-16
> **Col-1023 said:**
> How about stand-alone scanners, I have a hp colour laser printer, and am thinking of either getting a new scanner, or a second hand scanner.

Cannon & Epson seem to make most of the stand-alone scanners, though hp made them years ago, so which brand of scanners works best with linux?

TIA

I have a **Cannon NV1200** scanner, and works great under Linux, but **will not** work under Windows7! It use to work using windowsXP.

My **HP 895Cse** printer works great also under Linux. Has for years.

---

### Post by aikishugyo on 2010-08-16
I suggest looking at the following pages for support:

**1. printers:**
gutenprint. Currently version 5.2.6, addition of literally dozens of lasers, several Canon multi-functions (some tested by myself, and more to come soon), and Epson.

Home page: [http://gimp-print.sourceforge.net/]("http://gimp-print.sourceforge.net/")

New printers supported in 5.2.6 release: [http://libregraphicsworld.org/news.php?readmore=516]("http://libregraphicsworld.org/news.php?readmore=516")

Some notes on a few makers.

Yes, Epson is a mixed blessing, as for printing they offer great resolution (full resolution) under linux if the printer is supported. If gutenprint supports it well, I think it is the best choice---not use the Epson software!

Canon too is a mixed blessing, as the linux drivers only support up to 600dpi (apparently no-one has yet been able to spend enough paid or unpaid time to figure out a reliable way to program higher resolutions). But the printing works perfectly for supported printers.

HP provides their own drivers, and as some have said, this could be the best option for various reasons, maybe not so cheap though as printer heads are included with the ink cartridges IIRC.

**2. scanners:**
SANE project, particularly the CVS scanner support list (currently updated as of 10th August). A new release is due in Autumn, as there have been maybe two dozen additions to support since April including, I am happy to say, the latest Canoscan 9000F and many multi-function devices, plus various of the LiDE series. You won't see those on the support page yet, but maybe in September.

SANE page: [http://www.sane-project.org]("http://www.sane-project.org")

CVS supported devices: [http://www.sane-project.org/lists/sane-mfgs-cvs.html]("http://www.sane-project.org/lists/sane-mfgs-cvs.html")

I try when I get a multi-function device, to add support to both SANE and gutenprint (in many cases the printer part is borked when I get it though). If both SANE and gutenprint have support, then you can be guaranteed to have a smooth user experience.

Many of the older Canon devices are pretty good, and compact, the MP510 for example).

Another thing is that if you get such a multi-function Canon device and it is not supported, you can be guaranteed of support within a very short time if you volunteer to be a tester (for Epson not so easy).

The above is only my opinion!
Regards,
Gernot

---

### Post by TNT1 on 2010-08-16
I think HP does good and cheap... I am using a 2480 all in one for about 6 months now. Works perfect, even when I upgraded from 9.04 to 10.04, it just carried on going. And I got it new for less than 100USD...

---

### Post by Col-1023 on 2010-08-16
Thanks Gernot, a very informative post, I'll check the SANE sites before getting a scanner.

---

### Post by Starks on 2010-08-16
You can't go wrong with HP or Epson. HP is plug-n-use 99% of the time. No 500MB driver to download or anything.

Avoid Dell printers. Even though they are rebranded Lexmark, most don't work.

---

### Post by recluce on 2010-08-16
Before you run out and buy any printer, do some homework on your per page cost. "Cheap" can get _really expensive_ in the long run. This is especially true of entry-model Lexmark printers, which I would avoid like the plague.

My printer: Canon ip4500 with self-compiled Canon driver (for some reason they only have the binary for 32-bit Linux on their website). Works great - and a Rihac CISS (Continous Ink Supply System) makes the printing cost a bargain.

---

### Post by TDK800 on 2010-08-17
scanner isn't detected and when attempting to print a single page, the Epson printer is pushing out all sheets in the tray without printing on them.

I got the NX215 working on 9.10 following an old thread here, I think it was this one: [http://ubuntuforums.org/showthread.php?t=1353566](http://ubuntuforums.org/showthread.php?t=1353566)

Got response from Epso today:
"Linux drivers for Epson products are supplied by Avasys Corporation.
Note: Neither Epson nor Avasys provide support for Linux drivers."

---

### Post by ktp on 2010-08-17
> **recluce said:**
> Before you run out and buy any printer, do some homework on your per page cost. "Cheap" can get _really expensive_ in the long run. This is especially true of entry-model Lexmark printers, which I would avoid like the plague.

Good advise...people forget to look at long run cost and mostly focus on initial cost.

---

### Post by drfox on 2010-08-17
Brother also has excellent support for Linux.
I use an MFC-7840W. I can connect wirelessly, by network cable, or by USB. I can print and scan wirelessly. Faxing from Linux is not as simple as in windows, but I either go to the machine and fax paper or email a pdf through my computer. 
I think the machine cost me about $250 a couple years ago. 
HTH. Larry

---

### Post by jerrylamos on 2010-08-17
> **ktp said:**
> Good advise...people forget to look at long run cost and mostly focus on initial cost.

Long term costs include ink cartridge costs !!  I get mine from Amazon.  You have a choice of original equipment, "repackaged" original, almost like original, and "you takes your chances".

We use Epson because the ink is less soluble with moisture than HP.  Epson uses an electric quartz crystal squirter while HP uses a hot wire to boil a bubble of water based ink to create the splat.

Epson Stylus NX400 is on this pc running fine with Maverick Alpha 3, Lucid, ...  The little built in screen does a good job of telling which cartridges need replacement.  If I haven't used it for a while there is a linux utility for cleaning the jets.  

The scanner is fine.  Screen shot and viewer do a good job of resizing & printing.  For what I do Picasa lets me crop, lighten, ... whatever.  

A new one (model number now NX420) costs $69.99 from TigerDirect.com. $64.24 from Amazon, might be a difference in wireless or not and didn't look at shipping.  As model NX520 available from Epson at $64.99.  

Best deal is $49 from the Epson Store Clearance Center as "refurbished" model number NX510.  I've bought two printers from their clearance store and they were both "spotless" and have never given me trouble, so long as I use reputable ink.  Totally crazy that an apparently new printer with a set of ink cartridges costs close to the price that just a set of brand name ink cartridges cost making the printer nearly free!

Good luck,
Jerry

---

### Post by aikishugyo on 2010-08-18
> **recluce said:**
> My printer: Canon ip4500 with self-compiled Canon driver (for some reason they only have the binary for 32-bit Linux on their website). Works great - and a Rihac CISS (Continuous Ink Supply System) makes the printing cost a bargain.

Question: does this Canon driver provide greater than 600dpi? It seemed from my reading that it did not (but I understand one can get very different offerings from different Canon sites). I currently use my iP4500 on linux with max 600dpi (gutenprint drivers), or with the native Canon driver in a Windows VM if I want to print edgeless (photos) and/or high resolution.

---

### Post by zenarcher on 2010-08-18
I use an HP Officejet 6310 All-in-One.  I've had maybe three of this series over the past few years and would highly recommend it.  Everything works perfectly...scanner, printer and fax.  One of the features I really like is that the printer has an ethernet port on it, which allows me to plug an ethernet cable from the printer to my wireless router.  Then, when running "hp-setup," I can set the printer up as a network printer and print to it from any computer in the house by wireless or ethernet connection to the router.  That, for me, makes it invaluable.

Cheers,
zenarcher

---

### Post by ronacc on 2010-08-18
for low "cost per page" if you don't need color , go with a black and white laser . Hi quality text and low cost .

---

### Post by jerrylamos on 2010-08-18
> **ronacc said:**
> for low "cost per page" if you don't need color , go with a black and white laser . Hi quality text and low cost .
Ronacc, along the lines of this thread, 

"what's a good low cost black & white laser printer"?

Does the laser do grey scale?

Does the laser scan?

What do the laser cartridges cost?

These thoughts cross my mind when I buy ink cartridges, which I use for photos anyway....

Thanks, Jerry

---

### Post by recluce on 2010-08-18
> **aikishugyo said:**
> Question: does this Canon driver provide greater than 600dpi? It seemed from my reading that it did not (but I understand one can get very different offerings from different Canon sites). I currently use my iP4500 on linux with max 600dpi (gutenprint drivers), or with the native Canon driver in a Windows VM if I want to print edgeless (photos) and/or high resolution.

600 dpi is maximum and on plain paper, more is not really needed. The only difference I see to the stock drivers Ubuntu has on board is much better colour accuracy. For photo printing, I do the same thing that you do.

---

### Post by recluce on 2010-08-18
> **ronacc said:**
> for low "cost per page" if you don't need color , go with a black and white laser . Hi quality text and low cost .

The same caveat applies here that applies to ink jet printers. Prices per page vary greatly for laser printers as well. Once again, some companies pull tricks like selling printers with toner cartridges only half-full and charging allmost as much for a cartridge as for the whole printer. So unfortunately, you will have to do your homework here as well!

---

### Post by recluce on 2010-08-18
> **jerrylamos said:**
> 
These thoughts cross my mind when I buy ink cartridges, which I use for photos anyway....


If you spend more than $150 a year on ink cartridges, check these guys out: [http://www.rihac.com.au](http://www.rihac.com.au)

I use about 600 ml of ink per year. Now calculate the cost for that if you buy cartridges....

---

### Post by libssd on 2010-08-18
Count me in the HP camp, since my pre-linux days. Their printers offer good value for money, have good paper handling, and durable. I am not aware of another printer manufacturer who provides better support for Linux.

---

### Post by ronacc on 2010-08-18
> **jerrylamos said:**
> Ronacc, along the lines of this thread, 

"what's a good low cost black & white laser printer"?

Does the laser do grey scale?

Does the laser scan?

What do the laser cartridges cost?

These thoughts cross my mind when I buy ink cartridges, which I use for photos anyway....

Thanks, Jerry

 I have used both samsung and brother (my current) with good results , the toner cartridges are a touch expensive ( about $70 US ) but yeild more than 3000 pages for a per page cost of 3 cents including paper . You can get both stand alone and multi function versions . I haven't costed out the color lasers as I only do text or simple b/w diagrams .
 I personally avoid inkjets like the plague I'd sooner go back to a dot matrix .

---

