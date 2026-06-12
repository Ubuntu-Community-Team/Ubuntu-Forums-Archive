---
title: "TV Cards"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by gunthermeyer on 2007-04-16
Now that I got my dvd player to work with the add of RomeReactor because without his or her assistance I would not have been able to gotten the software to work. Now is there anone out there that can guide through to getting me to get my TV Tuner Card to work under Linux. I still have the software for the Windows but I know that the software will not work under Linux unless I can find some kind of special magic from gifted person to make it run under Linux. The TV Tuner Card is a Smart TV Card. Once again great thanks to RomeReactor for the great help.

---

### Post by tgm4883 on 2007-04-16
What tv tuner?

---

### Post by gunthermeyer on 2007-04-16
O.K. A TV Tuner Card allows a computer to receive television reception and radio reception with the aid of supported software. I bought this card for my used to be Windows system and it worked great but now I'm using Ubuntu and I think that I can resurrect the card from the grave to work in Ubuntu 6.10

---

### Post by tgm4883 on 2007-04-17
Yes, I know what a TV tuner card is, but it is a little impossible to help you without at least the manufacturer of the card.  I was asking what the manufacturer and model number of the card is and unless you give us this information, we can only help point you in the right direction.

---

### Post by gunthermeyer on 2007-04-17
The only name was that I could find was "**[COLOR="Red"]Smart TV Card[/COLOR]**" I don't know the chipset. It's a pcmcia card. That's all that I know about the specs other than the name of the card. Sorry I miss understood your last question. does this help. I know that is very vague.

---

### Post by tgm4883 on 2007-04-17
Is this your card
[http://www.techcomindia.com/itemdetail.asp?prodid=634](http://www.techcomindia.com/itemdetail.asp?prodid=634)

---

### Post by tgm4883 on 2007-04-17
also can you post the output of lspcmcia

---

### Post by moon2js on 2007-04-18
I just found an old tv tuner card and put it in my Edgy/Xubuntu box.

```
$ lspci

00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
```

Is there anything I need to do to make it work software-wise?

I have tvtime, but it doesn't find any channels whatsoever, but maybe this isn't strange because maybe my antennae wiring isn't what it should be.

---

### Post by moon2js on 2007-04-18
Wait, I think may found out [what I'm looking for in another thread]("http://ubuntuforums.org/showthread.php?t=407463").

Apparently, I need to add line "options bttv card=100" to /etc/modprobe.d/options. Does that sound, right?

---

### Post by tgm4883 on 2007-04-18
> **moon2js said:**
> Wait, I think may found out [what I'm looking for in another thread]("http://ubuntuforums.org/showthread.php?t=407463").

Apparently, I need to add line "options bttv card=100" to /etc/modprobe.d/options. Does that sound, right?

Well if your card is indeed 100 and you did this

> modprobe -r bt878 (because the bttv module was used by that module)
modprobe -r bttv
modprobe bttv card=100


and it worked, then yes.  Adding that should fix your problem.

---

### Post by moon2js on 2007-04-18
Oh, good catch.

I can't really identify the card visually.

Is there any way I can auto-detect it?

---

### Post by tgm4883 on 2007-04-18
There aren't any numbers or anything on the card?  Usually any numbers on the card are useful

---

### Post by moon2js on 2007-04-18
[IMG]http://i53.photobucket.com/albums/g78/mooniker/Philips.jpg[/IMG]
[IMG]http://i53.photobucket.com/albums/g78/mooniker/Korea.jpg[/IMG]

Does this say anything relevant?

---

### Post by tgm4883 on 2007-04-18
Yeah, lots of stuff.

So after a little googling, (which would of took less time had I seen the philips in the pic)

Is this your card
[http://www.shspvr.com/reviews/pvr/images/screenshot00.jpg](http://www.shspvr.com/reviews/pvr/images/screenshot00.jpg)

:EDIT:

Also, here is a link to the philips tuners on the V4Lwiki
[http://www.linuxtv.org/v4lwiki/index.php/Philips_Tuners](http://www.linuxtv.org/v4lwiki/index.php/Philips_Tuners)

---

### Post by moon2js on 2007-04-19
Thanks! And sorry about not mentioning Philips. I meant to do that.

I found my card's number on the Philips list, but now I'm trying to figure out what to do with that information.

Is there any chance that installation will auto detect this? (I popped in this card without doing anything in the first place.) I'm going to reinstall this system with Feisty.

---

### Post by crispy_420 on 2007-04-19
I'm decent with bt878 card setup but now I'm confused. Is it a pci card or pcmcia? Images I've seen suggest both.

Do we know chipset?

bt878 or saXXXX

---

### Post by moon2js on 2007-04-19
There are two cards being talked about by two people. Mine is an old PCI analog tv tuner (bt878). I just popped it in and trying to figure out how to make it work.

It's on [this list of Philips cards on the V4Lwiki]("http://www.linuxtv.org/v4lwiki/index.php/Philips_Tuners"), the second item on the "document (1)" rows (?).

---

### Post by crispy_420 on 2007-04-19
OK, you have a bt878 based card and not a saXXXX based card?

If so I may be able to help you. What is the exact make/model of card?

---

### Post by moon2js on 2007-04-19
It's a Philips, type "FM1236/HM/F" as on [this list of Philips tv tuners]("http://www.linuxtv.org/v4lwiki/index.php/Philips_Tuners") that describes it as "FM1236 Desktop video & FM radio module system M, N", I think.

lspci identifies as:
```
00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
```

---

