---
title: "Looking for a cheap, decent AGP card"
date: 2009-06-17
forum: Multimedia Software
---

### Post by juelze on 2009-06-17
Hi there,

I'm currently running Ubuntu 8.10 and I have an ATI 9800 Pro.  Compiz fusion bogs my system down and even videos play real slow at times.  I'm thinking of going to an Nvidia card because Jaunty did not like my video card and I ended up going back to a fresh install of Intrepid.  I don't play games or anything on my PC, so I don't need to upgrade anything else on my PC (AMD 2000+ 1.67ghz 1gb ram) but I'd like a better video card for compiz fusion and an overall better linux experience.  Any suggestions for a cheap, decent NVIDIA AGP card that is equal to or better then my 9800 pro?

Any advice is much appreciated!

Thanks,
Ryan

---

### Post by CatKiller on 2009-06-18
The GeForce 6200 might provide a slight improvement (haven't been able to find anything conclusive yet). Should still be available since it's a mainstream budget card. I haven't had any problems with mine. Actually, there may be some GeForce 7 cards that were made AGP, but I haven't had any experience with those.

---

### Post by zenbachry on 2009-06-18
I don't have any suggestion as to what kind of budget card to get since I really only deal with high performance pc parts, but I know that newegg.com has some pretty good deals. Even for lower-end stuff. Just can't go too low lol

---

### Post by steefjeqv on 2009-06-18
Hi,

I suggest you give Jaunty another go.

It has the latest xorg-ati driver which should work out of the box.
I too had a bit of trouble with my R300 card (ATI 9600), but now everything runs fine on Jaunty.
Once you get it running, you can add the following ppa to your sources.list.d :

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Oh, and stay away from fglrx (the AMD closed source graphics driver).

Whatever you do, keep the card as the R300 series will probably the first to support the new open source graphic environment (kernel mode-setting, gallium 3d, etc...).
With a little luck, all of these goodies will be operational for the 10.04 release.

Greetings,
Steven

---

### Post by juelze on 2009-06-18
> **steefjeqv said:**
> Hi,

I suggest you give Jaunty another go.

It has the latest xorg-ati driver which should work out of the box.
I too had a bit of trouble with my R300 card (ATI 9600), but now everything runs fine on Jaunty.
Once you get it running, you can add the following ppa to your sources.list.d :

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Oh, and stay away from fglrx (the AMD closed source graphics driver).

Whatever you do, keep the card as the R300 series will probably the first to support the new open source graphic environment (kernel mode-setting, gallium 3d, etc...).
With a little luck, all of these goodies will be operational for the 10.04 release.

Greetings,
Steven

Thanks for the tip!!!  I actually got my Jaunty CD in the mail a few weeks ago and have it staring at me (I tried Jaunty via the upgrade manager and had no luck).  I'll try this out possibly tonight and see how it works!

-Ryan

---

### Post by juelze on 2009-06-18
> **steefjeqv said:**
> Hi,


Once you get it running, you can add the following ppa to your sources.list.d :

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Oh, and stay away from fglrx (the AMD closed source graphics driver).

Greetings,
Steven

Ok, I tried the fglrx last time and that's when Jaunty went nuts.  So, I'm a Linux n00b, but I'm sick of Windows and have been happy with Ubuntu so far.  All I need to be able to do is surf the web, watch videos, download music and some office work from time to time.  So I haven't really stretched my legs and dove deep into Linux.  Can you break the above information down so I can understand what to do?

I see PPA is Parallel Port Adaptor, are you saying to go into the Synaptics manager and add that URL in there so it can pull those drivers?  Again, I apologize if this is beginner stuff, but I'm slowly learning Linux and so far what I see I like.

Thanks again!

-Ryan

---

### Post by juelze on 2009-06-18
Actually, I think I found some directions on how to do this.  I'll try tonight.  Wish me luck, because if I have an issue I'll be back here bothering you guys!

---

### Post by steefjeqv on 2009-06-18
Let us know if there's any trouble.

I think we're living in different time zones (it's 10 pm over here), so it may take some hours before I can reply. I try to sleep some of the time:D.

Greetings,
Steven

---

### Post by Tamara Perera on 2009-06-18
If you really looking for A cheap AGP card then you should not think about the quality because you would not able to buy any brad AGP card like Nvidea within a cheap cost. However I suggest you to buy Asrock motherboard to get a 384MB Built in agp card at a cheap rate.

---

### Post by juelze on 2009-06-19
> **steefjeqv said:**
> Let us know if there's any trouble.

I think we're living in different time zones (it's 10 pm over here), so it may take some hours before I can reply. I try to sleep some of the time:D.

Greetings,
Steven

Ok, I think I got it figured out.  I tried messing with it last night, but the wife and I went out for our anniversary and I had too many India Pale Ales.  :-)  Anyway, all I needed to do with that URL you posted was to go into System>Admin>Software sources then go to the 3rd party tab and paste these 2 PPA URLS:

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main

Correct???  

All and all everything seems to run great in Jaunty now.  I can do a lot of the eye candy effects without my system acting sluggish.  Most notably, Firefox could not scroll smoothly with the effects turned on with Intrepid, and with Jaunty it's silky smooth.  Man, I'm so glad I ditched XP.  It's like a full time job running Windows because you're battling against all sorts of junk (malware, spyware, viruses, system crashes, etc) and with Ubuntu, it just works!!!

Thanks again everyone!

Cheers,
Ryan

---

### Post by juelze on 2009-06-19
Ok, kept getting an error (didn't write it down) but I figured it out.  I had to add the PPA key to the software sources authentication tab.  So far everything is rockin!

---

### Post by steefjeqv on 2009-06-19
Glad to hear everything works fine.

> Ok, I think I got it figured out. I tried messing with it last night, but the wife and I went out for our anniversary and I had too many India Pale Ales.

Pale Ale, now that's something I haven't heard of for a while.
A lot of pubs in Belgium don't serve this anymore. Fine beer though.

Greetings,
Steven

---

### Post by Therion on 2009-06-19
> **steefjeqv said:**
> A lot of pubs in Belgium don't serve this anymore. Fine beer though.
You have **Orval**, quit complaining.







/Please send Orval, Palm...  Mainly Orval.

---

### Post by khelben1979 on 2009-06-19
> **steefjeqv said:**
> Oh, and stay away from fglrx (the AMD closed source graphics driver).

Whatever you do, keep the card as the R300 series will probably the first to support the new open source graphic environment (kernel mode-setting, gallium 3d, etc...).
With a little luck, all of these goodies will be operational for the 10.04 release.

Greetings,
Steven

My Radeon9800XT worked fine with using fglrx with Debian when I tried it a few years ago. I was able to play Unreal Tournament 2003, Doom 3 and some other games with pretty good frame rates.

If the ATi driver works bad with Ubuntu, maybe he should switch to another distribution instead?

Maybe I should mention that I compiled my own kernel (2.6.5) and made my own build of the graphics driver they provided, though. This should work with Ubuntu too, but it's never intended for less experienced Linux users to do so. :-k

---

