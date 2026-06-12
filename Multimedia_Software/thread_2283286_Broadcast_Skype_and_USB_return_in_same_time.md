---
title: "Broadcast Skype and USB return in same time"
date: 2015-06-20
forum: Multimedia Software
---

### Post by fraiddo on 2015-06-20
[COLOR=#111111][FONT=Ubuntu]I'm using butt [http://butt.sourceforge.net/](http://butt.sourceforge.net/) for broadcast audio, from a MP3 player and my micro - plugged into my Behringer mixer.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In Skype, all is good and my contacts hear my mic and sounds.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]And in Butt, i don't see how to send the USB return and Skype in a same time. It's possible ?[/FONT][/COLOR]

---

### Post by kostkon on 2015-06-20
Install the PulseAudio Volume Control utility (pavucontrol) from the software centre.

Start streaming as usual with butt, then open pavucontrol and you should see butt listed in the Recording tab; set the Monitor of your sound card as the recording device for butt, by clicking on the drop-down menu right next to it.

Everything that you play on your desktop should be picked up by butt, as I see it. I am not sure about your USB mic though. I have never run butt myself.

---

