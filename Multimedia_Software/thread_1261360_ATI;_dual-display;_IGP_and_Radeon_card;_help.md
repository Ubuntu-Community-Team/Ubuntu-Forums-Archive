---
title: "ATI; dual-display; IGP and Radeon card; help?"
date: 2009-09-08
forum: Multimedia Software
---

### Post by itzfritz on 2009-09-08
I have just installed jaunty on a new box that has an integrated Radeon HD3300 GPU, as well as a Radeon 4850HD PCI-e x16 card.  I have set up my two monitors, 28" and 19" LCDs, using the on-board hd3300 for the smaller LCD.  I have installed the new ATI 9.8 restricted binary drivers/catalyst, manually (created debs from the ati installer).
Unfortunately, it is not working as well as I had hoped; part of my screens are turning black, the box is hanging/crashing, compiz does weird things, etc.  
Should I leave the IGP alone and do a dual-head scenario using only the 4850HD?  I'd hate to do that, b/c both the IGP and the card have HDMI, which is what I am using for both LCDs.

What I am really looking for is someone who has experience in a dual-display Radeon system, and can offer some advice.  With AMD kicking their linux support up a notch, I figured it would be a good investment to move away from nvidia.

Should I just chill, and bump this thread after I've upgraded to 2.6.31 later this week (with it's ATI fixes)?

Thanks!!

(FYI, this new box is my first venture into getting rid of Windows for good!  been a nix user for a while, never took that dive though....)

---

### Post by markbuntu on 2009-09-09
I never had any luck getting my 3300 IGP to work with my HD3650 PCI-e x16 or my HD3450PCI-e but I have got the HD3650 working with the HD3450. with the latest Catalyst 9.8. I have been following this for a long time now and it does not appear that they have yet got a handle on the IGPs working with PCI cards though they seem to have finally fixed many of the problems with multiple PCI cards. 

But, I have three monitors working, YAY!!.

If I were you I would not go leaping into the 2.6.31 kernel with the ati driver though a pre-release 9.10 driver is in the karmic repos. You should look in the Development and Programming/Karmic forum first, there is an ongoing thread about it there.

---

