---
title: "8x AGP card in a 2x slot?"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by voided3 on 2006-11-05
Hello. I am considering putting a nvidia MX440 AGP card with twin VGA outs in an old comp of mine that supports AGP 2x max, and the card goes up to 8x. Is that acceptable with that card, and will it pose any problems down the road from a harware or software standpoint? Thanks!

P.S.- if power is a concern, it has a 250 watt power supply, and I have a 300 watt sitting around I could put in

---

### Post by tommcd on 2006-11-06
The only problem you will have is that the AGP card will run at 2X, not 8X, because that is what your motherboard supports. It's like running DDR-400 RAM in a PC that only supports DDR-266 RAM (like I do in an old E-machines PC I have). It will work, but at the slower RAM speed.

---

### Post by zgornel on 2006-11-06
> **voided3 said:**
> Hello. I am considering putting a nvidia MX440 AGP card with twin VGA outs in an old comp of mine that supports AGP 2x max, and the card goes up to 8x. Is that acceptable with that card, and will it pose any problems down the road from a harware or software standpoint? Thanks!

P.S.- if power is a concern, it has a 250 watt power supply, and I have a 300 watt sitting around I could put in
Watch out! AGP 2x slots use different voltages that 4x/8x ones. See in your motherboard manual what voltage is used and if the video card supports it. You might end up with fried hardware and we don't want that , do we ?
Check this out [http://www.ertyu.org/steven_nikkel/agpcompatibility.html](http://www.ertyu.org/steven_nikkel/agpcompatibility.html)

---

### Post by voided3 on 2006-11-06
Thanks for the link! By the look of it, if it doesn't physically fit in the slot it won't work since they are "keyed", but I believe  the card does have the appropriate notch. I suppose the question would be though is if it's backwards compatible with the different voltage. The nvidia site didn't say anything about it, so does anyone know where I can find a more detailed spec sheet for the MX440? If this card doesn't work out, I still have a TNT 2 or a TNT pro (forgot which, but it was in the comp when I got it) but the MX440 is the better card. Thanks!

---

### Post by zgornel on 2006-11-07
Nvidia produces video chips and rarely videocards (I gues only engineering samples) so you won't find AGP mechanical/electrical specifications on their site. Some AGP slots are not keyed (depending on the motherboard manufacturer, especially no-name boards) and you can put a agp 4x/8x in a 2x slot and burn the thing. Take a look at your motherboard manual (online manual or not) and see if the AGP slot supports 4x/8x cards.

---

### Post by voided3 on 2006-11-07
Hello again. I have the manual for the board, it's an Epox MVP3C baby AT super socket 7 board that was made before 4x/8x came out, so it wasn't designed with that in mind, plus it's keyed. However, I don't have the video card on hand (I know it's a GeForce4 MX440), but it doesn't have any obvious builder name association on it like ASUS or anything. What gave me the initial idea to put the card in was my Radeon 9250 in my current comp said it supports 2x, 4x, and 8x so I  thought that since the MX440 also is an older AGP card that it might support the higher voltage at lower speed. It really is more of a question as to what the card can support since the board is only 1x or 2x. Does anyone know of a successful install of one of these cards in a 2x only machine or where I can look to find out? Thanks again!

---

### Post by voided3 on 2006-11-07
I found this in an article about MX4200 Ti and MX440 AGP 8x cards: 

[http://www.digit-life.com/articles2/gf4/nv28-nv18.html](http://www.digit-life.com/articles2/gf4/nv28-nv18.html)


"The bus is entirely (forward and backward) compatible with cards of the previous version (AGP 2.0) and can work in 2x and 4x modes in the 2.0 standard and in 4x and 8x modes in the extended 3.0 standard. So, new cards which comply with the AGP 8x specification will be compatible with motherboards with AGP 2x, 4x and 8x, and new AGP 8x boards will support cards with 2x and 4x provided that they comply with the AGP 2.0 or 3.0 specification. As we know, there are some compatibility problems with earlier implementation of the AGP 8x (SIS 468, R300 etc.)."


It looks like it'll work if the board uses the 2.0 standard. Time to check the manual again...

---

### Post by voided3 on 2006-11-07
Alright, after I did some research, this is what I concluded: my board definetely is AGP 1.0 and the MX440s that run with the NV17 chip are 2x/4x agp and the NV18 chip equipped cards run agp 8x/4x ***AND*** 2x according to the links below:

[http://www.beyond3d.com/misc/chipcomp/?view=boarddetails&id=56](http://www.beyond3d.com/misc/chipcomp/?view=boarddetails&id=56)

[http://www.beyond3d.com/reviews/asus/v9180vs/](http://www.beyond3d.com/reviews/asus/v9180vs/)


I don't currently have access to the computer that currently has the card, which is running an IWILL KK266-R board w/ a 1.4ghz Athlon with AGP 4x, but I remember the program Powerstrip said I was running at the core speeds mentioned in the NV17 article, which makes me optimistic (I know the ASUS card was overclocked to 306, but the article said the stock ram speed was 275ddr, whereas mine was 200ddr). I suppose taking one more look at Powerstrip to see the core info page would be wise before I make the switch, but by the sound of it, either chip should support it. Any thoughts/corrections in reguards to my logic? Thanks!

---

### Post by weird_c00kie on 2006-11-07
> **voided3 said:**
> Hello. I am considering putting a nvidia MX440 AGP card with twin VGA outs in an old comp of mine that supports AGP 2x max, and the card goes up to 8x. Is that acceptable with that card, and will it pose any problems down the road from a harware or software standpoint? Thanks!

P.S.- if power is a concern, it has a 250 watt power supply, and I have a 300 watt sitting around I could put in

without having read what everyone has said, from personal experience, i'll say no.
i once went and spent $400 to buy the then-great 128mb Radeon 9600XT. it was an AGP 4x card. went home, happily installed it and stuff, but then my screen would come up as a jumbled mess. even after managing to disable the onboard graphics chip, the new card wouldn't work.
why?
motherboard only supported up to 2x AGP cards.
the result? by the time i figured this out it was too late to return the graphics card, so i was more or less forced to spend another $600 to upgrade my motherboard, CPU and RAM just so i could run the card.


i wouldn't go for it if i were you

---

### Post by voided3 on 2006-11-07
Hello. Did the the "jumbled mess" damage the card? If not, that may be my crude but effective answer to this question being simply not a concern of damage but compatibility. Ah what the heck, the thing is almost 8 years old, was practically free and I have FOUR other computers ranging from a 200mhz P1 to a Macbook Pro. The video card was free too! AND I have a agp 2x TNT card sitting around if i'm desperate. I'll try it and find out i guess, but any thoughts/suggestions are appreciated! Thanks!

---

### Post by zgornel on 2006-11-08
It's worth trying. Probably the video card won't even fit. Can't you test this ?

---

### Post by voided3 on 2006-11-08
Unfortunately I cannot until around christmas time when I am home from school. I brought my fastest desktop comp with me (Athlon XP @ 1463mhz... nothing special but scoots along quite well) for Windows games and Ubuntu everything else, and I got a Macbook Pro as part of tuition. I have three older desktops at home and the comp with the 2x agp is one of them. I know the card is keyed properly for the slot since it has both the 3.3v notch and the 1.5v notch, not one or the other, but my experiment will be on hold for a  little over a month. I'm upgrading my next fastest comp at home (Athlon @ 1.4ghz on an IWILL kk-266-r) with a new video card and hard drive to replace the MX440 that's in there, which is what's going in the 2x comp (which, as a mentioned previously, is a socket 7 EPoX board with a K6-III @ 450mhz). It's kind of a game of musical chairs since i'm taking the hard drives and vid card from the Athlon comp and putting them in the K6-III comp to make way for new peripherals and improve the older comp at the same time; it currently has a 8 gig quantum bigfoot in it (remember those, the huge 5 1/5" ones? yeah, I wish I didn't either). The K6-III comp has a PCI radeon 7000 in it now that I want to use on an even older 200mhz pentium 1 Compaq Presario, adding to the musical chairs game (believe me, a 32mb radeon is better than integrated 2mb S3 Virge graphics...). 
Anyway, the main reason behind this thread was to ask about the MX440's ability to work in that K6-III comp since I will have the parts availiable to take advantage of the AGP bus to give it a bit of a kick to prepare it for going solo with the Ubuntu fun fest (should its wireless card work with it... it does on win98 currently). Any more words of wisdom are always appreciated, and I will be sure to post how it turns out when I get it done in late december. In the meantime, i'll continue making a list of all of the parts I need for the musical chairs frankenstein-fest to be held on my workbench. Thanks again!

---

