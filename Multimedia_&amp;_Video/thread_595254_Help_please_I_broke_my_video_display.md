---
title: "Help please I broke my video display"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by d.j.schroeder on 2007-10-28
I was messing around trying to set up a mail server.  Absolutely not  a single thing to do with xorg at all.  I restarted my system and it decided not to display above 640x480.  I restarted again, same thing.  I followed the tutorial here:  [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I got through only the first part, rerunning the configuration script.  Now when the system boots I see the nice Ubuntu display as it loads everything.  Then nothing, at all.  I can't see anything and I don't even know how to get a terminal up so that I can put the old file back in place.

I do know that the system is running.  The web pages it hosts are still accessible.

Advice would be appreciated.

---

### Post by chadmounteny on 2007-10-28
press ctrl+alt+F1 and that will bring up a console screen for you

---

### Post by d.j.schroeder on 2007-10-28
I've tried that, nothing happens.  I've also tried to exit x with ctl+alt+backspace nothing happens.

---

### Post by chadmounteny on 2007-10-28
boot from a live cd, then take the xorg.conf and overwrite the one on the installed filesystem or use the grub option for ubuntu (recovery mode)

---

### Post by d.j.schroeder on 2007-10-28
Ubuntu recovery mode, boy I wish I saw that post before I did what I did.

I do have it working now, though I don't know why.  I enabled the onboard video in the BIOS and pulled out the video card.  Then at least it errored out when it couldn't start x and I got a terminal window.  I first tried to configure it to get that card to work, but of course that failed because I don't know what I'm doing, though it seemed to autodetect and fill in my answers for me.  Apparently those were incorrect though.  I copied the old xorg.conf file back and then powered down and put the video card back.

Of course now it works fine, but why?  Why did it stop working to begin with.  I don't get it.  But at least it's working.

---

