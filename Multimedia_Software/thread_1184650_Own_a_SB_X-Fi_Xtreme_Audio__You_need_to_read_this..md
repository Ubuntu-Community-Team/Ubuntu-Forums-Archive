---
title: "Own a SB X-Fi Xtreme Audio?  You need to read this."
date: 2009-06-11
forum: Multimedia Software
---

### Post by AoSteve on 2009-06-11
Well I've been working with this thing for two days straight on Ubuntu 9.04...  NOTHING..  I've followed every single "how-to" or idea thread/post.   Nothing works.  

I'm the kind of guy who likes to find out the true form of things and this started getting my nerves rattled.   So I went in search of finding something that would work.

I found my problem after about two hours of reading and searching.   There's quite a few models of the X-Fi line of Creatives latest addition to the sound blaster line.  Being a Creative user for over 15 years, I was suprised to find this.

Come to find out, the entire line of X-fi branded cards, aren't powered by the new EMU20k chip that powers the Titanium cards.

This is just one link to the MANY that you will find out there about this card.

[Disgruntled SB Purchaser on epinions.com]("http://www.epinions.com/review/Creative_Technology_PCIE_SB_X_Fi_Xtreme_Audio_Hard_Drive/content_469904952964")

I tore into it more and found out that this is true.  To test the theory, I tried a set of "X-Fi Titanium" drivers for my card in windows vista.   The thing about the creative cards in the past, the bigger differences were negligable and you could actually install the "good software" with the cheap cards.    Like, the Live! Value platform could use the same drivers, software, and abilities that the high end "X-Gamer" and "Platinum" owners could because the card was physically, the same.    I had a friend test this with his X-Fi Xtreme Gamer card, and he was able to install the Titanium pack of software and the drivers.   So, the fact remained the same, that you could, in effect, use the high end drivers.

Well, it was my turn and halfway through the process of installation, blue screen...  Hmm  odd...    So, I cleaned the system of the original drivers and tried it again, it installed this time and I thought, "Alright, sweet!"...    Reboot to windows resulted in no sound output and a driver error saying, "This device isn't working properly :  The driver installed may be incorrect or corrupt."    Nice..   If I could find any audigy2se drivers, I'd try them.

But aside from this point, I'm going to attempt to get this card working under ubuntu later today.  I'm gonna try some different driver sets as a couple posts I've found on the internet led me to find that people have actually got the PCI version of the X-Fi Xtreme Audio to work with the Audigy 2 drivers under different distro's of linux.   I may be out of luck, seeing as mine is PCI-e.   We'll see though.   

Either way, I'm done with Creative now.  This really upsets me as I've always used their cards and knew them to be one of the few companies that didn't cheat it's customers.   My sound card came with my motherboard, so I don't feel so "jipped", but still the fact remains.   If I wanted a $20 card with all software driven effects, I'd use an onboard sound system.   I'm saving up for an Xonar.

I'll update the current sound situation with Ubuntu, but I think the situation is quite grim here.   At least other brands of cards work with Ubuntu :(.

---

### Post by markbuntu on 2009-06-11
Until very recently creative was actively hostile to the linux community. Every driver in linux was the result of painful reverse engineering with absolutely no help from creative. Recently creative tried to write a linux drivers for the x-fi cards but it was a disaster. Since then they released some code and have been providing some help to the alsa driver maintainer to get a working x-fi driver. This work has been completed and a working alsa x-fi driver will be included in kernel 2.6.31 which we expect to see in a few months.

---

### Post by AoSteve on 2009-06-12
It's not the fact that they haven't been the nicest to the Linux guys.. but more the fact that they've shipped X-Fi cards that cost nearly $100 when really it's only a small portion of the software backing for the Titanium and it's running from a 5 year old design...   

I'll stick with another brand from now on as it's the only time I've ever been so frustrated with them.  They used to be a decent company considering the competition and never remarked old hardware for new use.  It just turns my lspci the wrong way in sort.   It's almost as bad as nVidia and their last couple years of remarking chips for new models by adding near pointless add-ons to the older cards and selling them for hundreds more.   

As for the other point, I've tried a couple different driver sets for the audigy and none work what so ever.  Not even a blip from my speakers.  :(   I'm guessing that the audigy drivers just won't understand the PCI-e control and will not work with this setup.  I'm hoping someone out there has a working X-Fi Audio like I do under linux.   Some reason I doubt, even with this soon to be released kernal with the working alsa X-Fi driver will work with this card.    

Either way, I'm saving up for an Xonar Dx or Dx2.   I won't buy a creative card again until I know that the line is a completely new system instead of a remarked X-fi.  :\

---

### Post by Shub902 on 2009-06-12
I have an "x-fi" extreme audio installed on my hp.  I was running XP for awhile, but I just installed Jaunty a few days ago, without removing my sound card.  The card still works in Ubuntu(I have sound) but I have no master volume.

---

### Post by AoSteve on 2009-06-12
> **Shub902 said:**
> I have an "x-fi" extreme audio installed on my hp.  I was running XP for awhile, but I just installed Jaunty a few days ago, without removing my sound card.  The card still works in Ubuntu(I have sound) but I have no master volume.

What drivers is it using?   I must know!   I just want basic sound, even a fart noise coming from the speakers would be a start!

---

### Post by Shub902 on 2009-06-13
> **AoSteve said:**
> What drivers is it using?   I must know!   I just want basic sound, even a fart noise coming from the speakers would be a start!

Haha.  I'm really quite new to Linux.  Where would I find the drivers?

Really wish I had the creative console to tweak the sound, but I'm just happy it works.
Also, I still can't figure out how to get the master volume(the one that comes with 9.04 and sits in the top bar) to control anything..

---

### Post by AbeJarano on 2010-12-25
Mine worked in 9.04 without any special changes.  In 10.10 no sound.

---

