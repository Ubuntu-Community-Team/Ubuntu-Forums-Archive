---
title: "Ati Aiw Rv350 9600xt Tv Tuner"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by CrustyRatFink on 2006-10-23
Hi,

Hopefully, this post will server to aggregate what seems like a whole bunch of conflicting information in the tubes of the internets into one place.  

I'd like to hit on a couple very specific questions:

"Is it possible to get an RV350-based All-in-Wonder card to display television input in Ubuntu (Dapper or Edgy)?  If no, why not?  If yes, is it then possible to utilize that card for something like MythTV, VLC rebroadcast, etc.?"

I followed a how-to about compiling ffmpeg and avview, but while it acted like it had found a device after godawful patching and propeller-headed compilation, nothing showed (i.e., black screen) for any input.  

I'd appreciate anyone even clarifying the issues here.  It strikes me that it must be *possible* to acquire the television input as it works in XP for VLC, for example.  Still, I can't bring myself to run Windows anymore-- just because of the viruses, the anti-piracy crap (guilty until someone in Bangalore decides you're innocent), the opacity of the system, etc.

Is is an encoding thing?  Is there just no driver available to pick up the input and how does it differ from tuners that do work?

Please educate me a bit.

Thanks,
CRF

---

### Post by CarpKing on 2006-10-23
Is [this]("http://www.ubuntuforums.org/showthread.php?t=273291") the HowTo you followed?  I intend to try it out, but I've kind of been waiting until Edgy, hoping that the newer open-source radeon driver will work for me.  When I installed Dapper, I had to install the closed-source drivers in order to get any sort of visible output to my monitor.  

From what I've gathered, fglrx has no support for video capture.  The GATOS project seems to be the source of ATI support in X.org, One source of confusion on this matter is between X.org and XFree86- the GATOS drivers are for XFree86, but code from them is included in X.org, which is what Ubuntu uses as of Dapper.  [This]("http://www.linuxtv.org/v4lwiki/index.php/ATI") page seems to indicate that the part about grabbing the file from the install disk might be unnecessary.  

Anytime I look into this situation, it seems I end up with 10-12 tabs open to different sites with different information, often from years apart.  Only a little of it is directly contradictory, but it sure is confusing.  If anything I said was wrong or misleading in any way, PLEASE tell me.  I really want to get this working.

---

### Post by CrustyRatFink on 2006-10-24
Yes.  That's the HOWTO.  And note the *important* thing about the BIOS.  It doesn't say what to do if you don't have that option in your BIOS, and I don't.

Anyway, it was a bear to get patched (ffmpeg) and built.  And then, after all, it didn't work.  I tried with both Dapper and Edgy, just in case.

Likewise, I end up with half a dozen windows open, and there are these sort of obtuse references to GATOS being "in" Xorg, but the stock Xorg drivers don't allow me to capture from the tuner (that is to say, it is entirely likely that I don't know how to do so).

I'd love to get something definitive like "if you load the stock ati xorg driver and enable option 'AllowTuner' in xorg.conf, you'll get a /dev/video0 that you can capture from..." or the like.

Imagine one started from scratch, and the documentation had diverged sufficiently to be seriously confusing.  If anyone can shed some light on the situation, I'd still be obliged.

How do these differ from other video capture cards? (e.g., Hauppage)
Can they be 'activated' with Xorg/GATOS?  How?

Ideally, what I'm shooting for is a machine that I can use to distribute my cable signal around my house to my (many) machines.  Just due to my computer-aholocism, I've got machines all over the house and yard with wireless.  When I ran XP on this box, I could pick up the stream with VLC and resend it to any VLC client on any other machine.  It was very cool.  I just... hate XP.

---

### Post by CarpKing on 2006-10-31
Since upgrading to Edgy, I have finally managed to get the open source drivers working.  I still don't have DRI (I'm hoping to try AIGLX as well).  However, enabling AGPfastwrite prevents X from starting up right, so I probably have to do something in the BIOS.  The DRI failure seems to be AGP-related as well.

---

### Post by CrustyRatFink on 2006-11-01
> **CarpKing said:**
> Since upgrading to Edgy, I have finally managed to get the open source drivers working.  I still don't have DRI (I'm hoping to try AIGLX as well).  However, enabling AGPfastwrite prevents X from starting up right, so I probably have to do something in the BIOS.  The DRI failure seems to be AGP-related as well.

OK, this is generally how these threads end... 

Would you mind running down for me (and posterity) what you did?  When you say it's "working," what do you mean?  You can watch TV in?  What app?  How'd you configure it?

I've got Edgy on the box now, and I just get nothing.  A black screen.

If you wouldn't mind, take a minute and run down your setup and results.

Thanks.

---

### Post by CarpKing on 2006-11-01
Sorry for the misconception.  I don't have TV-in yet.  I just was able to get X to start using the open-source radeon driver instead of fglrx, which I hadn't been able to do since Breezy.  I just thought it was worth mentioning in order to bump the thread and because fglrx was preventing me from even attempting this.

---

### Post by watson540 on 2006-11-10
TV in DOES work, it's just that you have to jack around with it for hours on end and when it finally does work the picture looks all fuzzy and junky anyway.

And sound is a whole 'nother story, it dont work for me ..period

---

### Post by CrustyRatFink on 2006-11-17
Hi Watson,

OK, again, it'd be great if you could run down what "jacking around" got yours to work.  If I can get a jumpstart, I might be able to make more progress with it.  At the moment, I've got just blank screen staring at me, and I'm stuck.

Did you use the process mentioned with ffmpeg and all that business?  

I understand that you're frustrated by it, but if you could see your way clear to elaborating, maybe someone could get it to work?

---

### Post by linolium on 2006-11-18
Hello everyone,

I am not a Ubuntu user nor am I the owner of the video card discussed here.  But I have been researching the exact same topic for the past few days and am on the verge of going crazy.  I have encountered the exact same information dating from years ago, pointing to things being merged into Xorg and such.

What I don't understand is how that would help in creating a /dev/video0 (what I lack) file, since that sort of thing isn't really created when you type "startx" if I am not mistaken.

Suffice to say if anyone has information about this or the card I use (VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]) I would be infinitely happy to hear from you.

---

### Post by CrustyRatFink on 2006-11-18
Well, linolium, we're at another point that these threads usually end up "I don't have this card... but... won't someone help me?"

Nothing personal... I think it's a natural result of the "you get what you pay for" moment that comes up fairly regularly in the linux world.  That's not a slam of linux.  It's a statement of fact.  Some stuff works.  Some stuff doesn't.  Unless some coder somewhere graciously (or selfishly) decides to allocate the time to figure out how this card works and then (even more miraculously) bothers to tell anyone about it, you're just out of luck.

My experience in weeks (months?) of chasing this around is that I think the former has happened, but the latter has not.  Clearly, some people have had some measure of success with these tuners.  And then I guess they lose interest.  It's always been this way and will always be this way I fear.

It's very frustrating but can't be directed at anyone or anything in particular-- best target is probably ATI themselves.  We all would love to get off Windows, but linux is still a long ways away for that purpose for most people.  Doesn't take too many things that don't work (wireless cards, tuners, bluetooth gear, etc.) or applications that aren't ported to rain on even the most eager fanboy's parade.  

Ah well, we could always ask for our money back.

---

### Post by pedalwrench on 2006-12-02
just a bump to get more readers and possible solutions

---

### Post by cainmark on 2007-01-24
I've been trying to switch to Ubuntu full time.  My hardware video card is the only thing stopping me.

It's the ATI All-in-Wonder 2006 edition.  Works great under XP.  I love the video wallpaper (is there anything similar for Gnome or KDE? VLC has it in WinXP, but can it have it in linux?) especially the thruview.  But I do hate XP.  Once I turned autoupdate off it works much better, though.

But, I've also been all over the internet trying many different things trying to get it to work.  It doesn't, and the few times I've read people have been able to ge it to work some, they don't get sound or are not able to record.

ATI seems to be the culprit here.  If they don't open source their tv-in drivers, linux users who paid for thir hardware are kind of, well, screwed.

Been trying since June and have resigned myself to dual-booting just for TV and hardcore video editing functions (simple stuff I can do with Kino, the more powerful Linux video editing programs [Cinerella] right now have too steep a learning curve for mutliple track compositing for me to investigate right now)

So I'll probably keep doing that until I can afford to buy an nVidia card and a Hauppage WinTV-150.

Although here's something I'd like to add to the discussion.  

Is it at all possible to get  a Hauppage WinTV-150 working for the TV-IN functions, but still use the ATI card  for display?  I really don't kow how all this works, I just want it to and I've already spent way more time than I should have on it.

Thanks for starting this thread and pinpointing the same problems I had.

---

