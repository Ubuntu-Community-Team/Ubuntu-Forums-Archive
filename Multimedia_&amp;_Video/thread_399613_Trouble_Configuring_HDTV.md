---
title: "Trouble Configuring HDTV"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by CrazyBoyD on 2007-04-02
I just upgraded my display to an HDTV with a native resolution of 1920x1080.  When I modified my xorg.conf to include only this option, it instead chose to display at 1400x1050.  My Xorg.log.0 file mentions that there are no valid modes.  If I put lower resolution modes in, it will choose those and work just fine.  I've looked through the forums and tried generating modelines and using dpkg-reconfigure, but it doesn't help.  How can I get my computer to output 1920x1080?  I am using an NVIDIA GeForce4 TI 4200 graphics card with the latest "nvidia" driver from the edgy repositories.

---

### Post by uberben on 2008-01-14
Hey CrazyBoyD, I'm having pretty much the same issue. I'm using a 1080i plasma with VGA in and the highest resolution i can get right now is 1400x1050. I am also using a GeForce4 TI 4200. Currently I'm using the open source drivers, but I have no problem switching to the proprietary. Did you have any luck? Does anyone else have any ideas?

---

### Post by CrazyBoyD on 2008-01-14
No luck so far.  The best I can do is to pick a resolution most closely matching the native resolution of my tv, then I let the tv stretch it to fit the screen.

---

