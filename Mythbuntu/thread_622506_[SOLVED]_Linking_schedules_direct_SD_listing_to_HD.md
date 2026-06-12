---
title: "[SOLVED] Linking schedules direct SD listing to HD?"
date: 2007-11-24
forum: Mythbuntu
---

### Post by Cryophallion on 2007-11-24
So, I am taking over a 2nd hand myth box with a  hauppage 250 card, and am adding in a pchdtv 5500 card so I can also get the digital channels (I use extended cable with no cable box, so I can get hd channels over the cable unencrypted).
So, here is my question. Is there a way to duplicate the sd listings for the hd versions of the channels? For example, I want to record the hd version of a cbs show, but hd isn't supported by schedules direct. Can you link the data from the sd to the hd guide so they both show the same thing?

Thanks in advance.

Cryo

---

### Post by ubnewbie2 on 2007-11-24
> **Cryophallion said:**
> So, I am taking over a 2nd hand myth box with a  hauppage 250 card, and am adding in a pchdtv 5500 card so I can also get the digital channels (I use extended cable with no cable box, so I can get hd channels over the cable unencrypted).
So, here is my question. Is there a way to duplicate the sd listings for the hd versions of the channels? For example, I want to record the hd version of a cbs show, but hd isn't supported by schedules direct. Can you link the data from the sd to the hd guide so they both show the same thing?

Thanks in advance.

Cryo

I am using XMLTV listings from Oztivo, but I  do what you are describing, simply by putting the XMLID of the SD channel, into the HD Channel entry as well (this is in the back-end config - mythtv-setup).

---

### Post by superm1 on 2007-11-25
> **Cryophallion said:**
> So, I am taking over a 2nd hand myth box with a  hauppage 250 card, and am adding in a pchdtv 5500 card so I can also get the digital channels (I use extended cable with no cable box, so I can get hd channels over the cable unencrypted).
So, here is my question. Is there a way to duplicate the sd listings for the hd versions of the channels? For example, I want to record the hd version of a cbs show, but hd isn't supported by schedules direct. Can you link the data from the sd to the hd guide so they both show the same thing?

Thanks in advance.

Cryo

HD is supported by schedules direct generally.  Check the Antenna line up or the digital cable line up.

---

### Post by Cryophallion on 2007-11-27
> **superm1 said:**
> HD is supported by schedules direct generally.  Check the Antenna line up or the digital cable line up.

And it worked. Although now I have a problem with the number sorting properly, but that is for another thread.

For anyone else looking to do this:

For cable (Comcast specifically here) with no box, I used standard cable listings for SD cable, and then used broadcast for HD, then scanned for channels for HD (qam256 here). The Digital cable did not give me proper listings for the HD channels, and the channel numbers ended up being the same as for broadcast (the stations actual number, not necessarily the channel cable has it set to).

However, changing the channel numbers didn't change the sort order, but that will be a new thread question.

Thanks for all your help.

---

### Post by road2elysium on 2007-11-27
> **Cryophallion said:**
> And it worked. Although now I have a problem with the number sorting properly, but that is for another thread.

For anyone else looking to do this:

For cable (Comcast specifically here) with no box, I used standard cable listings for SD cable, and then used broadcast for HD, then scanned for channels for HD (qam256 here). The Digital cable did not give me proper listings for the HD channels, and the channel numbers ended up being the same as for broadcast (the stations actual number, not necessarily the channel cable has it set to).

However, changing the channel numbers didn't change the sort order, but that will be a new thread question.

Thanks for all your help.

I just set up my PCHDTV-5500 a couple nights ago to replace my PVR-150.  I'm using ATSC/ClearQAM256 from a cable line.

Importing via Schedules Direct Analog Cable/Digital Cable didn't grab TV Guide Data or channels like it had previously for my PVR-150/analog.  So I resorted to doing a Cable-High Channel Scan and manually using the Frontend Channel Editor to input XMLTV IDs.  Running mythfilldatabase after this successfully grabbed the TV Guide Data.

Here are some links to check out:

[http://www.mythtv.org/wiki/index.php/Frontend_Channel_Editor]("http://www.mythtv.org/wiki/index.php/Frontend_Channel_Editor")
[http://www.mythtv.org/wiki/index.php/XMLTV_ID]("http://www.mythtv.org/wiki/index.php/XMLTV_ID")

---

