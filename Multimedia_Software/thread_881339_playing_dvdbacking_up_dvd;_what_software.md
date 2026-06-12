---
title: "playing dvd/backing up dvd; what software?"
date: 2008-08-05
forum: Multimedia Software
---

### Post by egalvan on 2008-08-05
I use DVD-FabHDDecrypter under windows to store my DVDs.

What is an equivalent product(s) for Ubuntu?

Ubuntu 8.04.01
2.8mHz cpu
2gB ram
lots and lots of storage


Also, i just picked up a used HP Multimedia Center, dual-core, 2gb, nvidia, dual-hd's, tv tuner, etc

Will MythUbuntu do this out-of the box?

Thanks
ErnestG:popcorn:

---

### Post by Vivaldi Gloria on 2008-08-07
> **egalvan said:**
> I use DVD-FabHDDecrypter under windows to store my DVDs. 

I actually use DVDFab under ubuntu with wine. No programs manages to get rid of all the encryption out there as good as DVDFab.

To rip them use dvd::rip. It's available in synaptic. I like it because it can rip multi-threaded.

---

### Post by egalvan on 2008-08-27
Any other thoughts/suggestions out there?

WordPerfect,
moving my DVD's to my server,
and Microsoft "Streets & Trips" are the last remaining vestiges of Microsoft on my machines, other than researching solutions for customer's problems.

ErnestG

:popcorn:

---

### Post by mc4man on 2008-08-27
For non structured protected titles (or those with minor sp your willing to fix if needed) you could use vobcopy. Rips to a VIDEO_TS folder inside of a volume name folder (usually title name.
Good command is > vobcopy -v -m -F 16 (assumes media mounted at /media/cdrom0
For other mount points append command, ex.
> vobcopy -v -m -F 16 /media/cdrom1

For many sp. titles you can also use k9copy. (will fix sp.) If you set the target sectors above disk size it will just rip, no transcoding. Sometimes though you may need to alter what your ripping ie. orig. menus, no orig. menus, movie only ect.
Defaults to creating an .iso, can be changed to folder (VIDEO_TS

As mentioned for some titles DVDFab.... is the only way 

To use vobcopy on sp. titles you need to compile yourself (very easy) and modify the read tries in the source. (defaults at 10 - too time consuming especially when the idea is to skip unreadable sectors

edit; for sp. titles and k9 if the dvd loads but the rip fails the first place to look is in the various titles/title sets for obviously bogus stuff.
A good tipoff is large size and short running time. Another suspect thing would be a series of titles the exact same size - a further test of those would be to open in vlc and see if you can play them. A little bit of experimenting with titles/title sets, menus usually proves fruitful.
And there's always dvdfab....

---

