---
title: "Send a specific MIDI command"
date: 2018-01-22
forum: Multimedia Software
---

### Post by kazakore on 2018-01-22
What is the easiest way to send a MIDI command to a MIDI device? I want to run a reset command to my Novation Twitch controller as thus:

> The most reliable way of returning to basic mode is with a software reset. It is good practice to send this when exiting any program:
Host » Twitch:
On MIDI channel 8, set controller number 0 to value 0
(in hex: B7 00 00; in decimal: 183 0 0)

I Ubuntu Studio installed so likely have dozens of possible solutions at my fingers. Could open Ardour or the likes and try and work out how to communicate with external MIDI from that (not a program Iv'e ever actually used) but I feel there must be a simpler, more elegant method...

---

