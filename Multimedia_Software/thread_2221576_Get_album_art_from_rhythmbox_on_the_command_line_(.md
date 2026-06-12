---
title: "Get album art from rhythmbox on the command line (conky)"
date: 2014-05-02
forum: Multimedia Software
---

### Post by pieroxy on 2014-05-02
Hello there. I'm looking for a way to extract my currently playing album cover art (that's for my conky).

I've found a few things here and there all advocating the same thing: Covers are in /home/USER/.cache/rhythmbox/covers/ARTIST - ALBUM.jpg.

The thing is it doesn't look like they are there anymore. I can see a folder at /home/USER/.cache/rhythmbox/album-art (notice the difference already), but the files are named 000000, 000001, etc and there's a store.tbd file along with this. But the currently playing album cover art seems to be in there.

Does anyone has any idea?

---

### Post by kostkon on 2014-05-02
You can always use D-Bus calls to get the album art. Rhythmbox (and many other players, including the linux version of the Spotify desktop client) implement the [MPRIS interface]("http://specifications.freedesktop.org/mpris-spec/latest/"). So you can create something that will be player agnostic.

---

### Post by pieroxy on 2014-05-03
Thanks for the tip. I have tried a few tutos out there, with the same results:

A) When I try a simple program :

```
#! /usr/bin/env python
import dbus

session_bus = dbus.SessionBus()

proxy_obj = session_bus.get_object(
    'org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')

player = dbus.Interface(proxy_obj, 'org.gnome.Rhythmbox.Player')

print player.getPlayingUri()

```

I always get the following exception:
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Rhythmbox was not provided by any .service files

B) conkyRhythmbox.py always gives me Unknown (or 0) no matter what datatype i put in...

Any idea? I've tried this with rhythmbox playing, paused, stopped, closed to no avail... rhythmbox-client works fine and gives me (almost) everything I need. (just the cover art is missing)

---

### Post by kostkon on 2014-05-03
Yeah, that does not work. You need to use a different interface to get the mpris metadata from Rhythmbox. And the object path you used for Rhythmbox is wrong. Anyway, the following code should do it:
```
sb = dbus.SessionBus()

rb_obj = sb.get_object("org.mpris.MediaPlayer2.rhythmbox", "/org/mpris/MediaPlayer2")

props_int = dbus.Interface(rb_obj, "org.freedesktop.DBus.Properties")

rb_meta_dict = props_int.Get("org.mpris.MediaPlayer2.Player", "Metadata")

title = rb_meta_dict["xesam:title"]
artists = ", ".join(rb_meta_dict["xesam:artist"]) # track can have more than one artist apparently
album = rb_meta_dict["xesam:album"]
cover_art_url = meta_dict["mpris:artUrl"]
# etc...
```

By doing the above you are getting the metadata dict that contains all the info for the current track (and thus you don't really need to use rhythmbox-client at all.) The full list of the metadata items can be found [here]("http://www.freedesktop.org/wiki/Specifications/mpris-spec/metadata/"). Beware that some values are dbus arrays and you should handle them accordingly like I've done for the artists above.

Hope that helps.

---

### Post by pieroxy on 2014-05-04
No no no no no, it doesn't help. IT ROCKS!

Thanks man, one less problem to solve today.

---

