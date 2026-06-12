---
title: "(another) wireless help :/"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by Plankton on 2005-12-28
I completely  failed to get my wireless card detected on my laptop.
I followed the howto: [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) rule by rule .. 
Everything worked (No errors.) 
Even the drivers used in the howto were the same as mine ...
but it still isn't detected ... i'm hopeless ...

please help me or I will be forced to change back to Windows!

---

### Post by freshy on 2005-12-28
Hi.

I've been trying to get my wireless working as well.  Here's a link to my post.   There is some advice in there that may help you get yours working.  Hope it helps and god luck.

[http://ubuntuforums.org/showthread.php?t=109058](http://ubuntuforums.org/showthread.php?t=109058)

---

### Post by Plankton on 2005-12-28
Yes,

But your wireless card has clearly been detected.

Mine hasn't.

Look: when I lspci i get

0000:00:09.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)


and when I lshw:

  *-network:0 UNCLAIMED
             description: Network controller
             product: Broadcom Corporation
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             resources: iomemory:febfa000-febfbfff irq:11

Totally different story I think.

---

### Post by freshy on 2005-12-28
Yep.  Well, mine still isn't working so I don't know what to do now.  :)

So, you were able to figure out which driver you needed... with the lspci -n command?

Mine is the form 168c:0013

Wish I could be more help but I think I am just as lost as you are.

---

### Post by Plankton on 2005-12-28
Yes I was able.

.. think I have the most comon chipset with problems :mad: Broadcom .. :/

---

### Post by Lambert on 2005-12-28
Yes, broadcom is difficult. some find instant success with ndiswrapper, some play for hours with different drivers.

The biggest 2 problems that I've seen 

1. incorrect driver used. What's on the cd may not work with ndiswrapper. so what driver did you load? At the end I'm posting a link to ndiswrapper wiki. there is an installation page there with instructions on making sure you find the correct driver (doesn't always lead to the correct driver as information comes from users like you and me)

2. Driver is not on harddrive correctly, ndiswrapper recognizes it's installed but it's not able to read the driver files. Did you load driver from cd or put it on the harddrive? If it's on the hard drive there should also be at least a .sys file needed and possibly a .bin file.



There are a lot of posts on ubuntu forums about ndiswrapper and it can be a confusing web to look through to find your answer. Of course maybe the right person will answer this.

I suggest looking at the ndiswrapper wiki for help.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by Plankton on 2005-12-29
[QUOTE=Lambert]Yes, broadcom is difficult. some find instant success with ndiswrapper, some play for hours with different drivers.

The biggest 2 problems that I've seen 

1. incorrect driver used. What's on the cd may not work with ndiswrapper. so what driver did you load? At the end I'm posting a link to ndiswrapper wiki. there is an installation page there with instructions on making sure you find the correct driver (doesn't always lead to the correct driver as information comes from users like you and me)

2. Driver is not on harddrive correctly, ndiswrapper recognizes it's installed but it's not able to read the driver files. Did you load driver from cd or put it on the harddrive? If it's on the hard drive there should also be at least a .sys file needed and possibly a .bin file.



There are a lot of posts on ubuntu forums about ndiswrapper and it can be a confusing web to look through to find your answer. Of course maybe the right person will answer this.

I suggest looking at the ndiswrapper wiki for help.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)[/QUOTE]


Well to answer your questions:

1) I looked up the driver as I was told by looking up the product ID and searching for the correct driver on the list. I have an Asus laptop and I had to download an Acer driver.. no problem said the wiki howto because it can be that your laptop is different from the driver's laptop so I downloaded it onto my HD and used it with Ndiswrapper.

2) I downloaded the driver onto my harddrive. There are 2 files called bcmwl5.inf &  BCMWL564.SYS, there was no .bin file .

maybe this can give you a clear view?

---

### Post by Plankton on 2005-12-29
A little detail:

My wireless network card hasn't been listed in the GUI System > Admin > Networking tool from the beginning ...

---

### Post by Plankton on 2005-12-29
Thanks for your great help and effort guys!

I got my wireless card detected!

The problem was there were 2 drivers installed so I deleted them both and started all over again.

Next step for me is to configure my wireless card so I can get online!

Kind regards,

Plankton

---

