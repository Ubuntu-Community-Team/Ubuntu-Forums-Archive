---
title: "Network card prevents me from booting -HELP"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by GuitarHero on 2006-06-30
[http://ubuntuforums.org/showthread.php?t=205637&page=3](http://ubuntuforums.org/showthread.php?t=205637&page=3)
That thread was mine when i thought the problem was grub.  Ive been trying to fix this a for a while now.  I had ubuntu installed on one computer and moved the hdd to a different one.  Now i cant boot into ubuntu.  I was able to the first time, but when i booted again it would stop booting after checking all file systems, which is where it detects and configures networkcards.  I wasnt sure if it was the file system stopping the boot or the networking, but after testing it with and without the network card, and reinstalling 3 times, ive narrowed it to the network card.

I can boot into ubuntu with the network card out,
I can boot into ubuntu with the network card in while it is not configured.
Once I configure and enable the card, it stops after checking all file systems at boot.  I dont know why but its very annoying.  My wireless network card is a Linksys wireless G 54mbps 2.4ghz card.  I am running Ubuntu Dapper Drake 32bit vesion on an AMD Athlong X2, ATI Radeon x1900xt(its using the vesa drivers, they're not great but they work until i can get fglrx), 2gb ram, 20gig HDD computer.

Any other info you need i will gladly provide.  I really want to use ubuntu, but this problem is driving me crazy.  These forums have helped me in the past and know i can get it working somehow.

---

### Post by GuitarHero on 2006-07-01
to the request of someone on #ubuntu, here is what iwconfig gives me with the live cd.  I also wanted to find the part of sudo cat /proc/modules that related to my network card but i couldnt figure out which one it was. none of them said wireless or anything.

ra0
RT61 Wireless ESSID:""
Mode: Auto   Channel:0
RTS thr=0 B   Fragment thr=0 B
Link Quality:0    Signal Level:0   Noise Level:113
Rx Invalid nwid:0    Rx invalid crypt:0 Rxinvalid



That was without configuring and enabling it.

---

### Post by GuitarHero on 2006-07-01
Would NDISwrapper fix my problems?

---

### Post by neveceral on 2006-07-01
[QUOTE=GuitarHero]Would NDISwrapper fix my problems?[/QUOTE]
no, i tryed it, ndiswrapper didn't work with rt61.inf for me
but i have the same problem look [here]("http://www.ubuntuforums.org/showthread.php?t=132980&page=10&highlight=rt61")

---

### Post by confused57 on 2006-07-01
I thought I'd check to see what progress you'd made getting your wireless working, seems you're not alone...probably won't help, but found this:

[http://www.ubuntuforums.org/showthread.php?t=190967](http://www.ubuntuforums.org/showthread.php?t=190967)

At least I bumped your thread...

---

### Post by GuitarHero on 2006-07-01
AGH nothing I do helps........ maybe ill just have to wait for edgy or find another distro i like(havnt found one except ubuntu that was appealing to me....)

---

### Post by GuitarHero on 2006-07-02
How would I even try ndiswrapper without internet?  How do I install it without internet......
Will this allow me to use the drivers that came with my card?

---

### Post by neveceral on 2006-07-02
[QUOTE=GuitarHero]Will this allow me to use the drivers that came with my card?[/QUOTE]
no, rt61.inf is not working with ndiswrapper [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L)
i am searching for  solution too, look here [http://www.ubuntuforums.org/showthread.php?t=132980&page=10&highlight=rt61](http://www.ubuntuforums.org/showthread.php?t=132980&page=10&highlight=rt61)

---

### Post by mips on 2006-07-02
Tried playing around with APCI & APIC as well as bios settings maybe ?

---

### Post by GuitarHero on 2006-07-02
Sorry I dont know what rt61.inf is, so thats why i asked.  Ive looked through BIOS and messed around with no success.  What's APCI and APIC

And neveceral, you are doing this on breezy right?  I wonder if the same fix would work for me too or not.

---

### Post by mips on 2006-07-02
Apologies, ACPI
When you boot you can use the option acpi=off or add it to grub. There is also a great search function here if you need more examples.

[http://www.acpi.info/](http://www.acpi.info/)

---

### Post by neveceral on 2006-07-02
[QUOTE=GuitarHero]Sorry I dont know what rt61.inf is, so thats why i asked.  [/QUOTE]
rt61.inf is windows driver for wifi card with chipset ralink rt61
	
[QUOTE=GuitarHero]And neveceral, you are doing this on breezy right?[/QUOTE]
no i am using Dapper Drake 6.06

---

### Post by GuitarHero on 2006-07-02
Ah that topic was in the breezy forum so i assumed.  Well I hope we find a solution.  I love ubuntu, when it works.

---

### Post by GuitarHero on 2006-07-02
Ah that topic was in the breezy forum so i assumed.  Well I hope we find a solution.  I love ubuntu, when it works.

---

### Post by GuitarHero on 2006-07-03
is there a way to get it to boot without configuring network devices?  If i could boot into ubuntu with the card in maybe i could ge tthe right drivers working or something.....

---

### Post by neveceral on 2006-07-03
yes, there is a way to boot without network devices. Install ubuntu and then don't allow network :-)), but i have right drivers and it isn't even working.
Special thread about booting problems with wifi cards is [here]("http://www.ubuntuforums.org/showthread.php?t=182460&highlight=rt61")
Daniel

---

### Post by GuitarHero on 2006-07-03
bump

---

### Post by GuitarHero on 2006-07-04
someone.....

---

### Post by GuitarHero on 2006-07-04
guess i should just try another distro

---

### Post by mips on 2006-07-05
[QUOTE=GuitarHero]guess i should just try another distro[/QUOTE]

Or maybe get a mac. Linux is not the solution for everyone, requires a bit of patience sometimes.

Did you have a look into ACPI and booting with it off ???

To disable network at bootup look at these (By the way the search function on this forum works quite well, I did a search for "Disable network during bootup" got the following):

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=175763](http://ubuntuforums.org/showthread.php?t=175763)

---

### Post by PriceChild on 2006-07-05
[quote=GuitarHero]I had ubuntu installed on one computer and moved the hdd to a different one.[/quote]
 
By this i'm guessing you mean that you just swapped the harddrive into different hardware and booted it again hoping all would still work.
 
I don't pretend to be an expert... but this practice here sounds EXTREMELY dodgy if you didn't do a reinstall.

---

### Post by GuitarHero on 2006-07-05
No I did it and it worked, but then i rebooted and i didnt, before that all my hardware was detected and installed.  Plus ive reinstalled like 4 times since.

---

### Post by GuitarHero on 2006-07-06
bump

---

### Post by GuitarHero on 2006-07-07
Well SUSE 10.1 didnt work either.  Doesnt anyone know how to find some drivers for this or something?

---

