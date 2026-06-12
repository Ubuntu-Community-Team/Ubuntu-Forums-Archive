---
title: "PIP with two analog TV cards"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Mrazek on 2009-08-27
Hi all,
 
maybe the stupid beginner's question: I want to use PIP (or simultaneous recording of other channel while watching something other) and has two supported analog cards. There is no problem to setup mythbuntu for liveTV with one of these cards but settings of video sources, inputs, input groups and their priorities is little tricky for me and both tuners installed at a time.
 
Am I right that I need ONLY one TV source for both cards and then their two TV inputs "connect" to this one TV source in backend setup? And what about input groups and priorities? May be I'm near the solution but I need to be kicked by somebody who knows the MythTV philosophy of working with more TV cards...

---

### Post by vidtek on 2012-03-04
> **Mrazek said:**
> Hi all,
 
maybe the stupid beginner's question: I want to use PIP (or simultaneous recording of other channel while watching something other) and has two supported analog cards. There is no problem to setup mythbuntu for liveTV with one of these cards but settings of video sources, inputs, input groups and their priorities is little tricky for me and both tuners installed at a time.
 
Am I right that I need ONLY one TV source for both cards and then their two TV inputs "connect" to this one TV source in backend setup? And what about input groups and priorities? May be I'm near the solution but I need to be kicked by somebody who knows the MythTV philosophy of working with more TV cards...

Mrazek-  The only stupid question is the one you don't ask.  We are all here to assist each other.
You're requirements are fairly basic and are well addressed by Mythtv.
Firstly, ensure your graphics drivers are installed for your flavour of Mythbuntu,  you need to activate the restricted drivers for your card.

Then ensure the drivers for your tv cards are correctly installed, I use Kaffiene to check they are working as it is easy to set up and intuitive to use.
Once you know all your hardware is ok, you can then set up Mythv.

Start mythtv-setup and install the tv cards. If your hardware is set up correctly, you will see them appear in a drop-down box if using a mouse or use the right arrow key to select from the 10 card options the card(s) you have in your machine.

Then set up your video sources.  I haven't been able to get a definitive answer on whether it's best to set up a video source for each card or just one for identical cards from my research.  The safest way is to set up a separate source for each card, this works well for me  (even with identical cards, there can be minor revision changes of chips that can break things).
Be sure to name your sources with something relevant so you will remember what they are later.  During this step you can set up the EPG as well.

Next associate the input with a video source.  You scan for your channels in this setup area.

The folder and drive where you want to store your recordings is also critical.  The default for some weird reason known only to the developers is in /var/lib/mythtv.  You will need to change this if you don't want your O/S drive filled quickly with recordings.  When you do, ensure that mythtv and your user has R/W rights to whatever folder you choose.

After you've done this you should be able to view and record live tv.

Best of luck, Tony.

---

