---
title: "What video card works with Ubuntu"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by Scrib on 2007-08-22
Hi all,

   I've just built a new system with Ubuntu and everything worked straight away. :guitar:

The only issue I have is that I am using the onboard motherboard video hardware and its a bit slow with Beryl and game, etc. I know I could turn them off, but I want the fancy stuff.

So, can anyone suggest a new video card that will:

1. Work straight away with Ubuntu - with no need for any tweeks or messing around.
2. Will work well with games such as World of Padman (best game ever by the way and FREE!)
3. Is reasonably priced. I'm not after the latest card with all sing and dancing stuff build in, just a  fairly powerful one that will work!
4. Price range - hummm - say between £50 and £150, but towards the £50 end if possible.
5. Is a popular make, such as NVidea.
6. I have a Intel D845GVSR motherboard ([http://www.intel.com/products/motherboard/d845gvsr/index.htm](http://www.intel.com/products/motherboard/d845gvsr/index.htm)) with a spare PCI slot - so I will have to be a PCI card and not a AVG.



Anyone help?

---

### Post by w4ett on 2007-08-22
A card like this:

[http://www.imagestore.us/Items/v28](http://www.imagestore.us/Items/v28)

Can probably be found in the UK and the EU for a comparable pricing.  It will run Beryl and Games pretty well.  Being limited to a PCI slot seriously hampers your choices,

I'll do some searching from the UK vendors and will get back with you.

---

### Post by w4ett on 2007-08-22
Here is a UK Vendor (Misco)

[http://www.misco.co.uk/applications/searchtools/item-Details.asp?EdpNo=189873&sourceid=2004](http://www.misco.co.uk/applications/searchtools/item-Details.asp?EdpNo=189873&sourceid=2004)

---

### Post by Scrib on 2007-08-24
Thanks W4ett for taking the time to look at this. I'll buy one of these and feed back the results.

---

### Post by Scrib on 2007-08-29
OK. My shiny new Geforce fx 5200 PCI card arrived this morning. Even though it says there are drivers for Linux, none were on the CD or the web site, that I could see.

So I plugged it in and allowed it to boot to the inbuilt mother board video card. As expected udetected the new card and asked to download and install the generic drivers for the card (If I read it right).

I allowed it to do this and reboot. I then got an error of:

[I]Failed to start the X server (your graphical interface). It is likey that it is not set up correctly.

Would you like to view the X server output to diagnose the problem?[/I]

I managed to recover from this by taking out the card, booting into safe mode and running through dpkg-reconfigure xserver-xorg. I'm now back to my original config.

Before I go any further I thought I'd ask here for the best method to install and setup this card - before I totaly screw it up. I've read in anther post ([http://ubuntuforums.org/showthread.php?t=221313&highlight=geforce+5200](http://ubuntuforums.org/showthread.php?t=221313&highlight=geforce+5200)) which seems to imply this will just instal with "no Tweaks". Not in my experience.

Can anyone help?

---

### Post by Scrib on 2007-08-29
Fixed it - I used ENVYto instal the video drivers - now working super!

---

### Post by w4ett on 2007-08-29
Super....Another satisfied Ubuntu customer!!!  :lolflag:

Good Luck

---

### Post by Scrib on 2007-09-01
A fews days in and al still working fine. I'm really happy with Ubuntu.

Slightly off subject - but are we due a new release soon? I heard somewhere that Ubuntu has a major ugade every six months. Is that true?

---

### Post by w4ett on 2007-09-01
The next release is October 2007 called Gutsy Gibbon, and yes, the development cycle is set at six month intervals, so the planned LTS (long term support release) will be in April 08.

---

