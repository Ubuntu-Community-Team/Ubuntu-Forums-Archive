---
title: "mythtv shceduled shows not recorded?"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by mgame2k on 2008-01-13
I have Mythbuntu installed. I got everything at the moment that I want workng except for MYth.

I can watch tv. However, after shceduling some shows for a test run. They weren't recorded? Says failed next to them. 

Any ideas what I've done wrong?

---

### Post by Scorpuk on 2008-01-13
Not sure if this will help, but can you try the following:


Quit mythfrontend.


Start a terminal window

type mythfrontend

schedule the next available half hour show to start (something that is not already showing)

Once that show has finished quit mythfrontend and have a scroll through the terminal window to see if there are any errors. If you can tsee anything then post everything in the terminal window from when you typed mythfrontend.


As a general tip starting mythfrontend from a terminal window should allow you to troubleshoot as mythfrontend will fill the terminal window with information as to what it is doing. :)

---

