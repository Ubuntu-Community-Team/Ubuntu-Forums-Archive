---
title: "Introspect error: The name org.gajim.dbus was not provided by any .service files"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by joris1977 on 2006-09-29
Introspect error: The name org.gajim.dbus was not provided by any .service files

is the error that the terminal gives me when i run quod libet. It refuses to play audio files.  Other audio players seem to be broke as well. (although mplayer seems to work fine; could it be a gstreamer problem?) It used to work fine, I´m not sure what made it break I´ve been insytalling tovid and firefox. I renember i updated a python. Any ideas how to solve this??

greetings

Joris

---

### Post by hugmenot on 2006-09-29
This is not related to playing audio. The error comes from the Gajim status message plugin and is harmless.
If playback doesn&#8217;t work it is due to something else.

---

### Post by joris1977 on 2006-10-01
Thanks Hugmenot for helping out again. Will no longer not try to longer solve the issue with the Gajim pluging. Hope i will find a way to get play back working again.

edit: it was  simple. just under system-preferences-multimedia systems selector - audio and then change the output plugin to alsa mixer....

Don't know how it changed, glad i saw someone suggesting this somewhere on the forums.](*,)

---

### Post by hugmenot on 2006-10-01
If you want the error message gone drop the attached file into /etc/dbus/system.d.
You need to gunzip it first and replace "username" with your actual username.
There will still be errors displayed if Gajim isn&#8217;t running but none if it is.

---

