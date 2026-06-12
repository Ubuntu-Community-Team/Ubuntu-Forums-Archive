---
title: "No Microphone input on ASUS a8n-sli deluxe in Ubuntu Fiesty"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by ThePinkSpartan on 2007-06-27
Hi folks,

New to the forums here and I have a bit of a problem.  I'm trying to make the jump to linux(ubuntu to be more specific) permanently as my desktop solution (it's currently just my server solution has been for a number of years) but I cannot for the life of me get my microphone input to work. I searched the forums couldn't find anyone with a similar problem unfortunately on my board and i've tried irc. I've also tried raising all the levels in alsamixer and that didn't help me at all.  Sound comes out just fine from my speakers, but input doesn't exist. I've even tried putting the mic in all the jacks and still have no luck.  The microphone works fine in my windows install (I have a dual boot currently setup).  Any advice please? Again, i'm running an ASUS a8n-sli deluxe mobo with a AMD 3700+ processor, 2 gigs of ram, and around 1.5tb of HDD space  distributed over an IDE and a SATA2 Raid config(and no I'm not using the raid for ubuntu, in fact I don't even have it setup thats a project for a later time.) Thank you for any help.

---

### Post by The other One on 2007-06-28
Hi!
I'm having a similar problem to you - mic works on my A8N-SLI, but I can't get line in to work :(

To get your mic in to work, use synaptic to install aumix. You have to run it from terminal (just type in aumix) and you'll find the right slider in there to get your mic happening.

Sorry if this is a little vague - I've just converted to LInux myself (2 months so far, never going back!)

---

### Post by ThePinkSpartan on 2007-06-28
Thanks i'll try that out tomorrow morning and let you know! :-)

---

### Post by ThePinkSpartan on 2007-06-30
So that didn't work either unforutnately, my mic is already turned up all the way and set to record...anyone else have any advice ? I tried both the aumix terminal and aumix-gtk on that one but volume was setup right record was set right even tried to change record/play option in every option box still nothing.

---

### Post by ThePinkSpartan on 2007-07-01
Figured it out on my own, Double-click the volume icon in gnome on the panel. Then under preferences enable the checkbox mic front input.

---

### Post by mjfleck2000 on 2007-07-01
> **ThePinkSpartan said:**
> Figured it out on my own, Double-click the volume icon in gnome on the panel. Then under preferences enable the checkbox mic front input.

You have got to be kidding... ;)  I have been messing with mic imput but had been unable to record sound.  I double clicked the sound icon in the upper right menu bar... and saw that the volume control was set at nothing!  Moved the volume control slider up to mid-way... bingo! We have mic input.

---

