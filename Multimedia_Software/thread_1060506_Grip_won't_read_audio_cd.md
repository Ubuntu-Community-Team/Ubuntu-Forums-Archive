---
title: "Grip won't read audio cd"
date: 2009-02-04
forum: Multimedia Software
---

### Post by lomonx on 2009-02-04
First off, I can play audio cds in Amarok fine, and I've been able to test ripping them using cdex in Windows, which also works.

Here's the problem: with Grip open I insert an audio cd and get no response. If I hit eject, it pops out the cd; if I hit eject again the cd tray comes back in and for 1 second I can see the track list for the cd as it should be. Then it disappears and says "No Disc", presumably 'cos it's set to poll every second and for some reason decides there's no disc suddenly.

Next, if I run Grip from the command line using the --verbose flag and repeat the above steps, the track list doesn't disappear at first, and CL output says "Drive status is 4" repeatedly. However, this doesn't last long and the tracks usually disappear again when I click something.

My cdrom device is set to "/dev/scd0" which seems to be where every other app is successfully looking.

I'm not sure what other info to offer at this point but happy to provide any asked for. I'd love to figure this out.

Thanks

---

### Post by icheyne on 2009-02-05
Maybe check out another ripper? [Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") is good.

---

