---
title: "Grey IR Remote WinTV-HVR-1250 Problems"
date: 2008-06-03
forum: Mythbuntu
---

### Post by NeroMaverick on 2008-06-03
**Down for TLDR ver..** I tend to be wordy
Hey everyone, just yesterday I bought the Hauppauge! WinTV-HVR-1250 card with IR port and remote. It is a PCI-E card and the remote that came with it is the grey version with the red green yellow and blue buttons on the bottom above the H! logo.

When I installed it I went straight to getting the remote to work, I don't actually care about the tuner features of the card, I only got it because of the remote.. long story short, supported Microsoft remote was $50, tuner card + remote was $54.

I think my system recognizes the card, but for some reason for the life of me cant get the IR to work. I've looked at just about every board on the net trying to find a solution, so I'm well aware of the programs and modules that go into getting it to work.

The only things I can find pertain to the 150 and 350 cards. There seems to be almost no info on the 1250 card. I'm running Mythbuntu 8.04 recently updated as of 5/31/08 or 6/1

**TLDR:**
   Trying to get WinTV-HVR-1250 to work with IR
   on a 8.04* Mythbuntu system
   /dev/lirc or /dev/lirc0 doesn't show
   irw breaks the lircd process

If anybody is willing to help, I'll be glad to give more info from commandline and whatnot.

Thanks!!

---

### Post by jobix on 2008-06-13
Did you get this working? I am looking at buying this same card for a mythbuntu system.

---

### Post by otahdfool on 2008-06-13
I've spent about 3 days trying to make this card's IR work.  I'm taking it back in the morning and getting something else.  (anything else) ((within reason)) (((that works in linux)))

:(

---

### Post by jobix on 2008-07-05
I bought this card but so far it doesn't seem to be working. It seems to be getting recognized but when I click "Watch TV" I just get some garbage - looks like some incorrectly decoded stuff. It's not blank neither is it static.

Any ideas?

---

### Post by theonlyrealperson on 2008-07-28
I have one of these too, and although the card works relatively well the IR doesn't work at all. From what I can gather, the whole card (including the IR receiver) works off the cx23885 driver.

Apperently, the driver works for the card but not the receiver yet. See [video4linux mailing list]("http://lists-archives.org/video4linux/22015-hauppauge-remote.html")

Anyone else getting intermittant flakiness on HDTV?

---

### Post by NeroMaverick on 2008-08-14
Well, I decided to scrap the idea of using this setup. Maybe in the future when it becomes a little more supported... I can't see why it would tho, considering the overall quality of the video that comes from this card. On Windows the quality is terrible.

A friend of mine was going to throw away his old XBOX remote and IR Dongle, I nabbed those and quickly went online to find out if it worked with Linux. The dongle is supported, with only one drawback. You need to solder a usb cable onto the dongle so it will plug into your system, and you can't use any xbox controller anymore. Once its all setup, it shouldn't be a problem to get working.

I solved the problem with the ugly XBOX remote with a Sony IR Commander remote, get the remote that learns commands from other remotes... trust me, it saves alot of time and hassle in the end. You just program the remote with the same buttons the XBOX remote uses and everything should work, while you're at it, program your tv remote as well. The remote was only $25 at target, and I've seen the XBOX IR receivers for about $10-$20 at gamestop. That's about all you need to get everything working.

Hope that helps for people who are looking for an IR solution for their Linux/MythTv boxes.

---

### Post by mbergen on 2008-08-30
Hi.  I found this thread while searching for a solution myself - I found a hint in a review of the product so I thought I'd post it here in case you are still having this trouble, or if anyone else goes searching for it.

You may think that the ir receiver is plugged all the way in but it might not be.  Because of the location of the place you plug it in, it's hard to get all the way in - on mine a metal piece in between where you plug in the cards was keeping the plastic part of the plug from going all the way in - it should be flush with the card, not out at all.  I had to unplug the card from the computer and plug the ir receiver with it out of the computer, then plug it back in, and try and bend back the metal piece on the computer a bit - now it is working fine.  I thought I might have been able to shave off the plastic portion of the plug a bit as well so it would fit in but didn't need to.

Meg

---

### Post by untjake on 2009-01-27
Anyone find a solution to this? I've made sure that the plug is secured correctly, but still no luck. I'm Not sure what I should try next.

---

### Post by trippinnik on 2009-03-01
Yeah, I'm not having any luck with this either. I think I can receive signals though. In OpenSuse Yast has an IR control panel and I get reading from /dev/ttyS0. But I'm not sure how to hook that in to mythtv or anything else.

---

### Post by barrelrollololol on 2012-09-27
> **mbergen said:**
> <snip>
You may think that the ir receiver is plugged all the way in but it might not be.  Because of the location of the place you plug it in, it's hard to get all the way in - on mine a metal piece in between where you plug in the cards was keeping the plastic part of the plug from going all the way in - it should be flush with the card, not out at all.  I had to unplug the card from the computer and plug the ir receiver with it out of the computer, then plug it back in, and try and bend back the metal piece on the computer a bit - now it is working fine.  I thought I might have been able to shave off the plastic portion of the plug a bit as well so it would fit in but didn't need to.

Meg

whoa, old thread, but I wanna say Hauppauge is still selling the WinTV 1250 that I purchased today Sep/2012

I was going crazy because the remote wasn't working. I thought it was dead batteries, I thought it was driver issue, I was just going crazy.

After reading Meg's solution it worked.  lol.  It seems I have not plugged the connection all the way in.  I thought it was all the way in but I used some force after reading Meg's post and heard a snap then after that the remote started working.

---

