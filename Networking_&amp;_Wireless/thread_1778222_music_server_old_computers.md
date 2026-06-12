---
title: "music server old computers"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by syoung27 on 2011-06-08
Alright so i'm sure it's been talking about millions of times, but im fresh with linux so im hoping to get a good answer to what im thinking.

so to start the question is can i link a laptop to a desktop?  reason is the laptop is decent enough to power a system, over 1ghz, 512ram, 40gb HDD..desktop is like..P3 500mhz 256 ram uhm i believe larger than 40gb.
i also have two externals i currently use for my everyday laptop. 250GB fat32, 1TB NTFS.
i would be willing to give one up for the server obviously to hold music ~90GB and obviously growing. preferably just the 250.

It would mostly be shared with my own laptop which runs Ubuntu11.04/Win7. PS3 also if possible, not necessary.
I'm thinking of putting Debian on the old system, i put it on the laptop so far, runs very nice. but it truely has nothing, and i didn't really select anything on install because i hit the enter button for the check boxes of servers by accident lol.

It would be setup via ethernet to my home modem (bell wireless modem).

I would be willing to use one or the other as the server, i dont have to like the laptop and desktop together. the desktop simply has my 7.1 soundcard so im trying to keep it in the mix. i suppose i could put them together at the modem to ethernet them in.

not sure what else i should describe! hopefully that gives it a good kickstart and some brilliant answers! :)

---

### Post by tgalati4 on 2011-06-08
I'm running freenas (http//freenas.org) on a Pentium 188 MHz (overclocked!) with 256 MB ram.  2 x 500 GB PATA drives ext3, 2 x 1 TB SATA drives (ZFS mirror) with a PCI SATA card.  No video card (that saves 10 watts).  It runs at 38 watts at idle with the disks spun down (set to 20 minutes), 45 watts in use, and 76 watts with all disks spinning.  Configuration is entirely through the web interface.  I recommend the stable version (0.7.2 Sabanda).  Version 0.8 is a complete rewrite and doesn't have all the multimedia stuff working yet.

Serves up my meager 50 GB music collection through DAAP and uPnP.  I can play music on my nokia n800, iTunes, and any linux computer running rhythmbox.  It takes about 15 seconds to load the music share into rhythmbox (~13k tracks).  With a permanent disk mount and importing the music into rhythmbox (local database but the music remains on the server), it loads up instantly, but takes ~1 hour to create the initial database.  I'm running over a 100baseT connection because I couldn't get my gigabit card to work in the old pc.  It was complaining about pci timing issues and I only hard one card to test, so I left it 100baseT.  It's fine for music streaming, but don't expect high def streaming.

To answer your original question, just try "sharing" a folder in your home directory and it will show up on the other machine.  Right-click on a folder and select "sharing options".  You computers need to be on the same network.

I run linux mint xfce on my old PIII, 500 MHz with 768 MB of RAM.  It's slow, but useful for standard web/email stuff.  Max out RAM if you can.

---

### Post by syoung27 on 2011-06-09
so the issue arising into my head right now is that neither of the old systems have usb 2.0, and i'd be running all my music from an external all the time. 
but all the info you gave was quite useful, ill look into the apps and see how well i can at least get all the comps seeing eachother tomorrow:)

---

### Post by syoung27 on 2011-06-09
checking out freenas right now, gonna try and do the thumbdrive route as i've yet to with any install for linux:)

---

### Post by tgalati4 on 2011-06-09
You can buy a USB pci card for cheap and that will give you 5 ports.  One internal (for freenas boot for instance) and 4 external.  If you look on the motherboard, there may be USB pins.  In that case you just need a USB header.  They would be USB 1.0 and slow--OK for bootup because freenas runs entirely in RAM, but not good for music stream.  So a new USB pci card would give you USB 2.0 performance and expandability.

I put a PATA/SATA card in my box so I can use the 1 and 2 TB SATA drives that are coming down in price.

---

### Post by syoung27 on 2011-06-10
anybody heard of vortextbox? im booting it now..

---

### Post by tgalati4 on 2011-06-10
Thanks for the heads up.  Looks interesting:

[http://vortexbox.org/](http://vortexbox.org/)

There was an Ubuntu home server project for a while, but it died.

---

### Post by syoung27 on 2011-06-10
booted, i can see it from my other computers but not showing any music. trying to configure it to read my external HDD. gah command prompt

---

