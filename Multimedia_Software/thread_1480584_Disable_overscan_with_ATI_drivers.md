---
title: "Disable overscan with ATI drivers?"
date: 2010-05-11
forum: Multimedia Software
---

### Post by chaospoodle on 2010-05-11
When I first installed Ubuntu, I installed the ATI drivers with Catalyst Control Center, too. I believe the next time I restarted my computer, it was overscanned. It had the 2 inch border around my display. It was terrible, and I wanted to stop using Ubuntu because I couldn't find a fix. I finally removed the drivers through the terminal (don't remember how) and the border was gone.

The problem is, I don't have any actual drivers for this card installed. It's a Radeon HD 4650. I was thinking of trying: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriverhttps://help.ubuntu.com/community/RadeonDriver")

Would the be a way to remove overscan with that? Or is there a way with ATI's closed source drivers I had the first time? Ubuntu crashes sometimes and the screen goes all weird, which I'm pretty sure is from the video card. I also can't see the boot splash for Ubuntu when starting up the computer, which I've heard can be caused by your video card.

I'd like to have the drivers for my card, but not have to worry about the damn 2 inch overscan.

---

### Post by smuggly on 2010-05-16
I Have The Same Problem.I Wish That CCC Could Just Have The Overscan Slider Like Windows. But Im Also Game For An Edit Of Xorg.conf. I Dont Have The Problem Using My VGA Plug.But, HDMI Does. Hopefully Someone Will Come Up With Something.  Thanks...

---

### Post by cableo on 2010-06-28
same here...

I am "missing" about an inch and a half around my lcd...

"it" thinks its hooked to a 36 inch when in fact it is only a 32.

ati x1200...

any thoughts would be great.

---

### Post by urbanus on 2010-06-29
The closed source driver DO have a over/underscan slider, so I don't see whats the problem. Older cards might not be supported by the newer drivers that supports this, but they have supported it for the last year or so, but the setting is a bit buried in the menu system I think. 

I don't think the X1xxx cards are supported by the newer binary drivers, but check the readme files from ATI, the cards are listed there.

---

### Post by Mark Phelps on 2010-06-29
> **urbanus said:**
> I don't think the X1xxx cards are supported by the newer binary drivers, but check the readme files from ATI, the cards are listed there.

No, the X1xxx cards are NOT supported by the newer binary drivers.

The last ones that DID support these cards came with Catalyst 9.3, and that would only work with Ubuntu 8.10 or earlier.

---

### Post by l1oyd on 2011-03-26
So I'm having the same problem.

Installed 10.10 on my new HTPC and when displaying the picture over HDMI with an ATI HD5570 I get a black bar around the whole screen of about 1 inch. 

Has any one had any luck with this issue?

CCC also sees my TV as a projector could this be part of my problem?

EDIT:

With a reinstall and using the open source driver I get to use the whole screen except for a purple line on the left hand side of about 2 pixels.

Also sound isn't coming over the HDMI anymore.

---

### Post by l1oyd on 2011-03-27
Back to using the latest ATI driver (11.2) and still the same problem. I can over scan the TV and make the black boarder not quite as large but it's still not filling the screen.

At least I have sound again...

---

### Post by goldaryn on 2011-03-27
Are you using the correct scale option in CCC?

---

### Post by l1oyd on 2011-03-27
I'm sorry I don't know where I would find that option? 

I'm very much a beginner.

EDIT: Looking around this option doesn't seem to be available?

---

### Post by goldaryn on 2011-03-28
System -> Preferences -> ATI Catalyst Control Centre (administrative)

Click on Display Manager then the monitor

Adjustments tab

Use Scale to full size and recommended is use graphics processor for scaling

---

