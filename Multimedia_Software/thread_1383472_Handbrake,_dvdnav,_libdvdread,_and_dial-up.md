---
title: "Handbrake, dvdnav, libdvdread, and dial-up"
date: 2010-01-17
forum: Multimedia Software
---

### Post by Bartender on 2010-01-17
Good day!
We're on dial-up at home.  Using our laptop, I can go into town and find some broadband.

At home we have two desktop PC's.  One running Jaunty and Handbrake .9.3, one running Karmic and HB .9.4.  I'm getting what appears to be the same errors on both PC's when using Handbrake on a DVD.  HB's activity log says that libdvdread was unable to read disc, or something like that, then I get hundreds of dvdnav errors.  CPU usage shoots to 99%.  

Then HB either disappears, or hangs, until I quit the application.  Karmic actually finished a scan on one DVD but all it picked up were the previews and extras, not the main title. 

On both PC's, Synaptic says libdvdread4 and dvdnav are installed.

On the Karmic PC I've managed to install "restricted-extras".  Not on the Jaunty PC.  I'd try installing Medibuntu but that looks like a nightmare on dial-up or via some sort of offline transfer.  If I have to, I can load the desktop PC's into the car and mooch some broadband from my step-mother-in-law :(

Anyone have any thoughts on what's missing?

---

### Post by mc4man on 2010-01-17
ck and see if libdvdcss2 is installed
It's available via the medibuntu repo (which is not 'installed', it's just a repo source that you can install packages from

For libdvdcss2 you don't have to add medibuntu, either retrieve directly from [here ]("http://packages.medibuntu.org/karmic/libdvdcss2.html")(there's no diff. between the versions other than 32 or 64 bit - you can use karmic on jaunty ect.

Or run this in a terminal - it's a very small dl, shouldn't be an issue on dialup

```
sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by Bartender on 2010-01-18
In the command you typed out, should that be libdvdcss2 instead of libdvdread4?

Anyway, I looked in Synaptic - libdvdcss2 was not there.  I just asked it to install, figuring that I could uninstall it if that's not the right thing to do...

EDIT:  That appears to have done it for the Jaunty PC running HB .9.3.  I'll try the same with the Karmic PC later on.  Thanks for the help!!

---

### Post by Bartender on 2010-01-19
Dangit, didn't work in Karmic.

No, wait a minute, yes it did.  I followed the link you provided and that worked like a charm.  I tried at first from Synaptic, which didn't list "libdvdcss2", but as you mention it's from Medibuntu repo, which I haven't installed yet so I guess it makes sense that Synaptic wouldn't know about it.  Anyway, your link worked and Karmic appears to be functional as well as Jaunty.

Thanks again!

---

