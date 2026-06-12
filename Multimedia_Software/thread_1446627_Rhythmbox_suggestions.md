---
title: "Rhythmbox suggestions?"
date: 2010-04-04
forum: Multimedia Software
---

### Post by MacHaddock on 2010-04-04
I want to be able to rate my rhythmbox songs with commands from anywhere.

Does anyone have any idea if there is a way of doing this?

---

### Post by stderr on 2010-04-04
There may be panel apps which can do this, and I would assume there are plugins for desktop-oriented widget sets such as gDesklets, etc., which can do this. However, since I don't use such things myself, I can't recommend any. 

Another way round this would be to hack up a little BASH script to do the job for you. Such a script could be easily integrated into... well, anything.

```
rhythmbox-client --print-playing-format "%at %aa %tt"
``` 

Shows you the currently playing Artist, Album and Track. You could hack up a bit of bash to locate a corresponding entry in rhythmbox's rhythmdb.xml (now located in ~/.local/share/rhythmbox/), perhaps using a CLI XML parser such as XMLstartlet. This is messy though, as you can't grab a definitive track ID from the rhythmbox-client app, so there may be multiple matching entries in rhythmdb.

Anyway, you can then use the XML parser to amend the rating tag. Here's the format of a song entry in rhythmdb.xml:

```
 
  <entry type="song">
**    <title>Against All Odds (Ft. Kano)</title>**
    <genre>Drum &amp; Bass</genre>
**    <artist>Chase &amp; Status</artist>**
**    <album>More Than Alot</album>**
    <track-number>3</track-number>
    <disc-number>1</disc-number>
    <duration>161</duration>
    <file-size>6472301</file-size>
    <location>file:///home/[PATH].mp3</location>
    <mtime>1230665762</mtime>
    <first-seen>1230677444</first-seen>
    <last-seen>1270378897</last-seen>
**    <rating>5</rating>**
    <play-count>2</play-count>
    <last-played>1268669940</last-played>
    <bitrate>320</bitrate>
    <date>733042</date>
    <mimetype>application/x-id3</mimetype>
    <mb-trackid></mb-trackid>
    <mb-artistid></mb-artistid>
    <mb-albumid></mb-albumid>
    <mb-albumartistid></mb-albumartistid>
    <mb-artistsortname></mb-artistsortname>
    <album-sortname></album-sortname>
  </entry>

```

If you're interested enough to try, feel free to ask for further assistance. But as I say, there are probably existing solutions out there.

---

### Post by Ferux on 2010-04-08
Check this site: [http://www.anandprakash.net/2009/02/26/change-rating-using-keyboard-in-rhythmbox/](http://www.anandprakash.net/2009/02/26/change-rating-using-keyboard-in-rhythmbox/)

The code which is printed there, can't be copy-pasted (you will get errors if you do so). I found the errors and changed the file (keep tabs in place!):
```

import dbus, sys



bus = dbus.SessionBus()



# Connect to player

proxy_obj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')

player = dbus.Interface(proxy_obj, 'org.gnome.Rhythmbox.Player')

rbshellobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Shell')

rbshell = dbus.Interface(rbshellobj, 'org.gnome.Rhythmbox.Shell')



def setRating(rating):

	currentsong = player.getPlayingUri();

	if currentsong is not None:

		rbshell.setSongProperty(currentsong, "rating",  dbus.Double(rating, variant_level=0))



try:

	if sys.argv[1] == "1":

		player.playPause(0)

	elif sys.argv[1] == "2":

		player.previous()

	elif sys.argv[1] == "3":

		player.next()

	elif sys.argv[1] == "4":

		setRating(1.0)
		player.next()

	elif sys.argv[1] == "5":

		setRating(5.0)

except dbus.exceptions.DBusException, (strerror):

	print "error: %s" % (strerror)

sys.exit(-1)

```

---

