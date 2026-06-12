---
title: "Mythgame not naming many MAME Roms"
date: 2009-07-10
forum: Mythbuntu
---

### Post by fatal3rror on 2009-07-10
Hi guys,

I am running the version of mythtv and mythgame from the repo and I setup the romdb database so that I could see the long game names for my MAME roms.

The problem is that many of the roms remain unnamed.  I went to check the database manually for the names of the roms to see if they are there to find that they are present.

The way that I setup romdb was to download romdb-20051116-01.zip from [http://www.phaze.org/romdb/](http://www.phaze.org/romdb/) and I ran the included sql script.

I ran an in depth scan in mythgame after clearing the game data.

This resulted in many MAME roms that were named correctly but many that were not._[COLOR=black][/COLOR]_

I was wondering if any of you have had this problem and if you were able to fix it.

Thanks!

---

### Post by ian dobson on 2009-07-11
Hi,

What do you see in your frontend log file (/var/log/mythtv/mythfrontend.log)

I see messages along te lines of (when I do a deep scan):

```

2009-07-11 10:22:18.978 MythGame:GAMEHANDLER: Found Rom : (mane) - terracra.zip
2009-07-11 10:22:18.978 MythGame:GAMEHANDLER: Found Rom : (mane) - terracrae.zip
2009-07-11 10:22:18.978 MythGame:GAMEHANDLER: Found Rom : (mane) - terracre.zip
2009-07-11 10:22:18.978 MythGame:GAMEHANDLER: Found Rom : (mane) - terraf.zip
2009-07-11 10:22:18.979 MythGame:GAMEHANDLER: Found Rom : (mane) - terrafu.zip
2009-07-11 10:22:18.979 MythGame:GAMEHANDLER: Found Rom : (mane) - tfrceac.zip
2009-07-11 10:22:18.979 MythGame:GAMEHANDLER: Found Rom : (mane) - tfrceacj.zip
2009-07-11 10:22:18.979 MythGame:GAMEHANDLER: Found Rom : (mane) - tgmj.zip
2009-07-11 10:22:18.979 MythGame:GAMEHANDLER: Found Rom : (mane) - thndrx2.zip
2009-07-11 10:22:18.980 MythGame:GAMEHANDLER: Found Rom : (mane) - thunderl.zip
2009-07-11 10:22:18.980 MythGame:GAMEHANDLER: Found Rom : (mane) - thunderx.zip
2009-07-11 10:22:18.980 MythGame:GAMEHANDLER: Found Rom : (mane) - thundfox.zip
2009-07-11 10:22:18.980 MythGame:GAMEHANDLER: Found Rom : (mane) - tigerh.zip
2009-07-11 10:22:18.980 MythGame:GAMEHANDLER: Found Rom : (mane) - tigeroad.zip
2009-07-11 10:22:18.983 MythGame:GAMEHANDLER Error: No romDB data read from database. Not imported?
2009-07-11 10:22:19.048 MythGame:GAMEHANDLER: NO ROMDB FOUND for /mytharchive/MameROMS/1941.zip
2009-07-11 10:25:05.917 MythGame:GAMEHANDLER: Update gametype MAME

```

But I'm not seeing any games showing up in myth game. If your only finding some games then I imagine that the roms are not in the romDB.

Regards
Ian Dobson

---

