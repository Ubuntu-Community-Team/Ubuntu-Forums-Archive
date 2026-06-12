---
title: "Bug or not, lineup data can add not subtract."
date: 2008-04-10
forum: Mythbuntu
---

### Post by volkswagner on 2008-04-10
I have pinpointed an annoyance with mythtv updating channel lineup.

I can log into Schedules Direct and add channels to an existing lineup via there own editor.  I then can go to mythbacken-setup and fetch lineup with the newly added channels.  This can be confirmed in channel editor.

I can log into SD and delete channels from an existing lineup.  When I fetch lineup in BE-setup the old channels are still in channel editor.  This is true even after mythfilldatabase.

My work around:[LIST=1]
[*]Delete the lineup
[*]Log into SD and edit lineup
[*]Create the same lineup again in BE-setup
[*]Apply source to input connections
[*]Verify lineup in Channel editor

[/LIST]

So, Bug or user error?
I believe this was also true in .20.  I am now running .21.  Shall I file a bug report?

---

### Post by grytpype on 2008-04-11
What I usually do is delete the channel from the MythTV lineup (I use MythWeb for that, to avoid having to run MythSetup), then log on to SD, edit the lineup and manually delete that same channel.  

Once you delete the channel on both the MythTV box and in the SD lineup, it doesn't come back.

---

