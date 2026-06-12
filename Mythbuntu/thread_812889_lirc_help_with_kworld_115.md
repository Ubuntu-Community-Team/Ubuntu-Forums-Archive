---
title: "lirc help with kworld 115"
date: 2008-05-30
forum: Mythbuntu
---

### Post by bah1976 on 2008-05-30
The final missing component of my successful first/new build is the remote.  On this particular part, I have no idea how to proceed.  I have read through some directions for using lirc, but I don't know what module to use - if any of them would even work.  In the MCC, there is no mention of this particular receiver.

So, my understanding is that the IR receiver part is the hardest - after that it's just configuring the buttons to do the right thing.  Theoretically, once the IR receiver is receiving IR codes, I should be able to see any IR codes from any remote - not that I plan to do that, just thinking out loud.  The obvious question is - how do I get the IR receiver to work?  I know it's not recognized at the moment, if I do "irw" it says Connection Refused.  I also don't see any mention of IR in lspci or dmesg.  One oddity that may or may not be relevant, in backend setup, the cards are listed as Air2PC cards under the DVB input.  I'm not overly concerned, since the tuners work without any issue - I figure it's because of the firmware used.  But does that firmware have an affect on the ability to use IR?  I'm just terribly confused.  If anybody has any direct experience with the remote setup on this card, or general advice on getting it setup, it will be much appreciated...

I am running 8.04 x64, and I have two kworld atsc-115 cards working well as tuners - just not as IR receivers.  I only need to be able to use one of them as an IR receiver - the other one will not be used.

---

### Post by sjrice on 2008-05-30
You will need to patch the kernel to use the ir receiver on the Kworld card.  See the [Kworld 110 & 115 mythtv wiki page]("http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110") for the details.

I have the Kworld 110, but ended up not using the remote receiver.  as I'm not really sure how to go about patching the mythbuntu kernel.  I'm using the Kworld remote with a cheap serial IR receiver that I got online for $5 (the infamous Packard Bell fastmedia one).  It works, but not that well.

If you do attempt to patch the kernel and get the IR receiver working, a nice how-to would be appreciated.  I found that what was provided on the wiki page wasn't enough info for me.  Good luck!

---

### Post by bah1976 on 2008-05-31
I know about the supposedly required kernel patch, but I am not entirely convinced of its requirement since those directions are a bit old (march 2007) and since Hardy is built on a newer kernel anyway.  I'm afraid I'm not knowledgeable or brave enough to attempt the patch myself either.  I'd like to, since I can't find any other directions, so I could guide somebody else, but I just don't have the experience.  Instead, I think I'm going to buy a Microsoft USB IR receiver and call it a day.  I'm off to ebay to look for IR receivers...

---

### Post by dracflamloc on 2008-06-20
Um, any luck getting this thing working? Mythdora even has it listed as a supported remote, but tried that instead of mythbuntu and it still wont work for me

---

### Post by bah1976 on 2008-06-21
Unfortunately, I did not get it working.  And even worse, I gave up.  I'm not qualified (in my own head) to do any heavy tinkering with the kernel to get this to work, and I didn't want to worry about it.  I took the easy way out and went with a microsoft usb mce remote.  Got it from buy.com for like $27 with shipping.  The trick is the IR receiver - once you get that to work, you can get any actual remote to work by using the right ir codes.  Check out lirc documentation (lirc.com ?) for some help with that.

---

### Post by DrewMac on 2008-06-21
I am also using a Microsoft MCE remote and USB receiver. I find it fast and the remote is very good quality. The receiver is supported out of the box and there is also the button map already installed for the remote. It works great; I highly recommend it.

---

### Post by ouellettesr on 2008-07-06
can you tell me how you got it to work? I have the microsoft remote and reciever but i cant get it to do anything in hardy. What programs are you using too?

---

