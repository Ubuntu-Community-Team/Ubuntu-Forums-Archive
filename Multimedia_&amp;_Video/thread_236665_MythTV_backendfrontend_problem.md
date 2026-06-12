---
title: "MythTV backend/frontend problem"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by phenolholic on 2006-08-15
Ok here's another problem, I FINALLY got mythbackend and mythfrontend to load. However, when I try to go into View TV in myth's main menu, I get a menu saying

WARNING: something is already using /dev/dsp, retrying.

with two options, continue without audio & return to menu. i click 'continue without audio' and all of a sudden I get logged out of X (i see the CLI login). also, something to note, when I run mythbackend in a terminal, I get:

2006-08-15 03:57:57.776 New DB connection, total: 1
Starting up as the master server.
2006-08-15 03:57:57.785 New DB connection, total: 2
Error getting inputs for the capturecard. Perhaps you have
forgotten to bind video sources to your card's inputs?
2006-08-15 03:57:57.797 New DB scheduler connection
bttv is defined, but isn't attached to a cardinput.
2006-08-15 03:57:57.799 mythbackend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-08-15 03:57:57.800 Enabled verbose msgs : important general
2006-08-15 03:57:59.799 Reschedule requested for id -1.
2006-08-15 03:57:59.806 Scheduled 0 items in 0.0 = 0.00 match + 0.00 place
2006-08-15 03:57:59.808 Seem to be woken up by USER


Notice the 'Error getting inputs for the capturecard. Perhaps you have
forgotten to bind video sources to your card's inputs?' and the 'bttv is defined, but isn't attached to a cardinput.' ..maybe that's the reason. Also, my tv card works under xawtv. Any info would be greatly appreciated!

---

