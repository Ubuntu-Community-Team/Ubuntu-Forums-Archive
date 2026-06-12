---
title: "New Video Source - Data Direct lineup not working..."
date: 2011-11-30
forum: Mythbuntu
---

### Post by jpummill2 on 2011-11-30
I have used MythTV for years (knoppmyth, Mythdora, and now Mythbuntu).

I have just installed Mythbuntu (11.10) for the first time and I plan to use it with an HDHomeRun Prime that I also just purchased.

I am following the tutorial at the following web site:  
[http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime](http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime)

I have updated my "Schedules Direct" account by removing my old SD Cable lineup and creating a new Digital Cable (HD) lineup.

I then go to the MythTV backend setup and create a new video source by doing the following:  
  1)  Name the source "Cox Cable"
  2)  Set listings grabber to "North America (SchedulesDirect.org) (International)
  3)  Set the User Id to my user id.
  4)  Set the Password to my password.
  5)  Click the "Retrieve Lineup" button.

The "Retrieving Lineups" dialog box opens for a split second and then closes.

At this point, I expect the "Data Direct Lineup" edit box to contain my lineups by it is still empty.

I have tried this multiple times with the same results.  I have also removed the "Digital Cable" lineup on Schedules Direct and replaced it with the old "SD Cable Lineup" but I am still getting the same result.

It seems as though the "Retrieve Lineup" button isn't actually connecting and downloading lineups.

Where does the "Video Source" information get stored when downloaded?  Is this something that could be corrupted and if so how could I clean it?

Any insight that could get me past this issue would be much appreciated.

Thank you...

---

### Post by nickrout on 2011-12-01
> **jpummill2 said:**
> I have used MythTV for years (knoppmyth, Mythdora, and now Mythbuntu).

I have just installed Mythbuntu (11.10) for the first time and I plan to use it with an HDHomeRun Prime that I also just purchased.

I am following the tutorial at the following web site:  
[http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime](http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime)

I have updated my "Schedules Direct" account by removing my old SD Cable lineup and creating a new Digital Cable (HD) lineup.

I then go to the MythTV backend setup and create a new video source by doing the following:  
  1)  Name the source "Cox Cable"
  2)  Set listings grabber to "North America (SchedulesDirect.org) (International)
  3)  Set the User Id to my user id.
  4)  Set the Password to my password.
  5)  Click the "Retrieve Lineup" button.

The "Retrieving Lineups" dialog box opens for a split second and then closes.

At this point, I expect the "Data Direct Lineup" edit box to contain my lineups by it is still empty.

I have tried this multiple times with the same results.  I have also removed the "Digital Cable" lineup on Schedules Direct and replaced it with the old "SD Cable Lineup" but I am still getting the same result.

It seems as though the "Retrieve Lineup" button isn't actually connecting and downloading lineups.

Where does the "Video Source" information get stored when downloaded?  Is this something that could be corrupted and if so how could I clean it?

Any insight that could get me past this issue would be much appreciated.

Thank you...


Well my suggestions - loook at your log files, or go to the mailing list. there are lots of shedules direct experts there.

---

### Post by jpummill2 on 2011-12-01
Thank you for the suggestion.

Not sure why this helped but I was able to fix the issue by changing my password on the Schedules Direct website.  I went from a 6 character/digit password to one  that was larger and the MythTV Video Source was able to connect and download the lineup.

Weird...

---

