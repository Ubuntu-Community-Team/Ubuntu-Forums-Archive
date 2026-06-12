---
title: "Mythbusters videos become named as Bamses billedbog 17"
date: 2012-07-07
forum: Mythbuntu
---

### Post by Korvar on 2012-07-07
I've got an odd one.

I record Mythbusters, and because I want to keep them, I periodically use [URL="http://www.mythtv.org/wiki/Mythlink.pl"]mythlink.pl
[/URL] to create human-readable links, then copy them to the videos folder.  

Anyway, *some* of the videos show up as "Bamses billedbog 17" instead of Mythbusters.  I edit the data in MythTV's front end, it looks okay, and then later I come back and it's all "Bamses billedbog 17" again.

Has anyone come across anything like this?

If it helps, here's a listing of my Mythbusters video directory.  All the ones without a timestamp in the filename have become "Bamses billedbog 17", the ones with timestamps never do.

```

Mythbusters - 2012-04-25, 7-00 PM - Lightning Strikes.mpg
Mythbusters - 2012-04-26, 7-00 PM - Stinky Car.mpg
Mythbusters - 2012-04-30, 7-00 PM - Chicken Gun.mpg
Mythbusters - 2012-05-01, 7-00 PM - Explosive Decompression.mpg
Mythbusters - 2012-05-02, 7-00 PM - Untitled.mpg
Mythbusters - 2012-05-03, 7-00 PM - Breakstep Bridge.mpg
Mythbusters - 2012-05-04, 7-08 PM - Buried in Concrete.mpg
Mythbusters - 2012-05-08, 7-00 PM - Myths Revisited.mpg
Mythbusters - 2012-05-09, 7-00 PM - Scuba Diver.mpg
Mythbusters - 2012-05-10, 7-00 PM - Ancient Death Ray.mpg
Mythbusters - 2012-05-11, 7-00 PM - Elevator of Death.mpg
Mythbusters - 2012-05-15, 7-00 PM - Quicksand.mpg
Mythbusters - 2012-05-16, 7-00 PM - Untitled.mpg
Mythbusters - 2012-05-18, 7-00 PM - Boom- Lift Catapult.mpg
Mythbusters - 2012-05-21, 7-00 PM - Bug Bomb.mpg
Mythbusters - 2012-05-22, 7-00 PM - Ming Dynasty Astronaut.mpg
Mythbusters - 2012-05-23, 7-00 PM - Brown Note.mpg
Mythbusters - 2012-05-24, 7-00 PM - Cement Mix- Up.mpg
Mythbusters_Archimedes Death Ray.mpg
Mythbusters - Border Slingshot.mpg
Mythbusters - Bulletproof Water.mpg
Mythbusters_Bullets Fired Up.mpg
Mythbusters_Cell Phones on Planes.mpg
Mythbusters - Chinese Invasion Alarm.mpg
Mythbusters - Confederate Rocket.mpg
Mythbusters - Escape Slide Parachute.mpg
Mythbusters_Franklin's Kite.mpg
Mythbusters_Helium Football.mpg
Mythbusters - Killer Brace Position.mpg
Mythbusters - Killer Tissue Box.mpg
Mythbusters - Mythbusters Revisited.mpg
Mythbusters_Paper Crossbow.mpg
Mythbusters_Seasickness- Kill or Cure.mpg
Mythbusters_Shredded Plane.mpg
Mythbusters_Steel Toe- Cap Amputation.mpg
Mythbusters_Vodka Myths.mpg

```

---

### Post by nickrout on 2012-07-08
your mythbusters episodes are not named with proper season and episode numbers and the myth therefore thinks they are movies. metadata is from themoviedb.org instead of thetvdb.com.

Compare:

[http://thetvdb.com/?tab=series&id=73388&lid=7](http://thetvdb.com/?tab=series&id=73388&lid=7)

(the series id is 73388)

then using that id on themoviedb.org:

[http://www.themoviedb.org/translate/movie/73388?language=en](http://www.themoviedb.org/translate/movie/73388?language=en) 

Fix your file naming.

---

### Post by Korvar on 2012-07-08
> **nickrout said:**
> your mythbusters episodes are not named with proper season and episode numbers and the myth therefore thinks they are movies. metadata is from themoviedb.org instead of thetvdb.com.


That's what it turned out to be.  Thanks.  Changed naming to:

```
Mythbusters - S01E09 - Lightning Strikes.mpg        Mythbusters - S03E15 - Killer Brace Position.mpg
Mythbusters - S01E10 - Stinky Car.mpg               Mythbusters - S03E16 - Bulletproof Water.mpg
Mythbusters - S01E12 - Chicken Gun.mpg              Mythbusters - S03E18 - Border Slingshot.mpg
Mythbusters - S01E13 - Explosive Decompression.mpg  Mythbusters - S03E19 - Killer Tissue Box.mpg
Mythbusters - S01E14 - Sinking Titanic.mpg          Mythbusters - S03E20 - Escape Slide Parachute.mpg
Mythbusters - S01E15 - Breakstep Bridge.mpg         Mythbusters - S03E21 - Mythbusters Revisited.mpg
Mythbusters - S01E16 - Buried in Concrete.mpg       Mythbusters - S03E22 - Chinese Invasion Alarm.mpg
Mythbusters - S02E01 - Myths Revisited.mpg          Mythbusters - S03E23 - Confederate Rocket.mpg
Mythbusters - S02E03 - Scuba Diver.mpg              Mythbusters - S03E24 - Vodka Myths.mpg
Mythbusters - S02E04 - Ancient Death Ray.mpg        Mythbusters - S03E25 - Steel Toe- Cap Amputation.mpg
Mythbusters - S02E05 - Elevator of Death.mpg        Mythbusters - S03E26 - Seasickness- Kill or Cure.mpg
Mythbusters - S02E07 - Quicksand.mpg                Mythbusters - S04E01 - Paper Crossbow.mpg
Mythbusters - S02E08 - Exploding Jawbraker.mpg      Mythbusters - S04E02 - Shredded Plane.mpg
Mythbusters - S02E10 - Boom- Lift Catapult.mpg      Mythbusters - S04E03 - Archimedes Death Ray Revisited.mpg
Mythbusters - S02E11 - Bug Bomb.mpg                 Mythbusters - S04E04 - Helium Football.mpg
Mythbusters - S02E12 - Ming Dynasty Astronaut.mpg   Mythbusters - S04E05 - Franklin's Kite.mpg
Mythbusters - S03E03 - Brown Note.mpg               Mythbusters - S04E06 - Cell Phones on Planes.mpg
Mythbusters - S03E04 - Cement Mix- Up.mpg           Mythbusters - S04E07 - Bullets Fired Up.mpg

```Reset details, and they're all now showing up properly.

Now all I have to do is find a way of getting the series and episode numbers automatically, as it doesn't appear to be in the EPG...

---

### Post by tgm4883 on 2012-07-08
> **Korvar said:**
> That's what it turned out to be.  Thanks.  Changed naming to:

```
Mythbusters - S01E09 - Lightning Strikes.mpg        Mythbusters - S03E15 - Killer Brace Position.mpg
Mythbusters - S01E10 - Stinky Car.mpg               Mythbusters - S03E16 - Bulletproof Water.mpg
Mythbusters - S01E12 - Chicken Gun.mpg              Mythbusters - S03E18 - Border Slingshot.mpg
Mythbusters - S01E13 - Explosive Decompression.mpg  Mythbusters - S03E19 - Killer Tissue Box.mpg
Mythbusters - S01E14 - Sinking Titanic.mpg          Mythbusters - S03E20 - Escape Slide Parachute.mpg
Mythbusters - S01E15 - Breakstep Bridge.mpg         Mythbusters - S03E21 - Mythbusters Revisited.mpg
Mythbusters - S01E16 - Buried in Concrete.mpg       Mythbusters - S03E22 - Chinese Invasion Alarm.mpg
Mythbusters - S02E01 - Myths Revisited.mpg          Mythbusters - S03E23 - Confederate Rocket.mpg
Mythbusters - S02E03 - Scuba Diver.mpg              Mythbusters - S03E24 - Vodka Myths.mpg
Mythbusters - S02E04 - Ancient Death Ray.mpg        Mythbusters - S03E25 - Steel Toe- Cap Amputation.mpg
Mythbusters - S02E05 - Elevator of Death.mpg        Mythbusters - S03E26 - Seasickness- Kill or Cure.mpg
Mythbusters - S02E07 - Quicksand.mpg                Mythbusters - S04E01 - Paper Crossbow.mpg
Mythbusters - S02E08 - Exploding Jawbraker.mpg      Mythbusters - S04E02 - Shredded Plane.mpg
Mythbusters - S02E10 - Boom- Lift Catapult.mpg      Mythbusters - S04E03 - Archimedes Death Ray Revisited.mpg
Mythbusters - S02E11 - Bug Bomb.mpg                 Mythbusters - S04E04 - Helium Football.mpg
Mythbusters - S02E12 - Ming Dynasty Astronaut.mpg   Mythbusters - S04E05 - Franklin's Kite.mpg
Mythbusters - S03E03 - Brown Note.mpg               Mythbusters - S04E06 - Cell Phones on Planes.mpg
Mythbusters - S03E04 - Cement Mix- Up.mpg           Mythbusters - S04E07 - Bullets Fired Up.mpg

```Reset details, and they're all now showing up properly.

Now all I have to do is find a way of getting the series and episode numbers automatically, as it doesn't appear to be in the EPG...

I believe if you put the inetref, season and episode number in your recording schedule, it will pull that information for future episodes of the program.

---

### Post by nickrout on 2012-07-08
> **tgm4883 said:**
> I believe if you put the inetref, season and episode number in your recording schedule, it will pull that information for future episodes of the program.How do you "put" them in your recording schedule?

---

### Post by tgm4883 on 2012-07-08
> **nickrout said:**
> How do you "put" them in your recording schedule?

If you are in the recording schedule in the frontend, then it is under metadata options. If you are in mythweb, it's under advanced options. I believe as long as the schedule has a season/episode (any season/episode) then that schedule is reflected as a tv show and uses ttvdb.

---

