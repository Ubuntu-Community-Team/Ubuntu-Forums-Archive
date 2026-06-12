---
title: "The Scaleo E Media Centre PC Thread"
date: 2009-10-03
forum: Multimedia Software
---

### Post by leftfootleashed on 2009-10-03
Hi,

I recently bought a Scaleo E barebones Media Centre PC from [here]("http://www.maplin.co.uk/Module.aspx?ModuleNo=228173&source=1") and currently trying to get everything up and running under an Ubuntu setup of some description. I wanted to start this thread in case anyone wants to offer me any advice about this system (particularly if they have experience using one) and so I can post updates when (and if) I get stuff working to help other people doing something similar.

I'll be using it mainly as a music jukebox, and want to listen to (and scrobble) my mp3 collection, last.fm radio and Spotify, but also want to watch stored videos, DVDs and online TV (4OD and iPlayer) sometimes, and since the box has a tuner, I'd quite like to make use of that too.

I've been flitting back and forth between a standard Jaunty install and Mythbuntu - I like the flexibility of a standard desktop, I can use whatever software I like (e.g. amarok 1.4) but Mythbuntu's 10-foot-interface is ideal, and - in theory at least - it should be easier to install and configure hardware.

The bits of hardware that seem to be giving people the hardest time are:
 - The tuner card: I think it's a dual tuner (i.e. separate analogue and digital tuners), but I don't know what make or model. I can't get  Mythbuntu to recognise it, and I don't know how to go about getting Ubuntu to use it.
 - The remote control: I got it to work partially under Mythbuntu using the Windows MCE (new) driver, but I can't figure out how to get it working with lirc (the Linux IR remote control package) under Ubuntu - there's no config file for it on the [lirc site]("http://www.lirc.org/") and I can't get irrecord (which, I think, manually  creates a config file by recording the signals from the remote) to work.
 - The front LCD display:
I've mananged to get lcdproc and LCDd (the Linux LCD packages, not sure which bit does what) to work, basically, so I get random system data (CPU usage, time, etc.) displayed, but would like to display information about currently playing media from Amarok (or failing that Mythbuntu). The driver I'm using is dm140 (I presume this is the model of LCD) which I found a link to on this [useful thread]("http://www.digital-kaos.co.uk/forums/f8/htpc-barebones-scaleo-e-10531/").
 - The front panel buttons: These worked to a certain extent under Mythbuntu, though I've no idea how. I'm not *too* bothered about them though.

At present I'm trying to knock a decent Ubuntu setup into shape, since Mythbuntu presented me with some unacceptable problems (most importantly the ability to scrobble). If anyone with Mythbuntu experience knows how I might overcome this and other problems, I'd love to hear from you. Ditto anyone who knows of a way I might create a customisable Mythbuntu-style interface for Ubuntu. In fact, I'd like to hear from anyone who has one of these boxes, no matter how much or how little you've managed to achieve.

Look forward to hearing from you

Dave :)

---

### Post by leftfootleashed on 2009-10-06
Update: Got an Amarok LCD [script]("http://www.kde-apps.org/content/show.php/lcdproc_amarok?content=39109") to work with LCDproc. Seems like the problem's been finding a script that'll work with LCDproc, rather than LCDproc not working with the hardware, as suspected. Now just gotta tweak the script to make it do what I want...

---

### Post by HeyLynx on 2012-10-17
Have you still got  the HTPC?

---

