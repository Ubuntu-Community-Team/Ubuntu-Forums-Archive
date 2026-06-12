---
title: "Kismet refuses to actually record GPS data, why?"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by dannysauer on 2012-04-27
So, I have a USB GPS unit (a Microsoft Streets and Trips serial unit that plugs into an included serial-USB adapter).  I plug this in to my Ubuntu system, and gpsd starts GPS'ing.  I can fire up cgps or xgps, and get a location.  GPSdrive also will show my location.  However, kismet is refusing to log any GPS data.

When I start the kismet server, it says
```
Logging data networks CSV XML weak cisco gps
Opened GPS connection to localhost port 2947
Listening on port 2501.
```

If I run gpsd in debug mode, I can see kismet disconnect when I exit the server.  I'm not sure why gpsd in the highest debug mode doesn't show an actual connect, but it doesn't show that with any other clients either.  You'd think that would be useful debugging information: "client connected".  Meh, I digress.

So, cgps before, during, and after kismet starts shows the GPS unit with a pretty accurate 3D lock.  Kismet connects to gpsd.  And the config file appears right:
```
sauer@trogdor:~$ sed -n 's/#.*$//;/gps/p' /etc/kismet/kismet.conf
gps=true
gpshost=localhost:2947
gpsmodelock=false
waypointdata=%h/.gpsdrive/way_kismet.txt
logtypes=dump,network,csv,xml,weak,cisco,gps
```

Yet, when I exit, it still says that it didn't log any GPS data, so it's deleting the log file.  It does this on both of my laptops, and does it both on oneric and, after upgrading last night (woo-hoo), it still does this on precise.  I did notice that enabling the gpsdrive waypoints makes the server not even create the gps log, but with that off, the gps log is created with the opening XML and then just never updated.

Anyone got any idea what super-secret config parameter or whatever I'm missing here?  Everything *looks* like it should be working.  I really need working GPS for my purposes (I'm walking around our facilities looking for rogue access points / auditing that the official points are actually working in the range as designed), and I hate using Windows tools. :)

I guess I should try BackTrack on a thumb drive just to eliminated software config / version oddities.  I'll follow-up either way. :)

---

### Post by dannysauer on 2012-05-03
No one else has GPS working with kismet either, eh? :)

---

