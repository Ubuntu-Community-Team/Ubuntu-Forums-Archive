---
title: "Mythbuntu on HP Media Center M7640N"
date: 2008-03-05
forum: Mythbuntu
---

### Post by quinnanya on 2008-03-05
I'm completely new to Linux and Mythbuntu. I've read through all the instructions I could find, but I'm still sorta stuck. I'm sorry if I'm missing something obvious...

I installed Mythbuntu on top of an existing Gutsy for a Backend/Frontend/Desktop setup, having killed off Windows for good. I have an[ HP Pavilion Media Center TV M7640N]("http://www.amazon.com/Pavilion-Desktop-Dual-Core-Processor-SuperMulti/dp/tech-data/B000ITOKRM/ref=de_a_smtd"), which has a built-in tuner. When I go to Capture Card Setup, the Probed info gives me "Hauppauge WinTV PVR-150". I set card type to MPEG-2 Encoder Card, and left the rest of the settings as the default. I also signed up for SchedulesDirect and added the username/password under the "video source" section. 

When I try to go into Channel Scanner, though, and use the Channel Scanner, it gives me blank pull-downs for Video Source and Capture Card, and says "Failed to open the card".

When I go into the frontend and try to watch TV, it just gives me either a black screen (Tuner 1 selected) or "MythTV is already using all available inputs for the channel you selected..." (Any other setting selected).

Any suggestions for how to fix the settings would be a big help. Thanks!

---

### Post by volkswagner on 2008-03-06
Steps for setting up your card.  1. New capture card, looks like you got this.  2. New video source (you should have already logged into schedules direct and set up a lineup), select grab listings.  Keep your eye on the field for starting channel.  It should automaticaly fill in the lowest channel in your lineup.  This also lets you know it is finished downloading.  If it does't there is a possible problem, or the field was already correct.  3. New input connection, if you are connecting direct to cable or antenna select TV 1.  You should now be able to select the source previously set up.  Now select scan>full scan. 
I hope I did not forget anything.  You should now be able to exit the backend setup and select OK to run mythfilldatabase.  This should take some time.  You should now be able to use card

---

### Post by quinnanya on 2008-03-07
Thanks for your help! One more strange thing has happened, though: when I had it search for channels, only a handful came up, and the only one that actually showed up was channel 4. I have a digital cable box, whose base channel is 4. I tried putting that in "external channel change command", but that just gives me static everywhere,  and in "preset tuner to channel", which similarly lets me see channel 4 but nothing else. The only way I can change channels is using the cable box's own remote, but Mythbuntu doesn't seem to be able to do it, which is causing some problem for recording. Any suggestions for how to fix it?

---

### Post by volkswagner on 2008-03-07
Please supply more detail.  If you are trying to capture from your cablebox, this is a more complex setup.  Are you using coax connection, svid, or composite.  You will need a way to change the channels on the box.  An IR blaster or possibly firewire will work (if your box has an active one).  Look here for more info.

Here is your bible for MYTH [http://www.mythtv.org/wiki/index.php/Category:HOWTO]("http://www.mythtv.org/wiki/index.php/Category:HOWTO")

connecting a cable box
[URL="http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat"]
http://www.mythtv.org/wiki/index.php/Connecting_Tuner_Card_To_Cable_Sat[/URL]



What is your cable box model?

Good luck

---

### Post by paddydd on 2008-03-23
Thanks Volkswagner for your help.

---

