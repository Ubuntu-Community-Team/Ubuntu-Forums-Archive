---
title: "Maverick Pulse Audio RAOP Stutter"
date: 2011-07-09
forum: Multimedia Software
---

### Post by CCMcC on 2011-07-09
I am running Maverick on a Dell Dimension 4600C.

I stream Pandora and Rythtmbox to an airport express connected to my stereo.

After 30 minutes, the signal starts to stutter, playing and then stopping and then playing again.

I have searched for a solution to no avail. I have turned up similar inquiries so I think this is a known issue.

The following link suggests editing the  "/etc/pulse/default.pa" file to "add the tsched=0 option to module-hal-detect (or module-alsa-source if you manually load it)."

[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html](http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html)

That file does not have a "module-hal-detect" line on my machine.

Does the advice in this link make sense as a solution? Should I add the tsched=0 argument to one or both of the alsa-related lines in this file on my machine? :confused:

Thanks for any help from a stumped noobie.

Caleb

---

