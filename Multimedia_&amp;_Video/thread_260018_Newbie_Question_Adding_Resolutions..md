---
title: "Newbie Question: Adding Resolutions."
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by napoelon on 2006-09-18
Well, I know during installation you can pick which resolutions you will like, but stupidly, I skipped through that part, thinking when I hit Enter it will add that resolution. I got to the "Screen Resolution", and up pops up just the defaults.

How do I add resolutions like 1280x1024, etc.?

Do I need a fresh install of Ubuntu?

Thanks!

---

### Post by pay on 2006-09-18
While you're in a Gnome session you can change the screen resolution anytime by going to System>Preferences>Screen Resolution and selecting your desired resolution. If it doesn't have the sreen resolution that you want then maybe installing the video drives will help.

---

### Post by enopepsoo on 2006-09-18
You may need to install the nvidia driver if you have that sort of a card.  That is just a guesss though.

---

### Post by Druidor on 2006-09-18
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index....0Configuration](https://wiki.caosity.org/tiki-index....0Configuration)

also the "sudo dpkg-reconfigure xserver-xorg" command allows you to go through the setup of the monitor etc again.

I had the problem of not being ale to see resolutions over 1024 at full 24 bit but droopping it down to 16 allowed the 1280 resolution to be active.

---

