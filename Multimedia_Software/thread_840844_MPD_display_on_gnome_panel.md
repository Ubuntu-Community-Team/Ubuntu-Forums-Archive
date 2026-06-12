---
title: "MPD display on gnome panel"
date: 2008-06-25
forum: Multimedia Software
---

### Post by threespacemen on 2008-06-25
For ages and ages I'd been looking for a good way of displaying mpd's currently playing song info (ie, title, artist, position, time remaining, etc) in an unobtrusive way on the (gnome) desktop. Toyed with sonata in compact mode (a bit too large), pympd in compact mode (definitely too large), foxytunes (have to have firefox window visible at all times), etc... but ideally, what I wanted was to display the information I wanted to be able to see at all times somewhere in the gnome panel. The music applet, as great and flexible as it is, doesn't show song title and artist, which was ideally what I wanted to be able to see. Thought about writing something simple in ruby tk and using the swallower applet, but never found the time, and my programming skillz aren't such that I was confident it would actually work the way I intended. Then I found musicus:

[http://musicus-mpc.berlios.de/](http://musicus-mpc.berlios.de/)

I have no idea what the actual client app is like, as all I really wanted it for was the gnome applet that it comes with... which, aside from not being transparent on my transparent panel (I'll look into the gtk settings one of these days...), is absolutely perfect, and allows for tag-based displaying of most mpd info on the panel. It's a very recent project, by the look of it, but so far seems very stable. There's no debs, but compiling is quick and straightforward, and all the required libs are available through apt-get.

Hopefully anyone else out there looking for the same thing will find this useful!

---

### Post by Strontium on 2008-08-09
Music Applet ([http://www.kuliniewicz.org/music-applet/](http://www.kuliniewicz.org/music-applet/)) does actually support displaying scrolling song info, but the version in the repository is too old for this feature.

You can get a deb of version 2.4.0 from getdebs.net or just compile from source.
You also need to install the package python-mpdclient for MPD functionality to work.

Thanks for finding that other app I will have to try it out.

---

### Post by threespacemen on 2008-08-10
Thanks for the heads-up mate! I've actually switched full-time to gentoo these days, but it's good to see that music-applet now supports song information. That pretty much makes musicus fairly redundant (as m-a integrates better into the gnome panel, and the scrolling info is rather nice) as long as you can get your hands on 2.3 or higher. Cheers!

---

