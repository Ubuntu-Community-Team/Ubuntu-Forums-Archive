---
title: "mythweather location not found"
date: 2008-03-17
forum: Mythbuntu
---

### Post by dragoster on 2008-03-17
I've updated to the new Myth 0.21 and everything is great except MythWeather. For some reason it cannot find my location, although it worked flawlessly in the previous version. I tried a bunch of different things

Boulder
Boulder, CO
80301 - 80309 

The only results for Colorado are Colorado Springs, CO and Colorado City, CA. I assume a source of locations is missing since not even Denver is on there.

How can I update the sources to be able to search US zip codes? Whatever the old MythWeather version was using was working great.

Thanks,
-D

---

### Post by volkswagner on 2008-03-17
Same problem Here in Port Ewen, NY

---

### Post by volkswagner on 2008-03-17
I guess the input method has changed.  I remember I used to be able to browse a list.

From wiki I was pointed here.  I checked out the list for NY and selected the nearest weather station on the list (four letter code).  Now I don't get the cool factor of showing my local town but I get accurate weather.  I don't know if this is the only way but, it solves mythweather from locking up.

[http://www.mythtv.org/wiki/index.php/MythWeather#Requirements]("http://www.mythtv.org/wiki/index.php/MythWeather#Requirements")


[http://www.weather.gov/data/current_obs/]("http://www.weather.gov/data/current_obs/")

---

### Post by kreegor on 2008-03-17
I have the same problem. I had it working fine with the previous version for local weather here in Australia but since the upgrade, Australia doesn't even appear in the list. Why do they have to change so much when it is upgraded? Surely the purpose of an upgrade is to keep the existing functionality but make it better.

---

### Post by dragoster on 2008-03-17
I've tried with no success the 4 letter code from NOAA (which is ironically located here in town). I assume we have to add a few sources to the database and get the xml parsing to work right. Any ideas on how to do that?

---

### Post by volkswagner on 2008-03-17
I am not sure where you got that code.  It should start with a "K'

Try this page and pick your nearest location(s)

[http://www.weather.gov/data/current_obs/seek.php?state=co&Find=Find]("http://www.weather.gov/data/current_obs/seek.php?state=co&Find=Find")

---

### Post by murbanci on 2008-03-20
Has anyone figured this out?  I'm having the same problem.  My city was there before the update, but now it cant be found.

---

### Post by dragoster on 2008-03-20
The KBJC code for the closest town where I live worked for some of the screens (current conditions, 18hr, 3 day, 6 day forecasts) but not for the others.

---

### Post by volkswagner on 2008-03-21
> **dragoster said:**
> The KBJC code for the closest town where I live worked for some of the screens (current conditions, 18hr, 3 day, 6 day forecasts) but not for the others.

What screens don't work?  The maps are handled by a different source I think.  For my setup, I was able to enter the nearest large city for the maps.  I was then offered a list to select.  This new setup takes a lot trial and error.

Here are the two different sources on my system.  All the weather screens I chose were NWS-XML.

HINT: Sometimes you may benefit entering a general direction in the search field.  When I enter "east" I get a large list to choose a map.

Source: ENVCAN-Animated-Map
Source: NWS-XML

Good Luck.  Post your success or errors.

---

