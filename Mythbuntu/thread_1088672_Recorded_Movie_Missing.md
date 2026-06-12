---
title: "Recorded Movie Missing"
date: 2009-03-06
forum: Mythbuntu
---

### Post by richwmn0 on 2009-03-06
I have installed MythBuntu 8.10 and sucessfully recorded 3 episodes of a show and one movie.  When I go to "Media Library" - "Watch Recordings" the movie does not show up (the 3 show episodes do), it does show up under "Manage Recordings" - "Previously Recorded" and on the "Recorded Programs" tab on MythWeb.  In addition there is a 8gig or so file in the recordings directory which corresponds to the date and time of the movie in question.  
How do I make it appear in "Watch Recordings"

Rich

---

### Post by klc5555 on 2009-03-06
> **richwmn0 said:**
> I have installed MythBuntu 8.10 and sucessfully recorded 3 episodes of a show and one movie.  When I go to "Media Library" - "Watch Recordings" the movie does not show up (the 3 show episodes do), it does show up under "Manage Recordings" - "Previously Recorded" and on the "Recorded Programs" tab on MythWeb.  In addition there is a 8gig or so file in the recordings directory which corresponds to the date and time of the movie in question.  
How do I make it appear in "Watch Recordings"

Rich



The database may believe (unlikely) that the recording was "livetv" rather than a scheduled recording. If so, the recording will be found in the livetv section of "autoexpire" list under "Information" --> "System Status", and can from that menu be moved to the "Default" group, whereupon it will appear in the "Watch Recordings" menu.  

If the database insists on believing that the recording doesn't exist when it does, or that it was deleted when it wasn't, often this is a little database burp that can be cured by a clean shutdown and restart. 

If, after these measures, the recording remains a complete mystery to your database, you can add it back into the database manually using the myth.rebuilddatabase.pl script in your /contrib directory. You may have to install some additional perl modules with the synaptic package manager to run this script, in particular libtimedate-perl, but if you then run the script while specifying the parameters  "--pass" with your MySQL installation's password and "--dir" with the directory your orphaned recording file is in, the script will find the recording, will find all available schedules information pertaining to it, will allow you to supply additional information if the defaults are not descriptive enough, and will index and commflag the recording for you while adding it into the database. 

Cheers! :)

---

### Post by boof1988 on 2009-03-06
> **klc5555 said:**
> The database may believe (unlikely) that the recording was "livetv" rather than a scheduled recording. If so, the recording will be found in the livetv section of "autoexpire" list under "Information" --> "System Status", and can from that menu be moved to the "Default" group, whereupon it will appear in the "Watch Recordings" menu.  

If the database insists on believing that the recording doesn't exist when it does, or that it was deleted when it wasn't, often this is a little database burp that can be cured by a clean shutdown and restart. 

If, after these measures, the recording remains a complete mystery to your database, you can add it back into the database manually using the myth.rebuilddatabase.pl script in your /contrib directory. You may have to install some additional perl modules with the synaptic package manager to run this script, in particular libtimedate-perl, but if you then run the script while specifying the parameters  "--pass" with your MySQL installation's password and "--dir" with the directory your orphaned recording file is in, the script will find the recording, will find all available schedules information pertaining to it, will allow you to supply additional information if the defaults are not descriptive enough, and will index and commflag the recording for you while adding it into the database. 

Cheers! :)

I am not trying to highjack this thread and I think this question relates to the thread topic.

I'm just getting a MythBox going and I had a similar problem with importing a DVD.  And I also want to copy my music collection to the music directory and then add it to the database.

Will myth.rebuilddatabase.pl add music (that is in the correctly specified directory) to the database as well?

---

### Post by newlinux on 2009-03-06
check the filter you have set on the watch recordings screen. It may be filtering out the movie. (I think you can press "m" to see and change the filter).

---

### Post by newlinux on 2009-03-06
> **boof1988 said:**
> I am not trying to highjack this thread and I think this question relates to the thread topic.

I'm just getting a MythBox going and I had a similar problem with importing a DVD.  And I also want to copy my music collection to the music directory and then add it to the database.

Will myth.rebuilddatabase.pl add music (that is in the correctly specified directory) to the database as well?

No it won't. But what music information do you want to add to the database? If it is just information about the music gotten mostly through id3 tags, if you copy the files over to your new music directory and scan it in myth that information will be built into the database again. If you want to move over playlists and such, then that will require some database work...

---

### Post by richwmn0 on 2009-03-06
> **newlinux said:**
> check the filter you have set on the watch recordings screen. It may be filtering out the movie. (I think you can press "m" to see and change the filter).

Thank you --
When I looked at the filter, it showed 4 items.  I changed it to live tv, saw 1 program, changed back to default group and the movie appeared.  Ghosts I guess. 
Thanks again.
Rich

---

