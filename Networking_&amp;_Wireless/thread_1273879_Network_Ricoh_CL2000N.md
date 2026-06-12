---
title: "Network Ricoh CL2000N"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by zmerch on 2009-09-23
I have a Ricoh Aficio CL2000N network color laser printer that supports just about every durned thing under the sun, but it had some... ah... "hardware issues" as of late so I hadn't used it under 9.04 before.

(My backup printer was a parallel Samsung ML2130 on a print server which worked fine under 8.10/9.04)

The printer is now repaired, and I want to return using it as my main printer, but something's wonky with the network printer driver... somewhere.

The printer supports PCL5e _and_ PostScript 3. For Network protocols, it speaks JetDirect, IPP, NetWare, Appletalk, NetBEUI, LPR, and others... and I can hit it's internal webserver, I can ping it, I can telnet to it's CLI management system, I can telnet to port 9100 & "confuse" it (I have yet to find a key sequence to break out of the CLI on that, so all the ^L^M^D^C^A escape sequences ad nauseum make it go kinda crazy, and once I had to reboot the printer ;) ) I can even print to a postscript file and netcat the file to port 9100, and the printer dutifully prints the page.

The printer also works fine on the network under Winders (both native and on VirtualBox) and on SuSE 9.3 Pro (yea, it's old, but hey... it still works! ;) ).

So, for y'all about to tell me "The printer isn't working right," well...
:guitar:

Anyway, The printer seems to set up fine, Ubuntu finds it, it reads some status from it, it sends print jobs successfully, on the printer I see it receiving data, then on the LCD on the printer I see a quick flash of "Resetting Job" and no page.

I've tried adding the page through the normal "ubuntu" printer setup, I've also tried through the CUPS web administration page, neither to any avail whatsoever. I've tried IPP, HP and LPR, and no love there either. :(

I do know that there's Postscript error description code that sometimes print drivers can add on (it was an option on my old QMS Magicolor laser) that might b0rk things up.

I'm no stranger to compiling packages if that would help... so don't be afraid to suggest higher-level repairs.

Anyone have any ideas what I could try to get this rascal working again?

Thanks,
Roger "Merch" Merchberger

---

### Post by zmerch on 2009-09-26
My one & only {bump} just in case someone with experience with this printer will see it this time around...

Thanks!
Roger "Merch" Merchberger```
             
```:popcorn:

---

### Post by zmerch on 2009-09-29
Otay,

Had a little more time to beat my brains in about this... but only a *little*. Tried every which way to try to get my beautyrific Postscript printer working... and no dice. :-(

I turned everything on in the printer I could - heck - I even turned on AppleTalk! and yet, the only thing recognized is HP JetDirect printing on port 9100, which I suspect the printer defaults to as I even tried the generic socket with no port (just: "socket://123.123.123.123/) and it would send postscript jobs to the printer, the printer would flash "Resetting Job..." and no sheets of dead trees came out.

Did a little research on that Intarweb thingy, and thought I'd diddle with the PCL5c emulation, and try as I might, trying to change the existing printer to use the PCL5c driver was... problematic. It seems Linux has finally gotten "Too automatic." It kept querying the printer, seeing it would speak Postscript, and automatically set up the PS driver. :confused: So, I set up a whole new printer, and eventually I was able to set up the Foomatic PCL5c driver, aimed it at port 9100, and yay! It worked.... in black & white. :confused: Maybe I'm dense, but the whole point of PCL5c is "color" - who ever heard of a color driver that prints only monochrome? So, back to the Interwibble, and found that many people had good luck with the FooMatic/hpijs driver, and so I tried that one, and in the immortal words of Emeril Lagasse: "Bam!"

Cons:

1) only 600dpi... but it's not a worrysome con for me. I'm not concerned at this point - if I wanna print pictures, I have my Kodak DyeSub printer... but that's another thread. I rarely have things to print that require 1200dpi, and so I have time to solve this issue if that need comes up again.

2) In my experience, the Postscript driver for this printer was less buggy than the PCL5c emulation in windows, and in all other Linuxes PCL wasn't an option. I just hope that I don't hit the same bugs in Linux, as I don't currently have a PS "Plan B."

3) I paid almost $100 extra for the Postscript & 256Meg of RAM *for Linux*. (Well, that and the DEC 3000 Model 300 that runs VMS.) Ungh.

4) The PS driver from Ricoh could do things like query the printer for toner levels & whatnot. Another "not a big deal" con, as the printer's web interface has rough graphics. Only 1-4 bars, but at least if I hit 1 bar, I know I have to stock up on toner, and oddly enough in my small town, I have a Ricoh dealer that keeps toners in stock!

Pros:

1) It actually works! Yay! Huge Pro!

2) If I do get the Postscript driver working, I now have a "PCL Plan B" in Linux which I've never had before (but oddly enough, never needed until now).

3) Had to add one more Pro just to make sure people don't think I'm unhappy there's more Con's than Pro's... ;-)

Anyway, I'm printing, which is the good news. I'm still bummed about the lack of Postscript at this point... but I'll get over it. :)

Laterz!
Roger "Merch" Merchberger

---

