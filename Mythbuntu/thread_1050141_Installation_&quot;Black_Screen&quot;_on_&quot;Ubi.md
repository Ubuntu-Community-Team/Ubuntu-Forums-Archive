---
title: "Installation &quot;Black Screen&quot; on &quot;Ubiquity Loading...&quot;"
date: 2009-01-25
forum: Mythbuntu
---

### Post by bryanf2009 on 2009-01-25
I have tried everything I can think of:

[LIST]
[*]F2 English
[*]F3 UK
[*]F4 Normal Mode
[*]F4 Safe Graphics Mode
[*]V4 OEM Mode
[*]F6 acpi=off
[*]F6 noapic
[*]F6 nolapic
[*]F6 edd=on
[*]F6 Free Software Only
[/LIST]

I tried the above in various combinations etc to no evail - just keep getting a balacn screen.

I have tried installs for:
[LIST]
[*]Mythbuntu 9.04 Alpha 3 64 Bit (x86_64)
[*]Mythbuntu 9.04 Alpha 3 32 Bit (i386)
[*]Mythbuntu 8.10 64 Bit (x86_64)
[/LIST]

One thing I noticed is there is only one install for x86_64 (I am assuming it is the same insatll for either AMD or INTEL.

I removed the "quiet splash" from the command so that I could view what was going on during the Linux install.  All is fine until it gets to "Ubiquity Loading..."  upon which  I get a balck screen.

Configuration:
[LIST]
[*]Motherboard: Intel DG965OT
[*]Processor:  Intel 3.4 Dual Core
[*]Memory:  1024MB
[*]SATA 320Gig. Deleted Partions on Disk (Thus a blank disk)  Note htis drive was used as a E Drive of the 
previous Windows system (I did a Quick Format on it before I deleted the partiions)
[*]Twinhan 1034 with CI
[/LIST]

Note:  I also tried putting in a Graphics card to no evail...I dont think it would be the on board graphics; but I gave this a go anyway.

I think it has to do somethign with my Disk Drive?

Please help
Thanks

---

### Post by scary_jeff on 2009-01-25
Are you using TV-out or a VGA-SCART adapter? I had a similar problem to this, it turns out that although the BIOS and first install menu might work through these interfaces, you can't use them to install. My solution was to install using a normal monitor, then set up the TV later.

Hope this is useful.

---

### Post by bryanf2009 on 2009-01-25
I have VGA out.  I am currently using the On Board VGA output to a LCD TV with a VGA input.  Thus - I dont think it is this; correct me if my assumtion is wrong

---

### Post by scary_jeff on 2009-01-25
Since you are using a real VGA connection, I can't be sure this is your problem. The easiest thing to just try before proceeding is to see if install works with an actual computer monitor that the video driver will be able to identify and select the correct resolution for. I suppose it's possible that the driver can't identify your TV properly.
If this works and you can install, you can set up your TV later using modelines or possibly using the configuration panel for whatever graphics driver you will end up using. It's probably best not to explain this any further now, because I might have got this whole thing wrong :)

---

### Post by bryanf2009 on 2009-01-25
I dont have a "Simple" PC Monitor.  

Anyway - When vieing the Installastion as it is going by.  There seems to be some form of Messgae "Invalid Card Number".  It is going by too fast to get the exact message.

It in seems to be failing on the ALSA

Setting up ALSA...
Incalid Card Number

Seems to be an issu with the amixer command during the install.

---

### Post by scary_jeff on 2009-01-25
I didn't have one either, so I borrowed one from work overnight. I'm a bit of a linux noob, so I don't have any other ideas apart from this one. Sorry!

---

### Post by bryanf2009 on 2009-01-25
Thnaks for your help.  Anyway - may be an issue with the ALSA as I am getting and error before I get the "Black Scrren"

---

### Post by bryanf2009 on 2009-01-25
Thanks again - I tried another LCD TV with VGA input and I can continue the install.  Having some problems with Sound and the Patition manager (the STD 20 All for Mythbuntu did not work; I had to use 50_biggest_free method)  keep you posted on the exact setting for this install.

---

