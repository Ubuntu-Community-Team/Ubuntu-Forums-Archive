---
title: "Printer Set-up via Wireless Router"
date: 2005-01-13
forum: Networking &amp; Wireless
---

### Post by ali_bongos_dad on 2005-01-13
Never mind being a Linux "newbie" I'm  new to the guts of computing! My experience is using software - MessWord, Eggshell and OughtoCad at work - not tinkering with the engine; that's for the IT dept. So bear with me with this problem.

How do I set up printing on my system. I have an IBM T22 Thinkpad with a DLink DWL-AG650 WiFi card; the printer is an HP Deskjet 959C which is connected to an SMC Barricade G 2804WBRP-G wireless router via its USB port.

The instructions that came with the router say to use the <printconf-gui> command to configure printing. However this command does not exist in Ubuntu/Gnome.

After Googling around I found someone who had a similar problem with their Mepis system; they found the answer by using the CUPS printer interface [http://localhost:631/admin](http://localhost:631/admin) and adding the printer as an LPD/LPR Device.
Ubuntu/Gnome forbids the use of that URI informing me to use Computer-> System Configuration-> Printing. That's were I come unstuck again. What do I type in the Host and Queue slots? Is the Host the Network Address of the router? Is Queue lp, lpt1, lpd or what? Do I have to include any Port numbers anywhere?
I've tried allsorts of permutations but without any results.

I'm sure it's a simple answer to most users but I'm tearing my hair out. Other than this problem I'm finding using Linux/Ubuntu and the included applications very enjoyable with little or no trouble.

---

### Post by hardcandy on 2005-01-14
The host should be the router IP address and the que should LPT1. Is CuPS refusing to connect because the router is asking for a password?

---

### Post by ali_bongos_dad on 2005-01-14
Many thanks, that worked.   

However the printer spews out a blank sheet of paper after every print job. Any ideas on how to stop this happening?

---

### Post by hardcandy on 2005-01-14
"The Barricade print server takes remote LPR requests and is compatible with LPRNG, LPR, CUPS, and commercial OS printing systems (Commercial OSs require special drivers to make it work however). There is a glitch in the Barricade's lpd however, and printing from a UNIX or Linux platform produces the actual print job, then a blank page, then an LPR job trailer page. Annoying and wasteful. The last time I checked SMC is working on fixing the firmware and releasing a patch to fix this bug. Until then be prepared to stuff one page back into your paper tray, and one page into your scrap paper pile."
[http://www.linuxhardware.org/article.pl?sid=03/03/14/2152244&mode=thread](http://www.linuxhardware.org/article.pl?sid=03/03/14/2152244&mode=thread)

Any chance of a firmware upgrade? The latest version is 12/6/04 if I typed everything in correctly. Double check me before downloading. 
[http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=5&userPartNumber=&modelNumber=544&partNumber=2427&downloadType=2&os=0](http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=5&userPartNumber=&modelNumber=544&partNumber=2427&downloadType=2&os=0)

---

### Post by moptop on 2005-02-28
not a ubuntu user yet, but debian/sid...  just wondered whether ali_bongos_dad or anyone else had tried out the firmware update?  Just wondering whether this problem is fixable yet...

matt

---

### Post by ali_bongos_dad on 2005-03-02
I haven't been able to install the new firmware. Incidentally the router/print server I have is the SMC2804WBRP-G and not as the ones Hardcandy posted about. 
I have tried to install the new firmware (dated 14.Feb.05)after reading your posting the other night but it would not install; then today I decided to download the f/w again in case there was a problem with the original download and I noticed that it had been revised again, still dated 14. Feb. 05 However I could not get this to install either. Even if or when it is installed I still do know if it will cure the problem.
The bulk of any printing done is via the two MS Window machines my family use; and there is no problem in that case. The amount of printing that is done from the Linux m/c is minimal, just the odd page or two, so I don't find the extra blank page too much of a problem.
BTW in my case the server only gives out one blank page after each print job and not two as suggested by Hardcandy so there isn't any waste.

---

### Post by gadgetgirl02 on 2007-11-24
I've got a similar problem with different hardware.

I've got an MSI wireless router with a USB port that connects to my Epson printer. The router can find the printer and knows what it is; the queue is enabled. This I've confirmed by accessing the router's settings via my wireless connection (which means that my Ubuntu machine can also find the router). Now I need to figure out how to get Ubuntu to see the printer that's attached to the router.

I know my router's IP address, and it says its print server name is lpt1. What I can't figure out is which fields to use in the printer config utility to tell Ubuntu where the printer is. Is this IPP? If so, how do I enter the address? I tried [http://192.168.1.294/lpt1](http://192.168.1.294/lpt1) (there, now you all know my router's local address :-) ), but that doesn't work. If I try using IPP, it says it can't find any queues.

---

### Post by gadgetgirl02 on 2007-11-25
I've done some more looking around on Ubuntu Forums and elsewhere, and decided I should expand my original post a bit:

It sounds like I should be using IPP as the option when I add a new printer, so that I can use the URI. However, when I do that (using either [http://192.168.1.254](http://192.168.1.254) or [http://192.168.1.254/lpt1](http://192.168.1.254/lpt1)), the printer setup says there are no queues available. I've tried using the Other option and entering the URI -- in that case the print job is created but never reaches the printer.

I also found an entry about a CUPS bug from a year ago that occurred when this network setup was used. The forum where people were commenting on the bug said it had never been resolved. Anyone here know about this?

---

### Post by ali_bongos_dad on 2007-11-25
If you look at the date of my original posting you will see it was almost 3 years ago! I'd forgotten about this problem as I now have a different printer and set-up.
I seem to remember that when I had the set-up you're referring to I used the LPD (Unix) option when setting up the printer, adding the router's URI to Host and lpt1 to Queue.
In your case the Host URI would be 192.168.1.294
Hope this helps.

---

### Post by gadgetgirl02 on 2007-11-25
Thanks for reviving the thread!

I've heard a few other people mention setting the printer up as a "Unix" printer. I must say I have no idea what that means. It's not an option in the printer setup -- how does one do this?

---

### Post by ali_bongos_dad on 2007-11-25
Go to System > Administration > Printing Select New Printer
Ubuntu should find the printer it will be shown in the Use a detected printer window.
Click on Forward and select the Manufacturer and Model for your printer.
That should be it.

---

### Post by gadgetgirl02 on 2007-11-25
Aha! There's the rub. It's not finding the printer. I've been entering the URI and server info in whatever fields will take it, but so far no go.

Maybe I should close this thread and open a new one.

Thanks for trying to help!

---

### Post by ali_bongos_dad on 2007-11-25
In that case try selecting Network Printer in Step 1 of Printer Connection
Then scroll to Unix Printer (LPD)
Fill in the Host and Queue as I said in my first reply
Then follow the instructions for the selection of your printer.
If this does not work then I'm also stuck.

---

### Post by gadgetgirl02 on 2007-11-25
:) Well, that *wasn't* it, but it made me look at my printer settings again, and I found it! It's one of those cases where in the process of solving the primary problem a secondary problem keeps you from resolving.

Here's a summary for anyone who happens to stumble across this thread in the future:

**Problem:** need to print to a remote printer connected via USB directly to my router

**Ubuntu version:** Gutsy Gibbon

[LIST]
[*]printer already known to work with Ubuntu (have used both connected directly to Ubuntu box and connected to a remote Ubuntu box, both with parallel and USB connections)
[*]router with USB connection directly to printer (Router is confirmed to work with Ubuntu; router can see printer on its USB port)
[/LIST]

**[SIZE="2"]Steps:[/SIZE]**

[LIST=1]
[*]Go to System->Administration->Printing
[*]Click New Printer. Ubuntu will search for printers. In my case it didn't find any, but if it does in your case you may be able to skip some of the steps below.
[*]The Select Connection dialogue will appear. Select LPD/LPR Host or Printer from the list.
[*]In the Hostname field, enter the URI of your router, which in my case is 192.168.1.254. Note: clicking the Probe button did nothing for me, so I just continued manual setting entry.
[*]In the Printername field, enter the print server name, which in my case is lpt1.
[*]Click the Forward button.
[*]Ubuntu will search for drivers. Tell Ubuntu what printer and driver you want to use (in my case, Epson Stylus Color 777, recommended driver). Click Forward.
[*]Enter the printer name, description, and location per the instructions in the dialogue.
[*]Now the parts that caught me: click the name of the printer in the Local Printers list, and make sure the Device URI says lpd://192.168.1.254/lpt1. If you didn't enter things correctly, it will say something different. Click the Change button and re-check your entry.
[*]Next, go to the Policies tab and make sure Enabled, Accepting Jobs, and Shared are all checked in the State section. For some bizarre reason, Enabled defaulted to being checked **off** when I first set up the printer on my laptop. That was the secondary problem keeping me from resolving my primary problem. I always did brand-new printer adds when I was fiddling with this, so I'm not sure how it got switched off. 
[/LIST]

If all that fails, you may have a different issue.

Thanks to ali_bongos_dad for responding to this thread after it lay dormant for three years -- more proof that the Ubuntu community is the best!

---

