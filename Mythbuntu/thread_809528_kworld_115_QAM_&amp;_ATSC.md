---
title: "kworld 115 QAM &amp; ATSC?"
date: 2008-05-27
forum: Mythbuntu
---

### Post by bah1976 on 2008-05-27
After some weeping and gnashing of teeth, I have a nearly configured mythbuntu system.  I have 8.04 x64, and more importantly two kworld 115 tuners.  If I have the tuners configured for ATSC, they pull signals from the top input.  If I have them configured for QAM256, they pull from the bottom input.  Is there anyway to use them both ways?  i.e., have tuner 1 port 1 ATSC, tuner 1 port 2 QAM, tuner 2 port 1 ATSC, tuner 2 port 2 QAM?  I read somewhere about making one a sub tuner by editing the database directly, but I can't find that reference again.  Plus, I'm not sure it would work anyway.  Anybody have any ideas or references for me to try?

Thanks!

---

### Post by Posh on 2008-05-28
I currently do this.  As long as you have a different source for QAM and ATSC it should be fine.

I used phpmyadmin to edit the cardinput table and add another cardinput.  You should make a copy of the line for your dvb card except change the cardinputid (just keep increasing the number), sourceid (to whatever source you are using), and inputname.  Then in mythsetup you should be able to scan for channels etc.

I know this is kind of brief but hopefully it gets you pointed in the right direction.

---

### Post by bah1976 on 2008-05-28
Posh - unfortunately, I think it's too brief.  I tried doing this, and the newly added cardinput didn't show up in mythsetup, and when I exited mythsetup it warned me that the new input was set to start on a channel that didn't exist.  So I know that at some level it's trying to interact, but not at the level I can scan channels with.  

Can you provide any additional information on how you did this?  I think you're doing what I want to do, but I apparently don't know as much about the database as you do.

Thanks in advance!

---

### Post by bah1976 on 2008-05-28
Ok, I'm making progress...  I now have both ports active, and I can scan for the different signals without moving any connections.  The next question - can I record from both ports at the same time?  Can I capture a QAM stream and an ATSC stream on the same 115 card?

---

### Post by twostar on 2008-05-29
My understanding is that the card will only capture from ATSC or QAM but not both at the same time. That's why it's important to modify the DB to add a subconnection to the card in Myth. It keeps myth from trying to record from both at the same time. 

I've got the same card but am only using it for OTA ATSC so I haven't added the other functions as a subconnection.

---

### Post by mdizzle on 2008-09-08
> **bah1976 said:**
> Ok, I'm making progress...  I now have both ports active, and I can scan for the different signals without moving any connections.  The next question - can I record from both ports at the same time?  Can I capture a QAM stream and an ATSC stream on the same 115 card?

Could you go in to more detail about how you did this? I'm tinkering with phpmyadmin but I can't figure out what all I need to add to which tables.. :(

---

### Post by bah1976 on 2008-09-08
First, go into the normal myth backend setup and make sure you have the card configured as a single tuner, and the two video sources configured for SchedulesDirect or whatever.  Give them meaningful names - mine are SD_ATSC and SD_QAM.  

Next, go into the capture card table and identify the "cardid" for the two cards you want to add this setup to.  This will work with a single card as well, just note the single cardid that indicates your tuner.

Check the "videosource" table - you should see multiple "sourceid" entries that correspond with the sources you setup in myth.  Make a note of the "sourceid" numbers.

Now, go to the cardinput table - this is where you'll actually make changes.
the cardid in this table is what links the input over to the capture card.  You should insert new rows and copy most of the details from the row that was configured in myth.  You should end up with two rows for each card, with the following notes: 
"cardinputid" needs to be unique for each row.  
"cardid" should be the same as the card you're configuring
"sourceid" should correspond with the video source you noted
"InputName" I don't know if this is required, but I've named them just to keep them separated.
I also have a value in "startchan" and "displayname"  You should be able to configure these through myth once the inputs are valid.

Once the cards are configured properly, you should be able to go back into myth and scan for channels.  Make sure when you scan you select the right input - you won't find QAM channels on the ATSC input or ATSC channels on the QAM input.  For my own sanity, I have the QAM channels separated by "." and the ATSC separated by "_".  This should get you pointed in the right direction.  If you mess something up, just delete all cards, inputs, sources, and start over.  (that's why my cardids are 36 & 37 instead of 1 & 2)

Ok - probably the easiest way to show all this is by example.  So  here's my setup.  (I apologize for the huge images - just wanted to get everything included)
Capturecard table:
[IMG]http://www.theheavners.net/capturecard.jpg[/IMG]

VideoSource table:
[IMG]http://www.theheavners.net/videosource.jpg[/IMG]

Cardid table:
[IMG]http://www.theheavners.net/cardid.jpg[/IMG]
Note that on card 36, I have two inputids: 131 & 133, with different sourceid, inputname, statchan, and displayname.  All other fields were system generated, and I just copied the values.

---

### Post by newlinux on 2008-09-08
Just an FYI, If you are using myth .21 there no longer is a parentid field. You can just use input groups to stop recordings from happening at the same time. Just create 2 different inputs (basically two different cards) one ATSC, one QAM, and then create an INPUT group and assign both of them too it. No direct database modification is needed anymore.

---

