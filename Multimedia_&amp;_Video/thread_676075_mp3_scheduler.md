---
title: "mp3 scheduler??"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by jperreault on 2008-01-23
Any suggestions please. 

I'm an absolute beginner in Linux, so if I ask something silly please forgive me.  

Our church chime system recently blew out it's pre-amp.  The cost to repair a chime system that is already 20+ years old was out of the question. The system is basically a clock that plays 1/4" cartridges at pre-programmed intervals. In addition the user can select the number of chimes it plays from 1 to 5 chimes or continuous mode.  The primary reason for not wanting to fix the existing unit was that the media it plays is wearing out and there are no replacements cartridges available.  In fact the company that originally produced the product no longer carries the cartridges, so we decided we wanted something a little more solid state and less analog. 

For this reason we choose the Asus EEE pc. It's cheap, solidstate with no moving parts and was more than adequate for our needs. The only thing wrong with it was the fisher price distribution of Linux it shipped with.   I have since converted it with XUBUNTU 7.10.  I used the eeeXUBUNTU distribution to get the laptop fully functional. The problem is that the laptop would be sitting in a steel case rendering the build in wireless adapter inadequate for our needs.  I decided add an external wireless USB adapter, and went with the Belkin Wireless G USB adapter.   A little fiddelling and a lot of reading I found a site that helped me install the drivers for the Belkin adapter w/o using ndwrapper. 

I have the music I need encoded (mp3) on a memory card that xubuntu recognizes as a FAT32 partition.  



What we  need is an application that can:

1] Check the current local time on the internet.  
2]  Play a select # of MP3 (predetermined by the end user) at specific times on specific days. 

What I would like is something that I can have it select from three different categories of MP3.
Gospel
Christmas
Patriotic

Christmas Music After November 12th to January 8th.  
Gospel Music from January 9th - until November 11th.   
Patriotic mp3 on Canada Day,  July 1st.  

 It would be nice it we could have it pick random mp3 from the appropriate folders, but sequential would also do.  

Most of the schedule is pretty repetitive except for Sundays,  & Christmas.   The only difference would be Sundays I need the chimes to start approx 20 Minutes earlier so they don't go off during  the actual service as they presently do. 

I had a momentary lapse of weakness and went to the "Dark Side" (Windows XP) but with a 4 Gig  hard drive. Updating XP  sucked the life out of the hard drive.  The XP initial Load was 1.7 Gigs then all the updates took XP up to 3.2 Gigs - after stripping out all the unnecessary applications, example files and other miscellaneous useless tools.  I had the system working with XP, WinAMP and a plug in (scheduler).  The problem is the scheduler plugin treated each day the same and often fire during Sunday Service.... Causing me no end of embarrassment.  

Suggestions would be GREATLY appreciated.

Thank you,
[email]james_perreault@hotmail.com[/email]

---

### Post by stalker145 on 2008-01-23
For the absolute most basic way of doing this, you *could* run a bunch of cron jobs to get the files played. I'm not sure if you could get any randomization going this route, but you could definitely play music at set intervals.

Hopefully someone with a better idea comes along. I just thought I'd throw an idea in there to get you started.

---

### Post by jperreault on 2008-01-23
Thanks... 

I will look up the command and syntax.   I also need to lean how to wire batch files.  


Slowly but surely I'll get there....




Some times it feels like I graduated from the Flat Forehead Engineering Association... (Insert Picture of head hitting CRT Here)....


:0)
James


One of the quotes I heard and absolutely loved was...
"Some people are like Slinkies  
Totally useless but still fun to watch when you push them down a flight of stairs."

---

### Post by jperreault on 2008-01-24
Anyone use orage?  I've set the scheduler to fire off... But the audio portion fails to play.  This would be the ideal application if I could get the audio working.  Other applications with audio work fine.


James

---

