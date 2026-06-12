---
title: "Help moving from WMC7 - Adding existing TV shows"
date: 2015-08-15
forum: Mythbuntu
---

### Post by penbrock on 2015-08-15
I am plunging in to MythTV again after hearing M$ is doing away with media center. I need some help getting it set up. Right now we use Plex to feed movies and TV shows. I mounted the movies directories and get them added to the \Video Gallery\. 

Now I need some help with all my recorded TV shows. Do I need to add them in to the video folders or is there a way to have 2 opetion, one for TV Shows, and another for Movies (Video Gallery works)

---

### Post by afremont on 2015-08-24
I'm glad that I'm not the only one that wants this.  I was considering writing a program or script of some kind to force feed the data into mythconverg so that the wmc recordings looked like they were done by mythtv.  I started looking into it and figured out some of the tables that I needed to load, but got sidetracked.  I have over 2000 WMC tv recordings that I would like to merge into the myth tv recordings NOT as videos.  It's a kodi thing and my wife is involved so it has to be seamless.  ;)

It looks like I can extract all the metadata straight from the WMC recording files and not have to pull it from WMC itself.  The problem is knowing what tables to load and which ones I can ignore (like I don't care about cross referencing the actors names etc)  I just want the basic information in the database such as series name, episode title, synopsis and maybe some of the dates.

I had made a previous post about it, but didn't get a lot of interest.  I did get a couple of suggestions, but ran into various issues with things and just moved on.

I'd like someone that's kind of an expert in the database to tell me what tables I absolutely have to load.  I think I can figure the rest out.  There's a bunch of tables in the database and I don't want to corrupt things.

---

### Post by penbrock on 2015-08-24
I got Mediaportal up and running on as a test. It had a plugin "MP-TVSeries" that all I had to do was point to my TV folder and it added everything just like my plex, pulls the descriptions, episode guides, and best of all it shows what episodes I'm missing and gives clickable licks to watch them from online streams (YouTube, Hulu, ect) I love it.
And "Moving Pictures" plugin does the same for movies. So now I have a menu item called TV Series, and one called Movies with every movie and show I have

---

### Post by afremont on 2015-08-24
That looks pretty cool, but only works on Windows.  That's not going to work for me.  I need to keep my front end box really light weight such as with a Raspberry Pi or Amazon Fire TV Stick, so I run Kodi on those.  I use MythTV just for a back end, but I would really like my old WMC TV recordings to seamlessly import into Myth as TV recordings.  I'm surprised that nobody has already created something to bridge this gap.

---

