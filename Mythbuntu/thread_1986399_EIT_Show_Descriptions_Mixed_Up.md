---
title: "EIT Show Descriptions Mixed Up"
date: 2012-05-24
forum: Mythbuntu
---

### Post by km782 on 2012-05-24
I have had Mythtv 0.25 running on Mythbuntu 12.04 for a few weeks now.  I am getting my channel guide info via EIT.  My tuner card is the Hauppauge HVR-2250.

Up until 3-4 days ago all of the EIT information was correct.  However, now on two channels all of the titles are correct but some of the descriptions are wrong and matching up with the wrong shows.  For instance, the show that is on now has the description from yesterday’s show 24 hours ago and the description that should be for today is under the show playing tomorrow.  They aren’t all off 24 hours though.  Some might be 12 or any other number of hours.  It just really seems to be random.  There are some shows that also have the correct information.  As another example, there are two back to back episodes of Seinfeld on today.  One looks to have the correct description and the other has a description for the local news show.

I checked with my TV’s tuner and it is pulling in the correct descriptions over EIT.  That means it is something specific to Mythv or my box.  Does anyone know what could be causing this?  I’m wondering if something is off in the database.  Maybe if I am able to wipe out all of the guide data and have Mythtv redownload the data to populate the guide, that will fix it?  Is there a simple way to delete the existing guide data?  Thanks for the help.

---

### Post by dekarl on 2012-06-05
> **km782 said:**
> ... My tuner card is the Hauppauge HVR-2250.

Up until 3-4 days ago all of the EIT information was correct.  However, now on two channels all of the titles are correct but some of the descriptions are wrong and matching up with the wrong shows. ...

HVR-2250 sounds like ATSC in the US?
You might be seeing [http://code.mythtv.org/trac/ticket/10067](http://code.mythtv.org/trac/ticket/10067), notably "... has another unwanted side effect that leftover unmatched items from  earlier calls can be picked up as incorrect matches on later calls. This  will result in program descriptions being updated with descriptions  from other shows - a behavior I'm seeing, which is the whole reason I  started looking at EITHelper. "

I don't know what would help Stuart A. to test this issue (he's in a DVB country). But a backend log with "--verbose EIT" and a dump of PID 0x12 of the relevant multiplex (made with dvbsnoop or similar) might be useful.

Regards,
Karl

---

