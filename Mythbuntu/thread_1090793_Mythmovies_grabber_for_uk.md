---
title: "Mythmovies grabber for uk"
date: 2009-03-08
forum: Mythbuntu
---

### Post by gilhooley on 2009-03-08
I wanted to get MythMovies working for the UK, so I googled, and found [this]("http://www.gossamer-threads.com/lists/mythtv/users/316916") which pulls the movie times from Google's movie search thing.
Unfortunately, it looks like Google have changed their format slightly since this was written, so the grabber no longer works.
Attached is an updated version which works for me on 8.10 with my postcode in the UK.
I'm not sure if it works elsewhere in the world - try using the Google movies search at [http://www.google.com/movies]("http://www.google.com/movies"), and cut-n-paste whatever URL works best for you into the [FONT="Courier New"]$googleurl[/FONT] variable.

---

### Post by TheHolm on 2009-05-05
BTW. It is works fine for other countries. 
And you can use location name instead of poscode.  "Do not forgot about quotation marks" 
"Sydney, NSW, Australia" works just fine.

---

### Post by jtroybailey on 2009-05-18
Hi Guys,

I haven't been able to get this working properly. It works in the cl though not in mythmovie itslef, says 'Failed to process the grabber data!' I have tried different versions by different people and they all do the same, i have reinstalled mythmovies.

What do you think?

Thanks, Jamie

---

### Post by pau1mi11er on 2009-05-18
I had a look at this and as far as I can see there needs to be a little bit of altering in the script.

It looks like it does not parse the postcode you state in the settings at all and it needs to be put into the script manually.

Looking at it from memory, there is something in the google url that ends in "[Postcode]". You need to put your postcode here with no spaces.

Running the command with %z as a parameter does no harm but is probably completely pointless. A later version, I suspect, will pick up this parameter but this has not been implemented by the writer yet.

Anyway, this is what I did to get it working (still need to sort out running times, rating and image but the guts of it works fine).

Paul:popcorn:

---

### Post by SiHa on 2009-05-19
+1 to the above. I had to hardcode the postcode just as stated, and the script works beautifully now.

---

### Post by beerguzzler on 2009-09-26
Deleted post, wrong thread!

---

### Post by jontywareing on 2009-10-18
Just thought you'd like to know that I've been maintaining/rewriting this script for some time now, it used to have new versions posted into mythtv trac but I've now put it up on github so it's easy to find and fork.

[http://github.com/Jonty/Googlemovies...ooglemovies.pl]("http://github.com/Jonty/Googlemovies/blob/master/googlemovies.pl")

Feel free to push changes back to me, I'll endeavour to merge them as quickly as possible.

Hope that helps someone,
--jonty

---

### Post by SiHa on 2009-10-18
Cheers! Will give it a go when I get some time.

---

