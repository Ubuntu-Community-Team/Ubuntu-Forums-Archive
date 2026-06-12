---
title: "GeForce 6200 S-Video"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by TheBigJimbrowski on 2007-01-20
Hi, 

Setup: 
P4 1.8, 1gig ram, XFX GeForce 6200 AGP 256MB, Pinnacle TV card etc, running Ubuntu Edgy.

When I plug the S-Video cable (4 pin) directly into my TV from the video card's socket, the refresh rate on the TV is wrong (although this is an improvement from nothing) I can see the desktop but the picture is repeated four times downwards and flickers...other words useless. (same goes for boot up screen, and the ubuntu splash screen etc) Is there a way to force the refresh rate on the second monitor (TV) within xorg.conf or maybe in nvidia-settings? I have also really looked hard in the BIOS to make sure there's no weirdness in there, and it all seems logical to me. (VGA socket to CRT is fine and dandio)

I wonder if the s-video socket is transmitting NTSC (60hz) by default, even though I bought this card in a PAL-B region (netherlands)?..hope i'm being dumb.

Has anyone else had this problem, and how did you fix it? >It's taken me weeks to get this far and I haven't asked many questions, so please be kind. :wink:

I just want to use a separate tv to watch movies, is all, should be very simple?? I'm so close now, and this is driving me crazy! :confused:

I attach the rersult of lspci and my xorg.conf for your amusement.

Thanks in advance!
Jim

---

### Post by fenian on 2007-01-20
Check out this link for setting up tvout
[https://wiki.ubuntu.com/NvidiaTVOut?highlight=%28tvout%29](https://wiki.ubuntu.com/NvidiaTVOut?highlight=%28tvout%29)
I prefe the seperate x-screens method.

---

### Post by TheBigJimbrowski on 2007-02-19
An update.

So after no joy at all from the GeForce 6200 from XFX, and no response from this forum, I bit the bullet and spent some more money (GeForce 7200 from XFX), and this time the thing worked once I had installed the drivers (so far only in XP). It seems that the svideo on the XFX cards defaults to NTSC (despite being sold in Europe, and the MAJORITY of the world is on PAL) but is at least changeable with drivers.

So, now I know it CAN be done under Ubuntu,(ie. the card is not faulty) but I haven't actually done it yet. The dual screen system is working fine, (I can see it through the scrolling, rolling mess of NTSC- NTSC = NoT Standards Compliant) I just haven't quite figured out how to force the svideo output to PAL yet in the nVidia drivers / xorg.conf. but I will, and now I KNOW the problem I can more easily solve it.

If I can't I'll be back, but when I do Ill post my working xorg.conf in the correct place.

Cheers
Jim

---

### Post by dannyboy79 on 2007-02-19
well I am hoping that you checked out the link that the guy posted before you went out and bought a new card because the PAL-B was supported in your 6200. The link specifically states:

If you are using an S-Video cable change "COMPOSITE" to "SVIDEO" If your TV uses PAL change "NTSC-M" to "PAL-B", or other TVStandard. A modestly comprehensive list is available below. You may also change MetaModes to whatever is appropriate for your system! 

So I don't see why you couldn't get it to work. It's a simply /etc/X11/xorg.conf change.

---

### Post by TheBigJimbrowski on 2007-02-20
*sigh* 

> I don't see why you couldn't get it to work. It's a simply /etc/X11/xorg.conf change.

Oh really? Then I must be just stupid then. Like I haven't already been editing my xorg.conf for weeks without success. And yes, I read the post thoroughly, and all the other different 'solutions' out there as well, and No they didn't work, I have no idea why not, but perhaps it *might* now with the new card, as the other one didn't even work under windows.

You might as well have said "I don't get why there are starving people, its just a matter of feeding them", but thanks for the input. Do you have this card? Are you in a PAL area? Do you have the same setup? If yes, Why not post your xorg.conf, or a link to it, that might've been vaguely helpful.

*Useful* comments still welcome, however, but ill post my solution when I get it working, and I *probably* will eventually.

---

### Post by dannyboy79 on 2007-02-20
**larger sigh**

I can't read your mind so I obviously I have no idea what you have or have not tried!! If I could've read your mind I would have realized that you don't deserve help as you're an *********.  you can fill in whatever word others call you all the time. Plus you're the one who posted his xorg.conf which DOESN'T contain any of the suggested options for getting PAL to work!!!! You're missing the following:

Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "PAL-B"

Also, I simply read thru a few of these threads here, [http://www.ubuntuforums.org/showthread.php?t=98456&page=26&highlight=pal](http://www.ubuntuforums.org/showthread.php?t=98456&page=26&highlight=pal)
and found many people getting PAL to work correctly using Nvidia TV-Out, so good luck. Yes, I do have the same card as you and no I don't have PAL. I was merely trying to help and for anyone to act as you have towards some1 who is trying to help them sure is rude!!!

---

### Post by TheBigJimbrowski on 2007-02-22
Sorry dude, but you weren't helping, the link before was helpful, all you did was say, 'I hope you didn't just do something stupid' In the tone a Mother uses when she says to her child, "I hope you didn't just steal a cookie from the jar..? hmmm?"...I asked for help, didn't get it, did what I thought was best and u came in and critised me for it, so it pissed me off. I'm just getting frustrated that's all, but ill get there.

I'm not an *******, I'm a human being, who doesn't believe the Ubuntu tagline to be true, it seems way too technically fiddly for me. I'm pretty knowledgeable about computers, Windows that is, but I haven't had to manually configure stuff for literally years and I don't like doing it, I hate it in fact, it feels so...80's.... So I took exception to your slightly bumtious reply, so i kicked it right back at you, for which I apologise.

However, thanks for your further help, despite my rudeness...I'm about to try it out...

Love you.

Jim

PS the xorg.conf I posted was for a previous setup (ATI I think from memory) which never worked, that was two cards ago...but I'm persevering with Ubuntu, in the face of it, as like you no doubt, I don't like breaking the law or paying the Big BG to use my PC, I don't want a medal, just a little credit for my intelligence.

---

### Post by TheBigJimbrowski on 2007-02-22
Success. At last. 

Genuinely, thanks for your help, sorry if I came across rude, I'm going for a long soak in the bath...and my cap is in my hand.

Ill post my working xorg in the proper place as promised (see the 'Post your working nVidia settings here post)

Cheers
Jim

---

