---
title: "Access free to air channels using ubuntu, a sky dish and as yet brought tv card"
date: 2011-01-23
forum: Multimedia Software
---

### Post by gredawarha on 2011-01-23
Hello all

I have moved into a house with an existing Sky digital dish.  The previous owner had a multi room set up so there is a spare cable in the room where my Ubuntu box is located.  

I have no intention of fitting a new sky box and getting a multi room subscription but was wondering whether anyone can advise me whether I would be able to view free to air channels on the Ubuntu machine using a TV card?

Any help would be much appreciated.

---

### Post by armyofgayunicorns on 2011-01-25
yes you can, but satellite tuner cards (DVB-S or DVB-S2 cards) are a bit of a minefield. There's a thread here:

[http://ubuntuforums.org/showthread.php?t=921377](http://ubuntuforums.org/showthread.php?t=921377)

which mentions a few cards that people have had little or no trouble setting up. get one of these ones then get mythTV or add all mythbuntu packages, there's comprehensive setup guides for mythTV and i've had it working with a DVB-T (digital terrestrial) card before with very little configuration needed.

However, i now have a satellite card with the DM1105 chipset which i have had no success at all in getting to work.

 some of the cheapest cards you'll find on ebay which come from china have the DM1105 chipset on them, so avoid them, they work fine in windows, just put it in your pci slot and run the install disk, but i've read and attempted to follow many complicated sets of instructions for how to get this card to work with linux and got nowhere. 

It does appear some people have succeeded in getting it to work, so if you do end up with one of these cards and get it to work, please let me know how you did it. it's an increasingly common chipset, however, so i'd expect it's only a matter of time before simple support is added to ubuntu.

What you need to keep in mind though, is that free-to-air and freesat are not the same thing. you will get all the free-to-air channels, but this does not mean that you'll get all the channels that you'll get with a freesat box, or an old sky box with a freesat viewing card in it.

to get all these channels is very difficult, and very difficult to find information on, as the processes that would allow you to receive them through a tuner card are the same processes that would allow you to illegally decrypt channels you should be paying for. because of this, most forums won't allow discussion of these topics, even when all you want to do is receive channels through your pc that you're already paying a subscription fee for.

if you want the full range of freesat channels and the option to add extra subscription channels, I'd recommend the one off payment for a freesat box. Your dish is already set up and pointed at the right satellite, so all you need to do is connect it all up, switch it on and scan for channels, and there's plenty websites that have directories for tuning in the channels that won't necessarily be found automatically by your box.

it doesn't have to be a freesat box, if you find a second hand sky box going cheap online, then you can get that and just buy a freesat viewing card.

---

### Post by matthewbpt on 2011-01-25
For the most up to date and comprehensive list of compatible devices go here  [http://www.linuxtv.org/wiki/index.php/Hardware_Device_Information](http://www.linuxtv.org/wiki/index.php/Hardware_Device_Information) . This page is particularly relevant to you [http://www.linuxtv.org/wiki/index.php/DVB-S2_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-S2_USB_Devices) . I use a DVB-T usb card with vlc to watch terrestrial freeview tv.

---

