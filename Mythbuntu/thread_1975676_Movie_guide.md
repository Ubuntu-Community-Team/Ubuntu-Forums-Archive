---
title: "Movie guide"
date: 2012-05-07
forum: Mythbuntu
---

### Post by CaptainSEO on 2012-05-07
I'm thinking of dumping Windows Media Centre and using Mythbuntu.

There are two features of 7MC I really don't want to loose, so are he following available in Mythbuntu?

**Movie guide**. The movie guide in 7MC shows all films coming in the next 2 weeks and is brilliant.

**Recorded TV HD**. This is a plug-in that separates recorded TV shows and films so that they can be viewed separately - not all mixed in together. Is there a way to do this with Mythbuntu?

---

### Post by thatguruguy on 2012-05-07
> **CaptainSEO said:**
> 
**Movie guide**. The movie guide in 7MC shows all films coming in the next 2 weeks and is brilliant.
I have my MythTV set up to automatically pull the next 2 weeks worth of TV listings from [Schedules Direct]("http://www.schedulesdirect.org/"), and it pulls the information daily.  MythTV shows how ever much data you have available, and color-codes for drama, comedy, musicals, etc.  You can also do a search if you think a particular movie is coming on in the next 2 weeks.  I haven't used Win7MC, but MythTV gives me the information I need.

> **CaptainSEO said:**
> **Recorded TV HD**. This is a plug-in that separates recorded TV shows and films so that they can be viewed separately - not all mixed in together. Is there a way to do this with Mythbuntu?

I don't know what anyone else does, but I transcode just about everything and move it into my "Videos" section.  The Videos section can be viewed flat (everything viewed together) or separated into logical chunks (e.g., movies and TV shows separately, with TV shows subdivided further into seasons).

---

### Post by nickrout on 2012-05-08
> **CaptainSEO said:**
> I'm thinking of dumping Windows Media Centre and using Mythbuntu.

There are two features of 7MC I really don't want to loose, so are he following available in Mythbuntu?

**Movie guide**. The movie guide in 7MC shows all films coming in the next 2 weeks and is brilliant.

**Recorded TV HD**. This is a plug-in that separates recorded TV shows and films so that they can be viewed separately - not all mixed in together. Is there a way to do this with Mythbuntu?

Mythweb (which allows you to do a lot of mythtv control via a web browser) has some canned searches which includes a movie search. Here is the list on my 0.24 system:

    * New Titles, Premieres
    * Movies
    * Movies, 3½ Stars or more
    * Movies, Stinkers (2 Stars or less)
    * Children's Movies
    * Non-Series HDTV
    * All HDTV
    * Non-Music Specials
    * Music Specials
    * Science Fiction Movies


Of course this all depends on the quality of your EPG data, if you are in the US you will use schedules direct and their data quality seems excellent from all reports.

---

### Post by tgm4883 on 2012-05-09
> **CaptainSEO said:**
> I'm thinking of dumping Windows Media Centre and using Mythbuntu.

There are two features of 7MC I really don't want to loose, so are he following available in Mythbuntu?

**Movie guide**. The movie guide in 7MC shows all films coming in the next 2 weeks and is brilliant.


MythTV does this in what is called search lists. Go into "Manage Recordings > Schedule Recordings > Search Lists" and choose Movies. It will show everything in the next two weeks that is a Movie.

> **CaptainSEO said:**
> 
**Recorded TV HD**. This is a plug-in that separates recorded TV shows and films so that they can be viewed separately - not all mixed in together. Is there a way to do this with Mythbuntu?

Recorded Content is all lumped together. You can do as a previous poster suggested and move the content into the movie section. You could also change the recording group you use for movies, and have then choose which group you are viewing when you are looking at the recorded content.

---

