---
title: "Input groups, with dual tuner card (Nova-T 500)"
date: 2008-05-04
forum: Mythbuntu
---

### Post by davewantsmoore on 2008-05-04
Hi.  Getting started with Mythbuntu 8.04, and am quite impressed.

I have a Nova-T 500 (single card with dual DVB tuners) but am finding LiveTV slightly awkward to use.

While one tuner is recording, only its currently tuned channel(s) is available to view... and to access channels on the other (idle) tuner, I must press MENU, Change Input, and chose the idle tuner.

Is this the correct behavior for MythTV?  I would 'expect' that the available channels across BOTH tuners would be available in a single channel list.


...I suspect I do not correctly understand 'Input Groups'.

The defaults (which I have not altered) for each tuner are:

1st tuner:
Input Group 1:  DVB0
Input Group 2:  Generic

2nd tuner:
Input Group 1:  DVB1
Input Group 2:  Generic



Is this correct?  Can someone explain to me how 'Input Groups' work in my situation?!

Many thanks.

---

### Post by volkswagner on 2008-05-04
To avoid conflicts input group one should have the same name.  This way the machine "knows" they share a source.

---

### Post by davewantsmoore on 2008-05-04
thanks volkswagner - I set up my groups as:

1st tuner
Input Group 1:  DVB1
Input Group 2:  Generic

2nd Tuner
Input Group 1:  DVB1
Input Group 2:  Generic

I still have the same problem as before.  Can you give more detail on how I should configure the groups please?!
(EDIT:  I also tried Group1 = DV1 / Group2 = DVB0)



Another example (just to clarify):

Tuner 1 is already recording on channel X
Tuner 2 is already recording on channel Y

When I start LiveTV, I can see the channel (or multiple channels if it's a DVB multiplex)  coming from Tuner 1.   To see the channel(s) from tuner 2, I must press MENU, Change Input, and select Tuner 2.

Should I have to manually change between tuners like this???... or is there a way to have all the available channels (from all tuners) in a single list.

---

I found an option "Avoid conflicts with live TV and recordings"...

This fixed the situation where one tuner is already recording and LiveTV starts - Now LiveTV will automatically start on the tuner that is not recording - GOOD

However it doesn't solve the problem where BOTH tuners are recording and I start live TV.   I'd like to be able to see all the available channels from both tuners (sometimes there are MANY, depending on the multiplexing) in a single list.

---

Perhaps I'm trying to make LiveTV do something it's not supposed to ?!!?

How does everyone else with multiple tuners, and DVB multiplexes (containing multiple channels) manage this?!


Thanks for reading :-p

---

