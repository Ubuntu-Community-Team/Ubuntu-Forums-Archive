---
title: "Just installed mythbuntu.  Need help setting it up.  Any takers?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by djrobthaman on 2009-03-18
Hi all,

I finally got all my parts for my little dvr setup and seem to be having a couple problems with mythbuntu.  If anybody knows how to fix them, I'd be forever grateful.

1.  I bought [JetWay JNC93-230W-LF Intel Atom 230 Intel 945GC Mini ITX Motherboard/CPU Combo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153136").  It says that the video chipset is Intel GMA 950 and there is an on-board tv-out.  Currently I have the default open source drivers that come with the install cd installed.  But this means that tv out is disabled.  What can I do to enable tv out?

2.  Also got [Hauppauge WinTV-Nova-S-Plus]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116011").  Mythbuntu lists this card in its video capture devices, but I still can't watch anything plugged in to it.  I went into another settings section (video connections or something like that) and when I try to scan for channels from any of the sources on the card it can't find anything.  What should I do?

3.  Somebody told me once that I could watch video files on shared hard drives over the network.  How do I set this up?

4.  I made a huge mistake.  You're all allowed to point and laugh now when I say that when I buy computer parts I must always make sure it can fit inside the case.  The hauppauge card I bought does not fit in the ITX case I bought.  Yay.  What I'm thinking of doing is putting it in my desktop and running my desktop as a mythtv server and the machine I just set up as a client.  With that in mind:

a)  Anyone know what settings I should use so that mythtv would work with the remote that comes with the hauppauge?

b)  Would the remote work for the dvr even though the tv tuner card (and therefore the remote receiver) is installed in the server and not the dvr itself?

c)  Can I watch dvds inside the dvd-rom in the dvr setup or, because it would be only a client, do the dvds have to be put in the machine that acts as the server (this sounds like a dumb question).

5.  This one has nothing to do with mythbuntu at all.  Just a large annoyance.  I don't want to have to keep a keyboard connected to this thing because I just want it to be a dvr.  Whenever I turn on the machine it stops right before reaching grub and says something like "Press F1 to continue or DEL to go to setup" and it won't budge until I press one.  Does anyone know if I change something in the BIOS or whatnot whether I can stop it from doing this?

Thanks so much for any help you can give me.  I'm sure I'll end up having tonnes more questions, but this is what I can come up with off the top of my head.

---

### Post by djrobthaman on 2009-03-19
So far I've managed to fix my problem in #5.  So now,, no keyboard required.  Yay.  Still stumped on the rest of them though.

And, of course, I've got a new one.  I went into synaptic and allowed it to perform all updates.  Since then, I haven't been able to connect to the internet.  I can't even connect to the router.  But if I plug the ethernet cable into my desktop it works just fine, so I know it has to be something somewhere in the update/upgrade process.  Any suggestions on how to fix that one?

Thanks

---

### Post by wolfen69 on 2009-03-19
are you running mythbuntu 8.10? [here]("http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf") is the installation manual.

perhaps you could just ask 1 question at a time. it is a lot to ask for help with 6 different problems at once.

also, how much research did you do before buying this hardware?

---

### Post by peterthewolf on 2009-03-30
Personally I would try setting up mythtv from a standard ubuntu install.

---

### Post by djrobthaman on 2009-05-05
Peterthewolf, I'm trying your suggestion and installed jaunty on there the other day.  My video output is great now that I found out about the xorg-edgers repository.

Now I've moved onto trying to watch cable.  So far I've put the cable card in my pc (since as I said earlier it can't fit in the dvr case... silly me).  The mythtv client I have running on my pc detects the card (a hauppauge nova-s, proper name and link is in the firt post), but I can't get the mythtv front end on the pc to play cable.  It goes to a black screen and freezes.

I don't know if this means bad things for trying to stream the cable from my pc to the client on the dvr box but I figure if I can't play the cable on my pc i'm definitely going to have a problem otherwise.  The way I have it set up right now is that my cable goes into a motorola cable box and then into the composite connector on my cable card.  Do you know what settings will let me watch the cable?

Thanks

---

