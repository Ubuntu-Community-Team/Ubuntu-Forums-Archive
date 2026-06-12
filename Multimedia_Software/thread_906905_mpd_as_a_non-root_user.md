---
title: "mpd as a non-root user"
date: 2008-08-31
forum: Multimedia Software
---

### Post by inspiteofmyself on 2008-08-31
i cannot get this to work. i installed mpd from the ubuntu repositories, and configured it to use pulseaudio as its output. if i run it as the root user it works flawlessly, if i run it as "mpd" it gets "connection refused" from the pulseaudio daemon.

i added "mpd" to the pulse-access and pulse-rt groups, but get the same result.

can someone help me get this resolved? id really like to stop running mpd as the root user :(

---

### Post by treehouse on 2008-09-04
You should be able to edit the line in ~/.mpdconf like so:

```

######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "this_is_your_user_name"
#
# The address and port to listen on.
#
bind_to_address                 "127.0.0.1"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################

```

however, for some reason on my machine it wasn't loading the configuration from here, so I had to edit /etc/mpd.conf the same way as well


change the user to your username, reboot X, and see how you're sitting.

---

