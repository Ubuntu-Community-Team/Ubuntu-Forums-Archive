---
title: "Sound set-up for broadcasting."
date: 2012-03-31
forum: Multimedia Software
---

### Post by acimi66 on 2012-03-31
Hi guys,
I'm pretty new to Linux and I have NEVER been able to get my broadcasting set-up CONSISTENTLY. I have been able to make broadcasts but the next time I go to do it I have sound issues ( mic not been heard) or connection issues ( sound OK but not broadcasting to the server). I realize I could have two or even three different problems, but the bottom line is it's driving me crazy.
I need help.
      the info; Ubuntu 11.10 with Internet DJ console + JACK connecting to an ICECAST2 server.
through terminal I get this:
~$ idjc ls

(idjcgui.py:9334): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(idjcgui.py:9334): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(idjcgui.py:9334): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(idjcgui.py:9334): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Internet DJ Console Version 0.8.5
Copyright 2005-2011 Stephen Fairchild
Released under the GNU General Public License V2.0

Language translation: en_US
jack client IDs: idjc-mx idjc-sc
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
Cannot lock down memory area (Cannot allocate memory)
Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
AcquireSelfRealTime error
Cannot lock down memory area (Cannot allocate memory)
JACK ERROR MESSAGE: Cannot use real-time scheduling (RR/5)(1: Operation not permitted)
JACK ERROR MESSAGE: JackClient::AcquireSelfRealTime error
shout_initialiser: shout_init called
jack error: Cannot lock down memory area (Cannot allocate memory)
jack error: Cannot use real-time scheduling (RR/5)(1: Operation not permitted)
jack error: JackClient::AcquireSelfRealTime error
started 1 encoders, 1 streamers, 2 recorders
threads initialised
jack sample rate is 48000
activated mic 1
Unknown destination port in attempted (dis)connection src_name [idjc-mx:dsp_out_l] dst_name [jamin:in_L]
Unknown destination port in attempted (dis)connection src_name [idjc-mx:dsp_out_r] dst_name [jamin:in_R]
Unknown source port in attempted (dis)connection src_name [jamin:out_L] dst_name [idjc-mx:dsp_in_l]
Unknown source port in attempted (dis)connection src_name [jamin:out_R] dst_name [idjc-mx:dsp_in_r]
Restoring previous session
Toggle OFF recieved for signal: Listen
namedtuple_PlayerRow:15: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
stream-mon was toggled ON
Metadata source was changed. Before: 3
Metadata source was changed. Now: 2
failed to get server stats for [http://host.acimi.com:8001/stream](http://host.acimi.com:8001/stream)
failed to get server stats for [http://host.acimi.com:8001/stream](http://host.acimi.com:8001/stream)
failed to get server stats for [http://host.acimi.com:8001/stream](http://host.acimi.com:8001/stream)
failed to get server stats for [http://host.acimi.com:8001/stream](http://host.acimi.com:8001/stream)
failed to get server stats for [http://host.acimi.com:8001/stream](http://host.acimi.com:8001/stream)
^CMixer got ^C interrupt.
/usr/share/pyshared/idjc/IDJCmedia.py:1106: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  entry = list(entry)
JackTemporaryException : now quits...
jack main caught signal 2
Mixer module has closed
JACK ERROR MESSAGE: jack_client_close called with a NULL client
failed to get server stats for [http://host.acimi.com:8001/stream](http://host.acimi.com:8001/stream)

I have added JACK settings screen shot below.

I have tried many variations and I cannot seem to get a consistent end result.

---

### Post by StephenF on 2012-04-01
The Ubuntu .10 releases use JACK2. The .04 releases use JACK1 which is generally less problematic. I guess you could wait for the next Ubuntu release.

---

### Post by acimi66 on 2012-04-01
Thanks Stephen,
I have been looking into JACK2 (jack-1.9.8 )
I'll get it installed and see if it's more consistent.

---

