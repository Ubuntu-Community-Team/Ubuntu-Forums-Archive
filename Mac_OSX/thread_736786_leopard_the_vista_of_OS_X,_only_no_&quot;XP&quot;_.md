---
title: "leopard the vista of OS X, only no &quot;XP&quot; to go back to"
date: 2008-03-27
forum: Mac OSX
---

### Post by darksidedude on 2008-03-27
so here I was, happy with my new Macbook, that came preinstalled with Leopard, I was excited as any new mac owner would be, it came with the standard 80gb hard drive, untill I looked at my HDD space, only about 55gb of space was free!!,

the meaning of this post is simmply this, Leopard in terms of HDD space alone, is like vista, a lot of fancy colors and windows but the space usage doesnt justify the space.

then i got the brilliant idea to just "downgrade" to Tiger, however I look and look at apple to find, Tiger is dead to them, cant find it anywhere!!

this is an intel macbook 3,1 if there is anyway to get tiger LEGALY, on this macbook, outside of EBAY, because most of those people dont even know the difference between a PPC and intel, if you have any ideas let me know, thanks much

---

### Post by schauerlich on 2008-03-27
Your best option would be to reinstall Leopard with the disks that came with your Macbook, and go into the installation options and take out all the printer drivers and other stuff that you probably don't need. That can reduce the size of your installation dramatically. Mine was only about 8-9GB, down from the 14GB it wanted initally. However, I find it hard to believe that just Leopard is really taking up 25GB on your hard drive... Even with everything that I have installed, all of my files, music, videos, and the OS itself, my OS X partition only has 29GB used. Maybe something else is wrong?

---

### Post by tubasoldier on 2008-03-27
If you have installed the iLife suite it will take up quite a bit. GarageBand and iDVD have about 2GB each of files. If you don't use those programs then there is no reason to have those in there.

---

### Post by marckie on 2008-03-27
> **tubasoldier said:**
> If you have installed the iLife suite it will take up quite a bit. GarageBand and iDVD have about 2GB each of files. If you don't use those programs then there is no reason to have those in there.

Yeah I agree... Check on those...

---

### Post by jrharvey on 2008-03-27
I would reinstall it using the leopard disk. If i remember right, i got my powerbook down to 5G

---

### Post by scramasax on 2008-03-27
> **marckie said:**
> Yeah I agree... Check on those...

And Garageband's *loops*, as well.  Those take up a lot of space.

The other thing is that OS X goes out with a lot of language packs, but you don't have to keep the languages you don't use.

The OP might remove any languages he doesn't speak -- for example, with Monolingual:

[http://monolingual.sourceforge.net/](http://monolingual.sourceforge.net/)

But those using Monolingual should check the Preferences and the settings and not remove anything with the *other* two tabs "Input menu" and "Architectures" unless they know what they're doing.  (Current Mac binaries are fat binaries --

[http://en.wikipedia.org/wiki/Fat_binary](http://en.wikipedia.org/wiki/Fat_binary)

-- so that the software can run on both PPC and Intel.  You can strip out the architecture you don't need, but if you remove the PPC architecture from system areas on Intel Macs, you'll break [Rosetta](http://www.apple.com/rosetta/).)

darksidedude:

Either use a tool like Monolingual or gradually work your way around each application bundle removing the languages you don't need manually.  Right-click on each [COLOR="SeaGreen"].app[/COLOR] "file" (it's actually a bundle not a file, although it appears like one in the file manager) and select "Get Info".  You see the section labelled languages?

[[IMG]http://img237.imageshack.us/img237/3756/itunesbm0.th.png[/IMG]](http://img237.imageshack.us/my.php?image=itunesbm0.png)

Highlight any you don't use and click the minus button.  You will get a warning, but language packs it *is* safe to remove, and that's what that control is for.  Watch the size of something like iTunes shrink dramatically.

This is a big reason for the bulk.  Apple has to cover both processor-architectures and many languages besides an awful lot of printers with a standardized product.  It's not a huge issue with the size of current hard drives, and users can always tailor that standardized product to their particular needs by stripping out the bits that don't apply to them personally.

---

### Post by scramasax on 2008-03-27
> **darksidedude said:**
> this is an intel macbook 3,1 if there is anyway to get tiger LEGALY, on this macbook, outside of EBAY, because most of those people dont even know the difference between a PPC and intel, if you have any ideas let me know, thanks much

Don't even bother trying.  You've no guarantee that Tiger will even run on a machine it didn't ship on.  There may well be hardware in that machine that Apple wasn't using when it was distributing Tiger.

---

### Post by darksidedude on 2008-03-27
oh and, i not a big fan of Leopard, i should have speicified but, I dont really like it, at my school we have 2 IMACS that have tiger, Tiger is faster and smother than leopard. the ram is the same and the ghz difference is minisule in the end anyway. 

this macbook, back when tiger still the latest, did indeed run on this machine, i looked it up, however I simply cant find Tiger

---

### Post by cprofitt on 2008-03-27
> **darksidedude said:**
> this is an intel macbook 3,1 if there is anyway to get tiger LEGALY, on this macbook, outside of EBAY, because most of those people dont even know the difference between a PPC and intel, if you have any ideas let me know, thanks much

Apple, unlike Microsoft, does not allow for downgrading of their products; in fact you might not be able to due to driver issues, etc.

Good luck.

---

### Post by Saint Angeles on 2008-03-27
check out ubuntu linux for best results.

---

### Post by dmitrijledkov on 2008-03-27
I saved in addition about 4 GB by deleting additional language support from Leopard basic. And from each application (browse inside applications by right clicking + show contents and delete lproj files i think with language names. Leave en though for english).

---

### Post by cprofitt on 2008-03-27
> **jrharvey said:**
> I would reinstall it using the leopard disk. If i remember right, i got my powerbook down to 5G

I never would have thought Apple would have been guilty of loading tons of carp on their machines... I thought that was reserved for Dell, HP and other Windows vendors and all the free AOL type carp.

---

### Post by darksidedude on 2008-03-27
I did try to install ubuntu accually but the instructions are hazy at best, because boot camp only suports 2 partitions, and how can I have a swap when the 2 partition limit is filled, HFS+ and ext3, also when ubuntu installs grub becomes the boot loader, and cant boot OS X,( something about a MBR not suposed to be there......

so here I am, running Vista, on 1gb of ram, supriseing its snappy, could be the dual core processor though? idk

---

### Post by scramasax on 2008-03-28
> **PrivateVoid said:**
> I never would have thought Apple would have been guilty of loading tons of carp on their machines... I thought that was reserved for Dell, HP and other Windows vendors and all the free AOL type carp.

They don't.

The only "trial" software on there is Microsoft Office and iWork.  And removing either is as easy as dragging them to the Trash, the architecture of the machine being as it is.  This is the advantage of having application bundles -- and no Registry.

Supplying people with machines that have the languages and the printer drivers they need is not "loading tons of crap".  It's necessary for the customers.

My last Sony Vaio took hours to clean -- literally.  And that's one of the reasons why I will never buy a machine from an OEM that distributes your company's software ever again.  That and their unethical and illegal activities.

I'm told HP are currently the worst offenders for installing unwanted "trial software".  Dell, contrary to what you think, will supply a (relatively) clean install now, but you have to ask for it.

Coming here with a little logo with "Linux" on and "Debian User" in the top left.  Do you really think that fools anyone? Do you really think we don't know on whose behalf you're trying to stir up trouble for competitors here?  I don't think even a basically unpleasant person could fool himself into thinking that software necessary for customers, such as printer drivers, and crapware were "the same thing" just for the sake of using that as an excuse to vent nastinesss.  However, someone acting on behalf of a certain large company might hope to fool careless readers into thinking they are.

---

### Post by handy on 2008-03-29
> **darksidedude said:**
> I did try to install ubuntu accually but the instructions are hazy at best, because boot camp only suports 2 partitions, and how can I have a swap when the 2 partition limit is filled, HFS+ and ext3, also when ubuntu installs grub becomes the boot loader, and cant boot OS X,( something about a MBR not suposed to be there......

so here I am, running Vista, on 1gb of ram, supriseing its snappy, could be the dual core processor though? idk

Gutsy installed on my Alu' iMac 24" quite easily, thought it is probably the easiest of all of the Mactel's to install to.  There is very good help available in the Intel Mac sub-forum, also the Wiki, & on the internet in general.

I'll post a few links below which you (or someone) may find helpful:

***_[http://www.rickycampbell.com/2008/01/24/the-intel-mac-partitioning-system-efi-and-gpt/](http://www.rickycampbell.com/2008/01/24/the-intel-mac-partitioning-system-efi-and-gpt/)_***

***_[http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/](http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/)_*** 

Scroll down through this list of titles in the Ubuntu Wiki to find the one that refers to your machine, I suggest at least skimming the 2 links above as they give great foundation knowledge for what those of us who have come from the world of the Windows desktop/notebook find as a new strangeness living in the Mactel hardware:

***_[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mac&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mac&titlesearch=Titles)_***

---

### Post by the.dark.lord on 2008-03-30
> **darksidedude said:**
> I did try to install ubuntu accually but the instructions are hazy at best, because boot camp only suports 2 partitions, and how can I have a swap when the 2 partition limit is filled, HFS+ and ext3, also when ubuntu installs grub becomes the boot loader, and cant boot OS X,( something about a MBR not suposed to be there......

so here I am, running Vista, on 1gb of ram, supriseing its snappy, could be the dual core processor though? idk

I chucked OS X Tiger on my iMac for the favor of Ubuntu, I don't repent it.

---

### Post by handy on 2008-03-30
> **the.dark.lord said:**
> I chucked OS X Tiger on my iMac for the favor of Ubuntu, I don't repent it.

Many find it useful to at least keep a small OS X partition for firmware updates.

---

