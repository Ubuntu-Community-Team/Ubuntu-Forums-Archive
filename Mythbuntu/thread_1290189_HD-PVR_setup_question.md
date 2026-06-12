---
title: "HD-PVR setup question"
date: 2009-10-13
forum: Mythbuntu
---

### Post by bcg30506 on 2009-10-13
We've been very happy mythtv users for years but are still on standard def. digital & analog cable.  I have 2 PVR-150's in my box with one using analog cable tuner input and the other using composite input from the digital cable box.  On that one, I'm using the IR blaster that came with the PVR-150 to change channels on the cable box.  All this is and has been working great for many years.

Now we have the itch to move up to high-definition cable.  We still want the capability to record 2 things at once or record one thing while watching live tv inside mythtv (cannot ever go back to watching tv without mythtv now to be able to rewind or pause then catch up - great feature!)

So I'm just trying to get my head wrapped around this.  I assume I'd need 2 HD cable boxes then 2 HD-PVR capture devices.  Is this right?  Can this work?  I've not seen any references online to people using more than one HD-PVR on a system.  Can a decently powered myth box handle this?  Then what would I do about controlling the cable boxes to change channels?

Can mythtv support recording in HD?  I know my box plays HD fine when I watch our Canon 1080p mts video files on it from our camcorder and watch Hulu in HD.  I have VDPAU setup and working very well (except for the nagging A/V sync issue that only occurs with VDPAU profile; Slim never seems to get out).

Sorry for the long message but I wanted to be thorough with my background and current setup and where we want to go.  This is the one thing that has kept us from upgrading to HD by now.

---

### Post by larsolav on 2009-10-13
Hi there,
I'm fairly new to this, and only have been using over the air stuff so far. I have been looking into HD cable now a little, and from my limited research I think you should be fine playing the captured HD-PVR files, as you are using VDPAU already. I also think you will need two sets of boxes (2 HD-PVRs and 2 Cable boxes)to record two shows at a time. Futhermore, the HD-PVR has a built-in IR blaster (see [http://www.hauppauge.com/site/products/data_hdpvr.html](http://www.hauppauge.com/site/products/data_hdpvr.html) )

---

### Post by bcg30506 on 2009-10-13
Awesome.  It looks great.  The remote is exactly what I have now so I won't even need to change my LIRC config it seems. :)

Are the audio outputs and video loop out so that I can watch TV straight from the box to my TV without MythTV if need be, while also sending the signal via USB to the myth box?  That may be a useful feature if it is.

If I bought and setup 2 of these, will mythtv handle it (especially the IR blaster portion)?  Do I need to remove my PVR-150 PCI cards or can they stay in place and simply not be used?  Any conflicts?  Would I need to tell mythbuntu to not load the 150 drivers when I configure the HD-PVR drivers?  If so, how is this done?

Thanks for the help!  I'm getting close to doing this but don't want a ton of downtime so I'm trying to be thorough up front.

EDIT:  I just found this review from this week on Amazon.com stating some issues with the Linux driver and firmware updates.  Can anyone confirm and address these items?

[http://www.amazon.com/Hauppauge-1212-Definition-Personal-Recorder/product-reviews/B0018LX0DY/ref=cm_cr_dp_synop?ie=UTF8&showViewpoints=0&sortBy=bySubmissionDateDescending#R29YOD4EL4G49A](http://www.amazon.com/Hauppauge-1212-Definition-Personal-Recorder/product-reviews/B0018LX0DY/ref=cm_cr_dp_synop?ie=UTF8&showViewpoints=0&sortBy=bySubmissionDateDescending#R29YOD4EL4G49A)

---

